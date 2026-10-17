<p class="ms-kicker">Episode 28</p>

# FX <span class="ms-outline">Forwards.</span>

## Why this episode

The last two episodes ([the policy rate](26-the-policy-rate.md), [QE and QT](27-qe-and-qt.md)) explained how each central bank sets the price of money in its own currency. This episode opens the foreign exchange market (FX) through the most direct link with all that. The gap between two countries' interest rates sets the price at which you can exchange those two currencies in the future. Not a forecast, an arbitrage calculation you can redo by hand.

## Reading an exchange rate

**EUR/USD = 1.10** means 1 euro costs 1.10 dollars.

- The first currency (EUR) is the **base currency**. You always price 1 unit of the base.
- The second (USD) is the **quote currency**, the one the price is written in.
- If EUR/USD goes to 1.12, you get more dollars for 1 euro, so the euro got stronger and the dollar weaker.
- If EUR/USD goes to 1.08, the euro got weaker.

### The pip

A **pip** is the 4th decimal, 0.0001. Going from 1.1000 to 1.1050 is a 50 pip move. Exception, for pairs with the yen (USD/JPY = 150.00) the pip is the 2nd decimal, 0.01, because one yen is worth very little.

### Bid, ask and spread

A bank always quotes two prices, for example EUR/USD 1.1000 / 1.1002.

- **Bid** (1.1000), the price at which the bank buys euros for dollars.
- **Ask** (1.1002), the price at which it sells them.
- The gap (2 pips) is the bank's margin. On the big pairs it is tiny, on thinly traded currencies it can be tens of pips.

### Quoting conventions

You do not choose the order of the currencies freely. The market follows a hierarchy. EUR comes before GBP, which comes before AUD, NZD, USD, CAD, CHF, then JPY. Hence EUR/USD, GBP/USD, USD/JPY, USD/CHF. The dollar is the base against most other currencies, but not against the euro or the pound.

### Market size

FX is the largest financial market in the world. The BIS triennial survey (the BIS is the central banks' bank) measured about $7.5tn traded **per day** in April 2022, about half of it in FX swaps (see below). The dollar is on one side of roughly 9 trades out of 10.

## Spot and forward

- **Spot.** You exchange today, at today's rate. In practice settlement happens 2 business days later (T+2), with a few exceptions like USD/CAD (T+1).
- **Forward.** You agree today on a rate, but the exchange happens later, for example in 1 year. Nothing changes hands before that date. The rate is locked.

## The question

EUR/USD is at 1.10 today. What rate should a bank give you to exchange in 1 year?

You might think it guesses where the euro will be in a year. It does not guess anything. It only uses the spot rate and the interest rate in each currency.

## The example, two paths

You have **€100** and want dollars in 1 year.

- Interest rate on euros, **2%** a year.
- Interest rate on dollars, **4%** a year.
- Spot, **1.10**.

**Path 1, exchange now, then save in dollars.**

```text
€100 × 1.10 = $110 today
$110 saved at 4% for 1 year -> 110 × 1.04 = $114.40
```

In a year you have **$114.40**.

**Path 2, save in euros, then exchange in a year.**

```text
€100 saved at 2% for 1 year -> 100 × 1.02 = €102
In a year you exchange €102 at the forward rate F -> 102 × F dollars
```

### Why both paths must give the same amount

Both paths have zero risk. From day one you know exactly what you will get.

If path 1 gave more dollars than path 2, everyone would do path 1 and the reverse of path 2 at the same time (borrow dollars, exchange into euros, save in euros, sell them back at the forward), and make money with no risk. Banks would lose every time. So the forward rate is set so that both paths give exactly the same result.

```text
102 × F = 114.40
F = 114.40 / 102 = 1.1216
```

The 1-year forward is **1.1216**.

## The formula

It is the same calculation written in general. It is called **covered interest parity** (CIP).

```text
Forward = Spot × (1 + quote currency rate × T) / (1 + base currency rate × T)
```

- **T** = time in years (6 months = 0.5, 3 months = 0.25).
- The **quote** currency's rate (the 2nd one) goes on **top**. The **base** currency's rate (the 1st one) goes at the **bottom**.

For EUR/USD, the dollar is the quote currency.

```text
1 year   : 1.10 × (1 + 0.04) / (1 + 0.02)             = 1.1216
6 months : 1.10 × (1 + 0.04 × 0.5) / (1 + 0.02 × 0.5) = 1.10 × 1.02 / 1.01 = 1.1109
```

For more than a year you use compounded rates, (1 + r)^T instead of (1 + r × T). And on a desk you count days exactly, with each currency's convention (actual days / 360 for the dollar and the euro, actual days / 365 for the pound).

## What it means

In a year you get 1.1216 dollars per euro instead of 1.10. On the forward, the euro is worth a bit more and the dollar a bit less.

The rule, **the currency with the higher interest rate is cheaper on the forward**. It trades at a **forward discount**. The other trades at a **forward premium**.

Why? Dollars pay 2% more than euros. If the forward did not adjust, you would switch your euros into dollars, earn the extra 2%, and lock in your way back into euros with the forward, with no risk at all. The forward takes exactly that 2% back. No free lunch.

### Forward points

The gap between forward and spot is called the **forward points**.

```text
1.1216 − 1.10 = 0.0216 = 216 pips
```

On a screen, banks do not quote the full forward. They quote the spot and the points (+216). The full forward (1.1216) is called the **outright**.

Quick approximation, the points are roughly spot × rate gap × T. Here 1.10 × 2% × 1 = 0.022, so about 220 pips.

## Second example, USD/JPY

Spot USD/JPY = 150. Dollar rate 4%, yen rate 0.5%. Here the dollar is the **base** currency, so its rate goes at the bottom.

```text
1-year forward = 150 × (1 + 0.005) / (1 + 0.04) = 150 × 1.005 / 1.04 = 144.95
```

The forward is **lower** than spot. That makes sense, the base currency (the dollar) has the higher rate, so it is the one trading at a discount. Forward points, 144.95 − 150 = −5.05 yen, so −505 pips (a yen pip is 0.01).

Same rule, the currency that pays more is cheaper in the future. Only the way it shows up in the number changes, depending on whether it is the base or the quote.

## The forward is not a forecast

This is the most important and most misunderstood point. The 1.1216 forward does **not** say the market thinks the euro will rise. It is just the result of the arbitrage. If the rates were the other way around (euro at 4%, dollar at 2%), the forward would be below spot, whatever the market thinks of the euro.

The "forecast" version of the formula exists, it is **uncovered interest parity** (UIP). It would say the higher-yielding currency will weaken by the rate gap. In practice it does not work. Studies show high-yielding currencies tend not to weaken that much, and sometimes even rise (the "forward premium puzzle", Fama, 1984). That is what makes the carry trade possible, borrowing in the low-rate currency and investing in the high-rate one, while keeping the currency risk. It often earns a little, and sometimes loses a lot at once.

**An example of that, August 2024.** For years, investors borrowed in yen (rates near zero) to invest in dollars and elsewhere. At the end of July 2024 the Bank of Japan raised rates and the yen rallied. USD/JPY went from about 162 in early July to about 142 on 5 August. Those who had borrowed in yen had to pay back more, they all cut their positions at the same time, which pushed the yen up further. On 5 August 2024 the Nikkei lost about 12% in one session.

Key difference. The forward (CIP) is **covered**, so there is no currency risk, and arbitrage makes it hold. The carry trade (UIP) is **not covered**, so you take the currency risk, and nothing forces the formula to hold.

## Who uses it

### A company hedging its FX risk

A French company will receive $10m in 1 year. Its costs are in euros. It does not know what the dollar will be worth in a year, so it sells its dollars forward today, at 1.1216.

```text
$10,000,000 / 1.1216 = €8,915,835
```

| EUR/USD in 1 year | Unhedged | With the forward |
|---|---|---|
| 1.00 | €10,000,000 | €8,915,835 |
| 1.1216 | €8,915,835 | €8,915,835 |
| 1.25 | €8,000,000 | €8,915,835 |

With the forward it knows its number to the cent. It gives up the good case (1.00) to protect itself from the bad case (1.25). It is the same trade-off as an [interest rate swap](10-interest-rate-swaps.md), you swap uncertainty for a fixed number.

### The FX swap, a loan in disguise

An **FX swap** combines two operations in one trade. An exchange at spot today, and the reverse exchange at the forward later.

**Example.** A European bank needs dollars for 3 months. It gives €100m and receives $110m today at the 1.10 spot. In 3 months it gives the dollars back and gets its €100m back, at the forward rate fixed today.

In practice it is a **dollar loan secured by euros**. Exactly like a [repo](11-repo.md), where you borrow cash against securities as collateral, except that here the collateral is another currency. The cost of the loan is hidden in the forward points.

It is the most traded FX product in the world. Non-US banks, Japanese insurers buying US bonds, European asset managers, they all use it to fund or hedge themselves in dollars.

### NDFs

Some currencies cannot be exchanged freely abroad (capital controls). For those, people use **NDFs** (non-deliverable forwards). Nobody delivers the currency. At maturity you compare the forward rate with the actual rate on the day and only settle the difference, in dollars. It is common for currencies like the Brazilian real, the Indian rupee or the Korean won.

## Where the formula breaks a bit, the cross-currency basis

Before 2008 the formula held almost perfectly. Since then there has been a persistent gap.

**Example.** With the rates from the example, the theoretical 3-month forward is:

```text
1.10 × (1 + 0.04 × 0.25) / (1 + 0.02 × 0.25) = 1.10 × 1.01 / 1.005 = 1.1055
```

Say the market actually quotes 1.1062. What dollar rate does that imply?

```text
1 + implied dollar rate × 0.25 = 1.1062 × 1.005 / 1.10 = 1.0107
implied dollar rate ≈ 4.27%
```

Borrowing dollars through the FX swap costs 4.27%, while the "normal" dollar rate is 4.00%. That gap of about 27 basis points is the **cross-currency basis**. By convention it is written as negative (here about −27 bps) when borrowing dollars through FX costs more than the formula says.

### Why it exists

- **Balance sheet cost.** To arbitrage the gap, a bank has to borrow and lend, so grow its balance sheet. Since 2008, capital rules (the leverage ratio in particular) make that expensive. The arbitrage still exists but it is no longer free, so it does not fully close the gap.
- **Demand for dollars.** Many non-US players need dollars (banks, Japanese insurers hedging their US bonds, companies with dollar debt). They are willing to pay a bit more.
- **Quarter-ends and year-ends.** Banks shrink their balance sheets before reporting dates. The basis often widens around those dates.

### In a crisis

The basis blows out when everyone wants dollars at the same time. In 2008, and again in March 2020. In March 2020 the Fed expanded its **swap lines**, FX swaps between the Fed and other central banks (ECB, BoJ, BoE, SNB...). It lends them dollars against their currency, and they lend the dollars on to their banks. The basis narrowed in the following weeks. The Fed acts as the dollar lender of last resort for the whole world.

## Classic pitfalls

- **"The forward is what the market expects."** No. It is the result of the spot + rates arbitrage. See UIP and CIP above.
- **Putting the rates on the wrong side.** The quote currency's rate (the 2nd) on top, the base currency's rate (the 1st) at the bottom. Quick check, the currency with the higher rate must be cheaper on the forward.
- **Mixing up points and outright.** "+216" are points, added to spot. The outright is 1.1216.
- **Forgetting the yen pip.** On USD/JPY, 1 pip = 0.01, not 0.0001.
- **Simple vs compound interest.** Under a year, (1 + r × T). Over a year, (1 + r)^T. And day count conventions differ by currency.
- **Thinking a hedge makes money.** It removes uncertainty, it does not create profit. If the dollar rises, the hedged company "loses" compared with the unhedged one.

## The S&T interview angle

**"EUR/USD is at 1.10, euro rate 2%, dollar rate 4%. 1-year forward?"** 1.10 × 1.04 / 1.02 = 1.1216. The dollar has the higher rate, so it is cheaper on the forward, so the EUR/USD forward is above spot.

**"Why does the higher-rate currency trade at a forward discount?"** Otherwise you could borrow in the low-rate currency, invest in the high-rate one, and hedge the way back with the forward for a risk-free profit. The forward cancels out the rate gap.

**"Is the forward a forecast?"** No, it is an arbitrage price. The forecast would be UIP, which does not hold in the data, and that is why the carry trade exists.

**"What is an FX swap and what is it for?"** A spot and an opposite forward in the same trade. Economically, a secured loan in another currency. It is used to fund in dollars or to hedge a foreign-currency portfolio.

**"What is the cross-currency basis?"** The gap between the dollar borrowing cost implied by FX swaps and the direct dollar rate. It exists because arbitrage costs balance sheet since 2008 and because demand for dollars outside the US is strong. It widens in crises and at quarter-ends.

**"How did the Fed calm the dollar market in March 2020?"** By expanding its swap lines with other central banks, which lent the dollars on to their banks.

## Links to previous episodes

- [The Policy Rate](26-the-policy-rate.md), policy rates set the rates that go into the formula.
- [QE and QT](27-qe-and-qt.md), low rates and then the fast 2022 hikes that moved rate gaps and forwards.
- [Interest Rate Swaps](10-interest-rate-swaps.md), the same logic of swapping uncertainty for a fixed number.
- [Repo](11-repo.md), an FX swap is a secured loan, like a repo with a currency as collateral.
- [Put-Call Parity](14-put-call-parity.md), the same arbitrage reasoning, two risk-free paths must cost the same.

<div class="ms-takeaway" markdown>

## Key takeaway

- EUR/USD = 1.10 means 1 euro costs 1.10 dollars. Base first, quote second.
- The forward is not a forecast. It is set so that exchanging now and saving, or saving and exchanging later, give the same result.
- `Forward = Spot × (1 + quote rate × T) / (1 + base rate × T)`.
- The currency with the higher interest rate is cheaper on the forward. The forward cancels out the rate gap.
- Companies use it to lock in their exchange rate, banks use FX swaps to borrow dollars.
- Since 2008, borrowing dollars through FX costs a bit more than the formula says (the cross-currency basis), and the gap blows out in a crisis.

</div>
