Series: [[Introduction to Financial Engineering and Risk Management]]

Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 1 M2V3 Review of Conditional Expectations and Variances]]

__Video Contents__:
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Review of Multivariate Distributions
> "We're now going to review multivariate distributions.Â âWe'll talk about multivariate CDFs, multivariate PDFs, conditionalÂ âdistributions, and so on"

---
### Multivariate Distributions I
Let $X=(X_1...X_n)^T$ be an n-dimensional vector of random variables.

**Definition.** $\forall x = (x_1,...,x_n) \in \mathbb{R}^n$, the joint cumulative distribution function (CDF) of X satisfies:
$$F_X(x)=F_X(x_1,...,x_n)=P(X_1 \le x_1,...,X_n \le x_n)$$
> "We say the joint CDF of x is given to usÂ âby the following. So, the joint CDF, Fx of little x is equalÂ âto the probability that X1 is less than or equal to little x1. âX2 is less than or equal to little x2. Up to xn being less than or equal toÂ âlittle x n."

Definition. For a fixed i, the marginal CDF of $X_i$ satisfies:
$$F_{X_i}(x_i) = F_X(\infty,...,\infty, x_i, \infty, ..., \infty)$$
For the marginal CDF of $X_i$ just plug infinity into all the components of the joint CDF except for the ith component, $x_i$.

It is then straightforward to generalize the previous definition to joint marginal distributions. Just plug in infinity again for all the arguments except for ith argument and jth argument as given:
$$F_{ij}(x_i,x_j) = F_X(\infty,...,\infty,x_i,\infty,...,\infty,x_j,\infty,...,\infty)$$
We also say that X has joint PDF $f_X(\cdot,...,\cdot)$ if we can write the joint CDF as an integral of the PDFs:
$$F_X(x_1,...,x_n) = \int_{-\infty}^{x_1} ... \int_{-\infty}^{x_n} f_X (u_1,...,u_n) du_1 ... du_n$$
Integrate the density function $f_X$ by the appropriate limits.

---
### Multivariate Distributions II
Discussing conditional CDFs
**Definition.** If $X_1 = (X_1...X_k)^T$ and $X_2 = (X_{k+1}...X_n)^T$ is a partition of X (1 thru n split at the kth element). Conditional CDF of $X_2$ given $X_1$ satisfies:
$$F_{X_2|X_1}(x_2|x_1) = P(X_2 \le x_2 | X_1=x_1)$$
> "We're going to partition our vector x1 up to xn intoÂ âtwo components. The first component is x1, which containsÂ âx1 up to xk. And the second component is this boldfaceÂ âx2 which contains xk plus 1 up to xn. And then we can talk about the conditionalÂ âCDF of x2 given x1,"

If X has a PDF, $f_X(\cdot)$, then the conditional PDF of $X_2$ given $X_1$ satisfies:
$$f_{X_2|X_1}(x_2|x_1) = \frac{f_X(x)}{f_{X_1}(x_1)}
= \frac{f_{X_1|X_2}(x_1|x_2) f_{X_2}(x_2)}{f_{X_1}(x_1)} \ (1)
$$
and the conditional CDF is then given by integrating the conditional pdf:
$$F_{X_2|X_1}(x_2|x_1) = \int_{-\infty}^{x_{k+1}} ... \int_{-\infty}^{x_{n}} \frac{f_X(x_1,...,x_k, u_{k+1},...,u_n)}{f_{X_1}(x_1)} du_{k+1}...du_n$$
where $f_{X_1}(\cdot)$ is the joint marginal PDF of $X_1$ which is given by:
$$f_{X_1}(x_1,...,x_k) = \int_{-\infty}^{\infty} ... \int_{-\infty}^{\infty} f_X (x_1,...,x_k, u_{k+1},...,u_n) du_{k+1}...du_n$$
---
### Independence
**Definition.** We say the collection X is independent if the joint CDF can be factored into the product of the marginal CDFs so that:
$$F_X(x_1,...,x_n)=F_{X_1}(x_1)...F_{X_n}(x_n)$$

Using (1) above, if $X_1, X_2$ are independent, then:
$$f_{X_2|X_1}(x_2|x_1)= \frac{f_X(x)}{f_{X_1}(x_1)}
=\frac{f_{X_1}(x_1) \cdot f_{X_2}(x_2)}{f_{X_1}(x_1)}
= f_{X_2}(x_2)
$$
So having information about $X_1$ tells you nothing about $X_2$.

---
### Implications of Independence
Let X and Y be independent random variables. Then for any events A and B:
$$P(X \in A, Y \in B) = P(X \in A) P(Y \in B)\ (2)$$
More generally, for any function $f(\cdot),g(\cdot)$, independence of X and Y implies:
$$E[f(X)g(Y)] = E[f(X)] E[g(Y)] \ (3)$$
(2) **follows from** (3) because:
$$\begin{aligned}

P(X\in A, Y\in B) &= E[1_{\{X \in A\}} 1_{\{Y \in B\}}] \\
&= E[1_{\{X \in A\}}] E[1_{\{Y \in B\}}] \\
&= P(X\in A) P(Y \in B)
\end{aligned}$$
The indicator function $1_{\{X \in A\}}$ means that it will take on a value of 1 if $X \in A$, 0 otherwise. When multiplying the indicator functions together, you get a 1 if X is in A, AND, Y is in B. Based on independence of X and Y, we break the expectation of product into product of expectation. And the expectation of an indicator function is the probability of the indicator function.

---
Implications of Indep Cont'd
More generally, if $X_1,...,X_n$ are independent random variables, then:
$$E[f_1(X_1) f_2(X_2) ... f_n(X_n)] = E[f_1(X_1)] \cdot E[f_2(X_2)]...E[f_n(X_n)]$$
The expectation of these functions together factorizes into the product of the separate expectations.

Random variables can also be conditionally independent. For example, X and Y are conditionally indep given Z, for all functions f and g, if:
$$
E[f(X)g(Y)|Z] = E[f(X)|Z] e[g(Y)|Z]
$$
Conditional independence is used in the (now) infamous Gaussian Copula model for pricing CDOs.

CDO context example: in a portfolio of N bonds, let $D_i$ be the event that the $i^{th}$ bond in a portfolio defaults. Not reasonable to assume that the $D_i$s are independent. There may be all sorts of macroeconomic factors or industry specific factors which will cause defaults to actually be dependent - maybe some industry crashes that might cause not just one firm to default but multiple firms in that industry to default.

But maybe they are conditionally independent given some other random variable Z so that
$$P(D_1,...,D_n|Z) = P(D_1|Z)...P(D_n|Z)$$which is often a lot easier to compute
Z might reflect some industry factor i.e., that governs how well a particular industry is doing. if we assume that the default events are conditionally independent given Z, then we can write the probability of D1 up to Dn given Z as the product of those factors, because we've kept Z constant. Individual product components are often easier to compute.

---
### The Mean Vector and Covariance Matrix
The mean vector of X is given by:
$$E[X] := (E[X_1]...E[X_n])^T$$
This is the vector of expected values of the vector components.

The covariance matrix (denoted by capital greek letter $\Sigma$) of X satisfies:
$$\Sigma := Cov(X) := E[(X-E[X]) (X-E[X])^T]$$
so that the $(i,j)^{th}$ element of $\Sigma$ is simply the covariance of $X_i$ and $X_j$. This is E(nx1 vec multiplied by 1xn which yields an nxn covar matrix).

The covariance matrix is symmetric and its diagonal (top left to bottom right) elements satisfy $\Sigma_{i,i} \ge 0$. So $Cov(X_i, X_j) = Cov(X_j, X_i)$, and $Cov(X_i, X_i)=Var(X_i) \ge 0$.

Well known property: It is also positive semi-definite so that $x^T \Sigma x \ge 0 \forall x \in \mathbb{R}^n$. X transpose sigmaX >= 0 for all vectors x in reals.

The correlation matrix $\rho(X)$ "rho of X" has $(i,j)^th$ element $\rho_{ij}:= Corr(X_i, X_j)$. It is also symmetric, positive semidefinite, and 1s along a diagonal.

Formula for correlations: $$Corr(X_i, X_j) := \frac{Cov(X_i,X_j)}{\sqrt{Var(X_i)}Var(X_j)}$$

---
### Variances and Covariances
For any matrix $A \in \mathbb{R}^{kxn}$ and vector $a \in \mathbb{R}^k$, we can take a linear combination of AX plus little a and compute the mean and covariance of this vector $AX+a$:
$$\begin{aligned}
E[AX+a] = AE[X]+a\ (4) \\
Cov(AX+a)=ACov(X)A^T\ (5)
\end{aligned}$$
Now, (5) implies:
$$Var(aX+bY) = a^2 Var(X)+b^2 Var(Y)+ 2abCov(X, Y)$$
If X and Y are independent, then Cov(X,Y) = 0. The converse is not true in general, if covariance is 0, then the variables are NOT NECESSARILY INDEPENDENT
