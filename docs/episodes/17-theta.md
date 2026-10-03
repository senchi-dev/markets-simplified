<p class="ms-kicker">Épisode 17</p>

# <span class="ms-outline">Theta.</span>

## Pourquoi cet épisode

Delta et Gamma concernaient le mouvement de l'action. Theta est différent, c'est ce qui arrive à l'option quand **rien ne bouge**.

## Définition

Le Theta mesure combien l'option perd de valeur **chaque jour qui passe**, en supposant que l'action reste au même prix et que la volatilité ne change pas. C'est le seul Greek qui bouge dans une direction **certaine**, le prix de l'action peut monter ou baisser (inconnu), mais le temps n'avance que dans un sens.

## Exemple chiffré

Call acheté à 5€, Theta = -0,07. Demain, si l'action n'a pas bougé, l'option vaut ~4,93€. Le surlendemain, ~4,86€. Perte d'argent en ne faisant rien, juste parce qu'un jour est passé.

## Pourquoi la valeur baisse mécaniquement

Quand on achète une option, on paie en partie pour la **chance que le prix bouge en sa faveur avant l'échéance**. Chaque jour qui passe, il reste moins de temps pour que ça arrive, donc cette chance vaut moins. On achète du temps, et la fenêtre rétrécit en permanence. C'est la partie **valeur temps** de la prime (extrinsic value) qui fond, pas la valeur intrinsèque.

**Ne pas confondre** avec la « valeur temps de l'argent » (actualisation, taux d'intérêt), aucun rapport. Ici c'est une question de probabilité et de temps restant.

**Comment on « paie ».** Aucun prélèvement, la perte est dans le **mark-to-market** (la valeur de revente de l'option baisse). Elle devient définitive si on revend au prix plus bas, ou si l'option expire sans valeur.

## Acheteur vs vendeur

- **Acheteur** : Theta **négatif**, le temps est son ennemi, sa position fond chaque jour.
- **Vendeur** : Theta **positif**, le temps est son ami, il encaisse cette érosion. C'est pour ça qu'un vendeur d'options gagne de l'argent dans un marché calme où rien ne bouge.

## Le deal gamma contre theta (le point central)

Rappel, être long gamma est confortable (convexité pour toi dans les deux sens), mais rien n'est gratuit. Le theta est le prix de ce confort.

`Long gamma = convexité pour toi, mais theta négatif (loyer quotidien payé)`

`Short gamma = convexité contre toi, mais theta positif (loyer quotidien encaissé)`

Les deux vont toujours ensemble, dans des sens opposés. Impossible d'avoir le gamma sans payer le theta, ou d'encaisser le theta sans subir le gamma. C'est le compromis fondamental de toute position d'options.

## Où le Theta frappe le plus fort

Maximal pour les options **ATM** (là où la valeur temps est la plus grosse, le fil du rasoir). Faible pour une option **deep ITM** (sa valeur est presque toute intrinsèque, peu de valeur temps à éroder). Même endroit que le Gamma maximal (ATM), normal, ce sont les deux faces de la même pièce.

## L'érosion n'est pas linéaire

Elle **s'accélère** à l'approche de l'échéance, surtout pour une ATM. Les derniers jours de vie d'une option ATM sont brutaux, la valeur temps s'effondre.

<div class="ms-takeaway" markdown>

## À retenir

Theta = érosion quotidienne de la valeur temps de l'option. Négatif pour l'acheteur, positif pour le vendeur. Maximal ATM, s'accélère près de l'échéance. Toujours le miroir du gamma, le prix à payer pour la convexité.

</div>
