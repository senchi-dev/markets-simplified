<p class="ms-kicker">Episode 10</p>

# Interest Rate Swaps <span class="ms-outline">(IRS).</span>

## Definition

An IRS is a contract between two parties who exchange interest payments on a **notional** for a set period. No principal is ever exchanged. The notional is only used as the basis for the calculation, exactly as with the CDS.

- **Party A** pays a **fixed rate**.
- **Party B** pays a **floating rate** (indexed to a reference rate such as SOFR).

On each payment date, only the **difference** between the two amounts is actually paid (netting), not both full amounts separately.

## Worked example

Notional €10M, payment every 6 months.

**Half-year 1, SOFR at 4%.**

- Party A owes 3% × 10M / 2 = €150,000.
- Party B owes 4% × 10M / 2 = €200,000.
- Net, Party B pays €50,000 to Party A.

**Half-year 2, SOFR at 2%.**

- Party A still owes €150,000 (fixed, never changes).
- Party B owes €100,000.
- Net, Party A pays €50,000 to Party B.

The 10M notional never moves. Only the small difference changes hands on each date.

## The full use case, a company hedging itself

A company has an actual floating-rate bank loan (SOFR + 1%) on €10M, borrowed at a floating rate because it is cheaper at issuance (see episode 1). It enters a swap **paying fixed (3%)** and **receiving floating (SOFR)**.

Combining its two flows:

- On its actual loan, it pays SOFR + 1%.
- On the swap, it receives SOFR (cancels the SOFR paid on the loan) and pays 3% fixed.

SOFR cancels out perfectly on both sides, leaving only **3% + 1% = 4% fixed**, all the time, whatever SOFR does next. It has turned a variable, unpredictable cost into a fixed, predictable one, without ever touching its actual loan.

## Why not just borrow fixed directly

Several reasons add up.

**1. Total cost.** A direct fixed rate is usually more expensive at issuance (see episode 1, the certainty premium). Borrowing floating and then swapping to fixed can cost **less in total** than borrowing fixed directly.

**2. Comparative advantage.** Classic theory says two different companies each have relatively better access to a different market (one to fixed, the other to floating). If each borrows where it has the advantage and then swaps for what it really wants, both come out ahead compared with borrowing directly in the rate type they wanted.

**3. Flexibility.** You can swap only part of the notional, only for a given period, or exit the swap independently of the underlying loan. A standard fixed loan is all or nothing, and often comes with heavy prepayment penalties.

**4. Market access.** Issuing a fixed-rate bond requires access to capital markets (high fixed costs), which only pays off for large raises. A floating-rate loan is more accessible, and the swap market is liquid and cheap to use afterwards.

## Terminology, payer swap vs receiver swap

A swap is always named after what you do with the **fixed** leg, never the floating one.

- **Payer swap.** You pay fixed, you receive floating.
- **Receiver swap.** You receive fixed, you pay floating.

## Why a counterparty takes the other side

Three possible profiles.

1. **The exact mirror.** A company with actual fixed-rate debt that wants to convert it to floating (asset-liability matching).
2. **A directional bet.** A party that thinks rates will fall enters a receiver swap (collects fixed, pays a floating rate it expects to be lower).
3. **The most common case, the market maker bank.** The exact term for this role is **market maker**, an institution that makes money by facilitating trades and capturing small price differences, not by predicting the direction of rates. The bank takes the other side of the trade, collects a small margin (bid-ask spread), then immediately finds an offsetting counterparty elsewhere to neutralize its own risk. It lives off spread and volume, not a directional bet.

## What the bank earns, precisely

Not a "premium" like with the CDS (which pays for real credit risk taken). The bank quotes a fixed rate slightly worse for the client than the "fair" market rate (e.g. 3.05% instead of 3.00%), built directly into the quoted rate rather than shown as a separate fee. It then hedges immediately with an offsetting trade elsewhere, and its profit comes down to the small difference captured between the two trades.

## The legal framework

Same setup as for the CDS, the **ISDA**. The two parties sign an **ISDA Master Agreement** once (general rules), then a short **Confirmation** for each new swap (the specific terms, notional, fixed rate, floating reference, maturity). No money changes hands at signing.

## How it is executed in practice

**Historically**, everything was negotiated by phone (voice trading) between the treasurer and the bank's desk. That is still the case today for large or bespoke trades.

**Today**, most standard swaps go through electronic platforms via an **RFQ (Request For Quote)** process: the company sends its request to several banks at once (via Bloomberg, Tradeweb, MarketAxess), the banks reply with their price within seconds, and the company clicks to execute with the best offer.

Since 2008, regulators (Dodd-Frank in the US, EMIR in Europe) have pushed standardized swaps onto mandatory electronic platforms (SEFs) and central clearing (LCH SwapClear), for more transparency after the role opaque OTC derivatives played in the crisis.

<div class="ms-takeaway" markdown>

## Key takeaway

An IRS does not remove the underlying loan. It layers a second contract on top that transforms its exposure, floating to fixed or the reverse, without ever touching the borrowed principal. The cost of this transformation is a small spread hidden in the quoted rate, the bank's compensation for providing the certainty the client is looking for.

</div>
