Prior: [[Financial Engineering and Risk Management - M3.1V2-3 Interest Rates and Fixed Income Instruments]] 

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

> "​In this module, we're going to ​introduce you to floating rate bonds, ​how to use the no arbitrage principle to price ​floating rate bonds and also to ​the term structure of interest rates. ​In this module, we're going ​to price a floating rate bond. ​This is a bond for which ​the interest rate or ​the coupon payment rate that you receive, ​is going to be dependent on ​the prevailing uncertain interest rate in the market. ​In order to price this instrument correctly, ​we have to use this idea called linear pricing."

### Linear Pricing
We will price a floating rate bond. Linear pricing theorem / result allows combining prices for different cash flows.
**Theorem.** (Linear Pricing) Suppose there is no arbitrage. Suppose also there are two cash flows whose prices are provided below:
- Price of cash flow $\mathbf{c}_A$ is $p_A$
- Price of cash flow $\mathbf{c}_B$ is $p_B$
Then the price of cash flow that pays $\mathbf{c}=\mathbf{c}_A + \mathbf{c}_B$ must be $p_A + p_B$.

Let p denote the price of the total cash flow c. Suppose $p<p_A+p_B$ i.e., c is cheap. Will create an arbitrage portfolio, i.e., a free-lunch portfolio
- Purchase c at price p cheap
- Sell cash flow $c_A$ and $c_B$ separately.
Price of the portfolio = $p-p_A-p_B < 0$, i.e., net income at time t = 0.
The cash flows cancel out at all times. Future cash flows = zero. Free lunch upfront credit; someone pays you to own this portfolio at t=0 and you have no future obligation. 

Idea = take a complicated CF, split htem up into simpler cash flows, price those simpler ones separately and then this theorem claims that the price of the total CF is going to be sum of those prices.

No arbitrage $\equiv$ no free lunch. Therefore, $p \ge p_A + p_B$.

We can reverse the argument if $p > p_A + p_B$
- Note that we need a liquid market for buying / selling all the cash flows. Needed for arb result to give a bound on prices. 
- Both of these results together shows that p must be exactly pA + pB.

---
### Simple Example of Linear Pricing
Cash flow $\mathbf{c} = (c_1,...,c_T)$ is a portfolio of T separate cash flows
- $\mathbf{c}^{(t)}$ pays $c_t$ at a time t and zero otherwise. 
- So now the portfolio is a series of zero coupon bonds.
Suppose the cash flows are annual and the annual interest rate is r.
Price of cash flow $\mathbf{c}^{(t)} = \frac{c_t}{(1+r)^t}$.
Price of cash flow $\mathbf{c} = \sum_{t=1}^T$ Price of cash flow $\mathbf{c}^{(t)} = \sum_{t=1}^T \frac{c_t}{(1+r)^t}$.

---
### Floating interest rates
Interest rates are random quantities ... they fluctuate with time.

Let $r_k$ denote the per period interest rate over period $[k, k+1)$ 
- The exact value of $r_k$ becomes known only at time $k$ (at the beginning of that period). Future payments unclear.
- 1-period loans issued in period $k$ to be repaid in period $k+1$ are charged $r_k$. Payment occurs at end of the period with rateset.
Cash flow of floating rate bond
- Coupon payment at time $k: r_{k-1}F$
- face value at time $n: F$
This above assumes annual coupons x annual rate, otherwise it'd be the semi-annual rate. 

Goal: Compute the arb-free price $P_f$ of the floating rate bond
Split up the cash flows of floating rate bond into simpler cash flows
- $p_k$ = Price of contract paying $r_{k-1}F$ at time $k$
- $P$ = Price of Principal F at time n = $\frac{F}{(1+r_0)^n}$ (which uses the interest rate right now, this is NPV of principal F)
Price of floating rate bond $P_f=P+\sum_{k=1}^n p_k$ aka price of the principal plus prices for the instrument paying $r_{k-1}$ at time $k$.
Rest of the slides tries to compute this $p_k$.

---
### Price of contract that pays $r_{k-1}F$ at time $k$
Goal: Construct a portfolio that has a deterministic cash flow. This is a DYNAMIC HEDGE FOR ONE FLOATING COUPON.
- The price of a deterministic cash flow at time t=0 is given by the NPV.
- This contract pays $r_{k-1}F$ at t = k. But that rate is not known at time t=0. Its exact value is only known at k-1 but is otherwise a random var. So construct portfolio where randomness is gone.

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
In the two intermediate steps the alpha is still unknown.
Third row, is just whatever the amount that was first borrowed that needed to be refi'd, that's the principal amount then grown by $(1+r_{k-1})$ which is only known at t=k-1.

Cash flow at time k: sum it up vertically.
$$\begin{aligned}
c_k &= r_{k-1}F - \alpha(1+r_0)^{k-1} (1+r_{k-1}) + \alpha(1+r_0)^k \\
&= \underset{random}{\underbrace{(F-\alpha(1+r_0)^{k-1})r_{k-1}}} + \underset{deterministic}{\underbrace{\alpha r_0(1+r_0)^{k-1}}}
\end{aligned}$$Because it's unknown let's set $\alpha = \frac{F}{(1+r_0)^{(k-1)}}$. Then the random term is 0. Here, alpha is the size of our hedge. You want the amount owed at time k-1 from the first borrowing to equal F. The refinancing amount at k-1 must be exactly F so that the amount owed at t=k is $F(1+r_{k-1})$. All this just without the notional component of it.

Net cash flow deterministic ... 
$c_0 = -p_k$ as the loans cancel.
$c_{k-1} = 0$ since it's a rollover.
$c_k = \alpha r_0(1+r_0)^{k-1} = Fr_0$. 

At t=k, $c_k = r_{k-1}F - \alpha (1+r_0)^{k-1}(1+r_{k-1}) + \alpha(1+r_0)^k$
Let Y = $\alpha(1+r_0)^{k-1}$.
Then the last term $\alpha(1+r_0)^k = \alpha(1+r_0)^{k-1} (1+r_0) = Y(1+r_0)$.
Now $c_k = r_{k-1}F - Y(1+r_{k-1}) + Y(1+r_0)$
When expanding: $c_k=r_{k-1}F - Y - Yr_{k-1} + Y + Yr_0$
The -Y+Y cancel. $c_k = r_{k-1}F - Yr_{k-1} + Yr_0$.
Factor the random rate in front. $c_k = r_{k-1}(F-Y) + Yr_0$.
Substitute back for Y: $c_k = r_{k-1}(F - \underbrace{\alpha (1+r_0)^{k-1}}) + \underbrace{\alpha (1+r_0)^{k-1}} r_0$
Now choose alpha where the random part is 0:
$F - \alpha (1+r_0)^{k-1} = 0$. We saw that $\alpha = \frac{F}{(1+r_0)^{(k-1)}}$.
Then $c_k = r_{k-1}(0) + Fr_0 = Fr_0$.


> Alpha is the amount you borrow/lend today so that the future refinancing principal equals F, which makes the unknown future interest payment from this contract exactly offset the unknown floating coupon.

---
### Price of floating rate bond (contd)
Price of the portfolio = $p_k - \alpha + \alpha = p_k = \frac{c_k}{(1+r)^k} = \frac{Fr_0}{(1+r)^k}$. This is just PV formula from above.
Recall that:
$$\begin{aligned}
P_f &= \frac{F}{(1+r_0)^n} + \sum_{k=1}^n p_k \text{, aka the principal plus sum of all the pks}\\
&= \frac{F}{(1+r_0)^n} + \sum_{k=1}^n \frac{Fr_0}{(1+r_0)^k} \\
&= \frac{F}{(1+r_0)^n} + \frac{Fr_0}{(1+r_0)} \sum_{k=1}^n \frac1{(1+r_0)^{k-1}} \\
&= \frac{F}{(1+r_0)^n} + \frac{Fr_0}{(1+r_0)} \cdot \frac{1 - \frac1{(1+r_0)^n}}{1-\frac1{1+r_0}} \\
&= F
\end{aligned}$$
The price $P_f$ of a floating rate bond is equal to its face value F.

The sum of pks = PV of every floating coupon payment. Because the slide here is using $r_0$ in numerator and denominator of $p_k$ calculation it assumes a flat curve where zeroes = $r_0$ for denom and all forward rates = $r_0$ for numerator.

> Pushes no-arb one step further. First use no-arb to calc price of deterministic CF. Now this above was actually the price of a stochastic cash flow, first by removing stochasticity and converting to deterministic CF. Then use no-arb to calc price of deterministic CF.

---
### Term Structure of Interest Rates
Interest rates depend on the term or duration of the loan. Why? IR is typically greater depending on the duration.
- Investors prefer their funds to be liquid rather than tied up
- Investors have to be offered a higher rate to lock in funds for a longer period.
- Other explanations: expectation of future rates (so what interest rate you charge now depends on future expectation), market segmentation (diff people in mkt interested in funds at diff terms/points in time; so IR for diff periods result in a term structure). 
- Reminder pure expectations, local expectations, liquidity preference, segmented markets, preferred habitat.
Spot rates: $s_t$ = interest rate for a loan maturing in $t$ years
$$\begin{aligned}
A \text{ in year } t \rightarrow PV = \frac{A}{(1+s_t)^t}
\end{aligned}$$In the denominator there, the s depends on t.

Discount rate $d(0, t) = \frac1{(1+s_t)^t}$. Can infer the spot rates from bond prices because default riks-free bonds are linear combination of coupon payments discounted at spots. Can compute spots using bonds prices at diff maturities.

Forward rate $f_{uv}$: interest rate quoted today for lending from year u to v. You can either lend it all at once for v years, or you can lend at u years, then from u to v immediately refi. That second loan contract is locked in at time 0, at the forward rate. No-arb forces these two options to be the same.
$$\begin{aligned}
(1+s_v)^v = (1+s_u)^u (1+f_{uv})^{(v-u)} \implies f_{uv} = \left( \frac{(1+s_v)^v}{(1+s_u)^u} \right)^{1/(v-u)} - 1
\end{aligned}$$
Relation between spot and forward rates:
$$\begin{aligned}
(1+s_t)^t = \prod_{k=0}^{t-1}(1+ f_{k,k+1})
\end{aligned}$$
Either go directly, or keep hopping 1 by 1 forward one year at a time.
![[Pasted image 20260425013951.png]]
