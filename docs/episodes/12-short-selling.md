<p class="ms-kicker">Épisode 12</p>

# Short <span class="ms-outline">Selling.</span>

## Pourquoi cet épisode

Le repo qu'on vient de voir a mentionné des traders empruntant une obligation « special » **pour couvrir une position courte**, sans jamais expliquer ce que ça veut dire. Ce fil se ferme ici.

## Définition

Shorter, c'est **vendre quelque chose que tu ne possèdes pas**, en pariant que son prix va **baisser**, pour le racheter plus tard moins cher.

## Le mécanisme en 4 étapes

1. Tu **empruntes** l'actif à quelqu'un qui le possède.
2. Tu le **vends** immédiatement au prix actuel, tu encaisses.
3. Tu attends que le prix **baisse** (ton pari).
4. Tu le **rachètes** moins cher, tu le rends au prêteur, tu gardes la différence.

## Un mécanisme universel

Ca marche sur **n'importe quel actif** qui se prête et se revend, actions, obligations, devises, matières premières, indices. Seul le nom du « prêt » change selon l'actif :

- **Obligations.** Le **repo** (épisode précédent), emprunter le titre contre du cash en garantie.
- **Actions.** Le **securities lending** (prêt de titres), généralement via le broker qui emprunte à de gros détenteurs institutionnels (fonds de pension, ETF).
- **Devises.** Emprunter une devise pour la vendre contre une autre, en pariant qu'elle va se déprécier.

## Le lien avec le CDS (boucle la série)

On a utilisé l'expression « short le crédit » pour le CDS sans l'expliquer. Acheter un CDS (acheter de la protection) est une façon de parier sur la dégradation d'un actif **sans jamais l'emprunter ni le vendre physiquement**, un short **synthétique**. Le short selling classique vu ici est un short **physique** (on emprunte et vend vraiment le titre). Même pari économique, deux mécaniques différentes pour l'exécuter.

## Le risque de perte illimitée (l'asymétrie fondamentale)

**Position longue classique** (acheter à 100€). Pire scénario, le prix tombe à 0€, perte maximale de 100€. **Perte plafonnée**.

**Position courte** (shorter à 100€). Si le prix **monte** au lieu de baisser :

- à 150€, perte de 50€
- à 500€, perte de 400€
- à 2000€, perte de 1900€

**Aucun plafond**, un prix peut monter à l'infini, contrairement à la baisse bornée à zéro. Asymétrie exactement inverse d'un achat classique.

## Le coût d'emprunt (borrowing fee)

Emprunter le titre n'est pas gratuit, des frais d'emprunt continus sont payés au prêteur, comme un loyer sur le titre. Plus un titre est demandé par les shorteurs (equivalent d'un titre « special » en repo), plus il devient cher et difficile à emprunter, parfois plusieurs dizaines de % annualisés, ce qui grignote le profit potentiel si le pari met du temps à se réaliser.

## La marge et l'appel de marge

Comme la perte est illimitée, le broker exige un dépôt de garantie en cash (**marge**) avant de laisser shorter.

**Exemple.** Short 1 action à 100€ (encaissés), plus marge exigée de 50€ (50% de la position). Coussin total 150€.

Si le prix monte à 130€, perte potentielle de 30€ si rachat immédiat. Le broker surveille en continu si le coussin restant reste au-dessus d'un seuil minimum (**maintenance margin**, souvent ~25-30% de la valeur de position).

Si le coussin tombe sous ce seuil, le broker envoie un **appel de marge** (margin call), demande de déposer plus de cash immédiatement. Sans réponse, le broker **rachète lui-même** la position au prix actuel, sans consentement, pour se protéger. La perte devient définitive à ce moment précis, souvent au pire moment possible.

## Le short squeeze

Mécanisme qui s'auto-alimente. Un actif fortement shorté commence à **monter** au lieu de baisser, les shorteurs perdent de l'argent, certains sont appelés en marge et forcés de racheter pour clôturer. Ce rachat massif fait **encore plus monter le prix**, ce qui déclenche d'autres appels de marge, boucle qui s'auto-alimente.

## Cas réel, GameStop, janvier 2021

Action massivement shortée par de gros hedge funds (Melvin Capital notamment). Une communauté de traders particuliers (Reddit WallStreetBets) a repéré ce fort taux de short et acheté massivement. Prix passé de **~20$ à près de 500$** en quelques semaines, forçant les fonds shortés à racheter à pertes colossales (Melvin Capital, pertes de plusieurs milliards, renfloué en urgence).

<div class="ms-takeaway" markdown>

## À retenir

Shorter = parier à la baisse sur n'importe quel actif, en l'empruntant, le vendant, puis le rachetant moins cher. Perte théoriquement illimitée (contrairement à l'achat classique), coût d'emprunt continu, et risque d'être forcé de racheter au pire moment si le marché tourne contre soi (squeeze).

</div>
