## Linear Regression: Univariate Case

Suppose that we have data $\mathcal{D}:=\{(x_i,y_i):i \in \{1,\dots,n\}\}$ where $\{(x_i,y_i)\}_{i=1}^n$ are observed values of random variables $\{Y_i\}_{i=1}^n$ and $\{X_i\}_{i=1}^n$ respectively, satisfying the relationship
```{math}
:label: eq_regression
Y_i = \beta_0 + \beta_1 X_i + \varepsilon_i.
```


Here, $\{\varepsilon_i\}_{i=1}^n$ are uncorrelated mean zero random variables with common variance $\sigma^2$, which we call *random errors*. 

````{prf:definition}
:label: def_regression

For random variables $Y$ and $X$ we define the *population regression function* (or merely the regression) of $Y$ with respect to $X$ as the function $f:\mathbb{R} \to \mathbb{R}$ such that 

$$
    f(x) = \mathbb{E}\left[ Y | X = x \right].
$$
````
In general, the word *regression* is used in statistics to signify a relationship between variables. From equation $(1)$, we can see that the regression function of any $Y_i$ with respect to $X_i$ is of the form 

$$
    \mathbb{E}\left[ Y_i | X_i = x_i \right]  = \beta_0 + \beta_1 x_i,
$$

which is a linear function of $x_i$. Thus, equation (1) defines a *linear regression*. One main purpose of regression is to predict $Y_i$ from of instances of $X_i$, and so it is common to refer to $Y_i$ as the response variable and $X_i$ as the predictor variable. The quantities $\beta_0$ and $\beta_1$ are called the *intercept* and *slope*, respectively, and are assumed to be fixed and unknown. Together they are known as the model *coefficients* or *parameters*. It is these unknown parameters that we wish to estimate, so that we can describe the relationship between the $Y_i$ and $X_i$.

````{prf:definition}
:label: def_sampleMeans

Let $\mathcal{D}:=\{(x_i,y_i):i \in \{1,\dots,n\}\}$ and $\langle\cdot,\cdot\rangle:\mathbb{R} \to \mathbb{R}$ be the canonical inner product on $\mathbb{R}$.

-  We define the *sample means* as 

$$
    \bar{x} = \frac{1}{n}\sum_{i=1}^n x_i \quad \text{ and } \quad  \bar{y} = \frac{1}{n}\sum_{i=1}^n y_i.
$$

- We define the *sums of squares* as 

$$

    S_{xx} = \lVert x-\bar{x}\rVert2  \quad \text{ and } \quad  S_{yy} = \lVert y-\bar{y}\rVert2.
$$

- We define the *sums of cross-products* as 

$$
    S_{xy} = \langle x-\bar{x}, y-\bar{y}\rangle.
$$
````