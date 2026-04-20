Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 2 M2V5 The Multivariate Normal Distribution]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research


## Introduction to Martingales

> "​In this module, we're going to introduce Martingales. ​Martingales play a very important role in finance. ​They won't play a hugely important role in this course, ​but they will crop up now and again, ​and it's worthwhile understanding what they are ​and seeing one or two examples of Martingales."

---
### Martingales
Definition. A random process, {$X_n : 0 \le n \le \infty$} is a martingale with respect to the information filtration, $\mathcal{F}_n$ and probability distribution $P$ if the two conditions below are satisfied:
1. $E^P[|X_n|] < \infty \forall\ n \ge 0$. This is a technical integrability condition, the expected value of the absolute value of $X_n$ must be finite for all n.
2. $E^P[X_{n+m}|\mathcal{F_n}]=X_n \forall n,m \ge 0$. The expected value of $X_{n+m}$ given $F_n = X_n$ for all n,m >=0.
Information filtration is a complicated way of recognizing the information we have at time n. So $\mathcal{F}_n$ will denote all information in the model that we know at time n. Usually $\mathcal{F}_n$ = the information given to us by $X_1$ up to $X_n$ so by time n we've seen all those values. 
Back to this second condition here. it's saying that expected value at any time in the future is equal to its current value today.

Martingales are often used to model fair games, have a rich history in the modelling of gambling problems because #2 (history doesn't matter) models the idea of a fair game. Future payoff expected = wealth today. 


We define a submartingale by replacing condition #2.
Using all the information available to me today (filtration Fn), the best guess of future = value today. 
$$
E^P[X_{future}|F_n] = X_n
$$
Define submartingale by replacing = with >= for a future greater than today (today is LOWER).
Define supermartingale by replacing = as <= for a future less than today (today is HIGHER).
A martingale is both a submartingale and a supermartingale.

---
### Constructing a Martingale from a Random Walk
Let $S_n := \sum_{i=1}^n X_i$ be a random walk where the $X_i$s are IID with mean $\mu$. 
Let $M_n := S_n-n\mu$. Then $M_n$ is a martingale.

CFA: drift approach removed.
$$\begin{aligned}
S_n &= \sum n(\mu+\sigma dt) = n\mu+\int\sigma dt \\
M_n &= S_n - n\mu = \int\sigma dt \\
\end{aligned}$$
Course:
$$\begin{aligned}
E_n[M_{n+m}] &= E_n \left[ \sum_{i=1}^{n+m} X_i - (n+m)\mu \right] \\
&= E_n \left[ \sum_{i=1}^{n+m} X_i \right] - (n+m)\mu \\
\end{aligned}$$
The expected value of $M_{n+m}$, conditional on time and information, is equal to the sum on the right.
We know that $M_{n+m} = S_{n+m} - (n+m)\mu$ from the formula of $M_n := S_n - n\mu$.
We take out the first $n X_i$ because they're known to us at time n, so take it outside the expectation of $\sum_{i=1}^{n+m}$ and converted it out in front as the actual sum not expected value.
$$\begin{aligned}
&= \sum_{i=1}^{n} X_i + E_n \left[ \sum_{i=n+1}^{n+m} X_i \right] - (n+m)\mu \\
&= \sum_{i=1}^n X_i + m\mu - (n+m)\mu \\
&= \sum_{i=1}^n X_i - n\mu = M_n

\end{aligned}$$
The Xis are iid, so knowing the values of the first n Xis tells us nothing about future Xis. We know their mean, so the expected sum is just $m\mu$. Last step is algebra then recognizing the definition of $M_n$ where that initial sum was defined to be $S_n$. 

---
### A Martingale Betting Strategy
Let $X_1,X_2,...$ be IID random variables with $P(X_i=1)=P(X_i=-1)=\frac12$.
Imagine $X_i$ representing the result of coin-flipping game:
- Win $1 if coin comes up heads
- Lose $1 if coin comes up tails'
Consider now a doubling strategy where we keep doubling the bet until we eventually win. Once we win, we stop and our initial bet is $1.
First note that size of bet on $n^{th}$ play is $2^{n-1}$. Assuming we're still playing at time n. On the first day we bet $1 which is 2^0. On second day, 2^1 because we doubled our bet. On the third day, 2^2=4 etc. So the size of bet is 2^n-1 assuming we're still playing at time n, and we're only playying if we haven't yet won a game up until this point.

Let $W_n$ denote total winnings after n coin tosses assuming $W_0 = 0$. Then $W_n$ is a martingale. 

To see this, note that $W_n$ will only take on two values, either 1, or $-2^n + 1$.
In case 1. Suppose we win for the first time on the $n^{th}$ bet.
$$\begin{aligned}

W_n &= -(1+2+...+2^{n-2}) + 2^{n-1} \\
&= -(2^{n-1}-1) + 2^{n-1} \\
&= 1
\end{aligned}$$
The reason is because sum from 1 to $2^{n-2}$ on the n-1st bet is how much we've lost til then, then on the nth bet we win $2^{n-1}$.
That loss sum, summing a geometric series:
$$\frac{a(1-r)^n}{1-r}$$ is the general form. This translates to $(1)(1-2)^{n-1} / (1-2)$ = $2^{n-1} - 1$.

Case 2. If we have not yet won after n bets then:
$$\begin{aligned}
W_n &= -(1+2+...+2^{n-1}) \\
&= -2^n + 1
\end{aligned}$$
To show $W_n$ is a martingale only need to show $E[W_{n+1}|W_n] = W_n$ (\*) then follows by iterated expectations that $E[W_{n+m}|W_n]=W_n$.
To calc: $E[W_{n+2}|W_n] = E[E[W_{n+2}|W_{n+1}]|W_n]$. That inner term $E[W_{n+2}|W_{n+1}]=W_{n+1}$ by (\* with n = n+1).
Thus $E[W_{n+1}|W_n] = W_n$ by (\*).
For any factor of little n, just iterating expectations.

---
There are two cases to consider.
1. $W_n=1$. Then, $P(W_{n+1}=1|W_n=1)=1$. Thus $E[W_{n+1}|W_n=1]=1=W_n$ (6). 
   If $W_n$ actually equals 1, we stop playing the game because we've already won and at some point we already stopped so the $W_n$ is always 1 afterwards.
2. $W_n=-2^n + 1$: bet $2^n$ on the n+1th toss, so that $W_{n+1} \in \set{1, -2^{n+1}+1}$. The win is either 1 if we win the first toss or it will be the loss up to $-2^{n+1}+1$. The probability of either of these occuring is 0.5, thus:
$$\begin{aligned}
P(W_{n+1}=1|W_n=-2^n+1) &= 1/2 \\
P(W_{n+1}=-2^{n+1}+1|W_n=-2^n+1) &= 1/2
\end{aligned}$$
therefore the expected value is WA sum = $$\begin{aligned}
E[W_{n+1}|W_n=-2^n+1] &= (1/2)1 + (1/2)(-2^{n+1}+1) \\
&= -2^n + 1 = W_n \ (7)
\end{aligned}$$
In both possible cases, from (6) and (7) therefore $E[W_{n+1}|W_n]=W_n$. Therefore it is a Martingale.

> Then generalize this example where you allow random bets on each play of the game. As long as those bets only depend on what you've seen up to that point, you will actually still get a Martingale. That observation is very related to trading strategies and Martingale strategies in finance. 

---
### Polya's Urn
Consider an urn which contains red balls and green balls. 
Initially there is just one green ball and one red ball in the urn.
At each time step a ball is chosen randomly from theu rn.
1. If the ball is red, then it's returned to the urn with an additional red ball.
2. Vice versa if green
Therefore, there are n + 2 balls at time n. We began with 2 balls and after every play of the game we added an additional up to n plays.

Let $X_n$ denote the number of red balls in the urn after n draws. Then:
$$\begin{aligned}
P(X_{n+1} = k+1 | X_n = k) &= \frac{k}{n+2} \\
PSeries: [[Introduction to Financial Engineering and Risk Management]]

Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 1 M2V3 Review of Conditional Expectations and Variances]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Review of Multivariate Distributions
> "We're now going to review multivariate distributions. ​We'll talk about multivariate CDFs, multivariate PDFs,