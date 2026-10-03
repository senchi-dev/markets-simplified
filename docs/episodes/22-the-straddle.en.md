<p class="ms-kicker">Episode 22</p>

# The <span class="ms-outline">Straddle.</span>

## Why this episode

The strategy that brings all the Greeks together at once (delta, gamma, vega, theta). It makes the whole options arc concrete.

## Definition

Buy **a call AND a put**, same strike, same expiry. You pay both premiums. It is a bet on a **big move**, whatever the direction. If the stock moves hard enough one way or the other, one of the two sides pays off big.

## Worked example

Apple at €100. Call strike 100 (premium €4) + put strike 100 (premium €4). Total cost = **€8**.

- Apple at 120: call worth 20, put 0 → 20 − 8 = **+€12**
- Apple at 80: put worth 20, call 0 → 20 − 8 = **+€12**
- Apple at 100 (right at the strike): both at 0 → **−€8** (max loss)
- Apple at 105: call worth 5, put 0 → 5 − 8 = **−€3** (it moved, but not enough)

## Breakevens

You only make money if the move exceeds the total cost (€8). Upper breakeven = 100 + 8 = **€108**. Lower breakeven = 100 − 8 = **€92**. In between, you lose. It is not "I bet it moves", it is "I bet it moves by more than €8".

## The Greeks, all at once

- **Delta neutral (at the start).** Call +0.5, put −0.5, they cancel out → no bet on direction. **Nuance**: only true at entry. As soon as the stock moves, gamma tilts delta in the direction of the move (e.g. Apple at 110 → call delta +0.8, put −0.2, total +0.6, net long).
- **Long gamma.** You love big moves, in both directions, and gains accelerate when the stock takes off.
- **Long vega.** If implied volatility rises, both options gain value, even before the stock moves.
- **Short theta (negative theta).** Every quiet day is expensive, you pay the decay on TWO options at once.

## The trap, vol crush

A straddle is most tempting **before an event** (earnings, an election), when a big move is expected. But that is exactly when implied vol is **inflated**, so both premiums are expensive. The actual move has to beat what is **already priced in**. After the event, vol crush drives the value down (long vega hurts). You can see the stock move as expected and still lose if the move is smaller than what was anticipated.

## The seller (short straddle)

The exact opposite: collects both premiums and wants the stock to stay still. Short gamma, short vega, positive theta. Very dangerous, it loses if the stock moves hard in either direction.

<div class="ms-takeaway" markdown>

## Key takeaway

Long straddle = call + put at the same strike. Delta neutral (at the start), long gamma, long vega, short theta. A pure bet on the size of the move, not the direction. It wins on a big move OR a rise in vol, and loses if the stock stalls. Watch out for vol crush after events.

</div>
