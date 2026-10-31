<p class="ms-kicker">Episode 32</p>

# <span class="ms-outline">ETFs.</span>

## Why this episode

Everyone owns an ETF or knows someone who does. Almost nobody knows why its price stays glued to what it holds. It is an arbitrage story, like [put-call parity](14-put-call-parity.md) or the [FX forward](28-fx-forwards.md), with a formula, calculations you can redo by hand, and real cases where the mechanism broke. It is also a classic interview question.

## What an ETF is

ETF = exchange-traded fund. A fund holds a basket of assets (for example the 500 stocks of the S&P 500) and you buy a share of the fund on the stock exchange, like a stock.

Two prices matter.

- **The NAV** (net asset value). What the basket inside is actually worth, per share.
- **The market price.** What the ETF trades at on the exchange.

```text
NAV per share = (value of all assets − liabilities) / number of shares
```

If the basket is worth $5,000,000 and there are 50,000 shares, NAV is **$100**.

A traditional fund (a mutual fund) is bought and sold at NAV directly from the fund, once a day. An ETF trades between investors all day, so its price could drift away from NAV. It almost doesn't, because of one mechanism.

## Why the price stays close to NAV

Players called **authorized participants** (APs), big banks and market makers, have the right to **create and destroy** ETF shares directly with the issuer. It is done in blocks called **creation units** (for example 50,000 shares, the size varies by fund), usually **in kind**, meaning the basket is swapped for shares, not cash.

### The ETF trades above NAV (premium)

NAV $100, market price $100.40.

```text
premium = 100.40 / 100 − 1 = +0.40%
```

The AP does this.

1. Buys the basket on the market, 50,000 × $100 = $5,000,000.
2. Hands it to the issuer, who gives back 50,000 new shares.
3. Sells them at $100.40, so 50,000 × 100.40 = $5,020,000.
4. Profit = **$20,000** (before costs).

Selling all those shares pushes the ETF price down toward NAV.

### The ETF trades below NAV (discount)

NAV $100, price $99.60, a discount of −0.40%.

1. The AP buys 50,000 shares for $4,980,000.
2. Gives them back to the issuer and receives the basket, worth $5,000,000.
3. Sells the basket.
4. Profit = **$20,000**.

Buying the shares pushes the price up toward NAV.

### The limit

```text
maximum gap ≈ AP's costs (trading fees + bid-ask + hedging cost)
```

As long as the gap is bigger than the costs, the arbitrage pays, so someone does it, so the gap closes. This is the **arbitrage band**.

### The live price, iNAV

The official NAV is calculated once a day, at the close. During the session the issuer publishes an estimate, the **iNAV** (indicative NAV), recalculated every few seconds from the basket's prices. It is the APs' reference.

## Primary market and secondary market

| | Primary market | Secondary market |
|---|---|---|
| Who | APs and the issuer | All investors |
| What | Creating and destroying shares, in blocks | Buying and selling existing shares on the exchange |
| Price | At NAV (basket against shares) | Market price, with a bid-ask |

When you buy an ETF on the exchange, you buy an existing share from another investor. The ETF does not need to sell any assets. The primary market only steps in when demand or supply goes beyond what the secondary market absorbs.

## What it really costs

### Tracking difference

```text
tracking difference = ETF return − index return
                    ≈ − expense ratio + securities lending income − trading costs
```

**Example.** Index +8.00%, expense ratio 0.20%, the ETF returns +7.82%. The tracking difference is −0.18% (the fund also earned a bit by lending out its securities).

**Tracking error** is something else. It is the volatility of that gap over time. A low tracking error means the ETF follows the index closely day after day.

### The effect of fees over 10 years

$10,000 invested for 10 years with a gross return of 7% a year.

| Annual fee | Value after 10 years |
|---|---|
| 0.20% (index ETF) | 10,000 × 1.068^10 = **$19,307** |
| 1.00% (typical active fund) | 10,000 × 1.06^10 = **$17,908** |
| Gap | **$1,398**, about 14% of the starting capital |

### The bid-ask

When you buy and sell, you also pay the gap between the bid and the ask. For a liquid ETF it can be 0.01% to 0.05%. On $100,000 with a 0.04% bid-ask, a round trip costs about $40. For a thinly traded ETF it can exceed 0.5%.

## When the mechanism breaks

The arbitrage works as long as the AP can **buy and sell the basket** quickly and at a known price. In a panic, that is no longer true.

### 1. 24 August 2015, the ETF "flash crash"

On Monday 24 August 2015, the US market opened after a sell-off in Chinese markets. The S&P 500 was down about 5% at one point in the session. Many stocks opened late or were halted repeatedly (individual circuit-breaker rules), so **the basket had no reliable price**. The iNAV became wrong and APs no longer knew how to arbitrage.

According to the SEC's research note published in December 2015, about 19% of exchange-traded products (ETPs) fell 20% or more at some point in the session, against under 5% of single stocks. More than a thousand halts hit 327 ETPs. Some ETFs traded far below their NAV for a few minutes, because there was no reference price for the stocks they held.

**Why.** An ETF's price is derived from the basket. With no price for the basket, the ETF price becomes just a panic price, which corrects when the basket starts quoting again.

### 2. March 2020, bond ETFs

Bonds trade rarely, over the counter (OTC). In a panic, **the ETF can be the only thing trading**. It becomes the real "price discovery", and the NAV, calculated from stale or estimated bond prices, lags behind.

Numbers from that period.

- The US bond ETF BND (total bond market) traded about 6% below its NAV on 12 March 2020, then came back to about a 1.7% discount the next day.
- The corporate bond ETF LQD traded below its NAV by roughly 3% to 5% depending on the measure and the moment, in the week of 16 to 20 March.
- On 23 March the Fed announced it would buy corporate bond **ETFs**, a first. Right after, LQD went from a discount of about 2.8% on 20 March to a premium of about 2.9% on 23 March, while its NAV had only gained about 1.4%. ETF purchases only started several weeks later, which shows the announcement was enough.

**Why.** APs could no longer buy the bond basket, which was barely selling, so they could no longer arbitrage the discount. And the discount was not necessarily an error. It reflected that the **real** value of the bonds was lower than the displayed NAV.

**The lesson.** An ETF is only as liquid as its assets. The less liquid the underlying (corporate bonds, high yield, emerging market debt), the bigger the gap to NAV can get under stress.

## Leveraged ETFs, the effect of daily reset

A 2x ETF aims for **2 times the daily return** of the index, not 2 times over a longer period. It resets its leverage every day.

**Example.** The index rises 10% one day and falls 10% the next.

```text
Index:      1.10 × 0.90 = 0.99      so −1%
2x ETF:     1.20 × 0.80 = 0.96      so −4%
```

"2 times" would have been −2%. Three days (+10%, −10%, +10%):

```text
Index:      1.10 × 0.90 × 1.10 = 1.089     +8.9%
2x ETF:     1.20 × 0.80 × 1.20 = 1.152     +15.2%   (not +17.8%)
```

The more the index oscillates, the wider the gap. This "volatility drag" is why these products are meant for a few days, not years.

## Physical or synthetic replication

- **Physical.** The ETF actually holds the stocks or bonds of the index (or a representative sample).
- **Synthetic.** The ETF holds a different basket and enters a **swap** with a bank, which pays it the index return. Common in Europe for indices that are hard to access. One extra risk, the bank on the swap (counterparty risk, seen in the [CDS](06-credit-default-swaps.md) episode).

## Classic pitfalls

- **Buying an illiquid ETF at any price.** The bid-ask can eat several months of return. Use limit orders and look at the iNAV.
- **Trading at the open or close of a wild session.** That is when the gap to NAV is widest.
- **Confusing the ETF's liquidity with its assets' liquidity.** A bond ETF trades like a stock but its basket does not.
- **Forgetting volatility drag** on leveraged or inverse ETFs.
- **Thinking tracking error is a cost.** It is a dispersion, the cost is the tracking difference.
- **Ignoring counterparty risk** on synthetic ETFs.
- **Treating a discount as a gift.** In March 2020, the discount partly reflected a real value lower than NAV, not only a pricing error.

## The S&T interview angle

**"How does an ETF stay close to its NAV?"** Through authorized participant arbitrage. If the ETF trades above NAV, the AP buys the basket, creates shares and sells them, which pushes the price down. Below NAV, it buys shares, redeems them for the basket and sells it, which pushes the price up.

**"Why can a bond ETF trade at a much bigger discount than an equity ETF?"** Because arbitrage requires being able to buy or sell the basket. Bonds trade rarely and the NAV uses stale prices. Under stress, the ETF becomes the real price.

**"What is the difference between tracking error and tracking difference?"** Tracking difference is the cumulative return gap between the ETF and its index, roughly the fees. Tracking error is the volatility of that gap.

**"Why doesn't a 2x ETF make twice the performance over a year?"** It resets its leverage every day. When the market oscillates, compounding loses value. Example, +10% then −10% gives −1% for the index and −4% for the 2x.

**"What is a market maker's role on an ETF?"** Quote a bid-ask, hedge its risk with the basket or futures, and create or redeem shares when the gap exceeds its costs.

**"Can ETF flows move the market?"** Yes. Large creations or redemptions force APs to buy or sell the underlying basket, which weighs on its prices, especially for less liquid assets.

## Links to previous episodes

- [Put-Call Parity](14-put-call-parity.md), same arbitrage logic, two paths that must cost the same.
- [FX Forwards](28-fx-forwards.md), a price set by arbitrage and not by a forecast.
- [QE and QT](27-qe-and-qt.md), March 2020 and the Fed's purchase of bond ETFs.
- [Credit Spread](05-credit-spread.md), the corporate bonds LQD holds.
- [Credit Default Swaps](06-credit-default-swaps.md), the counterparty risk of synthetic ETFs.
- [Repo](11-repo.md), bond market liquidity under stress.

<div class="ms-takeaway" markdown>

## Key takeaway

- An ETF is a listed basket. NAV = (assets − liabilities) / number of shares.
- Its price stays close to NAV because authorized participants create or redeem shares in blocks, and pocket the gap (example, 0.40% on $5m = $20,000).
- The real cost is tracking difference (≈ expense ratio) plus the bid-ask. 0.20% versus 1.00% in fees is about $1,400 on $10,000 over 10 years.
- The arbitrage breaks when the basket has no reliable price (24 August 2015) or cannot trade (bonds in March 2020).
- Leveraged ETFs reset their leverage every day. +10% then −10% gives −1% for the index and −4% for a 2x.
- An ETF is only as liquid as its assets.

</div>
