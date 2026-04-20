Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 2 M2V6-8 Introduction to Martingales - recovered]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Introduction to Brownian Motion

> "We're now going to introduce Brownian Motion. ​Brownian Motion is a very commonly used stercastic process in finance. ​It is the process that underlies the Black-Scholes methodology and we're going ​to discuss it now."

---
### Brownian Motion
**Definition.** A random process / stochastic process $\set{X_t: t \ge 0}$ is a Brownian motion with params $(\mu, \sigma)$ if:
1. For the following fixed times $0 < t_1 < t_2 < ... < t_{n-1} < t_n$: $$(X_{t_2} - X_{t_1}), (X_{t_3} - X_{t_2}), ..., (X_{t_n} - X_{t_{n-1}})$$are mutually independent. This is often called the Independent Increments property.
2. For s>0, $X_{t+s}-X_t \sim N(\mu s, \sigma^2 s)$. So mu and sigma were the params of the distribution, then for an increment of length s at xt+s vs xt, then that increment must have mean mu s and variance sigma^2 s.
3. $X_t$ is a continuous function of t
![[Pasted image 20260404183636.png]]
It means that you can draw a single path and it never jumps, this means that the brownian motion is continuous.

We say that $X_t$ is a $B(\mu, \sigma)$ Brownian motion with drift $\mu$ and volatility $\sigma$. 

Remark. Among the first people to introduce Brownian Motion mathematically: Bachelier (1900) and Einstein (1905) first to explore Brownian motion from mathematical viewpoint, whereas Wiener (1920s) was the first to show that it actually exists as a well-defined mathematical entity.
> "it's interesting that Bachelier, ​very little is known about him, he was a French mathematician and in fact, it turns ​out he, he has had a great role to play in, in, in finance. ​He was trying to model stock prices on the Paris stock exchange way back in 1900 and ​he tried to introduce the idea of a Brownian motion to do that. ​So it's very interesting to see, that a concept as important as Brownian motion, ​which is used throughout the physical sciences and engineering was actually ​introduced by Bachelier in a financial context. ​"

>  So Brownian motion, it's a hugely ​important stochastic process, and it plays a very big role in, in finance as well.

---
### Standard Brownian Motion
When $\mu=0, \sigma=1$ we have a standard Brownian motion SBM.
We will use $W_t$ to denote a SBM and we always assume that $W_0=0$ (the SBM begins at 0).
Note that if $X_t \sim B(\mu, \sigma)$ and $X_0=x$ then we can write $$X_t = x+ \mu t + \sigma W_t$$ where $W_t$ is SBM. Therefore $X_t \sim N(x + \mu t, \sigma^2 t)$. This is because if we have $X_t$ defined this way, then $E[X_t] = x + \mu t + \sigma E[W_t]$. Since Wt is SBM it has given mean of 0 x t, therefore mean is the $x + \mu t$.
The variance $Var(x_T)$, the constants don't matter they don't factor into variance. Only $\sigma^2 Var(W_t)$ matters, and we're given SBM has sigma of 1 per period, therefore overall variance is $\sigma^2 t$.

The jaggedness in the path exists even if zooming in, but the paths are continuous even though they're very jagged.

---
### Information Filtrations
For any random process we wil use $\mathcal{F}_t$ to denote the information available at time t:
- The set $\set{\mathcal{F}_t}_{t \ge 0}$ is then the information filtration. This was discussed in Martingales. [[Financial Engineering and Risk Management - Intro to Probability Part 2 M2V6-8 Introduction to Martingales - recovered]]
- So $E[\cdot | \mathcal{F}_t]$ denotes an expectation conditional on time t information available. 
We will usually write $E[\cdot|\mathcal{F}_t]$ as $E_t[\cdot]$.

Important Fact: The independent increments property of Brownian motion implies that any function of $W_{t+s} - W_t$ is independent of $\mathcal{F}_t$ and that $$(W_{t+s}-W_t) \sim N(0,s)$$
Knowing all of the information available to us at time t tells us nothing about the increment from Wt to Wt+s. The incremental is normal even conditional on the information filtration.

---
### A Brownian Motion Calculation
Q: What is $E_0[W_{t+s}W_s]$, the expected value of the product.
We can use a version of the conditional expectation identity to obtain that $$\begin{aligned}
E_0[W_{t+s}W_s] &= E_0[(W_{t+s}-W_s+W_s)W_s] \\
&= E_0[(W_{t+s}-W_s)W_s] + E_0 [W_s^2] \ (9)
\end{aligned}$$
You can multiply $W_s$ out to two expectations.
Now we claim that $E_0[W_s^2]=s$. We know this because $s=Var(W_s)$ and that is $= E[W_s^2] - E[W_s]^2$. The second term is 0 because SBM mean is 0.

To calculate first term on right hand side of (9), a version of the conditional expectation identity implies that $$\begin{aligned}
E_0 [(W_{t+s} - W_s)W_s] &= E_0[E_s[(W_{t+s}-W_s)W_s)]] \\
\end{aligned}$$
This above comes from conditioning on time s information. Then move $W_s$ from inner expectation outside, because we're already conditioned on time s and therefore it's a constant. $$\begin{aligned}
E_0[E_s[(W_{t+s}-W_s)W_s)]] \\
&= E_0[W_sE_s[(W_{t+s}-W_s)]] \\
&= E_0[W_s0] = 0

\end{aligned}$$
Then because of important fact $$(W_{t+s}-W_t) \sim N(0,s)$$Then we know that the expected value of that difference is 0. Therefore $W_s0$ = 0.

So we've shown that $E_0[W_{t+s}W_s]=s$.

---
## Geometric Brownian Motion
> " In this module we're going to discuss Geometric Brownian Motion. ​Geometric Brownian motion is a very important Stochastic process, a random ​process that's used everywhere in finance."

Definition: We say that a random process, X_t, is a geometric Brownian motion (GBM) if for all $t \ge 0$, $$X_t = X_0 e^{(\mu - \sigma^2/)t + \sigma W_t}$$ where $W_t$ is a standard Brownian motion.
We call $\mu$ the drift, $\sigma$ the volatility, and write $X_t \sim GBM(\mu, \sigma)$.
Now replace the equation above t with t+s. Note that $$\begin{aligned}
X_{t+s}&=X_0e^{(\mu - \sigma^2/2)(t+s)+\sigma W_{t+s}} \\
&= X_0 e^{(\mu-\sigma^2/2)t+\sigma W_t + (\mu-\sigma^2/s)s+\sigma(W_{t+s}-W_t)} \\
\end{aligned}$$
This step expands the first multiplication and then adds then subtracts $W_t$.
But that first quantity $X_0 e^{(\mu-\sigma^2/2)t+\sigma W_t}$ is actually just $X_t$.
Therefore $$=X_t e^{(\mu-\sigma^2/2)s + \sigma(W_{t+s}-W_t)} \ (10)$$This is a representation that is very useful for simulating security prices when they follow Geometric Brownian Motion.
The difference $W_{t+s}-W_t$ is just the normal random variable with mean 0 variance s $N(0,s)$, independent of $X_t$ based on the Independent Increments property of Brownian motion.

So to generate brownian motion at time 0 and t, but all the intermediate timestamps. To simulate intermediate time series points, just simulate N(0, deltatime). This generates a sample path of stock. 

---
Q: Suppose $X_t \sim GBM(\mu, \sigma)$, what is $E_t[X_{t+s}]$?
From equation 10 on the previous slide, we have:
$$\begin{aligned}
E_t[X_{t+s}] &= E_t[X_t e^{(\mu-\sigma^2/2)s + \sigma(W_{t+s}-W_t)}] \\
&= X_t e^{(\mu - \sigma^2/2)s} E_t[e^{\sigma(W_{t+s}-W_t)}]
\end{aligned}$$
The first $X_te^{(\mu - \sigma^2/2)s}$ is known to us so take it out of expectation. The right side the expectation exponent is Normal N(0, variance s). So trying to compute the expected value of that is making use of the moment generating function of a normal random.

If $Z \sim N(a, b^2)$, then it implies that $E[e^{uZ}]=e^{au+\frac12 b^2 u^2}$. This is mgf of normal random. So then use the standard result where a = 0 and $b^2$ = s, and u is $\sigma$. Expected value = $e^{\frac12 \sigma^2s}$. #formula 

Therefore $$=X_t e^{(\mu - \sigma^2/2)s} e^{(\sigma^2/2)s}$$
The sigma^2/2 cancels out and we get $=e^{\mu s}X_t$.
So the expected growth rate of $X_t$ is $\mu$.

---
The following properties of GBM follow imnmediately from the definition of BM:
1. Fix $t_1, t_2,...,t_n$, then the ratios of $X_t$s one period to the next are mutually independent, i.e., $X_{t_2} \div X_{t_1}$, $X_{t_3} \div X_{t_2}$ etc. up to n and n-1.
2. Paths of $X_t$ are continuous as a function of t (they do not jump).
3. For s>0, $log(X_{t+s} \div X_t) \sim N((\mu - \sigma^2/2)s, \sigma^2 s)$.
Recall we saw that $X_{t+s} = X_t e^{(\mu-\sigma^2/2)s + \sigma(W_{t+s}-W_t)}$ from equation 10.
The only random variable is that increment of $W_{t+s} - W_t$. Independent increments property of Brownian Motion implies property 1.
For the third property, $log(X_{t+s} \div X_t) = (\mu- \sigma^2/2)s + \sigma(W_{t+s}-W_t)$. Since that second term in the sum is normal (0, variance s), then the entire log is normal with the first term $(\mu-sigma^2/2)s$ and variance is the scalar multiple const $\sigma$ squared multiplied by s, i.e., $\sigma^2 s$.

---
Suppose $X_t \sim GBM(\mu, \sigma)$. Then:
1. If $X_t > 0$, then $X_{t+s}$ is always positive for any s > 0. So the limited liability of stock price is not violated. 
Again from equation 10: $$X_{t+s} = X_t e^{(\mu-\sigma^2/2)s + \sigma(W_{t+s}-W_t)}$$
if $X_t>0$ then the whole exponential will be positive and therefore $X_{t+s}>0$.
2. The distribution of the ratio $X_{t+s} / X_t$ only depends on s and not $X_t$. This was clear from previous slide when the log of the ratio of X at t+s and t is normally distributed, which only depends on what s is given fixed $\mu, \sigma$ params. This ratio can be thought of as the returns of a stock $R_{t,t+s}$ which don't depend on the current value of the stock.
These properties suggest that GBM might be a reasonable model for stock prices, and is the underlying model for the famous Black-Scholes option formula.

