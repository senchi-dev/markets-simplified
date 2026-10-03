<p class="ms-kicker">Episode 14</p>

# Put-Call <span class="ms-outline">Parity.</span>

## Why this episode

The Options episode treated the call and the put as two independent bets. They aren't. Their prices are tied by a strict mathematical relationship. It is also THE classic S&T interview question on options.

## Quick recap

A **call** = right to buy at a fixed price (the **strike**). A **put** = right to sell at that same fixed price. Both cost a small amount upfront, the **premium**.

<div class="ms-takeaway" markdown>

## The formula, remember this first

`Call − Put = Stock price − Strike (discounted)`

The rest of this note is just the intuition behind this equation.

</div>

## The construction, long call + short put, same strike/expiry

**Example.** Stock at €100 today, strike €100 for both, call premium €5, put premium €4. You buy the call and sell the put at the same time.

**Scenario A, final price €130.**

- Call: exercised, €30 gain, minus €5 premium paid = **+€25**.
- Short put: not exercised (nobody sells at €100 something worth €130), you keep the premium = **+€4**.
- **Total = +€29**

**Scenario B, final price €70.**

- Call: expires worthless, you lose the premium = **−€5**.
- Short put: exercised against you, forced to buy at €100 a stock worth €70, a €30 loss, offset by the €4 premium collected = **−€26**.
- **Total = −€31**

## The comparison with holding the stock directly

Stock bought directly at €100: from 100 to €130, a gain of **+€30**. From 100 to €70, a loss of **−€30**.

In both scenarios, the combined position (call + short put) moves **almost euro for euro** with the stock, offset by a constant fixed amount of **€1** (= €5 premium paid − €4 premium collected, the net cost of the structure).

## What "same exposure" really means

Not "same final result to the cent", but **same sensitivity to the price move** (the slope, 1 for 1). A €30 move in the stock produces a €30 move in the synthetic position in both directions (€29 when it rises by 30, a €31 loss when it falls by 30, the same €1 gap in both cases). That €1 is a fixed cost **known in advance**, which never depends on what the price does next, like an opening fee on an account whose interest rate stays the same.

## Synthetic position and leverage

Buying the stock directly ties up €100 of cash. The synthetic position (call + short put) costs only €1 net (plus margin on the short put, well below €100). For the **same exposure**, a tiny amount of capital tied up, so huge leverage.

## Why build this position instead of just holding the stock

Two real reasons.

1. **Leverage.** As seen above, the synthetic only ties up the small net cost of the premiums instead of the full stock price. Same exposure for much less capital.
2. **Avoiding borrowing the physical stock.** You can flip the construction (sell the call, buy the put) to create a **synthetic short**, which bets on a fall **without ever borrowing the stock**. This matters a lot when the stock is expensive or hard to borrow, exactly the "hard to borrow" problem from the short selling episode.

## The formula

`Call − Put = Stock price − Strike (discounted)`

## Why this relationship always holds, arbitrage

If the cost of the synthetic position drifted significantly from the real cost of holding the stock, arbitrageurs would immediately buy the cheaper side and sell the other, pocketing a **risk-free** profit. This constant arbitrage pressure, exactly the same mechanism as the CDS-bond basis (episode 6), keeps the call, the put and the stock consistent with each other. Parity isn't just a formula, it is the direct result of that arbitrage pressure.

## Key takeaway

Long call + short put (same strike/expiry) = a synthetic position identical to holding the stock, up to a fixed cost. Arbitrage guarantees this equivalence always holds, otherwise a risk-free profit would exist.
