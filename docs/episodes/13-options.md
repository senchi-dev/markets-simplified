# 13. Options (Calls & Puts)

## Pourquoi cet épisode

Le short selling a un vrai problème, la perte illimitée. Les options existent en partie pour résoudre ce problème, parier sur un mouvement de prix avec un risque limité (côté acheteur).

## Définition

Une option est un **droit, pas une obligation**, d'acheter ou de vendre un actif à un prix fixé dès aujourd'hui, appelé le **strike** (prix d'exercice), avant une date donnée appelée l'**expiration**. Pour obtenir ce droit, on paie une petite somme dès le départ, appelée la **prime**. Si ça ne vaut jamais le coup de l'utiliser, on abandonne simplement, en perdant uniquement cette prime, rien de plus.

- **Call** = droit d'**acheter** à un prix fixé.
- **Put** = droit de **vendre** à un prix fixé.

## Les 4 positions possibles

Chaque option a un acheteur et un vendeur (« writer »), donc 4 positions, pas 2.

- **Long call.** Acheter le droit d'acheter. Pari à la hausse.
- **Short call.** Vendre ce droit. Pari que le prix reste bas ou baisse.
- **Long put.** Acheter le droit de vendre. Pari à la baisse.
- **Short put.** Vendre ce droit. Pari que le prix reste haut ou monte.

## Exemple chiffré, long call

Action à 100€, call strike 110€, prime 5€, échéance 3 mois.

- Prix final 130€ : exercice, achat à 110€, revente possible à 130€, profit brut 20€, moins prime 5€ = **15€ net**.
- Prix final 95€ : pas d'intérêt à exercer, option expire sans valeur, perte limitée à la prime = **5€**.

## L'asymétrie fondamentale, où le risque se déplace

**L'acheteur** (long call ou long put) a toujours une perte **plafonnée à la prime**. Mais le gain diffère selon le type :

- **Long call** : gain **illimité** (le prix d'une action peut monter sans limite).
- **Long put** : gain **plafonné lui aussi**, pas illimité, car le prix ne peut jamais descendre sous 0. Gain max = strike − prime, grand mais borné.

**Le vendeur (writer)** a toujours un gain **plafonné à la prime encaissée**, mais un risque bien plus grand :

- **Short call.** Si le prix monte, obligation de vendre au strike alors que le prix de marché est bien plus haut. Si pas déjà propriétaire du sous-jacent (« naked call »), il faut racheter au prix de marché pour livrer, perte **théoriquement illimitée** (exactement comme le short selling classique). Version moins risquée, le **covered call** (on possède déjà le sous-jacent, donc pas de rachat forcé, juste perte de l'upside au-delà du strike).
- **Short put.** Si le prix baisse, obligation d'acheter au strike alors que le prix de marché est bien plus bas. Perte techniquement **plafonnée** (le prix ne peut pas descendre sous 0, perte max = strike − prime), mais reste très grande comparée à la prime encaissée.

## Exemples chiffrés des positions vendeuses

**Short call**, strike 110€, prime encaissée 5€. Prix explose à 300€, rachat obligatoire à 300€ pour livrer à 110€, perte de 190€ moins prime = **185€ de perte nette**.

**Short put**, strike 90€, prime encaissée 4€. Prix s'effondre à 20€, achat obligatoire à 90€ d'un titre qui vaut 20€, perte de 70€ moins prime = **66€ de perte nette**. Pire cas absolu (prix à 0), perte max = 90 − 4 = **86€**, plafonnée mais énorme.

## Pourquoi vendre une option volontairement, deux vraies stratégies

- **Vendre un put** : utile si on veut vraiment acheter l'action mais à un prix plus bas. Équivaut à être payé pour attendre. Si le prix descend jusqu'au strike, on achète au prix voulu. Sinon, on garde la prime sans rien acheter.
- **Covered call** : si on détient déjà l'action et qu'on pense qu'elle ne montera pas beaucoup, génère un revenu régulier supplémentaire.

## Le parallèle exact avec le CDS

Même structure que le CDS (épisode 6). L'acheteur de protection paie une petite prime, perte plafonnée, gros gain potentiel si l'événement arrive. Le vendeur de protection encaisse la prime, gain plafonné, perte potentiellement énorme si l'événement arrive. Acheter/vendre une option suit exactement cette même asymétrie.

## Moneyness, trois états

- **In the money (ITM)** : exercer maintenant serait profitable.
- **At the money (ATM)** : strike ≈ prix actuel.
- **Out of the money (OTM)** : exercer maintenant ferait perdre de l'argent, personne n'exerce.

## Ce qui compose la prime

`Prime = valeur intrinsèque (gain si exercée maintenant, souvent 0 si OTM) + valeur temps (extrinsic value, la chance que ça devienne rentable avant l'échéance)`

Le facteur le plus important derrière la valeur temps est la **volatilité**. Plus le sous-jacent est volatil, plus les options dessus sont chères (calls ET puts), car plus de chances d'un gros mouvement favorable d'ici l'expiration. Les traders d'options « tradent la volatilité » autant que la direction du prix.

## Bonus, Put-Call Parity et la position synthétique (pour approfondir plus tard)

Relation d'arbitrage classique, `Call − Put = Prix de l'action − Strike (actualisé)`. Acheter un call et vendre un put de même strike/échéance recrée exactement l'exposition d'être long l'action (même sensibilité euro pour euro au prix, à un coût fixe près lié au différentiel de primes). Utile pour un effet de levier massif (immobiliser 1€ de coût net au lieu de 100€ pour la même exposition), et c'est cette équivalence, maintenue par l'arbitrage, qui garde les prix du call, du put et de l'action cohérents entre eux.

## À retenir

Une option déplace le risque illimité du short selling vers le vendeur de l'option, en échange d'une prime. L'acheteur a toujours une perte plafonnée, le vendeur porte le vrai risque, exactement la même logique acheteur/vendeur que le CDS.
