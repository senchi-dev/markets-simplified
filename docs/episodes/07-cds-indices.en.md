<p class="ms-kicker">Episode 07</p>

# CDS Indices <span class="ms-outline">(CDX & iTraxx).</span>

## The starting idea

A single-name CDS (covered in the previous note) protects **one** company. But if a manager holds a diversified bond portfolio and wants to hedge against a **broad** deterioration in credit, buying 20 or 100 separate CDS would be slow, illiquid and expensive in transaction costs. The solution is **a single contract that references a whole basket of companies at once.**

## Definition

A **CDS index** is a single, standardized contract that references a **fixed basket** of names (companies), each with the same weight (e.g. 1/125 for a 125-name index). It is literally a portfolio of mini-CDS packaged into one liquid instrument.

## The two main families

| Family | Region | Examples |
| --- | --- | --- |
| **CDX** | North America | CDX IG (125 investment grade names), CDX HY (100 high yield names) |
| **iTraxx** | Europe / Asia | iTraxx Main (125 European IG names), iTraxx Crossover (75 riskier names) |

## IG vs HY, in detail

Rating agencies (S&P, Moody's, Fitch) grade a borrower's credit strength, like a school report card.

- **Investment Grade (IG)**, from **AAA** (the safest) down to **BBB−**. Low default risk (solid sovereigns, large caps like Apple or Nestlé). Low spread.
- **High Yield (HY)**, also called **"junk"**, **BB+ and below**. Higher default risk, so investors demand a higher yield to compensate (hence the name "high yield"). Spread is much wider and more volatile.

**The BBB−/BB+ boundary is critical.** A company downgraded from BBB− to BB+ becomes a **"fallen angel"**. Many funds are only allowed, by law or by their mandate, to hold IG, so they are **forced to sell** in a hurry, which mechanically amplifies the drop in the price of that debt. This is one of the best-known contagion mechanisms in credit markets.

## How the contract works

Same as a regular CDS. The buyer pays the **index spread**, and the seller pays if one of the names in the basket defaults.

**The real difference with single-name.** When **one** name in the basket defaults, it is **removed** from the index, the seller pays only for that name's weight (e.g. 1/125 of the total notional), and the contract **continues** on the remaining names with a notional reduced by the same amount. A default does not kill the whole contract, it just takes a slice out of it.

## Why the cost does NOT depend on the number of names

This point is often misunderstood. The premium paid **does not depend** on the number of names in the basket (125 or 5). It depends on the **notional chosen** by the buyer and the **average credit quality** of the basket.

**Example.** A manager with a portfolio of 20 bonds totaling €20M buys €20M of notional on CDX IG at a 70 bps spread. Cost = 0.70% × €20M = **€140,000/year**. One number, one trade, covering the whole portfolio against a broad deterioration of the credit market. Adding names to the reference basket never increases this cost. It only changes how diversified the referenced risk is, not the price per euro protected.

It is also the **cheapest** option for a broad hedge, because indices are far more liquid (tight bid-ask spread) than 20 single-name CDS bought separately. Some of those 20 issuers might not even have a liquid CDS at all.

## Systematic vs idiosyncratic risk (the key point never to confuse)

The index **pays almost nothing** on the default of a single name, since each name is only ~0.8% of the basket (1/125). So it is **not** the tool to hedge one specific company.

- **Idiosyncratic risk** (one specific company defaults, independently of the rest of the market) calls for a **single-name CDS** on that exact name. This is the typical case when a bank lends a large, concentrated amount to one counterparty. It wants a 1:1 hedge on that name, not a diluted hedge spread over 124 other companies it does not care about.
- **Systematic risk** (the whole credit market deteriorates at once, e.g. recession, rate shock, broad risk-off) is what the **index** is built for.

If one of the bonds held defaults and it is not in the index (or even if it is), the index barely offsets that specific loss. The real protection does not come from individual default payouts, but from **mark-to-market**. When credit deteriorates broadly, the bonds held lose value AND the protection on the index gains value (its spread widens too), so the two moves offset each other overall.

The practical rule in portfolio management is that a serious manager often combines both tools. The index hedges the diversified core of the portfolio (market risk), and targeted single-names cover the 2-3 names that worry them specifically (idiosyncratic risk).

## Why it is such a central tool in markets

- **Liquidity.** Far more liquid than any single-name, it is the simplest way to trade credit as an asset class in its own right.
- **Macro barometer, the "VIX of credit".** The VIX measures the expected implied volatility of the S&P 500 from option prices, a fear gauge for equities. A CDS index spread plays exactly the same role for credit, a single number that captures in real time the perceived stress across the whole corporate debt market. A sharply widening spread signals broad risk-off.
- **Hedging in a single trade.** Hedge an entire credit book in one transaction instead of dozens.
- **Expressing a macro view.** "I think credit is going to deteriorate" translates directly into buying protection on the index, without having to pick individual names.

## Rolls (semi-annual renewal)

The index composition is not fixed forever. Every **6 months** (fixed dates, **March 20** and **September 20**), a **new series** is launched with an updated list of names.

- Downgraded or illiquid names are removed, and new names can come in.
- Each series has a number (Series 40, 41, 42...).
- The most recent series is called **"on-the-run"**. That is where all the liquidity and trading volume concentrate.
- Previous series become **"off-the-run"**. They are still contractually valid, but much less liquid, with a wider spread.
- **"Rolling" a position** means moving from an old series to the new on-the-run series to stay in the liquid version of the market.

Analogy, it works exactly like how there is always a "current" freshly issued 10-year Treasury (on-the-run, very liquid), while previous issues become off-the-run (less traded).

## Historical context

CDS indices played a central role in the **2008** crisis (massive bets on a broad credit deterioration) and in the **"London Whale"** affair (JPMorgan, more than $6 billion of losses in 2012 on badly managed CDX IG positions). It is an excellent concrete example of how these instruments, although designed for hedging, can also become highly leveraged directional bets.

### The mechanism in detail (how they really lost the money, without any default)

JPMorgan's CIO had **sold protection** on CDX.IG.9, which made them **long credit** (by market convention, "buying the index" = selling protection = long credit, exactly like holding the bond itself). Hedge funds noticed that the size of their position was distorting the price of this off-the-run index, and took the opposite side (bought protection, **short credit**), betting that the spread would widen.

The spread did widen (100 bps → 140 bps in the teaching example). Same mechanism as the price of a fixed-rate bond when yields rise. JPMorgan was stuck collecting the old low spread while the market demanded a higher one for the same risk. Their position, revalued at market price (mark-to-market), showed a loss of several billion **without a single one of the 125 names defaulting**. By trying to defend their price and adding even more size, they amplified the problem before finally cutting the position, with more than $6.2 billion of losses in total.

<div class="ms-takeaway" markdown>

## Key takeaway

A single-name CDS covers **one** specific company. A CDS index covers (or bets on) **a whole market** in a single contract, with a cost that depends on the notional chosen, not on the number of names referenced.

</div>
