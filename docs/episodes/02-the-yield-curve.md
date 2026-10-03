<p class="ms-kicker">Épisode 02</p>

# The Yield <span class="ms-outline">Curve.</span>

## Définition

La **yield curve** (courbe des taux) représente, à un instant donné, le **yield** (rendement) d'obligations de **même qualité de crédit** (souvent des obligations d'État, ex. Treasuries US ou OAT françaises) mais de **maturités différentes**, 3 mois, 1 an, 2 ans, 5 ans, 10 ans, 30 ans...

En abscisse, la maturité. En ordonnée, le yield. On relie les points et on obtient une courbe.

## Pourquoi elle existe (l'intuition de base)

Normalement, prêter de l'argent plus longtemps devrait rapporter plus, car tu prends plus de risques sur une période plus longue (risque d'inflation, risque de taux, incertitude économique). C'est pour ça que la forme "par défaut" attendue est **montante**.

## Les 3 formes de la courbe

### 1. Normale / montante (upward sloping)

Taux longs supérieurs aux taux courts. C'est la forme la plus fréquente et la plus "saine". Le marché anticipe une croissance économique normale, avec des taux qui vont probablement monter ou rester stables, une période d'**expansion**.

### 2. Inversée (inverted)

Taux longs inférieurs aux taux courts. Contre-intuitif, prêter à 10 ans rapporte **moins** que prêter à 3 mois.

Ça arrive parce que les investisseurs anticipent que la banque centrale va **baisser** les taux dans le futur, car ils prévoient un ralentissement ou une récession. Ils se ruent alors sur les obligations **longues** pour verrouiller le taux actuel avant qu'il ne baisse, ce qui crée une forte demande, fait monter les **prix**, et comme prix et yield évoluent en **sens inverse**, les **yields longs baissent** mécaniquement.

C'est historiquement l'un des meilleurs prédicteurs de **récession** (l'inversion 2Y/10Y a précédé quasiment toutes les récessions US depuis 50 ans, avec un délai de 6 à 24 mois).

### 3. Plate (flat)

Peu de différence entre taux courts et longs. Le marché hésite entre scénario de croissance et scénario de ralentissement, ce qui traduit une forte **incertitude**. Souvent une phase de transition entre une courbe normale et une inversion (ou l'inverse).

## Pourquoi le prix et le yield bougent en sens inverse (rappel essentiel)

Une obligation paie des flux fixes (coupons + principal). Si le prix de marché de l'obligation **baisse**, le même flux fixe représente un **rendement plus élevé** par rapport au prix payé, donc le yield **monte**. Inversement, si le prix **monte**, le yield **baisse**. C'est mécanique, pas une coïncidence.

## Les théories qui expliquent la forme de la courbe (pour aller plus loin)

- **Expectations theory.** La courbe reflète purement les anticipations du marché sur les taux courts futurs. Si le marché anticipe des hausses de taux, la courbe est montante.
- **Liquidity preference theory.** Les investisseurs exigent une prime supplémentaire (liquidity premium) pour accepter de bloquer leur argent plus longtemps, ce qui pousse naturellement la courbe vers le haut, même sans anticipation de hausse.
- **Market segmentation theory.** Différents investisseurs (banques, assureurs, fonds de pension) ont des besoins de maturité différents et n'arbitrent pas parfaitement entre les segments, ce qui peut créer des distorsions locales sur la courbe.

## Pourquoi c'est un outil de décision concret

- Un gérant qui voit la courbe s'inverser peut **réduire son exposition aux actions cycliques** et se tourner vers des actifs défensifs.
- Les banques centrales surveillent la courbe pour calibrer leur politique monétaire.
- Les traders font des paris sur la **forme** de la courbe elle-même, pas juste son niveau. Un "steepener" parie que l'écart long-court va s'élargir, un "flattener" parie l'inverse.

## Pièges classiques à éviter

- Confondre le **niveau** des taux (tous les taux montent ou baissent ensemble) et la **forme** de la courbe (l'écart entre taux courts et longs change). Ce sont deux choses différentes.
- Une courbe inversée ne dit pas *quand* la récession arrivera précisément, juste qu'elle est anticipée par le marché.

<div class="ms-takeaway" markdown>

## À retenir

La yield curve encode les **anticipations collectives** du marché sur la trajectoire future des taux et de l'économie. Son **inversion** est l'un des signaux macro les plus suivis au monde.

</div>

> Suite logique, **Duration** et **DV01**, comment mesurer précisément la sensibilité d'une obligation à ces mouvements de taux.
