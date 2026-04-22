Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 5 M2V17-18 Non-Linear Optimization]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Introduction to no-arbitrage
> "​In this module, we'll introduce the concept of no-arbitrage and work through ​a very simple example of the application of the no-arbitrage principle to pricing. ​"

---
### Contracts, prices, and no-arbitrage
Consider the following contract
- Pay price p at time $t=0$
- Receive $c_k$ at time $t=k, k=1,...,T$
Note that the cash flow $c_k$ could be negative.
![[Pasted image 20260421002658.png]]
So you pay P at the beginning and get cash flows in exchange for purchasing this contract.

The goal of this module is to introduce the ideas of no-arb to fix this price P. In some instances, you can fix the price exactly. In other instances, you can only be able to bound the price (i.e., tell the price cannot be larger than a certain quantity or smaller than a certain quantity).

The no-arb condition bounds the price p for this contract.
- Weak No-Arbitrage: $c_k \ge 0 \forall k \ge 1 \implies p \ge 0$
- Strong No-Arbitrage: $c_k \ge 0 \forall k \ge 1 \text{ and } c_l > 0 \text{ for some } l \implies p > 0$
Both ideas eliminate possibility of free lunch.

In weak arb: suppose there is a contract where all cash flows associated are non-negative for time periods from k=1 onwards. Therefore c1 c2 c3 ... ct all >0. If there is such a contract, then the price for the contract must be >= 0.

In strong no-arb, suppose again contract's cash flows non-negative for all times in future, and there exists some time cL in the future where at time L the cash flow is strictly POSITIVE. Then the price for such a contract must be strictly positive.

Both of these conditions are motivated by the fact that in a market if there are contracts for which you get something for nothing, then just by supply and demand at that price, contract will be priced to a point where you had to pay a fair price.

Rationale for the weak no-arb condition:
Suppose that $p < 0$, negative price for non-negative cash flows.
- Since $c_k \ge 0 \forall k \ge 1$, then the buyer receives a positive value, $-p > 0$ at time 0, and then the buyer does not lose money thereafter. This is the free lunch.
- Seller can increase price as long as $p \le 0$ and still have buyers available. Keep increasing buyer as it's a bad deal. Keep increasing the price until at least p hits equal to 0. 
- Buyers will be willing to pay a higher price in order to compete. Seller might be able to increase the price to be something > 0 but the weak-noarb condition doesn't allow to figure how the price works once it goes above 0. We only say using weak noarb that price will be increased until p becomes >= 0.
You can make the same argument from the buyer's perspective. Since it's a good deal for any price less than 0, the buyer is willing to pay a higher price (accept a lower upfront credit) to compete with each other until a p < 0 cannot be sustained in the market.
Weak no-arb is built on supply and demand. We are building it on the fact that there are many buyers, many sellers. And information about details of the contract are available publicly, uniformly, to buyers and sellers. 

---
### Assumptions underlying no-arbitrage
Rationale for the strong no-arb condition (p must be strictly positive for where there exists cash flow strictly positive)
- Suppose that $p \le 0$
- Recall that $c_l > 0$ for some $l \ge 1$. Therefore, a free lunch as long as $p \le 0$.
- We can only guarantee that $p>0$ but not the precise value. The seller of the contract will still have an incentive to increase the price. The buyers will still be around, a good deal at something positive (just cannot guarantee the precise value that the price is going to be). Buyers and sellers compete to set the price p.

Implicit assumptions underlying the no-arbitrage condition
- Markets are liquid: sufficient number of buyers and sellers. If the markets are illiquid, then no-arb condition isn't valid, and the bounds that we generate using the no-arb argument will no longer be valid.
- Price information is available to all buyers and sellers. Price information basically means what are the cash flows. Any buyers/sellers ignorant about CF means price formation process does not happen. Buyers and sellers decide how to set the price efficiently given price info.
- Competition is supply and demand will correct any deviation from no-arbitrage prices

---
### Pricing a Simple Bond
Consider a very simple bond that pays A dollars in one year. We want to set the price for this bond p today. Suppose one is able to borrow and lend unlimited amounts in the market at an interest rate of r per year.
Computing fair / arbitrage free price by constructing two different portfolios.
- Buy the contract at price p
- Borrow $A/(1+r)$ at interest rate r
Cash flows associated with this portfolio:
$$\begin{aligned}
\begin{array}{|c|c|c|}
\hline
\text{Price of portfolio} & & \text{Cashflow in 1 year} \\
\hline 
z = p - \frac{A}{1+r} & & A-A = 0 \\
\hline
\end{array}
\end{aligned}$$
At the beginning, you pay p for the contract and received A discounted at r from the loan.
In the future, the contract will pay A dollars, and borrowing A dollars needs to be repaid (since borrowed A/1+r has now grown at 1+r so repayment amount is A). 

Weak no-arb: $c_1 \ge 0$ implies price $z \ge 0$ i.e., $p \ge \frac{A}{1+r}$. Here there's only the one cash flow $c_1$ in the future and it's 0. Therefore the price must be >= 0. 
Then because z = P - PV(A), P >= PV(A) at 1+r.
Therefore the weak no-arb condition has given me a lower bound on the price. 


---
### Pricing a simple bond (contd) - 2nd portfolio
Next construct the following portfolio.
- Sell the contract at price p
- Lend A/1+r at interest rate r
Cash flows associated with this portfolio:

$$\begin{aligned}
\begin{array}{|c|c|c|}
\hline
\text{Price of portfolio} & & \text{Cashflow in 1 year} \\
\hline 
z = \frac{A}{1+r} - p & & -A+A = 0 \\
\hline
\end{array}
\end{aligned}$$
The cash flow again is 0 in the future because lent PV(A) at 1+r, and because you sold hte contract, you are responsible to pay the A dollars to the buyer of the contract in one year. These two cash flows cancel. So $c_1 = 0 \ge 0$. 
Price of the portfolio: you sold the contract so you receive that amount as a credit and lending/buying the bond of PV(A) outflow, the difference forms that z upfront cost.

Now again weak no-arb $c_1 \ge 0$ implies price $\implies z \ge 0$, i.e., $p \le \frac{A}{1+r}$.
When z = PV(A)-p >= 0, then we know that PV(A) >= p.

Now, these two results together imply that p = A / 1 + r. No surprise because constructed NPV calc using no-arb condition. Advantage of doing it this way because shows what assumptions are needed for NPV to exist.

The result relied on the ability to borrow AND lend at rate r and at an unlimited amount.
Consider if borrowing/lending rates are different and if borrowing/lending markets are elastic.
No-arb conditions would still be valid but you'd have to use different portfolios. Different rates means can't use NPV but can use no-arb. Elastic markets means interest rates being charged on borrowing/lending depends on the amount of borrowing or lending. No-arb would give us bounds on what such a contract can cost, if not the exact price.






---
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
