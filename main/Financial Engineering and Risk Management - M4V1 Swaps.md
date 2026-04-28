Prior: [[Financial Engineering and Risk Management - M3.2V4-5 Floating Rate Bonds and Term Structure of Interest Rates]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Swaps
> "​Swaps are contracts that ​transform one kind of cash flow into another"

---
### Swaps
**Definition.** Swaps are contracts that transform one kind of CF into another.

**Example.**
- Plain vanilla swap: fixed IR vs floating IR
- Commodity swaps: exchange floating price for a fixed price (eg gold swaps, oil swaps)
- Ccy swaps
Why do companies construct swaps?
- Change the nature of cash flows
- Leverage strengths in different markets

---
### Example of Leveraging Strengths
Two companies and where debt is pricing:
$$\begin{aligned}
\begin{array}{|c|c|c|}
\hline
Company & Fixed & Floating \\
\hline
A & 4.0\% & \text{LIBOR} + 0.3\% \\
B & 5.2\% & \text{LIBOR} + 1.0\% \\
\hline
\end{array}
\end{aligned}$$
Company A is "better" in both but relatively weaker in the floating rate market. This means company B is stronger in the floating rate market. The difference between the rate for A and B is only 70 bps in floating, while B's fixed cost is 120 higher.
Companies can take advantage of diff of relative strengths in two markets, create instrument to let them borrow at a better rate than individually borrowing.

Company A:
- Borrows in fixed market at 4.0%
- Swaps with B: pays LIBOR and receives 3.95%
Company B:
- B borrows in the floating market at L+1.0%
- Swap with A: pays 3.95% and receives LIBOR
Effective rates:
- A: -4% + 3.9% - LIBOR = -(L+0.05%) and L+5 borrowing is better than what A could've gotten in floating rate market.
- B: -LIBOR -1% +LIBOR -3.95% = -4.95%. And 495 is better than the 520 it could've gotten in the fixed rate market.
Both gain by leveraging rel str for deal better in either fixed or floating market.
How the 3.95% etc coming out depends on supply and demand.

Important implicit assumption being made: companies A and B continue to exist, neither of them are going to default, if one of these companies defaults then the superstructure breaks down (so either of them exposes the other to a big risk).

Instead make it with an intermediary (fin intermediary) to take the CPY risk, guarantees you get the swap CF expected from the other CPY.

---
### Role of financial intermediaries
Same two companies:
A fixed 4.0% or L+30
B fixed 5.2% or L+100
Financial intermediary that constructs the swap.

Company A
- Borrows in fixed market at 4.0%
- Swap with Intermediary: pays LIBOR and receives 3.93% (ie receive 0.02% less)
Company B
- B borrows in the floating market at L+100
- Swap with Intermediary: pay 3.97% and receive Libor (ie pay 0.02% more)
Fin intermediary makes 4 bps = compensation for taking on CPY risk and providing a service. 2 bps from each party. Constructing the service also, as typically A and B don't know they exist so the fin intermdiary can bring these two parties to the table.

---
### Pricing IR Swaps
$r_t$ = floating (unknown) interest rate at time t
Cash flows at time $t=1,...,T$
- Company A (long, pay fix receive float): receives float $Nr_{t-1}$ and pays $NX$ fixed rate.
	- Cash flow received at time ti s based on the interest rate prevailing at time t-1.
- Company B (short): receives $NX$ and pays $Nr_{t-1}$
Value of swap to company A
- $N(r_0,...,r_{T-1})$ = CF of floating rate bond - face value. Therefore, value of swap to company A
$$\begin{aligned}
V_A = N(1-d(0,T)) - NX \sum_{t=1}^T d(0,t)
\end{aligned}$$
This is value of floating payments received minus value of fixed payments paid to company B. We know the floating rate bond value is equal to the principal, but we actually don't get the principal back which was never exchanged, hence subtract discount factor from 0 to T. `1 - df` discount factor leaves us with the PV of the floating interest payments. On the other side, `NX` is the entire amount of the interest payment where X is the coupon rate. That's just annuity formula on right.

Set X so that $V_A=0$ AT TIME = 0, just like for forward contracts, i.e.:
$$\begin{aligned}
X = \frac{1-d(0,T)}{\sum_{t=1}^T d(0,t)}
\end{aligned}$$
Value of swap = 0 at beginning; indiff taking a long or short.
