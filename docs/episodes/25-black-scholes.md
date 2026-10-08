<p class="ms-kicker">Épisode 25</p>

# Black-<span class="ms-outline">Scholes.</span>

## Pourquoi cet épisode

Black-Scholes revient dans presque tous les épisodes options. Le [delta](15-delta.md) vient de là, la [vol implicite](19-implied-volatility.md) s'obtient en l'inversant, et le [skew](21-the-volatility-skew.md) existe parce qu'une de ses hypothèses est fausse. On ne l'avait jamais ouvert. Cet épisode ferme l'arc options en expliquant le modèle lui-même, d'où il vient, comment on calcule un prix à la main, et pourquoi les desks l'utilisent encore alors que tout le monde sait qu'il est faux.

## C'est quoi un modèle

Un modèle, c'est une version simplifiée de la réalité écrite sous forme de formule. On lui donne des inputs, il sort un nombre. Il fait des hypothèses pour rendre le calcul possible, et ces hypothèses ne sont jamais parfaitement vraies. Un bon modèle n'est pas un modèle exact. C'est un modèle dont on connaît les erreurs.

Black-Scholes prend 5 inputs et sort le prix "juste" d'une option européenne (exerçable seulement à l'échéance).

## Le problème avant 1973

Avant Black-Scholes, pour pricer un call il fallait deviner deux choses. Où le cours allait finir, et quel taux utiliser pour actualiser un gain risqué. Chacun avait sa propre estimation du rendement de l'action et sa propre aversion au risque, donc chacun avait son propre prix. Il n'y avait pas de prix de référence.

L'apport de Black, Scholes et Merton, c'est de montrer qu'on n'a besoin ni du rendement espéré ni de l'aversion au risque. Le prix sort d'un argument d'arbitrage, comme la [put-call parity](14-put-call-parity.md).

## Les 5 inputs

| Input | Symbole | Ce que c'est | Où on le trouve |
|---|---|---|---|
| Prix du sous-jacent | `S` | Le cours de l'action aujourd'hui | À l'écran |
| Strike | `K` | Le prix d'exercice fixé dans le contrat | Dans le contrat |
| Maturité | `T` | Le temps restant avant l'échéance, **en années** (6 mois = 0,5) | Dans le contrat |
| Taux sans risque | `r` | Ce que rapporte un prêt sans risque (taux d'État), en taux continu | À l'écran |
| Volatilité | `σ` (sigma) | L'amplitude des mouvements du cours, en % par an | **Personne ne la connaît** |

Quatre inputs sur cinq sont observables. Le seul qu'il faut estimer, c'est la volatilité. C'est pour ça que tout le marché des options tourne autour de la vol, et que les traders cotent en vol plutôt qu'en euros.

Ce qui n'est **pas** dans la liste compte autant. Il n'y a pas le rendement espéré de l'action, ni l'avis du trader sur la direction.

## L'idée centrale, copier l'option

On peut fabriquer une copie exacte d'une option avec seulement deux ingrédients, des actions et du cash (emprunté ou placé). Si la copie paie exactement la même chose que l'option dans tous les scénarios, les deux doivent coûter la même chose. Sinon on achète le moins cher, on vend le plus cher, et on encaisse un profit sans risque. C'est la loi du prix unique.

### Version simple à une période

Pour voir le mécanisme, on simplifie à l'extrême. Action à 100 €, dans un an elle vaut soit 120 €, soit 80 €. Taux à 0 %. Call de strike 100 €.

- Si l'action monte à 120 €, le call paie 20 €.
- Si elle descend à 80 €, le call paie 0 €.

On cherche combien d'actions détenir pour reproduire ça. L'écart de payoff du call est de 20 €, l'écart de prix de l'action est de 40 €. Il faut donc 20 / 40 = **0,5 action**. Ce 0,5, c'est le [delta](15-delta.md).

- 0,5 action vaut 60 € si l'action monte, 40 € si elle baisse.
- On emprunte 40 € aujourd'hui (à rembourser 40 € puisque le taux est nul).
- Dans le scénario haut, 60 − 40 = 20 €. Dans le scénario bas, 40 − 40 = 0 €.

La copie paie exactement comme le call. Elle coûte aujourd'hui 0,5 × 100 − 40 = **10 €**. Donc le call vaut 10 €.

On n'a jamais utilisé la probabilité que l'action monte. Que tu penses qu'elle a 90 % de chances de monter ou 10 %, le call vaut 10 €. Si quelqu'un le vend 12 €, tu le vends aussi, tu achètes la copie à 10 €, et tu gardes 2 € quoi qu'il arrive.

### Passage au vrai modèle

Dans la réalité le cours ne prend pas deux valeurs, il bouge en continu. Black-Scholes fait la même chose en découpant le temps en intervalles infiniment petits. À chaque instant on ajuste le nombre d'actions détenues (c'est le **delta hedging**), et la copie suit l'option en permanence. La formule est le résultat de ce raisonnement poussé à la limite.

## Pourquoi le rendement espéré disparaît

Comme le prix vient d'une copie, il est le même pour un investisseur optimiste, pessimiste, prudent ou joueur. On peut donc faire le calcul dans un monde imaginaire où tout le monde est neutre au risque, où toutes les actions rapportent en moyenne le taux sans risque `r`. C'est ce qu'on appelle le **pricing risque-neutre**. Ce n'est pas une hypothèse sur la vraie vie. C'est un raccourci de calcul qui donne le bon prix parce que l'argument de copie le garantit.

Conséquence pratique, les probabilités qui sortent de Black-Scholes (comme `N(d2)`) sont des probabilités dans ce monde risque-neutre, pas des vraies probabilités. Sur un desk on dit "probabilité risque-neutre".

## La formule

Pour un call européen sur une action sans dividende :

```text
C = S × N(d1) − K × e^(−rT) × N(d2)

d1 = [ ln(S / K) + (r + σ² / 2) × T ] / ( σ × √T )
d2 = d1 − σ × √T
```

Pour un put européen :

```text
P = K × e^(−rT) × N(−d2) − S × N(−d1)
```

### Chaque symbole

- **C** et **P**, le prix du call et du put.
- **e**, une constante mathématique qui vaut environ 2,718.
- **e^(−rT)**, le **facteur d'actualisation**. Il transforme une somme payée à l'échéance en sa valeur d'aujourd'hui. À r = 4 % et T = 1 an, il vaut 0,9608. 100 € dans un an valent donc 96,08 € aujourd'hui.
- **ln**, le logarithme népérien. `ln(S / K)` mesure l'écart entre le cours et le strike en pourcentage (continu). ln(1) = 0, donc à la monnaie (S = K) ce terme vaut zéro. ln(110 / 100) ≈ 0,095, soit environ +9,5 %.
- **√T**, la racine carrée de la maturité. La vol grandit avec la racine du temps, pas avec le temps. Sur 4 ans le cours bouge environ 2 fois plus que sur 1 an, pas 4 fois plus.
- **σ × √T**, la volatilité totale sur toute la durée de vie de l'option.
- **N(x)**, une probabilité entre 0 et 1, expliquée juste en dessous.

### N(x) et la courbe en cloche

Imagine une courbe en cloche (la loi normale). La plupart des valeurs sont proches de 0, les valeurs extrêmes sont rares. N(x), c'est la part de la cloche qui se trouve à gauche de x.

| x | N(x) | Lecture |
|---|---|---|
| −2 | 0,023 | Presque rien à gauche |
| −1 | 0,159 | |
| 0 | 0,500 | Exactement la moitié |
| 0,1 | 0,540 | |
| 0,3 | 0,618 | |
| 1 | 0,841 | |
| 2 | 0,977 | Presque tout à gauche |

Propriété utile, N(−x) = 1 − N(x). La cloche est symétrique.

Black-Scholes suppose que le **logarithme** du prix suit cette loi normale, donc que le prix lui-même suit une loi **log-normale**. En clair, le prix ne peut pas devenir négatif, et une hausse de +50 % est à peu près aussi probable qu'une baisse de −33 % (les deux sont le même écart en log).

### d1 et d2

d1 et d2 mesurent à quel point l'option est dans ou en dehors de la monnaie, en nombre d'écarts-types (de "vols totales"). Plus ils sont grands, plus l'option est dans la monnaie.

- **N(d2)** = la probabilité (risque-neutre) que le call finisse dans la monnaie, donc qu'on paie effectivement le strike.
- **N(d1)** = le **delta** du call. C'est le nombre d'actions à détenir dans la copie. Ce n'est pas exactement une probabilité, c'est la sensibilité du prix au cours (voir l'[épisode 15](15-delta.md)).

d1 est toujours plus grand que d2, l'écart entre les deux vaut σ√T. C'est pour ça que le delta d'un call est toujours un peu plus grand que sa probabilité de finir dans la monnaie.

## Lire la formule en mots

```text
C = (ce que tu reçois en action, pondéré) − (ce que tu paies au strike, pondéré)
```

- `S × N(d1)` = la valeur de la partie action de la copie. On détient N(d1) actions qui valent S chacune.
- `K × e^(−rT) × N(d2)` = le cash emprunté dans la copie. C'est le strike actualisé, multiplié par la probabilité de devoir le payer.

C'est exactement la structure de l'exemple à une période (0,5 action moins 40 € empruntés), avec des valeurs calculées en continu.

## Exemple chiffré pas à pas

Action à 100 €, strike 100 € (à la monnaie), 1 an, taux 4 %, vol 20 %.

**Étape 1, d1.**

```text
ln(100 / 100) = 0
(r + σ² / 2) × T = (0,04 + 0,02) × 1 = 0,06
σ × √T = 0,20 × 1 = 0,20
d1 = (0 + 0,06) / 0,20 = 0,30
```

**Étape 2, d2.**

```text
d2 = 0,30 − 0,20 = 0,10
```

**Étape 3, les probabilités.**

```text
N(0,30) = 0,6179    (delta)
N(0,10) = 0,5398    (proba risque-neutre de finir ITM)
```

**Étape 4, le facteur d'actualisation.**

```text
e^(−0,04 × 1) = 0,9608
```

**Étape 5, le prix.**

```text
C = 100 × 0,6179 − 100 × 0,9608 × 0,5398
C = 61,79 − 51,87
C = 9,93 €
```

**Le put, même inputs.**

```text
P = 100 × 0,9608 × N(−0,10) − 100 × N(−0,30)
P = 96,08 × 0,4602 − 100 × 0,3821
P = 44,21 − 38,21
P = 6,00 €
```

**Vérification par la [put-call parity](14-put-call-parity.md).** C − P = S − K × e^(−rT), donc 9,93 − 6,00 = 3,93 et 100 − 96,08 = 3,92. Ça colle (l'écart vient des arrondis). Black-Scholes respecte la parité par construction.

Pourquoi le call vaut plus que le put alors qu'ils sont tous les deux à la monnaie ? Parce que le strike est payé dans un an. Avec un taux positif, payer 100 € plus tard coûte moins cher que payer 100 € aujourd'hui, ce qui avantage l'acheteur du call. À taux zéro, call et put à la monnaie valent exactement la même chose (7,97 € chacun dans cet exemple).

## Ce qui fait bouger le prix

Même option de base (S = 100, K = 100, T = 1 an, r = 4 %, σ = 20 %), on change un input à la fois.

| Ce qui change | Call | Put | Ce qu'on retient |
|---|---|---|---|
| Cas de base | 9,93 € | 6,00 € | |
| Vol à 30 % | 13,75 € | 9,83 € | Plus de vol = les deux plus chers |
| Vol à 10 % | 6,18 € | 2,26 € | Moins de vol = les deux moins chers |
| Vol à 21 % (+1 point) | 10,31 € | 6,39 € | +0,38 €, c'est le [vega](18-vega.md) |
| Cours à 101 € | 10,55 € | 5,63 € | Call +0,63 €, proche du delta 0,62 |
| Strike à 110 € (call OTM) | 5,66 € | 11,35 € | |
| Strike à 90 € (call ITM) | 16,06 € | 2,53 € | |
| Maturité 3 mois | 4,49 € | 3,49 € | Moins de temps = moins cher |
| Maturité 1 mois | 2,47 € | 2,14 € | |
| Taux à 0 % | 7,97 € | 7,97 € | Call = put à la monnaie |

Deux choses à voir dans ce tableau.

1. La vol est l'input qui pèse le plus. Passer de 20 % à 30 % fait monter le call de presque 40 %, sans que le cours ni la date ne bougent.
2. Le temps ne joue pas de façon linéaire. 3 mois valent 4,49 €, pas le quart de 9,93 €. C'est la racine carrée du temps, et c'est ce qui fait accélérer le [theta](17-theta.md) près de l'échéance.

## Le raccourci de desk

Pour une option à la monnaie, avec un taux faible :

```text
Call ≈ Put ≈ 0,4 × S × σ × √T
```

Sur l'exemple, 0,4 × 100 × 0,20 × 1 = 8 €. Le vrai prix à taux zéro est 7,97 €. Le 0,4 vient de 1 / √(2π) ≈ 0,399. Ça permet de pricer un straddle de tête (2 × 0,4 × S × σ × √T ≈ 0,8 × S × σ × √T) et de lire un prix d'option comme un mouvement attendu. C'est le calcul derrière l'[épisode 22 sur le straddle](22-the-straddle.md).

## Les Greeks sortent de la formule

Chaque Greek est la dérivée du prix Black-Scholes par rapport à un input. On note n(x) la hauteur de la cloche au point x, n(x) = e^(−x²/2) / √(2π).

| Greek | Formule (call) | Valeur dans l'exemple | Lecture |
|---|---|---|---|
| [Delta](15-delta.md) | `N(d1)` | 0,618 | +0,62 € si l'action prend 1 € |
| [Gamma](16-gamma.md) | `n(d1) / (S × σ × √T)` | 0,019 | Le delta prend 0,019 par euro de hausse |
| [Vega](18-vega.md) | `S × n(d1) × √T` (÷ 100 par point de vol) | 0,38 € | +0,38 € par point de vol |
| [Theta](17-theta.md) | `−S × n(d1) × σ / (2√T) − r × K × e^(−rT) × N(d2)` (÷ 365) | −0,016 € par jour | L'option perd 1,6 centime par jour |
| Rho | `K × T × e^(−rT) × N(d2)` (÷ 100) | 0,52 € | +0,52 € si les taux prennent 1 point |

Le delta du put vaut N(d1) − 1 = −0,382. Gamma et vega sont identiques pour le call et le put de même strike et même échéance, ce qui découle de la parité.

## Inverser la formule, la vol implicite

Dans la réalité on ne connaît pas σ, mais on voit le prix de l'option à l'écran. On fait donc tourner la formule à l'envers. On cherche la vol qui, mise dans Black-Scholes, redonne le prix observé. C'est la [vol implicite](19-implied-volatility.md).

Si le call à la monnaie de l'exemple cote 10,31 € au lieu de 9,93 €, la vol implicite est 21 %. Il n'existe pas de formule fermée pour faire ce calcul à l'envers, on procède par essais successifs (le prix monte toujours avec la vol, donc il y a une seule réponse).

C'est là que Black-Scholes change de rôle. Il ne sert plus à trouver un prix, il sert à **traduire** un prix en vol. Les options de strikes et de maturités différentes deviennent comparables sur une seule unité.

## Les hypothèses et où elles cassent

| Hypothèse | Dans la réalité | Conséquence |
|---|---|---|
| Vol constante | La vol change tout le temps et dépend du strike | Le [skew et le smile](21-the-volatility-skew.md) |
| Pas de sauts, le cours bouge en continu | Krachs, annonces de résultats, gaps à l'ouverture | Les puts très OTM valent plus que ce que dit le modèle |
| Rendements log-normaux | Les queues sont plus épaisses, les gros mouvements sont plus fréquents | Même effet, les extrêmes sont sous-pricés |
| Couverture en continu sans frais | On couvre à intervalles, avec des frais et un spread | Le hedge n'est jamais parfait, le P&L de couverture fluctue |
| Taux sans risque constant, prêt et emprunt au même taux | Les taux bougent, emprunter coûte plus cher que placer | Petit effet sur les options courtes, plus gros sur les longues |
| Pas de dividende | Beaucoup d'actions versent des dividendes | Extension de Merton, on retire le rendement du dividende |
| Exercice seulement à l'échéance (européenne) | Les options sur actions US sont souvent américaines | Il faut des arbres binomiaux ou d'autres méthodes |

### Le krach de 1987

Avant octobre 1987, la vol implicite était à peu près la même pour tous les strikes, comme le prévoit le modèle. Le 19 octobre 1987, le S&P 500 perd environ 20 % en une journée. Selon une loi log-normale avec les vols de l'époque, ce mouvement était censé ne quasiment jamais arriver. Depuis, le marché fait payer plus cher les puts OTM, et le skew est apparu de façon permanente sur les indices actions.

## Comment les desks l'utilisent quand même

Personne sur un desk ne croit que la vol est constante. Mais tout le monde utilise Black-Scholes comme **convention de cotation**. On met une vol différente pour chaque strike et chaque maturité, ce qui donne une **surface de volatilité**. La formule reste fausse, mais en y injectant la bonne vol pour chaque option, on retombe sur les prix du marché. Une phrase connue du métier résume ça, en substance, on met le mauvais chiffre dans la mauvaise formule pour obtenir le bon prix.

Pour les produits exotiques, les desks utilisent des modèles plus riches (vol locale, vol stochastique comme Heston, modèles à sauts), mais ils sont calibrés pour retrouver les prix Black-Scholes des options simples.

## Les cousins de Black-Scholes, côté taux

Sur un desk de taux on croise surtout deux variantes.

- **Black 76**, adapté par Fischer Black en 1976 pour les options sur futures et forwards. C'est le modèle standard pour les **caps**, les **floors** et les **swaptions**. On remplace S par le taux forward.
- **Bachelier (modèle normal)**, où le sous-jacent bouge en points de base plutôt qu'en pourcentage. Quand les taux européens sont passés sous zéro, Black 76 ne marchait plus (on ne peut pas prendre le log d'un nombre négatif). Le marché des swaptions s'est mis à coter en **vol normale**, en points de base par an.

C'est directement lié aux épisodes [swaps](10-interest-rate-swaps.md) et [courbe des taux](02-the-yield-curve.md).

## Un peu d'histoire

- **1973.** Fischer Black et Myron Scholes publient "The Pricing of Options and Corporate Liabilities" dans le Journal of Political Economy. Robert Merton publie la même année un article qui formalise la démonstration. La même année, le Chicago Board Options Exchange (CBOE) ouvre, premier marché organisé d'options cotées. Les traders adoptent la formule très vite.
- **1987.** Le krach révèle les limites de l'hypothèse de vol constante. Naissance du skew.
- **1995.** Fischer Black meurt.
- **1997.** Scholes et Merton reçoivent le prix Nobel d'économie. Le Nobel n'est pas attribué à titre posthume, mais le comité cite le rôle de Black.
- **1998.** Long-Term Capital Management (LTCM), le hedge fund dont Scholes et Merton étaient associés, perd environ 4,6 milliards de dollars en quelques mois. La Fed de New York organise un sauvetage par un consortium de banques. L'effondrement venait surtout d'un effet de levier énorme et de paris sur la convergence de spreads, pas de la formule d'options elle-même.

## Pièges classiques

- **Unités.** σ en décimal annuel (20 % = 0,20), T en années (3 mois = 0,25, 30 jours ≈ 30 / 365). Mettre T en jours ou σ en pourcentage donne des prix absurdes.
- **Taux continu.** La formule utilise un taux composé en continu. Un taux annuel de 4 % correspond à un taux continu de ln(1,04) ≈ 3,92 %. L'effet est faible mais existe.
- **N(d2) n'est pas la vraie probabilité.** C'est une probabilité risque-neutre. Elle ne dit rien sur ce qui va vraiment se passer.
- **N(d1) n'est pas une probabilité.** C'est le delta. On l'utilise parfois comme approximation grossière de la probabilité de finir ITM, mais c'est N(d2) qui joue ce rôle dans le modèle.
- **Vol historique ou implicite.** Mettre la vol historique dans la formule donne un prix "théorique". Le marché, lui, cote avec la vol implicite. Les deux sont presque toujours différentes (voir la variance risk premium dans l'[épisode 19](19-implied-volatility.md)).
- **Options américaines et dividendes.** La formule de base ne marche que pour une option européenne sans dividende. Un call américain sur une action sans dividende vaut la même chose qu'un européen (on n'a jamais intérêt à l'exercer en avance), mais ce n'est pas vrai pour un put américain.
- **"Le modèle est faux donc inutile."** Faux. Il est faux mais c'est la langue commune du marché. Tout le monde sait traduire un prix en vol avec la même formule.

## L'angle entretien S&T

**"Walk me through Black-Scholes."** Le prix d'une option européenne dépend de 5 inputs, cours, strike, maturité, taux et vol. On peut répliquer l'option avec l'action et du cash en ajustant le delta en continu, donc par absence d'arbitrage l'option vaut le coût de cette copie. Le rendement espéré n'apparaît pas. La formule est C = S N(d1) − K e^(−rT) N(d2), où N(d1) est le delta et N(d2) la probabilité risque-neutre d'exercice.

**"Quel input est le plus important ?"** La vol, parce que c'est le seul qu'on n'observe pas. Le reste se lit à l'écran.

**"Pourquoi le rendement attendu de l'action ne compte pas ?"** Parce que le prix vient d'une réplication. Deux personnes en désaccord sur la direction doivent quand même s'accorder sur le prix, sinon l'une des deux peut l'arbitrer.

**"Quelles sont les limites du modèle ?"** Vol constante (démentie par le skew), pas de sauts, queues trop fines, couverture continue sans frais. En pratique on garde la formule comme convention et on utilise une surface de vol.

**"Combien vaut à peu près un call à la monnaie sur un an, action à 100 et vol à 20 % ?"** 0,4 × 100 × 0,20 ≈ 8. Avec des taux positifs un peu plus (9,93 à 4 %).

**"Quel modèle pour une swaption ?"** Black 76 historiquement, Bachelier (vol normale) depuis les taux négatifs.

## Liens avec les épisodes précédents

- [Options](13-options.md) pour les définitions de call, put, strike et prime.
- [Put-Call Parity](14-put-call-parity.md), le même raisonnement d'arbitrage, et la relation que Black-Scholes respecte automatiquement.
- [Delta](15-delta.md), [Gamma](16-gamma.md), [Theta](17-theta.md), [Vega](18-vega.md), les dérivées de la formule.
- [Implied Volatility](19-implied-volatility.md), la formule utilisée à l'envers.
- [The Volatility Skew](21-the-volatility-skew.md), la preuve que l'hypothèse de vol constante est fausse.
- [The Straddle](22-the-straddle.md), le raccourci 0,8 × S × σ × √T en pratique.

<div class="ms-takeaway" markdown>

## À retenir

- Black-Scholes donne le prix d'une option européenne à partir de 5 inputs, cours, strike, maturité, taux et vol.
- L'idée de fond, on peut copier l'option avec l'action et du cash, donc l'option vaut ce que coûte la copie. Le rendement espéré et l'avis sur la direction n'interviennent pas.
- `C = S × N(d1) − K × e^(−rT) × N(d2)`. N(d1) est le delta, N(d2) la probabilité risque-neutre de finir dans la monnaie.
- La vol est le seul input inconnu, d'où la cotation en vol et la vol implicite.
- Raccourci à la monnaie, prix ≈ 0,4 × S × σ × √T.
- Le modèle est faux (vol constante, pas de sauts) et le skew le prouve. Les desks l'utilisent quand même comme langue commune, avec une vol différente par strike et par maturité.

</div>
