Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 5 M2V15-16 Linear Optimization]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Review of Nonlinear Optimization

> "​This module will review non-linear optimization, ​we'll go through the basics of ​non-linear optimization and ​we'll also talk about Lagrangian Relaxation, ​which is a technique that we use when there are ​constraints in the non-linear problem. ​It will be important when we start ​talking about portfolio selection it turns out ​the Lagrangian relaxation gives you ​a very nice way to work with portfolios. ​"

---
### Unconstrained Nonlinear Optimization

Hessian matrix section 0:24 to 6:20 the term should say "Positive definite" instead of Positive semidefinite, as the = local minimum

Unconstrained means that you're allowed to choose any vector that you like to try to minimize a function. To keep everything general, assume our optimization goal:
$min_{x\in \mathbb{R}^n} f(x)$ is our objective and thus x is a vector with n different components. It's an unconstrained problem so you can try minimize f over the entire space. 

It turns out that for nonlinear optimization, we have to differentiate between two minimum problems.
Ordinarily, we just want to find a vector which takes the minimum possible value.
![[Pasted image 20260419010404.png]]
In the following one dimensional x, f(x) yields a minimum point at x*.
It's the global min, the best point across the entire real line. But as we go through both derivatives, first derivative = gradient and second derivative Hessian matrix.

Derivatives can only look in the neighborhood of a point, they can't look far because derivatives are defined as taken limits of points coming arbitrarily close. The dip on the left is a local minimum because in just the neighborhood of the point, looking for points in the general interval, that point is the optimum. But if you leave the neighborhood then you get other points that are better or at least as good (i.e., x* as the global optimum point).
But within this interval I can't get any other point.

So for nonlinear optimization you have two categories of minimum points:
- x* is the global minimum if $f(y) \ge f(x*) \forall y$
- $x^*_{loc}$ local minimum if $f(y) \ge f(x^*_{loc}) \forall y \text{ s.t. } ||y-x^*_{loc}|| \le r$
Sufficient condition for local minimum:
- gradient $\nabla f(x) = \begin{bmatrix} \frac{\delta f}{\delta x_1} \\ \vdots \\ \frac{\delta f}{\delta x_n} \end{bmatrix} = \boldsymbol{0}$: local stationarity. Partial derivatives of the functions with respect to each component. Every component must be equal to 0.
- Hessian $\nabla^2 f(x) = \begin{bmatrix} \frac{\delta^2 f}{\delta x_1^2} & \frac{\delta^2 f}{\delta x_1 \delta x_2} & \cdots & \frac{\delta^2 f}{\delta x_1 \delta x_n} \\ \vdots&\vdots&\ddots&\vdots \\ \frac{\delta^2 f}{\delta x_n \delta x_1} & \frac{\delta^2 f}{\delta x_n \delta x_2} & \cdots & \frac{\delta^2 f}{\delta x_n^2} \end{bmatrix}$: positive **definite** (not just semi-definite)
Gradient condition is sufficient if the function f(x) is convex.

Example, if $f(x) = 2x_1^2 + 3x_2$:
$\frac{\delta f}{\delta x_1} = 4x_1$ and $\frac{\delta f}{\delta x_2} = 3$. Thus, $\nabla = \begin{bmatrix} 4x_1 \\ 3 \end{bmatrix}$. This is equal to 0 when $x_1$ = 0 for a local minimum. But that alone is not enough. We have to then take the matrix of second derivatives which must be positive semidefinite at any local minimum and positive definite if you want to be SURE that point is a local minimum.
So $Hessian_{11}$ is second deriv with respect to $x_1$ twice and 12 (one to the right) is with respect to $x_1$ then $x_2$. If a function is twice differentiable, then it doesn't matter the order with which you take the derivatives. To get a local min, that 2nd deriv matrix must have all non-negative eigenvalues. If all non-negative, then local min, if all strictly positive, then definitely a local min.

A function is convex if it "curves up" U shape. Take any two points, draw a straight line connecting, that straight point lines at/above the function so it is convex.
![[Pasted image 20260419134054.png]]
No cross-over or curve down etc. Convex functions are nice if trying to minimize because you don't have to check the Hessian. Just get gradient = 0.

---
### Unconstrained Nonlinear Optimization - Two Examples
Optimization problem:
$$\begin{aligned}
min_{x \in \mathbb{R}^2 x_1^2 + 3x_1x_2 + x_2^3}
\end{aligned}$$
Gradient (solve system of two equations):
$$\nabla f(x) = \begin{bmatrix} 2x_1+3x_2 \\ 3x_1 + 3x_2^2 \end{bmatrix} = 0 \rightarrow x=0, \begin{bmatrix}-\frac94 \\ \frac32 \end{bmatrix}$$
Hessian at x: $H = \begin{bmatrix} 2 & 3 \\ 3 & 6x_2 \end{bmatrix}$. The off diagonal of the matrix (the 3s) will be symmetrical.
- $x = 0: H = \begin{bmatrix} 2 & 3 \\ 3 & 0 \end{bmatrix}$. Not positive definite. Not local minimum. It has one positive eigenvalue and one negative eigenvalue. a is positive but determinant is negative. 
- $x = \begin{bmatrix} -\frac94 \frac32 \end{bmatrix}: H = \begin{bmatrix}2 & 3 \\ 3 & 9 \end{bmatrix}$. Positive semidefinite (and indeed positive DEFINITE). Local minimum.

---
Now we move onto constrained problems.
### Lagrangian Method
Constrained optimization problem.
$$\begin{aligned}
max_{x\in \mathbb{R}^2} 2ln(1+x_1)+4ln(1+x_2), \\
\text{s.t. } x_1+x_2=12
\end{aligned}$$
Convex problem. But constraints make the problem hard to solve.
The example problem, I have total wealth of 12 to be allocated between two businesses. Your goal is to maximize the payoff. The point of the log function means the more and more I put in, diminishing returns coming out of it. This is a convex function because log is a concave function and trying to maximize a concave function with respect to some linear constraints is a convex problem.

To get rid of the constraints, you can multiply it by a variable and add it to the objective. This multiplier v is sometimes called the Lagrange multiplier. The constraint 12 has been moved to the other side and hence -12. Subtract the whole thing from the maximization objective.
Solution = form a Lagrangian function
$$\begin{aligned}
\mathcal{L}(x, \mathbf{v}) = 2ln(1+x_1)+4ln(1+x_2)-v(x_1+x_2-12)
\end{aligned}$$
Now we can throw away the constraint.
This is similar to what we did on linear optimization when we dualized the constraints - multiply by a quantity multiplier with particular signs. Here we throw away the signs as well; v can be anything.

Compute the stationary points of the Lagrangian as a function of v:
$$\begin{aligned}
\nabla \mathcal{L}(\mathbf{x}, v) = \begin{bmatrix}
\frac2{1+x_1}-v \\
\frac4{1+x_2}-v
\end{bmatrix} = \mathbf{0}
\rightarrow
x_1 = \frac2v-1, x_2=\frac4v-1
\end{aligned}$$
Now, solve for v. Substituting in the constraint $x_1+x_2=12$ we get
$$\begin{aligned}
\frac6v=14 \rightarrow v=\frac37 \rightarrow \mathbf{x}=\frac13 \begin{bmatrix} 11 \\ 25 \end{bmatrix}
\end{aligned}$$
X is 11/3 and 25/3. Invest more in the second opportunity because it has a higher return $4ln(1+x_2)$. But as you scale up that return, the investment has dinimishing returns, so at some point it becomes profitable to go to the first one. The correct balance is in the ratio of 11:25.

---
### Portfolio Selection
Optimization problem
$$\begin{aligned}
max_\mathbf{x} \mathbf{\mu}^T\mathbf{x} - \lambda \mathbf{x}^T\mathbf{Vx} \\
\text{s.t. } \mathbf{1}^T\mathbf{x}=1
\end{aligned}$$
Constraints make the problem hard. 
$x \in \mathbb{R}^n$ so x has n different assets, vector with n components. The constraint is actually matrix sum of all elements $=\sum_{j=1}^n x_j$. $1 to invest. Choose a portfolio that maximizes return minus a risk aversion parameter lambda times the variance. So, maximize risk adjusted return.

Solution = again move the constraint into the objective via Lagrangian function.
$$\begin{aligned}
\mathcal{L}(\mathbf{x}, v) = \mathbf{\mu}^T\mathbf{x} - \lambda \mathbf{x}^T \mathbf{Vx} - v(\mathbf{1}^T \mathbf{x} - 1)
\end{aligned}$$
Solve for the maximum value with no constraints. No constraints, take derivative and equal to 0. 
$$\begin{aligned}
\mathbf{\nabla}_x \mathcal{L}(\mathbf{x}, v) = \mathbf{\mu} - 2\lambda \mathbf{Vx} - v\mathbf{1} = 0 \rightarrow \mathbf{x} = \frac1{2 \lambda} \cdot \mathbf{V}^{-1} (\mathbf{\mu} - v\mathbf{1})
\end{aligned}$$
This sets gradient = 0 and then isolates x on the right equation.

Solve for little v scalar from the constraint, plugging in x:
$$\begin{aligned}
\mathbf{1}^T \mathbf{x} = 1
\rightarrow
\mathbf{1}^T \mathbf{V}^{-1} (\mathbf{\mu}-v\mathbf{1}) = 2\lambda
\rightarrow
v = \frac{\mathbf{1}^T \mathbf{V}^-1 \mathbf{\mu} - 2 \lambda}{\mathbf{1}^T \mathbf{V}^{-1}\mathbf{1}}
\end{aligned}$$
Substitute back in the expression for $\mathbf{x}$, namely in the $\mathbf{x} = \frac1{2 \lambda} \cdot \mathbf{V}^{-1} (\mathbf{\mu} - v\mathbf{1})$.

Now using this technique, you can generate efficient frontiers, characterize their shape, any point of this frontier can be generated by a small set of mutual funds, this ultimately leads to the capital asset pricing model methodology for pricing assets in the market.


