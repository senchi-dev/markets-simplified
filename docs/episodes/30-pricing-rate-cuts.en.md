<p class="ms-kicker">Episode 30</p>

# Pricing Rate <span class="ms-outline">Cuts.</span>

## Why this episode

[Episode 26](26-the-policy-rate.md) said "the market is pricing 3 cuts this year" without showing where that number comes from. It is the most used number on a rates desk. Nobody asks the market what it expects from the central bank. You read it in a price, the price of an **OIS**. This episode gives the formulas to read that price, two ways to turn it into a probability of a cut, the maths for how much you make or lose when the pricing moves, and three real cases where what the market had priced turned out to be wrong.

## What an OIS is

OIS = overnight index swap. It is an [interest rate swap](10-interest-rate-swaps.md) whose floating leg is the **overnight rate** (SOFR in the US, €STR in the euro area), compounded day after day over the period.

- One side pays a **fixed** rate for the whole period.
- The other side pays the compounded overnight rate.
- At the end, only the difference is exchanged.

The fixed rate is chosen so the swap costs nothing on day one. So the fixed rate is the market's best estimate of the **average overnight rate** over the period. Same reasoning as the fixed rate on a plain swap.

## Formula 1, the OIS is an average

```text
OIS ≈ average of expected overnight rates over the period
    ≈ (r1 × t1 + r2 × t2 + ... ) / T
```

- **r1, r2...** = the expected overnight rate during each piece of the period.
- **t1, t2...** = the length of each piece, in years.
- **T** = the total length.

**Example.** Overnight today, **4.00%**. 1-year OIS, **3.625%**. The market expects an average of 3.625% over the year, so cuts are coming. How many? Suppose a 25 bps (0.25%) cut every 3 months, the first in 3 months.

```text
months 0-3    4.00%
months 3-6    3.75%
months 6-9    3.50%
months 9-12   3.25%
average       (4.00 + 3.75 + 3.50 + 3.25) / 4 = 3.625%
```

That matches the OIS. We read "3 cuts priced over the year" by rebuilding the path that gives 3.625%.

## Formula 2, a cut counts according to the time left

A cut decided early weighs more in the average than a cut decided late.

```text
effect on the average = size of the cut × (time left after the decision / T)
```

With the 3 cuts of 25 bps at 3, 6 and 9 months:

| Cut | Time left | Weight | Effect on the 1-year OIS |
|---|---|---|---|
| Month 3 | 9 months | 9/12 | 25 × 0.75 = 18.75 bps |
| Month 6 | 6 months | 6/12 | 25 × 0.50 = 12.5 bps |
| Month 9 | 3 months | 3/12 | 25 × 0.25 = 6.25 bps |
| Total | | | **37.5 bps** |

4.00% − 0.375% = **3.625%**. We recover the OIS.

Practical consequence. A 25 bps cut in 3 months only moves the 1-year OIS by 18.75 bps, not 25. To get "how many cuts" from an OIS, you have to account for their dates. A shorter OIS, covering only the next few meetings, gives a cleaner signal.

## Formula 3, the forward rate between two OIS

You want the expected average for a specific period. You compare two OIS of different lengths.

```text
forward = (R2 × T2 − R1 × T1) / (T2 − T1)
```

**Example.** 6-month OIS = 3.875%, 1-year OIS = 3.625%.

```text
6m forward starting in 6m = (3.625 × 1 − 3.875 × 0.5) / (1 − 0.5)
                          = (3.625 − 1.9375) / 0.5
                          = 3.375%
```

The market expects an average of 3.875% in the first 6 months, then 3.375% in the next 6. It is the same idea as the forward on the [yield curve](02-the-yield-curve.md) and the FX forward in [episode 28](28-fx-forwards.md), you get the future by comparing two horizons.

## Formula 4, from OIS to the probability of a cut

The central bank moves in 25 bps steps. The market, on the other hand, prices an **average** across possible scenarios.

```text
probability of a 25 bps cut ≈ expected cut at the meeting / 25 bps
```

**Example.** Current rate 4.00%. The expected rate after the next meeting, read from the OIS, is 3.875%.

```text
expected cut = 4.00 − 3.875 = 12.5 bps
probability  = 12.5 / 25 = 50%
```

The market prices a **50% chance of a 25 bps cut**. If the expected cut is 18.75 bps, it is 75%.

When the market is torn between 25 and 50 bps, the expected cut sits in between. For example, 37.5 bps expected means 50% of 25 bps and 50% of 50 bps.

## Formula 5, the fed funds future

Same information, futures version. The fed funds futures contract quotes a price.

```text
future price = 100 − expected average rate over the month
```

**Example.** Price 96.25, meaning an expected average rate of 100 − 96.25 = **3.75%**. A rising price means a falling expected rate, so more cuts priced. The CME FedWatch tool that everyone quotes turns these prices into probabilities with formula 4.

## Formula 6, how much you make or lose

If you think the central bank will cut more than the market prices, you **receive** the fixed rate on an OIS. You win if the market's fixed rate falls.

```text
P&L ≈ notional × DV01 per bp × change in OIS (in bps)
DV01 of a 1-year OIS ≈ notional × 0.0001 × 0.96   (duration close to 1 year, discounted)
```

**Example.** Notional $100m, 1-year OIS at 3.625%. DV01 ≈ 100,000,000 × 0.0001 × 0.96 ≈ **$9,600 per bp**. See [DV01](04-dv01.md).

| What the market does | Change in OIS | Receiver's P&L |
|---|---|---|
| One more 25 bps cut priced at 3 months | −18.75 bps | +$180,000 |
| One fewer 25 bps cut priced at 3 months | +18.75 bps | −$180,000 |
| Nothing moves | 0 | 0 |

(18.75 × 9,600 ≈ 180,000.)

A longer OIS has a bigger DV01. A 2-year OIS has a DV01 about 1.9 times that of a 1-year OIS, same logic as [duration](03-duration.md).

## Why the surprise is what counts

```text
market reaction ≈ what happened − what was priced
```

| Priced | Decision | Surprise | Reaction |
|---|---|---|---|
| 100% of a 25 cut | 25 cut | 0 | Almost none |
| 50% of a 25 cut | 25 cut | 12.5 bps more cut | Short rates fall |
| 100% of a 25 cut | No cut | −25 bps | Short rates jump |
| 100% of a 25 cut | 50 cut | +25 bps | Short rates fall hard |

And not only the decision of the day. **Forward guidance** (what the chair says about what comes next) moves the rest of the path, so the OIS on the following meetings.

## Real cases

### 1. March 2023, SVB: the market flips its pricing in 3 days

In early March 2023 the market was pricing more Fed hikes, with a terminal rate close to 5.5%. On 10 March Silicon Valley Bank failed ([episode 27](27-qe-and-qt.md)). Within days the market removed the hikes and priced cuts before the end of the year. The US 2-year yield, the most sensitive to Fed expectations, fell about 90 bps in three days (between 87 and 97 bps depending on the source and the time of measurement), its biggest three-day fall since the 1987 crash.

**The number.** A 2-year bond has a duration of about 1.9. A 0.90% fall in yield gives about +1.7% in price, so about **€170,000 gained on €10m** of notional. A trader who was receiving rates before the weekend made a huge gain, a payer took the loss.

**The lesson.** Pricing can flip within days when the nature of the risk changes. It was no longer about inflation but about financial stability.

### 2. 2024, pricing versus reality

December 2023, the Fed publishes its projections, the median member sees 3 cuts of 25 bps in 2024 (75 bps). The market goes further and prices as many as 6 or 7 cuts for the year in early 2024 (about 150 to 175 bps, depending on the date and the measure). Then inflation stays stronger than expected, and the market removes cuts over the following months.

**What happened.** The Fed cut by 100 bps in 2024 (50 bps in September, then 25 in November and 25 in December). Fewer than the market in early 2024, more than the 75 bps of the December median.

**The number.** An OIS receiver who entered when 175 bps were priced and exited when only 100 bps were left priced (for example) lost money on the pricing, even though the Fed did cut. To win you had to be right on the **number** of cuts, not only on the direction.

**The lesson.** Being right on direction is not enough. You have to be right relative to what is already priced.

### 3. September 2024, 25 or 50 bps

Ahead of the 18 September 2024 meeting, the market was torn between a 25 and a 50 bps cut. According to CME FedWatch estimates reported in the press, the probability of a 50 bps cut was about 14% the day before a Wall Street Journal article and a comment from Bill Dudley, then about 44% right after (other measures gave a bit more). In early August, after the yen shock ([episode 29](29-the-carry-trade.md)), it had reached about 70%.

The Fed cut by **50 bps**.

**The number.** With formula 4, a 44% probability of 50 bps gives an expected cut of 25 × 0.56 + 50 × 0.44 = 14 + 22 = **36 bps**. So the 50 bps cut was a surprise of +14 bps, small compared with most surprises. It was already largely priced.

**The lesson.** A big decision is not a big surprise. When pricing has converged before the meeting, the market barely moves, and what matters becomes what the chair says about the path.

## Classic pitfalls

- **"The market prices 3 cuts" without saying over what period.** With formula 2, 3 cuts over 12 months and 3 cuts by year-end do not give the same 1-year OIS.
- **Taking the OIS for an exact forecast.** It contains a small risk premium and it is the result of a price, not a survey. Useful for reading expectations, not for predicting.
- **Forgetting the meeting dates.** A cut in September weighs less on the 1-year OIS than a cut in March.
- **Confusing direction and pricing.** Being right that the Fed cuts earns nothing if it is already priced.
- **Turning a probability into a certainty.** "44%" means 56% of the market saw something else. It happens.
- **Mixing OIS and classic swap rates.** A swap on Libor or Euribor also contains bank credit risk. OIS has (almost) no credit risk, which is why it became the reference for reading expectations.

## The S&T interview angle

**"How do you know how many cuts are priced?"** You read the OIS for each meeting and look at the expected cut versus the current rate. Expected cut divided by 25 bps gives the probability of a 25 bps cut.

**"The 1-year OIS is at 3.625% and overnight is at 4.00%. What does it mean?"** The market expects an average of 3.625% over the year, so 37.5 bps below overnight on average. With 25 bps cuts, that matches 3 cuts spread at 3, 6 and 9 months.

**"Your trade if you think the Fed will cut more than the market prices?"** Receive fixed on an OIS or buy fed funds futures. I win if the pricing falls, and the size of the gain depends on the DV01.

**"Why doesn't a 25 bps cut move the 1-year OIS by 25 bps?"** Because the OIS is an average over the period. The effect is weighted by the time left after the cut.

**"What if the Fed cuts as expected?"** Nothing moves, because it was already priced. The market reacts to the surprise and to forward guidance.

**"Why OIS and not Libor?"** Because OIS contains almost no bank credit risk, so it reflects monetary policy expectations more cleanly.

## Links to previous episodes

- [The Policy Rate](26-the-policy-rate.md), the rate the OIS lets you read in advance.
- [QE and QT](27-qe-and-qt.md), SVB and the failure that flipped the pricing.
- [Interest Rate Swaps](10-interest-rate-swaps.md), an OIS is a swap, same mechanics.
- [The Yield Curve](02-the-yield-curve.md), the forward between two OIS follows the same logic as the curve forward.
- [DV01](04-dv01.md), to size the gain or loss when the pricing moves.
- [FX Forwards](28-fx-forwards.md), same forward formula between two horizons.
- [The Carry Trade](29-the-carry-trade.md), the August 2024 yen shock flipped Fed pricing.

<div class="ms-takeaway" markdown>

## Key takeaway

- An OIS is a swap whose floating leg is the overnight rate. Its fixed rate is the **expected average** overnight rate over the period.
- A cut counts according to the time left: effect = size × (time left / total length).
- Probability of a 25 bps cut ≈ expected cut at the meeting / 25 bps.
- The forward between two OIS: (R2 × T2 − R1 × T1) / (T2 − T1).
- An OIS receiver's gain ≈ notional × DV01 × change in bps.
- The market reacts to the **surprise**, not to the decision. Being right on direction earns nothing if it is already priced.

</div>
