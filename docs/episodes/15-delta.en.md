<p class="ms-kicker">Episode 15</p>

# <span class="ms-outline">Delta.</span>

## Why this episode

Put-Call Parity showed that a long call + short put moves euro for euro with the stock. That exact number, how much an option moves per euro of movement in the underlying, has a name: **Delta**. It is the first of the "Greeks" (an option's price sensitivities).

## Definition, the real mechanics

Delta measures **how much an option's price moves for a €1 move** in the underlying. It is a price sensitivity, not a probability (the nuance matters, see below).

- **Call**: Delta between **0 and 1**.
- **Put**: Delta between **-1 and 0**, negative because a put gains value when the stock **falls**, not when it rises.

## Why a deep ITM option moves euro for euro, the real mechanism

Recall from the Options episode, premium = intrinsic value + time value, with `intrinsic value = Stock price − Strike` (for a call, if positive).

The strike is **fixed**, it never moves. So if the stock price moves by €1, and the option is deep enough ITM to be almost certain to be exercised, its intrinsic value moves by exactly that same €1 (you subtract a fixed number from a number that moves). That is the real mechanical reason a deep ITM call tracks the stock almost 1 for 1. It is a question of **price sensitivity**, not a probability calculation.

**Deep OTM** is the opposite. Almost no intrinsic value, the price is almost entirely time value (a small chance of a big move before expiry). A €1 move in the stock barely changes that small chance, so the option barely moves.

## Probability, a useful shortcut, not the real definition

Many traders use Delta as a **rough approximation** of the probability that the option finishes profitable (Delta 0.3 ≈ roughly a 30% chance). It is a handy mental shortcut because the numbers often look similar, but it is **not** what Delta fundamentally measures. Delta is a price sensitivity. The probability is only an approximate mental model built on top of it.

## Corrected recap, moneyness depends on the option type

|  | In the money (ITM) | At the money (ATM) | Out of the money (OTM) |
| --- | --- | --- | --- |
| **Call** | Current price **> strike** | Current price ≈ strike | Current price **< strike** |
| **Put** | Current price **< strike** | Current price ≈ strike | Current price **> strike** |

**Why it's reversed between call and put.** An ITM call means you can buy **below** the market price, so the market price must be **above** the strike. An ITM put means you can sell **above** the market price, so the market price must be **below** the strike. It's reversed because the call and the put give opposite rights.

## Delta by moneyness

- **Deep ITM**: Delta close to **1** (call) or **-1** (put).
- **Deep OTM**: Delta close to **0**.
- **At the money**: Delta around **0.5** (call) or **-0.5** (put).

**A continuous scale, not fixed steps.** Delta moves gradually between these values, not in jumps. An option that is only slightly OTM still has real sensitivity. Its Delta can be 0.3 or 0.4, not close to 0. Only a **deep** OTM option (very far from the strike) has a Delta close to 0.

**Trap to avoid.** OTM does NOT mean "moves in the wrong direction". It means "moves very little, in either direction" (see the intrinsic value mechanism above).

## Delta is NOT fixed, it changes continuously (a key point often misunderstood)

The Delta you see when you buy the option is only a **snapshot at that exact moment**, not a value set in stone for the option's whole life. It is recalculated constantly, because the probability of finishing profitable changes with every price move.

**Example.** ATM call bought, stock at €100, strike €100, Delta = 0.5 at purchase.

- Stock rises to €120: the option is now clearly ITM, Delta **rises** toward 0.8-0.9.
- Stock falls back to €80: the option is now OTM, Delta **drops** toward 0.1-0.2.

The Greek that measures how fast Delta itself changes is called **Gamma**, a good topic for a future episode.


## The direct link with put-call parity

Long call + short put (same strike) = a Delta of **1**, identical to holding the stock directly, just built from two options. It is literally the same thing as the synthetic position from the previous episode, described with the right word.

## The practical use, hedging

A trader who sells options ends up with Delta exposure to the stock, and can offset it by buying or selling the right number of actual shares to bring total Delta back to zero (being "delta neutral"). Market makers (see the IRS episode) do this continuously. They don't bet on direction. They manage their Delta all day to stay neutral while capturing their spread.

## The useful shortcut, Delta as a rough probability

Delta is often used as a **rough approximation** of the probability that the option finishes in the money. A Delta of 0.3 very roughly suggests about a 30% chance. Not exact, but a shortcut traders really use.

<div class="ms-takeaway" markdown>

## Key takeaway

Delta measures an option's sensitivity to the price of the underlying, from 0 to 1 for a call and from -1 to 0 for a put. Deep ITM behaves like the stock, deep OTM barely moves in either direction, and it is the core hedging tool for market makers.

</div>
