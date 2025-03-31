---
Date: 2024-04-16
Reviewed: true
week_lec: 8
---
- [[#Two-Sample Independent Measures t-test]]
    - [[#Hypotheses]]
    - [[#Sampling distribution of sample differences]]
    - [[#Characteristics of sampling distribution of differences between sample-means]]
    - [[#Estimating the population variance for difference between means]]
    - [[#Obtaining and testing T-crit for independent samples]]
    - [[#Sample Problem]]
    - [[#Assumptions Underlying the T-Test for Independent Groups]]
    - [[#Effect size and confidence interval]]
    - [[#Sample problem]]
- [[#Two-Sample Dependent (Pai) Measures t-test]]
    - [[#Formula]]
    - [[#Example]]
- [[#Comparison: Independent vs Dependent t-test]]
    - [[#Practical Example]]
    - [[#Sensitivity of Dependent (Pai) Designs]]

---

## Two-Sample Independent Measures t-test

> [!important] This t-test compares two means that are drawn from separate, or independent samples.

The two-sample t-test is a bit more complex, and the logic goes:

1. Participants are randomly assigned to conditions (only **two group of participants**)
2. Means $\mu$ and SDs $\sigma$ are computed separately for each group
3. We then compare these values: is the difference consistent with what would be expected from chance alone? - is it the case that this two set of participant can be said to belong to the same set of population?

![[two_sample_t-test.png]]

> [!important] If the results are not consistent, we will say that the two group belong to two different populations (rejecting H0).

### Hypotheses

The null hypothesis (H0) posits that the means of the two groups are equal, suggesting they come from populations with the same mean (or differ by a specified amount):

$$H0: (\mu_1 - \mu_2) - \mu_{hyp} = 0$$

Where $\mu_1$ and $\mu_2$ are the means of the two populations from which the samples are drawn. The two-sample t-test estimates the probability of obtaining the observed mean difference (or some expected difference $\mu_{hyp}$) if H0 is true.

> [!important] Here
> 
> $_1$ and $_2$ stand for the population with the respective associated condition, and this apply to every other term like $\mu$, $\sigma$, etc.

**Bidirectional Hypothesis Testing**

We test if the means of the two samples are equal or not:

- H0: The two samples reflect the same population and so $\mu_1 = \mu_2$
- H1: The two samples reflect different populations, and $\mu_1 \ne \mu_2$

**Directional Hypothesis Testing**

We specify the direction of the difference between the means:

1. H1 $\mu_1 > \mu_2$; H0: $\mu_1 \leq \mu_2$
2. H1: $\mu_1 < \mu_2$; H0: $\mu_1 \geq \mu_2$

### Sampling distribution of sample differences

_What is the expected distance from two sample that belong to the same population?_

For the **single** sample tests, we focused on the mean of the sampling distribution of the mean and the sd. of the sampling error of the mean (Std. Err. Mean).

> [!important] For independent samples, we are interested in the
> 
> **sampling distribution of differences between means**, $\overline{x}_1 - \overline{x}_2$

==**Sampling distribution of the difference between sample means**==: If we  
simulate sampling $n_1$ and $n_2$ repeatedly from the sample population and calculated $\overline{x}_1$ and $\overline{x}_2$ this would produce **a distribution containing all the possible difference scores that could be obtained for these sample sizes**.

> [!important] This distribution of difference between the means is related to the samples sizes. The larger the sample sizes, the narrower the distribution, indicating more precise estimates of the mean difference.

### Characteristics of sampling distribution of differences between sample-means

The sampling distribution of the difference between means can be thought of as the distribution that would result if we repeated the following three steps over and over again:

1. sample $n_1$ scores from Population 1 and $n_2$ scores from Population 2
2. compute the means of the two samples ($\overline{x}_1$ and $\overline{x}_2$)
3. compute the difference between means, $\overline{x}_1 - \overline{x}_2$. The distribution of the differences between means is the sampling distribution of the difference between means.

As you might expect, the mean of the sampling distribution of the difference between means is:

$$\mu_{\overline{x}_1 - \overline{x}_2} = \mu_1 - \mu_2$$

Read in plain English as: the sampling distribution of the difference between means is equal to the difference between the mean of the Population 1 and the mean of the population 2.

> [!important] The sampling distribution of the difference between sample means is normal if the populations from which the samples are taken are normal.

The standard deviation of the sampling distribution of the differences between the means is calculated by:

$$\sigma_{\overline{x}_1 - \overline{x}_2} =  
\sqrt{  
\sigma^2 (  
\frac{1}{n_1}  
+  
\frac{1}{n_2}  
)  
}$$

Where $\sigma^2 = \sigma^2_1 = \sigma^2_2$ which is the variance of each population.

> [!important] For the standard two-sample independent measures t-test, both the null and alternative hypotheses assume that **the two population standard deviations are the same** (even if we don’t know what that standard deviation is).

If the population variance $\sigma_2^2$ was known we could derive a Z value for the difference using the standard logic:

$$z_\text{obt} = {{\red{(\overline{x}_1 - \overline{x}_2)} - \blue0} \over{\orange{\sqrt{\sigma^2 ({1\over{n_1}} + {1\over{n_2}})}}}}$$

The ==difference between the two samples== and ==the difference expected according to the null hypothesis (0)== is expressed in ==units of the relevant standard deviation==.

### Estimating the population variance for difference between means

> [!important] But,
> 
> **we don’t know the population variance**: we instead estimate it using a estimator $s_{\overline{x}_1 - \overline{x}_2}$ and conduct a T-test rather than a Z-test.

We need to estimate ==this parameter==:

$$z_\text{obt} = \frac{{(\overline{x}_1 - \overline{x}_2) - 0}} {\sqrt{\red{\sigma^2} ({1\over{n_1}} + {1\over{n_2}})}}$$

We do so by taking the variances of each sample $s^2_1$ and $s^2_2$ and deriving a **weighted mean**: the weights are the degree of freedom (_$df$)_ of each sample. This weighted or ==**pooled-variance-estimate**== is ultimately expressed as:

$$s_p^2 = {{SS_1 + SS_2} \over{(n_1 - 1) + (n_2 - 1)}}$$

Where:

- $SS_{1,2}$ are the **sum of squared deviations** of each samples scores from the mean of the sample.
- $(n_1 - 1) + (n_2 - 1)$ are the degrees of freedom for the independent sample test. In the end we lose two degree of freedom.

The ==**pooled-variance-estimate**== ==(==$s_{\text{pooled}}$ or $s_p$) is a sort of complicated average of the two standard deviations. Technically, the calculation inside the square root is an average of the sample variances, weighted by their degrees of freedom. Importantly, $s_p$ should always fall somewhere between the two sample standard deviations.

The denominator of the t-test, called the ==**pooled standard error**== $\blue{s_{\overline{x}_1 - \overline{x}_2}}$, is calculated from $s_p$ by:

$$\blue{s_{\overline{x}_1 - \overline{x}_2}} = s_p \sqrt{({1\over{n_1}} + {1\over{n_2}})}$$

### Obtaining and testing T-crit for independent samples

We said we don’t have access to the real standard deviation $\sigma$ of the population, and because of this we use an estimation of the SD from our samples. Substituting $\red{\sigma^2}$ in the previous formula will give us:

$$t_{obt} =  
\frac  
{\overline{x}_1 - \overline{x}_2}  
{\sqrt{({{SS_1 + SS_2} \over{(n_1 - 1) + (n_2 - 1)}})({1\over{n_1}} + {1\over{n_2}})}}$$

Which can also be rewritten more succinctly as:

$$t_{obt} =  
\frac  
{\overline{x}_1 - \overline{x}_2}  
{s_{\overline{x}_1 - \overline{x}_2}}$$

In the case where the null hypothesis ==**assumes a specific difference**== rather than 0, we put it in:

$$t_{obt} =  
\frac  
{(\overline{x}_1 - \overline{x}_2) - \green{\mu_{\overline{x}_1 - \overline{x}_2}}}  
{\sqrt{({{SS_1 + SS_2} \over{(n_1 - 1) + (n_2 - 1)}})({1\over{n_1}} + {1\over{n_2}})}}$$

> [!important] Note:
> 
> **if the two sample sizes are the same** ($s_{x_1} = s_{x_2} = n$), then the pooled standard error of the mean simplifies to:
> 
> $$s_{\overline{x}_1 - \overline{x}_2} = \sqrt{\frac  
> {SS_1 + SS_2}  
> {n}  
> }$$

### Sample Problem

A physiologist has conducted an experiment to evaluate the effect of hormone X on appetite behavior. Ten rats were injected with hormone X, and 10 other rats received a placebo injection. The number of pellets eaten were counted over a 20-minute period.

- H0 would be that the mean of the two groups are the same (placebo group is in this case the H0 population). $\mu_1 = \mu_2$
- H1 instead that hormone group’s mean varies enough as to reject H0. $\mu_1 \ne \mu_2$

```Python
import scipy.stats as stats
import numpy as np

hormone_group = [8, 10, 12, 6, 6, 7, 9, 8, 7, 11]
placebo_group = [5, 6, 3, 4, 7, 8, 6, 5, 4, 8]
t_obt = stats.ttest_ind(hormone_group, placebo_group)

hormone_mean = np.mean(hormone_group)  # 8.4
placebo_mean = np.mean(placebo_group)  # 5.6

print(t_obt)

# Output:
TtestResult(
		statistic=3.2998316455372225,
		pvalue=0.003982786775146326,
		df=18.0)
```

Our p-value is less than $α=0.05$. We therefore reject H0 and conclude that the mean count of eaten pellets is actually significantly greater in the hormone group, leading us to state that t**he hormone X has significant impact on appetite behavior**.

### Assumptions Underlying the T-Test for Independent Groups

1. **Normality of the Sampling Distribution**: The populations from which the samples are drawn should be normally distributed. However, this assumption can be relaxed if each sample size is at least 30, as the Central Limit Theorem ensures the sampling distribution of the mean will be approximately normal for large sample sizes.
2. **Homogeneity of Variance**: The independent variable (IV) is expected to affect the means but not the variances. In other words, **the variances of the two populations should be similar**. If the sample variances are significantly different, the t-test can still be performed, but special corrections (like Welch's correction) may be needed to adjust for this discrepancy.

### Effect size and confidence interval

The effect size for an independent measures t-test is Cohen’s d again. This time it’s measured as:

$$\hat{d} = \frac  
{\blue{|\overline{x}_1 - \overline{x}_2|}}  
{\orange{\sqrt{s^2_p}}}  
\qquad \text{where: }  
\orange{{s^2_p}} = {{SS_1 + SS_2} \over{(n_1 - 1) + (n_2 - 1)}}$$

> So in plain terms, our estimated Cohen’s is the ==absolute difference between the mean of our samples== divided by the ==root of the pooled-variance-estimate==.

Our interest is in the **confidence interval** that estimates the value of the difference between $\mu_1$ and $\mu_2$, which we calculate via the samples $\overline{x}_1$ and $\overline{x}_2$. We define the interval using:

$$\mu_{\text{lower/upper}} = (\overline{x}_1 - \overline{x}_2) \pm \green{s_{\overline{x}_1 - \overline{x}_2}} \times t_{\alpha/2}$$

> In plain English, the confidence interval is the difference between the mean of our samples plus/minus the ==estimated variance difference of our samples== (pooled standard error) times the $t$ value for a two-tailed test.

> [!important] Compare this to the CI for
> 
> $\mu$ which was
> 
> $$CI = \overline{x} \pm s_{\overline{x}} \times t_{\alpha/2}  
> \qquad \text{where: }  
> s_{\overline{x}} = s / \sqrt{n}.$$

### Sample problem

Going back to our rats experiment, with the hormone and the placebo groups, we can now define the effect size and confidence interval of our experiment:

$$\hat{d} = \frac  
{\blue{|\overline{x}_1 - \overline{x}_2|}}  
{\orange{\sqrt{s^2_p}}}  
=  
\frac{|8.4-5.6|}{\sqrt{3.6}}  
\approx 1.476$$

$$\mu_{\text{lower/upper}} = (\overline{x}_1 - \overline{x}_2) \pm {s_{\overline{x}_1 - \overline{x}_2}} \times t_{\alpha/2} = \\  
8.4-5.6 \pm 0.848 \times 2.1 = 1.019 \lrarr 4.580$$

Which, in plain English, tells us that

- the effect size is of 1.476, which is a very high value: approximately 92% of the second group would have a mean differing from the first group.
- our 95% confidence interval is between 1.019 and 4.580, with a margin of error of 1.7808: we are 95% sure that the real mean of the population lies between these values.

## **Two-Sample Dependent (Paired) Measures t-test**

> [!important] This test is used to compare two means for two samples for which we have reason to believe are dependent or correlated.

The most common example is a repeated-measure design where each subject is sampled twice - that’s why this test is sometimes called a ‘repeated measures t-test’.

![[dependent_t-test.png]]

Let’s look at an example to understand what is it about.

> Consider a weight-loss program where each participant lost exactly 9 kilograms. Here are the weights before and after the program for 10 subjects:
> 
> |   |   |   |   |   |   |   |   |   |   |   |
> |---|---|---|---|---|---|---|---|---|---|---|
> |Before (kg)|57|71|53|97|74|53|77|82|78|63|
> |After (kg)|48|62|44|88|65|44|68|73|69|54|
> 
> The mean weight before the program is 70.5 kg, and the mean weight after is 61.5 kg, indicating a significant average weight loss.
> 
> $$n = 10  
> \qquad  
> \mu_{\text{before}} = 70.5  
> \qquad  
> \mu_{\text{after}} = 61.5$$
> 
> However, running an independent measures t-test on these two samples yields a t-score of $t(18) = 1.43$ and a p-value of $p = 0.1691$.

Thus, statistically, we must conclude that the program did not produce a significant change in weight…? **But everyone lost 9 kg**! How could we not conclude that the weight loss program was effective? The problem is that **there is a lot of variability in the weights across subjects.** This variability ends up in the pooled standard deviation for the t-test.

> [!important] But we don’t care about the overall variability of the weights across subjects.
> 
>  _**We only care about the change due to the weight-loss program**_.

Experimental designs like this where we expect a correlation between measures are called ‘dependent measures’ designs.

> [!important] **The trick is to create a third variable,**
> 
> $D$**, which is the pair-wise differences between corresponding scores in the two groups**. You then simply run a t-test on the mean of these differences - usually to test if the mean of the differences, $D$, is different from zero.

> In this case, all the $D$s would be 9, and so would be the mean of them $\overline{D}$.
> 
> |   |   |   |   |   |   |   |   |   |   |   |
> |---|---|---|---|---|---|---|---|---|---|---|
> |Before (kg)|57|71|53|97|74|53|77|82|78|63|
> |After (kg)|48|62|44|88|65|44|68|73|69|54|
> |$D$|9|9|9|9|9|9|9|9|9|9|

### Formula

The formula to calculate t for a dependent measure t-test is:

$$t_{obt} =  
\frac{\overline{D}_{obt}}  
{s_D/\sqrt{N}}  
\quad  
\text{or}  
\quad  
\frac{\overline{D}_{obt}}{\sqrt{\frac{SS_D}{N(N-1)}}}$$

Where:

- $D$ is the difference score ($x_1-x_2$)
- $\overline{D}$ is the mean of the sample difference scores ($\frac{\Sigma D}{N}$)
- $s_D$ is the standard deviation of the sample difference scores ($s=\sqrt{\frac{∑(D−\overline{D})^2}{N−1}​​}$)
    
    > [!important] We use
    > 
    > $n - 1$ instead of $n$ to account for the bias in estimating the population variance and standard deviation from a sample. This correction, known as Bessel's correction, provides a more accurate and unbiased estimate of the population parameters.
    
- $N$ is the number of difference scores
    - Different from $n$, the sample size
- $SS_D = \Sigma(D-{\overline{D}_{obt}})^2$ is the sum of squares of sample difference scores

### Example

[High School vs. College GPAs](https://courses.washington.edu/psy524a/_book/two-sample-dependent-measures-t-test.html#high-school-vs.-college-gpas)

## Comparison: Independent vs Dependent t-test

For Independent samples test, the usual formula is simplified as follows whe**n samples sizer are equal** $n_1 = n_2$:

$$\text{independent } t_{obt} =  
\frac  
{\overline{x}_1 - \overline{x}_2 }  
{\sqrt{{{SS_1 + SS_2} \over{n(n - 1)}}}}$$

Let’s compare the two formulas, for the **independent t-test** and for the **dependent t-test**:

$$\text{dependent } t_{obt} =  
\frac{\overline{D}_{obt}}{\sqrt{\frac{SS_D}{N(N-1)}}}$$

In these formulas:

- $\overline{x}_1$ and $\overline{x}_2$ are the sample means for the two groups.
- $\overline{D}_{obt}$ is the mean of the difference scores for paired data.
- $SS_1$ and $SS_2$ are the sums of squares for the two independent samples.
- $SS_D$ is the sum of squares of the difference scores.
- $n$ is the sample size for each group in the independent test.
- $N$ is the total number of paired observations in the dependent test.

> [!important] Very often it happens that the
> 
> ==**sum of squares of sample difference scores**== is less than the ==**sum of squared deviations**==:
> 
> $$\green{SS_D} < \blue{SS_1 + SS_2}$$

**Why?**

- **Reduced Variability**: In a dependent design, we control for individual differences. Each person serves as their own control, which means we're only looking at the change for each individual, not the total variability between different people.
- **Internal Control**: By comparing each individual to themselves, we eliminate the variability caused by differences between people. This leads to less overall variability in the difference scores.

### Practical Example

Imagine two scenarios:

1. **Independent Groups**: You measure the weight of people in two different diet programs. The total variability includes differences in weight due to individual differences in metabolism, lifestyle, etc.
2. **Dependent Groups**: You measure the weight of the same people before and after a single diet program. The variability now only includes differences in weight change due to the diet, not differences in their initial weights.

> [!important] In the dependent design,
> 
> **the variability due to individual differences** (like metabolism) **is removed**, resulting in a smaller sum of squares $\green{SS_D}$ compared to $\blue{SS_1 + SS_2}$.

### Sensitivity of Dependent (Paired) Designs

Paired designs are often more sensitive than independent designs because they reduce variability by accounting for the same subjects across conditions. This increased sensitivity can lead to a greater ability to detect significant effects.

**Limitations of Repeated Measures Designs**  
  
Despite their sensitivity, repeated-measures (cross-over) designs have certain limitations:

1. **Order Effects**: The sequence in which treatments are administered can affect the results. Subjects might perform differently in the second condition due to fatigue or learning effects from the first condition.
2. **Carryover Effects**: The effect of the first treatment might carry over and influence the results of the second treatment. This can obscure the true effect of the second treatment.
3. **Increased Complexity**: Designing and analyzing repeated measures can be more complex, requiring more advanced statistical techniques to account for the correlation between measurements.

> [!important] While dependent (pai) t-tests can offer greater sensitivity due to uced variance, they also come with challenges such as order effects, carryover effects, and increased complexity in design and analysis.
> 
> **Independent t-tests, although potentially less sensitive, do not suffer from these particular limitations.**
