Prior: [[Financial Engineering and Risk Management - M4V1 Swaps]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Futures
> "​In this module, we're going to introduce you to futures, ​why futures are needed, ​how one can hedge using futures and in later module we're ​going to introduce you to the mechanics of ​the margin account associated with the futures."

---
### Problems with forward contracts
> "​Forwards were contracts that ​gave the buyer the right and the obligation ​to purchase a certain amount of ​an underlying asset at ​a specified price at a specified time."

- Not organized through an exchange.
- Consequently, no price transparency!
- Double-coincidence-of-wants: need someone to take the opposite side!
- Default risk of the CPY.

Let's suppose there is expiration time T. If you construct a forward at t=0, there would be a forward price struct at $F_0$. If you created the forward later, there would be a different $F_k$, $F_u$, all the different contracts have diff prices depending on when they were struck. It's very difficult to set these contracts up to a exchange. And so there is no price transparency which is important for supply/demand to set fair prices or no arb prices.

If there is no price transparency, one would not be able to constrcut arb prices (supply/demand would not equilibrate without arb free prices).

Double coincidence of wants if not organized thru exch and no price transparency, you need somebody to take the other side, find a CPY on the oher side and contracts can't be written if other side isn't available.

Like swaps, if you do a fwd with other cpy and they're not willing to make payments or bankrupt, expose to unnecessary risk.

> "​So one needs a contract ​that works like a forward contract, ​that's able to fix prices sometime in the future, ​but is able to solve ​these other problems associated with forward contracts. ​That is, it's organized through an exchange, ​there is price transparency, ​you can get in and get out of this contract very easily, ​there is no counter party with which you are contracting, ​you are contracting through brokers ​who are organized in an exchange."

---
### Futures Contract
Solution = futures
- Solves the problem of a multitude of prices for the same maturity by marking to market
	- Disbursing profits/losses at the end of each day
- Now contracts can be organized thru an exchange
- Can be written on any underlying securities with a settlement prices
	- Commodities
	- Broad based indices ie SP500, R2000 etc
	- Volatility of mkt (VIX futures)
- http://www.cmegroup.com/market-data/delayed-quotes/commodities.html
Kinds of commods, indices and other measurable quantities on which futures contracts are written.

---
### Mechanics of a futures contract
- Individuals open a margin account with a broker
- Enter into N futures contracts with price $F_0$, the futures price available at time t=0
- Deposit initial margin into the account $\approx 5-10\%$ of contract value, depends whether hedger, speculator etc.
- All P/L settled using margin account. Profit if long futures and you hold and price goes up; the profit is credited to margin account.
- Margin call if balance is low (maintenace margin breached, must bring it back to the initial margin)

---
### Pros/cons of futures
Pros:
- High leverage: high profit. Veyr small initial amounts of money upfront
- Very liquid. Can get exposure easily.
- Can be written on a wide variety of underlying assets. Can speculate on wide variety

Cons:
- high leverage means high risk exposure
- Futures prices are approx linear function of underlying; only linear payoffs can be hedged. If CF is nonlinear fn of some underlying asset price of market indicator, then cannot hedge using futures prices
- May not be flexible enough; back to fwds. Organized thru exchanges, mature at specified date, for specified quantities, only written for certain dommods etc. If you need to hedge that doesn't quite fit the specifications you might need to go back to broker, construct 1off fwd or take on basis risk.

---
###  Pricing Futures
To price futures, you need something called martingale pricing formalism.
- In full generality, IR random or stochastic; when stochastic IR, cannot use simple arb arguments to construct futures price.
You need deterministic IR: fwd price = futures price. 
- We know how to construct fwd price using arbitrage and thuse how to price futures.
We DO know At maturity, futures price $F_T$ = price of underlying $S_T$. Can use this to make some hedging arguments.

---
---
### Hedging using Futures: Long hedge
Suppose that today is 9/1. A baker needs 500k bushels of wheat on Dec 1. So, the baker faces the risk of an uncertain price on Dec 1. Use futures to fix that Dec 1 price.

Hedging strategy: buy 100 futures contracts maturing Dec 1, each for 5000 bushels (total 500k bushels)

CF on 12/1 maturity:
- Long Futures position at maturity: $F_T - F_0 = S_T - F_0$ because FT = ST at expiry. This is the cash settlement value.
- If you had to buy bushels in the spot market: $S_T$, to cancel the future. You use the profits from the future to actually buy the asset the baker needs.
- Effective cash flow: $S_T - F_0 - S_T = -F_0$
Overall Price is fixed at $F_0$.
Remember, this is not a fwd. Everything is cash settled.

Costs? Cash flows associated with margin calls. Only looking at beginning/end, you got into futures without putting money up front and end up with diff of spot price and future time minus the spot as the profit from futures; combined with cost in spot, appears you are fixing the cost to what was originally agreed upon (futures profit pays for any increase to buy at current spot).
In reality, you needed to fund a margin acc and add money if margin call. If any time there is margin call and not able to provide money needed to keep position going, broker will cancel position and the benefits you were thinking about getting from futures position are no longer available.
So, costs are not transparent making sure enough cash there to service the margin.

---
### Perfect hedges are not always possible
In the previous example, we had a perfect hedge. We assume the futures contract matures right at the time we want the money. But perfect hedges are not always possible. The terminal date which we want a CF may not have a futures expiration date. The CFs we want to hedge may not correspond to integer number of futures contracts.

- The date T may not have a futures expiration date
- $P_T$ may not correspond to an integer number of futures contracts
- A futures contract on the UL may not be available
- The futures contract might not be liquid
- The payoff $P_T$ may be nonlinear in the underlying

Basis = spot price of the UL - futures price
- Perfect hedge: basis = 0 at maturity
- Basis risk: basis $\ne$ 0 at time T
- Basis risk arises because the futures contract is on a related but different asset, or expires at a diff time

