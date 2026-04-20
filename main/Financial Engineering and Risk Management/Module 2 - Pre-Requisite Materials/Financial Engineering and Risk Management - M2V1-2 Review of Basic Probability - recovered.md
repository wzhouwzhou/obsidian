
"embedding_models:transformers#1774190777508": {"api_key":"","provider_key":"transformers","model_key":"TaylorAI/bge-micro-v2","dims":384,"max_tokens":512,"class_name":"EmbeddingModel","created_at":1774190777508,"key":"transformers#1774190777508"},

### Discrete Random Variables
The variance of any random variable, X, is defined as:
$$
\begin{align}
Var(X) :&= E[(X-E[X])^2] \\
        &= E[X^2] - E[X]^2
\end{align}
$$
### The Binomial Distribution
We say X has a binomial distribution `X ~ Bin(n,p)`
If X represents number of heads in n independent coin tosses, p = P(head).
$$
\begin{align}
P(X=r)&=\left( \begin{array} \\n \\ r\end{array} \right)p^r(1-p)^{n-r} \\

E[X] &= np \\
Var(X) &= np(1-p)
\end{align}
$$

Example:
If p = probability outperform and 1-p underperform,

```dataviewjs
const n = 10, r = 8, p = 0.5;
const f = x => x <= 1 ? 1 : x * f(x - 1);
const ff = r => f(n) / (f(r) * f(n - r));
const v = ff(r);

let sum = 0;
for (let r = 8; r <= 10; ++r)
  sum += ff(r) * (p ** r) * ((1-p) ** (n - r));

dv.paragraph(`$$

\\begin{aligned}
For \\binom{10}{8} \\\\

nCr\\ = (10\\ C\\ 8)
&= \\frac{10!}{8!\\cdot2!} \\\\
&= ${v} \\\\


P(X>=8) &= \sum_{r=8}^{n}{\\binom{n}{r}p^r(1-p)^{n-r}} \\ where \\ n=10 \\ and \\ p=1/2 \\\\
&= ${sum} \\\\

\\end{aligned}
$$`);
```


### Log-Normal Distribution
$X \sim LN(\mu, \sigma^2)$ = $log(X) \sim N(\mu, \sigma^2)$