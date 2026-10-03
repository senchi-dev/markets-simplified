# 1. Fixed vs Floating Rate Debt

## Le principe de base

Quand une entreprise ou un État emprunte de l'argent (émet de la dette), il doit choisir comment les intérêts seront calculés sur toute la durée du prêt. Deux régimes possibles, le taux fixe ou le taux variable.

## Taux fixe (Fixed Rate)

Le taux d'intérêt est **figé au moment de l'émission** et ne bouge jamais jusqu'à la maturité.

**Exemple concret.** Une entreprise émet une obligation à 5 ans, coupon fixe de 4%. Elle paiera exactement 4% par an, chaque année, pendant 5 ans, peu importe ce qui se passe sur les marchés.

**Avantages**

- **Certitude totale** sur les paiements futurs, ce qui rend les budgets et prévisions de trésorerie faciles.
- Protection si les taux **montent**, puisque tu restes bloqué à ton taux avantageux pendant que le marché paie plus cher.

**Inconvénients**

- Si les taux de marché **baissent**, tu continues de payer ton ancien taux, plus élevé. Tu ne profites pas de la baisse, sauf refinancement, qui coûte des frais.
- Moins de **flexibilité**, car rembourser par anticipation ou renégocier est souvent contractuellement plus contraignant et coûteux (clauses de remboursement anticipé, pénalités).
- Généralement **plus cher à l'émission** que le taux variable, car le prêteur exige une prime pour te garantir un taux stable sur toute la durée (il prend le risque de taux à ta place).

## Taux variable (Floating Rate)

Le taux est **recalculé périodiquement** (tous les 3 ou 6 mois en général) en fonction d'un taux de référence du marché.

**Formule type**

`Taux payé = Taux de référence + Marge (spread)`

Le taux de référence est aujourd'hui typiquement le **SOFR** (Secured Overnight Financing Rate, USA) ou l'**€STR** (Europe), qui ont remplacé le LIBOR (abandonné en 2023 suite au scandale de manipulation). La marge reflète le risque de crédit propre à l'emprunteur, plus l'emprunteur est risqué, plus la marge est large.

**Exemple concret.** Un prêt à taux variable coté "SOFR + 150 bps". Si le SOFR est à 4%, l'emprunteur paie 5,50%. Si le SOFR monte à 5%, il paie 6,50% au trimestre suivant.

**Avantages**

- Généralement **moins cher au départ** que le taux fixe.
- Plus facile à **refinancer, restructurer, rembourser** par anticipation.
- Facile à **couvrir** avec un instrument dérivé (interest rate swap).

**Inconvénients**

- Exposition directe au **risque de marché**. Si les taux montent, les paiements montent aussi, sans plafond (sauf si un cap est négocié).
- Moins de prévisibilité pour la trésorerie.

## Le pont entre les deux, les Interest Rate Swaps

Une entreprise peut emprunter à taux variable (conditions plus favorables à l'émission) puis **échanger** ses flux variables contre des flux fixes via un swap de taux avec une contrepartie (souvent une banque). Résultat, elle paie effectivement un taux fixe **synthétique**, sans avoir émis une dette à taux fixe classique.

Pourquoi faire ça plutôt que d'émettre directement à taux fixe ? Parce que le marché des swaps est très liquide et permet d'obtenir des conditions de couverture parfois plus avantageuses que d'émettre directement en fixe, surtout pour les émetteurs récurrents.

## Pourquoi les entreprises empruntent-elles souvent à taux variable ?

Deux raisons principales.

1. **Meilleures conditions à l'émission.** Les banques prêtent naturellement plus volontiers (et moins cher) à taux variable car elles transfèrent le risque de taux à l'emprunteur.
2. **Le risque se gère après coup** avec des swaps, séparément de la décision de financement initiale.

## L'intuition à retenir

Le taux fixe et le taux variable ne sont pas juste "deux façons de calculer un intérêt", c'est un **partage du risque de taux** entre le prêteur et l'emprunteur.

- **Fixe.** Le prêteur prend le risque que les taux montent (il est bloqué à un rendement fixe pendant que le marché paie mieux ailleurs), donc il facture une **prime de certitude** à l'emprunteur.
- **Variable.** L'emprunteur prend le risque que les taux montent, donc il paie **moins cher au départ** en échange d'assumer ce risque.

## Connexion avec la suite de la série

Cette distinction fixe/variable est la porte d'entrée vers tout le reste de la série. La sensibilité aux taux (**Duration**, **DV01**) ne concerne réellement que la dette à **taux fixe**, une obligation à taux variable a une duration très faible car son coupon se réajuste avant que le taux de marché n'ait le temps de faire bouger son prix.

> Suite logique, **The Yield Curve**, la carte complète des taux selon la maturité.
