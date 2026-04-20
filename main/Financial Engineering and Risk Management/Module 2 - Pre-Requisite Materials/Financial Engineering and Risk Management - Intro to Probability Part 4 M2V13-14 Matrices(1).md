Prior: [[Financial Engineering and Risk Management - Intro to Probability Part 3 M2V11-12 Vectors]]

__Video Contents__: 
Martin Haugh / Garud Iyengar
Columbia University
Industrial Engineering and Operations Research

## Review of Matrices
> "​In this module, we are going to review matrices. ​We'll define matrices. ​We're going to define operations ​such as transposes, inverses. ​We're going to talk about ​linear functions and how they are related to matrices. ​We're going to define concepts such as rank, ​which will play a role later on in the course in ​defining complete markets and hedging instruments."

---
### Matrices 
Matrices are rectangular arrays of real numbers
Examples: 
$A = \left[ \matrix{2 & 3 & 7 \\ 1 & 6 & 5} \right]$: 2x3 matrix (two rows three columns). Index by the (row, col). Here, $A_{12}$ = 3. $A_{23}$ = 5.
$B = [\matrix{2 & 3 & 7}]$: 1x3 matrix $\equiv$ row vector (where rows = 1). Column vectors have col = 1 and several rows. In the case of a vertical 3x1, this is $R^3$ aka $R^{3x1}$.
$$A = \left[ \matrix{a_{11} & a_{12} & ... & a_{1n} \\
a_{21} & a_{22} & ... & a_{2n} \\
... & ... & ... & ... \\
a_{m1} & a_{m2} & ... & a_{mn}
} \right]$$: m x n matrix ... $\mathbb{R}^{m \mathcal{x} n}$

$$I = \left[ \matrix{1 & 0 & ... & 0 \\
0 & 1 & ... & 0 \\
... & ... & ... & ... \\
0 & 0 & ... & 1
} \right]$$
: m x n Identity matrix. 1s along the diagonal and else are 0.
It turns out when multiplying matricies, this is effectively "1".

Vectors are clearly also matrices.

---
### Matrix Operations: Transpose
Transpose $A \in \mathbb{R}^{m x n}$. Swap rows and columns.
$$A^T = \left[ \matrix{a_{11} & a_{12} & ... & a_{1n} \\
a_{21} & a_{22} & ... & a_{2n} \\
... & ... & ... & ... \\
a_{m1} & a_{m2} & ... & a_{mn}
} \right]^T

=

\left[ \matrix{a_{11} & a_{21} & ... & a_{m1} \\
a_{12} & a_{22} & ... & a_{m2} \\
... & ... & ... & ... \\
a_{1n} & a_{2n} & ... & a_{mn}
} \right]
$$
Transpose of a row vector is a column vector.
Examples:
$A = \left[ \matrix{2 & 3 & 7 \\ 1 &6 & 5} \right]$: 2 x 3 matrix ... $A^T = \left[ \matrix{2 & 1 \\ 3 & 6 \\ 7 & 5} \right]$: 3 x 2 matrix
$v = \left[ \matrix{2 \\ 6 \\ 4} \right]$: column vector ... $v^T = \left[ \matrix{2 & 6 & 4} \right]$: row vector

---
### Matrix Operations: Multiplication
Multiplication: $A \in \mathbb{R}^{m x d}, B \in \mathbb{R}^{d x p}$ then $C = AB \in \mathbb{R}^{m x p}$. Row index m column index d. The row index of what you multiply against must be the same as column index of original (hence the d in mxd and dxp shapes of A and B, otherwise cannot multiply). The column length of B can be anything. You get an output of m x p so long as the inner dimensions are the same. 
$$c_{ij} = [ \array{a_{i1} & a_{i2} & ... & a_{id}}] \left[ \array{b_{ij} \\ b_{2j} \\ ... \\ b_{dj}} \right] =\sum_{l=1}^d a_{il}b_{ld}
$$
Row vector $v \in \mathbb{R}^{1xd}$ times column vector $w \in \mathbb{R}^{dx1}$ is a scalar.
Identity times any matrix $AI_n = I_m A = A$.
Examples:
$$\left[
\array{2 & 3 & 7 \\ 1 & 6 & 5} \right]
\left[ \array{2 \\ 6 \\ 4 } \right] =
\left[ 
\array{2(2)+3(6)+7(4) \\ 1(2)+6(6)+5(4)}
\right] =
\left[ \array{50 \\ 58}
\right]
$$
This is multiplying $R^{2x3}$ multiplied by a matrix in $R^{3x1}$. Your output c is $R^{2x1}$ given that the 3 inner shape is shared and outer dimensions define the product. Each element is the sumproduct row and column. To get $C_{11}$ and $C_{21}$.

$l_2$ norm: $$\begin{aligned}
||\left[\array{1 \\ -2} \right]||_2=\sqrt{1^2+(-2)^2} 
&= \sqrt{ \array{[1 & -2]} \left[ \array{1 \\ -2} \right] } \\
&= \sqrt{ \left[ \array{1 \\ -2} \right]^T \left[ \array{1 \\ -2} \right] }
\end{aligned}$$L2 norm is elementwise squared then sqrt, this is the dot product of itself sqrt'd. 

Inner product $v \cdot w = v^Tw$, so L2 norm is just sqrt of that.

---
### Linear functions
A function $f: \mathbb{R}^d \mapsto \mathbb{R}^m$ is linear if $$f(\alpha x + \beta y) = \alpha f(x) + \beta f(y),\ \alpha,\beta \in \mathbb{R}, x, y \in \mathbb{R}^d$$
A function f is linear if and only if $f(x) = Ax$ for matrix $A \in \mathbb{R}^{m x d}$. So it's linear if and only if you can find some matrix A.

Examples:
$$\begin{aligned}
f(x)&: \mathbb{R}^3 \mapsto \mathbb{R}: f(x) = [\array{2 & 3 & 4}] \left[ \array{x_1 \\ x_2 \\ x_3} \right] = 2x_1 + 3x_2 + 4x_3 \\

f(x)&: \mathbb{R}^3 \mapsto \mathbb{R}^2: f(x) = \left[ \array{2 & 3 & 4 \\ 1 & 0 & 2} \right] \left[ \array{x_1 \\ x_2 \\ x_3} \right] \\
&= \left[ \array{ 2x_1 + 3x_2 + 4x_3 \\ x_1 + 2x_3 } \right]
\end{aligned}$$
In the first example, A = $[2\ 3\ 4]$ of shape 1x3, d=3, m=1.
In the second example, A is 2x3. Output of the function is 2 rows x 1 col.

> "So in most of this course, ​we won't really be interested in just functions, ​we'll be interested in constraints, ​we'll be interested in sets of ​vectors that are defined by functions. ​These might be portfolios, ​these might be values of options, ​these might be other things ​that are random variables, and so on. ​So we're going to talk about two ​different kinds of constraints"

Linear constraints define sets of vectors that satisfy linear relationships.
- Linear equality: $\set{x: Ax=b}$ ... line, plane, etc.
- Linear inequality: $\set{x: Ax \le b}$ ... half-space.

For example, $[2, 3] \le [4, 5]$ because component-by-component the numbers are less. But $[2, 3] \nleq [4, 1]$ because 3 > 1.

---
### Rank of a Matrix
Column rank of $A \in \mathbb{R}^{m x d}$ = number of linearly independent columns
- range(A) = $\set{y: y=Ax\ for\ some\ x}$ 
- column rank of A = size of basis for range(A)
- column rank of A = m $\implies range(A) = \mathbb{R}^m$
Row rank of A = number of linearly independent rows.
Row rank = column rank, and $rank \le min\set{m,d}$

Example:
$$
A = \left[ \matrix{1 & 2 & 3 \\ 2 & 4 & 6}
\right], rank = 1, range(A)=\set{\lambda \left[ \matrix{1\\2}\right]: \lambda \in \mathbb{R}}
$$
On the right here, if we have that $$Ax = \left[ \matrix{x_1+2x_2+3x_3 \\ 2x_1 + 4x_2 + 6x_3} \right] = (x_1+2x_2+3x_3) \left[ \matrix{1\\2}\right]
$$. The $\left[ \matrix{1\\2}\right]$ scales up the polynomial here.
Graphing this vector generates a line:
![[Pasted image 20260409192137.png]]
The lambda allows infinite extension in $R^2$ space. 

$A \in \mathbb{R}^{n x n}$ and $rank(A)=n$ implies A is invertible, and $A^{-1} \in \mathbb{R}^{nxn}$
This means that the determinant is not 0 when the square matrix has all linearly independent columns and rows.

$$A^{-1}A=AA^{-1}=I$$

Higher rank means that we can get more out of a linear function, lower means less getting out.

