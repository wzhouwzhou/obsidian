### 1. Terminology and Review
Discrete random variables X and continuous random variables Y
X is given by probability mass function $f_X$, and Y is given by its probability distribution function $f_Y$; respectively the pmf and pdf.
A probability mass function is a function from the sample space: $$
\begin{align}
&\underset{sample space}{\underbrace{\Omega}} \rightarrow \mathbb{R}_{\ge 0}
&&{\Omega^{=\mathbb{R}}} \rightarrow \mathbb{R}_{\ge 0}

\\ \\

&st. \sum_{x\in\Omega}{f_X(x)}=1
&& \int_{y\in\Omega}{f_Y(y)}dy=1
\end{align}
$$
**Example:** x takes 1 with probability 1/3, -1 with probability 1/3 and 0 with probability 1/3.
Thus
$$X =\left\{
\begin{array}{l} 1 \quad (\text{prob } \tfrac13) \\ -1 \quad (\text{prob } \tfrac13) \\ 0 \quad (\text{prob } \tfrac13)
\end{array} \right. $$
The probability mass function pmf $f_X(1) = f_X(-1) = f_X(0) = \frac13$

**Example:** $f_Y(y)=1$ for all $y\in[0,1]$, 0 otherwise = PDF of uniform random variable $[0,1]$.

Probability of an event can be computed as $$\begin{align}
P(A)&=\sum_{x \in A}{f_X(x)} \\
&= \int_A{f_Y(y)dy}
\end{align}
$$
Expectation = mean:
$$\begin{aligned}
\mathbb{E}[X]&=\sum_{x \in \Omega}{x \cdot f_X(x)} \\
\mathbb{E}[Y]&=\int_{\Omega}{y\cdot f_Y(y)dy}
\end{aligned}$$

Two random variables $X_1$, $X_2$ are independent if $P(X_1 \in A\ and\ X_2 \in B) = P(X_1 \in A) \cdot P(X_2 \in B)\ \forall \ events\ A\ and\ B$

---
### Several concepts of independence.
Two popular:
Mutually independent events: $X_1$ is independent to $X_2$ and $X_3$ and $X_4$, etc. Every variable is independent from every other variable.
Pairwise independent events: It may be the case that pairing $X_1$ and $X_2$, or $X_2$ and $X_3$ or $X_1$ and $X_3$, are independent. But altogether it's not independent. Which means that the mutually independent events formula: $$\prod_{i=1}^n{P(X_i \in A_i)} = P(X_1 \in A_1) \cdot P(X_2 \in A_2) \ ... \ P(X_n \in A_n) \ \forall\ sets\ A_i$$
 is NOT true so formula does not hold. Now we focus on mutually independent. If we say several variables are independent, it means that whatever collection you take they're all independent.

Notion of indep rand vars.
The pdf of collections of rand vars if mutually indep is the product of the probability densities of the individual variables.
With the exponential family, if you have rand vars from the same exponential family, products of this density function factor out into a very simple form. It doesn't get more complicated as you look at the joint density of many variables and actually simplifies to the same exponential family. Designed so that it factors out when multiplied.

---
#### 1.1. Normal and lognormal distribution
One of the most famous distributions is the Normal distribution.
Continuous random variable is said to have normal distribution $N(\mu, \sigma)$ if:
the probability density function PDF = $$f(x)=\frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}} \ \forall \ \mathbb{R}(-\infty<x<\infty)$$
$\mu$: mean, $\sigma^2$: variance. Example $\mathcal{N}(0,1)$ symmetrical around the origin.
![[Pasted image 20260324232550.png]]

Our purpose = we want to model financial product i.e., the price of a stock using random variable.

Example. Can try using normal distribution first (doesn't make sense) but you can say that $P_n - P_{n-1} \sim \mathcal{N}(0,1)$.
This doesn't make sense because it doesn't take into account the order of magnitude of the price to model the change in price from now vs before is normal distributed the same regardless - absolute value of the increment identically distributed. This assumption doesn't make sense, not a good model. I'm giving just discrete increments while these are continuous random variables etc. Norm dist not good enough, we want % change.
In this case if the daily change $~\mathcal{N}(0,1)$, then $P_n \sim \mathcal{N}(0, \sqrt{n})$. If the average increment is 0 and there is no tendency, then the daily increment is 0. No matter how far you go, your rand var will be normally distributed. And it could have very large negative and positive values (doesn't make sense for price).
![[Pasted image 20260325105505.png]]

Usually what's normally distributed is the % of how much it changes daily.
(13.13)
Instead, we want a relative difference to be normally distributed, i.e., the % change is normally distributed. $\frac{P_n-P_{n-1}}{P_n} \sim \mathcal{N}(0,1)$

Now that we have this (where % change is normally distributed), what is the distribution of price, the random variable itself?

Define a lognormal random variable Y st. natural log(Y) is normally distributed.
To derive the probability distribution of this from the normal dist, you can use the change of variable formula.

**Change of variable formula:**
Suppose that X, Y are rand vars st. $$
P(X\leq x) = P(Y\leq h(x)) \ \forall \ X$$
Then $$
f_X(x)=f_Y(h(x))\cdot h'(x)$$

$$\begin{aligned}
y=h(x) \\
\frac{ d f(h(x))} {dx} = ? \\
\frac{df(y)}{dy} \ \cdot \frac{dh(x)}{dx} \\

\frac{df(y)}{dy} \ \cdot h'(x)

\end{aligned}$$

---
### 1.4 Log-Normal Distribution
So using this, h(x) in this case is log(x). We can find the formula for the variable. If Y is normally distributed, then X will be the distribution. We can now compute the pdf of the lognormal distribution using the probability distribution of normal distribution.

X: lognormal distribution
Y: normal distribution with mean $\mu$ var $\sigma$
$$\begin{align}
P(X\leq x) &= P(Y \leq ln(x)) \\
f_X(x)&=f_Y(ln(x)) \cdot \frac{dln(x)}{dx} \\
&= f_Y(ln(x)) \cdot \frac1x \\
= \frac1{x \sigma \sqrt{2 \pi}} e^{-{(ln(x)-\mu)}^2 / {2 \sigma ^2}}
\end{align}$$

given Normdist = $$f(x)=\frac{1}{\sigma \sqrt(2\pi)} e^{-{(x-\mu)^2} / {2\sigma^2}} $$
 Therefore the lognormal distribution is a distribution which has probability mass (density) function defined as: $$\frac1{x \sigma \sqrt{2 \pi}} e^{-{(ln(x)-\mu)}^2 / {2 \sigma ^2}} \ \forall \ (x>0)$$Lognormal dist are referred to based on the normal distribution $\mu$ and $\sigma$ but they're not the mean and variance because of the skew and so those statistics are different.

$$\begin{align}
\mathbb{E}[X] &= e^{\mu + \sigma^2 / 2} \\
\mathbb{Var}(X) &= e^{2\mu + \sigma^2} \cdot (e^{2\sigma} - 1)
\end{align}$$

Some other distributions we will see:
Poisson distribution -
Exponential distribution -

All of these (including LogNormal LN) can be grouped into a group of dists called Exponential Family of Distributions.
A distribution is called to be in an exponential family (belongs to an exponential family) if:
$\exists vector\ \theta$ that parameterizes the distribution s.t. the probability density function for this parameter theta can be written as:
$$ f^{(\theta)} = h(x) \cdot c(\theta) \cdot exp({\sum_{i=1}^{k}{\omega_i(\theta)t_i(x)}})$$
$h(x), t_i(x)$ depend only on x, and $c(\theta), \omega_i(\theta)$ depends only on $\theta$.

Exponential functions exhibit some good statistical behavior when you group them all.

**Looking at how LN falls into the exponential family.**
$$\begin{aligned}
&\frac1{x\sigma \sqrt{2\pi}} e^{-\frac{(ln(x) - \mu)^2}{2 \sigma^2}} \\
&=\frac1x \cdot \frac1{\sigma \sqrt{2\pi}}exp({-\frac{ln(x)^2}{2\sigma^2} + \frac{\mu ln(x)}{\sigma^2}-\frac{\mu^2}{2\sigma^2}}) \\
&h(x)=\frac1x \cdot c(\theta) = \frac1{\sigma \sqrt{2 \pi}} exp({- \frac{\mu^2}{2 \sigma^2}}) \\
&\theta=(\mu, \sigma)
\end{aligned}$$
This last formula, you've parameterized this family in terms of $\mu$ and $\sigma$, $h(x)$ will be $\frac1x$, $c(\theta)$ will be $\frac1{\sigma \sqrt{2\pi}}$ in front and in the exponent the $e^-{\mu^2}/{2\sigma^2}$ (because both don't depend on x). Figure out what $\omega$ and $t$ is.

Let $t_{1}(x) = ln(x)^2$. Let $t_2 = ln(x)$.
Let $\omega_1(theta)=-\frac1{2\sigma^2}$. Let $\omega_2=\frac\mu{\sigma^2}$.

This is how it fits into the exponential family.

---

Given a random variable:
1. We want to study its "statistics" represented by the k-th moments of this random variable.
        The k'th moment is defined as the $\mathbb{E}[X]^k$
        To study all the moments together in one function, you use the moment generating function. It encodes all the k-th moments of a random variable, thus contains all the statistical information of a random variable. When you want to study it, you don't have to consider each moment separately.

2. We want to study long-term or large-scale behavior. Assume e.g. one random variable with normal distribution. With just a single rand var, you have no control. The outcome can be anything according to that distribution. But if you have several rand vars with the exact same distribution, if the number is super large (i.e. 100 mil) and you plot how many of the rand vars fall into each point on a graph, it starts looking close to the bell curve. Denser in the middle, sparser on the outside. So you lack individual control on each rand var but large scale you know at least with very high probability that it looks bell curve. Which events are likely to happen with i.e. 99.9% probability. Two typical theorems = law of large numbers and central limit theorem.

---
### 2.1 Moment Generating Function
The mgf of a random variable is defined as:
$$M_x(t)=\mathbb{E}[e^{tX}]$$where t is some parameter $t \in \mathbb{R}$
Remark: Does not necessarily converge / exist
Example, lognormal distribution does not have a moment-generating function that converges.

Called mgf because if you take the k'th derivative of the function, then it actually gives the k'th moment of your random variable.
$$
\frac{d^{(k)}M_x}{dt^{(k)}}(0)=\mathbb{E}X^k \ \forall \ k \in \mathbb{N}\ integers
$$
That gives a different way of writing a mgf.
Because we may write the mgf as:
$$
M_x(t)=\sum_{k=0}^{\infty}{\frac{t^k}{k!}}\cdot (m_k,\ the\ k'th\ moment,=\mathbb{E}[X^k])
$$
based off the taylor expansion. Only if the mgf exists.

### Theorem 2.2

The mgf classifies your random variable.
So if two random variables X, Y have the same mgf, then X and Y have the same distribution.

The mgf encodes all info about your rand var, you're not losing anything. But be careful when applying this theorem because:
Remark. It does not imply that all random variables with identical k-th moments $\forall (k \in \mathbb{N})$ will have the same distribution.

If X and Y HAVE a mgf and they're the same, then they have the same distribution. Hole is that even if they have the same moments, it doesn't necessarily imply that they have the same mgf. They might both not have mgfs (i.e., mgfs don't exist). So, same moments may not mean they have the same distribution.


Sequence of random variables
If $X_1, X_2, ...$ is an infinite sequence of random variables, st. the mgf exists and it converges to the mfg for some variable x for all t.
$$M_{X_T}(t) \rightarrow M_X(t)
$$
The sequence of rand vars, whose mgf exists, and at each point t, it converges to the value of the mgf of some other random variable X.

In light of this theorem, it should be the case that the distribution of this sequence gets closer to the distribution of this random variable x.

To make that information formal, we write we conclude that for all x, the probability that X_i < x tends to the probability that X <= x. In this sense, the distributions of these random variables X_i converges to the distribution of that random variable X.
> Pointwise convergence is implied here. Thus the conclusion is also weak (weakest convergence in distribution)

**Several possible ways to define convergence but is technicality. Spirit is that the sequence converges if its mgf converges.**

Thus, if mgf exists, it's a powerful tool that allows to control the distribution. Applied in central limit theorem later.


### Theorem 3.1 Law of Large Numbers
Weak law of large numbers.
Let $X_1, X_2, ..., X_n$ be iid (iden indep distributed variables).

Let mean $\mu$, variance $\sigma^2$.

Define x = average of n random variables
X = $\frac1n (X_1+X_2...)$
Then the probability that $P(|X-\mu| \ge \epsilon) \rightarrow 0$ as $n \rightarrow \infty$, for all $\epsilon$

So whenever you have iids, when you take their average, if you take a large enough number of samples, they will be very close to the mean.

Example is in the casino. If playing blackjack, you have a very small disadvantage playing the optimal strategy, something like 48-49% win chance.
Designed so that variance is so big that this expectation mean is hidden.
Because player short sample, looks like mean doesn't matter because variance takes over. From casino POV, they take a very large n. For each round, from the casino's pov, taking enormous values of n. As long as they have slight advantage, they win large amount of money.
Most games played in casinos are designed like this. Looks like mean close to 50% but hidden by large variance. Casino has enough players playing the game so that the law of large numbers makes them money.

Rule of large numbers in this sense doesn't apply to poker because you're playing against other players. If you have an advantage by skill than other player, by say 5%, then you have edge over that player so you can win money. But in poker you're not playing against the casino so instead they take rake. For each round played by the players, they pay some fee to the casino. So money = accumulating fee there, not taking a chance bet.
If your edge > fee that the casino charges you, then now you can apply law of large numbers to yourself and win.

Example hedge fund doing high frequency trading that's the moral behind it, believing you have a small edge and win over time.
Problem is with large variance your belief starts to fall then it looks like expectation is negative.

**Proof of law of large numbers.**
Observe that the expectation of X is just (drop in definition of X):
$$\begin{aligned}
\mathbb{E}[X] &= \mathbb{E}[\frac1n \sum_{i=1}^n{X_i}] \\
&= \frac1n \sum_{i=1}^n \mathbb{E}X_i   \ (by\ linearity) \\
&= \mu
\end{aligned}$$
For the variance of X:
$$\begin{aligned}
\mathbb{V}(X) &= \mathbb{E}[(X-\mu)^2] \\
&= \mathbb{E}[(\frac1n \sum{(X_i-\mu)})^2] \\
&= \mathbb{E}[\frac1{n^2} \sum_{i=1}^n{(X_i-\mu)^2}] \\
&= \sigma^2/n

\end{aligned}$$

Therefore, the effect of averaging n terms does not affect average but it affects variance (it divides variance by sample size n) which gets smaller and smaller.
Using that we prove the statement:
Notice that probability x-mu >= epsilon, multiplied by epsilon squared, will be <= the variance of X.
$$\begin{aligned}

\epsilon^2 \cdot P(|X-\mu| \ge \epsilon) \le \mathbb{V}[X] = \frac{\sigma^2}{n} \\
P(|X-\mu| \ge \epsilon) \le \frac{\sigma^2}{n \epsilon^2} \\
When\ n\rightarrow \infty,\ term  \rightarrow 0,\ Prob\ deviate\ from\ mean\ by >\epsilon \rightarrow 0
\end{aligned}$$
This inequality holds because variance X is defined as (expectation of X minus mu), squared. For all the events when you have X-mu at least epsilon, your multiplying factor X^2 will be at least $\epsilon^2$ when you fall into the event $|X-\mu| \ge \epsilon$ we're looking at the probability for. Therefore, your variance must be at least that.

This proof also tells a bit more about the speed of convergence. Let's say you have a random variable X. Mean 50, epsilon 0.1.
Probability deviate from mean by more than 0.1 (epsilon). For example, want to be 99% sure that $|X-\mu|<0.1$. In this case, you want that PROBABILITY to be 0.01, hence $0.01 = \frac{\sigma^2}{n \epsilon^2} <= 0.01$. Plug in variance, epsilon, and get some bound of n. If you have more than that many trials, you can be 99% sure that you don't deviate from your mean by > epsilon. Gives some estimation but this is a very bad estimate. There are much more powerful estimates that can be done. That's an order of magnitude, millions of trials from here but in practice, using a lot more powerful tools (simialr to moment generating functions) of estimating, hundreds of most thousands.

By the name there is also the strong law of large numbers. In that theorem, conclusion is much stronger so convergence is stronger than here.
Also the condition given is very strong but weak law of large numbers can still hold if weakened, for example, the variance does not have to exist, it can be replaced by some other condition etc.

### 4. Central Limit Theorem
1:03:54

The weak law of large numbers (WLLN) said that if you have IID random variables 1/n SUM(X_i) over time this converges to $\mu$ mean in some weak sense. This happens because that 1/n SUM has mean $\mu$ and variance $\frac{\sigma^2}{n}$.

We exploit the fact that variance vanishes to get this. So replace 1/n with 1/sqrt(n).
What happens for a random variable $\frac1{\sqrt{n}} \sum_{i=1}^n X_i$, if $X_i$ has mean = 0?
We make this choice of 1/sqrt(n) is because if you do, now the average has mean of mu **=0** and variance of $\sigma^2$ just as in X_i. So this (the mean and var) is the same as X_i.

If rand var is the same mean and variance as original random variable, question is whether the distributions are equal. The central limit theorem answers this question.
When you take many indep events and take the average in this sense, their distribution converges to a normal distribution.

**Theorem:
**
Let $X_1, X_2,...,X_n$ be a IID random vars with mean $\mu$ variance $\sigma^2$.
Let $Y_n=\frac1{\sqrt{n}} \sum_{i=1}^n{(x_i - \mu)}$
Then, the distribution of $Y_n$ converges to that of the normal distribution with mean 0 and variance $\sigma^2$.
This means that $\forall x$ the probability $P(Y_n \le x) \rightarrow P(\mathcal{N}(0, \sigma^2) \le x)$

Interesting here is no matter what distribution you had in the beginning, if you average it out in this sense, then you converge to normal distribution.

**Proof:**
Prove it when the mgf exists. Assume that mgf $M_{X_i}(t)$ exists.
Central Limit Theorem earlier which was that if you know the mgf of $Y_n$s converges to the mgf of the normal, then the distribution converges.
Goal = prove the mgf of these $Y_n$s converges to the mgf of the normal, for all t (pointwise convergence).
$$
M_{Y_n}(t) \rightarrow M_{\mathcal{N}(0, \sigma^2)}(t) = e^\frac{{t^2 \sigma^2}}{2}
$$
!!! The mgf of the normal is well known as $e^\frac{{t^2 \sigma^2}}{2}$.
$$\begin{aligned}
M_{Y_n}(t) &= \mathbb{E}[e^{tY_n}] = \mathbb{E}[e^{t\cdot \frac1{\sqrt{n}} \sum_1^n{(x_i-\mu)}}]
\end{aligned}$$
Then, because each $X_i$s are independent, this sum will split into products.
$$\begin{aligned}
=\mathbb{E}\left[ \prod_{i=1}^n e^{t\cdot \frac1{\sqrt{n}} \sum_1^n{(x_i-\mu)}} \right]
\end{aligned}$$
Then because they're independent, product goes out.
$$\begin{aligned}

=\prod_{i=1}^n \mathbb{E} [e^{t\cdot \frac1{\sqrt{n}} \sum_1^n{(x_i-\mu)}}]

\end{aligned}$$
They're iid so you just have to take the n'th power:
$$\begin{aligned}

=\mathbb{E} \left[e^{t\cdot \frac1{\sqrt{n}} \sum_1^n{(x_i-\mu)}} \right]^n

\end{aligned}$$
Now we do some estimation with the Taylor expansion of this.
$$\begin{aligned}

=\mathbb{E} \left[1 + {\frac{t}{\sqrt{n}} {(x_i-\mu)}}
+ \frac1{2!}\cdot{\frac{t}{\sqrt{n}} {(x_i-\mu)^2}}
+ \frac1{3!}\cdot{\frac{t}{\sqrt{n}} {(x_i-\mu)^3}}...

\right]^n

\end{aligned}$$
The 1 comes out, second term is 0 because $x_i$ has mean $\mu$.
$$\begin{aligned}

= [1 &+ \frac12 \frac{t}{\sqrt{n}}\sigma^2 \ which\ is\ (x_i-\mu)^2\ when\ you\ take\ its\ expectation \\
&+ ...\ the\ terms\ after
]^n

\end{aligned}$$
For the terms after, because we're only interested in proving that for fixed t, this converges pointwise, we may consider t a fixed number. So when n goes to infinity, then all these terms are smaller orders of magnitude
$$\begin{aligned}
...+o (\frac1n )... \\
=[e^{\frac12 \frac{t^2 \sigma^2}n + o \frac1n}]^n
\end{aligned}$$
Then the n multiplies and cancels out.
We see that it ($M_{Y_n}(t)$) $=e^{\frac{t^2 \sigma^2}2+o}$
And as n goes to infinity o goes to 0.

Then by the earlier theorem, if we have this mgf converging, then we know the distribution converges.

Suppose there exists a random variable $\exists rand var\ X$ with unknown mean.
Goal is to estimate the mean. One way to do that is to make many indep trials of this randvar.
When taking trials $X_1, X_2,...,X_n$ and use $\frac{1}{n}(X_1+X_2+...+X_n)$ as our estimator of mean.
The law of large numbers says that this will be very close to the mean with n large enough, more than likely have a value close to the mean.
And then the central limit theorem tells you how the distribution of this variable is around the mean (the distribution of this sampling estimator will be somewhat normal around the true mean).

Because normal distrib has very small tails, we'll get really close quickly.

===



$$\begin{aligned}
Var(X\cdot e^Y) \\
&= E[(X\cdot e^Y)^2] - E[X\cdot e^Y]^2 \\
&= E[X^2\cdot e^{2Y}] - E[X\cdot e^Y]^2 \\
&= E[X^2\cdot e^{2Y}] - 1.65^2 \\
&= E[X^2] \cdot E[e^{2Y}] - 1.65^2 \\
&= 5 \cdot E[e^{2Y}] - 1.65^2 \\
&= 5 \cdot e^2 - 1.65^2 \\
\end{aligned}$$
