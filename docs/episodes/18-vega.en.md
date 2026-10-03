<p class="ms-kicker">Episode 18</p>

# <span class="ms-outline">Vega.</span>

## Why this episode

Delta and Gamma were about the stock price, Theta about time. Vega is about **volatility**, the size of expected moves. We had come across volatility without covering it (Options episode, "the more volatile the stock, the more expensive the options", and the VIX).

## Definition

Vega measures how much the option's price changes when the **volatility** of the underlying moves by 1 point (1%). Volatility = how much the market expects the stock to move around in all directions.

## Why volatility pushes the price up

An option is a bet on a future move. The harder the stock moves, the higher the chance it crosses the strike and finishes profitable. So more volatility = a more expensive option, for a call **and** for a put (both benefit from a big move, each in its own direction).

## Worked example

Call at €5, Vega = 0.20.

- Volatility 20% → 21% (+1 point): option ~€5.20.
- Volatility 20% → 18% (-2 points): option ~€4.60.

And this **without the stock moving a single cent**. It is only the market's expectation of the size of future moves that changes.

## Buyer vs seller

- **Buyer**: **long vega**, gains if volatility rises.
- **Seller**: **short vega**, gains if volatility falls.

## Trading volatility, not direction (the core of the job)

With Delta you bet on **direction** (up/down). With Vega you bet on the **size** of moves, with no view on direction. Example: an election or earnings in a week. You don't know if it will go up or down, but you are sure it will move a lot. Buying options (long vega) profits from the rise in volatility whatever the final direction. A pure bet on "something is going to happen".

## Implied vs realized volatility (key distinction)

Vega reacts to **implied volatility**, the volatility the market *expects* (built into option prices today), not *realized* volatility (what actually happened in the past). An option's price can rise just because the market expects more turbulence, even if nothing has happened yet.

## The classic trap, the vol crush

Just before a big event (quarterly earnings), implied volatility is **inflated** (everyone expects movement). Once the event has passed, the uncertainty disappears and implied volatility **collapses** (the "vol crush"). The trap: a beginner buys a call before earnings, the stock rises as hoped, but the option **still loses value** because the vega collapse ate more than the price rise brought in. Right on direction, but still a loss.

## Where Vega is strongest

Maximum **ATM** and for **long expiries** (the more time left, the more room volatility has to act). Same place as max gamma and theta. They all measure the same "time value" from different angles.

<div class="ms-takeaway" markdown>

## Key takeaway

Vega = the sensitivity of the option's price to volatility. Long vega (buyer) gains if vol rises, short vega (seller) gains if it falls. It lets you bet on the size of moves with no view on direction. Watch out for the vol crush after events.

</div>
