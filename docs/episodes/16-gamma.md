# 16. Gamma

## Pourquoi cet épisode

L'épisode Delta a laissé un fil ouvert, le Delta n'est pas fixe, il change en continu quand le prix bouge. Le Gamma mesure **à quelle vitesse** ce changement se produit. C'est un Greek de deuxième ordre.

## Définition et l'analogie qui débloque tout

- **Delta** = la vitesse à laquelle le prix de l'option bouge quand l'action bouge.
- **Gamma** = la vitesse à laquelle le **Delta lui-même** change quand l'action bouge.

Analogie voiture. Le prix de l'option = ta position. Le Delta = ta vitesse. Le Gamma = ton accélération (à quelle vitesse ta vitesse change). C'est une sensibilité de deuxième ordre, une dérivée de dérivée.

## Exemple chiffré

Action à 100€, call ATM, Delta 0,50, Gamma 0,05. Gamma de 0,05 veut dire, pour chaque 1€ de mouvement de l'action, le Delta change de 0,05.

- Action 100 → 101 : Delta 0,50 → 0,55
- Action 101 → 102 : Delta 0,55 → 0,60
- Action 102 → 103 : Delta 0,60 → 0,65

Le Delta s'accélère vers 1 quand l'action monte, le Gamma est le chiffre qui dit de combien il grimpe à chaque pas.

## Pourquoi le Gamma est maximal ATM (le fil du rasoir)

- **Deep ITM** (action 200, strike 100) : Delta ≈ 1, ne bouge presque pas quand l'action bouge → Gamma ≈ 0.
- **Deep OTM** (action 50, strike 100) : Delta ≈ 0, ne bouge presque pas → Gamma ≈ 0.
- **ATM** (action 100, strike 100) : Delta 0,5, l'option est sur le fil du rasoir entre finir nulle et finir rentable, un petit mouvement fait basculer le Delta violemment → **Gamma maximal**.

Le Gamma est le plus fort là où l'incertitude est la plus grande, autour du strike.

## Long gamma vs short gamma, le mécanisme

Règle simple, « long/short gamma » n'est pas un produit à acheter, c'est une conséquence du fait de posséder ou d'avoir vendu des options.

- **Acheter** une option (call OU put) → **long gamma**.
- **Vendre** une option (call OU put) → **short gamma**.

**Piège de vocabulaire.** « Long/short » ici ne parle PAS de parier à la hausse ou la baisse. Un acheteur de call ET un acheteur de put sont tous les deux long gamma. Ça parle de posséder de l'optionalité, pas de direction.

**Long gamma, la courbe joue pour toi.** Tu achètes un call, action à 100€, Delta 0,5.

- Action monte à 110€ → Delta grimpe à 0,7, tu gagnes plus vite par euro.
- Action baisse à 90€ → Delta tombe à 0,3, tu perds moins vite par euro.

Dans les deux sens, le changement de Delta t'avantage. C'est littéralement la **convexité** des obligations (épisode DV01).

**Short gamma, l'image miroir.** Le vendeur subit tout à l'envers, pertes qui accélèrent, gains qui ralentissent sur les gros mouvements. La prime encaissée est sa compensation pour accepter cette convexité négative.

## Le vrai enjeu pratique, le re-hedging (gamma scalping)

Le market maker vend des options et se couvre en achetant/vendant l'action pour rester delta-neutral. Mais le Delta change tout le temps (le Gamma), donc sa couverture ne tient jamais, il doit re-hedger en continu.

**Le piège du short gamma.** L'action monte → il doit acheter de l'action pour rééquilibrer (achat **haut**). L'action baisse → il doit vendre (vente **bas**). Il est condamné à « acheter haut, vendre bas » à chaque re-hedge, il **perd** sur cette danse, compensé par la prime encaissée.

L'acheteur (long gamma) fait l'inverse, « acheter bas, vendre haut », il **gagne** sur le re-hedging, qu'il paie via l'érosion du temps (le **Theta**, futur épisode).

## La dimension temps

Pour une option ATM, le Gamma **explose** à l'approche de l'expiration. À quelques heures de l'échéance, une option ATM est un quasi pile-ou-face qui va se résoudre très vite en 0 ou 1, le moindre mouvement fait basculer le Delta entre ~0 et ~1. Gamma énorme, très dangereux à gérer pour un vendeur.

## Le lien réel, le gamma squeeze (GameStop)

Dans le short squeeze de GameStop, il y avait une composante gamma. La foule achète massivement des calls, les market makers qui les vendent sont short gamma et doivent se couvrir en **achetant l'action**, ce qui fait monter le prix, ce qui augmente leur Delta (via le Gamma), ce qui les force à acheter encore plus. Boucle auto-alimentée, un **gamma squeeze**, qui a amplifié la flambée de 2021.

## À retenir

Le Gamma mesure la vitesse à laquelle le Delta change. Maximal ATM (fil du rasoir), proche de 0 aux extrêmes. Acheter une option = long gamma (convexité pour toi), vendre = short gamma (convexité contre toi, compensée par la prime). C'est le moteur du re-hedging permanent des market makers.
