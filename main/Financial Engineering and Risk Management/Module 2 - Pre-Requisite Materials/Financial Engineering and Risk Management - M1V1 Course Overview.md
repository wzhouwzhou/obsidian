Series: [[Introduction to Financial Engineering and Risk Management]]

__Video Contents__:
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

> "âIn this module, we're going to give you a brief overviewÂ âof the entire course of Financial Engineering and Risk Management.Â âWe'll introduce the ideas of financial markets, financial products,Â âwhat do financial markets and financial products do for you.Â âWe'll introduce the ideas of the mainÂ âproblems in financial engineering, and how these relateÂ âto the different issues that come upÂ âin practical application financial engineering and risk management."


---
### Why Financial Markets?
--
Financial markets enable efficient allocation of resources
* across **time**
>   "You have income available today, but you want to allocate that income for sometime in the future.
* across **states of nature**
>   "You have income available today but tomorrow the states of nature are uncertain. You don't know whether you would have income available there. ​You don't know what your costs are going to be in the future. ​Depending upon various events happening, ​you might need more or less amount of funds. 

> And financial markets allow you the possibility ​of taking funds that are available today, ​move them across time, and move them ​across to states of nature that are uncertain.

Young worker with a high salary. What should she do?
* Financial markets: invest in stocks and bonds to finance retirement, home ownership, education etc.
> "​If there are financial markets available, she could invest in stocks ​and bonds to finance retirement, home ownership, education and so on."
* No financial markets: consumption? what else?
> "​If there were no financial markets ​available, she would have such as, a home car and so on. ​But she's not going to be able to move that later on in ​time to have them available when the states of nature are not good. ​"

Farmer producing oranges (idea of states of nature)
- Financial markets: Hedge using futures markets, weather related derivatives.
> "The farmer is producing oranges, and she ​is open to the risk of the price of orange when she ​produced when he product gets ready and it goes into the market. ​If there were financial markets available, as they are right now, she could ​hedge the price of the oranges in the future using the futures market. ​She could also buy vetter related derivatives, ​and use these derivatives to protect against ​the possibility of her produce going bad as a result of freeze, and so on.
- No financial markets: only the spot market available 
> " ​If there were no financial markets available, she would ​be open to the vagaries of the spot market. ​She can not hedge the price, nor can she hedge against the uncertainty ​of a produce not coming through, because of some weather-related emergency."

---
### More on Markets and Products
Role of markets
- Gather information
> "Markets are a place ​where buyers and sellers come together. ​They take action based on their information."
- Aggregate liquidity i.e., supply and demand
> "This information gets aggregated, and that aggregated information ​gets deflected in the price of the product."
- Promote efficiency and fairness
> "​And in some sense, this information gathering is necessary ​in order for a fair price to be created. ​It aggregates liquidity, so there are many ​buyers and sellers for a particular product. ​If there was no market, the buyers and ​the sellers would have to go looking for a counter party. Looking for a person who wants to take the opposite position. ​With a market, all the buyers and ​sellers come together, the liquidity gets aggregated, ​and as a result, the, both the buyers and sellers get a better price. ​By gathering information and by gathering liquidity, ​markets introduce or promote efficiency and fairness."

Products: satisfy "needs"
- Hedge risk
- Allow speculation
> "​Financial products are created to satisfy needs. ​New products hedge risk. They also allow for speculation"
- Raise funds
- Fund liabilities
> "Products allow to, one to raise funds for an operation, for example, using ​by, by issuing shares and an IPO."

---
### Modelling Financial Markets
Two kinds of market models
> "​Financial markets can be modeled in several different ways. ​There are two standard market ​models that are out there."
- Discrete time models
	- Single period models
	- Multi-period models
> "One of them is called a discrete time ​model, in which time goes forward in discrete steps. ​There are single period discrete time models ​and there are multiperiod discrete time models. "
- Continuous time models
> "The other class of model is called continuous time models. Continuous time models, time does not ad, ​advance discretely but in a continuous fashion."

Pros/Cons of discrete time models
- Pros: All important concepts with less sophisticated mathematics
> "​We can introduce all important concepts with very easy mathematics. ​Much less sophisticated mathematics than is ​necessary for the continuous time model."
- Cons: No closed form solutions ... have to resort to numerical calculations
> "The problem with discrete time models is ​there are no closed form solutions possible. ​Solutions are not as elegant as those available for continuous ​time models, and one has to resort to numerical calculations. ​This used to be a problem ​when computation was hard, and you couldn't ​do sophisticated comput, computation on simple machines. ​But as the price of computers have been coming down, people have tended ​to move more and more into discrete time models because they are simpler. ​You can introduce all kinds of interesting effects and compute ​them, rather than trying to look for a closed form solution. ​The focus of this course will be on discrete time multi-period models."

Focus of this course: Discrete time multi-period models
> "​We want to keep the mathematics simple, and yet be able to introduce all ​the concepts that are necessary, for you ​to understand financial engineering and risk management."

Caveat: Very, very few continuous time concepts covered, e.g., the Black-Scholes Formula. 
> "this is a very classic formula. ​And anyone graduating from a course on financial engineering and ​risk management, ought to know this formula."

---
### Financial Economics vs Financial Engineering
**Financial Economics**: use equilibrium arguments to:
- Price equities, bonds, and other assets
- Set interest rates
> "Financial economics is concerned with using equilibrium ​concepts to price something called primary assets. ​These are equities, bonds, interest rates, and so on."

**Financial Engineering**: Assume prices of equities and interest rates given
- Price derivatives on equities, bonds, interest rates, etc. using the no-arbitrage condition
> "Financially engineering on the other hand assumes the price of the primary assets ​such that equities and interest rates are given. ​And the focus of this field is on pricing ​derivatives and these primary assets using the no arbitrage condition."

Not even close to being a complete separation:
- For example, Capital Asset Pricing Model (CAPM) of interest to both

---
### Central problems of FE
**Security Pricing**
- Primary securities: stocks and bonds ... financial economics
- Derivative securities: forwards, swaps, futures, options, on the underlying securities
> "​The main focus of security pricing is ​to price derivative securities such as forwards, ​swaps, futures, and options on the underlying ​primary securities using the no arbitrage condition."

**Portfolio Selection**: choose a trading strategy to maximize the utility of consumption and final wealth
- Intimiately related to security pricing
- Single-period models: Markowitz portfolio selection
- Real options, e.g., options on gas pipelines, oil leases, mines
> "The focus of portfolio selection, is to choose a trading ​strategy to maximize the utility of consumption and final wealth. ​It turns out that portfolio selection is very intimately related to security ​pricing, and this will become clearer as we go through the course. ​Single-period models, such as Markowitz portfolio ​selection, are very widely used in industry. ​Multi-period models are much harder, but starting to get more traction. ​There's also the issue of pricing and using ​real options, such as options on gas pipelines, oil ​leases, and mines. ​These are also part of a portfolio selection strategy."

**Risk Management**: understand the risks inherent in a portfolio
- Tail risk: probability of large losses
- Value at Risk and Conditional Value at Risk
- Starting to become important for portfolio selection as well
> "​The third important topic is risk management. ​And the goal of this area is to understand the risks inherent in the portfolio. ​Here, we are not trying to choose a portfolio, the portfolio is already given. ​We just want to stress test the, the portfolio ​to understand how it performs in different market conditions. ​The important topics that come up in risk management are tail risk, ​which is a probability of large losses. ​Two risk measures that have become very important for tail risk, ​are the value at risk and the condition of value at risk. ​These two risk measures were introduced for risk management, but have ​started to become much more important for portfolio selection as well."

Led to interesting applied math / operations research problems.
> "For example, how does ​a company manage its operational risks using financial products? ​This is a marriage between supply chain management one side, ​which is one of the core ideas in operations research. ​And financial engineering on the other side, ​which talks about risk management and portfolio selection. ​You bring the two together, and now you have the possibility of ​hedging operational risks, which have got ​nothing to do with financial engineering per ​se, and combining them with financial products to get an ​idea of how one could hedge the risk across different areas."

Columbia Engineering http://engineering.columbia.edu
On-Campus Graduate Programs http://gradengineering.columbia.edu
Online MS Programs & Certificates http://cvn.columbia.edu
Department of Industrial Engineering & Operations Research http://ieor.columbia.edu
Center for Financial Engineering http://cfe.columbia.edu


                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                