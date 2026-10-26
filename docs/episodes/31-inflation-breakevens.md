<p class="ms-kicker">Épisode 31</p>

# Inflation <span class="ms-outline">Breakevens.</span>

## Pourquoi cet épisode

Les épisodes [26](26-the-policy-rate.md), [27](27-qe-and-qt.md) et [30](30-pricing-rate-cuts.md) parlaient de la moitié « taux » du travail d'une banque centrale. L'autre moitié, c'est l'inflation, et c'est elle qui explique pourquoi elle monte ou baisse ses taux. Cet épisode montre comment lire ce que le marché attend comme inflation, directement dans le prix des obligations. C'est un outil de base sur un desk de taux, il tient en une formule, et il a des cas réels très clairs.

## Le problème

Une obligation classique paie un montant fixe, donc l'inflation en réduit la valeur réelle. Une obligation à 10 ans qui paie 4,20 % par an vaut moins en pouvoir d'achat si les prix montent de 5 % par an. Les investisseurs ont donc voulu une obligation qui les protège. Elle existe.

## Les obligations indexées sur l'inflation

Aux États-Unis, ce sont les **TIPS** (Treasury Inflation-Protected Securities). Au Royaume-Uni, les **index-linked gilts** ("linkers"). En France, les OATi et OAT€i. Le principe est le même.

- Le **principal** (le montant remboursé à la fin) est ajusté selon l'**indice des prix à la consommation** (CPI, le panier de prix suivi par un pays).
- Le **coupon** est un pourcentage fixe de ce principal ajusté.
- À l'échéance, tu récupères le principal ajusté, et aux États-Unis jamais moins que le nominal d'origine (le plancher anti-déflation).

**Exemple.** 1 000 $ de nominal, coupon 2 %, et les prix ont monté de 3 % depuis l'émission.

```text
ratio d'indice      = 1,03
principal ajusté    = 1 000 × 1,03 = 1 030 $
coupon              = 2 % × 1 030 = 20,60 $   (au lieu de 20,00 $)
```

Le rendement d'un TIPS s'appelle le **rendement réel**. C'est ce que tu gagnes **au-dessus** de l'inflation.

## La formule du breakeven

Un 10 ans nominal paie 4,20 %. Un 10 ans TIPS paie un rendement réel de 1,90 % **plus l'inflation**. Lequel est le meilleur dépend de l'inflation qui arrivera. Le niveau d'inflation où les deux donnent exactement le même résultat s'appelle le **breakeven** (point mort).

**Approximation.**

```text
breakeven = rendement nominal − rendement réel
          = 4,20 % − 1,90 % = 2,30 %
```

**Version exacte**, l'équation de Fisher.

```text
(1 + nominal) = (1 + réel) × (1 + inflation)
inflation     = 1,042 / 1,019 − 1 = 2,26 %
```

### Vérification avec de l'argent

Tu investis 1 $ sur 10 ans, à l'un ou l'autre.

```text
Nominal :  1,042^10                        = 1,509
TIPS    :  (1,019 × (1 + inflation))^10
   inflation 1,00 % par an  ->  1,334      le nominal gagne
   inflation 2,26 % par an  ->  1,509      égalité
   inflation 3,00 % par an  ->  1,622      le TIPS gagne
```

Lecture.

- Si l'inflation moyenne sur 10 ans est **au-dessus de 2,26 %**, le TIPS gagne.
- Si elle est **en dessous**, le nominal gagne.

Donc le breakeven est le **prix de l'inflation** par le marché. Qui pense que l'inflation sera plus haute que le breakeven achète le TIPS. Qui pense qu'elle sera plus basse achète le nominal.

## Ce que contient vraiment le breakeven

```text
breakeven = inflation attendue + prime de risque d'inflation − prime de liquidité
```

- **Prime de risque d'inflation.** Le supplément de rendement que veulent les détenteurs d'obligations nominales, parce qu'une inflation surprise leur fait mal.
- **Prime de liquidité.** Les TIPS sont plus difficiles à échanger, donc leur rendement est un peu plus haut, ce qui **baisse** le breakeven.

Le breakeven n'est donc pas une prévision pure. C'est la même leçon que pour l'[OIS](30-pricing-rate-cuts.md) et le forward, un prix qui reflète surtout des anticipations, plus un peu de bruit. En crise de liquidité, le bruit domine (mars 2020 plus bas).

## Le forward d'inflation : le 5y5y

On compare deux breakevens de durées différentes, comme pour le forward entre deux [OIS](30-pricing-rate-cuts.md) ou le forward FX de l'[épisode 28](28-fx-forwards.md).

```text
(1 + BE10)^10 = (1 + BE5)^5 × (1 + f)^5
f = [ (1 + BE10)^10 / (1 + BE5)^5 ]^(1/5) − 1
```

**Exemple.** BE à 5 ans = 2,50 %, BE à 10 ans = 2,30 %.

```text
f = [ 1,023^10 / 1,025^5 ]^(1/5) − 1 = 2,10 %
Raccourci : 2 × 2,30 − 2,50 = 2,10 %
```

Le marché attend 2,50 % d'inflation par an pendant 5 ans, puis **2,10 %** par an pendant les 5 ans d'après. C'est le **5y5y forward**, l'indicateur que les banques centrales regardent le plus. Il enlève le court terme (énergie, chocs temporaires) et mesure si le marché croit que l'inflation reviendra vers la cible de 2 % à long terme. S'il monte nettement au-dessus, la banque centrale a un problème de crédibilité, et elle réagit plus fort.

## Le swap d'inflation

Les desks n'échangent pas que des obligations. Ils utilisent des **swaps d'inflation zero-coupon**, qui donnent le breakeven sans avoir à acheter ni vendre d'obligation, avec la même logique qu'un [swap de taux](10-interest-rate-swaps.md).

- Le **payeur de fixe** paie `(1 + K)^T − 1` à l'échéance (K = le taux fixe d'inflation, T = les années).
- Il reçoit `CPI(T) / CPI(0) − 1`, l'inflation réellement mesurée.
- On n'échange que la différence.

**Exemple.** 10 ans, K = 2,30 %, notionnel 10 M$.

```text
Partie fixe :  1,023^10 − 1 = 25,53 %
Si les prix ont monté de 28 % au total en 10 ans :
  le payeur de fixe reçoit 28 % − 25,53 % = 2,47 % du notionnel = environ 247 000 $
Si les prix n'ont monté que de 20 % :
  il perd 25,53 % − 20 % = 5,53 % = environ 553 000 $
```

Les banques et les fonds de pension s'en servent. Un fonds de pension qui doit verser des retraites indexées sur l'inflation **reçoit** l'inflation pour se couvrir.

## Le trade et son P&L

Tu penses que l'inflation sera au-dessus du breakeven. Tu **achètes le TIPS et tu vends un nominal de même maturité**. C'est un **breakeven trade** (long breakevens).

Comme les deux obligations n'ont pas la même [duration](03-duration.md), on dimensionne avec le [DV01](04-dv01.md) pour garder la même sensibilité aux taux et ne garder que le pari sur l'inflation.

**Exemple.** On achète 10 M$ de TIPS 10 ans (duration réelle 8,4) et on vend du nominal 10 ans (duration 8,0).

```text
DV01 du TIPS     = 10 000 000 × 8,4 × 0,0001 = 8 400 $ par bp
Nominal à vendre = 8 400 / (8,0 × 0,0001) = 10,5 M$
```

Si le rendement réel baisse de 54 bps et que le nominal ne bouge pas, le breakeven passe d'environ 2,30 % à 2,84 %.

```text
P&L ≈ 8 400 × 54 = 453 600 $
```

Attention, ce calcul suppose que le rendement nominal est inchangé. Dans la réalité, quand l'inflation surprend à la hausse, les deux rendements bougent. Le trade ne garde que la **différence**.

## Cas réels

### Mars 2020, le Covid : le breakeven s'effondre

Le breakeven américain à 10 ans (série T10YIE de la Fed de St. Louis) passe d'environ 1,7 % début mars 2020 à environ 0,5 % en moins de deux semaines, avec un point bas autour du 19 mars (les sources secondaires donnent 0,50 %). Il finit le mois autour de 0,87 %. Le pétrole s'effondre, la demande aussi, et les investisseurs paient presque rien pour se protéger de l'inflation.

**Mais ce n'était pas qu'une prévision de déflation.** Pendant la ruée sur le cash de mars 2020, les investisseurs ont vendu tout ce qui se vendait, y compris les TIPS, moins liquides que les nominaux. La prime de liquidité a explosé, ce qui a écrasé le breakeven. Une partie du mouvement est du bruit, pas de l'information.

### 2021-2022 : l'inflation revient

L'inflation américaine passe d'environ 1,4 % début 2021 à plus de 9 % en juin 2022. Le breakeven à 10 ans monte autour de 3 % le 21 avril 2022 (2,99 % ou 3,02 % selon la source), son niveau le plus haut depuis 2008. Puis la Fed monte ses taux ([épisode 26](26-the-policy-rate.md)) et le breakeven retombe vers 2,1 % à 2,3 % fin 2022.

**Ce que ça montre.** Le marché n'a **pas** cru que l'inflation resterait à 8-9 %. Un breakeven à 10 ans autour de 3 %, ce n'est pas 9 %. Le 10 ans anticipait que la Fed ramènerait l'inflation. Les breakevens à 1 ou 2 ans, eux, étaient bien plus hauts (au-dessus de 4 % au printemps 2022). La **courbe** des breakevens inversée disait la même chose que la courbe des taux, de l'inflation maintenant, de la modération plus tard.

### Septembre 2022, Royaume-Uni : les linkers dans la crise LDI

La crise des fonds LDI de l'[épisode 27](27-qe-and-qt.md) touche aussi les gilts indexés. Les fonds de pension britanniques détiennent des linkers parce que leurs retraites versées sont indexées sur l'inflation. Les fonds LDI offrent une exposition avec levier à des gilts, dont des indexés. Quand les ventes forcées ont commencé, la Banque d'Angleterre a d'abord racheté des gilts longs classiques à partir du 28 septembre, puis a élargi ses achats aux **gilts indexés** le 11 octobre 2022, une première pour elle.

**La leçon.** Les breakevens et les linkers sont des instruments de **couverture** pour des acteurs énormes. Quand ils vendent sous contrainte, les prix bougent beaucoup, et ça n'a rien à voir avec l'inflation attendue.

## Pièges classiques

- **Prendre le breakeven pour une prévision d'inflation pure.** Il contient une prime de risque et une prime de liquidité.
- **Comparer des durées différentes.** Le breakeven à 5 ans et celui à 10 ans ne mesurent pas la même chose. Le 5y5y est le bon outil pour la période lointaine.
- **Oublier le décalage de l'indice.** Les TIPS utilisent le CPI avec un retard d'environ 3 mois (interpolation entre deux mois). Les ajustements du principal arrivent donc en retard sur les prix réels.
- **Ne pas dimensionner le trade.** Acheter 10 M$ de TIPS et vendre 10 M$ de nominal n'est pas neutre en taux, parce que les durations diffèrent. Il faut passer par le DV01.
- **Le plancher de déflation.** Aux États-Unis, le principal n'est jamais remboursé en dessous du nominal d'origine. Ça a de la valeur (c'est une option), surtout pour les TIPS émis récemment.
- **Mélanger inflation et variation du breakeven.** Si l'inflation réalisée dépasse le breakeven mais que celui-ci a baissé entre-temps, un trade avant l'échéance peut perdre.

## L'angle entretien S&T

**« C'est quoi un breakeven d'inflation ? »** La différence entre le rendement d'une obligation nominale et celui d'une obligation indexée de même maturité. C'est le niveau d'inflation où les deux rapportent pareil. Nominal 4,20 %, réel 1,90 %, breakeven 2,30 % (2,26 % avec Fisher).

**« Ça veut dire que le marché prévoit 2,30 % d'inflation ? »** Pas exactement. Le breakeven contient aussi une prime de risque d'inflation et une prime de liquidité. En mars 2020, la liquidité l'a fait chuter bien plus que les attentes réelles.

**« Ton trade si tu penses que l'inflation sera plus haute que le marché ne price ? »** Long breakeven, acheter le TIPS et vendre un nominal de même maturité, dimensionné au DV01. Ou recevoir l'inflation sur un swap zero-coupon.

**« C'est quoi le 5y5y ? »** Le taux d'inflation attendu par an entre dans 5 ans et dans 10 ans. Les banques centrales le surveillent, parce qu'il mesure l'ancrage des anticipations à long terme.

**« Qui reçoit l'inflation sur un swap ? »** Les fonds de pension et assureurs avec des engagements indexés sur l'inflation. Ils veulent être couverts si elle monte.

**« Pourquoi la Fed s'en soucie ? »** Parce que si les anticipations de long terme se détachent de 2 %, les gens et les entreprises fixent salaires et prix plus haut, et l'inflation s'auto-entretient. Elle doit alors monter ses taux plus fort.

## Liens avec les épisodes précédents

- [The Policy Rate](26-the-policy-rate.md), la banque centrale monte ses taux pour ramener l'inflation vers sa cible.
- [QE and QT](27-qe-and-qt.md), la crise LDI britannique touche aussi les linkers.
- [Pricing Rate Cuts](30-pricing-rate-cuts.md), même logique de lire une anticipation dans un prix, et même forward entre deux horizons.
- [Duration](03-duration.md) et [DV01](04-dv01.md), pour dimensionner le trade breakeven.
- [Interest Rate Swaps](10-interest-rate-swaps.md), le swap d'inflation a la même structure.
- [FX Forwards](28-fx-forwards.md), même formule de forward entre deux horizons.

<div class="ms-takeaway" markdown>

## À retenir

- Une obligation indexée ajuste son principal sur l'inflation. Son rendement est le rendement **réel**.
- Breakeven ≈ rendement nominal − rendement réel. Exact par Fisher : (1 + nominal) = (1 + réel) × (1 + inflation).
- Si l'inflation dépasse le breakeven, le TIPS gagne. Sinon, le nominal gagne.
- Le breakeven contient une prime de risque et une prime de liquidité. Ce n'est pas une prévision pure.
- Le 5y5y forward, f ≈ 2 × BE10 − BE5, mesure l'ancrage des anticipations à long terme.
- Le trade long breakeven se dimensionne au DV01. Mars 2020 (0,5 %), avril 2022 (environ 3 %) et la crise des linkers britanniques montrent que les breakevens bougent aussi pour des raisons de liquidité.

</div>
