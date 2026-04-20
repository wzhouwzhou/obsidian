__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Forwards


--
### Forward Contracts
**Definition.** A forward contract gives the buyer the right, and also the obligation, to purchase
- A specified amount of an asset
- At a specified time T
- At a specified price F (the forward price) set at time t = 0

Example.
- Forward contract for delivery of a stock with maturity 6 months
- Forward contract for sale of gold with maturity 1 year
- Forward contract to buy 10m $ worth of Euros with maturity 3 months
- Forward contract for delivery of 9-month T-Bill with maturity 3 months

---
### Setting the forward price F
**Goal:** Set the forward price F for a forward contract at time t=0 for 1 unit of an asset with
- asset price $S_t$ at time t
- and maturity T
$f_t$ = value/price at time t of a long position in the forward contract
Value at time T: $f_T=(S_T-F)$
- long position in forward: must purchase the asset at price F
- spot price of asset: $S_T$
Forward price F is set so that time t=0 value/price $f_0$ is 0
Use no-arbitrage principle to set F

---
### Short selling an asset
Short selling is the selling of shares in a stock that the seller doesn't own.
- The seller borrows the shares from the broker
- The shares comes from the brokerage's own inventory
- The shares are sold and the proceeds are credited to the seller's account
However ... sooner or later
- The seller must "close" the short by buying back the shares (called covering)

Profit/loss associated with a short sale
- Results in a profit when the price drops
- Results in a loss when the price increases

Short positions can be very risky
- Price can only drop to zero ... potential profit is bounded
- Price can increase to arbitrarily large values ... potential loss is unbounded

---
### No-arbitrage argument to set F
Assume asset has no intermediate cash flows, e.g. dividends, or storage costs

Portfolio: buy contract, short sell the underlying and lend $S_0$ up to time T
$$\begin{aligned}

\begin{array}{|c|c|c|}
\hline
\text{Cash flow} & \text{t = 0} & \text{t = T} \\
\hline
\text{Buy contract} & f_0 = 0 & f_T = S_T - F \\
\text{Short sell asset and buy back at time T } & +S_0 & -S_T \\
\text{Lend }S_0 \text{ up to }T & -S_0 & S0/d(0, T) \\
\hline
\text{Net cash flow} & 0 & S_0 / d(0,T)-F \\
\hline
\end{array}

\end{aligned}$$
The portfolio has a deterministic cash flow at time T and the cost = 0.
Therefore, 
$$\begin{aligned}
0 = ( \frac{S_0}{d(0,T)}-F)d(0, T) 
\rightarrow
F=\frac{S_0}{d(0,T)}
\end{aligned}$$
Why is F strictly greater than the spot price $S_0$? Cost of carry.

### Examples of forward contracts
**Example.** Forward contract on a non-dividend paying stock that matures in 6 months. The current stock price is $50 and the 6-month interest rate is 4% per annum.

**Solution.** Assuming semi-annual compounding, the discount factor
$$\begin{aligned}
d(0, .5) = \frac1{1+ \frac{0.04}2} = 0.9804
\end{aligned}$$
Therefore,
$$\begin{aligned}
F = 50/0.9804 = 51.0
\end{aligned}$$
---
### Forward value $f_t$ for $t > 0$
Recall the value of a long forward position
- at time 0: $f_0 = 0$
- at time T: $f_T = S_T - F$
- $F_0$: Forward price at time 0 for delivery at time T
- $F_t$: Forward price at time t for delivery at time T
Pricing via the no-arbitrage arguments
$$\begin{aligned}
\begin{array}{|c|c|c|}
\hline
\text{Cash flow} & {t = t} & {t = T}\\
\hline

\text{Short } F_t \text{ contract} & 0 & F_t - S_T \\
\hline

\text{Long } F_0 \text{ contract} & -f_t & S_T-F_0 \\
\hline 

\text{Net cash flow } & -f_t & F_t - F_0 \\

\hline
\end{array}
\end{aligned}$$
The portfolio has a deterministic cash flow. Therefore:
$$\begin{aligned}
f_t = (F_t - F_0)d(t, T)
\end{aligned}$$
