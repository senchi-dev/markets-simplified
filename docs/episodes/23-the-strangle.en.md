<p class="ms-kicker">Episode 23</p>

# The <span class="ms-outline">Strangle.</span>

## Why this episode

The straddle's direct cousin (episode 22), and the comparison everyone asks about right after.

## Definition

Same setup as a straddle: you buy a call and a put, same expiry. The difference is that the two strikes are **different**, and both are **out of the money (OTM)**, one below the current price and one above.

## Why do this instead of a straddle

OTM options cost less than ATM options (see the Delta and moneyness episode). So the strangle is **cheaper to enter** than the straddle.

## Worked example

Apple at 100.

| | Setup | Cost |
|---|---|---|
| **Straddle** | call 100 + put 100 | 8 |
| **Strangle** | call 110 (premium 2) + put 90 (premium 2) | 4 |

Half the price.

## Breakevens, the real trade-off

| | Upper breakeven | Lower breakeven |
|---|---|---|
| Straddle | 108 | 92 |
| Strangle | 114 | 86 |

The strangle paid less, so it needs a **bigger** move to become profitable. The straddle makes money as soon as Apple goes above 108 or below 92. The strangle needs 114 or 86.

Strangle math: upper breakeven = call strike + total cost = 110 + 4 = 114. Lower breakeven = put strike − total cost = 90 − 4 = 86.

## The Greeks

Same profile as the straddle at entry: **delta neutral, long gamma, long vega, short theta**. The difference comes down to two things only:

- how much you pay for that exposure (less)
- how far the stock has to go before it matters (further)

<div class="ms-takeaway" markdown>

## Key takeaway

The real choice is not straddle versus strangle in the abstract. It is: how big a move do you actually expect, and is it better to pay more upfront for a lower profitability bar (straddle), or pay less but need a bigger move (strangle).

</div>
