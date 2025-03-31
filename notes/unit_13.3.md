---
Date: 2024-06-05
Reviewed: true
week_lec: 14
---
- [[#Mathematical Features of Correlation]]
    - [[#Correlation and covariance]]
    - [[#Scaling the covariance]]
    - [[#Correlation is not always informative]]
    - [[#Spearman’s Correlation]]
    - [[#Statistical Significance of Correlation]]
    - [[#Compare a Correlation against a Population]]
        - [[#Fisher’s r to z conversion]]
        - [[#A Confidence Interval on estimating the Correlation of the Population]]
    - [[#Partial Correlations]]
    - [[#Multivariate]]

---

# Mathematical Features of Correlation

### Correlation and covariance

> [!important] **Covariance**
> 
> is a measure of the joint variability of two random variables.

Covariance can be computed as the product of deviation of their values from their mean divided by the sample size minus 1:

$$COV(x,y) = \frac{\sum(x-\mu_x)\times(y-\mu_y)}{n-1}$$

- Covariance naturally obtains **naturally higher positive values when above-mean values in one variable are accompanied by above-mean values in another** (and conversely for below-mean).
    
    > A person with height and IQ above the mean, you got a higher positive value…
    
- Cases of mismatch (above in X but below in Y) will give negative COV

> [!important] Data points in quadrants I and III contribute to increasing the covariance, while data points in quadrants II and IV contribute to decreasing it.
> 
> ![[Untitled 22.png|Untitled 22.png]]

### Scaling the covariance

Covariance just reflects joint departure from means and reflects the original units of the X and Y variables. This means that **unit changes will impact covariance, even if the relationship between variables is the same.**

> [!important] Covariance has no theoretical upper or lower bounds.

To ‘**Standardize’ the covariance**, we divide it by the multiplication of SD(X) and SD(Y). **This correlation is the definition of our** ==**Pearson correlation**== ==$r$==, and can be computed as the ratio between the sample covariance and the product of the standard deviation of x and y.

$$r = \frac{\text{sample}\_{COV}(x,y)}{s_x\times s_y}$$

> [!important] This is the value we get from the sample.
> 
> **It doesn’t really tell us which is the actual relationship in the population**, because the fraction terms might be relatively poor approximations.

If two variables are truly independent in the population, then if we sampled an infinite numbers of datapoints from it the covariance $COV$ will be 0, and hence also the correlation $r$ will be 0.

### Correlation is not always informative

**Anscombe's quartet** comprises four datasets that have **nearly identical simple descriptive statistics** (means, regression and residual), yet have **very different distributions** and appear very different when graphed.

> [!important] Key point:
> 
> plot your data.

![[Untitled 1 11.png|Untitled 1 11.png]]

Anscombe’s Quartet

In set 3 and 4 we see how much outliers can have an impact on our data!

### Spearman’s Correlation

If there is a **worry of outlier values**, we might not want to use a measure of correlation based on distances from means. Instead, we can compute a measure of correlations based on whether the Ranks of the two variables match.

> [!important] Spearman’s correlation doesn’t work on the raw data of X and Y, but
> 
> **works on their ranks.** You are basically asking: do high ranks of X tend to occur with high ranks of Y?

It is said to be a **monotonic relationship:** it can find a strong relationship even if the relationship is non-linear, which is kind of cool. It ranges from -1 to +1, and it is **robust to outliers** (unlike Pearson's correlation).

![[Untitled 2 11.png|Untitled 2 11.png]]

Spearman correlation here says that it is perfect, while Pearson’s says is 0.97

> [!important] Use this spearman correlation when you do not want to speculate.

Spearman’s is more conservative

> [!important] SLIDE 68: There are
> 
> **many other different types of correlations**, but we won’t delve into them

### Statistical Significance of Correlation

Once you compute your correlation you can test whether it is significant.

> [!important] Just know that
> 
> **it is possible** to test the significance of a correlation.

> [!important] NO FORMULA

## Compare a Correlation against a Population

> [!important] In some values the H0 states that the correlation is NOT 0, but is instead SOMETHING ELSE.

How do I know whether my correlation differs from population’s correlation (say 0.5)? We need some rule!

The problem in comparing one correlation with the other is that **the correlation coefficient (**$r$**) estimated from the samples will be biased towards values higher than the mean**.

> [!important] And so, instead of comparing the raw R values,
> 
> **we first need to transform them so that their distribution is normal.**

> In the example below, we can see that the distribution is left-skewed, wrongly indicating that the sample correlations are more likely to be less than 0.8.
> 
> ![[Untitled 3 10.png|Untitled 3 10.png]]
> 
> Also, sample correlations are more likely to underestimate the true correlation when sample sizes are small.

### Fisher’s r to z conversion

The transformation of R values for purposes of comparison is called **Fisher’s R to Z conversion**

Just understand that when we compare…. we have to go through the step of Z-normalizing

> [!important] The fisher’s R to Z conversion
> 
> **actually changes the shape of the distribution**, differently from the simple Z-normalization which doesn’t change the shape of the distribution but just shifts it towards 0.

> [!important] SKIP SLIDE 73

### A Confidence Interval on estimating the Correlation of the Population

What is likely to be the true correlation in the population given our sample correlation? Computable through the **true value of the population estimate** formula.

> [!important] DONT MEMORIZE THE EQUATION

$$Z(T.V.) =Z \pm z(\frac \alpha 2) \sqrt{\frac{1}{N-3}}$$

We see that we have a potentially gross estimation in the sample. Luckily we can produce this confidence interval by taking our z-score… **The true value of the population is going to be into this boundaries (in z values)**.

> [!important] We have to know that we cannot trust our correlation directly.

## Partial Correlations

> [!important] In some cases, it is obvious that a relation between two Variables,
> 
> $x_1$ and $x_2$ is probably due to a third variable.

> For example: Body weight may be correlated with reading ability. This could be interesting, but most (if not all) of this correlation may be due to Age, because Age is related to both variables. Adults weight more than kids!
> 
> If we held Age constant (examining the relation within a given age group) would the relationship of _weight to reading_ still exist?

If we have three variable X Y Z and we do not care about Z, we will create a modified version of them that models the impact of Z: $X_Z$ and $Y_Z$. At this point we compute the correlation between these scores, and it can be extremely different from the one we got at the beginning!

> [!important] To do this mathematically, we **partial out** the impact of a variables from our variables to achieve **corrected scores**: we will then see if these correlate with each other.

Once you remove this third variable we have some cleaned, corrected score (in the case above (weight and reading scores).

> [!important] You need to know the terminology

> [!important] $r_{12.3}$
> 
> is the correlation between variable 1 ($x_1$) and variable 2 ($x_2$) adjusted for the linear association of each og them with variable 3 ($x_3$). This linear association will be assessed by **linear regression**.

Basically, we are going to try to predict $x_1$ from $x_2$ etc. and see how it goes: the regression will capture how well it did, and the residual will tell us what we were not able to predict.

**For simplicity we use z-scored variables**

We predict the normalized version of the first score as usual: $z_1 = r_{12}z_3$

> [!important] Check here for a refresh:

At this point instead of the original values for $x_1$ and $x_2$ we have their ‘remainders’- the distances from predicted $\hat y$ - that is not explained by $x_3$, and we correlate these residuals.

> [!important] **We are interested here in the residuals**
> 
> as they represent what the regression could not predict!

> [!important] SLIDE 77: JUST KNOW THAT there is an actual equation that lets you compute this partial correlations.

For each of our observation, take the residual and subtract it from the true value (for each variable), multiply, and divide everything by N (the number of participants in the sample) times the multiplication of the standard deviations of the respective residuals

> [!important] Useful in
> 
> **experimental NLP**

[https://towardsdatascience.com/4-reasons-why-correlation-does-not-imply-causation-f202f69fe979#:~:text=(1) We’re missing,you think of%3F](https://towardsdatascience.com/4-reasons-why-correlation-does-not-imply-causation-f202f69fe979#:~:text=(1)%20We%E2%80%99re%20missing,you%20think%20of%3F)

## Multivariate

> [!important] NOT IN THE EXAM!

Here we compare tables to tables: you want to predict a lot of features rather than just one.