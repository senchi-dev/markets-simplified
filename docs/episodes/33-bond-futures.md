<p class="ms-kicker">Épisode 33</p>

# Bond <span class="ms-outline">Futures.</span>

## Pourquoi cet épisode

Le future sur obligation est le produit que voit un desk de taux toute la journée. C'est l'outil le plus liquide pour couvrir ou parier sur les taux, il se relie directement au [repo](11-repo.md), au [DV01](04-dv01.md) et au carry de l'[épisode 29](29-the-carry-trade.md), et c'est une question d'entretien S&T classique (« c'est quoi le cheapest-to-deliver ? »). Il a une formule, des exemples qu'on refait à la main, et un cas réel où il a cassé (mars 2020).

## D'abord, c'est quoi un future

Un future est un contrat pour acheter ou vendre quelque chose à un prix fixé, à une date fixée. Contrairement à un forward ([épisode 28](28-fx-forwards.md)), il s'échange en Bourse et il est réglé **tous les jours**.

- Tu déposes un petit montant, la **marge** (margin).
- Chaque soir, la variation du prix est payée en cash. Si tu es acheteur et que le prix baisse, tu paies. S'il monte, tu reçois. C'est le **mark-to-market**.

**Exemple.** Un future sur le Treasury américain à 10 ans, taille du contrat 100 000 $, prix coté pour 100.

```text
Achat de 1 contrat à 110,00, le prix tombe à 109,00
perte = (110 − 109) / 100 × 100 000 = 1 000 $, payés le jour même
```

Le prix est coté en points et en 32es de point. 1/32 de point vaut 100 000 / 32 / 100 = **31,25 $**. Sur le 10 ans, le plus petit pas de cotation (le tick) est la moitié de ça, soit **15,625 $**.

## Un future sur obligation

C'est un contrat pour livrer une obligation d'État à une date future. Le problème, un État émet beaucoup d'obligations différentes, avec des coupons et des maturités différents. La Bourse laisse donc le vendeur **choisir laquelle livrer**, dans un panier d'obligations éligibles (pour le 10 ans américain standard, des titres avec entre 6,5 et 10 ans de durée restante).

Pour comparer ces obligations de façon équitable, chacune reçoit un **facteur de conversion** (conversion factor, CF).

```text
CF = prix de l'obligation si elle rapportait 6 % de rendement (pour 1 de nominal)
```

Le 6 % est un rendement de référence fixé par la Bourse, pas un coupon.

**Exemple.** Une obligation à 10 ans avec un coupon de 4 %, valorisée à un rendement de 6 %.

```text
CF ≈ 0,8512
```

Plus le coupon est bas, plus le CF est petit, parce que l'obligation vaut moins à 6 %.

## Ce que reçoit le vendeur

```text
prix de facturation = prix du future × CF + intérêts courus
```

Les intérêts courus (accrued interest) sont la part du prochain coupon que le vendeur a déjà gagnée.

**Exemple.** Future à 110,00, CF = 0,85.

```text
110,00 × 0,85 = 93,50   (+ intérêts courus)
```

## Le cheapest-to-deliver (CTD)

Le vendeur choisit l'obligation qui lui coûte le moins cher à acheter par rapport à ce qu'il va recevoir. Pour chaque obligation du panier :

```text
coût net = prix pied de coupon de l'obligation − prix du future × CF
```

**Exemple.** Future à 110,00.

| Obligation | Prix (pied de coupon) | CF | Future × CF | Coût net |
|---|---|---|---|---|
| A | 93,80 | 0,85 | 93,50 | **0,30** |
| B | 101,90 | 0,92 | 101,20 | 0,70 |

L'obligation A a le coût net le plus faible, c'est donc le **CTD**. Le prix du future suit l'obligation CTD.

C'est pour ça qu'un future sur obligation n'est pas lié à une obligation précise. Son prix est à peu près :

```text
prix du future ≈ (prix du CTD + coût de portage) / CF
```

### Quelle obligation devient CTD

Le CF est calculé à 6 %. Quand les rendements du marché sont **sous 6 %**, le CTD tend à être l'obligation de **duration la plus courte** du panier. Quand ils sont **au-dessus de 6 %**, c'est plutôt celle de duration la plus longue. Quand les rendements bougent et qu'une autre obligation devient la moins chère, on dit que le CTD **bascule**. Ça change la sensibilité du future aux taux, ce qui compte pour la couverture.

## La base et le repo implicite

La **base** est le coût net ci-dessus. C'est ce que tu paies pour détenir l'obligation plutôt que le future.

Le **taux de repo implicite** est le rendement que tu gagnes en achetant le CTD et en vendant le future pour le livrer.

```text
repo implicite = (prix de facturation / prix pied plein de l'obligation aujourd'hui − 1) × 360 / jours
```

**Exemple.** CTD A. Prix pied plein aujourd'hui 94,80 (93,80 pied de coupon + 1,00 de coupon couru). Livraison dans 90 jours, coupon couru alors 2,00, future à 110,00.

```text
prix de facturation = 110 × 0,85 + 2,00 = 95,50
repo implicite = (95,50 / 94,80 − 1) × 360 / 90 = 2,95 %
```

On compare au vrai taux de [repo](11-repo.md), ce que coûte le financement de l'obligation.

| Situation | Conséquence |
|---|---|
| Repo réel 4,30 % > repo implicite 2,95 % | Emprunter coûte plus cher que ce que rapporte le trade. Pas de trade. Le future est cher par rapport à l'obligation. |
| Repo réel < repo implicite | On achète l'obligation (financée en repo), on vend le future, on empoche l'écart presque sans risque. C'est le **basis trade**. |

## Couvrir un portefeuille avec des futures

Le DV01 d'un future est à peu près le DV01 du CTD divisé par son CF.

**Exemple.** Le CTD A a une duration modifiée d'environ 7,5, prix 93,80.

```text
DV01 du CTD pour 100 000 $ de nominal = 93,80 % × 100 000 × 7,5 × 0,0001 = 70,35 $
DV01 d'un contrat de future           = 70,35 / 0,85 = 82,76 $
```

Un portefeuille d'obligations a un DV01 de 42 000 $ par point de base. Pour le couvrir, on vend des futures.

```text
contrats à vendre = 42 000 / 82,76 ≈ 507
```

Les chiffres de duration et de DV01 ici sont des ordres de grandeur pour l'exemple, pas des données de marché.

## Pourquoi les hedge funds adorent la base

Le basis trade rapporte un écart minuscule. Les fonds le font donc avec un **levier énorme**, en finançant l'achat de l'obligation en repo. C'est du carry ([épisode 29](29-the-carry-trade.md)) : petit gain régulier, grosse perte si ça se dénoue.

### Mars 2020

Début mars 2020, le marché du Treasury se tend. Les positions de basis trade subissent des pertes et des appels de marge (sur les futures et sur le repo). Les fonds revendent les obligations qu'ils détenaient et rachètent des futures. Une analyse chiffre la réduction des positions courtes en futures des hedge funds à environ 62 Md$ entre le 3 et le 17 mars 2020, accompagnée d'un dénouement équivalent de positions en obligations financées en repo.

Ce dénouement a poussé les rendements à la hausse et élargi la base, ce qui a fait perdre d'autres fonds. La Fed a acheté des Treasuries en masse, souvent cité à environ 1 600 Md$ entre mars et mai 2020 (source secondaire).

**À nuancer.** Les chercheurs ne sont pas d'accord sur le poids du basis trade. L'OFR et la Dallas Fed disent que le dénouement a amplifié le stress. Une étude de la Fed de Cleveland estime que c'était plutôt une conséquence qu'une cause principale. Le point sûr, les positions étaient levier, et le dénouement a eu lieu en même temps que le reste de la crise.

## Pièges classiques

- **Croire qu'un future suit une seule obligation.** Il suit le CTD, qui peut changer.
- **Oublier le facteur de conversion.** Le DV01 et la couverture se calculent avec le CF.
- **Confondre future et forward.** Le future est réglé chaque jour (appels de marge), le forward à l'échéance.
- **Le 6 % n'est pas un coupon.** C'est un rendement de référence pour calculer le CF.
- **Ignorer le mark-to-market.** Une position gagnante sur le papier peut vider le cash si les appels de marge tombent avant que le prix revienne.
- **Prendre le basis trade pour sans risque.** Sans levier il est presque sans risque. Avec un levier de 50 ou 100, c'est une vente de volatilité de financement.
- **Utiliser des chiffres de duration approximatifs pour couvrir.** Le DV01 du CTD doit être recalculé quand les rendements bougent.

## L'angle entretien S&T

**« C'est quoi le cheapest-to-deliver ? »** L'obligation du panier éligible que le vendeur du future a intérêt à livrer, celle qui minimise prix de l'obligation moins prix du future fois facteur de conversion. Le prix du future suit le CTD.

**« À quoi sert le facteur de conversion ? »** À rendre comparables des obligations de coupons et de maturités différents. C'est le prix de l'obligation à un rendement de 6 %, par unité de nominal.

**« Comment couvres-tu un portefeuille avec des futures ? »** Je calcule le DV01 du portefeuille, le DV01 d'un contrat (DV01 du CTD divisé par son CF), et je vends le nombre de contrats qui égalise les deux.

**« C'est quoi un basis trade ? »** Acheter l'obligation CTD financée en repo et vendre le future. Je gagne le repo implicite moins le coût réel du repo. Un petit gain, qu'on lève avec beaucoup de levier.

**« Que s'est-il passé en mars 2020 ? »** Les basis trades levier ont subi des appels de marge pendant la crise de liquidité, ont vendu leurs obligations, ont poussé les rendements à la hausse, et la Fed a dû acheter des Treasuries en masse.

**« Quand le CTD bascule-t-il ? »** Quand les rendements bougent assez pour qu'une autre obligation du panier devienne la moins chère à livrer. Sous 6 % de rendement, c'est plutôt la duration la plus courte.

## Liens avec les épisodes précédents

- [Repo](11-repo.md), le financement du basis trade et le repo implicite.
- [DV01](04-dv01.md) et [Duration](03-duration.md), pour calculer le nombre de contrats à vendre.
- [FX Forwards](28-fx-forwards.md), le future est un forward réglé chaque jour.
- [The Carry Trade](29-the-carry-trade.md), le basis trade est du carry avec levier.
- [QE and QT](27-qe-and-qt.md), la Fed qui rachète des Treasuries en mars 2020.
- [Pricing Rate Cuts](30-pricing-rate-cuts.md), le future sur fed funds est le même type de contrat sur le taux court.

<div class="ms-takeaway" markdown>

## À retenir

- Un future est un contrat standardisé, réglé chaque jour (mark-to-market, marge).
- Un future sur obligation laisse le vendeur choisir quelle obligation livrer dans un panier. Prix de facturation = prix du future × CF + intérêts courus.
- Le CTD est l'obligation qui minimise : prix − future × CF. Le future suit le CTD.
- Repo implicite = (facturation / prix pied plein − 1) × 360 / jours. S'il est plus haut que le vrai repo, le basis trade rapporte.
- DV01 d'un contrat ≈ DV01 du CTD / CF. On l'utilise pour dimensionner une couverture.
- Le basis trade est du carry avec levier, et il s'est dénoué en mars 2020, avec une Fed qui a dû racheter des Treasuries en masse.

</div>
