<p class="ms-kicker">Episode 16</p>

# <span class="ms-outline">Gamma.</span>

## Why this episode

The Delta episode left a loose thread: Delta isn't fixed, it changes continuously as the price moves. Gamma measures **how fast** that change happens. It is a second-order Greek.

## Definition and the analogy that unlocks everything

- **Delta** = how fast the option's price moves when the stock moves.
- **Gamma** = how fast **Delta itself** changes when the stock moves.

Car analogy. The option's price = your position. Delta = your speed. Gamma = your acceleration (how fast your speed changes). It is a second-order sensitivity, a derivative of a derivative.

## Worked example

Stock at €100, ATM call, Delta 0.50, Gamma 0.05. A Gamma of 0.05 means that for every €1 move in the stock, Delta changes by 0.05.

- Stock 100 → 101: Delta 0.50 → 0.55
- Stock 101 → 102: Delta 0.55 → 0.60
- Stock 102 → 103: Delta 0.60 → 0.65

Delta accelerates toward 1 as the stock rises. Gamma is the number that tells you how much it climbs at each step.

## Why Gamma peaks ATM (the knife's edge)

- **Deep ITM** (stock 200, strike 100): Delta ≈ 1, barely moves when the stock moves → Gamma ≈ 0.
- **Deep OTM** (stock 50, strike 100): Delta ≈ 0, barely moves → Gamma ≈ 0.
- **ATM** (stock 100, strike 100): Delta 0.5, the option is on a knife's edge between finishing worthless and finishing profitable, and a small move swings Delta violently → **maximum Gamma**.

Gamma is strongest where uncertainty is greatest, around the strike.

## Long gamma vs short gamma, the mechanism

Simple rule: "long/short gamma" isn't a product you buy. It is a consequence of owning or having sold options.

- **Buying** an option (call OR put) → **long gamma**.
- **Selling** an option (call OR put) → **short gamma**.

**Vocabulary trap.** "Long/short" here does NOT refer to betting on a rise or a fall. A call buyer AND a put buyer are both long gamma. It is about owning optionality, not direction.

**Long gamma, the curve works for you.** You buy a call, stock at €100, Delta 0.5.

- Stock rises to €110 → Delta climbs to 0.7, you gain faster per euro.
- Stock falls to €90 → Delta drops to 0.3, you lose more slowly per euro.

In both directions, the change in Delta works in your favor. It is literally the **convexity** of bonds (DV01 episode).

**Short gamma, the mirror image.** The seller gets everything in reverse: losses that accelerate, gains that slow down on big moves. The premium collected is the compensation for accepting this negative convexity.

## The real practical issue, re-hedging (gamma scalping)

The market maker sells options and hedges by buying/selling the stock to stay delta-neutral. But Delta changes all the time (that's Gamma), so the hedge never holds. They have to re-hedge continuously.

**The short gamma trap.** The stock rises → they must buy stock to rebalance (buying **high**). The stock falls → they must sell (selling **low**). They are condemned to "buy high, sell low" on every re-hedge, so they **lose** on this dance, offset by the premium collected.

The buyer (long gamma) does the opposite, "buy low, sell high", and **gains** on re-hedging, which they pay for through time decay (**Theta**, a future episode).

## The time dimension

For an ATM option, Gamma **explodes** as expiration approaches. A few hours before expiry, an ATM option is almost a coin flip that will resolve very quickly into 0 or 1, and the slightest move swings Delta between ~0 and ~1. Huge Gamma, very dangerous for a seller to manage.

## The real-world link, the gamma squeeze (GameStop)

There was a gamma component in the GameStop short squeeze. The crowd bought calls massively. The market makers who sold them were short gamma and had to hedge by **buying the stock**, which pushed the price up, which increased their Delta (through Gamma), which forced them to buy even more. A self-feeding loop, a **gamma squeeze**, which amplified the 2021 surge.

<div class="ms-takeaway" markdown>

## Key takeaway

Gamma measures how fast Delta changes. Maximum ATM (knife's edge), close to 0 at the extremes. Buying an option = long gamma (convexity for you), selling = short gamma (convexity against you, offset by the premium). It is the engine behind market makers' constant re-hedging.

</div>
