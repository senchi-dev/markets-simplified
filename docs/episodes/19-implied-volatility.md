<p class="ms-kicker">Épisode 19</p>

# Implied <span class="ms-outline">Volatility.</span>

## Pourquoi cet épisode

Le Vega mesurait la sensibilité à la volatilité. Mais quelle volatilité ? La volatilité implicite, celle que le marché anticipe, intégrée dans le prix des options. C'est ce que les traders d'options échangent réellement. (Note, on saute le **Rho**, sensibilité aux taux, le Greek le moins important, quasi ignoré sur les desks actions.)

## Définition (confirmée CFA)

Un **modèle**, c'est juste une formule qui prend plusieurs éléments connus, fait le calcul, et recrache un seul nombre (ici, le prix juste de l'option). Le modèle standard s'appelle **Black-Scholes** (ou Black-Scholes-Merton, 1973).

Le prix d'une option sort donc de ce modèle, qui prend en entrée le prix de l'action, le strike, le temps restant, les taux, et la **volatilité**. Tous ces inputs sont connus **sauf la volatilité future**.

*(Nuance : Black-Scholes pur suppose une vol unique et constante, faux en pratique, d'où le volatility skew (épisode 21) et des modèles plus avancés comme Heston, Dupire, SABR.)*

La volatilité implicite s'obtient en faisant tourner le modèle **à l'envers** : on observe le prix de marché réel de l'option, et on cherche quelle volatilité il faudrait mettre dans le modèle pour retomber sur ce prix. La vol est la seule inconnue (le reste est observable).

`Prix observé sur le marché → modèle inversé → quelle volatilité explique ce prix ? = volatilité implicite`

## Ce que ça représente

L'anticipation du marché sur l'ampleur des mouvements futurs, telle qu'intégrée dans le prix des options maintenant. IV haute = options chères, le marché anticipe un gros mouvement. IV basse = options bon marché, le marché anticipe le calme.

**Nuance rigoureuse.** L'IV est une mesure **risque-neutre**, pas une pure prévision. Ce n'est pas exactement « ce que le marché pense que la vol sera ».

## L'IV tourne quasi toujours plus haut que la réalisée (variance risk premium)

Point qui fait la différence entre réciter et comprendre. L'IV **surestime systématiquement** les mouvements réels. C'est le **variance risk premium (VRP)**. Les gens paient une prime pour la protection (institutions qui achètent des puts) et pour le risque de saut brutal, donc le prix des options porte une prime au-dessus du mouvement réellement attendu.

Chiffres au 12 mars 2026 sur le SPY : IV 30 jours à **25,74%** vs volatilité réalisée à **16,68%**, écart ~9 points. Positif ~79% du temps. Vendre cet écart est une stratégie à part entière. \[source SharpeTwo\]

## Distinction implicite vs réalisée

- **Implicite** : la vol que le marché *anticipe*, extraite du prix des options aujourd'hui. C'est ce à quoi le Vega réagit.
- **Réalisée** : la vol qui s'est *effectivement* produite, mesurée a posteriori sur les mouvements passés.

## Cotation en vol (convention desk/dealer, PAS retail)

Sur un desk / entre dealers, les options ne sont pas cotées en euros mais en **vol**. Un dealer dit « je t'achète à 18 de vol », pas « à 5 euros ». Le prix en euros n'est que l'output calculé après avoir mis cette vol dans le modèle. Ce qui se négocie vraiment, c'est la volatilité.

**À cadrer.** C'est la convention du monde OTC / institutionnel. Le retail, lui, voit des primes en dollars sur son broker (avec l'IV affichée à côté). Ne PAS dire « le prix en € n'existe pas » (faux, il se règle en cash), dire « ils raisonnent en vol ».

## Pourquoi c'est central

C'est la vraie monnaie d'échange des options. Un trader compare l'IV cotée à sa propre prévision de vol pour repérer les options mal priceées (IV > sa prévision = option chère à vendre, IV < sa prévision = option bon marché à acheter).

<div class="ms-takeaway" markdown>

## À retenir

Volatilité implicite = la vol extraite du prix de marché en inversant le modèle. C'est l'anticipation (risque-neutre) du marché sur les mouvements futurs, elle tourne quasi toujours plus haut que la réalisée (variance risk premium), et c'est en vol, pas en prix, que les desks négocient réellement les options.

</div>
