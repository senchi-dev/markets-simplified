<p class="ms-kicker">Episode 08</p>

# CDO <span class="ms-outline">Tranches.</span>

## The starting idea

A CDO (Collateralized Debt Obligation) takes a large pool of loans or bonds (hundreds or thousands of mortgages, for example) and slices it into tranches with different levels of risk. It is the central instrument of the 2008 crisis and of the film *The Big Short*.

## The pool vs the CDO, an important distinction

The **pool** refers only to the underlying assets themselves (the 1000 loans). The **CDO** refers to the whole structure. A bank creates an **SPV** (Special Purpose Vehicle, a separate legal entity) that buys and holds the pool, then issues the tranches sold to investors. The full picture is the pool held by the SPV, the SPV issuing the tranches, and the tranches sold to investors. Together they form the CDO.

## The tranches, all on the same pool

This point is often misunderstood. A tranche is **not** tied to a specific subset of loans. **All** tranches have a claim on the **same entire pool**. The difference between them is not "which loans" but the **order of priority** for receiving cash and for absorbing losses from that shared pool.

Analogy, a building with a flood that rises gradually. It is not that each apartment has its own separate water risk. It is the same water and the same building, but the ground-floor apartment (the equity) gets hit first, and the top-floor one (super senior) only if the water rises very high.

## The tranches, from riskiest to safest

- **Equity tranche.** Absorbs the first losses. Highest risk, highest return.
- **Mezzanine tranche.** Absorbs losses only once the equity is fully wiped out. Medium risk, medium return.
- **Senior / Super senior tranche.** Only takes losses if everything below it has been wiped out. Lowest risk, lowest return.

## Attachment and detachment points

Each tranche is defined precisely by attachment/detachment points, the range of pool losses (in %) where it starts and stops absorbing losses. Each tranche is a separate security (its own identification code, its own rating, its own coupon), documented in the prospectus at issuance. It is never ambiguous or decided after the fact.

Example on a pool with €100M of potential losses.

| Tranche | Attachment - Detachment | Typical rating |
| --- | --- | --- |
| Equity | 0% - 3% | unrated |
| Mezzanine | 3% - 7% | BBB |
| Senior | 7% - 15% | AA |
| Super senior | 15% - 100% | AAA |

## The waterfall

Incoming cash flows and losses work like a cascade (waterfall). Payments flow to the top tranche first (super senior gets paid first). Losses hit the bottom tranche first (equity gets hit first).

## The key point, correlation between the underlying loans

This structure only creates real safety for the senior tranche if the underlying loans in the pool are **not too correlated** with each other. It is not the tranches that need low correlation between them (they are sequential by construction). It is the default risk between the individual loans in the pool.

**Scenario A, low correlation.** 100 loans in different cities and sectors, with defaults that are almost independent of each other. Having dozens of simultaneous defaults is statistically very rare. Losses stay contained in the equity, and the senior is almost never hit. The AAA rating is justified.

**Scenario B, high correlation (the reality of 2008).** The loans were all US subprime, all exposed to the same single factor, US house prices. It was not 100 independent bets but one big bet disguised as 100 small ones. When prices fell everywhere at the same time, defaults came in a massive, simultaneous wave, cutting through the equity and the mezzanine, and even hitting the senior and super senior.

The rating agencies rated these CDOs as if they were Scenario A, while the economic reality was Scenario B. This is one of the central mechanisms of the 2008 crisis, and the exact bet that Michael Burry and others made in *The Big Short*.

## How you actually buy one

You pick a specific CDO, pick a specific tranche within that CDO, and buy it by paying its entry price, exactly like a bond. In exchange, you receive regular coupons funded by the pool's payments.

## How you lose money, two distinct mechanisms

**1. The actual loss (write-down).** If defaults are numerous enough to eat through all the tranches below yours and start hitting yours, the tranche takes a write-down and the amount owed is reduced. You do not get all your capital back at maturity, and/or the coupons are reduced or cut.

**2. The loss of value before any default (mark-to-market).** Same mechanism as for the CDS and the London Whale. If the market starts to believe that losses will probably reach a given tranche, that tranche's price on the secondary market falls, even if no actual default has hit it yet. As long as no actual write-down has happened, the coupon stays the same (set on the original notional). Only the resale price drops.

## Realized vs unrealized loss

As long as you do not sell, the price drop is only a paper loss (unrealized). If you hold the tranche to maturity and defaults never actually reach it, you collect all the scheduled coupons and get your full capital back. The price drop never had any real impact. The loss only becomes real if you sell at the wrong time, or if an actual write-down eventually happens.

**The 2008 accounting trap.** Banks and funds are required by accounting rules to value their positions at the current market price (mark-to-market accounting), even with no intention to sell. As soon as prices collapsed, these institutions had to report huge losses immediately, triggering margin calls and forced sales, and turning a paper loss into a very real one. This is one of the mechanisms that turned a credit crisis into a broad liquidity crisis.

<div class="ms-takeaway" markdown>

## Key takeaway

A CDO does not remove risk. It just reorganizes who takes the hit first. The real protection of the senior tranche depends entirely on an assumption about correlation between the assets in the pool, and that is exactly the assumption that collapsed in 2008.

</div>

> Next up, **The Big Short**, how Michael Burry and others identified and traded this exact flaw.
