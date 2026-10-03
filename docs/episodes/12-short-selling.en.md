<p class="ms-kicker">Episode 12</p>

# Short <span class="ms-outline">Selling.</span>

## Why this episode

The repo episode we just covered mentioned traders borrowing a "special" bond **to cover a short position**, without ever explaining what that means. This is where that thread closes.

## Definition

Shorting means **selling something you do not own**, betting that its price will **fall**, so you can buy it back later for less.

## The mechanism in 4 steps

1. You **borrow** the asset from someone who owns it.
2. You **sell** it immediately at the current price and collect the cash.
3. You wait for the price to **fall** (your bet).
4. You **buy it back** for less, return it to the lender, and keep the difference.

## A universal mechanism

It works on **any asset** that can be lent and resold, stocks, bonds, currencies, commodities, indices. Only the name of the "loan" changes depending on the asset:

- **Bonds.** The **repo** (previous episode), borrowing the security against cash as collateral.
- **Stocks.** **Securities lending**, usually through the broker, which borrows from large institutional holders (pension funds, ETFs).
- **Currencies.** Borrowing a currency to sell it against another, betting that it will depreciate.

## The link with the CDS (closing the loop on the series)

We used the phrase "short credit" for the CDS without explaining it. Buying a CDS (buying protection) is a way to bet on an asset deteriorating **without ever borrowing or physically selling it**, a **synthetic** short. The classic short selling covered here is a **physical** short (you actually borrow and sell the security). Same economic bet, two different mechanics to execute it.

## The risk of unlimited loss (the fundamental asymmetry)

**Classic long position** (buying at €100). Worst case, the price falls to €0, a maximum loss of €100. **Capped loss**.

**Short position** (shorting at €100). If the price **rises** instead of falling:

- at €150, a loss of €50
- at €500, a loss of €400
- at €2000, a loss of €1900

**No cap**. A price can rise indefinitely, unlike a fall, which is bounded at zero. The exact opposite asymmetry of a classic purchase.

## The borrowing cost (borrowing fee)

Borrowing the security is not free. Ongoing borrowing fees are paid to the lender, like rent on the security. The more short sellers want a security (the equivalent of a "special" security in repo), the more expensive and harder it becomes to borrow, sometimes several tens of % annualized, which eats into the potential profit if the bet takes time to play out.

## Margin and margin calls

Because the loss is unlimited, the broker requires a cash deposit as collateral (**margin**) before letting you short.

**Example.** Short 1 share at €100 (cash collected), plus a required margin of €50 (50% of the position). Total cushion €150.

If the price rises to €130, that is a potential loss of €30 if you buy back immediately. The broker continuously checks whether the remaining cushion stays above a minimum threshold (**maintenance margin**, often ~25-30% of the position value).

If the cushion falls below that threshold, the broker sends a **margin call**, asking you to deposit more cash immediately. With no response, the broker **buys back** the position itself at the current price, without your consent, to protect itself. The loss becomes final at that exact moment, often at the worst possible time.

## The short squeeze

A self-reinforcing mechanism. A heavily shorted asset starts to **rise** instead of falling, short sellers lose money, and some get margin calls and are forced to buy back to close. That massive buying pushes **the price even higher**, which triggers more margin calls, a self-reinforcing loop.

## Real case, GameStop, January 2021

A stock heavily shorted by large hedge funds (Melvin Capital in particular). A community of retail traders (Reddit WallStreetBets) spotted this high short interest and bought massively. The price went from **~$20 to nearly $500** in a few weeks, forcing the short funds to buy back at huge losses (Melvin Capital, losses of several billion, bailed out in an emergency).

<div class="ms-takeaway" markdown>

## Key takeaway

Shorting = betting on a fall in any asset by borrowing it, selling it, then buying it back for less. Theoretically unlimited loss (unlike a classic purchase), an ongoing borrowing cost, and the risk of being forced to buy back at the worst moment if the market turns against you (squeeze).

</div>
