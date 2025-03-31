---
Date: 2024-05-30
Reviewed: true
---
- [[#Effect Sizes]]
    - [[#Interpreting the effect size]]
- [[#Confidence Intervals]]
    - [[#Understanding the formula]]
    - [[#Confidence Interval for Z Test]]
    - [[#Confidence Interval for Binomial Distribution]]
    - [[#Summary]]
    - [[#Sample Problem I]]

---

## Effect Sizes

Remember, ‘**statistical significance**’, which is the **p-value**, is the probability that you would obtain your observation given that H0 is true. But even though the word ‘significant’ sounds like ‘important’, **a statistically significant result may not be that interesting.**

So, besides knowing whether a given set of values differs from another (or form zero), we want to obtain **a measure for the magnitude of the difference in a meaningful conceptual unit**. This is called the **Effect Size**.

We’ll go back to IQ’s again so that we can use the simple z-test, but the idea holds for any hypothesis test.

> Suppose you want to test the hypothesis that the IQ’s of college students is different from 100. You go and sample the entire population at your university, which had an enrollment of 36206 students and find that the mean IQ is 100.25. With our sample size, the standard error of the mean is $\frac{\sigma}{\sqrt n} = \frac{15}{√36206} = 0.0788$**.**
> 
> Our z-score is therefore:
> 
> $$z_{obt} = \frac{\overline{x} - \mu}{\sigma_{\overline{x}}} =  
> \frac{100-100.25}{0.0788} =  
> 3.1713$$
> 
> Let’s calculate the p-value for a two-tailed test:
> 
> ```Python
> import scipy.stats, numpy
> 
> n = 36206
> mu = 100
> sigma = 15
> x = 100.25
> sem = sigma/numpy.sqrt(n)
> z = (x - mu) / sem  # As above in LaTeX
> 
> # Our p will be splitten in two since it's a two-tailed test
> p =  2*(1 - scipy.stats.norm.cdf(z,0,1))
> print(f"Our p-value for a two-tailed test is {p}")
> ```
> 
> `Our p-value for a two-tailed test is: 0.001517583`
> 
> We conclude that our mean of 100.25 is significantly different from 100 and that IQ’s of college students is significantly different from the general population.

…but how excited can you be about a 0.25 of an IQ point difference? I don’t think it’s something you’d run out and tell your friends and send the result to Nature or something.

> [!important] Our results are statistically significant because our sample size is so large! Technically this is only true if H0 is false, but it doesn’t have to be
> 
> _very_ false. **The problem with p-values is that they don’t reflect the real size of the effect.**
> 
> > "Give me a sample size large enough and I can reject any H0”  
> > - _…not Archimedes_

We need something sort of in between the p-value and the difference between means. This is the _effect size_. It’s defined as ‘Cohen’s $d$’ and it reflects the difference from a reference value in interpretable units.

> [!important] Cohen’s
> 
> $d$ is the difference in the means in standard deviation units.

Its conceptual representation is:

$$d =  
\frac  
{\text{| absolute mean difference |}}  
{\text{population standard deviation}} =  
\frac{| {\overline{x}} - \mu |}{\sigma}$$

> [!important] The
> 
> **direction of the difference is irrelevant to effect size**: understandable also by the absolutes (|) around the “mean difference”.

For unknown standard deviation $\sigma$, we use $s$ and our Cohen $d$ will become $\hat{d}$:

$$\hat{d} = \frac{|\overline{x} - \mu|}{s}$$

> For IQ’s, a mean IQ of 115 would have an effect size of d=1, since 115 is one standard deviation above the mean. For our example:
> 
> $$\hat{d} =  
> \frac{|\overline{x} - \mu|}{\sigma} =  
> \frac{|100 - 100.25|}{15} =  
> 0.0167$$
> 
> > [!important] Our difference in means is very small compared to the standard deviation of the population.

### Interpreting the effect size

Cohen suggested in the 1988 some values to interpret the effect size:

|Cohen’s $d$|Effect size|
|---|---|
|0.2|small|
|0.5|medium|
|0.8|large|

These values are a rough guide.

> [!important] Statistically significant effects might be associated with trivial effect sizes.

There are two main advantages effect size:

1. It **doesn’t depend on the sample size** (although it does get more reliable with increasing sample size)
2. It’s **in standardized units**. This means that effect sizes can be compared across experiments that have different units and sample sizes.

## Confidence Intervals

Lets say we find a substantial effect size. There is a difference between your sample and the hypothesized value, suggesting it reflects a different population - that is, it does not reflect the null-hypothesis population.

But what then can we say about **the mean of the population that our sample reflects?**

> [!important] Using the sample mean
> 
> $\mu_{\overline{x}}$ and sample standard deviation $\sigma_{\overline{x}}$ it **is possible to make a probabilistic statement of the mean of the population from which our sample is drawn**. This statement is made using a ==Confidence Interval==.

While **the sample mean is a** _**point estimate**_ of the population mean (and thus uses one value for estimation), **the Confidence Interval is an** _**interval estimate**_: it provides a _range_ of values for which one is reasonably confident that the range includes the population mean.

- **Point Estimate**: The sample mean is a single value estimate of the population mean.
- **Interval Estimate**: The Confidence Interval provides a range of values that likely includes the population mean.

We usually construct a **95% Confidence Interval**, such that the probability that the interval contains the population value is 0.95.

The confidence interval can therefore be defines as:

$$\overline{x}_{\text{obt}} - s_{\overline{x}} \times t_{0.025}  
\leq  
\mu  
\leq  
\overline{x}_{\text{obt}} + s_{\overline{x}} \times t_{0.025}$$

Where:

- $\overline{x}_{\text{obt}}$ is the Sample mean
- $s_{\overline{x}}$ is the Standard Error of the Mean ($s / \sqrt{n}$ )
- $t_{0.025}$ is the T value corresponding to upper or lower critical values

> [!important] Or more generally:
> 
> $$CI = \overline{x} \pm s_{\overline{x}} \times t_{\alpha/2}$$

### Understanding the formula

What does it mean, really?

In 95% of the cases, the obtained t will be between the 2.5% and 97.5% cumulative probability values. $t_{\text{obt}} = \frac {\overline{x}_{\text{obt}} - \mu} {s_{\overline{x}}}$

$$P (  
\overline{x}_{\text{obt}} - s_{\overline{x}} \times t_{0.025}  
\leq  
\mu  
\leq  
\overline{x}_{\text{obt}} + s_{\overline{x}} \times t_{0.025}  
)  
= 0.95$$

In what sense are we saying there’s 95% that the CI contains the mean? Our confidence is 0.95 that the interval we now calculated for this data set  
contains the population mean.  

> [!important] We deduce that a
> 
> **more narrow interval will imply a better estimator of the population mean**. The larger the sample, the more narrow the interval.

A nice thing about confidence intervals compared to p-values and t-statistics is that **they are in the units of our measurement**. And, for this reason, they give us our critical value for rejecting H0 in our measured units.

> Example in python:
> 
> ```Python
> import scipy.stats as stats
> import numpy as np
> 
> # Sample data
> sample_mean = 115
> sample_size = 40
> sample_sd = 3.16
> 
> # Standard Error of the Mean
> sem = sample_sd / np.sqrt(sample_size)
> 
> # Degrees of freedom
> df = sample_size - 1
> 
> # T value for 95% confidence (two-tailed)
> t_value = stats.t.ppf(1 - 0.025, df)
> 
> # Margin of error
> margin_of_error = sem * t_value
> 
> # Confidence Interval
> ci_lower = sample_mean - margin_of_error
> ci_upper = sample_mean + margin_of_error
> 
> print(f"95% Confidence Interval: ({ci_lower:.2f}, {ci_upper:.2f})")
> ```
> 
> Outputs `95% Confidence Interval: (113.99, 116.01)`
> 
> This code calculates the 95% confidence interval for a sample mean of 115, with a sample size of 40, and a sample standard deviation of 3.16. The result will provide the range within which we are 95% confident that the population mean lies.

### Confidence Interval for Z Test

For a standard normal (Z) distribution, a 95% confidence interval can be calculated as follows:

$$P\left(\overline{X} - 1.96 \times s_{\overline{X}} \leq \mu \leq \overline{X} + 1.96 \times s_{\overline{X}}\right) = 0.95$$

In this case:

- $\overline{X}$ is the sample mean.
- $s_{\overline{X}}$ is the standard error of the mean, calculated as $\frac{\sigma}{\sqrt{n}}$, where $\sigma$ is the population standard deviation and $n$ is the sample size.
- 1.96 is the critical value $z_{crit}$ for a 95% confidence interval in a standard normal distribution.

### Confidence Interval for Binomial Distribution

For binomial distributions, we can use the normal approximation to calculate a confidence interval for a binomial proportion. This approximation is valid when the sample size is large enough, specifically when both $np$ and $n(1-p)$ are greater than 5.

The formula for the binomial proportion confidence interval is:

$$\hat{p} \pm z_{\red{\alpha/2}} \times \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$$

Where:

- $\hat{p}$ is the sample proportion ($\hat{p} = \frac{x}{n}$, where $x$ is the number of successes and $n$ is the sample size).
- $z$ is the critical value $z_{crit}$ from the standard normal distribution for the desired confidence level (1.96 for a 95% confidence interval).
- $_{\red{\alpha/2}}$ is the alpha level’s z-score for a two tailed test.
- $n$ is the sample size.

> Here is an example of how to calculate a 95% confidence interval for both a Z test and a binomial proportion using Python.
> 
> ```Python
> import scipy.stats as stats
> import numpy as np
> 
> # Z test example
> sample_mean = 110
> population_sd = 15
> sample_size = 40
> 
> # Standard error of the mean
> sem = population_sd / np.sqrt(sample_size)
> 
> # 95% Confidence interval for Z test
> z_critical = 1.96
> ci_lower_z = sample_mean - z_critical * sem
> ci_upper_z = sample_mean + z_critical * sem
> 
> print(f"95% Confidence Interval for Z test: ({ci_lower_z:.2f}, {ci_upper_z:.2f})")
> 
> # Binomial proportion example
> num_successes = 60
> total_trials = 100
> sample_proportion = num_successes / total_trials
> 
> # Standard error for the proportion
> se_proportion = np.sqrt(sample_proportion * (1 - sample_proportion) / total_trials)
> 
> # 95% Confidence interval for binomial proportion
> ci_lower_binomial = sample_proportion - z_critical * se_proportion
> ci_upper_binomial = sample_proportion + z_critical * se_proportion
> 
> print(f"95% Confidence Interval for Binomial proportion: ({ci_lower_binomial:.4f}, {ci_upper_binomial:.4f})")
> ```
> 
> Output: `95% Confidence Interval for Z test: (105.35, 114.65)` and `95% Confidence Interval for Binomial proportion: (0.5040, 0.6960)`

### Summary

We now have four ways of telling people about the size of our results. First, there’s simply the difference between our observed mean and null hypothesis mean. Then there is the p-value, the confidence interval, and the effects size. Each has their own advantages and disadvantages. The following table summarizes the attributes of each:

||Statistical significance|Real units|Compare across experiments|Requires H0|Decision about H0|
|---|---|---|---|---|---|
|**Difference of Means**|No|Yes|No|Yes|No|
|**p-value**|Yes|No|No|Yes|Yes|
|**Confidence Interval**|Yes (sort of)|Yes|No|No|Yes|
|**Effect Size**|No|No|Yes|Yes|No|

### Sample Problem I

An ethologist is interested in determining the average weight of adult Olympic marmots (found only on the Olympic Peninsula in Washington). It would be expensive and impractical to trap and measure the whole population, so a random sample of 15 adults is trapped and weighed. The sample has a mean of 7.2 kilograms and a standard deviation of 0.48. **Construct the 95% confidence interval for the population mean.**

We know that:

$$n = 15, \quad \mu_{\overline{x}} = 7.2, \quad \sigma_{\overline{x}} = 0.48, \quad df = n-1=14$$

Looking at the t-table (or computing it with a software) we know that the $t_{crit}$ for a sample of size 14 with alpha set to 0.05 for a two-tailed test is 2.145.

$$t_{crit} \approx 2.145$$

We can also derive the Standard Error of the Mean $s_{\overline{x}}$ with our formula:

$$s_{\overline{x}} = \frac{\sigma}{\sqrt{n}} = \frac{0.48}{\sqrt{15}} \approx 0.124$$

Knowing this we can apply our formula and construct the 95% confidence interval:

$$P (  
\mu_{\overline{x}} - s_{\overline{x}} \times t_{0.025}  
\leq  
\mu  
\leq  
\mu_{\overline{x}} + s_{\overline{x}} \times t_{0.025}  
)  
= 0.95\\  
P (  
7.2 - 0.124 \times 2.145  
\leq  
\mu  
\leq  
7.2 + 0.124 \times 2.145  
)  
= 0.95\\  
P (  
6.934  
\leq  
\mu  
\leq  
7.466  
)  
= 0.95$$

We are 95% sure that the mean of the population is between 6.934 and 7.466. Our margin of error is 0.532