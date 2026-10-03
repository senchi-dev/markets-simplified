<p class="ms-kicker">Épisode 15</p>

# <span class="ms-outline">Delta.</span>

## Pourquoi cet épisode

Put-Call Parity a montré que call acheté + put vendu bouge euro pour euro avec l'action. Ce chiffre précis, combien une option bouge par euro de mouvement du sous-jacent, a un nom, le **Delta**. C'est le premier des « Greeks » (les sensibilités de prix d'une option).

## Définition, la vraie mécanique

Le Delta mesure de **combien le prix d'une option bouge pour un mouvement de 1€** du sous-jacent. C'est une sensibilité de prix, pas une probabilité (la nuance compte, voir plus bas).

- **Call** : Delta entre **0 et 1**.
- **Put** : Delta entre **-1 et 0**, négatif car un put gagne de la valeur quand l'action **baisse**, pas monte.

## Pourquoi un Deep ITM bouge euro pour euro, le vrai mécanisme

Rappel de l'épisode Options, la prime = valeur intrinsèque + valeur temps, avec `valeur intrinsèque = Prix de l'action − Strike` (pour un call, si positif).

Le strike est **fixe**, il ne bouge jamais. Donc si le prix de l'action bouge de 1€, et que l'option est assez profondément ITM pour être quasi certaine d'être exercée, sa valeur intrinsèque bouge d'exactement ce même 1€ (on soustrait un nombre fixe d'un nombre qui bouge). C'est ça, la vraie raison mécanique pour laquelle un call deep ITM suit l'action quasi 1 pour 1, une question de **sensibilité de prix**, pas de calcul de probabilité.

**Deep OTM**, l'inverse. Presque aucune valeur intrinsèque, le prix est presque entièrement de la valeur temps (une petite chance de gros mouvement avant l'échéance). Un mouvement de 1€ de l'action change à peine cette petite chance, donc l'option bouge à peine.

## La probabilité, un raccourci utile, pas la vraie définition

Beaucoup de traders utilisent le Delta comme une **approximation grossière** de la probabilité que l'option finisse rentable (Delta 0,3 ≈ 30% de chances environ). C'est un raccourci mental pratique parce que les chiffres se ressemblent souvent, mais ce n'est **pas** ce que le Delta mesure fondamentalement. Le Delta est une sensibilité de prix, la probabilité n'est qu'un modèle mental approximatif construit par-dessus.

## Rappel corrigé, la moneyness dépend du type d'option

|  | In the money (ITM) | At the money (ATM) | Out of the money (OTM) |
| --- | --- | --- | --- |
| **Call** | Prix actuel **> strike** | Prix actuel ≈ strike | Prix actuel **< strike** |
| **Put** | Prix actuel **< strike** | Prix actuel ≈ strike | Prix actuel **> strike** |

**Pourquoi c'est inversé entre call et put.** Un call ITM veut dire qu'on peut acheter **en dessous** du prix du marché, donc le prix du marché doit être **au-dessus** du strike. Un put ITM veut dire qu'on peut vendre **au-dessus** du prix du marché, donc le prix du marché doit être **en dessous** du strike. Inversé parce que call et put donnent des droits opposés.

## Le Delta selon la moneyness

- **Deep ITM** : Delta proche de **1** (call) ou **-1** (put).
- **Deep OTM** : Delta proche de **0**.
- **At the money** : Delta autour de **0,5** (call) ou **-0,5** (put).

**Une échelle continue, pas des paliers fixes.** Le Delta évolue progressivement entre ces valeurs, pas par sauts. Une option seulement légèrement OTM garde une vraie sensibilité, son Delta peut être 0,3 ou 0,4, pas proche de 0. Seul un OTM **profond** (très loin du strike) a un Delta proche de 0.

**Piège à éviter.** OTM ne veut PAS dire « bouge dans la mauvaise direction », ça veut dire « bouge très peu, dans n'importe quelle direction » (voir le mécanisme de la valeur intrinsèque ci-dessus).

## Le Delta n'est PAS fixe, il change en continu (point clé souvent mal compris)

Le Delta que tu vois au moment d'acheter l'option n'est qu'une **photo à cet instant précis**, pas une valeur gravée pour toute la durée de vie de l'option. Il se recalcule en permanence, parce que la probabilité de finir rentable change à chaque mouvement du prix.

**Exemple.** Call acheté ATM, action à 100€, strike 100€, Delta = 0,5 à l'achat.

- Action monte à 120€ : option maintenant clairement ITM, Delta **remonte** vers 0,8-0,9.
- Action retombe à 80€ : option maintenant OTM, Delta **redescend** vers 0,1-0,2.

Le Greek qui mesure à quelle vitesse le Delta lui-même change s'appelle le **Gamma**, un bon sujet pour un futur épisode.


## Le lien direct avec Put-Call Parity

Call acheté + put vendu (même strike) = Delta de **1**, identique à détenir l'action directement, juste construit à partir de deux options. C'est littéralement la même chose que la position synthétique de l'épisode précédent, dite avec le bon mot.

## L'usage pratique, le hedging

Un trader qui vend des options se retrouve avec une exposition Delta à l'action, et peut la compenser en achetant ou vendant le bon nombre d'actions réelles pour ramener le Delta total à zéro (être « delta neutral »). Les market makers (rappel épisode IRS) font ça en continu, ils ne parient pas sur la direction, ils gèrent leur Delta toute la journée pour rester neutres tout en captant leur spread.

## Le raccourci utile, Delta comme proba approximative

Le Delta est souvent utilisé comme une **approximation grossière** de la probabilité que l'option finisse dans la monnaie. Un Delta de 0,3 suggère très approximativement environ 30% de chances, pas exact, mais un raccourci réellement utilisé par les traders.

<div class="ms-takeaway" markdown>

## À retenir

Le Delta mesure la sensibilité d'une option au prix du sous-jacent, de 0 à 1 pour un call, de -1 à 0 pour un put. Deep ITM se comporte comme l'action, deep OTM bouge à peine dans les deux sens, et c'est l'outil central du hedging pour les market makers.

</div>
