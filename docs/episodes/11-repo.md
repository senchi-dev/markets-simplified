<p class="ms-kicker">Épisode 11</p>

# Repo <span class="ms-outline">(Repurchase Agreements).</span>

## Définition

Un repo (repurchase agreement) est un **prêt garanti à très court terme** (souvent overnight), déguisé juridiquement en deux transactions de vente d'obligations.

- **Aujourd'hui.** Partie A vend une obligation à Partie B, reçoit du cash en échange.
- **Demain (ou dans quelques jours).** Partie A rachète la même obligation à Partie B, à un prix légèrement plus élevé.

Cette petite différence de prix est l'intérêt du prêt, déguisé en écart de prix entre deux ventes. Économiquement, l'obligation n'est jamais vraiment vendue, elle sert de **collatéral** pour emprunter du cash pendant une courte période.

## Le taux EST l'écart de prix, pas un frais séparé

Le taux repo (overnight) n'est pas « taux + collatéral » comme deux choses distinctes. Le collatéral garantit le prêt, et le taux d'intérêt est entièrement exprimé par l'écart entre prix de vente et prix de rachat.

**Formule.** `Prix de rachat = Prix de vente × (1 + taux repo × jours/360)`

**Exemple.** Vente à 100€ aujourd'hui, taux repo annualisé 5%, overnight (1 jour, convention jours/360).

`Prix de rachat = 100 × (1 + 5% × 1/360) = 100,0139€`

Ces 0,0139€ en plus correspondent exactement à un jour d'intérêt à 5% annualisé sur 100€.

## Pourquoi ce n'est PAS équivalent à juste vendre l'obligation

Le point le plus important. Dans un repo, **le prix de rachat est fixé à l'avance**, dès la signature. Peu importe ce que fait le prix de marché de l'obligation entre-temps, ça ne change rien au prix de rachat convenu.

- **Partie A** (qui donne l'obligation, reçoit le cash) garde **tout le risque de prix** de l'obligation pendant toute l'opération.
- **Partie B** (qui prête le cash, reçoit l'obligation) ne prend **jamais** de risque de prix sur l'obligation, elle touche juste son taux repo garanti.

Un achat ferme exposerait l'acheteur au risque de prix pendant toute la détention, ce qui n'est pas ce qu'il veut s'il place juste du cash excédentaire pour une nuit avec un rendement sûr. Le repo **sépare volontairement** « emprunter/prêter du cash » de « prendre un risque de prix sur l'obligation ».

## Repo rate vs taux interbancaire, deux marchés différents

- **Taux interbancaire.** Les banques se prêtent entre elles **sans collatéral** (en blanc, sur la confiance/le risque de contrepartie).
- **Taux repo.** Prêt **garanti** par un collatéral (une obligation).

Comme le repo est sécurisé, le risque est plus faible qu'un prêt interbancaire non garanti, donc **le taux repo est généralement plus bas** que le taux interbancaire.

**Lien direct avec l'épisode IRS.** SOFR, utilisé dans tous les exemples de l'épisode précédent, n'est **pas** un taux interbancaire, c'est littéralement un **taux repo**. SOFR = **Secured** Overnight Financing Rate, « secured » (garanti/sécurisé) parce qu'il est calculé à partir de vraies transactions repo overnight, des prêts adossés à un vrai collatéral obligataire, sur le marché du Trésor US.

Différent de l'ancien **LIBOR**, qui était **unsecured** (non garanti), un petit panel de banques déclarait simplement le taux auquel elles pensaient pouvoir se prêter entre elles, sans aucune vraie transaction ni collatéral derrière ce chiffre. Des banques ont été prises à déclarer de faux taux pour profiter de leurs propres positions, le scandale de manipulation du LIBOR, ce qui a poussé le marché vers un taux basé sur de vraies transactions sécurisées.

## Comment se marché fonctionne en pratique

Pas juste deux acteurs isolés au téléphone. Marché liquide avec un taux de référence public très suivi, le **GC rate** (General Collateral rate). Banques, fonds monétaires, dealers, et la banque centrale y participent chaque jour en très grande taille.

- **Tri-party repo.** Un agent tiers (ex. BNY Mellon) gère la garde du collatéral et le règlement entre plein de participants, standardisé.
- **Compensation centrale (FICC).** De plus en plus de repo passe par une chambre de compensation centrale, comme les swaps.

## GC vs Special, deux régimes de taux

- **General Collateral (GC) rate.** Taux « normal », quand n'importe quelle obligation d'État standard fait l'affaire comme collatéral.
- **Special.** Certaines obligations précises sont en très forte demande (souvent des traders qui en ont besoin pour couvrir une position courte). Pour l'obtenir, les prêteurs de cash acceptent un taux anormalement bas, parfois proche de zéro ou négatif, juste pour mettre la main sur ce titre précis.

## Ce qui fixe le taux repo au quotidien

`Taux repo = ancré par le taux directeur de la banque centrale (plancher/plafond via facilités permanentes) + ajusté en continu par l'offre/demande réelle de cash vs collatéral + peut diverger fortement si le collatéral est « special »`

## Cas réel, septembre 2019

Une combinaison de grosses échéances fiscales et d'un règlement massif d'émissions du Trésor US a asséché le cash disponible d'un coup. Le taux repo overnight a explosé jusqu'à **10%** en une nuit, contre ~2% habituellement. La Fed a dû intervenir en urgence en injectant massivement des liquidités.

## Contexte Maroc (pour information, pas dans le post LinkedIn)

Au Maroc, le repo s'appelle **pension livrée**, encadré par la **Loi 24-01** (2004). Bank Al-Maghrib l'utilise comme outil principal de politique monétaire (avances à 7 jours pour injecter, pensions livrées pour retirer de la liquidité), avec un marché privé interbancaire très mince en comparaison (BAM ≈ 156,6 Mds MAD/jour d'intervention vs ~1,7 Md MAD/jour de marché interbancaire libre). Lancement récent (février 2025) d'un marché à terme interbancaire avec l'indice **MONIA**, l'équivalent marocain du SOFR. Sources primaires, [bkam.ma](http://bkam.ma) et [ammc.ma](http://ammc.ma).

<div class="ms-takeaway" markdown>

## À retenir

Le repo n'est pas une vente, c'est un prêt garanti où le prix de rachat fixe à l'avance sépare le financement (cash contre collatéral) du risque de prix (qui reste chez le propriétaire d'origine). C'est le marché qui fait tourner le financement à court terme de tout le système bancaire, et sa référence moderne (SOFR) en est directement issue.

</div>
