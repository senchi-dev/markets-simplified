# 3. Duration

## Le piège de vocabulaire à éviter dès le départ

Le mot "duration" cache **deux concepts liés mais différents**.

- **Macaulay duration**, un concept théorique, mesuré en **années**.
- **Modified duration**, la version pratique, utilisée pour mesurer la **sensibilité du prix**, exprimée en **%**.

Beaucoup de gens les confondent. Il faut les distinguer clairement.

## Macaulay Duration, le temps moyen pondéré

C'est la **moyenne pondérée du temps** auquel tu reçois tes flux (coupons + remboursement du principal), où chaque échéance est pondérée par la **valeur actuelle** de ce flux (pas sa valeur nominale).

**Formule (intuition, sans besoin de la calculer à la main)**

`Macaulay Duration = Σ [ t × PV(flux au temps t) ] / Prix de l'obligation`

**Exemple simple, le cas extrême du zéro-coupon.** Une obligation zéro-coupon à 5 ans ne paie **rien** avant la maturité, un seul flux, à T=5. Tout le poids est concentré sur ce seul flux, donc sa Macaulay duration vaut **exactement 5 ans**, la même que sa maturité.

**Exemple avec coupons.** Une obligation à 5 ans qui paie un coupon chaque année **plus** le principal à la fin a une Macaulay duration **inférieure à 5 ans** (par exemple ~4,3 ans), parce qu'une partie de l'argent est récupérée **avant** l'échéance finale via les coupons. Plus le coupon est élevé, plus la duration est courte, tu récupères ton argent plus vite.

## La règle d'or à retenir

- Duration **augmente** avec la **maturité** (plus long terme = duration plus grande, logique).
- Duration **diminue** avec un **coupon plus élevé** (tu es remboursé plus vite en cours de route).
- Une obligation zéro-coupon a la duration **maximale** possible pour sa maturité, égale à sa maturité elle-même.

## Modified Duration, la version utilisable en pratique

C'est la mesure qu'on utilise réellement en salle de marché. Elle donne le **changement de prix approximatif en %** pour un mouvement de **1% (100 bps)** du yield.

**Formule (relation avec Macaulay)**

`Modified Duration ≈ Macaulay Duration / (1 + yield)`

**Comment l'utiliser**

`% changement de prix ≈ − Modified Duration × changement de yield`

**Exemple concret.** Une obligation a une Modified Duration de **7**. Si les yields montent de **1%** (100 bps), son prix baisse d'environ **7%**. Si les yields baissent de 0,5% (50 bps), son prix monte d'environ 3,5%.

Le signe **négatif** est essentiel, prix et yield bougent toujours en sens opposé (rappel du concept vu dans la Yield Curve).

## Pourquoi la duration est LE vrai indicateur de risque de taux

Deux obligations peuvent avoir la même maturité mais des durations très différentes selon leur coupon. Une obligation à 10 ans avec un gros coupon a une duration bien inférieure à 10, donc bien **moins sensible** aux mouvements de taux qu'une obligation zéro-coupon à 10 ans. **La maturité seule ne suffit pas à juger le risque de taux, la duration si.**

## Effective Duration (pour aller plus loin)

Pour des obligations avec des **options intégrées** (callable bonds, obligations convertibles), la Modified Duration classique ne fonctionne plus bien car les flux futurs peuvent changer selon le niveau des taux. On utilise alors l'**Effective Duration**, calculée en simulant des variations de yield et en observant l'impact réel sur le prix, plutôt qu'en utilisant la formule analytique.

## À retenir

- **Duration élevée**, petit mouvement de taux, gros mouvement de prix. Portefeuille "long duration" = très sensible aux taux.
- **Duration faible**, les taux bougent, le prix réagit peu. Portefeuille "short duration" = défensif face au risque de taux.
- Le vrai risque en fixed income n'est pas "la maturité", c'est la **sensibilité**, c'est-à-dire la duration.

> Suite logique, **DV01**, la même sensibilité, mais traduite directement en argent plutôt qu'en pourcentage.
