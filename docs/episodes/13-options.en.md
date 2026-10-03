<p class="ms-kicker">Episode 13</p>

# Options <span class="ms-outline">(Calls & Puts).</span>

## Why this episode

Short selling has a real problem: unlimited loss. Options exist partly to solve it. They let you bet on a price move with limited risk (on the buyer's side).

## Definition

An option is a **right, not an obligation**, to buy or sell an asset at a price fixed today, called the **strike** (exercise price), before a given date called the **expiration**. To get this right, you pay a small amount upfront, called the **premium**. If it is never worth using, you simply walk away and lose only the premium, nothing more.

- **Call** = right to **buy** at a fixed price.
- **Put** = right to **sell** at a fixed price.

## The 4 possible positions

Every option has a buyer and a seller ("writer"), so there are 4 positions, not 2.

- **Long call.** Buy the right to buy. A bet on the price going up.
- **Short call.** Sell that right. A bet that the price stays low or falls.
- **Long put.** Buy the right to sell. A bet on the price going down.
- **Short put.** Sell that right. A bet that the price stays high or rises.

## Worked example, long call

Stock at €100, call strike €110, premium €5, 3-month expiry.

- Final price €130: you exercise, buy at €110, can resell at €130, gross profit €20, minus €5 premium = **€15 net**.
- Final price €95: no point exercising, the option expires worthless, loss limited to the premium = **€5**.

## The fundamental asymmetry, where the risk moves

**The buyer** (long call or long put) always has a loss **capped at the premium**. But the gain depends on the type:

- **Long call**: **unlimited** gain (a stock price can rise without limit).
- **Long put**: gain **also capped**, not unlimited, because the price can never go below 0. Max gain = strike − premium, large but bounded.

**The seller (writer)** always has a gain **capped at the premium collected**, but takes on much bigger risk:

- **Short call.** If the price rises, the seller must sell at the strike while the market price is much higher. If they don't already own the underlying ("naked call"), they must buy it back at market price to deliver, a **theoretically unlimited** loss (exactly like classic short selling). The less risky version is the **covered call** (you already own the underlying, so no forced buyback, you just give up the upside above the strike).
- **Short put.** If the price falls, the seller must buy at the strike while the market price is much lower. The loss is technically **capped** (the price can't go below 0, max loss = strike − premium), but it stays very large compared to the premium collected.

## Worked examples of the short positions

**Short call**, strike €110, premium collected €5. The price explodes to €300, you must buy back at €300 to deliver at €110, a €190 loss minus the premium = **€185 net loss**.

**Short put**, strike €90, premium collected €4. The price collapses to €20, you must buy at €90 a stock worth €20, a €70 loss minus the premium = **€66 net loss**. Absolute worst case (price at 0), max loss = 90 − 4 = **€86**, capped but huge.

## Why sell an option on purpose, two real strategies

- **Selling a put**: useful if you actually want to buy the stock, but at a lower price. It's like being paid to wait. If the price drops to the strike, you buy at the price you wanted. If not, you keep the premium without buying anything.
- **Covered call**: if you already hold the stock and think it won't rise much, it generates extra regular income.

## The exact parallel with the CDS

Same structure as the CDS (episode 6). The protection buyer pays a small premium, has a capped loss, and a big potential gain if the event happens. The protection seller collects the premium, has a capped gain, and a potentially huge loss if the event happens. Buying or selling an option follows exactly the same asymmetry.

## Moneyness, three states

- **In the money (ITM)**: exercising now would be profitable.
- **At the money (ATM)**: strike ≈ current price.
- **Out of the money (OTM)**: exercising now would lose money, so nobody exercises.

## What makes up the premium

`Premium = intrinsic value (gain if exercised now, often 0 if OTM) + time value (extrinsic value, the chance it becomes profitable before expiry)`

The most important driver of time value is **volatility**. The more volatile the underlying, the more expensive its options (calls AND puts), because there is a higher chance of a big favorable move before expiration. Options traders "trade volatility" as much as price direction.

## Bonus, put-call parity and the synthetic position (to dig into later)

A classic arbitrage relationship, `Call − Put = Stock price − Strike (discounted)`. Buying a call and selling a put with the same strike/expiry exactly recreates the exposure of being long the stock (same euro-for-euro sensitivity to the price, up to a fixed cost tied to the difference in premiums). It is useful for massive leverage (tying up €1 of net cost instead of €100 for the same exposure), and it is this equivalence, enforced by arbitrage, that keeps the prices of the call, the put and the stock consistent with each other.

<div class="ms-takeaway" markdown>

## Key takeaway

An option shifts the unlimited risk of short selling onto the option seller, in exchange for a premium. The buyer always has a capped loss, the seller carries the real risk. It is exactly the same buyer/seller logic as the CDS.

</div>
