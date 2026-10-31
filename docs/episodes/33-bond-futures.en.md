<p class="ms-kicker">Episode 33</p>

# Bond <span class="ms-outline">Futures.</span>

## Why this episode

The bond future is the product a rates desk looks at all day. It is the most liquid tool for hedging or betting on rates, it connects directly to [repo](11-repo.md), [DV01](04-dv01.md) and the carry of [episode 29](29-the-carry-trade.md), and it is a classic S&T interview question ("what is the cheapest-to-deliver?"). It has a formula, examples you can redo by hand, and a real case where it broke (March 2020).

## First, what a future is

A future is a contract to buy or sell something at a fixed price, on a fixed date. Unlike a forward ([episode 28](28-fx-forwards.md)), it trades on an exchange and is settled **every day**.

- You post a small deposit, the **margin**.
- Every evening, the price move is paid in cash. If you are long and the price falls, you pay. If it rises, you receive. This is **mark-to-market**.

**Example.** A US 10-year Treasury future, contract size $100,000, price quoted per 100.

```text
Buy 1 contract at 110.00, the price falls to 109.00
loss = (110 − 109) / 100 × 100,000 = $1,000, paid that same day
```

The price is quoted in points and 32nds of a point. 1/32 of a point is worth 100,000 / 32 / 100 = **$31.25**. On the 10-year, the smallest quoting step (the tick) is half of that, so **$15.625**.

## A bond future

It is a contract to deliver a government bond at a future date. The problem is that a government issues many different bonds, with different coupons and maturities. So the exchange lets the seller **choose which one to deliver**, from a basket of eligible bonds (for the standard US 10-year, securities with between 6.5 and 10 years of remaining life).

To compare these bonds fairly, each one gets a **conversion factor** (CF).

```text
CF = price of the bond if it yielded 6%  (per 1 of par)
```

The 6% is a reference yield set by the exchange, not a coupon.

**Example.** A 10-year bond with a 4% coupon, valued at a 6% yield.

```text
CF ≈ 0.8512
```

The lower the coupon, the smaller the CF, because the bond is worth less at 6%.

## What the seller receives

```text
invoice price = futures price × CF + accrued interest
```

Accrued interest is the part of the next coupon the seller has already earned.

**Example.** Future at 110.00, CF = 0.85.

```text
110.00 × 0.85 = 93.50   (+ accrued interest)
```

## The cheapest-to-deliver (CTD)

The seller picks the bond that costs the least to buy compared with what they will receive. For each bond in the basket:

```text
net cost = clean price of the bond − futures price × CF
```

**Example.** Future at 110.00.

| Bond | Clean price | CF | Futures × CF | Net cost |
|---|---|---|---|---|
| A | 93.80 | 0.85 | 93.50 | **0.30** |
| B | 101.90 | 0.92 | 101.20 | 0.70 |

Bond A has the lowest net cost, so it is the **CTD**. The futures price follows the CTD bond.

That is why a bond future is not tied to one specific bond. Its price is roughly:

```text
futures price ≈ (CTD price + carry cost) / CF
```

### Which bond becomes the CTD

The CF is calculated at 6%. When market yields are **below 6%**, the CTD tends to be the bond with the **shortest duration** in the basket. When they are **above 6%**, it tends to be the one with the longest duration. When yields move and a different bond becomes the cheapest, the CTD is said to **switch**. That changes the future's sensitivity to rates, which matters for hedging.

## The basis and the implied repo

The **basis** is the net cost above. It is what you pay to hold the bond rather than the future.

The **implied repo rate** is the return you earn by buying the CTD and selling the future to deliver it.

```text
implied repo = (invoice price / bond's dirty price today − 1) × 360 / days
```

**Example.** CTD A. Dirty price today 94.80 (93.80 clean + 1.00 accrued). Delivery in 90 days, accrued then 2.00, future at 110.00.

```text
invoice price = 110 × 0.85 + 2.00 = 95.50
implied repo = (95.50 / 94.80 − 1) × 360 / 90 = 2.95%
```

Compare with the real [repo](11-repo.md) rate, what it costs to finance the bond.

| Situation | Consequence |
|---|---|
| Real repo 4.30% > implied repo 2.95% | Borrowing costs more than the trade earns. No trade. The future is expensive versus the bond. |
| Real repo < implied repo | Buy the bond (financed in repo), sell the future, pocket the gap almost risk-free. This is the **basis trade**. |

## Hedging a portfolio with futures

A future's DV01 is roughly the CTD's DV01 divided by its CF.

**Example.** CTD A has a modified duration of about 7.5, price 93.80.

```text
CTD DV01 per $100,000 of face = 93.80% × 100,000 × 7.5 × 0.0001 = $70.35
DV01 of one futures contract  = 70.35 / 0.85 = $82.76
```

A bond portfolio has a DV01 of $42,000 per basis point. To hedge it, you sell futures.

```text
contracts to sell = 42,000 / 82.76 ≈ 507
```

The duration and DV01 figures here are orders of magnitude for the example, not market data.

## Why hedge funds love the basis

The basis trade earns a tiny gap. So funds run it with **huge leverage**, financing the bond purchase in repo. It is carry ([episode 29](29-the-carry-trade.md)): a small steady gain, a big loss if it unwinds.

### March 2020

In early March 2020 the Treasury market tightened. Basis trade positions suffered losses and margin calls (on both futures and repo). Funds sold the bonds they held and bought back futures. One analysis puts the reduction in hedge funds' short futures positions at roughly $62bn between 3 and 17 March 2020, matched by an unwind of repo-financed bond positions.

That unwind pushed yields up and widened the basis, which hurt other funds. The Fed bought Treasuries in huge size, often cited at about $1.6tn between March and May 2020 (secondary source).

**A nuance.** Researchers disagree on how much the basis trade mattered. The OFR and the Dallas Fed say the unwind amplified the stress. A Cleveland Fed study argues it was more a consequence than a main cause. The safe point is that the positions were leveraged, and the unwind happened at the same time as the rest of the crisis.

## Classic pitfalls

- **Thinking a future tracks a single bond.** It tracks the CTD, which can change.
- **Forgetting the conversion factor.** DV01 and hedging are calculated with the CF.
- **Confusing future and forward.** A future is settled daily (margin calls), a forward at maturity.
- **The 6% is not a coupon.** It is a reference yield used to calculate the CF.
- **Ignoring mark-to-market.** A position that is winning on paper can drain cash if margin calls hit before the price comes back.
- **Treating the basis trade as riskless.** Without leverage it is almost riskless. With leverage of 50 or 100, it is a short position on funding volatility.
- **Using rough duration figures to hedge.** The CTD's DV01 has to be recalculated when yields move.

## The S&T interview angle

**"What is the cheapest-to-deliver?"** The bond in the eligible basket that the future's seller has the most interest in delivering, the one that minimises bond price minus futures price times conversion factor. The futures price follows the CTD.

**"What is the conversion factor for?"** To make bonds with different coupons and maturities comparable. It is the price of the bond at a 6% yield, per unit of par.

**"How do you hedge a portfolio with futures?"** I calculate the portfolio's DV01, the DV01 of one contract (the CTD's DV01 divided by its CF), and sell the number of contracts that equalises the two.

**"What is a basis trade?"** Buy the CTD bond financed in repo and sell the future. I earn the implied repo minus the real repo cost. A small gain, scaled up with a lot of leverage.

**"What happened in March 2020?"** Leveraged basis trades took margin calls during the liquidity crisis, sold their bonds, pushed yields up, and the Fed had to buy Treasuries in huge size.

**"When does the CTD switch?"** When yields move enough for another bond in the basket to become the cheapest to deliver. Below 6% yield, it tends to be the shortest duration.

## Links to previous episodes

- [Repo](11-repo.md), the financing of the basis trade and the implied repo.
- [DV01](04-dv01.md) and [Duration](03-duration.md), to calculate the number of contracts to sell.
- [FX Forwards](28-fx-forwards.md), a future is a forward settled every day.
- [The Carry Trade](29-the-carry-trade.md), the basis trade is carry with leverage.
- [QE and QT](27-qe-and-qt.md), the Fed buying Treasuries in March 2020.
- [Pricing Rate Cuts](30-pricing-rate-cuts.md), the fed funds future is the same kind of contract on the short rate.

<div class="ms-takeaway" markdown>

## Key takeaway

- A future is a standardised contract, settled daily (mark-to-market, margin).
- A bond future lets the seller choose which bond to deliver from a basket. Invoice price = futures price × CF + accrued interest.
- The CTD is the bond that minimises: price − future × CF. The future follows the CTD.
- Implied repo = (invoice / dirty price − 1) × 360 / days. If it is above the real repo, the basis trade pays.
- DV01 of one contract ≈ CTD DV01 / CF. It is used to size a hedge.
- The basis trade is leveraged carry, and it unwound in March 2020, with the Fed having to buy Treasuries in huge size.

</div>
