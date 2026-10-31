<p class="ms-kicker">Épisode 32</p>

# <span class="ms-outline">ETFs.</span>

## Pourquoi cet épisode

Tout le monde possède un ETF ou connaît quelqu'un qui en possède un. Presque personne ne sait pourquoi son prix reste collé à ce qu'il contient. C'est une histoire d'arbitrage, comme la [put-call parity](14-put-call-parity.md) ou le [forward FX](28-fx-forwards.md), avec une formule, des calculs qu'on refait à la main, et des cas réels où le mécanisme a cassé. C'est aussi une question d'entretien classique.

## C'est quoi un ETF

ETF = exchange-traded fund, un fonds coté. Un fonds détient un panier d'actifs (par exemple les 500 actions du S&P 500) et tu achètes une part du fonds en Bourse, comme une action.

Deux prix comptent.

- **La NAV** (net asset value, valeur liquidative). Ce que vaut réellement le panier à l'intérieur, par part.
- **Le prix de marché.** Ce à quoi l'ETF s'échange en Bourse.

```text
NAV par part = (valeur de tous les actifs − dettes) / nombre de parts
```

Si le panier vaut 5 000 000 $ et qu'il y a 50 000 parts, la NAV est de **100 $**.

Un fonds classique (un OPCVM ou mutual fund) s'achète et se vend directement à la NAV auprès du fonds, une fois par jour. Un ETF s'échange entre investisseurs toute la journée, donc son prix pourrait s'éloigner de la NAV. Il ne le fait presque pas, à cause d'un mécanisme.

## Pourquoi le prix reste proche de la NAV

Des acteurs appelés **participants autorisés** (authorized participants, APs), de grandes banques et des teneurs de marché, ont le droit de **créer et de détruire** des parts d'ETF directement avec l'émetteur. Ça se fait par blocs appelés **creation units** (par exemple 50 000 parts, la taille varie selon les fonds), en général **en nature** (in kind), c'est-à-dire qu'on échange le panier contre des parts, pas du cash.

### L'ETF cote au-dessus de la NAV (prime)

NAV 100 $, prix de marché 100,40 $.

```text
prime = 100,40 / 100 − 1 = +0,40 %
```

L'AP fait ceci.

1. Il achète le panier sur le marché, 50 000 × 100 $ = 5 000 000 $.
2. Il le remet à l'émetteur, qui lui donne 50 000 parts neuves.
3. Il les vend à 100,40 $, soit 50 000 × 100,40 = 5 020 000 $.
4. Profit = **20 000 $** (avant frais).

Vendre toutes ces parts fait baisser le prix de l'ETF vers la NAV.

### L'ETF cote sous la NAV (décote)

NAV 100 $, prix 99,60 $, soit une décote de −0,40 %.

1. L'AP achète 50 000 parts pour 4 980 000 $.
2. Il les rend à l'émetteur et reçoit le panier, qui vaut 5 000 000 $.
3. Il vend le panier.
4. Profit = **20 000 $**.

Acheter les parts fait remonter le prix vers la NAV.

### La limite

```text
écart maximal ≈ coûts de l'AP (frais de transaction + bid-ask + coût de couverture)
```

Tant que l'écart dépasse les coûts, l'arbitrage rapporte de l'argent, donc quelqu'un le fait, donc l'écart se referme. C'est la **bande d'arbitrage**.

### Le prix en direct, l'iNAV

La NAV officielle est calculée une fois par jour, à la clôture. Pendant la séance, l'émetteur publie une estimation, l'**iNAV** (indicative NAV), recalculée toutes les quelques secondes à partir des prix du panier. C'est la référence des APs.

## Marché primaire et marché secondaire

| | Marché primaire | Marché secondaire |
|---|---|---|
| Qui | Les APs et l'émetteur | Tous les investisseurs |
| Quoi | Création et destruction de parts, par blocs | Achat et vente de parts existantes en Bourse |
| Prix | À la NAV (panier contre parts) | Prix de marché, avec un bid-ask |

Quand tu achètes un ETF en Bourse, tu achètes une part existante à un autre investisseur. L'ETF n'a pas besoin de vendre ses actifs. Le primaire n'intervient que si la demande ou l'offre dépasse ce que le secondaire absorbe.

## Ce que ça coûte vraiment

### Le tracking difference

```text
tracking difference = rendement de l'ETF − rendement de l'indice
                    ≈ − frais de gestion + revenus de prêt de titres − coûts de transaction
```

**Exemple.** Indice +8,00 %, frais de gestion 0,20 %, l'ETF rend +7,82 %. Le tracking difference est de −0,18 % (le fonds a aussi gagné un peu en prêtant ses titres).

Le **tracking error** est autre chose. C'est la volatilité de cet écart dans le temps. Un tracking error faible veut dire que l'ETF suit l'indice de près jour après jour.

### L'effet des frais sur 10 ans

10 000 $ placés 10 ans avec un rendement brut de 7 % par an.

| Frais annuels | Valeur après 10 ans |
|---|---|
| 0,20 % (ETF indiciel) | 10 000 × 1,068^10 = **19 307 $** |
| 1,00 % (fonds actif classique) | 10 000 × 1,06^10 = **17 908 $** |
| Écart | **1 398 $**, soit environ 14 % du capital de départ |

### Le bid-ask

À l'achat et à la vente, tu paies aussi l'écart entre le prix acheteur et le prix vendeur. Pour un ETF liquide, il peut être de 0,01 % à 0,05 %. Sur 100 000 $ avec un bid-ask de 0,04 %, un aller-retour coûte environ 40 $. Pour un ETF peu échangé, ça peut dépasser 0,5 %.

## Quand le mécanisme casse

L'arbitrage marche tant que l'AP peut **acheter et vendre le panier** rapidement et à un prix connu. Dans une panique, ce n'est plus vrai.

### 1. Le 24 août 2015, le « flash crash » des ETFs

Le lundi 24 août 2015, le marché américain ouvre après une chute des marchés chinois. L'indice S&P 500 perd environ 5 % à un moment de la séance. Beaucoup d'actions n'ouvrent pas à l'heure ou sont suspendues à répétition (les règles de circuit-breaker individuelles), donc **le panier n'a pas de prix fiable**. L'iNAV devient faux et les APs ne savent plus comment arbitrer.

D'après la note de recherche de la SEC publiée en décembre 2015, environ 19 % des produits cotés (ETPs) ont perdu 20 % ou plus à un moment de la séance, contre moins de 5 % des actions. Plus d'un millier de suspensions ont touché 327 ETPs. Certains ETFs ont coté très en dessous de leur NAV pendant quelques minutes, parce qu'il n'y avait plus de prix de référence pour les actions qu'ils détenaient.

**Pourquoi.** Le prix d'un ETF est dérivé du panier. Sans prix pour le panier, le prix de l'ETF devient un simple prix de panique, qui se corrige quand le panier reprend des cotations.

### 2. Mars 2020, les ETFs obligataires

Les obligations s'échangent peu, de gré à gré (OTC). Dans une panique, **l'ETF peut être la seule chose qui s'échange**. Il devient la vraie « découverte du prix », et la NAV, calculée à partir de prix d'obligations anciens ou estimés, est en retard.

Des chiffres de cette période.

- L'ETF obligataire américain BND (marché obligataire global) a coté environ 6 % sous sa NAV le 12 mars 2020, avant de revenir à environ 1,7 % de décote le lendemain.
- L'ETF d'obligations d'entreprises LQD a coté sous sa NAV d'environ 3 % à 5 % selon la mesure et le moment, la semaine du 16 au 20 mars.
- Le 23 mars, la Fed annonce qu'elle va acheter des **ETFs** d'obligations d'entreprises, une première. Dans la foulée, LQD passe d'une décote d'environ 2,8 % le 20 mars à une prime d'environ 2,9 % le 23 mars, alors que sa NAV n'avait pris qu'environ 1,4 %. Les achats d'ETFs n'ont démarré que plusieurs semaines plus tard, ce qui montre que l'annonce a suffi.

**Pourquoi.** Les APs ne pouvaient plus acheter le panier d'obligations, qui ne se vendait presque pas, donc ils ne pouvaient plus arbitrer la décote. Et la décote n'était pas forcément une erreur. Elle reflétait que la **vraie** valeur des obligations était plus basse que la NAV affichée.

**La leçon.** Un ETF n'est liquide que dans la mesure où ses actifs le sont. Plus l'actif sous-jacent est illiquide (obligations d'entreprises, high yield, dette émergente), plus l'écart avec la NAV peut être grand en stress.

## Les ETFs à effet de levier, l'effet de la remise à zéro quotidienne

Un ETF 2x vise **2 fois le rendement journalier** de l'indice, pas 2 fois sur la durée. Il remet son levier à zéro chaque jour.

**Exemple.** L'indice monte de 10 % un jour puis baisse de 10 % le lendemain.

```text
Indice :        1,10 × 0,90 = 0,99      soit −1 %
ETF 2x :        1,20 × 0,80 = 0,96      soit −4 %
```

Il aurait fallu −2 % pour « 2 fois ». Trois jours (+10 %, −10 %, +10 %) :

```text
Indice :        1,10 × 0,90 × 1,10 = 1,089     +8,9 %
ETF 2x :        1,20 × 0,80 × 1,20 = 1,152     +15,2 %   (et non +17,8 %)
```

Plus l'indice oscille, plus l'écart se creuse. Ce « volatility drag » est la raison pour laquelle ces produits sont faits pour quelques jours, pas pour des années.

## Réplication physique ou synthétique

- **Physique.** L'ETF détient vraiment les actions ou obligations de l'indice (ou un échantillon représentatif).
- **Synthétique.** L'ETF détient un autre panier et conclut un **swap** avec une banque, qui lui verse le rendement de l'indice. Fréquent en Europe pour des indices difficiles d'accès. Un risque en plus, celui de la banque qui fait le swap (le risque de contrepartie, vu dans l'épisode [CDS](06-credit-default-swaps.md)).

## Pièges classiques

- **Acheter un ETF peu liquide à n'importe quel prix.** Le bid-ask peut manger plusieurs mois de rendement. Utiliser des ordres limite et regarder l'iNAV.
- **Acheter à l'ouverture ou à la clôture d'une séance agitée.** C'est là que l'écart avec la NAV est le plus grand.
- **Confondre la liquidité de l'ETF et celle de ses actifs.** Un ETF obligataire se négocie comme une action mais son panier, non.
- **Oublier le volatility drag** sur les ETFs à effet de levier ou inversés.
- **Croire que le tracking error est un coût.** C'est une dispersion, le coût c'est le tracking difference.
- **Ignorer le risque de contrepartie** des ETFs synthétiques.
- **Prendre une décote pour un cadeau.** En mars 2020, la décote reflétait en partie une vraie valeur plus basse que la NAV, pas seulement une erreur de prix.

## L'angle entretien S&T

**« Comment un ETF reste-t-il proche de sa NAV ? »** Par l'arbitrage des participants autorisés. Si l'ETF cote au-dessus de la NAV, l'AP achète le panier, crée des parts et les vend, ce qui fait baisser le prix. En dessous de la NAV, il achète des parts, les rachète contre le panier et le vend, ce qui fait monter le prix.

**« Pourquoi un ETF obligataire peut-il décoter beaucoup plus qu'un ETF actions ? »** Parce que l'arbitrage suppose de pouvoir acheter ou vendre le panier. Les obligations s'échangent peu et la NAV utilise des prix en retard. En stress, l'ETF devient le vrai prix.

**« Quelle est la différence entre tracking error et tracking difference ? »** Le tracking difference est l'écart de rendement cumulé entre l'ETF et son indice, en gros les frais. Le tracking error est la volatilité de cet écart.

**« Pourquoi un ETF 2x ne fait pas deux fois la performance sur un an ? »** Il remet son levier à zéro chaque jour. Quand le marché oscille, la composition fait perdre de la valeur. Exemple, +10 % puis −10 % donne −1 % pour l'indice et −4 % pour le 2x.

**« Quel est le rôle d'un teneur de marché sur un ETF ? »** Coter un bid-ask, couvrir son risque avec le panier ou des futures, et créer ou racheter des parts quand l'écart dépasse ses coûts.

**« Les flux d'ETFs peuvent-ils faire bouger le marché ? »** Oui. Des créations ou rachats massifs obligent les APs à acheter ou vendre le panier sous-jacent, ce qui pèse sur ses prix, surtout sur des actifs peu liquides.

## Liens avec les épisodes précédents

- [Put-Call Parity](14-put-call-parity.md), même logique d'arbitrage, deux chemins qui doivent coûter pareil.
- [FX Forwards](28-fx-forwards.md), un prix fixé par l'arbitrage et non par une prévision.
- [QE and QT](27-qe-and-qt.md), mars 2020 et l'achat d'ETFs obligataires par la Fed.
- [Credit Spread](05-credit-spread.md), les obligations d'entreprises que détient LQD.
- [Credit Default Swaps](06-credit-default-swaps.md), le risque de contrepartie des ETFs synthétiques.
- [Repo](11-repo.md), la liquidité des marchés obligataires en stress.

<div class="ms-takeaway" markdown>

## À retenir

- Un ETF est un panier coté. NAV = (actifs − dettes) / nombre de parts.
- Son prix reste proche de la NAV parce que des participants autorisés créent ou rachètent des parts par blocs, et empochent l'écart (exemple, 0,40 % sur 5 M$ = 20 000 $).
- Le coût réel, c'est le tracking difference (≈ frais de gestion) plus le bid-ask. 0,20 % contre 1,00 % de frais, c'est environ 1 400 $ d'écart sur 10 000 $ en 10 ans.
- L'arbitrage casse quand le panier n'a plus de prix fiable (24 août 2015) ou ne peut plus se négocier (obligations en mars 2020).
- Les ETFs à effet de levier remettent leur levier à zéro chaque jour. +10 % puis −10 % donne −1 % pour l'indice et −4 % pour un 2x.
- Un ETF n'est liquide que dans la mesure où ses actifs le sont.

</div>
