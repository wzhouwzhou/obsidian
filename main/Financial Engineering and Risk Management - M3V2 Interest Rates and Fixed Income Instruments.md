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

Interest rates are typically quoted on annual basis, even if the compounding period is less than 1 year.
- n compounding periods per year
- rate of interest r
- A invested for y years yields $A(1+\frac{r}{n})^{y \cdot n}$

**Definition.** Continuous compounding corresponds to the situation where the length of the compounding period goes to 0. Therefore, an amount A invested for y years is worth $lim_{n \rightarrow \infty} A(1+r/n)^{yn} = Ae^{ry}$ at maturity.

---
### Present Value
The price P of a contract that pays $\mathbf{c} = (c_0, c_1, c_2,...,c_N)$
- $c_k > 0 \equiv \text{cash inflow}$, and $c_k < 0 \equiv \text{cash outflow}$
PV assuming interest rate r per period
$$PV(\mathbf{c}; r) = c_0 + \frac{c_1}{1+r} + \frac{c_2}{(1+r)^2}+...+\frac{c_N}{(1+r)^N} = \sum_{k=0}^N \frac{c_k}{(1+r)^k}$$
No-arbitrage argument. Suppose one can borrow and lend at rate r.

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
Portfolio cash flows = 0for times $k \ge 1$.
Price of portfolio = $p - \sum_{k=0}^T c_k/(1+r)^k \ge 0 \implies p \ge \sum_{k=0}^T c_k/(1+r)^k$

To obtain the upper bound: reverse the portfolio.

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
Portfolio cash flows = 0 for times $k \ge 1$
Price of portfolio = $\sum_{k=0}^T c_k/(1+r)^k - p \ge 0 \implies p \le \sum_{k=0}^T c_k / (1+r)^k$

These two bounds together implies that p = PV(c) @ r.

Important: we could both lend and borrow at rate r.
If lending and borrowing rate differ: bounds change.

---
### Different lending and borrowing rates
Can lend at rate $r_L$ and borrow rate at rate $r_B$ where $r_L \le r_B$.
Portfolio: buy contract, and borrow 