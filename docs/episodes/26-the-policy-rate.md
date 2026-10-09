<p class="ms-kicker">Épisode 26</p>

# The Policy <span class="ms-outline">Rate.</span>

## Pourquoi cet épisode

Tous les épisodes taux de la série partent du même point sans jamais l'expliquer. La [courbe des taux](02-the-yield-curve.md) commence au taux overnight, la jambe variable d'un [swap](10-interest-rate-swaps.md) se fixe sur un taux overnight, et le [repo](11-repo.md) fabrique SOFR. Tous ces taux sont ancrés par une seule décision, le taux directeur de la banque centrale. Cet épisode explique ce qu'est une banque centrale, comment elle fixe ce taux sans jamais dire à une banque quel taux pratiquer, comment ce taux se propage au reste de l'économie, et pourquoi elle le monte ou le baisse.

## Ce qu'est une banque centrale

C'est la banque des banques. Les banques commerciales (BNP, JPMorgan, Deutsche Bank...) ont un compte chez la banque centrale. L'argent sur ces comptes s'appelle les **réserves**. Les banques s'en servent pour se payer entre elles à la fin de chaque journée. Quand tu fais un virement de ta banque vers une autre, au bout de la chaîne ce sont des réserves qui passent d'un compte à l'autre chez la banque centrale.

Point clé, **seule la banque centrale peut créer des réserves**. Les banques peuvent se les prêter entre elles, mais pas en fabriquer. Ce monopole, c'est ce qui lui permet de contrôler le prix de l'argent à très court terme.

Les principales banques centrales.

| Banque centrale | Zone | Comité qui décide | Réunions |
|---|---|---|---|
| Federal Reserve (Fed) | États-Unis | FOMC (Federal Open Market Committee) | 8 par an |
| European Central Bank (ECB / BCE) | Zone euro | Governing Council (Conseil des gouverneurs) | 8 réunions de politique monétaire par an |
| Bank of England (BoE) | Royaume-Uni | Monetary Policy Committee (MPC) | 8 par an |
| Bank of Japan (BoJ) | Japon | Policy Board | 8 par an |

## Ce qu'est le taux directeur

C'est le taux que la banque centrale utilise pour piloter le prix de l'argent **overnight**, c'est-à-dire prêté d'aujourd'hui à demain. Chaque banque centrale a le sien.

- **Fed.** Une **fourchette cible** pour le fed funds rate, large de 0,25 %. Par exemple 4,25 % – 4,50 %. Le fed funds rate est le taux auquel les banques se prêtent leurs réserves overnight, sans garantie.
- **BCE.** Trois taux, dont un seul compte vraiment aujourd'hui, le **taux de la facilité de dépôt** (DFR, deposit facility rate).
- **BoE.** Le Bank Rate, un seul taux.

Quand on dit "la Fed a monté ses taux de 25 bps", ça veut dire que la fourchette entière a été décalée de 0,25 % vers le haut (1 bp, un point de base, vaut 0,01 %).

## Le mécanisme, un plancher et un plafond

La banque centrale ne téléphone à personne pour imposer un taux. Elle fixe deux taux, et le marché se place entre les deux.

- **Le plancher.** Le taux que la banque centrale paie aux banques sur l'argent laissé chez elle. Aucune banque ne prêtera à une autre banque en dessous, puisque laisser l'argent à la banque centrale rapporte ce taux sans aucun risque.
- **Le plafond.** Le taux auquel la banque centrale prête aux banques contre des titres en garantie (du collatéral). Aucune banque n'empruntera à une autre au-dessus, puisqu'elle peut emprunter directement à la banque centrale.

### Exemple chiffré, la BCE

Prenons des taux BCE à 2,00 % pour le dépôt (DFR), 2,15 % pour les opérations principales de refinancement (MRO), 2,40 % pour la facilité de prêt marginal (MLF).

- La banque A a 1 Md€ en trop ce soir. Elle ne le prêtera pas à la banque B en dessous de 2,00 %, puisque la BCE lui donne 2,00 % sans risque.
- La banque B a besoin de 1 Md€ ce soir. Elle ne paiera pas plus de 2,40 %, puisqu'elle peut emprunter à la BCE à 2,40 % (si elle a du collatéral).
- Donc le taux overnight entre banques finit entre 2,00 % et 2,40 %. C'est le **corridor**.

Si la BCE baisse ses taux de 25 bps, tout le corridor passe à 1,75 % – 2,15 %, et le taux overnight suit **le jour même**.

Depuis septembre 2024, l'écart entre le DFR et le MRO est de 0,15 %, et l'écart entre le MRO et le MLF reste de 0,25 %.

### Système corridor ou système plancher

Où le taux de marché se place dans le corridor dépend de la quantité de réserves.

| | Réserves rares (système corridor) | Réserves abondantes (système plancher) |
|---|---|---|
| Situation | Les banques ont tout juste les réserves dont elles ont besoin | Les banques ont beaucoup plus de réserves que nécessaire |
| Rôle de la banque centrale | Ajuster chaque jour la quantité de réserves pour viser le milieu du corridor | Fixer le taux plancher, la quantité n'est plus le sujet |
| Où se place le taux de marché | Vers le milieu, près du taux principal | Collé au plancher |
| Exemple | BCE et Fed avant 2008 | BCE et Fed après les années de QE |

Après la crise de 2008 et le quantitative easing (QE, voir plus bas), le système est inondé de réserves. Personne n'a besoin d'emprunter, tout le monde a de l'argent à placer. Le taux de marché descend donc au plancher. C'est pour ça que **€STR** (le taux overnight de référence en euro, publié par la BCE) cote quelques points de base sous le DFR. En mars 2024, la BCE a confirmé qu'elle pilote sa politique via le DFR.

### Côté Fed

La Fed fonctionne aussi en réserves abondantes depuis 2008 ("ample reserves"). Ses outils, avec des niveaux d'exemple pour une fourchette 4,25 % – 4,50 %.

| Outil | Rôle | Exemple |
|---|---|---|
| ON RRP (overnight reverse repo facility) | Plancher. La Fed emprunte du cash aux fonds monétaires contre des Treasuries, même ceux qui n'ont pas accès aux réserves | 4,25 % (bas de fourchette) |
| IORB (interest on reserve balances) | Le taux payé aux banques sur leurs réserves, l'outil principal | 4,40 % |
| EFFR (effective fed funds rate) | Le taux de marché qui en résulte | environ 4,33 % |
| Standing Repo Facility et discount window | Plafond. La Fed prête contre collatéral | 4,50 % (haut de fourchette) |

L'ON RRP existe parce que les fonds monétaires ne peuvent pas avoir de réserves à la Fed. Sans ce plancher, ils prêteraient leur cash en dessous de la fourchette.

## Comment le taux se propage

```text
taux directeur
  -> taux overnight (fed funds, €STR, SOFR, repo)       le jour même
  -> bas de la courbe (T-bills, obligations 2 ans)       via les anticipations
  -> swaps, crédits immobiliers, prêts aux entreprises
  -> emprunt, dépenses, embauches
  -> inflation                                            12 à 24 mois plus tard
```

### Étape 1, l'overnight

Les taux overnight bougent le jour de la décision, mécaniquement, par l'arbitrage du corridor. SOFR (le taux repo américain, [épisode 11](11-repo.md)) et €STR suivent.

### Étape 2, la courbe, via les anticipations

Un taux à 2 ans ne suit pas la décision du jour. Il suit ce que le marché **anticipe** pour toutes les décisions des 2 prochaines années. En première approximation :

```text
taux 2 ans ≈ moyenne des taux overnight attendus sur 2 ans + prime de terme
```

La prime de terme, c'est le petit supplément que les investisseurs demandent pour bloquer leur argent plus longtemps.

**Exemple.** Le taux overnight est à 4,00 %. Le marché s'attend à une moyenne de 4,00 % la première année et 3,00 % la deuxième (des baisses arrivent).

```text
taux 2 ans ≈ (4,00 % + 3,00 %) / 2 = 3,50 %   (+ une petite prime de terme)
```

Le 2 ans est déjà sous l'overnight alors que la banque centrale n'a encore rien fait. C'est exactement ce qui crée une [courbe inversée](02-the-yield-curve.md). Une courbe inversée, c'est le marché qui price des baisses de taux futures.

### Étape 3, l'économie réelle

Les banques se financent à des taux liés à l'overnight et au bas de courbe. Quand leur coût de financement monte, elles prêtent plus cher aux ménages et aux entreprises. Un crédit immobilier à taux variable bouge vite ([épisode 1](01-fixed-vs-floating-rate-debt.md)). Un crédit à taux fixe suit plutôt les taux longs.

## Comment le marché price les décisions futures

Sur un desk, on ne dit pas "je pense que la Fed va baisser". On dit "le marché price 3 baisses cette année". Ce chiffre sort des **swaps OIS** (overnight index swaps), des swaps dont la jambe variable est le taux overnight (même logique que l'[épisode 10](10-interest-rate-swaps.md)), et des futures sur fed funds.

**Exemple.** Overnight à 4,00 %. Le marché anticipe une baisse de 25 bps tous les trimestres à partir de dans 3 mois.

```text
mois 0-3   : 4,00 %
mois 3-6   : 3,75 %
mois 6-9   : 3,50 %
mois 9-12  : 3,25 %
moyenne    : 3,625 %
```

Le swap OIS 1 an cote donc autour de 3,625 %. En lisant ce taux, un trader en déduit "3 baisses pricées sur l'année". Si l'OIS 1 an passe à 3,75 % après un bon chiffre d'emploi, le marché a retiré une partie d'une baisse.

Conséquence importante, **une décision déjà pricée ne fait pas bouger le marché**. Si tout le monde attend une baisse de 25 bps et qu'elle arrive, la courbe bouge à peine. Ce qui fait bouger le marché, c'est la **surprise**, ou ce que la banque centrale dit sur la suite (la forward guidance).

## Pourquoi monter ou baisser

### Le mandat

| Banque centrale | Mandat |
|---|---|
| Fed | Double mandat, plein emploi et stabilité des prix. Cible de 2 % d'inflation (formalisée en 2012) |
| BCE | Stabilité des prix d'abord. Cible symétrique de 2 % à moyen terme (revue de stratégie 2021) |
| BoE | Cible de 2 % fixée par le gouvernement |

- **Inflation trop haute -> hausse.** Emprunter coûte plus cher, épargner rapporte plus, donc les ménages et les entreprises dépensent moins, la demande ralentit, et les prix montent moins vite.
- **Économie trop faible, inflation basse -> baisse.** Emprunter coûte moins cher, ce qui soutient l'investissement et la consommation.

### Le délai

L'effet sur l'inflation prend souvent 12 à 24 mois, et ce délai n'est pas stable (Milton Friedman parlait de délais longs et variables). Une banque centrale décide donc sur des **prévisions**, pas sur le chiffre du mois. Si elle attendait que l'inflation soit revenue à 2 % pour arrêter de monter, elle aurait déjà trop monté.

### Taux nominal et taux réel

Le taux réel, c'est le taux nominal moins l'inflation.

```text
taux directeur 4 %, inflation 3 %  -> taux réel = 1 %   (politique plutôt restrictive)
taux directeur 2 %, inflation 5 %  -> taux réel = −3 %  (politique très accommodante)
```

Ce qui freine l'économie, c'est le taux réel. En 2021-2022, les taux directeurs étaient encore proches de zéro alors que l'inflation dépassait 5 %, donc la politique restait très accommodante malgré les premières hausses.

### La règle de Taylor

Un repère utilisé par les économistes pour juger si le taux est "au bon niveau" (John Taylor, 1993).

```text
taux = r* + inflation + 0,5 × (inflation − 2 %) + 0,5 × écart de production
```

- **r\*** = le taux réel neutre, celui qui ne freine ni n'accélère l'économie. On ne l'observe pas, on l'estime (souvent autour de 0,5 % à 1 %).
- **écart de production** (output gap) = l'écart en % entre ce que l'économie produit et ce qu'elle pourrait produire sans créer d'inflation.

**Exemple.** r* = 1 %, inflation = 4 %, écart de production = 0.

```text
taux = 1 % + 4 % + 0,5 × (4 % − 2 %) + 0 = 6 %
```

Si le taux directeur est à 4 %, la règle dit qu'il est trop bas. Aucune banque centrale ne l'applique mécaniquement, mais le marché et les journalistes s'en servent comme point de comparaison.

## Quand le taux est à zéro, QE et QT

Une banque centrale ne peut pas baisser beaucoup sous zéro. La BCE a quand même eu un DFR négatif de juin 2014 à juillet 2022 (jusqu'à −0,50 %). Quand le taux directeur ne peut plus baisser, il reste un autre outil.

- **QE (quantitative easing).** La banque centrale achète massivement des obligations d'État avec des réserves qu'elle crée. Ça fait monter le prix des obligations, donc baisser les taux longs. Ça crée aussi l'excès de réserves qui a fait passer les systèmes en mode plancher.
- **QT (quantitative tightening).** L'inverse. La banque centrale laisse ses obligations arriver à échéance sans les remplacer, ou les vend. Les réserves diminuent.

Le taux directeur agit sur le bas de la courbe, le QE et le QT agissent plutôt sur le haut de la courbe.

## Cas réels

- **Volcker, 1979-1981.** L'inflation américaine dépasse 14 % en 1980. Paul Volcker, président de la Fed, laisse le fed funds rate monter autour de 20 %. Récession sévère, mais l'inflation retombe sous 4 % en 1983. C'est la référence historique d'une banque centrale qui casse l'inflation.
- **2008 et 2020.** Taux ramenés à zéro et QE massif dans les deux crises.
- **2022-2023.** La Fed passe de 0 % – 0,25 % (mars 2022) à 5,25 % – 5,50 % (juillet 2023), dont 4 hausses consécutives de 0,75 % en 2022. Le cycle le plus rapide depuis les années 1980. La BCE monte en juillet 2022 pour la première fois en 11 ans. Le 2 ans américain passe de moins de 1 % à plus de 4 % en 2022, et la courbe 2 ans – 10 ans reste inversée environ deux ans.
- **Septembre 2024.** La Fed baisse de 0,50 %. Quatre mois plus tard, le taux américain à 10 ans a pris environ 1 %. Le marché a revu à la hausse ses anticipations de croissance et d'inflation, et la prime de terme a monté. Une baisse du taux directeur ne garantit pas une baisse des taux longs.

## Pièges classiques

- **"La banque centrale fixe les taux des crédits."** Non. Elle fixe l'overnight. Le reste est fixé par le marché, qui intègre ses anticipations, la prime de terme et le risque de crédit ([épisode 5](05-credit-spread.md)).
- **"Une hausse fait toujours monter toute la courbe."** Non. Si le marché pense que la hausse va casser la croissance, les taux longs peuvent baisser. La courbe s'aplatit ou s'inverse.
- **"La décision fait bouger le marché."** Seulement la partie non anticipée. Le jour J, on compare la décision et le discours à ce qui était pricé.
- **Les points de base.** 25 bps = 0,25 %, pas 25 %. Et une "hausse de 25 bps" sur une fourchette Fed décale les deux bornes.
- **Taux nominal et réel.** Un taux à 5 % avec 6 % d'inflation n'est pas restrictif.
- **Taux overnight non garanti et garanti.** Le fed funds rate est un prêt sans garantie entre banques. SOFR est un repo, donc garanti par des Treasuries. Ils sont proches mais ce n'est pas le même taux.

## Le lien avec la duration

Quand le marché price plus de hausses, les taux montent, et le prix des obligations baisse. De combien, c'est la [duration](03-duration.md) qui le dit.

**Exemple.** Une obligation à 2 ans a une duration d'environ 1,9. Une surprise hawkish (plus dure que prévu) fait monter le 2 ans de 0,50 %.

```text
variation de prix ≈ −1,9 × 0,50 % = −0,95 %
```

Sur 10 M€ de nominal, c'est environ 95 000 € de perte. En [DV01](04-dv01.md), environ 1 900 € par point de base.

## L'angle entretien S&T

**"Comment la Fed fixe-t-elle concrètement les taux ?"** Elle fixe une fourchette pour le fed funds rate et la fait respecter avec des taux administrés. L'IORB rémunère les réserves des banques, l'ON RRP met un plancher pour les fonds monétaires, et la Standing Repo Facility sert de plafond. Comme les réserves sont abondantes, le taux de marché se colle au bas de la fourchette.

**"La Fed baisse de 25 bps, que fait le 2 ans ?"** Ça dépend de ce qui était pricé. Si la baisse était attendue, presque rien. Le 2 ans réagit à la surprise et au discours sur les prochaines réunions.

**"Pourquoi la courbe s'inverse-t-elle ?"** Parce que le marché anticipe des baisses de taux, souvent parce qu'il anticipe un ralentissement. Les taux courts sont tenus par le taux directeur actuel, les taux plus longs intègrent les baisses futures.

**"Comment sais-tu combien de baisses sont pricées ?"** En lisant les swaps OIS et les futures sur fed funds, et en comparant les taux forwards au taux overnight actuel.

**"Ton trade si tu penses que la Fed va baisser plus que ce que le marché price ?"** Recevoir le taux fixe sur un swap court terme (receiver), ou acheter des obligations à 2 ans. Si les baisses arrivent, les taux courts baissent et la position gagne.

**"Différence entre système corridor et système plancher ?"** Corridor quand les réserves sont rares et que la banque centrale ajuste la quantité pour viser le milieu. Plancher quand les réserves sont abondantes, le taux de marché se colle au taux de dépôt.

## Liens avec les épisodes précédents

- [Fixed vs Floating](01-fixed-vs-floating-rate-debt.md), les dettes à taux variable suivent directement le taux directeur.
- [The Yield Curve](02-the-yield-curve.md), le taux directeur ancre le bout gauche de la courbe.
- [Duration](03-duration.md) et [DV01](04-dv01.md), ce que perd une obligation quand les anticipations bougent.
- [Interest Rate Swaps](10-interest-rate-swaps.md), le taux fixe d'un swap est le pari du marché sur les taux directeurs futurs.
- [Repo](11-repo.md), les taux repo et SOFR se placent dans le corridor.

<div class="ms-takeaway" markdown>

## À retenir

- La banque centrale est la banque des banques. Elle seule crée les réserves, ce qui lui permet de contrôler le taux overnight.
- Elle n'impose aucun taux. Elle fixe un plancher (ce qu'elle paie sur les dépôts) et un plafond (ce qu'elle facture pour prêter), et l'arbitrage fait le reste.
- Avec des réserves abondantes, le taux de marché se colle au plancher. C'est le cas de la Fed et de la BCE aujourd'hui.
- L'overnight bouge le jour même. Le reste de la courbe bouge sur les anticipations des prochaines décisions.
- Une décision déjà pricée ne fait presque rien bouger. C'est la surprise qui compte.
- On monte quand l'inflation est trop haute, on baisse quand l'économie est trop faible, avec 12 à 24 mois de délai, donc on décide sur des prévisions.

</div>
