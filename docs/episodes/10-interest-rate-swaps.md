<p class="ms-kicker">Épisode 10</p>

# Interest Rate Swaps <span class="ms-outline">(IRS).</span>

## Définition

Un IRS est un contrat entre deux parties qui échangent des paiements d'intérêts sur un **notionnel** pendant une durée fixée. Aucun capital n'est jamais échangé, le notionnel sert uniquement de base de calcul, exactement comme pour le CDS.

- **Partie A** paie un **taux fixe**.
- **Partie B** paie un **taux variable** (indexé sur un taux de référence comme le SOFR).

À chaque date de paiement, seule la **différence** entre les deux montants est réellement versée (netting), pas les deux montants complets séparément.

## Exemple chiffré complet

Notionnel 10 M€, paiement tous les 6 mois.

**Semestre 1, SOFR à 4%.**

- Partie A doit 3% × 10M / 2 = 150 000€.
- Partie B doit 4% × 10M / 2 = 200 000€.
- Net, Partie B verse 50 000€ à Partie A.

**Semestre 2, SOFR à 2%.**

- Partie A doit toujours 150 000€ (fixe, ne change jamais).
- Partie B doit 100 000€.
- Net, Partie A verse 50 000€ à Partie B.

Le notionnel de 10M ne bouge jamais, seule la petite différence s'échange à chaque date.

## Le cas d'usage complet, une entreprise qui se couvre

Une entreprise a un vrai prêt bancaire à taux variable (SOFR + 1%) sur 10M€, emprunté variable car moins cher à l'émission (rappel épisode 1). Elle entre dans un swap en **payant fixe (3%)** et **recevant variable (SOFR)**.

En combinant ses deux flux :

- Sur son prêt réel, elle paie SOFR + 1%.
- Sur le swap, elle reçoit SOFR (annule le SOFR payé sur le prêt) et paie 3% fixe.

Le SOFR s'annule parfaitement des deux côtés, il ne reste que **3% + 1% = 4% fixe**, tout le temps, peu importe ce que fait le SOFR ensuite. Elle a transformé un coût variable et imprévisible en coût fixe et prévisible, sans jamais toucher à son prêt réel.

## Pourquoi pas emprunter fixe directement

Plusieurs raisons se cumulent.

**1. Le coût total.** Le taux fixe direct est généralement plus cher à l'émission (rappel épisode 1, prime de certitude). Emprunter variable puis swapper en fixe peut coûter **moins cher au total** que d'emprunter fixe directement.

**2. L'avantage comparatif.** Théorie classique, deux entreprises différentes ont chacune un accès relatif meilleur à un marché différent (l'une au fixe, l'autre au variable). Si chacune emprunte là où elle a l'avantage puis échange via un swap contre ce qu'elle veut vraiment, les deux ressortent gagnantes par rapport à un emprunt direct dans le type de taux souhaité.

**3. La flexibilité.** On peut swapper seulement une partie du notionnel, seulement pour une période donnée, ou sortir du swap indépendamment du prêt sous-jacent. Un prêt fixe classique est tout ou rien, et souvent assorti de pénalités de remboursement anticipé lourdes.

**4. L'accès au marché.** Émettre une obligation à taux fixe nécessite d'accéder aux marchés de capitaux (coûts fixes élevés), rentable seulement pour de grosses levées. Un prêt variable est plus accessible, le marché des swaps est liquide et peu coûteux à utiliser ensuite.

## Terminologie, payer swap vs receiver swap

Le nom du swap se base toujours sur ce qu'on fait avec la jambe **fixe**, jamais la variable.

- **Payer swap.** On paie le fixe, on reçoit le variable.
- **Receiver swap.** On reçoit le fixe, on paie le variable.

## Pourquoi une contrepartie prend l'autre côté

Trois profils possibles.

1. **Le miroir exact.** Une entreprise avec une vraie dette fixe qui veut la convertir en variable (matching actif-passif).
2. **Un pari directionnel.** Une partie qui pense que les taux vont baisser entre en receiver swap (encaisse le fixe, paie un variable qu'elle anticipe plus bas).
3. **Le cas le plus fréquent, la banque market maker.** Le terme exact pour ce rôle est **market maker** (teneur de marché), une institution qui gagne de l'argent en facilitant des trades et en captant de petits écarts de prix, pas en prédisant la direction des taux. La banque prend l'autre côté du trade, encaisse une petite marge (bid-ask spread), puis va immédiatement trouver une contrepartie inverse ailleurs pour neutraliser son propre risque. Elle vit du spread et du volume, pas d'un pari directionnel.

## Ce que gagne la banque, précisément

Pas un « premium » comme pour le CDS (qui rémunère un vrai risque de crédit pris). La banque cote un taux fixe légèrement moins bon pour le client que le taux « juste » du marché (ex. 3,05% au lieu de 3,00%), intégré directement dans le taux proposé, pas affiché comme des frais séparés. Elle se couvre ensuite immédiatement avec un trade opposé ailleurs, son profit se résume au petit écart capturé entre les deux trades.

## Le cadre juridique

Même organisation que pour le CDS, l'**ISDA**. Les deux parties signent une fois un **ISDA Master Agreement** (règles générales), puis une **Confirmation** courte pour chaque nouveau swap (les termes spécifiques, notionnel, taux fixe, référence variable, durée). Aucun argent n'est échangé à la signature.

## Comment ça s'exécute concrètement

**Historiquement**, tout se négociait par téléphone (voice trading) entre le trésorier et le desk de la banque, encore le cas aujourd'hui pour les trades gros ou sur-mesure.

**Aujourd'hui**, la majorité des swaps standards passent par des plateformes électroniques via un processus **RFQ (Request For Quote)** : l'entreprise envoie sa demande simultanément à plusieurs banques (via Bloomberg, Tradeweb, MarketAxess), les banques répondent avec leur prix en quelques secondes, l'entreprise clique pour exécuter avec la meilleure offre.

Depuis 2008, les régulateurs (Dodd-Frank aux US, EMIR en Europe) ont poussé les swaps standardisés vers des plateformes électroniques obligatoires (SEFs) et une compensation centrale (LCH SwapClear), pour plus de transparence après le rôle des dérivés OTC opaques dans la crise.

<div class="ms-takeaway" markdown>

## À retenir

Un IRS ne supprime pas le prêt sous-jacent, il superpose un deuxième contrat qui transforme son exposition, variable en fixe ou l'inverse, sans jamais toucher au capital emprunté. Le coût de cette transformation est un petit spread caché dans le taux proposé, la contrepartie de la banque pour fournir la certitude recherchée.

</div>
