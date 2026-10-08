<p class="ms-kicker">Episode 25</p>

# Black-<span class="ms-outline">Scholes.</span>

## Why this episode

Black-Scholes shows up in almost every options episode. [Delta](15-delta.md) comes from it, [implied volatility](19-implied-volatility.md) is what you get by running it backwards, and the [skew](21-the-volatility-skew.md) exists because one of its assumptions is wrong. We never opened it up. This episode closes the options arc by explaining the model itself, where it comes from, how to price an option by hand, and why desks still use it when everyone knows it is wrong.

## What a model is

A model is a simplified version of reality written as a formula. You give it inputs, it gives you a number. It makes assumptions so the maths becomes possible, and those assumptions are never perfectly true. A good model is not an exact model. It is a model whose errors you know.

Black-Scholes takes 5 inputs and gives the "fair" price of a European option (one that can only be exercised at expiry).

## The problem before 1973

Before Black-Scholes, pricing a call meant guessing two things. Where the stock would end up, and what rate to use to discount a risky payoff. Everyone had their own estimate of the stock's return and their own appetite for risk, so everyone had their own price. There was no reference price.

What Black, Scholes and Merton showed is that you need neither the expected return nor the risk appetite. The price comes out of an arbitrage argument, just like [put-call parity](14-put-call-parity.md).

## The 5 inputs

| Input | Symbol | What it is | Where you find it |
|---|---|---|---|
| Underlying price | `S` | The stock price today | On the screen |
| Strike | `K` | The exercise price written in the contract | In the contract |
| Maturity | `T` | Time left until expiry, **in years** (6 months = 0.5) | In the contract |
| Risk-free rate | `r` | What a riskless loan pays (government rate), continuously compounded | On the screen |
| Volatility | `σ` (sigma) | How much the stock moves around, in % per year | **Nobody knows it** |

Four of the five inputs are observable. The only one you have to estimate is volatility. That is why the whole options market revolves around vol, and why traders quote in vol rather than in dollars or euros.

What is **not** on the list matters just as much. There is no expected return for the stock, and no view from the trader on direction.

## The core idea, copying the option

You can build an exact copy of an option with only two ingredients, shares and cash (borrowed or lent). If the copy pays exactly the same as the option in every scenario, the two must cost the same. Otherwise you buy the cheaper one, sell the more expensive one, and lock in a risk-free profit. This is the law of one price.

### A simple one-period version

To see the mechanism, simplify as much as possible. Stock at €100, in one year it is worth either €120 or €80. Interest rate 0%. Call with a €100 strike.

- If the stock goes to €120, the call pays €20.
- If it falls to €80, the call pays €0.

How many shares do you need to reproduce that? The call's payoff moves by €20, the stock's price moves by €40. So you need 20 / 40 = **0.5 shares**. That 0.5 is the [delta](15-delta.md).

- 0.5 shares are worth €60 if the stock goes up, €40 if it goes down.
- You borrow €40 today (and pay back €40, since the rate is zero).
- In the up scenario, 60 − 40 = €20. In the down scenario, 40 − 40 = €0.

The copy pays exactly like the call. Today it costs 0.5 × 100 − 40 = **€10**. So the call is worth €10.

We never used the probability that the stock goes up. Whether you think it has a 90% chance of rising or 10%, the call is worth €10. If someone sells it at €12, you sell it too, buy the copy at €10, and keep €2 whatever happens.

### Moving to the real model

In reality the price does not take two values, it moves continuously. Black-Scholes does the same thing by cutting time into infinitely small steps. At every instant you adjust the number of shares you hold (this is **delta hedging**), and the copy tracks the option all the time. The formula is what you get when you push this reasoning to the limit.

## Why the expected return disappears

Because the price comes from a copy, it is the same for an optimistic investor, a pessimistic one, a careful one or a gambler. So you can do the maths in an imaginary world where everyone is risk-neutral and every stock earns, on average, the risk-free rate `r`. This is called **risk-neutral pricing**. It is not a claim about real life. It is a calculation shortcut that gives the right price because the copying argument guarantees it.

In practice this means the probabilities that come out of Black-Scholes (like `N(d2)`) are probabilities in that risk-neutral world, not real-world probabilities. On a desk people say "risk-neutral probability".

## The formula

For a European call on a stock that pays no dividend:

```text
C = S × N(d1) − K × e^(−rT) × N(d2)

d1 = [ ln(S / K) + (r + σ² / 2) × T ] / ( σ × √T )
d2 = d1 − σ × √T
```

For a European put:

```text
P = K × e^(−rT) × N(−d2) − S × N(−d1)
```

### Every symbol

- **C** and **P**, the price of the call and the put.
- **e**, a mathematical constant worth about 2.718.
- **e^(−rT)**, the **discount factor**. It turns an amount paid at expiry into what it is worth today. At r = 4% and T = 1 year it equals 0.9608. So €100 in a year is worth €96.08 today.
- **ln**, the natural logarithm. `ln(S / K)` measures the gap between the stock price and the strike as a (continuous) percentage. ln(1) = 0, so at the money (S = K) this term is zero. ln(110 / 100) ≈ 0.095, so about +9.5%.
- **√T**, the square root of the maturity. Volatility grows with the square root of time, not with time. Over 4 years a stock moves roughly 2 times more than over 1 year, not 4 times more.
- **σ × √T**, the total volatility over the whole life of the option.
- **N(x)**, a probability between 0 and 1, explained just below.

### N(x) and the bell curve

Picture a bell curve (the normal distribution). Most values sit close to 0, extreme values are rare. N(x) is the share of the bell curve that sits to the left of x.

| x | N(x) | Reading |
|---|---|---|
| −2 | 0.023 | Almost nothing to the left |
| −1 | 0.159 | |
| 0 | 0.500 | Exactly half |
| 0.1 | 0.540 | |
| 0.3 | 0.618 | |
| 1 | 0.841 | |
| 2 | 0.977 | Almost everything to the left |

Useful property, N(−x) = 1 − N(x). The bell curve is symmetric.

Black-Scholes assumes the **logarithm** of the price follows this normal distribution, so the price itself follows a **log-normal** distribution. In plain words, the price can never go negative, and a +50% move is roughly as likely as a −33% move (both are the same distance in log terms).

### d1 and d2

d1 and d2 measure how far in or out of the money the option is, in number of standard deviations (of "total vols"). The bigger they are, the deeper in the money the option is.

- **N(d2)** = the (risk-neutral) probability that the call finishes in the money, so that you actually pay the strike.
- **N(d1)** = the call's **delta**. It is the number of shares to hold in the copy. It is not exactly a probability, it is the sensitivity of the price to the stock (see [episode 15](15-delta.md)).

d1 is always bigger than d2, and the gap between them is σ√T. That is why a call's delta is always a bit bigger than its probability of finishing in the money.

## Reading the formula in words

```text
C = (what you get in stock, weighted) − (what you pay at the strike, weighted)
```

- `S × N(d1)` = the value of the stock part of the copy. You hold N(d1) shares worth S each.
- `K × e^(−rT) × N(d2)` = the cash borrowed in the copy. It is the discounted strike, multiplied by the probability of having to pay it.

This is exactly the structure of the one-period example (0.5 shares minus €40 borrowed), with values computed continuously.

## Worked example, step by step

Stock at €100, strike €100 (at the money), 1 year, rate 4%, vol 20%.

**Step 1, d1.**

```text
ln(100 / 100) = 0
(r + σ² / 2) × T = (0.04 + 0.02) × 1 = 0.06
σ × √T = 0.20 × 1 = 0.20
d1 = (0 + 0.06) / 0.20 = 0.30
```

**Step 2, d2.**

```text
d2 = 0.30 − 0.20 = 0.10
```

**Step 3, the probabilities.**

```text
N(0.30) = 0.6179    (delta)
N(0.10) = 0.5398    (risk-neutral probability of finishing ITM)
```

**Step 4, the discount factor.**

```text
e^(−0.04 × 1) = 0.9608
```

**Step 5, the price.**

```text
C = 100 × 0.6179 − 100 × 0.9608 × 0.5398
C = 61.79 − 51.87
C = €9.93
```

**The put, same inputs.**

```text
P = 100 × 0.9608 × N(−0.10) − 100 × N(−0.30)
P = 96.08 × 0.4602 − 100 × 0.3821
P = 44.21 − 38.21
P = €6.00
```

**Check with [put-call parity](14-put-call-parity.md).** C − P = S − K × e^(−rT), so 9.93 − 6.00 = 3.93 and 100 − 96.08 = 3.92. It matches (the gap is rounding). Black-Scholes respects parity by construction.

Why is the call worth more than the put when both are at the money? Because the strike is paid in a year. With a positive rate, paying €100 later costs less than paying €100 today, which helps the call buyer. At a zero rate, the at-the-money call and put are worth exactly the same (€7.97 each in this example).

## What moves the price

Same base option (S = 100, K = 100, T = 1 year, r = 4%, σ = 20%), changing one input at a time.

| What changes | Call | Put | What to take from it |
|---|---|---|---|
| Base case | €9.93 | €6.00 | |
| Vol at 30% | €13.75 | €9.83 | More vol = both more expensive |
| Vol at 10% | €6.18 | €2.26 | Less vol = both cheaper |
| Vol at 21% (+1 point) | €10.31 | €6.39 | +€0.38, that is [vega](18-vega.md) |
| Stock at €101 | €10.55 | €5.63 | Call +€0.63, close to the 0.62 delta |
| Strike at €110 (OTM call) | €5.66 | €11.35 | |
| Strike at €90 (ITM call) | €16.06 | €2.53 | |
| 3 months to expiry | €4.49 | €3.49 | Less time = cheaper |
| 1 month to expiry | €2.47 | €2.14 | |
| Rate at 0% | €7.97 | €7.97 | Call = put at the money |

Two things to see in this table.

1. Vol is the input that matters most. Going from 20% to 30% lifts the call by almost 40%, without the stock or the date moving.
2. Time does not work linearly. 3 months are worth €4.49, not a quarter of €9.93. That is the square root of time, and it is what makes [theta](17-theta.md) speed up near expiry.

## The desk shortcut

For an at-the-money option with a low rate:

```text
Call ≈ Put ≈ 0.4 × S × σ × √T
```

In the example, 0.4 × 100 × 0.20 × 1 = €8. The true price at a zero rate is €7.97. The 0.4 comes from 1 / √(2π) ≈ 0.399. It lets you price a straddle in your head (2 × 0.4 × S × σ × √T ≈ 0.8 × S × σ × √T) and read an option price as an expected move. That is the maths behind [episode 22 on the straddle](22-the-straddle.md).

## The Greeks come out of the formula

Each Greek is the derivative of the Black-Scholes price with respect to one input. Write n(x) for the height of the bell curve at x, n(x) = e^(−x²/2) / √(2π).

| Greek | Formula (call) | Value in the example | Reading |
|---|---|---|---|
| [Delta](15-delta.md) | `N(d1)` | 0.618 | +€0.62 if the stock gains €1 |
| [Gamma](16-gamma.md) | `n(d1) / (S × σ × √T)` | 0.019 | Delta gains 0.019 per €1 rise |
| [Vega](18-vega.md) | `S × n(d1) × √T` (÷ 100 per vol point) | €0.38 | +€0.38 per vol point |
| [Theta](17-theta.md) | `−S × n(d1) × σ / (2√T) − r × K × e^(−rT) × N(d2)` (÷ 365) | −€0.016 per day | The option loses 1.6 cents a day |
| Rho | `K × T × e^(−rT) × N(d2)` (÷ 100) | €0.52 | +€0.52 if rates rise by 1 point |

The put's delta is N(d1) − 1 = −0.382. Gamma and vega are identical for a call and a put with the same strike and expiry, which follows from parity.

## Running it backwards, implied vol

In real life you do not know σ, but you can see the option's price on the screen. So you run the formula backwards. You look for the vol that, plugged into Black-Scholes, gives back the observed price. That is [implied volatility](19-implied-volatility.md).

If the at-the-money call in the example trades at €10.31 instead of €9.93, the implied vol is 21%. There is no closed-form formula for this reverse calculation, you solve it by trial and error (the price always rises with vol, so there is only one answer).

This is where Black-Scholes changes job. It is no longer used to find a price, it is used to **translate** a price into a vol. Options with different strikes and maturities become comparable on a single unit.

## The assumptions and where they break

| Assumption | In reality | Consequence |
|---|---|---|
| Constant volatility | Vol changes all the time and depends on the strike | The [skew and the smile](21-the-volatility-skew.md) |
| No jumps, the price moves continuously | Crashes, earnings announcements, gaps at the open | Deep OTM puts are worth more than the model says |
| Log-normal returns | Tails are fatter, big moves happen more often | Same effect, extremes are underpriced |
| Continuous hedging with no costs | You hedge at intervals, with fees and a bid-ask spread | The hedge is never perfect, hedging P&L moves around |
| Constant risk-free rate, borrow and lend at the same rate | Rates move, borrowing costs more than lending | Small effect on short options, bigger on long ones |
| No dividends | Many stocks pay dividends | Merton's extension, you subtract the dividend yield |
| Exercise only at expiry (European) | US single-stock options are usually American | You need binomial trees or other methods |

### The 1987 crash

Before October 1987, implied vol was roughly the same for every strike, as the model predicts. On 19 October 1987 the S&P 500 lost about 20% in a single day. Under a log-normal distribution with the vols of the time, that move was supposed to almost never happen. Since then the market charges more for OTM puts, and the skew has been a permanent feature of equity indices.

## How desks still use it

Nobody on a desk believes vol is constant. But everyone uses Black-Scholes as a **quoting convention**. You use a different vol for each strike and each maturity, which gives a **volatility surface**. The formula is still wrong, but by plugging the right vol into it for each option, you get back the market prices. A well-known line in the industry sums it up, roughly, you put the wrong number into the wrong formula to get the right price.

For exotic products, desks use richer models (local vol, stochastic vol like Heston, jump models), but those are calibrated to match the Black-Scholes prices of plain options.

## The rates cousins of Black-Scholes

On a rates desk you mostly see two variants.

- **Black 76**, adapted by Fischer Black in 1976 for options on futures and forwards. It is the standard model for **caps**, **floors** and **swaptions**. You replace S with the forward rate.
- **Bachelier (the normal model)**, where the underlying moves in basis points rather than in percent. When European rates went below zero, Black 76 stopped working (you cannot take the log of a negative number). The swaption market moved to quoting in **normal vol**, in basis points per year.

This links directly to the [swaps](10-interest-rate-swaps.md) and [yield curve](02-the-yield-curve.md) episodes.

## A bit of history

- **1973.** Fischer Black and Myron Scholes publish "The Pricing of Options and Corporate Liabilities" in the Journal of Political Economy. Robert Merton publishes a paper the same year that formalises the proof. The same year, the Chicago Board Options Exchange (CBOE) opens, the first organised exchange for listed options. Traders adopt the formula very quickly.
- **1987.** The crash exposes the limits of the constant-vol assumption. The skew is born.
- **1995.** Fischer Black dies.
- **1997.** Scholes and Merton receive the Nobel prize in economics. The Nobel is not awarded posthumously, but the committee mentions Black's role.
- **1998.** Long-Term Capital Management (LTCM), the hedge fund where Scholes and Merton were partners, loses about $4.6 billion in a few months. The New York Fed organises a rescue by a group of banks. The collapse came mostly from huge leverage and bets on spreads converging, not from the option formula itself.

## Classic pitfalls

- **Units.** σ as an annual decimal (20% = 0.20), T in years (3 months = 0.25, 30 days ≈ 30 / 365). Putting T in days or σ in percent gives absurd prices.
- **Continuous rate.** The formula uses a continuously compounded rate. A 4% annual rate is a continuous rate of ln(1.04) ≈ 3.92%. Small effect, but real.
- **N(d2) is not the real probability.** It is a risk-neutral probability. It says nothing about what will actually happen.
- **N(d1) is not a probability.** It is the delta. People sometimes use it as a rough proxy for the probability of finishing ITM, but in the model that role belongs to N(d2).
- **Historical vs implied vol.** Plugging historical vol into the formula gives a "theoretical" price. The market quotes with implied vol. The two are almost always different (see the variance risk premium in [episode 19](19-implied-volatility.md)).
- **American options and dividends.** The basic formula only works for a European option with no dividend. An American call on a non-dividend stock is worth the same as a European one (early exercise is never worth it), but that is not true for an American put.
- **"The model is wrong so it is useless."** Wrong. It is wrong, but it is the common language of the market. Everyone knows how to turn a price into a vol with the same formula.

## The S&T interview angle

**"Walk me through Black-Scholes."** The price of a European option depends on 5 inputs, stock price, strike, maturity, rate and vol. You can replicate the option with the stock and cash by adjusting the delta continuously, so by no-arbitrage the option is worth what the copy costs. The expected return does not appear. The formula is C = S N(d1) − K e^(−rT) N(d2), where N(d1) is the delta and N(d2) the risk-neutral probability of exercise.

**"Which input matters most?"** Vol, because it is the only one you cannot observe. The rest you read on the screen.

**"Why doesn't the stock's expected return matter?"** Because the price comes from replication. Two people who disagree on direction still have to agree on the price, otherwise one of them can arbitrage it.

**"What are the model's limits?"** Constant vol (contradicted by the skew), no jumps, tails too thin, continuous costless hedging. In practice the formula is kept as a convention and used with a vol surface.

**"Roughly what is a 1-year at-the-money call worth, stock at 100, vol at 20%?"** 0.4 × 100 × 0.20 ≈ 8. A bit more with positive rates (9.93 at 4%).

**"Which model for a swaption?"** Black 76 historically, Bachelier (normal vol) since negative rates.

## Links to previous episodes

- [Options](13-options.md) for the definitions of call, put, strike and premium.
- [Put-Call Parity](14-put-call-parity.md), the same arbitrage reasoning, and a relationship Black-Scholes respects automatically.
- [Delta](15-delta.md), [Gamma](16-gamma.md), [Theta](17-theta.md), [Vega](18-vega.md), the derivatives of the formula.
- [Implied Volatility](19-implied-volatility.md), the formula run backwards.
- [The Volatility Skew](21-the-volatility-skew.md), the proof that the constant-vol assumption is wrong.
- [The Straddle](22-the-straddle.md), the 0.8 × S × σ × √T shortcut in practice.

<div class="ms-takeaway" markdown>

## Key takeaway

- Black-Scholes gives the price of a European option from 5 inputs, stock price, strike, maturity, rate and vol.
- The core idea, you can copy the option with the stock and cash, so the option is worth what the copy costs. The expected return and any view on direction play no part.
- `C = S × N(d1) − K × e^(−rT) × N(d2)`. N(d1) is the delta, N(d2) the risk-neutral probability of finishing in the money.
- Vol is the only unknown input, hence quoting in vol and implied vol.
- At-the-money shortcut, price ≈ 0.4 × S × σ × √T.
- The model is wrong (constant vol, no jumps) and the skew proves it. Desks still use it as a common language, with a different vol for each strike and maturity.

</div>
