<p class="ms-kicker">Épisode 27</p>

# QE and <span class="ms-outline">QT.</span>

## Pourquoi cet épisode

L'[épisode 26](26-the-policy-rate.md) expliquait comment une banque centrale contrôle le taux overnight. Mais en 2008 puis en 2020, les banques centrales ont descendu ce taux à zéro et l'économie avait encore besoin d'aide. Le taux directeur ne contrôle que l'argent au jour le jour, alors que les crédits immobiliers, les prêts aux entreprises et l'emprunt des États se fixent sur les **taux longs** (5, 10, 30 ans). Le QE est l'outil qui sert à faire baisser ces taux longs. Le QT est la marche arrière.

Cet épisode explique comment ça marche concrètement, dans les bilans, pourquoi ça fait baisser les taux, ce que ça a donné en vrai, et surtout les fois où ça a mal tourné, avec pourquoi.

## Définitions

**QE (quantitative easing, assouplissement quantitatif).** La banque centrale achète massivement des obligations, surtout des obligations d'État (la Fed a aussi acheté des MBS, des obligations adossées à des crédits immobiliers, voir l'[épisode 8](08-cdo-tranches.md)). Elle les paie avec des **réserves qu'elle crée**.

**QT (quantitative tightening, resserrement quantitatif).** L'inverse. La banque centrale réduit la taille de son bilan, soit en ne réinvestissant pas les obligations qui arrivent à échéance (QT passif), soit en les vendant sur le marché (QT actif).

Point important, la banque centrale n'achète pas les obligations directement à l'État. Elle les achète sur le **marché secondaire**, à des investisseurs (fonds de pension, assureurs, banques). Financer directement l'État est interdit à la BCE par les traités européens.

## Ce qui se passe dans les bilans

La Fed achète 1 Md$ de Treasuries à un fonds de pension.

| Acteur | Actif | Passif |
|---|---|---|
| Fed | +1 Md$ de Treasuries | +1 Md$ de réserves (dues à la banque du fonds) |
| Banque du fonds | +1 Md$ de réserves à la Fed | +1 Md$ de dépôt (dû au fonds de pension) |
| Fonds de pension | −1 Md$ de Treasuries, +1 Md$ de dépôt | |

Trois conséquences.

1. Le fonds de pension a échangé une obligation contre du cash.
2. La banque se retrouve avec des réserves nouvelles, créées par la Fed.
3. Le bilan de la Fed a grossi de 1 Md$.

Fais ça pour des milliers de milliards et le système bancaire est inondé de réserves. C'est exactement pour ça que la Fed et la BCE fonctionnent aujourd'hui en **système plancher**, avec le taux de marché collé au taux de dépôt ([épisode 26](26-the-policy-rate.md)).

Le QT fait le chemin inverse. Quand une obligation détenue par la Fed arrive à échéance, le Trésor rembourse la Fed. L'argent sort du compte du Trésor, qui doit réemprunter auprès d'investisseurs privés, et ces investisseurs paient avec des dépôts bancaires. Au bout de la chaîne, des réserves disparaissent.

## Pourquoi ça fait baisser les taux longs

### 1. L'effet prix

Un acheteur énorme arrive sur le marché, le prix des obligations monte, et quand le prix d'une obligation monte, son rendement baisse.

**Exemple.** Une obligation à 10 ans a une [duration](03-duration.md) d'environ 9. Si les achats font monter son prix de 4 % :

```text
baisse de rendement ≈ 4 % / 9 ≈ 0,45 %
```

### 2. Moins de duration disponible (l'effet de rareté)

La banque centrale retire des obligations longues des mains des investisseurs. Ceux qui veulent quand même des actifs longs (un assureur vie doit couvrir des engagements à 30 ans) se battent pour ce qui reste, donc acceptent un rendement plus faible. En pratique, c'est la **prime de terme** qui baisse, le supplément demandé pour bloquer son argent longtemps.

### 3. Le rééquilibrage de portefeuille

Le fonds de pension a maintenant du cash qui ne rapporte presque rien. Il le replace dans des obligations d'entreprises ou des actions. Les [spreads de crédit](05-credit-spread.md) se resserrent et les actions montent. C'est voulu, la banque centrale veut que toute la structure des taux baisse, pas seulement les taux d'État.

### 4. Le signal

Acheter des obligations pendant des années dit au marché que les taux directeurs vont rester bas longtemps. Les anticipations de taux courts futurs baissent, et donc les taux longs aussi.

### Ordres de grandeur

Les études de la Fed sur le premier QE (Gagnon, Raskin, Remache et Sack, 2011) estiment qu'il a fait baisser le taux à 10 ans américain d'environ 0,3 % à 1 %, surtout via la prime de terme. Les effets des programmes suivants sont estimés plus faibles, parce que le marché les anticipait déjà.

## Le QE en chiffres

### Fed

| Programme | Date | Ce qui a été acheté |
|---|---|---|
| QE1 | Nov. 2008 – 2010 | MBS et dette d'agences, puis Treasuries à partir de mars 2009 (environ 1 750 Md$ au total) |
| QE2 | Nov. 2010 – juin 2011 | 600 Md$ de Treasuries |
| QE3 | Sept. 2012 – oct. 2014 | Achats sans montant total fixé, 40 Md$ de MBS par mois, puis + 45 Md$ de Treasuries par mois |
| QE Covid | Mars 2020 – mars 2022 | Achats illimités au départ, puis 120 Md$ par mois |

Le bilan de la Fed passe d'environ 900 Md$ avant 2008 à environ 4 500 Md$ en 2015, puis près de 9 000 Md$ au pic de 2022.

### BCE

- Janvier 2015, lancement de l'APP (asset purchase programme) avec des achats d'obligations d'État, 60 Md€ par mois à partir de mars 2015.
- Mars 2020, PEPP (pandemic emergency purchase programme), enveloppe portée à 1 850 Md€.
- Arrêt des réinvestissements de l'APP en juillet 2023, et du PEPP fin 2024.

### Banque du Japon

Pionnière du QE dès 2001. En 2013, QQE (quantitative and qualitative easing). En 2016, elle ajoute le **yield curve control**, elle vise directement un taux à 10 ans autour de 0 % et achète autant que nécessaire pour le tenir. Elle finit par détenir plus de la moitié de la dette d'État japonaise. Elle sort des taux négatifs et du contrôle de la courbe en mars 2024, avec sa première hausse de taux en 17 ans.

## Le QT en pratique

- **Fed, 2017-2019.** Premier QT, réduction progressive, arrêtée en 2019 (voir le repo de septembre 2019 plus bas).
- **Fed, depuis juin 2022.** QT passif avec des plafonds mensuels montés jusqu'à 95 Md$ par mois (60 Md$ de Treasuries, 35 Md$ de MBS). Le plafond sur les Treasuries est réduit à 25 Md$ en juin 2024 puis à 5 Md$ en avril 2025, et la Fed met fin à la réduction du bilan le 1er décembre 2025.
- **BoE.** Seule grande banque centrale à faire du QT **actif**, en vendant des gilts sur le marché à partir de novembre 2022.

Pourquoi ralentir puis arrêter ? Parce qu'en système plancher, il faut assez de réserves pour que le taux reste collé au plancher. Si on en retire trop, le marché monétaire se tend. C'est exactement ce qui s'est passé en 2019.

## Quand ça a mal tourné

### 1. Le taper tantrum, 2013

**Ce qui s'est passé.** En mai 2013, Ben Bernanke, président de la Fed, dit devant le Congrès que la Fed pourrait **ralentir** ses achats (le "tapering") dans les prochaines réunions. Il ne parle pas d'arrêter, ni de vendre, ni de monter les taux. Le taux américain à 10 ans passe d'environ 1,6 % début mai à près de 3 % en septembre. Les monnaies et les obligations des pays émergents s'effondrent (Inde, Indonésie, Brésil, Turquie, Afrique du Sud, surnommés les "Fragile Five").

**Pourquoi.** Le QE avait écrasé la prime de terme et poussé les investisseurs vers des actifs plus risqués, dont la dette émergente. Le simple signal que l'acheteur principal allait ralentir a suffi pour que le marché réintègre d'un coup la prime de terme et que l'argent sorte des émergents. Le marché réagit aux anticipations, pas aux achats eux-mêmes.

**La leçon.** Sortir du QE se communique très lentement et très à l'avance. Depuis, la Fed annonce ses plans de réduction des mois à l'avance.

### 2. La panique du repo, septembre 2019

**Ce qui s'est passé.** Le 17 septembre 2019, le taux repo overnight américain s'envole. SOFR passe à 5,25 % alors que la fourchette des fed funds est à 2,00 % – 2,25 %, et certaines transactions se font autour de 10 % en séance. Le fed funds effectif sort de sa fourchette par le haut.

**Pourquoi.** Le premier QT avait fait baisser les réserves d'environ 2 800 Md$ (2014) à environ 1 400 Md$. Ce jour-là, deux sorties de cash tombent en même temps. Les entreprises paient leurs impôts trimestriels, et des achats de nouvelles Treasuries sont réglés. Les deux font passer du cash des banques vers le compte du Trésor à la Fed. Les banques qui avaient encore des réserves ne voulaient pas descendre sous leur coussin réglementaire et interne, donc personne ne prêtait. Le système n'avait plus assez de réserves pour fonctionner en mode plancher.

**La réponse.** La Fed injecte du cash via des opérations de repo dès le lendemain, puis recommence à acheter des T-bills (environ 60 Md$ par mois à partir d'octobre 2019) pour reconstituer les réserves. En 2021 elle crée une facilité permanente de repo (la Standing Repo Facility, [épisode 26](26-the-policy-rate.md)).

**La leçon.** Il existe un niveau minimum de réserves, et personne ne sait exactement où il est avant de le toucher. C'est pour ça que le QT de 2022 a été ralenti puis arrêté avant d'y arriver.

### 3. La crise des gilts et des fonds LDI, Royaume-Uni, septembre 2022

**Ce qui s'est passé.** Le 23 septembre 2022, le gouvernement britannique présente un "mini-budget" avec de grosses baisses d'impôts non financées. Les gilts (obligations d'État britanniques) chutent violemment. Le taux à 30 ans passe d'environ 3,7 % à plus de 5 % en quelques jours. Le 28 septembre, la BoE annonce qu'elle va **acheter** des gilts longs, jusqu'à 5 Md£ par jour, alors qu'elle s'apprêtait à commencer à en **vendre** dans le cadre de son QT.

**Pourquoi.** Beaucoup de fonds de pension britanniques à prestations définies utilisaient des stratégies **LDI** (liability-driven investment). Pour couvrir leurs engagements de long terme, ils s'exposaient aux gilts longs avec du levier, via des swaps et du repo. Quand les taux montent violemment, ces positions perdent de l'argent et les contreparties demandent du collatéral supplémentaire (des appels de marge). Pour trouver ce cash, les fonds vendent des gilts, ce qui fait encore monter les taux, ce qui déclenche de nouveaux appels de marge. Une spirale. La BoE intervient comme acheteur de dernier recours pour la casser.

**La réponse.** Achats temporaires du 28 septembre au 14 octobre 2022, environ 19 Md£ au total, et report du début des ventes de QT au 1er novembre. Les règles de levier des fonds LDI ont ensuite été durcies.

**La leçon.** Le QT et la politique budgétaire peuvent se percuter. Et une banque centrale peut se retrouver à faire du QE et du QT en même temps, avec deux objectifs différents (stabilité financière d'un côté, politique monétaire de l'autre).

### 4. Silicon Valley Bank, mars 2023

**Ce qui s'est passé.** SVB, 16e banque américaine, fait faillite le 10 mars 2023 en deux jours de retraits massifs.

**Pourquoi c'est lié au QE.** Pendant le QE Covid, les dépôts bancaires ont explosé (les réserves créées par la Fed finissent en dépôts, voir les bilans plus haut). Les dépôts de SVB ont environ triplé entre 2019 et 2021. SVB a placé une grosse partie de cet argent dans des Treasuries et des MBS longs à taux très bas. Quand la Fed a monté ses taux en 2022, le prix de ces obligations a chuté (c'est la [duration](03-duration.md)). Les pertes latentes atteignaient environ 15 Md$ fin 2022, à peu près l'équivalent de ses fonds propres. Quand SVB a dû vendre une partie de ces titres avec perte pour rembourser des dépôts, les clients ont paniqué et retiré leur argent.

**La leçon.** Le QE crée des dépôts que les banques doivent placer quelque part. S'ils sont placés en obligations longues sans couverture, la sortie du QE et la hausse des taux transforment ça en risque de taux énorme.

### 5. Les pertes des banques centrales

**Ce qui s'est passé.** La Fed affiche des pertes à partir de septembre 2022. Elle les comptabilise en "deferred asset" (un actif différé à rembourser sur ses profits futurs), qui dépasse 200 Md$. La BoE a perdu de l'argent sur son portefeuille de QE, et c'est le Trésor britannique qui couvre ces pertes. La BCE affiche une perte pour 2023, sa première depuis le début des années 2000.

**Pourquoi.** Pendant le QE, la banque centrale a acheté des obligations qui rapportent 1 ou 2 %, et les a financées avec des réserves. Quand elle monte ses taux à 4 ou 5 %, elle paie ce taux sur les réserves (c'est l'IORB, [épisode 26](26-the-policy-rate.md)). Elle reçoit 1-2 % et paie 4-5 %, donc elle perd de l'argent. C'est un carry négatif, comme une banque qui emprunte plus cher qu'elle ne prête.

**Pourquoi ce n'est pas une faillite.** Une banque centrale ne peut pas faire faillite dans sa propre monnaie, puisqu'elle la crée. Le vrai coût est politique et budgétaire. Elle ne verse plus de profits à l'État pendant des années, et ses pertes deviennent un sujet de débat.

## Pièges classiques

- **"Le QE, c'est imprimer des billets."** Non. Le QE crée des réserves, que seules les banques détiennent. Ce n'est pas de la monnaie qui arrive directement dans la poche des ménages. L'effet sur l'inflation passe par les taux et les prix des actifs.
- **"Le QE finance l'État."** Pas directement. Les achats se font sur le marché secondaire. Mais en pratique, le QE rend l'emprunt de l'État moins cher, d'où le débat.
- **"Le QE a provoqué l'inflation de 2021-2022."** Le QE de 2009-2014 n'a pas créé d'inflation. Celle de 2021-2022 vient d'un mélange de chocs (chaînes d'approvisionnement, énergie, gros plans de relance budgétaire, demande post-Covid). Le rôle exact du QE Covid est encore discuté.
- **"Le QT, c'est vendre des obligations."** Le plus souvent non. La Fed et la BCE font du QT passif, elles laissent juste les obligations arriver à échéance.
- **Le stock compte plus que le flux.** Ce qui pèse sur les taux longs, c'est la quantité totale d'obligations détenue par la banque centrale, pas le rythme d'achat du mois.

## L'angle entretien S&T

**"Explique le QE."** La banque centrale achète des obligations sur le marché avec des réserves qu'elle crée. Ça fait monter les prix et baisser les rendements longs, surtout en compressant la prime de terme, ça pousse les investisseurs vers des actifs plus risqués, et ça signale que les taux resteront bas.

**"Quelle différence entre baisser le taux directeur et faire du QE ?"** Le taux directeur agit sur le bas de la courbe, le QE sur le haut. Le QE sert quand le taux directeur est déjà à zéro.

**"Que fait le QT à la courbe ?"** Il remet de la duration sur le marché, donc il pousse la prime de terme et les taux longs à la hausse. Effet de pentification (la courbe se redresse).

**"Pourquoi la Fed a arrêté son QT ?"** Pour ne pas retomber dans une situation de réserves rares comme en septembre 2019, où le repo s'est envolé.

**"Raconte-moi la crise LDI."** Hausse brutale des taux longs après le mini-budget, appels de marge sur les positions à levier des fonds de pension, ventes forcées de gilts, spirale, intervention de la BoE comme acheteur de dernier recours.

**"Pourquoi les banques centrales perdent de l'argent ?"** Elles paient le taux directeur sur les réserves créées pendant le QE, alors que les obligations achetées rapportent beaucoup moins.

## Liens avec les épisodes précédents

- [The Policy Rate](26-the-policy-rate.md), l'outil pour le bas de la courbe, et le système plancher que le QE a créé.
- [The Yield Curve](02-the-yield-curve.md), le QE aplatit la courbe, le QT la pentifie.
- [Duration](03-duration.md) et [DV01](04-dv01.md), pour chiffrer l'effet des achats et les pertes de SVB.
- [Credit Spread](05-credit-spread.md), le rééquilibrage de portefeuille resserre les spreads.
- [Repo](11-repo.md), le marché qui a cassé en septembre 2019.

<div class="ms-takeaway" markdown>

## À retenir

- Le QE, c'est la banque centrale qui achète des obligations avec des réserves qu'elle crée. Le QT, c'est la marche arrière.
- Il sert à faire baisser les taux longs quand le taux directeur est déjà à zéro, surtout en écrasant la prime de terme.
- Il a inondé les banques de réserves, d'où le système plancher actuel.
- Ce qui peut mal tourner. Le simple signal de sortie fait bondir les taux (2013). Trop de QT assèche le repo (2019). Des positions à levier construites sur des taux bas cassent quand les taux montent (LDI 2022, SVB 2023). Et la banque centrale perd de l'argent quand elle monte ses taux.

</div>
