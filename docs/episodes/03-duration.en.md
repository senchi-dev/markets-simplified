<p class="ms-kicker">Episode 03</p>

# <span class="ms-outline">Duration.</span>

## The vocabulary trap to avoid from the start

The word "duration" hides **two related but different concepts**.

- **Macaulay duration**, a theoretical concept, measured in **years**.
- **Modified duration**, the practical version, used to measure **price sensitivity**, expressed in **%**.

Many people confuse them. You need to keep them clearly apart.

## Macaulay Duration, the weighted average time

It is the **weighted average time** at which you receive your cash flows (coupons + repayment of principal), where each date is weighted by the **present value** of that cash flow (not its face value).

**Formula (for intuition, no need to compute it by hand)**

`Macaulay Duration = Σ [ t × PV(cash flow at time t) ] / Bond price`

**Simple example, the extreme case of the zero-coupon bond.** A 5-year zero-coupon bond pays **nothing** before maturity, just one cash flow, at T=5. All the weight is on that single cash flow, so its Macaulay duration is **exactly 5 years**, the same as its maturity.

**Example with coupons.** A 5-year bond that pays a coupon every year **plus** the principal at the end has a Macaulay duration **below 5 years** (for example ~4.3 years), because part of the money comes back **before** final maturity through the coupons. The higher the coupon, the shorter the duration, since you get your money back faster.

<div class="ms-takeaway" markdown>

## The golden rule to remember

- Duration **increases** with **maturity** (longer term = higher duration, which makes sense).
- Duration **decreases** with a **higher coupon** (you are paid back faster along the way).
- A zero-coupon bond has the **maximum** possible duration for its maturity, equal to its maturity itself.

</div>

## Modified Duration, the version you actually use

This is the measure actually used on a trading floor. It gives the **approximate % price change** for a **1% (100 bps)** move in yield.

**Formula (link with Macaulay)**

`Modified Duration ≈ Macaulay Duration / (1 + yield)`

**How to use it**

`% price change ≈ − Modified Duration × change in yield`

**Worked example.** A bond has a Modified Duration of **7**. If yields rise by **1%** (100 bps), its price falls by about **7%**. If yields fall by 0.5% (50 bps), its price rises by about 3.5%.

The **negative** sign is essential. Price and yield always move in opposite directions (a reminder of the concept seen in the Yield Curve).

## Why duration is THE real measure of rate risk

Two bonds can have the same maturity but very different durations depending on their coupon. A 10-year bond with a large coupon has a duration well below 10, so it is much **less sensitive** to rate moves than a 10-year zero-coupon bond. **Maturity alone is not enough to judge rate risk, duration is.**

## Effective Duration (going further)

For bonds with **embedded options** (callable bonds, convertible bonds), the classic Modified Duration no longer works well because future cash flows can change depending on the level of rates. In that case you use **Effective Duration**, calculated by simulating yield changes and observing the actual impact on price, rather than using the analytical formula.

## Key takeaway

- **High duration**, small rate move, big price move. A "long duration" portfolio = very sensitive to rates.
- **Low duration**, rates move, the price barely reacts. A "short duration" portfolio = defensive against rate risk.
- The real risk in fixed income is not "maturity", it is **sensitivity**, in other words duration.

> Next up, **DV01**, the same sensitivity, but expressed directly in money rather than as a percentage.
