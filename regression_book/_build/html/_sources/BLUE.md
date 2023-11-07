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
Thus, to find the BLUE estimator for $\beta_1$ we must find $\{d_i\}_{i=1}^n$ that satisfy {eq}`eq_betaConditions` and minimize {eq}`eq_varianceCondition`. One could use Lagrange multipliers to find the coefficients, but we will rely on the following lemma.  For a proof see [Lemma 11.2.7]{cite}`casella_statistical_2002`.

````{prf:lemma}
:label: lemma_Casella

Let $\left(v_1, \ldots, v_k\right)$ be constants and let $\left(c_1, \ldots, c_k\right)$ be positive constants. Then, for $\mathcal{A}=\left\{\mathbf{a}=\left(a_1, \ldots, a_k\right): \sum a_i=0\right\}$,

$$
\max _{\mathbf{a} \in \mathcal{A}}\left\{\frac{\left(\sum_{i=1}^k a_i v_i\right)^2}{\sum_{i=1}^k a_i^2 / c_i}\right\}=\sum_{i=1}^k c_i\left(v_i-\bar{v}_c\right)^2
$$

where $\bar{v}_c=\frac{\sum c_i v_i}{ \sum c_i }$. The maximum is attained at any $\mathbf{a}$ of the form $a_i=K c_i\left(v_i-\right.$ $\left.\bar{v}_c\right)$, where $K$ is a nonzero constant.
````
