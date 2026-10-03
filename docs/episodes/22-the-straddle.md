# 22. The Straddle

## Pourquoi cet épisode

La stratégie qui rassemble tous les Greeks d'un coup (delta, gamma, vega, theta). Rend concret tout l'arc options.

## Définition

Acheter **un call ET un put**, même strike, même échéance. On paie les deux primes. Pari sur un **gros mouvement**, peu importe la direction. Si ça bouge assez fort dans un sens ou l'autre, un des deux côtés rapporte gros.

## Exemple chiffré

Apple à 100€. Call strike 100 (prime 4€) + put strike 100 (prime 4€). Coût total = **8€**.

- Apple à 120 : call vaut 20, put 0 → 20 − 8 = **+12€**
- Apple à 80 : put vaut 20, call 0 → 20 − 8 = **+12€**
- Apple à 100 (pile au strike) : les deux à 0 → **−8€** (perte max)
- Apple à 105 : call vaut 5, put 0 → 5 − 8 = **−3€** (a bougé mais pas assez)

## Breakevens

On ne gagne que si le mouvement dépasse le coût total (8€). Breakeven haut = 100 + 8 = **108€**. Breakeven bas = 100 − 8 = **92€**. Entre les deux, perte. Ce n'est pas « je parie que ça bouge », c'est « je parie que ça bouge de plus de 8€ ».

## Les Greeks, tous d'un coup

- **Delta neutral (au départ).** Call +0,5, put −0,5, s'annulent → aucun pari sur la direction. **Nuance** : vrai seulement à l'ouverture. Dès que ça bouge, le gamma fait pencher le delta dans le sens du mouvement (ex. Apple à 110 → delta call +0,8, put −0,2, total +0,6, net long).
- **Long gamma.** On adore les gros mouvements, dans les deux sens, les gains accélèrent quand ça part.
- **Long vega.** Si la volatilité implicite monte, les deux options prennent de la valeur, même avant que l'action bouge.
- **Short theta (theta négatif).** Chaque jour calme coûte cher, on paie l'érosion sur DEUX options à la fois.

## Le piège, le vol crush

Un straddle est le plus tentant **avant un événement** (résultats, élection), quand on attend un gros mouvement. Mais c'est là que la vol implicite est **gonflée**, donc les deux primes sont chères. Le mouvement réel doit dépasser ce qui est **déjà price**. Après l'événement, le vol crush fait chuter la valeur (le long vega souffre). On peut voir l'action bouger comme prévu et perdre quand même si le mouvement est plus petit que ce qui était anticipé.

## Le vendeur (short straddle)

L'inverse exact : encaisse les deux primes, veut que l'action reste immobile. Short gamma, short vega, theta positif. Très dangereux, perd si ça bouge fort dans n'importe quel sens.

## À retenir

Straddle long = call + put même strike. Delta neutral (au départ), long gamma, long vega, short theta. Pari pur sur l'ampleur du mouvement, pas la direction. Gagne si gros mouvement OU hausse de vol, perd si l'action stagne. Attention au vol crush après les événements.
