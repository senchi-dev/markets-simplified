# 20. The Gamma Squeeze

## Pourquoi cet épisode

Synthèse de plusieurs épisodes : gamma, delta hedging, market makers, et le short squeeze de GameStop. Un cas concret où la couverture d'options fait exploser un cours.

## Le setup

Quand tu achètes un call, quelqu'un te le vend, généralement un **market maker**. Il ne veut pas parier sur la direction, juste encaisser son spread. Donc il se **couvre** : ayant vendu un call, il achète une partie de l'action pour rester delta-neutral.

## Le mécanisme clé, le gamma

Le nombre d'actions qu'il doit détenir n'est **pas fixe**. Quand l'action monte, le call qu'il a vendu devient plus sensible à l'action (son delta grimpe), donc il doit **acheter encore plus d'actions** pour rester couvert. C'est le **gamma** (épisode 16).

## La boucle auto-alimentée

- Une foule achète massivement des calls sur une action.
- Les market makers qui les vendent achètent des actions pour se couvrir.
- Cet achat fait monter l'action.
- Action plus haute = ils ont besoin d'encore plus d'actions, donc ils rachètent.
- Ce qui fait encore monter l'action.

La boucle s'auto-alimente, le cours part à la verticale en quelques jours, porté par la **couverture**, pas par une vraie réévaluation de l'entreprise.

## Gamma squeeze vs short squeeze (distinction clé)

- **Short squeeze** (épisode 12) : des vendeurs à découvert forcés de racheter l'action pour clôturer leurs positions.
- **Gamma squeeze** : des market makers forcés d'acheter l'action pour couvrir des options qu'ils ont vendues.

Personnes différentes, raison différente. **GameStop 2021 était les deux en même temps**, d'où l'ampleur du mouvement.

## Le point contre-intuitif

Personne dans la boucle ne cherche à faire monter le prix. Les market makers préféreraient ne pas acheter du tout. Ils y sont forcés, encore et encore, par leur propre couverture.

## À retenir

Gamma squeeze = boucle où l'achat massif de calls force les market makers à acheter l'action pour se couvrir, ce qui fait monter le cours, ce qui les force à acheter encore plus. C'est le delta hedging + le gamma qui s'emballent. À ne pas confondre avec le short squeeze, même si les deux peuvent se combiner.
