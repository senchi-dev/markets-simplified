<p class="ms-kicker">Épisode 30</p>

# Pricing Rate <span class="ms-outline">Cuts.</span>

## Pourquoi cet épisode

L'[épisode 26](26-the-policy-rate.md) disait « le marché price 3 baisses cette année » sans montrer d'où sort ce chiffre. C'est le chiffre le plus utilisé sur un desk de taux. Personne ne demande au marché ce qu'il attend de la banque centrale. On le lit dans un prix, celui d'un **OIS**. Cet épisode donne les formules pour lire ce prix, deux méthodes pour le transformer en probabilité de baisse, le calcul du gain ou de la perte quand le pricing bouge, et trois cas réels où ce que le marché avait pricé s'est avéré faux.

## C'est quoi un OIS

OIS = overnight index swap. C'est un [swap de taux](10-interest-rate-swaps.md) dont la jambe variable est le **taux overnight** (SOFR aux États-Unis, €STR en zone euro), composé jour après jour sur la période.

- Un côté paie un taux **fixe** pendant toute la période.
- L'autre côté paie le taux overnight composé.
- À la fin, on n'échange que la différence.

Le taux fixe est choisi pour que le swap ne coûte rien le premier jour. Donc le taux fixe est la meilleure estimation du marché pour la **moyenne du taux overnight** sur la période. C'est le même raisonnement que pour le fixe d'un swap classique.

## Formule 1, l'OIS est une moyenne

```text
OIS ≈ moyenne des taux overnight attendus sur la période
    ≈ (r1 × t1 + r2 × t2 + ... ) / T
```

- **r1, r2...** = le taux overnight attendu pendant chaque morceau de période.
- **t1, t2...** = la durée de chaque morceau, en années.
- **T** = la durée totale.

**Exemple.** Overnight aujourd'hui, **4,00 %**. OIS à 1 an, **3,625 %**. Le marché attend une moyenne de 3,625 % sur l'année, donc des baisses. Combien ? Supposons une baisse de 25 bps (0,25 %) tous les 3 mois, la première dans 3 mois.

```text
mois 0-3    4,00 %
mois 3-6    3,75 %
mois 6-9    3,50 %
mois 9-12   3,25 %
moyenne     (4,00 + 3,75 + 3,50 + 3,25) / 4 = 3,625 %
```

Ça colle avec l'OIS. On a lu « 3 baisses pricées sur l'année » en reconstruisant le chemin qui donne 3,625 %.

## Formule 2, une baisse pèse selon le temps qui reste

Une baisse décidée tôt pèse plus dans la moyenne qu'une baisse décidée tard.

```text
effet sur la moyenne = taille de la baisse × (temps restant après la décision / T)
```

Avec les 3 baisses de 25 bps à 3, 6 et 9 mois :

| Baisse | Temps restant | Poids | Effet sur l'OIS 1 an |
|---|---|---|---|
| Mois 3 | 9 mois | 9/12 | 25 × 0,75 = 18,75 bps |
| Mois 6 | 6 mois | 6/12 | 25 × 0,50 = 12,5 bps |
| Mois 9 | 3 mois | 3/12 | 25 × 0,25 = 6,25 bps |
| Total | | | **37,5 bps** |

4,00 % − 0,375 % = **3,625 %**. On retrouve l'OIS.

Conséquence pratique. Une baisse de 25 bps dans 3 mois ne fait bouger l'OIS 1 an que de 18,75 bps, pas de 25. Pour savoir « combien de baisses » à partir d'un OIS, il faut tenir compte de leur date. Un OIS plus court, qui couvre seulement les prochaines réunions, donne un signal plus propre.

## Formule 3, le taux forward entre deux OIS

On veut la moyenne attendue pour une période précise. On compare deux OIS de durées différentes.

```text
forward = (R2 × T2 − R1 × T1) / (T2 − T1)
```

**Exemple.** OIS 6 mois = 3,875 %, OIS 1 an = 3,625 %.

```text
forward 6m dans 6m = (3,625 × 1 − 3,875 × 0,5) / (1 − 0,5)
                   = (3,625 − 1,9375) / 0,5
                   = 3,375 %
```

Le marché attend une moyenne de 3,875 % les 6 premiers mois, puis 3,375 % les 6 suivants. C'est la même idée que le forward de la [courbe des taux](02-the-yield-curve.md) et que le forward FX de l'[épisode 28](28-fx-forwards.md), on obtient le futur en comparant deux horizons.

## Formule 4, de l'OIS à la probabilité d'une baisse

La banque centrale décide par pas de 25 bps. Le marché, lui, price une **moyenne** entre les scénarios possibles.

```text
probabilité d'une baisse de 25 bps ≈ baisse attendue à la réunion / 25 bps
```

**Exemple.** Taux actuel 4,00 %. Le taux attendu après la prochaine réunion, lu sur l'OIS, est 3,875 %.

```text
baisse attendue = 4,00 − 3,875 = 12,5 bps
probabilité     = 12,5 / 25 = 50 %
```

Le marché price **50 % de chances d'une baisse de 25 bps**. Si la baisse attendue est de 18,75 bps, c'est 75 %.

Quand le marché hésite entre 25 et 50 bps, la baisse attendue est entre les deux. Exemple, 37,5 bps attendus, c'est 50 % de 25 bps et 50 % de 50 bps.

## Formule 5, le futur sur fed funds

Même information, version marché à terme. Le contrat de futures sur fed funds cote un prix.

```text
prix du future = 100 − taux moyen attendu sur le mois
```

**Exemple.** Prix 96,25, soit un taux moyen attendu de 100 − 96,25 = **3,75 %**. Un prix qui monte, c'est un taux attendu qui baisse, donc plus de baisses pricées. L'outil CME FedWatch que tout le monde cite transforme ces prix en probabilités avec la formule 4.

## Formule 6, combien on gagne ou on perd

Si tu penses que la banque centrale baissera plus que ce que le marché price, tu **reçois** le taux fixe sur un OIS. Tu gagnes si le taux fixe du marché baisse.

```text
P&L ≈ notionnel × DV01 par bp × variation de l'OIS (en bps)
DV01 d'un OIS 1 an ≈ notionnel × 0,0001 × 0,96   (la durée est proche de 1 an, actualisée)
```

**Exemple.** Notionnel 100 M$, OIS 1 an à 3,625 %. DV01 ≈ 100 000 000 × 0,0001 × 0,96 ≈ **9 600 $ par bp**. Voir le [DV01](04-dv01.md).

| Ce que fait le marché | Variation de l'OIS | P&L du receveur |
|---|---|---|
| Une baisse de 25 bps en plus à 3 mois | −18,75 bps | + 180 000 $ |
| Une baisse de 25 bps en moins à 3 mois | +18,75 bps | − 180 000 $ |
| Rien ne bouge | 0 | 0 |

(18,75 × 9 600 ≈ 180 000.)

Un OIS de durée plus longue a un DV01 plus gros. Un OIS 2 ans a un DV01 d'environ 1,9 fois celui d'un OIS 1 an, avec la même logique que la [duration](03-duration.md).

## Pourquoi la surprise compte

```text
réaction du marché ≈ ce qui s'est passé − ce qui était pricé
```

| Pricé | Décision | Surprise | Réaction |
|---|---|---|---|
| 100 % d'une baisse de 25 | Baisse de 25 | 0 | Presque aucune |
| 50 % d'une baisse de 25 | Baisse de 25 | +12,5 bps de baisse en plus | Les taux courts baissent |
| 100 % d'une baisse de 25 | Pas de baisse | −25 bps | Les taux courts montent fort |
| 100 % d'une baisse de 25 | Baisse de 50 | +25 bps | Les taux courts baissent fort |

Et pas seulement la décision du jour. La **forward guidance** (ce que le président dit sur la suite) déplace tout le reste du chemin, donc l'OIS sur les réunions suivantes.

## Cas réels

### 1. Mars 2023, SVB : le marché inverse son pricing en 3 jours

Début mars 2023, le marché pricait des hausses de taux supplémentaires de la Fed, avec un taux final proche de 5,5 %. Le 10 mars, Silicon Valley Bank fait faillite ([épisode 27](27-qe-and-qt.md)). En quelques jours, le marché retire les hausses et price des baisses avant la fin de l'année. Le taux américain à 2 ans, le plus sensible aux anticipations de la Fed, perd environ 90 bps en trois jours (selon l'horaire de mesure, entre 87 et 97 bps selon les sources), sa plus forte baisse sur trois jours depuis le krach de 1987.

**Le chiffre.** Une obligation à 2 ans a une duration d'environ 1,9. Une baisse de 0,90 % du rendement donne environ +1,7 % de prix, soit environ **170 000 € de gain sur 10 M€** de nominal. Un trader qui avait mis un receveur de taux avant le week-end a vu un gain énorme, un payeur a subi la perte.

**La leçon.** Le pricing peut basculer en quelques jours quand le risque change de nature. Il ne s'agissait plus d'inflation mais de stabilité financière.

### 2. 2024, le pricing contre la réalité

Décembre 2023, la Fed publie ses prévisions, la médiane des membres voit 3 baisses de 25 bps en 2024 (75 bps). Le marché va plus loin et price jusqu'à 6 ou 7 baisses pour l'année début 2024 (environ 150 à 175 bps, selon la date et la mesure). Puis l'inflation reste plus forte que prévu, et le marché retire des baisses au fil des mois.

**Ce qui s'est passé.** La Fed a baissé de 100 bps en 2024 (50 bps en septembre, puis 25 en novembre et 25 en décembre). Moins que le marché début 2024, plus que les 75 bps de la médiane de décembre.

**Le chiffre.** Un receveur d'OIS qui est entré quand 175 bps étaient pricés et qui est sorti quand il n'en restait que 100 de pricés (par exemple) a perdu de l'argent sur le pricing, même si la Fed a bien baissé. Pour gagner, il fallait avoir raison sur le **nombre** de baisses, pas seulement sur la direction.

**La leçon.** Être juste sur la direction ne suffit pas. Il faut être juste par rapport à ce qui est déjà pricé.

### 3. Septembre 2024, 25 ou 50 bps

Avant la réunion du 18 septembre 2024, le marché hésitait entre une baisse de 25 et de 50 bps. Selon les estimations de CME FedWatch reprises par la presse, la probabilité d'une baisse de 50 bps était d'environ 14 % la veille d'un article du Wall Street Journal et d'un commentaire de Bill Dudley, puis d'environ 44 % juste après (d'autres mesures donnaient un peu plus). Début août, après le choc du yen ([épisode 29](29-the-carry-trade.md)), elle avait atteint environ 70 %.

La Fed a baissé de **50 bps**.

**Le chiffre.** Avec la formule 4, une probabilité de 50 bps de 44 % donne une baisse attendue de 25 × 0,56 + 50 × 0,44 = 14 + 22 = **36 bps**. La baisse de 50 bps était donc surprenante de +14 bps, ce qui est petit comparé à la plupart des surprises. Elle était déjà largement pricée.

**La leçon.** Une grosse décision n'est pas une grosse surprise. Quand le pricing a convergé avant la réunion, le marché bouge peu, et l'important devient ce que dit le président pour la suite.

## Pièges classiques

- **« Le marché price 3 baisses » sans préciser la période.** Avec la formule 2, 3 baisses sur 12 mois et 3 baisses d'ici la fin de l'année ne donnent pas le même OIS 1 an.
- **Prendre l'OIS pour une prévision exacte.** Il contient une petite prime de risque et il est le résultat d'un prix, pas d'une enquête. Utile pour lire les anticipations, pas pour prédire.
- **Oublier la date des réunions.** Une baisse en septembre pèse moins sur l'OIS 1 an qu'une baisse en mars.
- **Confondre direction et pricing.** Avoir raison que la Fed baisse ne rapporte rien si c'est déjà pricé.
- **Passer d'une probabilité à une certitude.** « 44 % » veut dire que 56 % du marché voyait autre chose. Ça arrive.
- **Mélanger OIS et taux de swap classique.** Un swap de taux sur Libor ou Euribor contient aussi du risque de crédit bancaire. L'OIS est (presque) sans risque de crédit, c'est pour ça qu'il est devenu la référence pour lire les anticipations.

## L'angle entretien S&T

**« Comment sais-tu combien de baisses sont pricées ? »** On lit l'OIS pour chaque réunion, et on regarde la baisse attendue par rapport au taux actuel. Baisse attendue divisée par 25 bps, ça donne la probabilité d'une baisse de 25.

**« L'OIS à 1 an cote 3,625 % et l'overnight est à 4,00 %. Qu'est-ce que ça veut dire ? »** Le marché attend une moyenne de 3,625 % sur l'année, donc 37,5 bps de moins que l'overnight en moyenne. Avec des baisses de 25 bps, ça correspond à 3 baisses réparties à 3, 6 et 9 mois.

**« Ton trade si tu penses que la Fed baissera plus que le marché ne price ? »** Recevoir le fixe sur un OIS ou acheter des futures sur fed funds. Je gagne si le pricing baisse, et la taille du gain dépend du DV01.

**« Pourquoi une baisse de 25 bps ne fait pas bouger l'OIS 1 an de 25 bps ? »** Parce que l'OIS est une moyenne sur la période. L'effet est pondéré par le temps restant après la baisse.

**« Et si la Fed baisse comme prévu ? »** Rien ne bouge, parce que c'était déjà pricé. Le marché réagit à la surprise et à la forward guidance.

**« Pourquoi l'OIS et pas le Libor ? »** Parce que l'OIS n'inclut presque pas de risque de crédit bancaire, donc il reflète les anticipations de politique monétaire de façon plus propre.

## Liens avec les épisodes précédents

- [The Policy Rate](26-the-policy-rate.md), le taux que l'OIS permet de lire à l'avance.
- [QE and QT](27-qe-and-qt.md), SVB et la faillite qui a fait basculer le pricing.
- [Interest Rate Swaps](10-interest-rate-swaps.md), l'OIS est un swap, même mécanique.
- [The Yield Curve](02-the-yield-curve.md), le forward entre deux OIS suit la même logique que le forward de la courbe.
- [DV01](04-dv01.md), pour chiffrer le gain ou la perte quand le pricing bouge.
- [FX Forwards](28-fx-forwards.md), même formule de forward entre deux horizons.
- [The Carry Trade](29-the-carry-trade.md), le choc du yen d'août 2024 a fait basculer le pricing de la Fed.

<div class="ms-takeaway" markdown>

## À retenir

- Un OIS est un swap dont la jambe variable est le taux overnight. Son taux fixe est la **moyenne attendue** de l'overnight sur la période.
- Une baisse pèse dans la moyenne selon le temps qui reste : effet = taille × (temps restant / durée totale).
- Probabilité d'une baisse de 25 bps ≈ baisse attendue à la réunion / 25 bps.
- Le forward entre deux OIS : (R2 × T2 − R1 × T1) / (T2 − T1).
- Le gain d'un receveur d'OIS ≈ notionnel × DV01 × variation en bps.
- Le marché réagit à la **surprise**, pas à la décision. Être juste sur la direction ne rapporte rien si c'est déjà pricé.

</div>
