# 14. Put-Call Parity

## Pourquoi cet épisode

L'épisode Options a traité call et put comme deux paris indépendants. Ils ne le sont pas, leurs prix sont liés par une relation mathématique stricte. C'est aussi LA question classique en entretien S&T sur les options.

## Rappel rapide

Un **call** = droit d'acheter à un prix fixé (le **strike**). Un **put** = droit de vendre à ce même prix fixé. Les deux coûtent une petite somme dès le départ, la **prime**.

## La formule, à retenir en premier

`Call − Put = Prix de l'action − Strike (actualisé)`

Tout le reste de la fiche n'est que l'intuition derrière cette équation.

## La construction, call acheté + put vendu, même strike/échéance

**Exemple.** Action à 100€ aujourd'hui, strike 100€ pour les deux, prime du call 5€, prime du put 4€. On achète le call, on vend le put simultanément.

**Scénario A, prix final 130€.**

- Call : exercice, gain de 30€, moins prime payée 5€ = **+25€**.
- Put vendu : n'est pas exercé (personne ne vend à 100€ un truc qui vaut 130€), on garde la prime = **+4€**.
- **Total = +29€**

**Scénario B, prix final 70€.**

- Call : expire sans valeur, perte de la prime = **−5€**.
- Put vendu : exercé contre nous, achat forcé à 100€ d'un titre qui vaut 70€, perte de 30€, compensée par la prime encaissée de 4€ = **−26€**.
- **Total = −31€**

## La comparaison avec détenir l'action directement

Action achetée directement à 100€ : de 100 à 130€, gain de **+30€**. De 100 à 70€, perte de **−30€**.

Dans les deux scénarios, la position combinée (call + put vendu) bouge **quasiment euro pour euro** avec l'action, décalée d'un montant fixe constant de **1€** (= 5€ de prime payée − 4€ de prime encaissée, le coût net de la structure).

## Ce que « même exposition » veut vraiment dire

Pas « même résultat final au centime près », mais **même sensibilité au mouvement du prix** (la pente, 1 pour 1). Un mouvement de 30€ sur l'action produit un mouvement de 30€ sur la position synthétique dans les deux sens (29€ quand ça monte de 30, 31€ de perte quand ça baisse de 30, même écart de 1€ dans les deux cas). Ce 1€ est un coût fixe **connu à l'avance**, qui ne dépend jamais de ce que fait le prix ensuite, comme des frais d'ouverture sur un compte dont le taux d'intérêt reste identique.

## Position synthétique et effet de levier

Acheter l'action directement immobilise 100€ de cash. La position synthétique (call + put vendu) ne coûte net que 1€ (plus une marge sur le put vendu, bien inférieure à 100€). Pour la **même exposition**, un capital immobilisé minuscule, un effet de levier énorme.

## Pourquoi construire cette position plutôt que juste détenir l'action

Deux vraies raisons.

1. **Le levier.** Déjà vu, la synthétique n'immobilise que le petit coût net des primes au lieu du prix plein de l'action, même exposition pour bien moins de capital.
2. **Éviter d'emprunter le titre physique.** On peut inverser la construction (vendre le call, acheter le put) pour créer un **short synthétique**, qui parie sur une baisse **sans jamais emprunter l'action**. Ça compte énormément quand le titre est cher ou difficile à emprunter, exactement le problème des titres « hard to borrow » vu dans l'épisode short selling.

## La formule

`Call − Put = Prix de l'action − Strike (actualisé)`

## Pourquoi cette relation tient toujours, l'arbitrage

Si le coût de la position synthétique s'écartait significativement du coût réel de détenir l'action, des arbitrageurs achèteraient immédiatement le côté le moins cher et vendraient l'autre, empochant un profit **sans risque**. Cette pression d'arbitrage permanente, exactement le même mécanisme que le CDS-bond basis (épisode 6), maintient le call, le put et l'action cohérents entre eux. La parité n'est pas juste une formule, c'est le résultat direct de cette pression d'arbitrage.

## À retenir

Call acheté + put vendu (même strike/échéance) = position synthétique identique à détenir l'action, à un coût fixe près. L'arbitrage garantit que cette équivalence reste toujours vraie, sinon un profit sans risque existerait.
