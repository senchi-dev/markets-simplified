<p class="ms-kicker">Episode 27</p>

# QE and <span class="ms-outline">QT.</span>

## Why this episode

[Episode 26](26-the-policy-rate.md) explained how a central bank controls the overnight rate. But in 2008 and again in 2020, central banks took that rate to zero and the economy still needed help. The policy rate only controls day-to-day money, while mortgages, corporate loans and government borrowing are priced off **long-term rates** (5, 10, 30 years). QE is the tool used to push those long rates down. QT is the reverse.

This episode explains how it works in the balance sheets, why it lowers rates, what it did in practice, and above all the times it went wrong, and why.

## Definitions

**QE (quantitative easing).** The central bank buys large amounts of bonds, mostly government bonds (the Fed also bought MBS, bonds backed by mortgages, see [episode 8](08-cdo-tranches.md)). It pays for them with **reserves it creates**.

**QT (quantitative tightening).** The reverse. The central bank shrinks its balance sheet, either by not reinvesting the bonds that mature (passive QT) or by selling them on the market (active QT).

Important point, the central bank does not buy bonds directly from the government. It buys them on the **secondary market**, from investors (pension funds, insurers, banks). Financing governments directly is forbidden for the ECB by the European treaties.

## What happens in the balance sheets

The Fed buys $1bn of Treasuries from a pension fund.

| Who | Assets | Liabilities |
|---|---|---|
| Fed | +$1bn Treasuries | +$1bn reserves (owed to the fund's bank) |
| The fund's bank | +$1bn reserves at the Fed | +$1bn deposit (owed to the pension fund) |
| Pension fund | −$1bn Treasuries, +$1bn deposit | |

Three consequences.

1. The pension fund swapped a bond for cash.
2. The bank ends up with new reserves, created by the Fed.
3. The Fed's balance sheet grew by $1bn.

Do that for trillions and the banking system is flooded with reserves. That is exactly why the Fed and the ECB now run a **floor system**, with the market rate stuck to the deposit rate ([episode 26](26-the-policy-rate.md)).

QT goes the other way. When a bond held by the Fed matures, the Treasury repays the Fed. The money leaves the Treasury's account, so the Treasury has to borrow again from private investors, who pay with bank deposits. At the end of the chain, reserves disappear.

## Why it lowers long rates

### 1. The price effect

A huge buyer shows up, bond prices go up, and when a bond's price goes up its yield goes down.

**Example.** A 10-year bond has a [duration](03-duration.md) of about 9. If the buying pushes its price up 4%:

```text
yield drop ≈ 4% / 9 ≈ 0.45%
```

### 2. Less duration available (the scarcity effect)

The central bank takes long bonds out of investors' hands. Those who still need long assets (a life insurer has to cover 30-year liabilities) compete for what is left, so they accept a lower yield. In practice it is the **term premium** that falls, the extra yield demanded for locking money up for a long time.

### 3. Portfolio rebalancing

The pension fund now holds cash that pays almost nothing. It puts it into corporate bonds or stocks. [Credit spreads](05-credit-spread.md) tighten and stocks go up. That is intended, the central bank wants the whole structure of rates to fall, not just government yields.

### 4. The signal

Buying bonds for years tells the market that policy rates will stay low for a long time. Expected future short rates fall, and so do long rates.

### Orders of magnitude

Fed research on the first QE (Gagnon, Raskin, Remache and Sack, 2011) estimates it lowered the US 10-year yield by roughly 0.3% to 1%, mostly through the term premium. Later programmes are estimated to have had smaller effects, because markets already expected them.

## QE in numbers

### Fed

| Programme | Dates | What was bought |
|---|---|---|
| QE1 | Nov 2008 to 2010 | MBS and agency debt, then Treasuries from March 2009 (about $1.75tn in total) |
| QE2 | Nov 2010 to June 2011 | $600bn of Treasuries |
| QE3 | Sept 2012 to Oct 2014 | No fixed total, $40bn of MBS a month, then an extra $45bn of Treasuries a month |
| Covid QE | March 2020 to March 2022 | Unlimited at first, then $120bn a month |

The Fed's balance sheet went from about $900bn before 2008 to about $4.5tn in 2015, then close to $9tn at the 2022 peak.

### ECB

- January 2015, launch of the APP (asset purchase programme) with government bond buying, €60bn a month from March 2015.
- March 2020, PEPP (pandemic emergency purchase programme), with the envelope raised to €1.85tn.
- APP reinvestments stopped in July 2023, PEPP reinvestments at the end of 2024.

### Bank of Japan

The QE pioneer, from 2001. In 2013, QQE (quantitative and qualitative easing). In 2016 it added **yield curve control**, targeting the 10-year yield directly around 0% and buying as much as needed to hold it. It ended up owning more than half of Japanese government debt. It left negative rates and yield curve control in March 2024, with its first rate hike in 17 years.

## QT in practice

- **Fed, 2017-2019.** First QT, gradual runoff, stopped in 2019 (see the September 2019 repo episode below).
- **Fed, from June 2022.** Passive QT with monthly caps raised to $95bn a month ($60bn Treasuries, $35bn MBS). The Treasury cap was cut to $25bn in June 2024, then to $5bn in April 2025, and the Fed ended balance sheet runoff on 1 December 2025.
- **BoE.** The only major central bank running **active** QT, selling gilts on the market from November 2022.

Why slow down and then stop? Because in a floor system you need enough reserves for the rate to stay at the floor. Take out too many and money markets tighten. That is exactly what happened in 2019.

## When it went wrong

### 1. The taper tantrum, 2013

**What happened.** In May 2013, Fed chair Ben Bernanke told Congress the Fed could **slow** its purchases ("tapering") in the coming meetings. He did not talk about stopping, selling, or hiking. The US 10-year yield went from about 1.6% in early May to close to 3% by September. Emerging market currencies and bonds sold off hard (India, Indonesia, Brazil, Turkey and South Africa, nicknamed the "Fragile Five").

**Why.** QE had crushed the term premium and pushed investors into riskier assets, including emerging market debt. Just the signal that the main buyer would slow down was enough for the market to put the term premium back in at once and for money to leave emerging markets. The market reacts to expectations, not to the purchases themselves.

**The lesson.** Exiting QE has to be communicated very slowly and very early. Since then the Fed announces its balance sheet plans months in advance.

### 2. The repo panic, September 2019

**What happened.** On 17 September 2019, the US overnight repo rate spiked. SOFR printed 5.25% while the fed funds range was 2.00% to 2.25%, and some trades went through around 10% during the day. The effective fed funds rate broke above its range.

**Why.** The first QT had taken reserves from about $2.8tn (2014) down to about $1.4tn. That day, two cash drains landed at the same time. Companies paid their quarterly taxes, and purchases of newly issued Treasuries settled. Both moved cash from banks into the Treasury's account at the Fed. Banks that still had reserves did not want to go below their regulatory and internal buffers, so nobody lent. The system no longer had enough reserves to run as a floor system.

**The response.** The Fed injected cash through repo operations from the next day, then started buying T-bills again (about $60bn a month from October 2019) to rebuild reserves. In 2021 it created a permanent repo facility (the Standing Repo Facility, [episode 26](26-the-policy-rate.md)).

**The lesson.** There is a minimum level of reserves, and nobody knows exactly where it is until they hit it. That is why the 2022 QT was slowed and then stopped before getting there.

### 3. The gilt and LDI crisis, UK, September 2022

**What happened.** On 23 September 2022, the UK government presented a "mini-budget" with large unfunded tax cuts. Gilts (UK government bonds) sold off violently. The 30-year yield went from about 3.7% to above 5% in a few days. On 28 September the BoE announced it would **buy** long gilts, up to £5bn a day, at the very moment it was about to start **selling** them as part of its QT.

**Why.** Many UK defined-benefit pension funds used **LDI** strategies (liability-driven investment). To hedge their long-term liabilities, they took exposure to long gilts with leverage, through swaps and repo. When rates jump, those positions lose money and counterparties ask for more collateral (margin calls). To raise that cash, funds sell gilts, which pushes rates up further, which triggers new margin calls. A spiral. The BoE stepped in as buyer of last resort to break it.

**The response.** Temporary purchases from 28 September to 14 October 2022, about £19bn in total, and the start of QT sales pushed back to 1 November. Leverage rules for LDI funds were tightened afterwards.

**The lesson.** QT and fiscal policy can collide. And a central bank can end up doing QE and QT at the same time, for two different goals (financial stability on one side, monetary policy on the other).

### 4. Silicon Valley Bank, March 2023

**What happened.** SVB, the 16th largest US bank, failed on 10 March 2023 after two days of massive withdrawals.

**Why it is linked to QE.** During Covid QE, bank deposits exploded (the reserves created by the Fed end up as deposits, see the balance sheets above). SVB's deposits roughly tripled between 2019 and 2021. SVB put a large part of that money into long Treasuries and MBS at very low yields. When the Fed raised rates in 2022, the price of those bonds fell (that is [duration](03-duration.md)). Unrealised losses reached about $15bn at the end of 2022, roughly the size of its equity. When SVB had to sell some of those securities at a loss to pay out deposits, clients panicked and pulled their money.

**The lesson.** QE creates deposits that banks have to put somewhere. If they go into long bonds without a hedge, the exit from QE and rising rates turn that into a huge rate risk.

### 5. Central bank losses

**What happened.** The Fed started posting losses in September 2022. It books them as a "deferred asset" (to be repaid from future profits), which went above $200bn. The BoE lost money on its QE portfolio, and the UK Treasury covers those losses. The ECB reported a loss for 2023, its first since the early 2000s.

**Why.** During QE the central bank bought bonds paying 1% or 2% and funded them with reserves. When it raises rates to 4% or 5%, it pays that rate on reserves (IORB, [episode 26](26-the-policy-rate.md)). It earns 1-2% and pays 4-5%, so it loses money. That is negative carry, like a bank that borrows at a higher rate than it lends.

**Why it is not a bankruptcy.** A central bank cannot go bust in its own currency, since it creates it. The real cost is political and fiscal. It stops sending profits to the government for years, and its losses become a political debate.

## Classic pitfalls

- **"QE is printing banknotes."** No. QE creates reserves, which only banks hold. It is not money landing directly in households' pockets. The effect on inflation goes through rates and asset prices.
- **"QE finances the government."** Not directly. Purchases happen on the secondary market. But in practice QE makes government borrowing cheaper, hence the debate.
- **"QE caused the 2021-2022 inflation."** The 2009-2014 QE did not create inflation. The 2021-2022 inflation came from a mix of shocks (supply chains, energy, large fiscal stimulus, post-Covid demand). The exact role of Covid QE is still debated.
- **"QT means selling bonds."** Usually not. The Fed and the ECB run passive QT, they just let bonds mature.
- **The stock matters more than the flow.** What weighs on long rates is the total amount of bonds the central bank holds, not this month's pace of buying.

## The S&T interview angle

**"Explain QE."** The central bank buys bonds on the market with reserves it creates. That pushes prices up and long yields down, mostly by compressing the term premium, pushes investors into riskier assets, and signals that rates will stay low.

**"Difference between cutting the policy rate and doing QE?"** The policy rate works on the front end of the curve, QE on the long end. QE is used when the policy rate is already at zero.

**"What does QT do to the curve?"** It puts duration back into the market, so it pushes the term premium and long rates up. A steepening effect.

**"Why did the Fed stop QT?"** To avoid falling back into scarce reserves like September 2019, when repo spiked.

**"Walk me through the LDI crisis."** A sharp jump in long rates after the mini-budget, margin calls on pension funds' leveraged positions, forced gilt sales, a spiral, and the BoE stepping in as buyer of last resort.

**"Why do central banks lose money?"** They pay the policy rate on the reserves created during QE, while the bonds they bought pay much less.

## Links to previous episodes

- [The Policy Rate](26-the-policy-rate.md), the tool for the front end, and the floor system QE created.
- [The Yield Curve](02-the-yield-curve.md), QE flattens the curve, QT steepens it.
- [Duration](03-duration.md) and [DV01](04-dv01.md), to size the effect of purchases and SVB's losses.
- [Credit Spread](05-credit-spread.md), portfolio rebalancing tightens spreads.
- [Repo](11-repo.md), the market that broke in September 2019.

<div class="ms-takeaway" markdown>

## Key takeaway

- QE is the central bank buying bonds with reserves it creates. QT is the reverse.
- It is used to push long rates down when the policy rate is already at zero, mostly by crushing the term premium.
- It flooded banks with reserves, which is why we have today's floor system.
- What can go wrong. Just signalling the exit makes rates jump (2013). Too much QT dries up repo (2019). Leveraged positions built on low rates break when rates rise (LDI 2022, SVB 2023). And the central bank loses money when it hikes.

</div>
