<p class="ms-kicker">Episode 01</p>

# Fixed vs Floating Rate <span class="ms-outline">Debt.</span>

## The basic principle

When a company or a government borrows money (issues debt), it has to choose how interest will be calculated over the life of the loan. There are two possible regimes, fixed rate or floating rate.

## Fixed Rate

The interest rate is **locked in at issuance** and never moves until maturity.

**Worked example.** A company issues a 5-year bond with a 4% fixed coupon. It will pay exactly 4% a year, every year, for 5 years, no matter what happens in the markets.

**Advantages**

- **Full certainty** on future payments, which makes budgets and cash flow forecasts easy.
- Protection if rates **rise**, since you stay locked in at your favorable rate while the market pays more.

**Disadvantages**

- If market rates **fall**, you keep paying your old, higher rate. You don't benefit from the drop unless you refinance, which comes with fees.
- Less **flexibility**, because repaying early or renegotiating is often more restrictive and costly under the contract (prepayment clauses, penalties).
- Usually **more expensive at issuance** than floating rate, because the lender demands a premium to guarantee you a stable rate for the whole term (it takes on the rate risk in your place).

## Floating Rate

The rate is **reset periodically** (usually every 3 or 6 months) based on a market reference rate.

**Standard formula**

`Rate paid = Reference rate + Margin (spread)`

Today the reference rate is typically **SOFR** (Secured Overnight Financing Rate, USA) or **€STR** (Europe), which replaced LIBOR (discontinued in 2023 after the manipulation scandal). The margin reflects the borrower's own credit risk. The riskier the borrower, the wider the margin.

**Worked example.** A floating rate loan priced at "SOFR + 150 bps". If SOFR is at 4%, the borrower pays 5.50%. If SOFR rises to 5%, it pays 6.50% the following quarter.

**Advantages**

- Usually **cheaper at the start** than fixed rate.
- Easier to **refinance, restructure, or repay** early.
- Easy to **hedge** with a derivative (interest rate swap).

**Disadvantages**

- Direct exposure to **market risk**. If rates rise, payments rise too, with no ceiling (unless a cap is negotiated).
- Less predictability for cash flow.

## The bridge between the two, Interest Rate Swaps

A company can borrow at a floating rate (better terms at issuance) and then **swap** its floating payments for fixed payments through an interest rate swap with a counterparty (often a bank). The result is that it effectively pays a **synthetic** fixed rate, without having issued conventional fixed rate debt.

Why do this instead of issuing fixed rate debt directly? Because the swap market is very liquid and can sometimes offer better hedging terms than issuing fixed directly, especially for frequent issuers.

## Why do companies often borrow at a floating rate?

Two main reasons.

1. **Better terms at issuance.** Banks are naturally more willing to lend (and lend more cheaply) at a floating rate because they transfer the rate risk to the borrower.
2. **The risk is managed afterwards** with swaps, separately from the initial financing decision.

<div class="ms-takeaway" markdown>

## The intuition to remember

Fixed and floating rates are not just "two ways to calculate interest". They are a **split of rate risk** between the lender and the borrower.

- **Fixed.** The lender takes the risk that rates rise (it is stuck with a fixed return while the market pays better elsewhere), so it charges the borrower a **certainty premium**.
- **Floating.** The borrower takes the risk that rates rise, so it pays **less at the start** in exchange for bearing that risk.

</div>

## How this connects to the rest of the series

The fixed/floating distinction is the entry point to the rest of the series. Rate sensitivity (**Duration**, **DV01**) really only applies to **fixed rate** debt. A floating rate bond has a very low duration because its coupon resets before the market rate has time to move its price.

> Next up, **The Yield Curve**, the full map of rates by maturity.
