<p class="ms-kicker">Episode 17</p>

# <span class="ms-outline">Theta.</span>

## Why this episode

Delta and Gamma were about the stock moving. Theta is different. It is what happens to the option when **nothing moves**.

## Definition

Theta measures how much value the option loses **each day that passes**, assuming the stock stays at the same price and volatility doesn't change. It is the only Greek that moves in a **certain** direction. The stock price can go up or down (unknown), but time only moves one way.

## Worked example

Call bought at €5, Theta = -0.07. Tomorrow, if the stock hasn't moved, the option is worth ~€4.93. The day after, ~€4.86. You lose money by doing nothing, just because a day has passed.

## Why the value falls mechanically

When you buy an option, you are partly paying for the **chance that the price moves in your favor before expiry**. Each day that passes, there is less time left for that to happen, so that chance is worth less. You are buying time, and the window keeps shrinking. It is the **time value** part of the premium (extrinsic value) that melts, not the intrinsic value.

**Don't confuse this** with the "time value of money" (discounting, interest rates). No connection at all. Here it is about probability and time remaining.

**How you "pay".** Nothing is debited. The loss shows up in the **mark-to-market** (the option's resale value falls). It becomes final if you sell at the lower price, or if the option expires worthless.

## Buyer vs seller

- **Buyer**: **negative** Theta. Time is the enemy, the position melts every day.
- **Seller**: **positive** Theta. Time is a friend, the seller collects this decay. That is why an options seller makes money in a calm market where nothing moves.

## The gamma vs theta deal (the central point)

Recall that being long gamma is comfortable (convexity for you in both directions), but nothing is free. Theta is the price of that comfort.

`Long gamma = convexity for you, but negative theta (daily rent paid)`

`Short gamma = convexity against you, but positive theta (daily rent collected)`

The two always go together, in opposite directions. You can't have the gamma without paying the theta, or collect the theta without taking the gamma. It is the fundamental trade-off of every options position.

## Where Theta hits hardest

Maximum for **ATM** options (where time value is largest, the knife's edge). Low for a **deep ITM** option (its value is almost all intrinsic, so there's little time value to decay). Same place as maximum Gamma (ATM), which makes sense, they are two sides of the same coin.

## Decay isn't linear

It **accelerates** as expiry approaches, especially for an ATM option. The last days of an ATM option's life are brutal, time value collapses.

<div class="ms-takeaway" markdown>

## Key takeaway

Theta = the daily decay of the option's time value. Negative for the buyer, positive for the seller. Maximum ATM, accelerates near expiry. Always the mirror of gamma, the price you pay for convexity.

</div>
