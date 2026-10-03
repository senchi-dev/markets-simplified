# 7. CDS Indices (CDX & iTraxx)

## L'idée de départ

Un CDS single-name (vu dans la fiche précédente) protège **une seule** entreprise. Mais si un gérant détient un portefeuille diversifié d'obligations et veut se couvrir contre une dégradation **générale** du crédit, acheter 20 ou 100 CDS séparés serait lent, illiquide et coûteux en frais de transaction. La solution, **un seul contrat qui référence tout un panier d'entreprises d'un coup.**

## Définition

Un **indice CDS** est un contrat unique et standardisé qui référence un **panier fixe** de noms (entreprises), chacun pesant le même poids (ex. 1/125 pour un indice à 125 noms). C'est littéralement un portefeuille de mini-CDS empaqueté dans un seul instrument liquide.

## Les deux grandes familles

| Famille | Zone géographique | Exemples |
| --- | --- | --- |
| **CDX** | Amérique du Nord | CDX IG (125 noms investment grade), CDX HY (100 noms high yield) |
| **iTraxx** | Europe / Asie | iTraxx Main (125 noms IG européens), iTraxx Crossover (75 noms plus risqués) |

## IG vs HY, en détail

Les agences de notation (S&P, Moody's, Fitch) notent la solidité de crédit d'un emprunteur, comme un bulletin scolaire.

- **Investment Grade (IG)**, de **AAA** (le plus sûr) jusqu'à **BBB−**. Faible risque de défaut (États solides, grandes capitalisations comme Apple ou Nestlé). Spread bas.
- **High Yield (HY)**, aussi appelé **"junk"**, **BB+ et en dessous**. Risque de défaut plus élevé, donc rendement exigé plus élevé pour compenser (d'où le nom "high yield"). Spread nettement plus large et plus volatil.

**La frontière BBB−/BB+ est critique.** Une entreprise dégradée de BBB− à BB+ devient un **"fallen angel"**. Beaucoup de fonds n'ont légalement/statutairement le droit de détenir que de l'IG, ils sont **forcés de vendre** en urgence, ce qui amplifie mécaniquement la chute du prix de cette dette. Un des mécanismes de contagion les plus connus des marchés de crédit.

## La mécanique du contrat

Identique à un CDS classique, l'acheteur paie le **spread de l'indice**, le vendeur paie en cas de défaut d'un des noms du panier.

**La vraie différence avec le single-name.** Quand **un seul** nom du panier fait défaut, il est **retiré** de l'indice, le vendeur paie pour le poids de ce nom uniquement (ex. 1/125 du notionnel total), et le contrat **continue** sur les noms restants, avec un notionnel réduit d'autant. Un défaut ne tue pas tout le contrat, il en grignote juste une tranche.

## Pourquoi le coût ne dépend PAS du nombre de noms

Point souvent mal compris, le premium payé **ne dépend pas** du nombre de noms dans le panier (125 ou 5), il dépend du **notionnel choisi** par l'acheteur et de la **qualité de crédit moyenne** du panier.

**Exemple.** Un gérant avec un portefeuille de 20 obligations pour un total de 20 M€ achète 20 M€ de notionnel de CDX IG à 70 bps de spread. Coût = 0,70% × 20 M€ = **140 000€/an**, un seul chiffre, un seul trade, qui couvre tout son portefeuille contre une dégradation générale du marché du crédit. Ajouter des noms au panier de référence n'augmente jamais ce coût, ça change seulement la diversification du risque référencé, pas le prix par euro protégé.

C'est aussi l'option **la moins chère** pour un hedge large, car les indices sont bien plus liquides (spread bid-ask serré) que 20 CDS single-name achetés séparément, certains de ces 20 émetteurs pourraient même ne pas avoir de CDS liquide du tout.

## Risque systématique vs risque idiosyncratique (le point clé à ne jamais confondre)

L'indice **ne paie presque rien** sur le défaut d'un seul nom, chaque nom ne pèse que ~0,8% du panier (1/125). Ce n'est donc **pas** l'outil pour couvrir une entreprise précise.

- **Risque idiosyncratique** (une entreprise précise fait défaut, indépendamment du reste du marché), il faut un **single-name CDS** sur ce nom précis. C'est le cas typique quand une banque prête une grosse somme concentrée à une seule contrepartie, elle veut un hedge 1:1 sur ce nom, pas un hedge dilué sur 124 autres entreprises qui ne l'intéressent pas.
- **Risque systématique** (tout le marché du crédit se dégrade en même temps, ex. récession, choc de taux, risk-off généralisé), l'**indice** est l'outil adapté.

Si une des obligations détenues fait défaut et qu'elle n'est pas dans l'indice (ou même si elle y est), l'indice ne compense presque pas cette perte précise. La vraie protection ne vient pas des payouts de défaut individuels, mais du **mark-to-market**, quand le crédit se dégrade largement, les obligations détenues perdent de la valeur ET la protection sur l'indice en gagne (son spread s'écarte aussi), les deux mouvements se compensent globalement.

Règle pratique retenue en gestion de portefeuille, un gérant sérieux combine souvent les deux outils, l'indice pour couvrir le fond diversifié du portefeuille (risque de marché), et des single-names ciblés sur les 2-3 noms qui l'inquiètent spécifiquement (risque idiosyncratique).

## Pourquoi c'est un outil si central sur les marchés

- **Liquidité.** Bien plus liquide que n'importe quel single-name, c'est la façon la plus simple de trader le crédit comme une classe d'actifs à part entière.
- **Baromètre macro, le "VIX du crédit".** Le VIX mesure la volatilité implicite anticipée du S&P 500 à partir des prix des options, un thermomètre de la peur sur les actions. Le spread d'un indice CDS joue exactement le même rôle pour le crédit, un seul chiffre qui capture en temps réel le niveau de stress perçu sur tout le marché de la dette d'entreprise. Spread qui s'écarte fortement, signal de risk-off généralisé.
- **Hedging en un seul trade.** Couvrir tout un book de crédit en une seule opération plutôt que des dizaines.
- **Exprimer une vue macro.** "Je pense que le crédit va se dégrader" se traduit directement en achat de protection sur l'indice, sans avoir à sélectionner des noms individuels.

## Les rolls (renouvellement semestriel)

La composition de l'indice n'est pas figée pour toujours. Tous les **6 mois** (dates fixes, **20 mars** et **20 septembre**), une **nouvelle série** est lancée avec une liste de noms mise à jour.

- Les noms dégradés ou devenus illiquides sont retirés, de nouveaux noms peuvent entrer.
- Chaque série a un numéro (Series 40, 41, 42...).
- La série la plus récente est dite **"on-the-run"**, c'est là que se concentrent toute la liquidité et le volume de trading.
- Les séries précédentes deviennent **"off-the-run"**, toujours valides contractuellement, mais bien moins liquides, spread plus large.
- **"Roller" une position** veut dire migrer d'une ancienne série vers la nouvelle série on-the-run pour rester dans la version liquide du marché.

Analogie, exactement comme il existe toujours un Treasury 10 ans "actuel" fraîchement émis (on-the-run, très liquide), pendant que les émissions précédentes deviennent off-the-run (moins tradées).

## Contexte historique

Les indices CDS ont joué un rôle central lors de la crise de **2008** (paris massifs sur la dégradation généralisée du crédit) et lors de l'affaire de la **"London Whale"** (JPMorgan, plus de 6 milliards $ de pertes en 2012 sur des positions CDX IG mal gérées), un excellent exemple concret pour illustrer à quel point ces instruments, bien que conçus pour le hedging, peuvent aussi devenir des paris directionnels à très fort effet de levier.

### Le détail du mécanisme (comment ils ont vraiment perdu l'argent, sans aucun défaut)

Le CIO de JPMorgan avait **vendu de la protection** sur le CDX.IG.9, ce qui les rendait **long le crédit** (en convention de marché, "acheter l'indice" = vendre la protection = long crédit, exactement comme détenir l'obligation elle-même). Des hedge funds ont repéré que la taille de leur position distordait le prix de cet indice off-the-run, et ont pris le côté opposé (acheté de la protection, **short le crédit**), pariant que le spread allait s'écarter.

Le spread s'est effectivement écarté (100 bps → 140 bps dans l'exemple pédagogique). Même mécanique que le prix d'une obligation à taux fixe quand les yields montent, JPMorgan restait bloqué à encaisser l'ancien spread bas pendant que le marché en exigeait un plus élevé pour le même risque. Leur position, réévaluée au prix de marché (mark-to-market), affichait une perte de plusieurs milliards **sans qu'aucun des 125 noms n'ait fait défaut**. En essayant de défendre leur prix en rajoutant encore plus de taille, ils ont amplifié le problème avant de finalement couper la position, plus de 6,2 milliards $ de pertes au total.

## À retenir

Single-name CDS couvre **une** entreprise précise. Indice CDS couvre (ou parie sur) **tout un marché** en un seul contrat, avec un coût qui dépend du notionnel choisi, pas du nombre de noms référencés.
