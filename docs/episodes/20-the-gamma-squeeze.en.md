<p class="ms-kicker">Episode 20</p>

# The Gamma <span class="ms-outline">Squeeze.</span>

## Why this episode

A synthesis of several episodes: gamma, delta hedging, market makers, and the GameStop short squeeze. A concrete case where option hedging sends a stock price through the roof.

## The setup

When you buy a call, someone sells it to you, usually a **market maker**. They don't want to bet on direction, just collect their spread. So they **hedge**: having sold a call, they buy some of the stock to stay delta-neutral.

## The key mechanism, gamma

The number of shares they need to hold is **not fixed**. When the stock rises, the call they sold becomes more sensitive to the stock (its delta goes up), so they have to **buy even more shares** to stay hedged. That is **gamma** (episode 16).

## The self-feeding loop

- A crowd buys calls on a stock in huge size.
- The market makers selling them buy shares to hedge.
- That buying pushes the stock up.
- Higher stock = they need even more shares, so they buy again.
- Which pushes the stock up further.

The loop feeds itself, and the price goes vertical in a few days, driven by **hedging**, not by any real revaluation of the company.

## Gamma squeeze vs short squeeze (key distinction)

- **Short squeeze** (episode 12): short sellers forced to buy back the stock to close their positions.
- **Gamma squeeze**: market makers forced to buy the stock to hedge options they sold.

Different people, different reason. **GameStop 2021 was both at the same time**, which explains the size of the move.

## The counterintuitive point

Nobody in the loop is trying to push the price up. The market makers would rather not buy at all. They are forced to, again and again, by their own hedging.

<div class="ms-takeaway" markdown>

## Key takeaway

Gamma squeeze = a loop where massive call buying forces market makers to buy the stock to hedge, which pushes the price up, which forces them to buy even more. It is delta hedging + gamma spiraling out of control. Not to be confused with a short squeeze, even though the two can combine.

</div>
