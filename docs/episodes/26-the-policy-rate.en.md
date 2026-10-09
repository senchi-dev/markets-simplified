<p class="ms-kicker">Episode 26</p>

# The Policy <span class="ms-outline">Rate.</span>

## Why this episode

Every rates episode in the series starts from the same point without ever explaining it. The [yield curve](02-the-yield-curve.md) starts at the overnight rate, the floating leg of a [swap](10-interest-rate-swaps.md) resets on an overnight rate, and [repo](11-repo.md) produces SOFR. All of these rates are anchored by one decision, the central bank's policy rate. This episode explains what a central bank is, how it sets that rate without ever telling a bank what rate to charge, how the rate spreads to the rest of the economy, and why it gets raised or cut.

## What a central bank is

It is the bank of the banks. Commercial banks (BNP, JPMorgan, Deutsche Bank...) hold an account at the central bank. The money in those accounts is called **reserves**. Banks use reserves to pay each other at the end of every day. When you send money from your bank to someone at another bank, at the end of the chain it is reserves that move from one account to another at the central bank.

Key point, **only the central bank can create reserves**. Banks can lend reserves to each other, but they cannot make new ones. That monopoly is what lets the central bank control the price of very short-term money.

The main central banks.

| Central bank | Area | Deciding committee | Meetings |
|---|---|---|---|
| Federal Reserve (Fed) | United States | FOMC (Federal Open Market Committee) | 8 a year |
| European Central Bank (ECB) | Euro area | Governing Council | 8 monetary policy meetings a year |
| Bank of England (BoE) | United Kingdom | Monetary Policy Committee (MPC) | 8 a year |
| Bank of Japan (BoJ) | Japan | Policy Board | 8 a year |

## What the policy rate is

It is the rate the central bank uses to steer the price of **overnight** money, meaning money lent from today to tomorrow. Each central bank has its own.

- **Fed.** A **target range** for the fed funds rate, 0.25% wide. For example 4.25% to 4.50%. The fed funds rate is the rate at which banks lend reserves to each other overnight, unsecured.
- **ECB.** Three rates, of which only one really matters today, the **deposit facility rate** (DFR).
- **BoE.** Bank Rate, a single rate.

When people say "the Fed hiked by 25 bps", it means the whole range moved up by 0.25% (1 bp, a basis point, is 0.01%).

## The mechanism, a floor and a ceiling

The central bank does not call anyone to impose a rate. It sets two rates, and the market settles between them.

- **The floor.** The rate the central bank pays banks on money left with it. No bank will lend to another bank below that, because leaving the money at the central bank earns that rate with zero risk.
- **The ceiling.** The rate at which the central bank lends to banks against securities pledged as collateral. No bank will borrow from another bank above that, because it can borrow from the central bank directly.

### Worked example, the ECB

Take ECB rates of 2.00% on deposits (DFR), 2.15% on main refinancing operations (MRO), and 2.40% on the marginal lending facility (MLF).

- Bank A has €1bn spare tonight. It will not lend it to Bank B below 2.00%, because the ECB pays 2.00% with no risk.
- Bank B needs €1bn tonight. It will not pay more than 2.40%, because it can borrow from the ECB at 2.40% (if it has collateral).
- So the overnight rate between banks ends up between 2.00% and 2.40%. That is the **corridor**.

If the ECB cuts by 25 bps, the whole corridor moves to 1.75% to 2.15%, and the overnight rate follows **the same day**.

Since September 2024 the gap between the DFR and the MRO is 0.15%, and the gap between the MRO and the MLF is still 0.25%.

### Corridor system or floor system

Where the market rate sits inside the corridor depends on how many reserves there are.

| | Scarce reserves (corridor system) | Abundant reserves (floor system) |
|---|---|---|
| Situation | Banks have just about the reserves they need | Banks have far more reserves than they need |
| Central bank's job | Adjust the amount of reserves every day to aim for the middle of the corridor | Set the floor rate, quantity is no longer the issue |
| Where the market rate sits | Near the middle, close to the main rate | Stuck to the floor |
| Example | ECB and Fed before 2008 | ECB and Fed after the QE years |

After the 2008 crisis and quantitative easing (QE, see below), the system is flooded with reserves. Nobody needs to borrow, everyone has cash to place. So the market rate drops to the floor. That is why **€STR** (the euro overnight benchmark, published by the ECB) trades a few basis points below the DFR. In March 2024 the ECB confirmed it steers policy through the DFR.

### On the Fed side

The Fed has also run an "ample reserves" system since 2008. Its tools, with example levels for a 4.25% to 4.50% range.

| Tool | Role | Example |
|---|---|---|
| ON RRP (overnight reverse repo facility) | Floor. The Fed borrows cash from money market funds against Treasuries, including from firms that cannot hold reserves | 4.25% (bottom of the range) |
| IORB (interest on reserve balances) | The rate paid to banks on their reserves, the main tool | 4.40% |
| EFFR (effective fed funds rate) | The market rate that results | about 4.33% |
| Standing Repo Facility and discount window | Ceiling. The Fed lends against collateral | 4.50% (top of the range) |

The ON RRP exists because money market funds cannot hold reserves at the Fed. Without that floor they would lend their cash below the range.

## How the rate spreads

```text
policy rate
  -> overnight rates (fed funds, €STR, SOFR, repo)     same day
  -> front end of the curve (T-bills, 2y bonds)        through expectations
  -> swaps, mortgages, corporate loans
  -> borrowing, spending, hiring
  -> inflation                                          12 to 24 months later
```

### Step 1, overnight

Overnight rates move on the day of the decision, mechanically, through the corridor arbitrage. SOFR (the US repo rate, [episode 11](11-repo.md)) and €STR follow.

### Step 2, the curve, through expectations

A 2-year rate does not follow today's decision. It follows what the market **expects** from every decision over the next 2 years. As a first approximation:

```text
2y rate ≈ average of expected overnight rates over 2 years + term premium
```

The term premium is the small extra that investors ask for locking their money up for longer.

**Example.** The overnight rate is 4.00%. The market expects an average of 4.00% in year one and 3.00% in year two (cuts are coming).

```text
2y rate ≈ (4.00% + 3.00%) / 2 = 3.50%   (+ a small term premium)
```

The 2-year is already below overnight even though the central bank has not done anything yet. That is exactly what creates an [inverted curve](02-the-yield-curve.md). An inverted curve is the market pricing future rate cuts.

### Step 3, the real economy

Banks fund themselves at rates linked to overnight and the front end of the curve. When their funding cost rises, they lend more expensively to households and companies. A floating-rate mortgage moves quickly ([episode 1](01-fixed-vs-floating-rate-debt.md)). A fixed-rate one follows long-term rates more.

## How the market prices future decisions

On a desk nobody says "I think the Fed will cut". People say "the market is pricing 3 cuts this year". That number comes from **OIS swaps** (overnight index swaps), swaps whose floating leg is the overnight rate (same logic as [episode 10](10-interest-rate-swaps.md)), and from fed funds futures.

**Example.** Overnight at 4.00%. The market expects a 25 bp cut every quarter starting in 3 months.

```text
months 0-3   : 4.00%
months 3-6   : 3.75%
months 6-9   : 3.50%
months 9-12  : 3.25%
average      : 3.625%
```

So the 1-year OIS trades around 3.625%. Reading that rate, a trader says "3 cuts priced over the year". If 1-year OIS moves to 3.75% after a strong jobs number, the market has taken out part of a cut.

Important consequence, **a decision that is already priced does not move the market**. If everyone expects a 25 bp cut and it happens, the curve barely moves. What moves the market is the **surprise**, or what the central bank says about what comes next (forward guidance).

## Why hike or cut

### The mandate

| Central bank | Mandate |
|---|---|
| Fed | Dual mandate, maximum employment and stable prices. 2% inflation target (formalised in 2012) |
| ECB | Price stability first. Symmetric 2% target over the medium term (2021 strategy review) |
| BoE | 2% target set by the government |

- **Inflation too high -> hike.** Borrowing costs more, saving pays more, so households and companies spend less, demand slows, and prices rise more slowly.
- **Economy too weak, inflation low -> cut.** Borrowing gets cheaper, which supports investment and spending.

### The lag

The effect on inflation often takes 12 to 24 months, and the delay is not stable (Milton Friedman talked about long and variable lags). So a central bank decides on **forecasts**, not on this month's number. If it waited for inflation to be back at 2% before it stopped hiking, it would already have hiked too much.

### Nominal and real rates

The real rate is the nominal rate minus inflation.

```text
policy rate 4%, inflation 3%  -> real rate = 1%    (fairly restrictive)
policy rate 2%, inflation 5%  -> real rate = −3%   (very loose)
```

What slows the economy is the real rate. In 2021-2022 policy rates were still close to zero while inflation was above 5%, so policy stayed very loose even after the first hikes.

### The Taylor rule

A reference economists use to judge whether the rate is "at the right level" (John Taylor, 1993).

```text
rate = r* + inflation + 0.5 × (inflation − 2%) + 0.5 × output gap
```

- **r\*** = the neutral real rate, the one that neither slows nor speeds up the economy. You cannot observe it, you estimate it (often around 0.5% to 1%).
- **output gap** = the gap in % between what the economy produces and what it could produce without creating inflation.

**Example.** r* = 1%, inflation = 4%, output gap = 0.

```text
rate = 1% + 4% + 0.5 × (4% − 2%) + 0 = 6%
```

If the policy rate is at 4%, the rule says it is too low. No central bank applies it mechanically, but markets and journalists use it as a benchmark.

## When the rate is at zero, QE and QT

A central bank cannot go much below zero. The ECB still had a negative DFR from June 2014 to July 2022 (down to −0.50%). When the policy rate cannot go lower, there is another tool.

- **QE (quantitative easing).** The central bank buys large amounts of government bonds with reserves it creates. That pushes bond prices up, so long-term rates down. It also creates the excess reserves that moved systems to floor mode.
- **QT (quantitative tightening).** The reverse. The central bank lets its bonds mature without replacing them, or sells them. Reserves shrink.

The policy rate works on the front end of the curve, QE and QT work more on the long end.

## Real cases

- **Volcker, 1979-1981.** US inflation goes above 14% in 1980. Paul Volcker, Fed chair, lets the fed funds rate rise to around 20%. Severe recession, but inflation falls below 4% by 1983. It is the historical reference for a central bank breaking inflation.
- **2008 and 2020.** Rates cut to zero and massive QE in both crises.
- **2022-2023.** The Fed goes from 0% to 0.25% (March 2022) to 5.25% to 5.50% (July 2023), including 4 consecutive 0.75% hikes in 2022. The fastest cycle since the 1980s. The ECB hikes in July 2022 for the first time in 11 years. The US 2-year goes from under 1% to over 4% during 2022, and the 2s10s curve stays inverted for about two years.
- **September 2024.** The Fed cuts by 0.50%. Four months later the US 10-year rate is about 1% higher. The market raised its growth and inflation expectations and the term premium went up. A policy rate cut does not guarantee lower long-term rates.

## Classic pitfalls

- **"The central bank sets loan rates."** No. It sets overnight. The rest is set by the market, which adds its expectations, the term premium and credit risk ([episode 5](05-credit-spread.md)).
- **"A hike always lifts the whole curve."** No. If the market thinks the hike will hurt growth, long rates can fall. The curve flattens or inverts.
- **"The decision moves the market."** Only the part that was not expected. On the day, you compare the decision and the statement with what was priced.
- **Basis points.** 25 bps = 0.25%, not 25%. And a "25 bp hike" on a Fed range moves both ends.
- **Nominal vs real.** A 5% rate with 6% inflation is not restrictive.
- **Unsecured vs secured overnight.** Fed funds is an unsecured loan between banks. SOFR is repo, so it is secured by Treasuries. They are close but not the same rate.

## The link with duration

When the market prices more hikes, rates go up and bond prices go down. How much is given by [duration](03-duration.md).

**Example.** A 2-year bond has a duration of about 1.9. A hawkish surprise (tougher than expected) lifts the 2-year by 0.50%.

```text
price change ≈ −1.9 × 0.50% = −0.95%
```

On €10m notional that is a loss of about €95,000. In [DV01](04-dv01.md) terms, about €1,900 per basis point.

## The S&T interview angle

**"How does the Fed actually set rates?"** It sets a target range for the fed funds rate and enforces it with administered rates. IORB pays banks on their reserves, ON RRP puts a floor for money market funds, and the Standing Repo Facility acts as a ceiling. Because reserves are abundant, the market rate sits near the bottom of the range.

**"The Fed cuts 25 bps, what does the 2-year do?"** It depends on what was priced. If the cut was expected, almost nothing. The 2-year reacts to the surprise and to the message about the next meetings.

**"Why does the curve invert?"** Because the market expects rate cuts, often because it expects a slowdown. Short rates are held by the current policy rate, longer rates include the future cuts.

**"How do you know how many cuts are priced?"** By reading OIS swaps and fed funds futures, and comparing forward rates with today's overnight rate.

**"Your trade if you think the Fed will cut more than the market prices?"** Receive fixed on a short-dated swap (a receiver), or buy 2-year bonds. If the cuts come, short rates fall and the position makes money.

**"Corridor vs floor system?"** Corridor when reserves are scarce and the central bank adjusts the quantity to aim for the middle. Floor when reserves are abundant and the market rate sticks to the deposit rate.

## Links to previous episodes

- [Fixed vs Floating](01-fixed-vs-floating-rate-debt.md), floating-rate debt follows the policy rate directly.
- [The Yield Curve](02-the-yield-curve.md), the policy rate anchors the left end of the curve.
- [Duration](03-duration.md) and [DV01](04-dv01.md), what a bond loses when expectations move.
- [Interest Rate Swaps](10-interest-rate-swaps.md), the fixed rate on a swap is the market's bet on future policy rates.
- [Repo](11-repo.md), repo rates and SOFR sit inside the corridor.

<div class="ms-takeaway" markdown>

## Key takeaway

- The central bank is the bank of the banks. Only it can create reserves, which lets it control the overnight rate.
- It does not impose any rate. It sets a floor (what it pays on deposits) and a ceiling (what it charges to lend), and arbitrage does the rest.
- With abundant reserves, the market rate sticks to the floor. That is the case for the Fed and the ECB today.
- Overnight moves the same day. The rest of the curve moves on expectations of the next decisions.
- A decision that is already priced barely moves anything. The surprise is what counts.
- Hike when inflation is too high, cut when the economy is too weak, with a 12 to 24 month lag, so decisions are made on forecasts.

</div>
