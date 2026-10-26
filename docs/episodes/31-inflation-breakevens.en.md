<p class="ms-kicker">Episode 31</p>

# Inflation <span class="ms-outline">Breakevens.</span>

## Why this episode

Episodes [26](26-the-policy-rate.md), [27](27-qe-and-qt.md) and [30](30-pricing-rate-cuts.md) covered the "rates" half of a central bank's job. The other half is inflation, and it is the reason central banks hike or cut. This episode shows how to read what the market expects for inflation straight from bond prices. It is a basic tool on a rates desk, it fits in one formula, and it has very clear real cases.

## The problem

A normal bond pays a fixed amount, so inflation erodes its real value. A 10-year bond paying 4.20% a year is worth less in purchasing power if prices rise 5% a year. So investors wanted a bond that protects them. It exists.

## Inflation-linked bonds

In the US they are **TIPS** (Treasury Inflation-Protected Securities). In the UK, **index-linked gilts** ("linkers"). In France, the OATi and OAT€i. The principle is the same.

- The **principal** (the amount repaid at the end) is adjusted with the **consumer price index** (CPI, the basket of prices a country tracks).
- The **coupon** is a fixed percentage of that adjusted principal.
- At maturity you get the adjusted principal back, and in the US never less than the original par (the deflation floor).

**Example.** $1,000 par, 2% coupon, and prices have risen 3% since issue.

```text
index ratio          = 1.03
adjusted principal   = 1,000 × 1.03 = $1,030
coupon               = 2% × 1,030 = $20.60   (instead of $20.00)
```

A TIPS yield is called the **real yield**. It is what you earn **above** inflation.

## The breakeven formula

A nominal 10-year pays 4.20%. A 10-year TIPS pays a real yield of 1.90% **plus inflation**. Which is better depends on the inflation that comes. The inflation level where both give exactly the same result is called the **breakeven**.

**Approximation.**

```text
breakeven = nominal yield − real yield
          = 4.20% − 1.90% = 2.30%
```

**Exact version**, the Fisher equation.

```text
(1 + nominal) = (1 + real) × (1 + inflation)
inflation     = 1.042 / 1.019 − 1 = 2.26%
```

### Check with money

You invest $1 for 10 years in one or the other.

```text
Nominal :  1.042^10                          = 1.509
TIPS    :  (1.019 × (1 + inflation))^10
   inflation 1.00% a year  ->  1.334         nominal wins
   inflation 2.26% a year  ->  1.509         tie
   inflation 3.00% a year  ->  1.622         TIPS wins
```

Reading.

- If average inflation over 10 years is **above 2.26%**, the TIPS wins.
- If it is **below**, the nominal wins.

So the breakeven is the market's **price of inflation**. Someone who thinks inflation will be higher than the breakeven buys the TIPS. Someone who thinks it will be lower buys the nominal.

## What the breakeven really contains

```text
breakeven = expected inflation + inflation risk premium − liquidity premium
```

- **Inflation risk premium.** The extra yield nominal bond holders want, because surprise inflation hurts them.
- **Liquidity premium.** TIPS are harder to trade, so their yield is a bit higher, which **lowers** the breakeven.

So the breakeven is not a pure forecast. Same lesson as the [OIS](30-pricing-rate-cuts.md) and the forward, a price that mostly reflects expectations, plus some noise. In a liquidity crisis the noise dominates (March 2020 below).

## The inflation forward: the 5y5y

You compare two breakevens of different lengths, like the forward between two [OIS](30-pricing-rate-cuts.md) or the FX forward in [episode 28](28-fx-forwards.md).

```text
(1 + BE10)^10 = (1 + BE5)^5 × (1 + f)^5
f = [ (1 + BE10)^10 / (1 + BE5)^5 ]^(1/5) − 1
```

**Example.** 5-year BE = 2.50%, 10-year BE = 2.30%.

```text
f = [ 1.023^10 / 1.025^5 ]^(1/5) − 1 = 2.10%
Shortcut: 2 × 2.30 − 2.50 = 2.10%
```

The market expects 2.50% inflation a year for 5 years, then **2.10%** a year for the 5 years after that. This is the **5y5y forward**, the indicator central banks watch the most. It strips out the short term (energy, temporary shocks) and measures whether the market believes inflation will come back to the 2% target over the long run. If it rises clearly above, the central bank has a credibility problem, and it reacts harder.

## The inflation swap

Desks do not only trade bonds. They use **zero-coupon inflation swaps**, which give the breakeven without buying or selling a bond, with the same logic as an [interest rate swap](10-interest-rate-swaps.md).

- The **fixed payer** pays `(1 + K)^T − 1` at maturity (K = the fixed inflation rate, T = years).
- It receives `CPI(T) / CPI(0) − 1`, the inflation actually measured.
- Only the difference is exchanged.

**Example.** 10 years, K = 2.30%, notional $10m.

```text
Fixed leg:  1.023^10 − 1 = 25.53%
If prices rose 28% in total over 10 years:
  the fixed payer receives 28% − 25.53% = 2.47% of notional = about $247,000
If prices only rose 20%:
  it loses 25.53% − 20% = 5.53% = about $553,000
```

Banks and pension funds use it. A pension fund that has to pay inflation-linked pensions **receives** inflation to hedge itself.

## The trade and its P&L

You think inflation will be above the breakeven. You **buy the TIPS and sell a nominal of the same maturity**. This is a **breakeven trade** (long breakevens).

Since the two bonds do not have the same [duration](03-duration.md), you size with [DV01](04-dv01.md) to keep the same rate sensitivity and keep only the bet on inflation.

**Example.** Buy $10m of 10-year TIPS (real duration 8.4) and sell 10-year nominal (duration 8.0).

```text
TIPS DV01        = 10,000,000 × 8.4 × 0.0001 = $8,400 per bp
Nominal to sell  = 8,400 / (8.0 × 0.0001) = $10.5m
```

If the real yield falls 54 bps and the nominal does not move, the breakeven goes from about 2.30% to 2.84%.

```text
P&L ≈ 8,400 × 54 = $453,600
```

Careful, this calculation assumes the nominal yield is unchanged. In reality, when inflation surprises up, both yields move. The trade only keeps the **difference**.

## Real cases

### March 2020, Covid: the breakeven collapses

The US 10-year breakeven (the St. Louis Fed's T10YIE series) went from about 1.7% in early March 2020 to about 0.5% in less than two weeks, with a low around 19 March (secondary sources give 0.50%). It ended the month around 0.87%. Oil collapsed, demand collapsed, and investors were paying almost nothing for inflation protection.

**But it was not only a deflation forecast.** During the dash for cash in March 2020, investors sold everything sellable, including TIPS, which are less liquid than nominals. The liquidity premium blew out, which crushed the breakeven. Part of the move is noise, not information.

### 2021-2022: inflation comes back

US inflation went from about 1.4% in early 2021 to above 9% in June 2022. The 10-year breakeven rose to around 3% on 21 April 2022 (2.99% or 3.02% depending on the source), its highest since 2008. Then the Fed hiked ([episode 26](26-the-policy-rate.md)) and the breakeven fell back to about 2.1% to 2.3% by the end of 2022.

**What it shows.** The market did **not** believe inflation would stay at 8-9%. A 10-year breakeven around 3% is not 9%. The 10-year was pricing that the Fed would bring inflation down. Breakevens at 1 or 2 years were much higher (above 4% in spring 2022). The inverted **curve** of breakevens said the same as the rate curve, inflation now, moderation later.

### September 2022, UK: linkers in the LDI crisis

The LDI fund crisis of [episode 27](27-qe-and-qt.md) also hit index-linked gilts. UK pension funds hold linkers because the pensions they pay are linked to inflation. LDI funds offer leveraged exposure to gilts, including index-linked ones. When forced selling started, the Bank of England first bought conventional long gilts from 28 September, then widened its purchases to **index-linked gilts** on 11 October 2022, a first for it.

**The lesson.** Breakevens and linkers are **hedging** instruments for huge players. When they sell under pressure, prices move a lot, and it has nothing to do with expected inflation.

## Classic pitfalls

- **Taking the breakeven for a pure inflation forecast.** It contains a risk premium and a liquidity premium.
- **Comparing different maturities.** The 5-year and 10-year breakevens do not measure the same thing. The 5y5y is the right tool for the distant period.
- **Forgetting the index lag.** TIPS use the CPI with a lag of about 3 months (interpolated between two months). Principal adjustments therefore lag actual prices.
- **Not sizing the trade.** Buying $10m of TIPS and selling $10m of nominal is not rate-neutral, because the durations differ. You have to go through DV01.
- **The deflation floor.** In the US, principal is never repaid below the original par. That has value (it is an option), especially for recently issued TIPS.
- **Mixing realised inflation and the change in the breakeven.** If realised inflation ends up above the breakeven but the breakeven fell in the meantime, a trade closed before maturity can lose.

## The S&T interview angle

**"What is an inflation breakeven?"** The difference between the yield on a nominal bond and on an inflation-linked bond of the same maturity. It is the inflation level where both pay the same. Nominal 4.20%, real 1.90%, breakeven 2.30% (2.26% with Fisher).

**"Does that mean the market forecasts 2.30% inflation?"** Not exactly. The breakeven also contains an inflation risk premium and a liquidity premium. In March 2020, liquidity made it fall much more than real expectations.

**"Your trade if you think inflation will be higher than the market prices?"** Long breakeven, buy the TIPS and sell a nominal of the same maturity, sized on DV01. Or receive inflation on a zero-coupon swap.

**"What is the 5y5y?"** The expected annual inflation rate between 5 years and 10 years from now. Central banks watch it because it measures how well long-term expectations are anchored.

**"Who receives inflation on a swap?"** Pension funds and insurers with inflation-linked liabilities. They want to be covered if it rises.

**"Why does the Fed care?"** Because if long-term expectations come loose from 2%, people and companies set wages and prices higher, and inflation feeds itself. The central bank then has to hike harder.

## Links to previous episodes

- [The Policy Rate](26-the-policy-rate.md), the central bank hikes to bring inflation back to target.
- [QE and QT](27-qe-and-qt.md), the UK LDI crisis also hit linkers.
- [Pricing Rate Cuts](30-pricing-rate-cuts.md), same logic of reading an expectation in a price, and the same forward between two horizons.
- [Duration](03-duration.md) and [DV01](04-dv01.md), to size the breakeven trade.
- [Interest Rate Swaps](10-interest-rate-swaps.md), the inflation swap has the same structure.
- [FX Forwards](28-fx-forwards.md), same forward formula between two horizons.

<div class="ms-takeaway" markdown>

## Key takeaway

- An inflation-linked bond adjusts its principal with inflation. Its yield is the **real** yield.
- Breakeven ≈ nominal yield − real yield. Exact with Fisher: (1 + nominal) = (1 + real) × (1 + inflation).
- If inflation ends above the breakeven, the TIPS wins. Otherwise, the nominal wins.
- The breakeven contains a risk premium and a liquidity premium. It is not a pure forecast.
- The 5y5y forward, f ≈ 2 × BE10 − BE5, measures how well long-term expectations are anchored.
- The long-breakeven trade is sized on DV01. March 2020 (0.5%), April 2022 (about 3%) and the UK linker episode show breakevens also move for liquidity reasons.

</div>
