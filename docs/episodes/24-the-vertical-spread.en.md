<p class="ms-kicker">Episode 24</p>

# The Vertical <span class="ms-outline">Spread.</span>

## Why this episode

Straddles and strangles are non-directional bets on the size of the move. The vertical spread is the opposite: a **directional** bet, built to cost less and risk less than a call or a put bought on its own.

## Definition

Same expiry, same option type (two calls or two puts), two different strikes. You **buy** one and **sell** another. The premium collected on the option you sell reduces the cost, but the maximum gain becomes capped.

## The four versions

| | Calls | Puts |
|---|---|---|
| **Bullish** | Bull call spread (you pay upfront) | Bull put spread (you collect upfront) |
| **Bearish** | Bear call spread (you collect upfront) | Bear put spread (you pay upfront) |

"Bull" or "bear" = the direction you are betting on. Paying or collecting upfront = the direction of cash at entry. Paying upfront is called a **debit spread**, collecting is a **credit spread**.

## Bull call spread, step by step

Apple at 100. You buy the 100 call for 5 and sell the 110 call for 2.

- Net cost: 5 − 2 = **3**
- Max loss: **3** (the whole cost)
- Max gain: gap between strikes (10) − cost (3) = **7**
- Breakeven: 100 + 3 = **103**

At expiry:

| Apple ends at | 100 call bought | 110 call sold | Net after the cost of 3 |
|---|---|---|---|
| 95 | 0 | 0 | **−3** |
| 103 | 3 | 0 | **0** |
| 110 | 10 | 0 | **+7** |
| 130 | 30 | −20 | **+7** |

Above 110, the sold call loses exactly what the bought call gains on every extra euro. The gain stops growing at 7. That is the price of the cheaper entry.

## Why the sold call has no unlimited risk here

Options episode: a call sold on its own ("naked") has unlimited loss, because you may have to buy the stock at the market price to deliver it. Here it is not naked. You also own the 100 call, which gives you the right to buy at 100. If Apple rises to 300 and you have to sell at 110, the 100 call lets you buy at 100 to deliver. The loss on the sold leg is covered by the gain on the bought leg. Hence a max loss limited to the 3 you paid.

## Comparison with the 100 call bought alone

| | 100 call alone | Bull call spread |
|---|---|---|
| Cost | 5 | 3 |
| Max loss | 5 | 3 |
| Max gain | unlimited | 7 |
| Breakeven | 105 | 103 |

Cheaper, less risk, profitable sooner. In exchange, you give up all the gain above 110. If you expect a moderate rise (toward 110), the spread is the better choice. If you expect a very big move, the call alone is better.

## The Greeks

The sold option offsets part of the bought option, so everything is dampened (illustrative figures):

| | 100 call bought | 110 call sold | Net |
|---|---|---|---|
| Delta | +0.50 | −0.30 | **+0.20** |
| Theta (per day) | −0.07 | +0.05 | **−0.02** |
| Vega | +0.20 | −0.15 | **+0.05** |

- **Smaller delta**: less exposed to direction than a call alone.
- **Theta close to zero**: time hurts much less than with a call alone.
- **Low vega**: a vol crush hurts much less, a good answer to the trap seen in the Straddle episode.

## Credit spreads, the mirror image

**Bull put spread**: you sell the 100 put for 5, buy the 90 put for 2, and **collect 3** upfront.

- Max gain: the **3** collected (if Apple stays above 100)
- Max loss: gap (10) − credit (3) = **7** (if Apple falls below 90)
- Breakeven: 100 − 3 = **97**

You get paid first, and take a capped risk if you are wrong.

**Bear put spread** (the bearish debit counterpart): buy the 100 put, sell the 90 put. It makes money if the stock falls, with the gain capped below 90.

<div class="ms-takeaway" markdown>

## Key takeaway

Vertical spread = buy one option and sell another of the same type, same expiry, different strike. Cheaper and less risky than a single option, with a capped gain. Dampened Greeks (smaller delta, theta, vega). Debit spread if you pay upfront, credit spread if you collect.

</div>
