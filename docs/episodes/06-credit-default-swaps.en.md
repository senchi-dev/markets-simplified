<p class="ms-kicker">Episode 06</p>

# Credit Default Swaps <span class="ms-outline">(CDS).</span>

## Definition

A **CDS (Credit Default Swap)** is **insurance against the default** of an entity (company or government). The protection buyer pays a regular premium. In exchange, if the reference entity defaults, the protection seller covers the loss. This lets you **trade credit risk directly**, without ever needing to hold the underlying bond.

**Full analogy.** It works exactly like car insurance. You pay a premium every year (even if nothing happens), and if you have an accident (the default), the insurer pays you back. The difference with real insurance is that you can buy a CDS on a company **even if you never lent it any money**. This is called a "naked CDS", like buying insurance on your neighbor's house. It became famous for its role in the 2008 crisis, when banks were betting on the default of entities without necessarily holding their debt.

## The two parties to the contract

- **Protection buyer.** The one who wants to hedge (or bet on a credit deterioration). They pay the premium.
- **Protection seller.** The one who takes on the risk in exchange for the premium, betting that the entity will not default. They collect the premium as long as nothing happens, but must pay a large amount in case of default.

## The two "legs" of the contract

A CDS rests on two opposite payment flows.

### 1. Premium leg

The buyer pays a regular premium (quarterly or annual depending on the contract) to the seller, as long as nothing happens. This premium, expressed in bps per year of the notional, **is the CDS spread**. A small, predictable, recurring flow.

### 2. Contingent leg

"Contingent" means conditional. This payment only happens **if** a credit event occurs. If the entity defaults, the seller makes **a single payment** to the buyer to cover their loss. This flow happens zero times (nothing happens) or once (default).

## What exactly is a "credit event"?

CDS contracts are standardized by **ISDA** (International Swaps and Derivatives Association). The credit events that trigger a payment typically include **bankruptcy**, **failure to pay** (missing a coupon or principal payment), and **restructuring** (forced restructuring of the debt, e.g. a cut in principal or coupons imposed on creditors).

An ISDA committee (the Determination Committee) officially decides whether a credit event has occurred, which triggers the settlement process.

## The payout (settlement of the contract)

`Payout = (1 − Recovery rate) × Notional`

The **notional** is the amount of debt the contract covers. It is the calculation base. Nobody exchanges this amount directly, it is only used to calculate the premium and the payout. The **recovery rate** is what the creditor gets back through the **liquidation** of the defaulted company's assets (buildings, inventory, patents, cash...). The CDS covers **the rest**, in other words the actual loss.

**Example.** You are owed €100. Recovery rate = 40%, you get €40 back through the liquidation, so you actually lose €60. The CDS pays that €60 (= (1 − 40%) × €100).

## Recovery rate, model assumption vs market reality (classic pitfall)

There are **two different recovery rates**, and you should not confuse them.

1. **The "standard" 40%** is a **market convention** used to *estimate/price* a CDS before any actual default, a historical average observed on senior corporate debt.
2. **The actual recovery rate** is set at the time of the real default through an **organized auction (ISDA auction)**, where the market collectively sets the true recovery value. This number can be very different from the assumed 40% (sometimes 60%, sometimes 5%).

**The CDS always pays on the ACTUAL recovery, never on the theoretical 40%.**

### If you are hedged, you are protected against the actual loss, whatever the actual recovery

If you hold the bond **and** you bought a CDS on it, there are two possible scenarios.

- Actual recovery = 40% → the bond loses 60, the CDS pays 60, net = 0.
- Actual recovery = 0% (worse than expected) → the bond loses 100, the CDS pays **100** (since it pays (1−0%) = 100%), net = 0 all the same.

The CDS pays you back your **actual** loss, not a loss based on a fixed assumption. That is what makes it valuable as a hedge.

## Asset or liability? (the accounting side of a CDS)

A CDS is a derivative whose value changes depending on which side you are on and on spread moves.

- **Protection buyer.** If the credit spread widens (perceived risk goes up), the position **gains value** for them, so it is an **asset**.
- **Protection seller.** In the same scenario, they owe more and more value to the other side, so it is a **liability** for them.

Classic insurance logic. For the policyholder with a claim, the policy is worth gold. For the insurer, it is a debt it has to honor.

## The CDS spread, how it is set

The CDS spread is not arbitrary. It is set so that the contract is **fair** at signing. What the buyer pays on average must equal what the seller expects to pay out.

## CDS spread vs bond credit spread, and the "basis"

Both measure the **same** underlying credit risk, so they stay close through **arbitrage** (if the gap gets too wide, traders buy one and sell the other to capture the profit, which pulls them back together).

**CDS-bond basis = CDS spread − Bond credit spread.** It is literally "the spread between the two spreads".

- Basis close to 0, the two markets agree.
- Basis different from 0, there are real frictions. The bond may be illiquid, hard to short, or have funding costs different from the CDS.

**The CDS is a "purer" signal** of credit risk. It does not need the bond (no funding cost to hold it), which removes part of the liquidity noise found in the classic bond credit spread.

## Implied probability of default (without any statistics)

The logic is the **break-even** point. What the seller collects on average must equal what they expect to pay out.

`Spread = PD × (1 − Recovery)`, where **PD** stands for **Probability of Default** (annual probability of default).

You isolate PD by dividing both sides by (1 − Recovery).

`PD = Spread ÷ (1 − Recovery)`

**Full example.**

- Spread = 3% (300 bps)
- Recovery = 40%, so (1 − Recovery) = 60%
- `PD = 3% ÷ 60% = 5%` implied probability of default per year.

**Intuition check (no formula).** You pay €3 a year, and if there is a default, you receive €60. For paying 3 to be "fair" against receiving 60, the chance of default has to be about 3/60 = 1/20 = **5%**. A market price translates directly into a probability.

<div class="ms-takeaway" markdown>

## Key takeaway

A CDS lets you take a view on credit risk **without ever holding the bond**, and its price (the spread) is literally **the market's estimate** of an entity's probability of default.

</div>

> Next up, **CDS Indices (CDX & iTraxx)**, the same principle, but applied to a basket of 125 companies in a single contract.
