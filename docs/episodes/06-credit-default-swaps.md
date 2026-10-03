<p class="ms-kicker">Épisode 06</p>

# Credit Default Swaps <span class="ms-outline">(CDS).</span>

## Définition

Un **CDS (Credit Default Swap)** est une **assurance contre le défaut** d'une entité (entreprise ou État). L'acheteur de protection paie une prime régulière, en échange, si l'entité de référence fait défaut, le vendeur de protection lui rembourse la perte. Cela permet de **trader le risque de crédit directement**, sans jamais avoir besoin de détenir l'obligation sous-jacente.

**Analogie complète.** C'est exactement une assurance auto. Tu paies une prime chaque année (peu importe s'il ne se passe rien), si tu as un accident (le défaut), l'assureur te rembourse. La différence avec une vraie assurance, tu peux acheter un CDS sur une entreprise **même si tu ne lui as jamais prêté d'argent**, c'est ce qu'on appelle un "naked CDS", acheter une assurance sur la maison du voisin. Célèbre pour son rôle dans la crise de 2008, les banques pariaient sur le défaut d'entités sans forcément détenir leur dette.

## Les deux parties du contrat

- **Protection buyer (acheteur de protection).** Celui qui veut se couvrir (ou parier sur une dégradation du crédit). Il paie la prime.
- **Protection seller (vendeur de protection).** Celui qui prend le risque en échange de la prime, pariant que l'entité ne fera pas défaut. Il encaisse la prime tant que rien n'arrive, mais doit payer un gros montant en cas de défaut.

## Les deux "legs" (jambes) du contrat

Un CDS repose sur deux flux de paiement opposés.

### 1. Premium leg (jambe de la prime)

L'acheteur paie une prime régulière (trimestrielle ou annuelle selon le contrat) au vendeur, tant que rien ne se passe. Cette prime, exprimée en bps par an du notionnel, **est le CDS spread**. Flux petit, prévisible, répété.

### 2. Contingent leg (jambe conditionnelle)

"Contingent" veut dire conditionnel, ce paiement n'a lieu **que si** un événement de crédit (credit event) se produit. Si l'entité fait défaut, le vendeur fait **un seul paiement** au buyer pour couvrir sa perte. Ce flux arrive zéro fois (rien ne se passe) ou une fois (défaut).

## Qu'est-ce qu'un "credit event" exactement ?

Les contrats CDS sont standardisés par l'**ISDA** (International Swaps and Derivatives Association). Les événements de crédit qui déclenchent un paiement incluent typiquement la **bankruptcy** (faillite), la **failure to pay** (défaut de paiement d'un coupon ou du principal), et le **restructuring** (restructuration forcée de la dette, ex. baisse du principal ou des coupons imposée aux créanciers).

Un comité ISDA (Determination Committee) décide officiellement si un credit event a eu lieu, ce qui déclenche le processus de règlement.

## Le payout (règlement du contrat)

`Payout = (1 − Recovery rate) × Notionnel`

Le **notionnel** est le montant de dette que le contrat couvre, la base de calcul, personne n'échange ce montant directement, il sert juste à calculer la prime et le payout. Le **recovery rate** est ce que le créancier récupère via la **liquidation** des actifs de l'entreprise en défaut (bâtiments, stocks, brevets, cash...). Le CDS couvre **le reste**, c'est-à-dire la vraie perte.

**Exemple.** Tu es dû 100€. Recovery rate = 40%, tu récupères 40€ via la liquidation, tu perds réellement 60€. Le CDS paie ces 60€ (= (1 − 40%) × 100€).

## Recovery rate, hypothèse de modèle vs réalité du marché (piège classique)

Il y a **deux recovery rates différents**, à ne pas confondre.

1. **Le 40% "standard"** est une **convention de marché** utilisée pour *estimer/pricer* un CDS avant tout défaut réel, une moyenne historique observée sur la dette senior d'entreprise.
2. **Le recovery rate réel** est déterminé au moment du vrai défaut par une **enchère organisée (auction ISDA)**, où le marché fixe collectivement la vraie valeur de récupération. Ce chiffre peut être très différent du 40% supposé (parfois 60%, parfois 5%).

**Le CDS paie toujours sur le recovery RÉEL, jamais sur le 40% théorique.**

### Si tu es couvert, tu es protégé contre la vraie perte, quel que soit le recovery réel

Si tu détiens l'obligation **et** tu as acheté un CDS dessus, deux scénarios possibles.

- Recovery réel = 40% → l'obligation perd 60, le CDS paie 60, net = 0.
- Recovery réel = 0% (pire que prévu) → l'obligation perd 100, le CDS paie **100** (car il paie (1−0%) = 100%), net = 0 quand même.

Le CDS te rembourse ta perte **réelle**, pas une perte basée sur une hypothèse figée. C'est ce qui fait sa valeur en tant que couverture.

## Asset ou liability ? (le sens comptable du CDS)

Un CDS est un dérivé dont la valeur évolue selon le côté où tu es et selon les mouvements de spread.

- **Acheteur de protection.** Si le spread de crédit s'écarte (le risque perçu augmente), la position **gagne de la valeur** pour lui, c'est un **asset**.
- **Vendeur de protection.** Dans ce même scénario, il doit de plus en plus de valeur en face, c'est une **liability** pour lui.

Logique d'assurance classique, pour l'assuré avec un sinistre, la police vaut de l'or, pour l'assureur, c'est une dette qu'il doit honorer.

## Le CDS spread, comment il est fixé

Le CDS spread n'est pas arbitraire, il est fixé pour que le contrat soit **juste (fair)** au moment de la signature, ce que le buyer paie en moyenne doit égaler ce que le seller s'attend à payer.

## CDS spread vs Credit spread obligataire, et le "basis"

Les deux mesurent le **même** risque de crédit sous-jacent, donc ils restent proches par **arbitrage** (si l'écart devient trop grand, des traders achètent l'un et vendent l'autre pour capter le profit, ce qui les recolle).

**CDS-bond basis = CDS spread − Credit spread obligataire.** C'est littéralement "le spread entre les deux spreads".

- Basis proche de 0, les deux marchés sont d'accord.
- Basis différent de 0, il y a des frictions réelles, l'obligation peut être illiquide, difficile à shorter, ou avoir des coûts de financement différents du CDS.

**Le CDS est un signal plus "pur"** du risque de crédit, il n'a pas besoin de l'obligation (pas de coût de financement pour la détenir), ce qui élimine une partie du bruit de liquidité qu'on retrouve dans le credit spread obligataire classique.

## La probabilité de défaut implicite (sans aucune statistique)

La logique est celle du **point d'équilibre (break-even)**, ce que le vendeur encaisse en moyenne doit égaler ce qu'il s'attend à payer.

`Spread = PD × (1 − Recovery)`, où **PD** veut dire **Probability of Default** (probabilité de défaut annuelle).

On isole PD en divisant les deux côtés par (1 − Recovery).

`PD = Spread ÷ (1 − Recovery)`

**Exemple complet.**

- Spread = 3% (300 bps)
- Recovery = 40%, donc (1 − Recovery) = 60%
- `PD = 3% ÷ 60% = 5%` de probabilité de défaut implicite par an.

**Check d'intuition (sans formule).** Tu paies 3€/an, si défaut, on te verse 60€. Pour que payer 3 soit "juste" face à recevoir 60, il faut que la chance de défaut soit environ 3/60 = 1/20 = **5%**. Un prix de marché se traduit directement en probabilité.

<div class="ms-takeaway" markdown>

## À retenir

Un CDS permet de prendre une vue sur le risque de crédit **sans jamais détenir l'obligation**, et son prix (le spread) est littéralement **l'estimation du marché** de la probabilité de défaut d'une entité.

</div>

> Suite logique, **CDS Indices (CDX & iTraxx)**, le même principe, mais appliqué à un panier de 125 entreprises en un seul contrat.
