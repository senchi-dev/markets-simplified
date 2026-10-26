<p class="ms-kicker">Episode 29</p>

# The Carry <span class="ms-outline">Trade.</span>

## Why this episode

[Episode 28](28-fx-forwards.md) showed that the forward is **covered**. You lock the exchange rate, so you earn nothing more than the risk-free rate. The carry trade is exactly the same setup **without the hedge**. You keep the interest rate gap, and you take the currency risk. It is one of the most widely used strategies in the market, and it has a very particular shape of risk, small steady gains and big sudden losses.

## Definition

You borrow in a **low**-rate currency (the funding currency), exchange the money into a **high**-rate currency, invest it, and **do not hedge** the exchange rate. You collect the rate gap, the **carry**, as long as the exchange rate does not move against you.

The classic version for years, borrow in **yen** (rate near 0%) and invest in **dollars** (4% to 5%). The yen even has a name in this role, the funding currency. People talked about "Mrs Watanabe", the Japanese retail savers who put their money abroad.

## The worked example

USD/JPY = 150 (1 dollar costs 150 yen). Yen rate **0.5%**, dollar rate **4%**.

**Today.**

```text
You borrow ¥15,000,000 at 0.5%
You exchange: 15,000,000 / 150 = $100,000
You invest $100,000 at 4%
```

**In 1 year.**

```text
You have:  $100,000 × 1.04     = $104,000
You owe:   ¥15,000,000 × 1.005 = ¥15,075,000
```

You hold dollars and you owe yen. Everything depends on the exchange rate in a year.

| USD/JPY in 1 year | $104,000 are worth | You repay | Result in yen | In dollars | On $100,000 |
|---|---|---|---|---|---|
| 160 (dollar up) | ¥16,640,000 | ¥15,075,000 | +¥1,565,000 | +$9,781 | +9.8% |
| 150 (unchanged) | ¥15,600,000 | ¥15,075,000 | +¥525,000 | +$3,500 | +3.5% |
| 144.95 | ¥15,075,000 | ¥15,075,000 | 0 | 0 | 0% |
| 140 (yen up) | ¥14,560,000 | ¥15,075,000 | −¥515,000 | −$3,679 | −3.7% |
| 130 (yen way up) | ¥13,520,000 | ¥15,075,000 | −¥1,555,000 | −$11,962 | −12.0% |

A 6.7% move in the yen (150 to 140) wipes out a whole year of interest, and more.

## The break-even is the forward

At what rate do you earn nothing?

```text
104,000 × X = 15,075,000
X = 15,075,000 / 104,000 = 144.95
```

That is **exactly the forward rate** from the previous episode (150 × 1.005 / 1.04 = 144.95).

So the carry trade is a **bet that the exchange rate in a year will be better than the forward**. Not better than spot, better than the forward.

### Same trade, forward version

You can run the same trade without borrowing or investing anything. You **buy USD/JPY forward** at 144.95. In a year, if spot is at 150, you buy at 144.95 and sell at 150:

```text
profit = 150 − 144.95 = ¥5.05 per dollar  ->  5.05 / 144.95 ≈ 3.5%
```

Same result as the borrow and invest setup (3.5%). That is why on a desk people say "long USD/JPY forward" to mean "running carry". The forward points (−505 pips, episode 28) are the price of being long the high-rate currency, and the trade wins if spot ends above the forward.

## Why it works (most of the time)

[Episode 28](28-fx-forwards.md) said that **uncovered interest parity** (UIP) predicts the high-rate currency should weaken by exactly the rate gap. If that were true, the carry trade would earn zero on average.

In practice it is false. Studies (starting with Fama, 1984) show high-rate currencies weaken **less** than the rate gap, sometimes not at all. That is the "forward premium puzzle". So the carry trade has made money on average over decades.

### Why the market lets that exist

The most common answer is that carry is the **payment for taking a risk**, like the insurance you sell. You collect a small premium every year, and in exchange you accept losing a lot when the market panics. Carry behaves like selling an option, whose payoff we saw in [episode 13](13-options.md) (small premium, big possible loss).

Other explanations put forward. Central banks smoothing exchange rates. Investors reacting too slowly to rate gaps. Corporate hedging flows. Nobody has a definitive answer.

## How it loses, the sudden losses

The gains are **small and steady** (a few % a year). The losses are **big and abrupt**. Traders say carry goes up the stairs and comes down the elevator. Carry returns have "negative skew", lots of small gains and rare very large losses.

### Leverage

Almost nobody runs carry without leverage, because 3.5% a year is small. With leverage:

| Leverage | Gain if nothing moves (3.5%) | Loss if USD/JPY goes to 140 (−3.7%) |
|---|---|---|
| 1x | +3.5% | −3.7% |
| 5x | +17.5% | −18.4% |
| 10x | +35% | −36.8% |
| 20x | +70% | −73.6% |

At 20x leverage, a 6.7% move in the yen destroys three quarters of the capital. And FX brokers force-liquidate well before that.

### The unwind spiral

Everyone runs the same trade, borrowing yen and selling it. When something scares the market:

1. Investors close their positions, so they **buy back yen** to repay their loans.
2. Buying yen pushes it up.
3. A stronger yen makes the other carry traders lose money, so they close too (margin calls, stop-losses).
4. The yen goes up even more.

It is the same mechanism as the UK pension fund spiral in [episode 27](27-qe-and-qt.md) (forced selling moves the price, which forces more selling). It is also the same as the gamma squeeze in [episode 20](20-the-gamma-squeeze.md), where some people's hedging feeds the move that forces others.

## When it went wrong

### 1. October 1998, after LTCM

In the summer of 1998 Russia defaulted on its debt and the fund LTCM collapsed ([episode 25](25-black-scholes.md)). Hedge funds, which had borrowed yen to fund positions everywhere, unwound all at once. On 7 and 8 October 1998, USD/JPY went from about 135 to about 112 in two days, a yen roughly 15% stronger.

**Why.** Carry positions were huge and concentrated in the same funding currency. When funds needed cash elsewhere, they all bought back yen at the same time.

### 2. 2008, AUD/JPY

Australia had rates around 7%, Japan around 0.5%. AUD/JPY was the most popular carry pair. It was worth about 107 in July 2008 and about 55 in October 2008. Almost half its value in three months.

**Why.** The Lehman crisis sent everyone into safe currencies (yen, dollar) and out of high-rate currencies. Over those three months, the carry earned (about 6.5% a year, so about 1.6% over the period) counted for nothing against a 45% fall.

### 3. January 2015, the Swiss franc

Since 2011 the Swiss central bank (SNB) had held a floor at 1.20 francs per euro. Swiss rates were very low. Many households in Poland, Hungary and other Eastern European countries had borrowed **in Swiss francs** for their mortgage, because the rate was lower than a loan in local currency. Without knowing it, they were in a carry trade, **borrowed in francs, earning in zloty or forint**.

On 15 January 2015 the SNB dropped the floor without warning. The franc rose up to about 30% against the euro within minutes, and ended the day roughly 15% to 20% higher.

**Consequences.** These households' debt rose by the same amount overnight, while their salaries stayed in local currency. FX brokers went bust the same day because clients' losses were bigger than their deposits (for example Alpari UK, and FXCM had to be rescued). The common thread, a position that earns a small carry for years, with a central bank hiding a jump risk.

### 4. August 2024, the yen

For years, investors around the world had borrowed in yen. At the end of July 2024 the Bank of Japan raised rates and hinted at more hikes. At the same time the Fed signalled cuts, so the rate gap was narrowing from both sides. USD/JPY went from about 162 in early July to about 142 on 5 August, a yen roughly 14% stronger. The Nikkei lost about 12% on 5 August, its worst session since 1987, then almost fully rebounded over the following days.

**Why.** The rate gap that justified the trade was shrinking (less carry), and the yen was rising (currency loss). Both effects worked in the same direction, so positions closed at the same time.

## How to judge whether carry is attractive

### The carry to volatility ratio

Earning 3.5% does not mean the same thing if the pair moves 5% a year or 15% a year.

```text
carry / vol ratio = rate gap / volatility of the exchange rate
```

**Example.** Rate gap 3.5%.
- If USD/JPY implied volatility is 7%, ratio = 3.5 / 7 = 0.5.
- If it is 14%, ratio = 3.5 / 14 = 0.25.

With the same rate gap, the trade is half as attractive when volatility doubles. Traders look for a high ratio, and a falling ratio (rising volatility) is a warning sign.

### What options say

In [episode 21](21-the-volatility-skew.md) we saw that put and call prices are not symmetric when the market fears one direction. For a carry pair, the market pays more to protect against a **fall in the high-rate currency** (so against the unwind). You read it in the **risk reversal**, the difference in implied volatility between a put and a call of the same delta. When the risk reversal becomes very lopsided, the market is pricing unwind risk.

### Hedging with options

You can buy a put on the high-rate currency (here a USD/JPY put, which gains if the dollar falls against the yen) to cap the loss. It costs premium, which eats part of the carry. It is [episode 13](13-options.md) applied to FX. The trade becomes carry with a loss floor, and its profitability depends on the ratio between the carry received and the premium paid.

## Carry is not only FX

The word "carry" generally means **what you earn if nothing moves**.

| Market | What the trade does | The carry | The risk |
|---|---|---|---|
| FX | Long the high-rate currency, short the low-rate one | The rate gap | The unwind, a currency jump |
| Bonds | Buy a long bond funded in short [repo](11-repo.md) | The coupon minus the repo cost | Rates rise ([duration](03-duration.md)) |
| Yield curve | Pay or receive in a [swap](10-interest-rate-swaps.md), sit on the slope of the [curve](02-the-yield-curve.md) | Roll-down (the bond gets closer to maturity and slides down the curve) | The curve moves |
| Credit | Sell protection on a [CDS](06-credit-default-swaps.md) | The premium received | Default |
| Options | Sell an option, see [theta](17-theta.md) | The premium that decays | The big move |

Same structure every time. A small steady income, against a big rare loss.

## Classic pitfalls

- **Thinking carry is a free gain.** As long as you do not hedge, it is not riskless at all. The gain is payment for currency risk.
- **Comparing to spot instead of the forward.** The break-even is the forward (144.95), not spot (150). That small gap is the difference between winning and losing.
- **Forgetting leverage.** The numbers on unlevered carry are small. Leverage is what makes the trade attractive, and what makes it dangerous.
- **Jump risk on a managed exchange rate.** When a central bank defends a floor or a cap (Swiss franc in 2015), the risk is hidden until the day it jumps all at once.
- **Trusting recent volatility.** Volatility is low just before unwinds, because carry is working well. A very high carry to vol ratio can be a sign of complacency rather than a good deal.
- **Costs.** Bid-ask, funding the leverage, daily rollover. On 3.5% of carry, they matter.

## The S&T interview angle

**"What is a carry trade?"** Borrowing in a low-rate currency, investing in a high-rate currency, without hedging the exchange rate. You earn the rate gap as long as the high-rate currency does not weaken by more than that gap.

**"Where is the break-even?"** At the forward rate. If the final spot is better than the forward, the trade wins, otherwise it loses.

**"Why does it work, when uncovered parity says the opposite?"** High-rate currencies weaken on average by less than the rate gap (forward premium puzzle). Carry is also payment for taking unwind risk.

**"What is the risk profile?"** Small steady gains, big abrupt losses. Negative skew, like selling an option.

**"Why do losses all arrive at the same time?"** Everyone runs the same trade, so when a shock hits, everyone closes at once, which moves the price against everyone else. A spiral of forced selling.

**"Give examples."** 1998 after LTCM, 2008 AUD/JPY, 2015 Swiss franc, August 2024 yen.

**"How do you hedge it?"** With a put on the high-rate currency. It caps the loss but eats part of the carry.

**"What is the difference between a carry trade and a forward?"** A forward is covered, so it earns nothing more than rates. Carry is not covered, so it can win or lose. Carry is a bet that the final spot will be better than the forward.

## Links to previous episodes

- [FX Forwards](28-fx-forwards.md), the carry break-even is the forward.
- [QE and QT](27-qe-and-qt.md), the same forced-selling spiral, and rate gaps between countries come from central banks.
- [The Policy Rate](26-the-policy-rate.md), rate decisions create and destroy the gaps.
- [Options](13-options.md), carry looks like selling an option, and an option can hedge it.
- [Volatility Skew](21-the-volatility-skew.md), the risk reversal reads the fear of an unwind.
- [Theta](17-theta.md), selling options is carry too.

<div class="ms-takeaway" markdown>

## Key takeaway

- A carry trade is borrowing in a low-rate currency and investing in a high-rate currency, without hedging the exchange rate.
- The break-even is the forward rate. The trade wins if the final exchange rate is better than the forward.
- It wins on average because high-rate currencies weaken less than the rate gap, but that is payment for a risk.
- The profile is small steady gains, big sudden losses. Leverage amplifies both.
- Losses arrive together because everyone runs the same trade and exits at the same time (1998, 2008, 2015, 2024).
- Carry is not only FX. It is also bonds funded in repo, selling CDS and selling options.

</div>
