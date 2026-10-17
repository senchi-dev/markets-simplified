<p class="ms-kicker">Épisode 28</p>

# FX <span class="ms-outline">Forwards.</span>

## Pourquoi cet épisode

Les deux derniers épisodes ([taux directeur](26-the-policy-rate.md), [QE et QT](27-qe-and-qt.md)) expliquaient comment chaque banque centrale fixe le prix de l'argent dans sa monnaie. Cet épisode ouvre le marché des changes (FX, pour foreign exchange) par le lien le plus direct avec tout ça. L'écart entre les taux de deux pays fixe le prix auquel on peut échanger ces deux monnaies dans le futur. Pas une prévision, un calcul d'arbitrage qu'on peut refaire à la main.

## Lire un taux de change

**EUR/USD = 1,10** veut dire que 1 euro coûte 1,10 dollar.

- La première monnaie (EUR) est la **devise de base**. On donne toujours le prix d'1 unité de la base.
- La deuxième (USD) est la **devise de cotation**, celle dans laquelle le prix est exprimé.
- Si EUR/USD passe à 1,12, on obtient plus de dollars pour 1 euro, donc l'euro s'est renforcé et le dollar s'est affaibli.
- Si EUR/USD passe à 1,08, l'euro s'est affaibli.

### Le pip

Un **pip** est la 4e décimale, 0,0001. Passer de 1,1000 à 1,1050, c'est un mouvement de 50 pips. Exception, pour les paires avec le yen (USD/JPY = 150,00), le pip est la 2e décimale, 0,01, parce qu'un yen vaut très peu.

### Bid, ask et spread

Une banque cote toujours deux prix, par exemple EUR/USD 1,1000 / 1,1002.

- **Bid** (1,1000), le prix auquel la banque achète des euros contre des dollars.
- **Ask** (1,1002), le prix auquel elle en vend.
- L'écart (2 pips) est la marge de la banque. Sur les grandes paires il est minuscule, sur les monnaies peu échangées il peut être de dizaines de pips.

### Les conventions de cotation

On ne choisit pas librement l'ordre des devises. Le marché suit une hiérarchie. EUR passe avant GBP, qui passe avant AUD, NZD, USD, CAD, CHF, puis JPY. D'où EUR/USD, GBP/USD, USD/JPY, USD/CHF. Le dollar est la base face à la plupart des autres monnaies, mais pas face à l'euro ni la livre.

### La taille du marché

Le FX est le plus gros marché financier du monde. L'enquête triennale de la BIS (la banque des banques centrales) mesurait environ 7 500 Md$ échangés **par jour** en avril 2022, dont environ la moitié en FX swaps (voir plus bas). Le dollar est d'un côté d'environ 9 transactions sur 10.

## Spot et forward

- **Spot.** On échange aujourd'hui, au taux du jour. En pratique le règlement se fait 2 jours ouvrés plus tard (T+2), sauf quelques exceptions comme USD/CAD (T+1).
- **Forward (ou terme).** On se met d'accord aujourd'hui sur un taux, mais l'échange se fait plus tard, par exemple dans 1 an. Rien ne s'échange avant la date. Le taux est bloqué.

## La question

EUR/USD est à 1,10 aujourd'hui. Quel taux une banque doit-elle te proposer pour échanger dans 1 an ?

On pourrait croire qu'elle devine où sera l'euro dans un an. Elle ne devine rien. Elle utilise seulement le taux spot et les taux d'intérêt de chaque monnaie.

## L'exemple, deux chemins

Tu as **100 €** et tu veux des dollars dans 1 an.

- Taux d'intérêt sur l'euro, **2 %** par an.
- Taux d'intérêt sur le dollar, **4 %** par an.
- Spot, **1,10**.

**Chemin 1, changer maintenant puis placer en dollars.**

```text
100 € × 1,10 = 110 $ aujourd'hui
110 $ placés à 4 % pendant 1 an -> 110 × 1,04 = 114,40 $
```

Dans un an tu as **114,40 $**.

**Chemin 2, placer en euros puis changer dans un an.**

```text
100 € placés à 2 % pendant 1 an -> 100 × 1,02 = 102 €
Dans un an tu changes 102 € au taux forward F -> 102 × F dollars
```

### Pourquoi les deux chemins doivent donner la même chose

Les deux chemins sont sans risque. Dès aujourd'hui tu sais exactement ce que tu auras.

Si le chemin 1 donnait plus de dollars que le chemin 2, tout le monde ferait le chemin 1 et l'inverse du chemin 2 en même temps (emprunter en dollars, changer en euros, placer en euros, revendre au forward), et gagnerait de l'argent sans risque. Les banques perdraient à chaque fois. Le taux forward est donc fixé pour que les deux chemins donnent exactement le même résultat.

```text
102 × F = 114,40
F = 114,40 / 102 = 1,1216
```

Le forward à 1 an est **1,1216**.

## La formule

C'est le même calcul écrit de façon générale. On l'appelle la **parité des taux d'intérêt couverte** (covered interest parity, CIP).

```text
Forward = Spot × (1 + taux de la devise de cotation × T) / (1 + taux de la devise de base × T)
```

- **T** = la durée en années (6 mois = 0,5, 3 mois = 0,25).
- Le taux de la devise de **cotation** (la 2e) va en **haut**. Celui de la devise de **base** (la 1re) va en **bas**.

Pour EUR/USD, le dollar est la devise de cotation.

```text
1 an    : 1,10 × (1 + 0,04) / (1 + 0,02)             = 1,1216
6 mois  : 1,10 × (1 + 0,04 × 0,5) / (1 + 0,02 × 0,5) = 1,10 × 1,02 / 1,01 = 1,1109
```

Pour des durées de plus d'un an, on utilise des taux composés, (1 + r)^T au lieu de (1 + r × T). Et sur un desk on compte les jours exactement, avec la convention de chaque monnaie (jours réels / 360 pour le dollar et l'euro, jours réels / 365 pour la livre).

## Ce que ça veut dire

Dans un an tu obtiens 1,1216 dollar par euro au lieu de 1,10. Sur le forward, l'euro vaut un peu plus et le dollar un peu moins.

La règle, **la devise qui a le taux d'intérêt le plus haut est moins chère sur le forward**. On dit qu'elle cote en **déport** (forward discount). L'autre cote en **report** (forward premium).

Pourquoi ? Le dollar rapporte 2 % de plus que l'euro. Si le forward ne s'ajustait pas, tu passerais tes euros en dollars, tu toucherais 2 % de plus, et tu bloquerais ton retour en euros avec le forward, sans aucun risque. Le forward te reprend exactement ces 2 %. Pas de repas gratuit.

### Les points de terme

L'écart entre le forward et le spot s'appelle les **points de terme** (forward points).

```text
1,1216 − 1,10 = 0,0216 = 216 pips
```

Sur un écran, les banques ne cotent pas le forward complet. Elles cotent le spot et les points (+216). Le forward complet (1,1216) s'appelle l'**outright**.

Approximation rapide, les points valent à peu près spot × écart de taux × T. Ici 1,10 × 2 % × 1 = 0,022, soit environ 220 pips.

## Deuxième exemple, USD/JPY

Spot USD/JPY = 150. Taux dollar 4 %, taux yen 0,5 %. Ici le dollar est la devise de **base**, donc son taux va en bas.

```text
Forward 1 an = 150 × (1 + 0,005) / (1 + 0,04) = 150 × 1,005 / 1,04 = 144,95
```

Le forward est **plus bas** que le spot. Normal, c'est la devise de base (le dollar) qui a le taux le plus haut, donc c'est elle qui cote en déport. Points de terme, 144,95 − 150 = −5,05 yens, soit −505 pips (pip yen = 0,01).

Même règle, la monnaie qui rapporte le plus est moins chère dans le futur. Seule la façon dont ça apparaît dans le chiffre change selon qu'elle est base ou cotation.

## Le forward n'est pas une prévision

C'est le point le plus important et le plus mal compris. Le forward à 1,1216 ne dit **pas** que le marché pense que l'euro va monter. Il est juste le résultat de l'arbitrage. Si les taux étaient inversés (euro à 4 %, dollar à 2 %), le forward serait sous le spot, quel que soit l'avis du marché sur l'euro.

La version "prévision" de la formule existe, c'est la **parité des taux non couverte** (uncovered interest parity, UIP). Elle dirait que la monnaie qui rapporte plus va se déprécier d'autant. En pratique, ça ne marche pas. Les études montrent que les monnaies à taux élevés ont plutôt tendance à ne pas se déprécier autant, voire à monter (c'est le "forward premium puzzle", Fama, 1984). C'est ce qui rend possible le carry trade, emprunter dans la monnaie à taux bas et placer dans celle à taux haut, en gardant le risque de change. Ça rapporte souvent un peu, et parfois ça perd beaucoup d'un coup.

**Exemple d'un coup comme ça, août 2024.** Pendant des années, des investisseurs ont emprunté en yen (taux proches de zéro) pour placer en dollars ou ailleurs. Fin juillet 2024, la Banque du Japon monte ses taux et le yen remonte. USD/JPY passe d'environ 162 début juillet à environ 142 le 5 août. Ceux qui avaient emprunté en yen doivent rembourser plus cher, ils coupent leurs positions en même temps, ce qui fait encore monter le yen. Le 5 août 2024, le Nikkei perd environ 12 % en une séance.

Différence clé. Le forward (CIP) est **couvert**, donc sans risque de change, et l'arbitrage le fait tenir. Le carry trade (UIP) n'est **pas couvert**, donc on prend le risque de change, et rien ne force la formule à tenir.

## Qui s'en sert

### Une entreprise qui couvre son risque de change

Une entreprise française va recevoir 10 M$ dans 1 an. Ses coûts sont en euros. Elle ne sait pas combien vaudra le dollar dans un an, donc elle vend ses dollars à terme aujourd'hui, au forward de 1,1216.

```text
10 000 000 $ / 1,1216 = 8 915 835 €
```

| EUR/USD dans 1 an | Sans couverture | Avec le forward |
|---|---|---|
| 1,00 | 10 000 000 € | 8 915 835 € |
| 1,1216 | 8 915 835 € | 8 915 835 € |
| 1,25 | 8 000 000 € | 8 915 835 € |

Avec le forward, elle connaît son chiffre au centime près. Elle renonce au cas favorable (1,00) pour se protéger du cas défavorable (1,25). C'est le même échange qu'avec un [swap de taux](10-interest-rate-swaps.md), on échange l'incertitude contre un chiffre fixe.

### Le FX swap, un prêt déguisé

Un **FX swap** combine deux opérations dans un seul trade. Un échange au spot aujourd'hui, et l'échange inverse au forward plus tard.

**Exemple.** Une banque européenne a besoin de dollars pendant 3 mois. Elle donne 100 M€ et reçoit 110 M$ aujourd'hui au spot de 1,10. Dans 3 mois, elle rend des dollars et récupère ses 100 M€, au taux forward fixé aujourd'hui.

En pratique c'est un **prêt en dollars garanti par des euros**. Exactement comme un [repo](11-repo.md), où on emprunte du cash contre des titres en garantie, sauf qu'ici la garantie est une autre monnaie. Le coût du prêt est caché dans les points de terme.

C'est le produit FX le plus échangé au monde. Les banques non américaines, les assureurs japonais qui achètent des obligations américaines, les gestionnaires européens, tous s'en servent pour se financer ou se couvrir en dollars.

### Les NDF

Certaines monnaies ne peuvent pas être échangées librement à l'étranger (contrôle des changes). Pour elles, on utilise des **NDF** (non-deliverable forwards). Personne ne livre la monnaie. À l'échéance, on compare le taux forward au taux réel du jour et on règle seulement la différence, en dollars. C'est courant pour des monnaies comme le real brésilien, la roupie indienne ou le won coréen.

## Là où la formule casse un peu, la base cross-currency

Avant 2008, la formule tenait presque parfaitement. Depuis, il y a un écart persistant.

**Exemple.** Avec les taux de l'exemple, le forward 3 mois théorique est :

```text
1,10 × (1 + 0,04 × 0,25) / (1 + 0,02 × 0,25) = 1,10 × 1,01 / 1,005 = 1,1055
```

Supposons que le marché cote en réalité 1,1062. Quel taux en dollars ça implique ?

```text
1 + taux dollar implicite × 0,25 = 1,1062 × 1,005 / 1,10 = 1,0107
taux dollar implicite ≈ 4,27 %
```

Emprunter des dollars via le FX swap coûte 4,27 %, alors que le taux dollar "normal" est 4,00 %. L'écart d'environ 27 points de base est la **base cross-currency** (cross-currency basis). Par convention on la note négative (ici environ −27 bps) quand emprunter des dollars via le FX coûte plus cher que prévu.

### Pourquoi elle existe

- **Le coût du bilan.** Pour arbitrer l'écart, une banque doit emprunter et prêter, donc gonfler son bilan. Depuis 2008, les règles de capital (ratio de levier notamment) rendent ça coûteux. L'arbitrage existe mais il n'est plus gratuit, donc il ne referme pas complètement l'écart.
- **La demande de dollars.** Beaucoup d'acteurs non américains ont besoin de dollars (banques, assureurs japonais qui couvrent leurs obligations américaines, entreprises endettées en dollars). Ils sont prêts à payer un peu plus.
- **Les fins de trimestre et d'année.** Les banques réduisent leur bilan avant leurs dates de publication. La base se creuse souvent autour de ces dates.

### En crise

La base explose quand tout le monde veut des dollars en même temps. En 2008, puis en mars 2020. En mars 2020, la Fed a élargi ses **swap lines**, des FX swaps entre la Fed et d'autres banques centrales (BCE, BoJ, BoE, BNS...). Elle leur prête des dollars contre leur monnaie, et elles les reprêtent à leurs banques. La base s'est resserrée dans les semaines qui ont suivi. C'est la Fed qui joue le rôle de prêteur de dernier recours en dollars pour le monde entier.

## Pièges classiques

- **"Le forward, c'est ce que le marché prévoit."** Non. C'est le résultat de l'arbitrage spot + taux. Voir UIP et CIP plus haut.
- **Mettre les taux du mauvais côté.** Le taux de la devise de cotation (la 2e) en haut, celui de la base (la 1re) en bas. Vérification rapide, la monnaie au taux le plus haut doit être moins chère sur le forward.
- **Confondre points et outright.** "+216" sont des points, à ajouter au spot. L'outright est 1,1216.
- **Oublier le pip du yen.** Sur USD/JPY, 1 pip = 0,01, pas 0,0001.
- **Intérêts simples ou composés.** En dessous d'un an, (1 + r × T). Au-dessus, (1 + r)^T. Et les conventions de jours changent selon la monnaie.
- **Croire que la couverture fait gagner de l'argent.** Elle supprime l'incertitude, elle ne crée pas de profit. Si le dollar monte, l'entreprise couverte "perd" par rapport à celle qui ne l'est pas.

## L'angle entretien S&T

**"EUR/USD est à 1,10, taux euro 2 %, taux dollar 4 %. Forward 1 an ?"** 1,10 × 1,04 / 1,02 = 1,1216. Le dollar a le taux le plus haut, donc il est moins cher sur le forward, donc EUR/USD forward au-dessus du spot.

**"Pourquoi la monnaie au taux le plus haut est-elle en déport ?"** Sinon on pourrait emprunter dans la monnaie à taux bas, placer dans celle à taux haut, et couvrir le retour avec le forward pour un profit sans risque. Le forward efface l'écart de taux.

**"Le forward est-il une prévision ?"** Non, c'est un prix d'arbitrage. La prévision serait l'UIP, qui ne tient pas empiriquement, et c'est pour ça que le carry trade existe.

**"C'est quoi un FX swap et à quoi ça sert ?"** Un spot et un forward inverse dans le même trade. Économiquement, un prêt garanti dans une autre monnaie. Ça sert à se financer en dollars ou à couvrir un portefeuille en devise étrangère.

**"C'est quoi la base cross-currency ?"** L'écart entre le coût d'emprunt en dollars implicite dans les FX swaps et le taux dollar direct. Elle existe parce que l'arbitrage coûte du bilan depuis 2008 et parce que la demande de dollars hors des États-Unis est forte. Elle se creuse en crise et aux fins de trimestre.

**"Comment la Fed a calmé le marché du dollar en mars 2020 ?"** En élargissant ses swap lines avec les autres banques centrales, qui ont reprêté des dollars à leurs banques.

## Liens avec les épisodes précédents

- [The Policy Rate](26-the-policy-rate.md), ce sont les taux directeurs qui fixent les taux qu'on met dans la formule.
- [QE and QT](27-qe-and-qt.md), les taux bas puis la hausse rapide de 2022 qui ont fait bouger les écarts de taux et les forwards.
- [Interest Rate Swaps](10-interest-rate-swaps.md), même logique d'échanger une incertitude contre un chiffre fixe.
- [Repo](11-repo.md), le FX swap est un prêt garanti, comme un repo avec une monnaie en garantie.
- [Put-Call Parity](14-put-call-parity.md), le même raisonnement d'arbitrage, deux chemins sans risque doivent coûter pareil.

<div class="ms-takeaway" markdown>

## À retenir

- EUR/USD = 1,10 veut dire 1 euro coûte 1,10 dollar. Base en premier, cotation en second.
- Le forward n'est pas une prévision. Il est fixé pour que changer maintenant et placer, ou placer et changer plus tard, donnent le même résultat.
- `Forward = Spot × (1 + taux cotation × T) / (1 + taux base × T)`.
- La monnaie au taux d'intérêt le plus haut est moins chère sur le forward. Le forward efface l'écart de taux.
- Les entreprises s'en servent pour bloquer leur taux de change, les banques pour emprunter des dollars via les FX swaps.
- Depuis 2008, emprunter des dollars via le FX coûte un peu plus que la formule (la base cross-currency), et l'écart explose en crise.

</div>
