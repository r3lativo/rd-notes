---
Date: 2024-05-30
Reviewed: true
---
- [[#T-test vs Z-test]]
    - [[#Sample problem]]
- [[#Sampling Distribution of T values]]
    - [[#Understanding Degrees of Freedom (@import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')dfdfdf﻿)]]
    - [[#T distribution]]
    - [[#Typical Scenarios of Use for a 1-Sample T-Test]]
    - [[#P-Values for Two-Tailed Test]]

---

## T-test vs Z-test

Up until now we looked at the Z-test, that can **only be used when both the mean** $\mu$ **and the standard deviation** $\sigma$ of the null-hypothesis population **are known**.

The T-test, instead, is used when the mean $\mu$ of the null-hypothesis population is **not known** (but can be specified) and the standard deviation $\sigma$ is **unknown.** It can be applied to evaluate differences between one sample and expectations (as Z-test); and can also be used to compare two independent samples.

> [!important] The main difference is that
> 
> **we use T-test when population’s Standard Deviation (**$\sigma$**) is not known.**

The Z-test uses $\sigma$, the SD of the null-hypothesis population, to compute the **Standard Error of the Mean**: the actual SD of the sample taken is not used!

In contrast, the T-Test does make use of the SD of the sample ($s$) to estimate the Standard Error of the Mean.

![[t-test.png]]

The formula to estimate the **Standard Error of the Mean (SEM) for T-test** is:

$$s_{\overline{x}} = \frac{s}{\sqrt{n}}$$

Where $s$ is the SD of the sample that estimates $\sigma$ the SD of the population; and $s_{\overline{x}}$ is the Sample Standard Error of the Mean and estimates $\sigma_{\overline{x}}$ the Standard Error of the Mean from null-population.

> [!important] $s$
> 
> and $s_{\overline{x}}$ are **estimates** of the population that we derive from our sample.

Let’s compare the Z-test and the T-test side by side:

$$z_{obt} =  
\frac{\overline{X}_{obt}-\mu} {\red{\sigma / \sqrt{n}}}$$

$$t_{obt} =  
\frac{\overline{X}_{obt}-\mu} {\red{s / \sqrt{n}}}$$

Why do we care? Not knowing the population standard deviation really is the most common situation: after all, we’re trying to make an inference about the population so it’s unlikely that we know that much about it.

If we don’t know the population standard deviation **it might make sense to use the standard deviation of our sample instead**. After all, the sample standard deviation $s$ is an unbiased estimate of the population standard deviation $\sigma$.

### Sample problem

> Assume you are told that the mean IQ of university students is 110. You have no knowledge of the $\sigma$ of IQ in the (null-hypothesis) population. You suspect that the IQ of this year’s applicants might differ from usual, and you obtain IQ scores from a random sample of those ($n=40$) and find their mean IQ $\mu = 115$ and the standard deviation of the sample $s = 10$.
> 
> - H0: The random sample of $n=40$ is a random sample from a population with $\mu = 110$ → This year applicants have the same IQ as the university mean.
> - H1: The random sample of $n=40$ is **not** a random sample from a population with $\mu = 110$ → This year applicants have a different IQ as the university mean.
> 
> $$t_{obt} =  
> \frac{\overline{X}_{obt}-\mu} {s / \sqrt{n}} =  
> \frac{115 - 110} {10 / \sqrt{40}} = 3.16$$

Nice! We were able to obtain t by comparing our sample with a population (university students) by using the mean on the population and the mean and SD of our sample, plus its size.

> [!important] But,
> 
> **against which critical value do we evaluate** $t_{obt}$**?**

For Z-tests: a single reference sampling distribution that determines critical values for all Z-tests, independent of sample size.

For T-tests: there are different sampling distributions that determine the critical value of each test. These depend on your sample size.

## Sampling Distribution of T values

> [!important] The sampling distribution of the T value is a probability distribution that shows how T values would vary if we drew all possible samples of a fixed size
> 
> $n$ from the null-hypothesis population.

This distribution provides:

1. All possible different T values for samples of size $n$.
2. The probability of each T value.

**The distribution of ‘t’ scores has a known shape**: it’s much like a normal distribution but it has **longer tails**. It also varies with sample size. As the sample size increases, the estimate of the population standard deviation gets more accurate (like a Central Limit Theorem for standard deviations). This makes the t-distribution look more like the z-distribution with larger sample sizes.

The shape of this distribution is influenced by the ==**degrees of freedom**==, which are typically related to the sample size in the context of the T-test.

### Understanding Degrees of Freedom ($df$)

**Degrees of Freedom (**$df$**)** refer to the number of values in a calculation that are free to vary. The concept is crucial for determining the appropriate distribution to use in hypothesis testing and other statistical procedures.

1. **Mean of 10 numbers**:
    - To calculate the mean of 10 numbers, you need all 10 values.
    - Degrees of freedom: $df = 10$.
2. **Discrete probability values in a Binomial distribution**:
    - For a binomial distribution with 10 trials (successes range from 0 to 10), knowing the probabilities for 0 to 9 successes determines the probability of 10 successes because the total probability must sum to 1.
        
        > [!important] Remember that if successes range from 0 to 10, there are
        > 
        > **11 discrete probability values**: the number of successes can be 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 = 11 total.
        
    - Degrees of freedom: $df = 10$.
3. **Sum of squared differences from the mean**:
    - For 10 values $X_1, X_2, \ldots, X_{10}$, the sum of the deviations from the mean is always zero by definition ($\sum (X - \bar{X}) = 0$).
    - Once you have the deviations for 9 values, the 10th deviation is determined.
    - Degrees of freedom: $df = 9$.

In general, degrees of freedom reflect the number of independent pieces of information that are available to estimate another statistic. For example, when calculating a sample variance, $df$ is $n-1$ because one degree of freedom is lost due to using the sample mean in the calculation. It’s buried ==here== and ==here:==

$$t_{obt} =  
\frac{\overline{X}_{obt}-\mu} {\red s / \sqrt{n}}$$

$$\red s = \sqrt {  
\frac  
{\Sigma(\blue{X-\overline{X}})^2}  
{n-1}  
}$$

### T distribution

The t distribution is **symmetrical about zero**, and **becomes closer to normally distributed Z distribution with increasing** $df$**.** Here are some example t-distributions:

![[Untitled 28.png|Untitled 28.png]]

You can see how the t-distribution starts out with fat tails for 4 degrees of freedom ($df=4$) and tightens up with increasing $df$. By $df = 32$ the t-distribution is nearly identical to the z-distribution.

> [!important] This tells us that
> 
> **the obtained t value** $t_{obt}$ **is evaluated against critical values matched for** $df$**.** We can do this with a t-table or with dedicated software (like R or SciPy).

![[Untitled 1 17.png|Untitled 1 17.png]]

T-table

> Let’s go back to our sample problem. We stopped at:
> 
> $$t_{obt} =  
> \frac{\overline{X}_{obt}-\mu} {s / \sqrt{n}} =  
> \frac{115 - 110} {10 / \sqrt{40}} = 3.16$$
> 
> We set our $\alpha = 0.05$, and ours is a two-tailed probability (the IQ of the new applicants can be different from the university mean both being above or below it).
> 
> Looking at the t-table above, we derive that the critical target for our obtained t for $df = n-1 = 39$ is not there. Using $df = 30$ we set $t_{crit}=2.042$ which can in the end reject our null hypothesis, and lead us to think that these new applicants really have a higher IQ from the university mean.
> 
> We can also use python to calculate it:
> 
> ```Python
> import scipy.stats as stats
> 
> # Given values
> alpha = 0.05
> df = 39
> 
> # Calculate the critical t-value for a two-tailed test
> t_crit = stats.t.ppf(1 - alpha/2, df)
> print("Critical t-value (t_crit):", t_crit)
> ```
> 
> This will output `Critical t-value (t_crit): 2.022690911734728` .

### Typical Scenarios of Use for a 1-Sample T-Test

A 1-sample T-test is used to determine if the mean of a single sample is significantly different from a known or hypothesized population mean. Here are two common scenarios:

1. **Comparing Raw Values in a Distribution Against a Single Target Value**:
    - **Objective**: To check if the sample mean is significantly different from a given reference value.
    - **Given**: Sample observations.
    - **Derived**: Sample mean, standard deviation (SD), and sample size (N).
    - **Example**: You have a sample of students' test scores and want to compare the average score against a passing score of 70.
2. **Repeated Measures Context**:
    - **Objective**: To evaluate the difference score between two conditions.
    - **Given**: Paired sample observations from two different conditions.
    - **Derived**: Difference scores for each pair, mean difference (Delta), standard deviation of differences, and number of pairs.
    - **Example**: You measure the same group of participants before and after an intervention to see if there is a significant change in their performance.

In the first scenario, you directly compare the sample mean to a known value. In the second scenario, you calculate the differences between paired observations and then compare the mean of these differences to zero, effectively treating the differences as a single sample. This second approach is also known as a **T-test for paired samples**.

> Let's go through an example of a 1-sample T-test in Python using `scipy.stats`.
> 
> **Scenario 1: Comparing Raw Values Against a Single Target Value**
> 
> Assume we have the following sample data: `[72, 65, 78, 70, 69, 75, 67]` and we want to compare it against a target value of 70.
> 
> ```Python
> import scipy.stats as stats
> import numpy as np
> 
> # Sample data
> sample_data = np.array([72, 65, 78, 70, 69, 75, 67])
> target_value = 70
> 
> # Perform 1-sample t-test
> t_statistic, p_value = stats.ttest_1samp(sample_data, target_value)
> 
> print("T-statistic:", t_statistic)
> print("P-value:", p_value)
> ```
> 
> **Scenario 2: Repeated Measures Context**
> 
> Assume we have paired data representing pre-intervention and post-intervention scores:
> 
> - Pre-intervention scores: `[68, 70, 65, 72, 66, 74, 68]`
> - Post-intervention scores: `[72, 75, 70, 76, 70, 78, 74]`
> 
> We want to see if there is a significant difference between the pre and post scores.
> 
> ```Python
> import scipy.stats as stats
> import numpy as np
> 
> # Paired data
> pre_scores = np.array([68, 70, 65, 72, 66, 74, 68])
> post_scores = np.array([72, 75, 70, 76, 70, 78, 74])
> 
> # Calculate the differences
> differences = post_scores - pre_scores
> 
> # Perform 1-sample t-test on the differences
> t_statistic, p_value = stats.ttest_1samp(differences, 0)
> 
> print("T-statistic:", t_statistic)
> print("P-value:", p_value)
> ```

In both scenarios, the T-statistic and p-value will help us determine whether to reject the null hypothesis, which states that there is no significant difference. If the p-value is less than the significance level (typically 0.05), we reject the null hypothesis.

### P-Values for Two-Tailed Test

When conducting a two-tailed test, we are interested in whether our sample mean is significantly different from a known population mean in either direction (higher or lower). This involves evaluating both the upper and lower tails of the sampling distribution.

Procedure:

1. **Calculate the Test Statistic**: Typically, this is a t-score or z-score.
2. **Find the P-Value for the Test Statistic**: This p-value is for one tail.
3. **Double the One-Tailed P-Value**: Because we are interested in departures in both directions (either higher or lower), the two-tailed p-value is twice the one-tailed p-value.