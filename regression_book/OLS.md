### Ordinary Least Squares (OLS)

Our first estimation of $\beta_0$ and $\beta_1$ will involve drawing a straight line through the data $\mathcal{D}$ that 'comes as close as possible' to all the points. In particular, let $\hat{y}_i = \hat{\beta}_0 + \hat{\beta}_1 x_i$ be a straight line that predicts the value of $Y_i$ based on the observed value $x_i$ of $X_i$. Then $e_i = y_i - \hat{y}_i$ represents the $i$-th *residual*, and we aim to find estimates $\hat{\beta}_0$ and $\hat{\beta}_1$ that minimise the *residual sum of squares* 

````{math}
:label: eq_RSS
    \text{RSS}(a,b) := \sum_{i=1}^n e_i^2 = \sum_{i=1}^n ( y_i - (a + b x_i) )^2,
````
i.e.
````{math}
    (\hat{\beta}_0,\hat{\beta}_1) =  \text{argmin}_{(a,b)\in \mathbb{R}^2} \sum_{i=1}^n ( y_i - (a + b x_i) )^2.
````

If we fix $b$, then the value of $a$ that minimises {eq}`eq_RSS` is 

````{math}
    a = \frac{1}{n}\sum_{i=1}^n (y_i - b x_i) = \bar{y} - b \bar{x}.
````

Substituting this value of $a$ into {eq}`eq_RSS` gives us 
````{math}
    \frac{1}{n}\sum_{i=1}^n (y_i - (  \bar{y} - b \bar{x} + b x_i ))^2 = S_{yy} - 2b S_{xy} + b^2 S_{xx}.
````
Thus, 
````{math}
    \frac{\text{d}}{\text{d}b}  \text{RSS}(\bar{y} - b \bar{x},b) = 0 \Leftrightarrow b = \frac{S_{xy}}{S_{xx}},
````
whence $\frac{S_{xy}}{S_{xx}}$ is a global minimum as $\frac{\text{d}^2}{\text{d}b^2}  \text{RSS}(\bar{y} - b \bar{x},b) > 0$. We may conclude that 
````{math}
    \hat{\beta}_0 = \bar{y} - \frac{S_{xy}}{S_{xx}} \bar{x}   \quad \text{and} \quad\hat{\beta}_1 = \frac{S_{xy}}{S_{xx}}.
````