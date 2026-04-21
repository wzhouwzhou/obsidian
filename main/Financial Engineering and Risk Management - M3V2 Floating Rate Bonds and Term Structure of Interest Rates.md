

### Linear Pricing
**Theorem.** (Linear Pricing) Suppose there is no arbitrage. Suppose also:
- Price of cash flow $\mathbf{c}_A$ is $p_A$
- Price of cash flow $\mathbf{c}_B$ is $p_B$
Then the price of cash flow that pays $\mathbf{c}=\mathbf{c}_A + \mathbf{c}_B$ must be $p_A + p_B$.

Let p denote the price of the total cash flow c. Suppose $p<p_A+p_B$ i.e., c is cheap. Will create an arbitrage portfolio, i.e., a free-lunch portfolio
- Purchase c at price p
- Sell cash flow $c_A$ and $c_B$ separately.
Price of the portfolio = $p-p_A-p_B < 0$, i.e., net income at time t = 0.
The cash flows cancel out at all times. Future cash flows = zero. Free lunch.
No arbitrage $\equiv$ no free lunch. Therefore, $p \ge p_A + p_B$.
We can reverse the argument if $p > p_A + p_B$
- Note that we need a liquid market for buying / selling all the cash flows.

---
### Simple Example of Linear Pricing
Cash flow $\mathbf{c} = (c_1,...,c_T)$ is a portfolio of T separate cash flows
- $\mathbf{c}^(t)$ pays $c_t$ at a time t and zero otherwise.
Suppose the cash flows are annual and the annual interest rate is r.
Price of cash flow $\mathbf{c}^{(t)} = \frac{c_t}{(1+r)^t}$.
Price of cash flow $\mathbf{c} = \sum_{t=1}^T$ Price of cash flow $\mathbf{c}^{(t)} = \sum_{t=1}^T \frac{c_t}{(1+r)^t}$.

---
### Floating interest rates
Interest rates are random quantities ... they fluctuate with time.

Let $r_k$ denote the per period interest rate over period $[k, k+1)$ 
- The exact value of $r_k$ becomes known only at time $k$.
- 1-period loans issued in period $k$ to be repaid in period $k+1$ are charged $r_k$
Cash flow of floating rate bond
- Coupon payment at time $k: r_{k-1}F$
- face value at time $n: F$
Goal: Compute the arb-free price $P_f$ of the floating rate bond
Split up the cash flows of floating rate bond into simpler cash flows
- $p_k$ = Price of contract paying $r_{k-1}F$ at time $k$
- $P$ = Price of Principal F at time n = \frac{F}{(1+r)^n}
Price of floating rate bond $P_f=P+\sum_{k=1}^n p_k$

---
### Price of contract that pays $r_{k-1}F$ at time $k$
Goal: Construct a portfolio that has a deterministic cash flow
- The price of a deterministic cash flow at time t=0 is given by the NPV.

$$\begin{aligned}
\begin{array}{|c|c|c|c|}
\hline
&t=0&t=k-1&t=k\\
\hline
\text{Buy contract }&-p_k&&r_{k-1}F \\
\text{Borrow }\alpha\text{ over }[0,k-1] & \alpha & -\alpha(1+r_0)^{k-1} \\
\text{Borrow }\alpha(1+r_0)^{k-1} \text{ over } [k-1, k] & & \alpha(1+r_0)^{k-1} & -\alpha (1+r_0)^{k-1} (1+r_{k-1}) \\
\text{Lend } \alpha \text{ from } [0, k] & -\alpha & & \alpha(1+r_0)^k \\
\hline

\end{array}
\end{aligned}$$

Cash flow at time k
$$\begin{aligned}
c_k &= r_{k-1}F - \alpha(1+r_0)^{k-1} (1+r_{k-1}) + \alpha(1+r_0)^k \\
&= \underset{random}{\underbrace{(F-\alpha(1+r_0)^{k-1})r_{k-1}}} + \underset{deterministic}{\underbrace{\alpha r_0(1+r_0)^{k-1}}}
\end{aligned}$$Set $\alpha = \frac{F}{(1+r_0)^{(k-1)}}$. Then the random term is 0.
Net cash flow deterministic ... $c_k = \alpha r_0(1+r_0)^{k-1} = Fr_0$.

---
### Price of floating rate bond (contd)
Price of the portfolio = $p_k - \alpha + \alpha = p_k = \frac{c_k}{(1+r)^k} = \frac{Fr_0}{(1+r)^k}$
Recall that:
$$\begin{aligned}
P_f &= \frac{F}{(1+r_0)^n} + \sum_{k=1}^n p_k \\
&= \frac{F}{(1+r_0)^n} + \sum_{k=1}^n \frac{Fr_0}{(1+r_0)^k} \\
&= \frac{F}{(1+r_0)^n} + \frac{Fr_0}{(1+r_0)} \sum_{k=1}^n \frac1{(1+r_0)^{k-1}} \\
&= \frac{F}{(1+r_0)^n} + \frac{Fr_0}{(1+r_0)} \cdot \frac{1 - \frac1{(1+r_0)^n}}{1-\frac1{1+r_0}} \\
&= F
\end{aligned}$$
The price $P_f$ of a floating rate bond is equal to its face value F.

---
### Term Structure of Interest Rates
Interest rates depend on the term or duration of the loan. Why?
- Investors prefer their funds to be liquid rather than tied up
- Investors have to be offered a higher rate to lock in funds for a longer period.
- Other explanations: expectation of future rates, market segmentation
Spot rates: $s_t$ = interest rate for a loan maturing in $t$ years
$$\begin{aligned}
A \text{ in year } t \rightarrow PV = \frac{A}{(1+s_t)^t}
\end{aligned}$$
Discount rate $d(0, t) = \frac1{(1+s_t)^t}. Can infer the spot rates from bond prices.
Forward rate $f_{uv}$: interest rate quoted today for lending from year u to v.

