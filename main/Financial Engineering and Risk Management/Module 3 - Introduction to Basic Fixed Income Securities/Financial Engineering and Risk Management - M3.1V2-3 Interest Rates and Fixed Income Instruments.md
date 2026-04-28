Prior: [[Financial Engineering and Risk Management - M3V1 Introduction to No-Arbitrage]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## IR and FI Instruments
> "​In this module, we're going to introduce you to ​interest rates, present values, ​and how present values are implied ​by the no-arbitrage principles, ​and also, introduce you to ​the idea of fixed-income instruments."

---
### Simple and Compound Interest
**Definition.** An amount A invested for n periods at a simple interest rate of r per period is worth $A(1+n \cdot r)$ at maturity.
**Definition.** An amount A invested for n periods at a compound interest rate of r per period is worth $A(1+r)^n$ at maturity.
At time 0 you invest A and now it's become (1+r)A, and then next period it becomes A(1+r)^2.

Interest rates are typically quoted on annual basis, even if the compounding period is less than 1 year. 
- n compounding periods per year
- rate of interest r
- A invested for y years yields $A(1+\frac{r}{n})^{y \cdot n}$
The total number of periods is y x n.

**Definition.** Continuous compounding corresponds to the situation where the length of the compounding period goes to 0. Therefore, an amount A invested for y years is worth $lim_{n \rightarrow \infty} A(1+r/n)^{yn} = Ae^{ry}$ at maturity for continuous compounding.
The solution here is that $\frac{\delta A}{\delta t} = rA$, and solve this equation. 

---
### Present Value
The price P of a contract that pays $\mathbf{c} = (c_0, c_1, c_2,...,c_N)$
- $c_k > 0 \equiv \text{cash inflow}$, and $c_k < 0 \equiv \text{cash outflow}$
PV assuming interest rate r per period
$$PV(\mathbf{c}; r) = c_0 + \frac{c_1}{1+r} + \frac{c_2}{(1+r)^2}+...+\frac{c_N}{(1+r)^N} = \sum_{k=0}^N \frac{c_k}{(1+r)^k}$$
Argue that this value is in fact the arb-free price p for this contract.
No-arbitrage argument. Suppose one can borrow and lend at rate r, and at unlimited amount.

At the beginning you pay an amount p and receive any initial cash flow c0. Replicate the funding using annual zeros borrowed.
$$\begin{aligned}
\begin{array}{|c|c|c|c|c|c|}
\hline
\text{Cash flows} & t=0 & t=1 & t=2 & t=k & t=T \\
\hline

\text{Buy contract} & -p+c_0 & c_1 & c_2 & c_k & c_T \\
\text{Borrow } c_1/(1+r) \text{ up to time 1 } &
c_1 / (1+r) & -c_1 \\
\text{Borrow } c_2/(1+r)^2 \text{ up to time 2 } &
c_2 / (1+r)^2 & & -c_2 \\
\text{Borrow } c_k/(1+r)^k \text{ up to time k } &
c_k / (1+r)^k & & & -c_k \\
\text{Borrow } c_T/(1+r)^T \text{ up to time T } &
c_T / (1+r)^T & & & & -c_T \\
\hline
\end{array}
\end{aligned}$$
Portfolio cash flows = 0 for times $k \ge 1$.
Price of portfolio = $p - \sum_{k=0}^T c_k/(1+r)^k \ge 0 \implies p \ge \sum_{k=0}^T c_k/(1+r)^k$
All future cash flows >= 0 so the price to construct must be >= 0. In this equation, price is the outflow amount.

To obtain the upper bound: reverse the portfolio. Sell the contract, invest the proceeds.

$$\begin{aligned}
\begin{array}{|c|c|c|c|c|c|}
\hline
\text{Cash flows} & t=0 & t=1 & t=2 & t=k & t=T \\
\hline

\text{Sell contract} & p-c_0 & -c_1 & -c_2 & -c_k & -c_T \\
\text{Lend } -c_1/(1+r) \text{ up to time 1 } &
c_1 / (1+r) & c_1 \\
\text{Lend } -c_2/(1+r)^2 \text{ up to time 2 } &
c_2 / (1+r)^2 & & c_2 \\
\text{Lend } -c_k/(1+r)^k \text{ up to time k } &
c_k / (1+r)^k & & & c_k \\
\text{Lend } -c_T/(1+r)^T \text{ up to time T } &
c_T / (1+r)^T & & & & c_T \\
\hline
\end{array}
\end{aligned}$$
Selling the contract involves negative future cash flows because need to pay it out (like shorting bond / borrowing and then paying interest).

Portfolio cash flows = 0 for times $k \ge 1$
Price of portfolio = $\sum_{k=0}^T c_k/(1+r)^k - p \ge 0 \implies p \le \sum_{k=0}^T c_k / (1+r)^k$

These two bounds together implies that p = PV(c) @ r.

Important: we could both lend and borrow at rate r.
If lending and borrowing rate differ: bounds change.

---
### Different lending and borrowing rates
Can lend at rate $r_L$ and borrow rate at rate $r_B$ where $r_L \le r_B$.
Portfolio: buy contract, and borrow $\frac{c_k}{(1+r_B)^k} (1+r_B)^k$ for k years, $k = 1,...,N$
- Cash flow in year k: $c_k - \frac{c_k}{(1+r_B)^k} (1+r_B)^k = 0$ for $k \ge 1$
- No-arb price = $p - c_0 - sum_{k=1}^N \frac{c_k}{(1+r_B)^k} \ge 0$
- Lower bound on price $p \ge PV(c)$ @ $r_B$
Price of contract must be no less than cost to borrow.

Portfolio: sell contract, and lend $\frac{c_k}{(1+r_L)^k}$ for k years, $k=1,...,N$
- Cash flow in year k: $-c_k + \frac{c_k}{(1+r_L)^k} (1+r_L)^k = 0$ for $k \ge 1$
- No-arb: price = $-p + c_0 + \sum_{k=1}^N \frac{c_k}{(1+r_L)^k} \ge 0$
- Upper bound on price $p \le PV(c)$ @ $r_L$
Contract must be as good of a deal if not better than lending at rL.

Bounds on the price $PV(c)$ @ $r_B \le p \le PV(c)$ @ $r_L$.

Set the price based on supply and demand. 
> "​It's set basically by supply and demand, ​depending upon whether the buyers or ​the sellers who has more of a market power, ​the price would either go to the lower ​bound or it will go to the upper bound. ​The supply and demand sets the price."

#### Flash cards
1. Under simple interest, interest per period re,aoms constant as time passes.
2. In the first construction, the amount c_1 / 1+r is borrowed at time 0 to offset the cash flow c1 at time 1.
3. The primary purpose of dividing r by n in discrete compounding is because r is expressed annually and need to find interest per period.
4. For a typical investor, the borrowing rate rB represents bank / margin loan interest rate charged.
5. In the second construction, the initial action on the contract at t=0 is selling.
6. When rL != rB, the contract P is going to be constrained PV(borrowing rB) <= P <= PV(lending rL).
7. Alternative math approach to yield the continuous compounding formula besides using limits = derivative where dA/dt = rA and solve difeq.
8. In continuous compounding equation A e^{ry}, the y represents the number of years of the investing/compounding.
9. In an incomplete market, supply/demand determines the actual price P within the no-arb interval.
10. Under weak no-arb, time 0 price of any portfolio with non-negative future CF must have non-negative time t=0 price p >= 0.

---
### Fixed Income Securities
Fixed income securities "guarantee" a fixed cash flow. Are these risk-free? No. They guarantee a dollar amount but there are risks.
- Default risk - at some point, the entity backing this fixed-income security might go bankrupt, the CF you were really promised is not going to come through. Only risk-free stated is US gov or equally stable gov to guarantee the CF will come. Corp FI securities always open to default risk.
- Inflation risk - even if they don't default, value of currency might go down over period so fixed cash flow is now of lower value. To hedge against this people have thought about TIPS - inflation protected securities.
- Market risk - even if no heavy inflation risk. Securities may become more or less valuable as time goes by. To sell securities in market, price end up getting will fluctuate over time and thus open yourself to market risk.

Perpetuity $c_k = A \forall k \ge 1$.
$$\begin{aligned}
p = \sum_{k=1}^\infty \frac{A}{(1+r)^k} = \frac{A}{r}
\end{aligned}$$
Provides fixed amount A for all times in future. Borrow/lend at rate r.

Annuity: $c_k = A \forall k = 1,...,n$
Pays amount A for periods k = 1 thru n.
Annuity = Perpetuity - Perpetuity starting in year n+1. 
Price p = $\frac{A}{r} - \frac{1}{(1+r)^n} \cdot \frac{A}{r} = \frac{A}{r} \left( 1-\frac1{(1+r)^n} \right)$.
First perpetuity is A/r and second perpetuity is A/r then discounted backwards n periods.
![[Pasted image 20260423002953.png]]
Second perpetuity cancels with later CFs of the first.

---
### Bonds
Features of bonds:
- Face value F: usually 100 or 1000
- Coupon rate $\alpha$ pays $c = \alpha F / 2$ every 6 months
- Maturity T: date of the payment of the face value and the last coupon
- Price P
- Quality rating: S&P Ratings AAA, AA, BBB, BB, CCC, CC
Quality is trying to get at the default risk; high quality bond low default risk.
Bonds differ in many dimensions ... hard to compare bonds. Characterize by at least 4 quantities (face value, coupon, maturity, price). Use YTM to help compare.

Yield to maturity $\lambda$, given
$$\begin{aligned}
P = \sum_{k=1}^{2T} \frac{c}{(1+\lambda / 2)^k} + \frac{F}{(1+ \lambda / 2)^{2T}}
\end{aligned}$$
is the annual interest rate at which price P = PV of coupon payments PLUS face value.

---
### Yield to Maturity
YTM $\lambda$
$$\begin{aligned}
P = \sum_{k=1}^{2T} \frac{c}{(1+\lambda/2)^k} + \frac{F}{(1+\lambda/2)^{2T}}
\end{aligned}$$
Why do we think in terms of yields:
- Summarizes face value, coupon, maturity, and quality
- Relates to quality: lower quality -> lower price -> higher YTM (understandable movements). Lower quality higher YTM because uncertain they'll come, discount those strongly.
- Relates to IR movements (IR change in market causes YTM to change similarly)
But YTM is a crude measure. Does not capture everything. Tries to summarize four different numbers in a single number.

---

