# 23. The Strangle

## Pourquoi cet épisode

Cousin direct du straddle (épisode 22), la comparaison que tout le monde pose juste après.

## Définition

Même montage qu'un straddle : on achète un call et un put, même échéance. La différence, c'est que les deux strikes sont **différents**, et tous les deux **hors de la monnaie (OTM)**, un en dessous du prix actuel, un au-dessus.

## Pourquoi faire ça plutôt qu'un straddle

Des options OTM coûtent moins cher que des options ATM (rappel épisode Delta et moneyness). Donc le strangle coûte **moins cher à l'entrée** que le straddle.

## Exemple chiffré

Apple à 100.

| | Montage | Coût |
|---|---|---|
| **Straddle** | call 100 + put 100 | 8 |
| **Strangle** | call 110 (prime 2) + put 90 (prime 2) | 4 |

Moitié moins cher.

## Les breakevens, le vrai compromis

| | Breakeven haut | Breakeven bas |
|---|---|---|
| Straddle | 108 | 92 |
| Strangle | 114 | 86 |

Le strangle a payé moins, donc il faut un mouvement **plus gros** pour devenir rentable. Le straddle gagne dès qu'Apple dépasse 108 ou passe sous 92. Le strangle a besoin de 114 ou 86.

Calcul du strangle : breakeven haut = strike du call + coût total = 110 + 4 = 114. Breakeven bas = strike du put − coût total = 90 − 4 = 86.

## Les Greeks

Même profil que le straddle à l'ouverture : **delta neutral, long gamma, long vega, short theta**. La différence porte sur deux choses seulement :

- combien on paie pour cette exposition (moins cher)
- jusqu'où l'action doit aller avant que ça compte (plus loin)

## À retenir

Le vrai choix n'est pas straddle contre strangle dans l'absolu. C'est : quelle ampleur de mouvement on attend réellement, et vaut-il mieux payer plus cher au départ pour une barre de rentabilité plus basse (straddle), ou payer moins cher en ayant besoin d'un plus gros mouvement (strangle).
