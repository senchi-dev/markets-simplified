<p class="ms-kicker">Episode 19</p>

# Implied <span class="ms-outline">Volatility.</span>

## Why this episode

Vega measured sensitivity to volatility. But which volatility? Implied volatility, the one the market expects, built into option prices. It is what options traders actually trade. (Note: we skip **Rho**, sensitivity to interest rates. It is the least important Greek and is almost ignored on equity desks.)

## Definition (CFA-confirmed)

A **model** is just a formula that takes several known inputs, runs the calculation, and spits out a single number (here, the fair price of the option). The standard model is called **Black-Scholes** (or Black-Scholes-Merton, 1973).

So the price of an option comes out of this model, which takes as inputs the stock price, the strike, the time remaining, interest rates, and **volatility**. All of these inputs are known **except future volatility**.

*(Nuance: pure Black-Scholes assumes a single, constant vol, which is wrong in practice. Hence the volatility skew (episode 21) and more advanced models like Heston, Dupire, SABR.)*

Implied volatility is found by running the model **in reverse**: you observe the option's actual market price, and you look for the volatility you would need to plug into the model to get back to that price. Vol is the only unknown (everything else is observable).

`Price observed in the market → inverted model → what volatility explains this price? = implied volatility`

## What it represents

The market's expectation of how big future moves will be, as built into option prices right now. High IV = expensive options, the market expects a big move. Low IV = cheap options, the market expects calm.

**Rigorous nuance.** IV is a **risk-neutral** measure, not a pure forecast. It is not exactly "what the market thinks vol will be".

## IV almost always runs higher than realized (variance risk premium)

This is the point that separates reciting from understanding. IV **systematically overestimates** actual moves. This is the **variance risk premium (VRP)**. People pay a premium for protection (institutions buying puts) and for the risk of a sudden jump, so option prices carry a premium above the move that is actually expected.

Figures as of 12 March 2026 on SPY: 30-day IV at **25.74%** vs realized volatility at **16.68%**, a gap of ~9 points. Positive ~79% of the time. Selling this gap is a strategy in its own right. \[source SharpeTwo\]

## Implied vs realized

- **Implied**: the vol the market *expects*, extracted from option prices today. This is what Vega reacts to.
- **Realized**: the vol that *actually* happened, measured after the fact on past moves.

## Quoting in vol (desk/dealer convention, NOT retail)

On a desk or between dealers, options are not quoted in euros but in **vol**. A dealer says "I'll buy at 18 vol", not "at 5 euros". The euro price is just the output calculated after plugging that vol into the model. What is really being negotiated is volatility.

**To frame carefully.** This is the convention of the OTC / institutional world. Retail traders see premiums in dollars on their broker (with IV shown next to them). Do NOT say "the € price doesn't exist" (wrong, it settles in cash). Say "they think in vol".

## Why it is central

It is the real currency of options. A trader compares the quoted IV with their own vol forecast to spot mispriced options (IV > their forecast = expensive option to sell, IV < their forecast = cheap option to buy).

<div class="ms-takeaway" markdown>

## Key takeaway

Implied volatility = the vol extracted from the market price by inverting the model. It is the market's (risk-neutral) expectation of future moves, it almost always runs higher than realized (variance risk premium), and desks actually trade options in vol, not in price.

</div>
