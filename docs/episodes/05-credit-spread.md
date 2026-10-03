<p class="ms-kicker">Épisode 05</p>

# Credit <span class="ms-outline">Spread.</span>

## Définition

Le **credit spread** est le rendement **supplémentaire** qu'un investisseur exige pour prêter à un emprunteur **risqué** (une entreprise) plutôt qu'à un emprunteur considéré comme **sans risque** (un État solide, dans sa propre devise).

**Formule**

`Credit spread = Yield de l'obligation d'entreprise − Yield de l'obligation d'État (même maturité)`

**Exemple concret.** Une obligation d'entreprise à 10 ans offre un yield de 5,5%. L'obligation d'État à 10 ans (référence "sans risque") offre 3,2%. Le credit spread vaut 5,5% − 3,2% = **2,3%, soit 230 bps.**

## Pourquoi on compare toujours à même maturité

Le yield d'une obligation dépend à la fois du **risque de crédit** et du **niveau général des taux** (vu dans la Yield Curve). En comparant deux obligations de **même maturité**, on isole uniquement l'effet du risque de crédit, sinon on comparerait des pommes et des oranges, une partie de l'écart viendrait juste de la forme de la courbe des taux.

## Ce qui compose vraiment un credit spread (le point subtil)

Le spread n'est **pas** un pur reflet du risque de défaut. Il agrège plusieurs composantes.

1. **Prime de risque de défaut (default risk premium).** La probabilité que l'entreprise ne rembourse pas, pondérée par la perte potentielle.
2. **Prime de liquidité (liquidity premium).** Les obligations d'entreprise se tradent moins facilement que les obligations d'État, les investisseurs exigent une compensation pour ce manque de liquidité.
3. **Prime d'incertitude / d'aversion au risque.** Même sans changement de la probabilité réelle de défaut, si les investisseurs deviennent globalement plus nerveux (période de stress macro), ils exigent un spread plus large partout, sur toutes les entreprises.
4. Parfois une composante **fiscale** (traitement fiscal différent des obligations d'État vs corporate selon les juridictions).

C'est pour ça que les spreads peuvent s'écarter même si le risque de défaut d'une entreprise précise n'a pas changé, le marché reprice la liquidité ou l'incertitude générale, pas juste le crédit propre à cette boîte.

## Pourquoi on surveille les spreads de si près

Le credit spread est un **double signal**.

- Il reflète la **qualité de crédit perçue** de l'émetteur.
- Il reflète la **confiance générale du marché**. En période de stress (2008, mars 2020), les spreads s'écartent brutalement sur **tout le marché**, même pour des entreprises solides, parce que la prime de liquidité et d'incertitude explose.

En pratique, les spreads sont un baromètre macro presque aussi suivi que les indices actions.

## Exemple d'écartement en période de crise

En 2008, les spreads de crédit corporate IG sont passés d'environ 100-150 bps à plus de **600 bps** en quelques mois, pas parce que toutes ces entreprises ont soudainement eu 6 fois plus de chances de faire faillite, mais parce que la liquidité s'est asséchée et la panique a fait grimper la prime d'incertitude partout.

<div class="ms-takeaway" markdown>

## À retenir

Le credit spread mesure le prix du risque de crédit, mais c'est un signal **composite**, qualité de crédit, liquidité et confiance de marché mélangés. Ne jamais l'interpréter comme une mesure pure du risque de défaut.

</div>

> Suite logique, **Credit Default Swaps (CDS)**, l'instrument qui permet de trader ce risque de crédit directement, sans passer par l'obligation elle-même.
