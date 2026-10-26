<p class="ms-kicker">Épisode 29</p>

# The Carry <span class="ms-outline">Trade.</span>

## Pourquoi cet épisode

L'[épisode 28](28-fx-forwards.md) montrait que le forward est **couvert**. Tu bloques le taux de change, donc tu ne gagnes rien de plus que le taux sans risque. Le carry trade est exactement le même montage **sans la couverture**. Tu gardes l'écart de taux, et tu prends le risque de change. C'est l'une des stratégies les plus utilisées du marché, et elle a une forme de risque très particulière, de petits gains réguliers et de grosses pertes d'un coup.

## Définition

Tu empruntes dans une monnaie à taux **bas** (la monnaie de financement), tu changes l'argent dans une monnaie à taux **haut**, tu le places, et tu **ne couvres pas** le taux de change. Tu touches l'écart de taux, le **carry**, tant que le taux de change ne bouge pas contre toi.

La version classique pendant des années, emprunter en **yen** (taux proche de 0 %) et placer en **dollars** (4 à 5 %). Le yen a un nom dans ce rôle, la monnaie de financement. On parlait de "Mrs Watanabe", les épargnants japonais qui plaçaient leur argent à l'étranger.

## L'exemple chiffré

USD/JPY = 150 (1 dollar coûte 150 yens). Taux yen **0,5 %**, taux dollar **4 %**.

**Aujourd'hui.**

```text
Tu empruntes 15 000 000 ¥ à 0,5 %
Tu changes : 15 000 000 / 150 = 100 000 $
Tu places 100 000 $ à 4 %
```

**Dans 1 an.**

```text
Tu as :  100 000 $ × 1,04      = 104 000 $
Tu dois : 15 000 000 ¥ × 1,005 = 15 075 000 ¥
```

Tu as des dollars et tu dois des yens. Tout dépend du taux de change dans un an.

| USD/JPY dans 1 an | 104 000 $ valent | Tu rends | Résultat en yens | En dollars | Sur 100 000 $ |
|---|---|---|---|---|---|
| 160 (dollar monte) | 16 640 000 ¥ | 15 075 000 ¥ | +1 565 000 ¥ | +9 781 $ | +9,8 % |
| 150 (inchangé) | 15 600 000 ¥ | 15 075 000 ¥ | +525 000 ¥ | +3 500 $ | +3,5 % |
| 144,95 | 15 075 000 ¥ | 15 075 000 ¥ | 0 | 0 | 0 % |
| 140 (yen monte) | 14 560 000 ¥ | 15 075 000 ¥ | −515 000 ¥ | −3 679 $ | −3,7 % |
| 130 (yen monte beaucoup) | 13 520 000 ¥ | 15 075 000 ¥ | −1 555 000 ¥ | −11 962 $ | −12,0 % |

Un mouvement de 6,7 % du yen (150 vers 140) efface toute l'année d'intérêts, et au-delà.

## Le point d'équilibre est le forward

À quel taux ne gagnes-tu rien ?

```text
104 000 × X = 15 075 000
X = 15 075 000 / 104 000 = 144,95
```

C'est **exactement le taux forward** de l'épisode précédent (150 × 1,005 / 1,04 = 144,95).

Donc le carry trade est un **pari que le taux de change dans un an sera meilleur que le forward**. Pas meilleur que le spot, meilleur que le forward.

### Même trade, version forward

On peut faire le même trade sans emprunter ni placer rien. On **achète USD/JPY à terme** à 144,95. Dans un an, si le spot est à 150, tu achètes à 144,95 et tu revends à 150 :

```text
profit = 150 − 144,95 = 5,05 ¥ par dollar  ->  5,05 / 144,95 ≈ 3,5 %
```

Même résultat que le montage emprunt + placement (3,5 %). C'est pour ça que sur un desk on parle de "long USD/JPY forward" pour dire "faire du carry". Les points de terme (−505 pips, épisode 28) sont le prix à payer pour être long de la monnaie à taux haut, et le trade gagne si le spot finit au-dessus du forward.

## Pourquoi ça marche (la plupart du temps)

L'[épisode 28](28-fx-forwards.md) disait que la **parité non couverte** (UIP) prévoit que la monnaie à taux haut se déprécie exactement de l'écart de taux. Si c'était vrai, le carry trade rapporterait zéro en moyenne.

En pratique, c'est faux. Les études (à partir de Fama, 1984) montrent que les monnaies à taux haut se déprécient **moins** que l'écart de taux, parfois pas du tout. C'est le "forward premium puzzle". Le carry trade a donc gagné de l'argent en moyenne sur des décennies.

### Pourquoi le marché laisse ça exister

La réponse la plus répandue, c'est que le carry est la **rémunération d'un risque**, comme l'assurance qu'on vend. Tu encaisses une petite prime chaque année, et en échange tu acceptes de perdre beaucoup quand le marché panique. Le carry se comporte comme la vente d'une option, dont on a vu le profil dans l'[épisode 13](13-options.md) (petite prime, grosse perte possible).

Autres explications avancées. Les banques centrales qui lissent les taux de change. Les investisseurs qui réagissent trop lentement aux écarts de taux. Les flux de couverture des entreprises. Personne n'a de réponse définitive.

## Comment ça perd, les pertes d'un coup

Les gains sont **petits et réguliers** (quelques % par an). Les pertes sont **grosses et brutales**. Les traders disent que le carry monte par l'escalier et descend par l'ascenseur. Les rendements d'un carry trade sont "à asymétrie négative" (negative skew), il y a beaucoup de petits gains et de rares très grosses pertes.

### Le levier

Presque personne ne fait du carry sans levier, parce que 3,5 % par an est peu. Avec du levier :

| Levier | Gain si rien ne bouge (3,5 %) | Perte si USD/JPY va à 140 (−3,7 %) |
|---|---|---|
| 1x | +3,5 % | −3,7 % |
| 5x | +17,5 % | −18,4 % |
| 10x | +35 % | −36,8 % |
| 20x | +70 % | −73,6 % |

Avec un levier de 20x, un mouvement de 6,7 % du yen détruit les trois quarts du capital. Et les courtiers FX déclenchent la liquidation de force bien avant ça.

### La spirale de dénouement

Tout le monde fait le même trade, emprunter du yen et le vendre. Quand quelque chose fait peur au marché :

1. Les investisseurs ferment leurs positions, donc ils **rachètent du yen** pour rembourser leurs prêts.
2. Racheter du yen le fait monter.
3. Un yen plus fort fait perdre les autres carry traders, qui ferment à leur tour (appels de marge, stop-loss).
4. Le yen monte encore plus.

C'est la même mécanique que la spirale des fonds de pension britanniques de l'[épisode 27](27-qe-and-qt.md) (les ventes forcées font bouger le prix, ce qui force d'autres ventes). C'est aussi la même que le gamma squeeze de l'[épisode 20](20-the-gamma-squeeze.md), où la couverture des uns nourrit le mouvement qui force les autres.

## Quand ça a mal tourné

### 1. Octobre 1998, après LTCM

L'été 1998, la Russie fait défaut sur sa dette, le fonds LTCM s'effondre ([épisode 25](25-black-scholes.md)). Les hedge funds, qui avaient emprunté en yen pour financer des positions partout, dénouent d'un coup. Les 7 et 8 octobre 1998, USD/JPY passe d'environ 135 à environ 112 en deux jours, un yen environ 15 % plus fort.

**Pourquoi.** Les positions de carry étaient énormes et concentrées sur la même monnaie de financement. Quand les fonds ont eu besoin de cash ailleurs, tous ont racheté du yen en même temps.

### 2. 2008, l'AUD/JPY

L'Australie avait des taux autour de 7 %, le Japon autour de 0,5 %. AUD/JPY était la paire de carry la plus populaire. Elle valait environ 107 en juillet 2008 et environ 55 en octobre 2008. Presque la moitié de sa valeur en trois mois.

**Pourquoi.** La crise Lehman a fait fuir tout le monde vers les monnaies sûres (yen, dollar) et vendre les monnaies à taux haut. Sur ces trois mois, le carry gagné (environ 6,5 % par an, donc environ 1,6 % sur la période) ne pesait rien face à une baisse de 45 %.

### 3. Janvier 2015, le franc suisse

Depuis 2011, la banque centrale suisse (BNS) maintenait un plancher à 1,20 franc pour 1 euro. Les taux suisses étaient très bas. Beaucoup de ménages en Pologne, en Hongrie et dans d'autres pays d'Europe de l'Est s'étaient endettés **en francs suisses** pour leur crédit immobilier, parce que le taux était plus bas que celui du crédit en monnaie locale. Ils étaient, sans le savoir, dans un carry trade, **empruntés en franc, revenus en zloty ou en forint**.

Le 15 janvier 2015, la BNS abandonne le plancher sans prévenir. Le franc monte jusqu'à environ 30 % face à l'euro en quelques minutes, et finit la journée autour de 15 à 20 % plus haut.

**Conséquences.** La dette de ces ménages a augmenté d'autant en une nuit, alors que leurs salaires restaient en monnaie locale. Des courtiers FX ont fait faillite le jour même, parce que leurs clients avaient des pertes supérieures à leur dépôt (par exemple Alpari UK, et FXCM a dû être renfloué). Le point commun, une position qui gagne un petit carry pendant des années, avec une banque centrale qui cache un risque de saut.

### 4. Août 2024, le yen

Pendant des années, des investisseurs du monde entier avaient emprunté en yen. Fin juillet 2024, la Banque du Japon relève ses taux et laisse entendre d'autres hausses. En même temps, la Fed laisse entrevoir des baisses, donc l'écart de taux se réduit des deux côtés. USD/JPY passe d'environ 162 début juillet à environ 142 le 5 août, un yen environ 14 % plus fort. Le Nikkei perd environ 12 % le 5 août, sa pire séance depuis 1987, puis rebondit presque entièrement dans les jours suivants.

**Pourquoi.** L'écart de taux qui justifiait le trade diminuait (moins de carry), et le yen montait (perte de change). Les deux effets jouent dans le même sens, donc les positions ferment en même temps.

## Comment mesurer si le carry est intéressant

### Le ratio carry / volatilité

Gagner 3,5 % ne veut pas dire la même chose si la paire bouge de 5 % par an ou de 15 % par an.

```text
ratio carry / vol = écart de taux / volatilité du taux de change
```

**Exemple.** Écart de taux 3,5 %.
- Si la volatilité implicite de USD/JPY est 7 %, ratio = 3,5 / 7 = 0,5.
- Si elle est 14 %, ratio = 3,5 / 14 = 0,25.

Avec le même écart, le trade est deux fois moins intéressant quand la volatilité double. Les traders cherchent un ratio élevé, et une baisse du ratio (volatilité qui monte) est un signal d'alerte.

### Ce que disent les options

On a vu dans l'[épisode 21](21-the-volatility-skew.md) que le prix des puts et des calls n'est pas symétrique quand le marché craint une direction. Pour une paire de carry, le marché paie plus cher pour se protéger contre la **chute de la monnaie à taux haut** (donc contre le dénouement). On lit ça dans le **risk reversal**, la différence de volatilité implicite entre un put et un call de même delta. Quand ce risk reversal devient très déséquilibré, le marché price un risque de dénouement.

### Se couvrir avec des options

On peut acheter un put sur la monnaie à taux haut (ici un put USD/JPY, qui gagne si le dollar baisse face au yen), pour plafonner la perte. Ça coûte de la prime, qui mange une partie du carry. C'est l'[épisode 13](13-options.md) appliqué au FX. Le trade devient un carry avec un plancher de perte, et sa rentabilité dépend du ratio entre le carry reçu et la prime payée.

## Le carry n'est pas que du FX

Le mot "carry" désigne en général **ce que tu gagnes si rien ne bouge**.

| Marché | Ce que fait le trade | Le carry | Le risque |
|---|---|---|---|
| FX | Long la monnaie à taux haut, court celle à taux bas | L'écart de taux | Le dénouement, le saut de change |
| Obligations | Acheter une obligation longue financée en [repo](11-repo.md) court | Le coupon moins le coût du repo | Les taux montent ([duration](03-duration.md)) |
| Courbe des taux | Être payeur ou receveur dans un [swap](10-interest-rate-swaps.md), être sur la pente de la [courbe](02-the-yield-curve.md) | Le roll-down (le titre se rapproche de l'échéance et glisse le long de la courbe) | La courbe bouge |
| Crédit | Vendre de la protection sur un [CDS](06-credit-default-swaps.md) | La prime reçue | Le défaut |
| Options | Vendre une option, voir [theta](17-theta.md) | La prime qui s'érode | Le gros mouvement |

Même structure à chaque fois. Un petit revenu régulier, contre une grosse perte rare.

## Pièges classiques

- **Croire que le carry est un gain sans risque.** Tant que l'on ne couvre pas, ce n'est pas du tout sans risque. Le gain est la rémunération d'un risque de change.
- **Comparer au spot et pas au forward.** Le point d'équilibre est le forward (144,95), pas le spot (150). Il y a un petit écart qui fait la différence entre gagner et perdre.
- **Oublier le levier.** Les chiffres d'un carry sans levier sont petits. C'est le levier qui rend le trade attractif, et qui le rend dangereux.
- **Le risque de saut d'un taux de change administré.** Quand une banque centrale défend un plancher ou un cap (franc suisse en 2015), le risque est caché jusqu'au jour où il saute d'un coup.
- **Se fier à la volatilité récente.** La volatilité est basse juste avant les dénouements, parce que le carry marche bien. Un ratio carry / vol très élevé peut être un signe de complaisance plutôt qu'une bonne affaire.
- **Les coûts.** Bid-ask, financement du levier, rollover quotidien. Sur 3,5 % de carry, ça compte.

## L'angle entretien S&T

**"C'est quoi un carry trade ?"** Emprunter dans une monnaie à taux bas, placer dans une monnaie à taux haut, sans couvrir le change. On gagne l'écart de taux tant que la monnaie à taux haut ne se déprécie pas plus que cet écart.

**"Où est le point d'équilibre ?"** Au taux forward. Si le spot final est meilleur que le forward, le trade gagne, sinon il perd.

**"Pourquoi ça marche, alors que la parité non couverte dit le contraire ?"** Les monnaies à taux haut se déprécient en moyenne moins que l'écart de taux (forward premium puzzle). Le carry est aussi une rémunération pour le risque de dénouement.

**"Quel est le profil de risque ?"** Petits gains réguliers, grosses pertes brutales. Asymétrie négative, comme vendre une option.

**"Pourquoi les pertes arrivent-elles toutes en même temps ?"** Tout le monde fait le même trade, donc quand un choc arrive, tout le monde ferme en même temps, ce qui fait bouger le prix contre tous les autres. Une spirale de ventes forcées.

**"Cite des exemples."** 1998 après LTCM, 2008 AUD/JPY, 2015 franc suisse, août 2024 yen.

**"Comment on se couvre ?"** Avec un put sur la monnaie à taux haut. Ça plafonne la perte mais ça mange une partie du carry.

**"Quelle est la différence entre un carry trade et un forward ?"** Un forward est couvert, donc il ne rapporte rien de plus que les taux. Le carry n'est pas couvert, donc il peut gagner ou perdre. Le carry est un pari que le spot final sera meilleur que le forward.

## Liens avec les épisodes précédents

- [FX Forwards](28-fx-forwards.md), le point d'équilibre du carry est le forward.
- [QE and QT](27-qe-and-qt.md), la même spirale de ventes forcées, et les écarts de taux entre pays viennent des banques centrales.
- [The Policy Rate](26-the-policy-rate.md), ce sont les décisions de taux qui créent et défont les écarts.
- [Options](13-options.md), le carry ressemble à une vente d'option, et une option peut le couvrir.
- [Volatility Skew](21-the-volatility-skew.md), le risk reversal lit la peur du dénouement.
- [Theta](17-theta.md), vendre de l'option, c'est du carry aussi.

<div class="ms-takeaway" markdown>

## À retenir

- Le carry trade, c'est emprunter dans une monnaie à taux bas, placer dans une monnaie à taux haut, sans couvrir le change.
- Le point d'équilibre est le taux forward. Le trade gagne si le taux de change final est meilleur que le forward.
- Il gagne en moyenne parce que les monnaies à taux haut se déprécient moins que l'écart de taux, mais c'est la rémunération d'un risque.
- Le profil est petits gains réguliers, grosses pertes d'un coup. Le levier amplifie les deux.
- Les pertes arrivent en même temps parce que tout le monde fait le même trade et sort en même temps (1998, 2008, 2015, 2024).
- Le carry n'existe pas qu'en FX. C'est aussi les obligations financées en repo, la vente de CDS et la vente d'options.

</div>
