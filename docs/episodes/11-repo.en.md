<p class="ms-kicker">Episode 11</p>

# Repo <span class="ms-outline">(Repurchase Agreements).</span>

## Definition

A repo (repurchase agreement) is a **very short-term secured loan** (often overnight), legally dressed up as two bond sale transactions.

- **Today.** Party A sells a bond to Party B and receives cash in exchange.
- **Tomorrow (or in a few days).** Party A buys the same bond back from Party B at a slightly higher price.

That small price difference is the interest on the loan, disguised as a price gap between two sales. Economically, the bond is never really sold. It serves as **collateral** to borrow cash for a short period.

## The rate IS the price gap, not a separate fee

The (overnight) repo rate is not "rate + collateral" as two separate things. The collateral secures the loan, and the interest rate is expressed entirely by the gap between the sale price and the repurchase price.

**Formula.** `Repurchase price = Sale price × (1 + repo rate × days/360)`

**Example.** Sale at €100 today, annualized repo rate 5%, overnight (1 day, days/360 convention).

`Repurchase price = 100 × (1 + 5% × 1/360) = €100.0139`

That extra €0.0139 is exactly one day of interest at 5% annualized on €100.

## Why this is NOT the same as just selling the bond

This is the most important point. In a repo, **the repurchase price is set in advance**, at signing. Whatever the bond's market price does in the meantime, it changes nothing to the agreed repurchase price.

- **Party A** (gives the bond, receives the cash) keeps **all the price risk** of the bond for the whole operation.
- **Party B** (lends the cash, receives the bond) **never** takes any price risk on the bond. It just collects its guaranteed repo rate.

An outright purchase would expose the buyer to price risk for the whole holding period, which is not what it wants if it is just parking excess cash overnight for a safe return. The repo **deliberately separates** "borrowing/lending cash" from "taking price risk on the bond".

## Repo rate vs interbank rate, two different markets

- **Interbank rate.** Banks lend to each other **without collateral** (unsecured, based on trust and counterparty risk).
- **Repo rate.** A loan **secured** by collateral (a bond).

Because a repo is secured, the risk is lower than on an unsecured interbank loan, so **the repo rate is generally lower** than the interbank rate.

**Direct link with the IRS episode.** SOFR, used in all the examples of the previous episode, is **not** an interbank rate. It is literally a **repo rate**. SOFR = **Secured** Overnight Financing Rate, "secured" because it is calculated from actual overnight repo transactions, loans backed by real bond collateral, in the US Treasury market.

This is different from the old **LIBOR**, which was **unsecured**. A small panel of banks simply reported the rate at which they thought they could lend to each other, with no actual transaction or collateral behind the number. Banks were caught reporting false rates to benefit their own positions, the LIBOR manipulation scandal, which pushed the market toward a rate based on actual secured transactions.

## How this market works in practice

It is not just two isolated players on the phone. It is a liquid market with a closely watched public benchmark rate, the **GC rate** (General Collateral rate). Banks, money market funds, dealers and the central bank all take part every day in very large size.

- **Tri-party repo.** A third-party agent (e.g. BNY Mellon) handles collateral custody and settlement between many participants, in a standardized way.
- **Central clearing (FICC).** More and more repo goes through a central clearing house, like swaps.

## GC vs Special, two rate regimes

- **General Collateral (GC) rate.** The "normal" rate, when any standard government bond will do as collateral.
- **Special.** Some specific bonds are in very high demand (often from traders who need them to cover a short position). To get them, cash lenders accept an abnormally low rate, sometimes close to zero or negative, just to get hold of that specific security.

## What sets the repo rate day to day

`Repo rate = anchored by the central bank policy rate (floor/ceiling via standing facilities) + continuously adjusted by actual supply/demand of cash vs collateral + can diverge sharply if the collateral is "special"`

## Real case, September 2019

A combination of large tax deadlines and a massive settlement of US Treasury issuance drained available cash all at once. The overnight repo rate spiked to **10%** in one night, versus ~2% normally. The Fed had to step in urgently with a massive injection of liquidity.

## The Moroccan context

In Morocco, repo is called **pension livrée** (delivered repurchase agreement), governed by **Law 24-01** (2004). Bank Al-Maghrib uses it as its main monetary policy tool (7-day advances to inject liquidity, pensions livrées to withdraw it), with a very thin private interbank market by comparison (BAM ≈ 156.6 bn MAD/day of intervention vs ~1.7 bn MAD/day of free interbank market). A forward interbank market was recently launched (February 2025) with the **MONIA** index, the Moroccan equivalent of SOFR. Primary sources, [bkam.ma](http://bkam.ma) and [ammc.ma](http://ammc.ma).

<div class="ms-takeaway" markdown>

## Key takeaway

A repo is not a sale. It is a secured loan where the repurchase price set in advance separates the financing (cash against collateral) from the price risk (which stays with the original owner). It is the market that runs short-term funding for the entire banking system, and its modern benchmark (SOFR) comes directly from it.

</div>
