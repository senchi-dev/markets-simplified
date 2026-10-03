<p class="ms-kicker">Épisode 18</p>

# <span class="ms-outline">Vega.</span>

## Pourquoi cet épisode

Delta et Gamma étaient sur le prix de l'action, Theta sur le temps. Vega est sur la **volatilité**, l'ampleur des mouvements attendus. On avait croisé la volatilité sans la traiter (épisode Options, « plus l'action est volatile, plus les options sont chères », et le VIX).

## Définition

Le Vega mesure combien le prix de l'option change quand la **volatilité** du sous-jacent bouge de 1 point (1%). La volatilité = à quel point le marché s'attend à ce que l'action bouge dans tous les sens.

## Pourquoi la volatilité fait monter le prix

Une option est un pari sur un mouvement futur. Plus l'action bouge fort, plus il y a de chances qu'elle franchisse le strike et finisse rentable. Donc plus de volatilité = option plus chère, pour un call **comme** pour un put (les deux profitent d'un gros mouvement, chacun dans son sens).

## Exemple chiffré

Call à 5€, Vega = 0,20.

- Volatilité 20% → 21% (+1 point) : option ~5,20€.
- Volatilité 20% → 18% (-2 points) : option ~4,60€.

Et ça **sans que l'action ait bougé d'un centime**. C'est juste l'anticipation du marché sur l'ampleur des mouvements futurs qui change.

## Acheteur vs vendeur

- **Acheteur** : **long vega**, gagne si la volatilité monte.
- **Vendeur** : **short vega**, gagne si la volatilité baisse.

## Trader la volatilité, pas la direction (le cœur du métier)

Avec le Delta on parie sur la **direction** (monte/baisse). Avec le Vega on parie sur **l'ampleur** des mouvements, sans avis sur le sens. Exemple, une élection ou des résultats dans une semaine, on ne sait pas si ça monte ou baisse mais on est sûr que ça va bouger fort. Acheter des options (long vega) profite de la hausse de volatilité quelle que soit la direction finale. Pari pur sur « il va se passer quelque chose ».

## Volatilité implicite vs réalisée (distinction clé)

Le Vega réagit à la **volatilité implicite**, celle que le marché *anticipe* (intégrée dans le prix des options aujourd'hui), pas la volatilité *réalisée* (celle qui s'est produite dans le passé). Le prix d'une option peut grimper juste parce que le marché s'attend à plus de turbulences, même si rien ne s'est encore passé.

## Le piège classique, le vol crush

Juste avant un gros événement (résultats trimestriels), la volatilité implicite est **gonflée** (tout le monde anticipe du mouvement). Une fois l'événement passé, l'incertitude disparaît, la volatilité implicite **s'effondre** (le « vol crush »). Résultat piège, un débutant achète un call avant les résultats, l'action monte comme espéré, mais l'option **perd quand même de la valeur** car l'effondrement du vega a mangé plus que la hausse du prix n'a rapporté. Raison sur la direction, perte quand même.

## Où le Vega est le plus fort

Maximal **ATM** et pour les **échéances longues** (plus il reste de temps, plus la volatilité a d'espace pour agir). Même endroit que le gamma et le theta max, tout ça mesure la même « valeur temps » sous des angles différents.

<div class="ms-takeaway" markdown>

## À retenir

Vega = sensibilité du prix de l'option à la volatilité. Long vega (acheteur) gagne si la vol monte, short vega (vendeur) si elle baisse. Permet de parier sur l'ampleur des mouvements sans avis de direction. Attention au vol crush après les événements.

</div>
