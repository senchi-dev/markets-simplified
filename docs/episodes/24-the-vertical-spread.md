<p class="ms-kicker">Épisode 24</p>

# The Vertical <span class="ms-outline">Spread.</span>

## Pourquoi cet épisode

Straddle et strangle sont des paris sans direction, sur l'ampleur du mouvement. Le vertical spread est l'inverse : un pari **directionnel**, construit pour coûter moins cher et risquer moins qu'un call ou un put acheté seul.

## Définition

Même échéance, même type d'option (deux calls ou deux puts), deux strikes différents. On en **achète** un et on en **vend** un autre. La prime encaissée sur l'option vendue réduit le coût, mais le gain maximum devient plafonné.

## Les quatre versions

| | Calls | Puts |
|---|---|---|
| **Haussier (bull)** | Bull call spread (on paie au départ) | Bull put spread (on encaisse au départ) |
| **Baissier (bear)** | Bear call spread (on encaisse au départ) | Bear put spread (on paie au départ) |

« Bull » ou « bear » = la direction pariée. Payer ou encaisser au départ = le sens du cash à l'ouverture. Payer au départ s'appelle un **debit spread**, encaisser un **credit spread**.

## Bull call spread, pas à pas

Apple à 100. On achète le call 100 pour 5, on vend le call 110 pour 2.

- Coût net : 5 − 2 = **3**
- Perte max : **3** (tout le coût)
- Gain max : écart entre les strikes (10) − coût (3) = **7**
- Breakeven : 100 + 3 = **103**

À l'échéance :

| Apple finit à | Call 100 acheté | Call 110 vendu | Net après le coût de 3 |
|---|---|---|---|
| 95 | 0 | 0 | **−3** |
| 103 | 3 | 0 | **0** |
| 110 | 10 | 0 | **+7** |
| 130 | 30 | −20 | **+7** |

Au-dessus de 110, le call vendu perd exactement ce que le call acheté gagne sur chaque euro supplémentaire. Le gain arrête de grandir à 7. C'est le prix de l'entrée moins chère.

## Pourquoi le call vendu n'a pas de risque illimité ici

Épisode Options : un call vendu seul (« naked ») a une perte illimitée, car on peut devoir acheter l'action au prix de marché pour la livrer. Ici il n'est pas nu. On possède aussi le call 100, qui donne le droit d'acheter à 100. Si Apple monte à 300 et qu'on doit vendre à 110, le call 100 permet d'acheter à 100 pour livrer. La perte sur la jambe vendue est couverte par le gain sur la jambe achetée. D'où une perte max limitée aux 3 payés.

## Comparaison avec le call 100 acheté seul

| | Call 100 seul | Bull call spread |
|---|---|---|
| Coût | 5 | 3 |
| Perte max | 5 | 3 |
| Gain max | illimité | 7 |
| Breakeven | 105 | 103 |

Moins cher, moins de risque, rentable plus tôt. En échange, on abandonne tout le gain au-dessus de 110. Si on attend une hausse modérée (vers 110), le spread est le meilleur choix. Si on attend un très gros mouvement, le call seul est meilleur.

## Les Greeks

L'option vendue compense une partie de l'option achetée, donc tout est atténué (chiffres illustratifs) :

| | Call 100 acheté | Call 110 vendu | Net |
|---|---|---|---|
| Delta | +0,50 | −0,30 | **+0,20** |
| Theta (par jour) | −0,07 | +0,05 | **−0,02** |
| Vega | +0,20 | −0,15 | **+0,05** |

- **Delta plus petit** : moins exposé à la direction qu'un call seul.
- **Theta proche de zéro** : le temps fait beaucoup moins mal qu'à un call seul.
- **Vega faible** : un vol crush fait beaucoup moins mal, une bonne réponse au piège vu dans l'épisode Straddle.

## Les credit spreads, l'image miroir

**Bull put spread** : on vend le put 100 pour 5, on achète le put 90 pour 2, on **encaisse 3** au départ.

- Gain max : les **3** encaissés (si Apple reste au-dessus de 100)
- Perte max : écart (10) − crédit (3) = **7** (si Apple passe sous 90)
- Breakeven : 100 − 3 = **97**

On est payé d'abord, et on prend un risque plafonné si on a tort.

**Bear put spread** (le pendant baissier en debit) : acheter le put 100, vendre le put 90. Gagne si l'action baisse, gain plafonné sous 90.

<div class="ms-takeaway" markdown>

## À retenir

Vertical spread = acheter une option et en vendre une autre de même type, même échéance, strike différent. Moins cher et moins risqué qu'une option seule, gain plafonné. Greeks atténués (delta, theta, vega plus petits). Debit spread si on paie au départ, credit spread si on encaisse.

</div>
