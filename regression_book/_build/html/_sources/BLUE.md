### Best Linear Unbiased Estimators (BLUE)

Note that in the least squares estimation of the model parameters, there was no statistical inference as such, we merely fitted a line to the data according to some criterion. We will now show that the $(\hat{\beta}_0,\hat{\beta}_1)$ as derived by OLS are optimal in a statistical sense. 

In particular, we will derive unbiased linear estimators for $\beta_0$ and $\beta_1$ that have the smallest possible variance. Such an estimator will be called a *best* estimator. An estimator is linear if it is of the form

````{math}
:label: eq_estimator
    \sum_{i=1}^n d_i Y_i
````
where $\{d_i\}_{i=1}^n$ are fixed constants. If {eq}`eq_estimator` is an unbiased estimator of $\beta_1$, then 
````{math}
    \beta_1 = \mathbb{E}\left[\sum_{i=1}^n d_i Y_i\right] =  \beta_0  \sum_{i=1}^n d_i  + \beta_1 \sum_{i=1}^n x_i d_i,
````
whence 
````{math}
:label: eq_betaConditions
     \sum_{i=1}^n d_i = 0 \quad \text{ and } \quad  \sum_{i=1}^n x_i d_i = 1.
````
Note that 
````{math}
:label: eq_varianceCondition
     \text{Var}\left[ \sum_{i=1}^n d_i Y_i \right] = \sigma^2 \sum_{i=1}^n d_i^2.
````
Thus, to find the BLUE estimator for $\beta_1$ we must find $\{d_i\}_{i=1}^n$ that satisfy {eq}`eq_betaConditions` and minimize {eq}`eq_varianceCondition`. Similarly, to find the BLUE estimator for $\beta_0$ we must find $\{d_i\}_{i=1}^n$ that minimize {eq}`eq_varianceCondition` and satisfies

````{math}
:label: eq_alphaConditions
     \sum_{i=1}^n d_i = 1 \quad \text{ and } \quad  \sum_{i=1}^n x_i d_i = 0.
````

One could use Lagrange multipliers to find the coefficients, but we will rely on the following lemma.  For a proof see [Lemma 11.2.7]{cite}`casella_statistical_2002`.

````{prf:lemma}
:label: lemma_casella

Let $\left(v_1, \ldots, v_k\right)$ be constants and let $\left(c_1, \ldots, c_k\right)$ be positive constants. Then, for $\mathcal{A}=\left\{\mathbf{a}=\left(a_1, \ldots, a_k\right): \sum a_i=0\right\}$,

$$
\max _{\mathbf{a} \in \mathcal{A}}\left\{\frac{\left(\sum_{i=1}^k a_i v_i\right)^2}{\sum_{i=1}^k a_i^2 / c_i}\right\}=\sum_{i=1}^k c_i\left(v_i-\bar{v}_c\right)^2
$$

where $\bar{v}_c=\frac{\sum c_i v_i}{ \sum c_i }$. The maximum is attained at any $\mathbf{a}$ of the form $a_i=K c_i\left(v_i-\right.$ $\left.\bar{v}_c\right)$, where $K$ is a nonzero constant.
````
We may now state the following

````{prf:proposition}
:label: prop_blue 

The BLUE for $\beta_1$ and $\beta_0$ are given by 

$$
\begin{aligned}
\hat{\beta}_1 = \frac{S_{xY}}{S_{xx}} \quad \text{ and } \quad \hat{\beta}_0 = \bar{Y} - \hat{\beta}_1\bar{x},
\end{aligned}
$$
respectively.
````

````{prf:proof}

We begin by calculating $\hat{\beta}_1$.  Fix a non-zero constant $K$ and let $d_i := K(x_i - \bar{x})$. Then according to {prf:ref}`lemma_casella`, $(d_1,\dots,d_n)$ maximises 

```{math}
:label: eq_toMax
    \frac{\left(\sum_{i=1}^n d_i x_i\right)^2}{\sum_{i=1}^n d_i^2}
```

among all $(d_1,\dots,d_n)$ that satisfy $\sum_{i=1}^n d_i=0$. In particular, if we let $K = \frac{1}{S_{xx}}$, then $\sum_{i=1}^n d_i x_i = 1$, and so $(d_1,\dots,d_n)$ maximizes {eq}`eq_toMax` among all $(d_1,\dots,d_n)$ that satisfy {eq}`eq_betaConditions`. Moreover, in this case {eq}`eq_toMax` becomes

```{math}
    \frac{1}{\sum_{i=1}^n d_i^2},
```
whence $(d_1,\dots,d_n)$ satisfies {eq}`eq_betaConditions` and {eq}`eq_varianceCondition`. We may conclude that $\sum_{i=1}^n d_i Y_i$ is the BLUE estimator for $\beta_1$ where

```{math}
    \sum_{i=1}^n d_i Y_i = \sum_{i=1}^n \frac{(x_i - \bar{x})Y_i}{S_{xx}} = \frac{S_xY}{S_{xx}} = \hat{\beta}_1.
```

````