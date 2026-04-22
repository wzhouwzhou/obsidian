Series: [[Introduction to Financial Engineering and Risk Management]]

Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 2 M2V4 Multivariate Distribution and Independence - recovered]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

> "We are now going to discuss the multivariate normal distribution. ​The multivariate normal distribution is a very important distribution in finance. ​It crops up in many different applications including, for example, mean variance ​analysis and asset allocation, as well as geometric Brownian motion and the ​Black-Scholes formula"

---
### The Multivariate Normal Distribution I
If the n-dimensional vector $X$ is multivariate normal with mean vector $\mu$ and covariance matrix $\Sigma$ then we write:
$$X~MN_n(\mu, \Sigma)$$
The subscript n of $N_n$ denotes dimensionality of vector X.

The PDF of X is given by:
$$f_X(x) = \frac1{(2 \pi)^{n/2} |\Sigma|^{1/2}}
e^{1\frac12 (x-\mu)^T \Sigma^{-1}(x-\mu)}
$$
Where $|\cdot|$ denotes the determinant. 

Standard multivariate normal has $\mu = 0$ and $\Sigma = I_n$, the nxn identity matrix. In this case, the $X_i$s are independent. We can see this because the joint PDF of X, i.e., $$f_X(x)=\prod_{i=1}^n \frac1{\sqrt{2 \pi}}e^{-\frac12 x_i^2}$$
This follows from the pdf function above when $\mu=0$ and that term disappears, and sigma $\Sigma$ collases into the identity so the sum ends up just being $x_i^2 \div 2$.

And we know that if joint PDF factorizes into product of marginal PDFs, then the random variables are independent.

Next, the moment generating function MGF of X satisfies:
$$\phi _X(s) = E[e^{s^T X}] = e^{s^T \mu + \frac12 s^T \Sigma s}$$
This is a function of factor s, raise e to the s transpose X.
To illustrate in the one dimensional case:
Suppose that x is a scalar random variable, then the mgf of it is:
$$ \phi_X(s)=E[e^{sx}] = e^{s \mu + \frac12 \sigma^2 s^2} $$when $X \sim \mathcal{N}(\mu, \sigma^2)$. This is the mgf of scalar normal random. Now we generalize it. #formula 

---
### The Multivariate Normal Distribution II
Recall our partition of X into $X_1=(X_1...X_k)^T$ and $X_2 = (X_{k+1}...X_n)^T$.
Extend this notation naturally:
$$\begin{aligned}
\mu = 
\begin{pmatrix}
\mu_1 \\ \mu_2
\end{pmatrix}
\ and\ 
\Sigma =
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12} \\
\Sigma_{21} & \Sigma_{22} \\
\end{pmatrix}
\end{aligned}$$
are the mean and covariance matrix of $(X_1, X_2)$.

Then we have the following results on marginal and conditional distributions of X:
**Marginal Distribution**
The marginal distribution of a multivariate normal random vector is itself normal. In particular, $X_i \sim MN(\mu_i, \Sigma_{ii}), for\ i=1,2$.
The distribution of XI is multivariate normal, example as follows:
$$\begin{aligned}
X_1 \sim MN_{k\ components} (\mu_1, \Sigma_{11}) \\
X_2 \sim MN_{n-k\ components} (\mu_2, \Sigma_{22})

\end{aligned}$$

Bivariate normal density function when correlation between X1 and X2 is 80%:
![[Pasted image 20260401190013.png|697]]

This correlation is visible when rotating the surface:
![[Pasted image 20260401190359.png]]

correl of 0.8 shows that the large values X1 are generally asssociated with large values of X2.

---
### The Multivariate Normal Distribution III
**Conditional Distribution**
Assuming $\Sigma$ is positive definite, the conditional distribution of a multivariate normal distribution is also a multivariate normal distribution. In particular:
$$X_2|X_1=x_1 \in MN(\mu_{2.1},\Sigma_{2.1})$$
where $\mu_{2.1} = \mu_2 + \Sigma_{21} \Sigma_{11}^{-1} (x_1-\mu_1)$ and $\Sigma_{2.1} = \Sigma_{22} - \Sigma{21} \Sigma_{11}^{-1} \Sigma_{12}$.

Intuition for this result. graph points of X1/X2 in a scatter from some distribution (ie bivar normal). 
![[Pasted image 20260401220539.png]]
![[Pasted image 20260421231318.png]]

For a given x1, with correlation, x2 is more likely to be up there above the mean. Likewise, we also expect variance of X2 to have shrunk, knowing something about X1 would tell us something about X2 and reduce uncertainty about the location of X2. The expression for $\Sigma_{2.1}$ tells us how to actually do that.
Hence conditional distribution of a multivariate normal is also multivariate normal.

**Linear Combinations**
A linear combination, $AX+a$ of a multivariate normal random vector, X, is normally distributed with mean vector $AE[X]+a$ and covariance matrix $A\ Cov(X)\ A^T$.

