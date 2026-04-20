Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 4 M2V13-14 Matrices]]


__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Review of Linear Optimization

> "​In this module, we will be walking through ​a review of linear optimization using a hedging example. ​We're going to see ​how there are two kinds of optimization problem, ​something called a primal optimization problem, ​something called a dual optimization problem, ​how they are related. ​We'll also introduce the idea of Lagrangian relaxation. ​"

---
### Hedging Problem
Given $d$ assets, i.e., 3 or 4 some number of assets that are there in the market. 
The price of these assets at time zero is $t=0: p \in \mathbb{R}^d$, therefore, it's some price vector with d components where every component tells me the price of that particular asset.

At time t=1, the market outcomes are uncertain and we have no idea what state the market is going to be. It's going to be in one of $m$ possible states.

So here's stage 0, and then it can branch out to many different states afterwards:
![[Pasted image 20260413234817.png]]

Therefore, the price of asset $j$ in state $i = S_{ij}$.
We can do this two different ways. We can either give the price of all assets at any given state (cross section), or can we can tell the price of a given asset in all possible states. Use matrices to flip these two ideas. 
$S_j$ is a column vector which tells the price of asset j in all possible states. So $S_{1j},S_{2j}$ etc where asset j is fixed. The number of states goes from 1 to m.
Then you can take these columns of assets, stack them up by time, and represent in a matrix $S$ with $m$ state rows and $d$ asset columns:
$$
S_j =
\begin{bmatrix}
S_{1j} \\
S_{2j} \\
\vdots \\
S_{mj}
\end{bmatrix},
\qquad
S =
\begin{bmatrix}
S_1 & S_2 & \cdots & S_d
\end{bmatrix}
=
\begin{bmatrix}
S_{11} & S_{12} & \cdots & S_{1d} \\
S_{21} & S_{22} & \cdots & S_{2d} \\
\vdots & \vdots & \ddots & \vdots \\
S_{m1} & S_{m2} & \cdots & S_{md}
\end{bmatrix}
\in \mathbb{R}^{m \times d}
$$
Each row of this matrix is the set of all assets given a particular state. And column is what happens to a particular asset in all the different states.

Now knowing what happens to the asset, you want to hedge an obligation. An obligation is vector x in m-dimensional real because m different states determine the amount of my obligation. In a bad state, perhaps the liability is worth lower = pay less. You want to buy a portfolio now (a certain number of shares of assets now) to have enough money to pay such obligation.
4;39 ok
Hedge an obligation $X \in \mathbb{R}^m$.
- Have to pay $X_i$ if state $i$ occurs
- Buy/short sell $\theta = (\theta_1,...,\theta_d)^T$ shares to cover obligation
Thetas could be negative = allow possibility of short selling. 


---
Position $\boldsymbol{\theta} \in \mathbb{R}^d$ purchased at time $t=0$.
- $\theta_j =$ number of shares of asset j purchased, $j=1,...,d$
- Cost of the position $\boldsymbol{\theta} = \sum_{j=1}^d p_j \theta_j = \boldsymbol{p}^T \boldsymbol{\theta}$. The inner product of p and theta. The cost is just the price of every asset times number of shares in hedge.

When a state i occurs, you are holding $\theta_j$ shares of the asset which is priced $S_{ij}$. You are liquidating the portfolio now. This is payoff in that state, represented by $y_i$.
Payoff from liquidating position at time t=1:
- payoff $y_i$ in state $i$: $y_i = \sum_{j=1}^d S_{ij} \theta_j$
- Stacking payoffs for all states: $\boldsymbol{y}=\boldsymbol{S \theta}$ , y is simply the matrix of prices of all assets in all market states, weighted by theta.
- Viewing the payoff vector **y**: $\boldsymbol{y} \in range(\boldsymbol{S})$
$$\boldsymbol{y}=[\array{\boldsymbol{S}_1 & \boldsymbol{S}_2 & ... & \boldsymbol{S}_d}]
\left[ \array{\theta_1 \\ \theta_2 \\ ... \\ \theta_d} \right] =
\sum_{j=1}^d \theta_j \boldsymbol{S}_j
$$
So instead of multiplying row by row, think of it as column by column. The above is just swapping the dot product. theta times S not S times theta now. Still summed from j = 1 to d assets. Now the payoff ys are just linear combinations of the columns. With vector y, you can generate a payoff in the range of the matrix S. A vector y belongs to the range of S if these are all vectors of $S \theta$ where $\theta \in R^d$. Therefore y belongs to the range of S.
On the notion of rank, rank tells us how rich a space is and how many different vectors can be generated in the range. So the rank of S = m (all possible payoffs can be generated) for us to then hedge everything. If rank(S) < m, there are certain payoff vectors that cannot be generated because they cannot be produced taking matrix S and multiplying by theta.

Later in course discuss complete and incomplete markets (ie rank of the matrix).

Payoff **y** hedges **X** if $\boldsymbol{y} \ge \boldsymbol{X}$. So component by component, the payoff generated using portfolio is greater than the payoff needed to hedge at time 1.

---
Optimization problem:
Minimize the price of the portfolio such that it hedges obligation. The objective function (max or min) is a linear function of theta. The constraints on what thetas you can choose are also linear 

$$
min \sum_{j=1}^d p_j \theta_j (\equiv p^T \theta)
$$
subject to:
$$\sum_{j=1}^d S_{ij}\theta_j \ge X_i, i=1,...,m (\equiv \boldsymbol{S \theta} \ge \boldsymbol{X})$$
(ie subject to the portfolio hedging my obligation X).

Features of this optimization problem
- Linear objective function: $\boldsymbol{p}^T \boldsymbol{\theta}$ , this is a linear fn of theta
- Linear inequality constraints: $\boldsymbol{S \theta} \ge \boldsymbol{X}$. linear inequality constraint

Example of a linear program
- Linear objective function: either a min/max (doesn't matter)
- Linear inequality and equality constraints
If these are true then we call it a linear program aka linear optimization problem. Model and solve efficiently; can get a lot of interpretation out of them. 
One focus on linear optimization and interpretation = duality.

---
### Linear Programming Duality
Linear program
$$P = min_x c^T x\ subject\ to\ Ax \ge b$$
Another linear program 
$$ D = max_u b^T u\ subject\ to\ A^T u =c,u \ge 0$$
In this case, min becomes a max.
You will be given D from P here, no need to derive D from P.

Theorem.
- Weak Duality: $P \ge D$
- Bound: x feasible for P, u feasible for D, $c^Tx \ge P \ge D \ge b^T u$
- Strong Duality: Suppose P or D finite. Then $P=D$
- Dual of the dual is the primal (original) problem

![[Pasted image 20260418121641.png]]
The minimization of P occurs in a space above such curve / line function P. So the shaded area above P is that $c^T x$ that we're trying to minimize.
Maximizing D is similarly up to D. And D will always be greater than the $b^T u$
The first theorem says that the drawing is correct and $P \ge D$.
Optimal value of primal P will thus be greater than optimal value of D. This generates that chain of inequalities. 

Now:
![[Pasted image 20260418122018.png]]

If you find an x and a u such that $c^Tx$ and $b^T u$ are very close to each other, then x must be close to optimal and u must be close to optimal for the dual. 
Strong duality: If either P or D finite, then they must be equal.
Dual linear programs = dual of a dual is the primal.

---
### More Duality Results
Another primal-dual pair. There is strong duality in the following:
$$min_x\ c^T x = max_u\ b^T u\ subject\ to\ Ax=b\ subject\ to\ A^Tu=c$$
This equality from string duality holds only if you can show that either P OR!!! D is finite.

General concept called Lagrangian relaxation = how to construct a dual. 
Begin with the problem $$\begin{aligned}
P &= min\set{c^T x: Ax \ge b} \\
&\ge min \set{c^Tx - u^T(Ax-b):Ax \ge b}\ \forall\ u\ge0 \\

\end{aligned}$$
You take your principal problem which is minimize $c^Tx$ subject to $Ax \ge b$. Now, you take a vector u which is component wise at least 0. And Ax is still >= b. Therefore, Ax - b >= 0.
If you multiply something >= 0 and multiply it by another thing >= 0, you get to keep the inequality.
So take $c^Tx$ and subtract this positive (u multiplied by Ax-b) term, this will get a lower amount that is <= the previous value. Hence P >= this lower amount.

Then:
$$\begin{aligned}
&\ge min \set{c^Tx - u^T(Ax-b):Ax \ge b}\ \forall\ u\ge0 \\
&\ge b^T u + min \set{(c-A^Tu)^Tx:x \in \mathbb{R}^n} \\

\end{aligned}$$
These two statements are equivalent because the minimization of P is going on over x not over $b^Tu$ so you can move it out to the front and minimize what's left, then factor for x. So you're only minimizing (c-Au)x. 
And what happened to the Ax >= b constraint, threw it away. But you're guaranteed that if you throw away the constraints, the set over which I can optimize, the set of X's that I can choose are larger. Before we used to have a floor value where Ax >= b, but now we relaxed that, and therefore, the objective's minimum only becomes smaller. So that second line is actually smaller than the first line.

Now you have some vector, suppose $D=(c-A^Tu)$ and you want to minimize $D^Tx$. If you have a vector pointing towards top right, how to do this?
![[Pasted image 20260419002036.png]]
Well you multiply this vector by x pointing off to negative infinity. So, nonzero D x large negative x = negative infinity. Hence:
$$
\begin{aligned}
=
\begin{cases}
b^T u & \text{if } A^T u = c \\
-\infty & \text{otherwise}
\end{cases}
\end{aligned}
$$
If D isn't 0, then you get - infinity. Otherwise, if D = 0, meaning $c = A^Tu$, then you get $P \ge b^Tu + 0$.
Hence, $P \ge max \set{b^Tu : A^Tu =c \text{ and } u \ge 0}$
This immediately gives you weak duality. A bit more work can give strong duality.

What we've just done is called dualizing constraints and relaxing them via Lagrangian relaxation.
Dualizing = take constraints, multiply them by a variable which has a particular sign. Ax-b constraint, we multiplied by a vector u which had a positive sign, this is dualization. Then you relax the constraint (throwing away Ax >= b). By doing dualization and relaxation, this is Lagrangiang relaxation, gives you duals which have nice properties.


