# 8. CDO Tranches

## L'idée de départ

Un CDO (Collateralized Debt Obligation) prend un grand pool de prêts ou d'obligations (des centaines ou des milliers de prêts immobiliers par exemple) et le découpe en tranches de risque différent. C'est l'instrument central de la crise de 2008 et du film *The Big Short*.

## Le pool vs le CDO, une distinction importante

Le **pool** désigne uniquement les actifs sous-jacents eux-mêmes (les 1000 prêts). Le **CDO** désigne la structure entière. Une banque crée un **SPV** (Special Purpose Vehicle, une entité juridique séparée) qui achète et détient le pool, puis émet les tranches vendues aux investisseurs. Le schéma complet, pool détenu par le SPV, le SPV émet les tranches, les tranches vendues aux investisseurs forment le CDO.

## Les tranches, toutes sur le même pool

Point souvent mal compris, une tranche n'est **pas** liée à un sous-ensemble spécifique de prêts. **Toutes** les tranches ont une créance sur le **même pool entier**. La différence entre elles n'est pas « quels prêts » mais l'**ordre de priorité** pour recevoir l'argent et pour absorber les pertes de ce pool commun.

Analogie, un immeuble avec une inondation qui monte progressivement. Ce n'est pas que chaque appartement a son propre risque d'eau distinct, c'est la même eau, le même bâtiment, mais l'appartement du rez-de-chaussée (l'equity) est touché en premier, celui du dernier étage (super senior) seulement si l'eau monte très haut.

## Les tranches, du plus risqué au plus sûr

- **Equity tranche.** Absorbe les premières pertes. Risque le plus élevé, rendement le plus élevé.
- **Mezzanine tranche.** Absorbe les pertes seulement une fois l'equity totalement consommée. Risque moyen, rendement moyen.
- **Senior / Super senior tranche.** Ne prend des pertes que si tout ce qui est en dessous a été consommé. Risque le plus faible, rendement le plus faible.

## Attachment et detachment points

Chaque tranche est définie précisément par des points d'attachement/détachement, la plage de pertes du pool (en %) où elle commence et arrête d'encaisser des pertes. Chaque tranche est un titre séparé (son propre code d'identification, sa propre notation, son propre coupon), documenté dans le prospectus dès l'émission, ce n'est jamais ambigu ni déterminé après coup.

Exemple sur un pool de 100 M€ de pertes potentielles.

| Tranche | Attachment - Detachment | Notation typique |
| --- | --- | --- |
| Equity | 0% - 3% | non notée |
| Mezzanine | 3% - 7% | BBB |
| Senior | 7% - 15% | AA |
| Super senior | 15% - 100% | AAA |

## Le waterfall

Les flux de cash entrants et les pertes fonctionnent comme une cascade (waterfall). Les paiements coulent vers la tranche du haut en premier (super senior payée en premier). Les pertes touchent la tranche du bas en premier (equity touchée en premier).

## Le point clé, la corrélation entre les prêts sous-jacents

Cette structure ne crée une vraie sécurité pour la tranche senior que si les prêts sous-jacents du pool ne sont **pas trop corrélés** entre eux. Ce n'est pas les tranches entre elles qui doivent être peu corrélées (elles sont séquentielles par construction), c'est le risque de défaut entre les prêts individuels du pool.

**Scénario A, corrélation faible.** 100 prêts dans des villes et secteurs différents, des défauts quasiment indépendants les uns des autres. Avoir des dizaines de défauts simultanés est statistiquement très rare. Les pertes restent contenues dans l'equity, la senior n'est presque jamais touchée. La notation AAA est justifiée.

**Scénario B, corrélation forte (la réalité de 2008).** Les prêts étaient tous des subprimes US, tous exposés au même facteur unique, le prix de l'immobilier américain. Ce n'était pas 100 paris indépendants mais un seul gros pari déguisé en 100 petits paris. Quand les prix ont chuté partout en même temps, les défauts sont arrivés en vague massive et simultanée, traversant l'equity, la mezzanine, et touchant même la senior et la super senior.

Les agences de notation ont noté ces CDO comme si c'était le Scénario A, alors que la réalité économique était le Scénario B. C'est un des mécanismes centraux de la crise de 2008, et le pari exact que Michael Burry et d'autres ont pris dans *The Big Short*.

## Comment on achète concrètement

On choisit un CDO précis, on choisit une tranche précise dans ce CDO, et on l'achète en payant son prix d'entrée, exactement comme une obligation. En échange, on reçoit des coupons réguliers financés par les paiements du pool.

## Comment on perd de l'argent, deux mécanismes distincts

**1. La perte réelle (write-down).** Si les défauts sont assez nombreux pour manger toutes les tranches en dessous de la sienne et commencer à toucher la sienne, la tranche subit un write-down, le montant dû est réduit. On ne récupère pas tout son capital à l'échéance, et/ou les coupons sont réduits ou coupés.

**2. La perte de valeur avant tout défaut (mark-to-market).** Même mécanisme que pour le CDS et le London Whale. Si le marché commence à croire que les pertes vont probablement atteindre une tranche donnée, le prix de cette tranche sur le marché secondaire chute, même si aucun défaut réel ne l'a encore touchée. Tant qu'aucun write-down réel n'a eu lieu, le coupon reste identique (fixé sur le notionnel d'origine), seul le cours de revente chute.

## Perte réalisée vs non réalisée

Tant qu'on ne vend pas, la chute de cours n'est qu'une perte sur le papier (non réalisée). Si on garde la tranche jusqu'à maturité et que les défauts n'atteignent jamais vraiment cette tranche, on touche tous les coupons prévus et on récupère le capital intégral, la chute de cours n'a jamais eu d'impact réel. La perte ne devient vraie que si on vend au mauvais moment, ou si un vrai write-down finit par arriver.

**Le piège comptable de 2008.** Les banques et fonds sont obligés comptablement de valoriser leurs positions au prix de marché actuel (mark-to-market en comptabilité), même sans intention de vendre. Dès que les cours se sont effondrés, ces institutions ont dû afficher des pertes énormes immédiatement, déclenchant appels de marge et ventes forcées, transformant une perte de papier en perte bien réelle. Un des mécanismes qui a transformé une crise de crédit en crise de liquidité généralisée.

## À retenir

Un CDO ne supprime pas le risque, il réorganise juste qui encaisse le choc en premier. La protection réelle de la tranche senior dépend entièrement d'une hypothèse sur la corrélation entre les actifs du pool, et c'est exactement cette hypothèse qui s'est effondrée en 2008.

> Suite logique, **The Big Short**, comment Michael Burry et d'autres ont identifié et tradé cette faille exacte.
