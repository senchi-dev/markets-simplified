# 21. The Volatility Skew

## Pourquoi cet épisode

Prolongement direct de la vol implicite (épisode 19). Black-Scholes suppose une vol unique et constante, faux en pratique, et le skew est la preuve visuelle de cette faille. Question d'entretien S&T ultra classique.

## Le point de départ, une hypothèse fausse

Chaque option a sa propre vol implicite (extraite de son prix). Une action a plein de strikes, donc plein de vols implicites. Black-Scholes suppose que la volatilité est une propriété de **l'action elle-même**, un seul niveau d'agitation. Le strike n'est qu'un nombre choisi dans le contrat, sans effet sur combien l'action bouge vraiment. Donc en théorie, toutes les options d'une même échéance devraient donner la **même** vol implicite. Une **ligne plate**.

## Ce qu'on observe vraiment

Ce n'est pas plat. Si on trace la vol implicite en fonction du strike, on obtient une **courbe**. Les strikes bas ont une vol implicite bien plus haute que les strikes hauts.

**Exemple, Apple à 100, échéance 1 mois.**

- Strike 80 : 32%
- Strike 100 (ATM) : 20%
- Strike 120 : 18%

## Pourquoi la courbe penche (le cœur)

1. **La peur des krachs.** Les actions chutent plus violemment qu'elles ne montent. Le marché price un plus gros risque à la baisse.
2. **La demande de couverture.** Tout le monde achète des puts à strike bas pour se protéger. Cette forte demande fait monter le prix de ces puts, et un prix d'option plus haut = une vol implicite plus haute (on inverse le modèle). La peur se transforme mécaniquement en vol gonflée sur les strikes bas.

## Les deux formes

- **Skew (ou smirk)** : courbe **penchée**, vol haute à gauche (strikes bas), basse à droite. C'est ce qu'on voit sur les **actions et indices**.
- **Smile** : les **deux** bords remontent, forme symétrique. Plutôt sur le **FX et les matières premières**.

## Put ou call ? La parité tranche (lien épisode 14)

À chaque strike il existe **les deux**, un call ET un put. La Put-Call Parity les force à avoir **exactement la même vol implicite**. Donc un point de la courbe n'est ni un call ni un put, c'est un seul chiffre partagé par les deux. « Puts à gauche / calls à droite » = on lit juste la vol sur l'option **OTM** (liquide) à chaque bout.

### La preuve mathématique (pour révision)

Parité (arbitrage pur, sans hypothèse de modèle) : `C − P = S − K·e^(−rT)`. Les prix Black-Scholes la respectent pour toute σ : `BS_call(σ) − BS_put(σ) = S − K·e^(−rT)`.

On note σ_c la vol implicite du call (`BS_call(σ_c) = C_mkt`). En injectant σ_c dans la parité BS :

```text
BS_put(σ_c) = BS_call(σ_c) − (S − K·e^(−rT))
            = C_mkt − (S − K·e^(−rT))
            = C_mkt − (C_mkt − P_mkt)   [parité du marché]
            = P_mkt
```

Donc σ_c est aussi la vol implicite du put. La vol implicite étant unique (Vega = ∂C/∂σ = S·√T·N'(d1) > 0, donc BS strictement croissant en σ), on a **σ_p = σ_c**.

## Formule Black-Scholes (rappel, où vit la vol)

```text
C = S·N(d1) − K·e^(−rT)·N(d2)
d1 = [ ln(S/K) + (r + σ²/2)·T ] / (σ·√T)
d2 = d1 − σ·√T
```

Le seul input inconnu est σ. Le skew, c'est le fait que σ_impl(K) dépend de K au lieu d'être constant, la preuve directe que l'hypothèse de vol constante est fausse.

## À retenir

Le skew = la vol implicite tracée contre le strike n'est pas plate mais penchée (actions) ou en sourire (FX). Causé par la peur des krachs et la demande de couverture qui gonflent la vol des puts à strike bas. Chaque point est partagé par le call et le put du strike (parité). C'est la preuve empirique que Black-Scholes (vol constante) est faux.
