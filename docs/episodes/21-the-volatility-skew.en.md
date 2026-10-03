<p class="ms-kicker">Episode 21</p>

# The Volatility <span class="ms-outline">Skew.</span>

## Why this episode

A direct follow-up to implied vol (episode 19). Black-Scholes assumes a single, constant vol, which is wrong in practice, and the skew is the visual proof of that flaw. A classic S&T interview question.

## The starting point, a wrong assumption

Each option has its own implied vol (extracted from its price). A stock has lots of strikes, so lots of implied vols. Black-Scholes assumes volatility is a property of **the stock itself**, a single level of agitation. The strike is just a number chosen in the contract, with no effect on how much the stock actually moves. So in theory, all options with the same expiry should give the **same** implied vol. A **flat line**.

## What we actually see

It is not flat. If you plot implied vol against strike, you get a **curve**. Low strikes have a much higher implied vol than high strikes.

**Example, Apple at 100, 1-month expiry.**

- Strike 80: 32%
- Strike 100 (ATM): 20%
- Strike 120: 18%

## Why the curve slopes (the core)

1. **Fear of crashes.** Stocks fall more violently than they rise. The market prices a bigger downside risk.
2. **Hedging demand.** Everyone buys low-strike puts to protect themselves. This strong demand pushes up the price of those puts, and a higher option price = a higher implied vol (we invert the model). Fear turns mechanically into inflated vol on low strikes.

## The two shapes

- **Skew (or smirk)**: a **sloping** curve, high vol on the left (low strikes), low on the right. This is what you see on **equities and indices**.
- **Smile**: **both** edges curve up, a symmetric shape. More common in **FX and commodities**.

## Put or call? Parity settles it (link to episode 14)

At each strike there are **both**, a call AND a put. Put-Call Parity forces them to have **exactly the same implied vol**. So a point on the curve is neither a call nor a put, it is a single number shared by both. "Puts on the left / calls on the right" just means we read the vol off the **OTM** (liquid) option at each end.

### The mathematical proof (for revision)

Parity (pure arbitrage, no model assumption): `C − P = S − K·e^(−rT)`. Black-Scholes prices respect it for any σ: `BS_call(σ) − BS_put(σ) = S − K·e^(−rT)`.

Let σ_c be the call's implied vol (`BS_call(σ_c) = C_mkt`). Plugging σ_c into BS parity:

```text
BS_put(σ_c) = BS_call(σ_c) − (S − K·e^(−rT))
            = C_mkt − (S − K·e^(−rT))
            = C_mkt − (C_mkt − P_mkt)   [market parity]
            = P_mkt
```

So σ_c is also the put's implied vol. Since implied vol is unique (Vega = ∂C/∂σ = S·√T·N'(d1) > 0, so BS is strictly increasing in σ), we get **σ_p = σ_c**.

## Black-Scholes formula (reminder, where vol lives)

```text
C = S·N(d1) − K·e^(−rT)·N(d2)
d1 = [ ln(S/K) + (r + σ²/2)·T ] / (σ·√T)
d2 = d1 − σ·√T
```

The only unknown input is σ. The skew is the fact that σ_impl(K) depends on K instead of being constant, direct proof that the constant-vol assumption is wrong.

<div class="ms-takeaway" markdown>

## Key takeaway

The skew = implied vol plotted against strike is not flat but sloping (equities) or smile-shaped (FX). It is caused by fear of crashes and hedging demand, which inflate the vol of low-strike puts. Each point is shared by the call and the put at that strike (parity). It is the empirical proof that Black-Scholes (constant vol) is wrong.

</div>
