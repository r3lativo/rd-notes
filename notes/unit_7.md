---
Date: 2024-04-09
Reviewed: true
week_lec: 7.2
---
- [[#Sampling Distributions]]
    - [[#Hypothesis testing and the Sampling Distribution]]
    - [[#Generating a Sampling Distribution]]
    - [[#Obtaining Sampling Distribution for 2-throw problem]]
- [[#The Normal Deviate (Z) test]]
    - [[#The Sampling Distribution of the Mean (SDM)]]
    - [[#The Central Limit Theorem]]
    - [[#Demonstrations]]
    - [[#When is SDM bell-shaped?]]
    - [[#Back to the Example]]
    - [[#Implementing Z Test Using Critical Regions]]
    - [[#Using the Critical Region]]
    - [[#Example of a Z-Test Implementation in Python]]
    - [[#Summary of Z-test]]
- [[#Sample Problems]]

---

## Sampling Distributions

> [!important] The sampling distribution of a statistic is the distribution of that statistic, considered as a random variable, when derived from a random sample of size
> 
> $n$. It may be considered as **the distribution of the statistic for all possible samples from the same population of a given sample size**.

So, the sampling distribution of a statistic consists of:

- All the values that the statistic can take
- The probability of getting each value **under the assumption that sampling was random**

> When we evaluated the probability of obtaining certain numbers of heads _on the assumption that the coin was fair_, we used the Binomial Distribution (with head probability $p=0.5$) as the Sampling Distribution of reference.

### Hypothesis testing and the Sampling Distribution

Hypothesis testing is directly related to the sampling distribution in the following way:

1. **Define and Calculate the Statistic**: Identify and compute the appropriate statistic for your hypothesis.
2. **Evaluate the Statistic**: Using the sampling distribution, determine if the probability of obtaining this statistic (or a more extreme value) is less than your predefined alpha ($\alpha$) level.

> [!important] The specific
> 
> **statistic** and the relevant **sampling distribution** will vary depending on the study, but the fundamental process remains the same. This approach helps in deciding whether to reject the null hypothesis based on the calculated probabilities.

The statistics can be a Z, a T… the important thing is to have a relative distribution in respect to all others results.

### Generating a Sampling Distribution

A sampling distribution can be created in two ways:

1. **A-priori Using Known Distributions**: For well-described distributions, we can use existing formulas to create the sampling distribution. For example, with the Binomial distribution, we can compute the mean analytically.
2. **Empirically by Sampling**: We can also derive a sampling distribution by repeatedly taking samples of size $n$ from the population and calculating the statistic for each sample.

> For instance, if we didn't have a Binomial function and wanted to construct a sampling distribution for the number of heads when throwing two coins, **we would derive this empirically by repeatedly simulating the coin tosses and recording the results**.

> [!important] While using a-priori principles is often possible,
> 
> **empirical generation of sampling distributions is necessary when analytical derivation is not feasible**.

### Obtaining Sampling Distribution for 2-throw problem

Let’s say we do an experiment in which we toss two coins and see how many of them land on heads (so, none of them, only one, or both).

Here's a Python program that simulates the tossing of two coins 1000 times, checks the distribution of how many times none, only one, or both of them land on heads, and then prints the results and plots a histogram.

```Python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Function to simulate the coin toss
def toss_two_coins(n):
    results = []
    for _ in range(n):
        toss1 = np.random.choice([0, 1])  # 0 for tails, 1 for heads
        toss2 = np.random.choice([0, 1])
        results.append(toss1 + toss2)
    return results

# Simulate 1000 tosses
n_tosses = 1000
results = toss_two_coins(n_tosses)

# Count the occurrences of 0, 1, and 2 heads
counts = {
    "None (0 heads)": results.count(0),
    "One (1 head)": results.count(1),
    "Both (2 heads)": results.count(2)
}

# Print the results in a table format
df = pd.DataFrame(list(counts.items()), columns=['Outcome', 'Frequency'])
print(df)

# Plotting the histogram
plt.bar(df['Outcome'], df['Frequency'], color=['red', 'blue', 'green'])
plt.xlabel('Number of Heads')
plt.ylabel('Frequency')
plt.title('Distribution of Heads in 1000 Tosses of Two Coins')
plt.show()
```

![[Distr_of_Hs.png]]

||Outcome|Frequency|
|---|---|---|
|0|None (0 heads)|238|
|1|One (1 head)|488|
|2|Both (2 heads)|274|

## The Normal Deviate (Z) test

The **null-hypothesis population** is an actual or theoretical set of population scores that would result if the experiment were done on the entire population and the independent variable had no effect. It is called the null-hypothesis population because it is used to test the validity of the null hypothesis.

> [!important] The
> 
> **Z-test** is used **when we know the parameters of the null-hypothesis population.**
> 
> $$z_{obt} = \frac{\overline{X}_{obt}-\mu}{\sigma_{\overline{x}}} =  
> \frac{\overline{X}_{obt}-\mu}{\sigma_{x} / \sqrt{n}}$$

![[z-test.png]]

Let’s see an example.

> Assume you are superintendent of public schools in Rovereto. Recently, local citizens have been concerned that the instruction program in the public schools may be an inferior one. _**You decide to conduct an experiment to investigate the matter.**_
> 
> You set alpha $\alpha = 00.5$ for making your decision. You begin by comparing the reading level of current high school seniors with **established norms**, which are based on scores from a reading proficiency test **administered nationally to a large number of high school seniors**. The scores of this population are normally distributed with mean $\mu$ = 75 and standard deviation $\sigma$ = 16.
> 
> > [!important] In this case,
> > 
> > **we actually know the parameters of the null-hypothesis** (for the entire) **population**.
> 
> For your experiment you administer the reading test to 100 randomly selected high school seniors in Rovereto, and the consequent obtained mean of the sample $(\overline{X}_{obt}) = 72$.
> 
> **What is your conclusion?** The sample mean 72 is lower than the population mean 75, but **how meaningful is this difference?**
> 
> $$H0: (\overline{X}_{obt}) = \mu \ \ \text{ while } \ \  
> H1 : (\overline{X}_{obt}) < \mu$$
> 
> > [!important] We want to determine probability of obtaining a mean score such as 72 when sampling 100 individuals from a population with
> > 
> > $\mu = 75$ and $\sigma = 16$.
> 
> Since the statistic whose distribution we are studying is the mean, we can say that **we are determining the extremeness of the sampling distribution of the mean**.

> [!important] Recap: we are trying to determine the probability of obtaining an
> 
> $\overline{X}$ mean score when sampling $N$ individuals from a population of which we know the mean $\mu$, the standard deviation $\sigma$, and also that is normal (i.e. bell-shaped).

To do so, we will use the **Central Limit Theorem**, and in particular the sampling distribution of the mean.

### The Sampling Distribution of the Mean (SDM)

> [!important] The
> 
> **sampling distribution of the mean** provides all the values the mean can take, along with the probability of obtaining each value if sampling is random from the null-hypothesis population.

Assume there is a population $X$, which will be our null-hypothesis population, of which we know its mean $\mu_X$ and standard deviation $\sigma_X$. Now consider that we take repeated samples $x$ of size $n$ from this population $X$. We then go on and calculate the mean of each sample (so ${\overline{x}_1}, {\overline{x}_2}, \dots, {\overline{x}_n}$).

$$X = \text{population},\ x = \text{sample},\ \overline{x} = \text{mean of sample}$$

**This set of values composes the Sampling Distribution of the Mean (SDM) for samples of size** $n$ **taken from a specific population,** as per above.

> [!important] Using the same notation, the sampling distribution of the mean has its own mean, called
> 
> **the mean of the sampling distribution of the mean** $\mu_{\overline{x}}$, and its own standard deviation, called **the standard deviation of the sampling distribution of the mean** $\sigma_{\overline{x}}$.

$$\mu_{\overline{x}} : \text{the mean of the sampling distribution of the mean}$$

> [!important] **The SDM provides a theoretical distribution**
> 
> ==**assigning probabilities to each possible sample mean**==, assuming random sampling from the null-hypothesis population.

### The Central Limit Theorem

There are three parts to the **Central Limit Theorem.**

1. The **mean of the sampling distribution of the mean** will be the same as the population mean:
    
    $$⁍$$
    
    > [!important] The mean is an
    > 
    > _unbiased_ statistic, so sample means will be, on average, equal to the population mean.
    
2. For a sample size $n$, the **Standard Deviation of the SDM** $\sigma_{\overline{x}}$**,** sometimes shortened to the _**standard error of the mean**_ , or ‘**S.E.M**.’ or even just **‘SE**’. will be:
    
    $$⁍$$
    
    > [!important] This indicates that the variability of sample means decreases with larger sample sizes, reflecting the "error" in estimation.
    
3. **The sampling distribution of the mean will tend to be close to normally distributed**. Moreover, the sampling distribution of the mean will tend towards normality as:
    1. (a) the population tends toward normality,
    2. and/or (b) the sample size increases*.
        
        > [!important] This last part is the most remarkable. It means that even if the population is not normally distributed,
        > 
        > **the sampling distribution of the mean will be roughly normal if your sample size is large enough**.
        

### Demonstrations

Below is the results of a simulation demonstrating the Central Limit Theorem.

![[Untitled 21.png|Untitled 21.png]]

The graph on the top is the population distribution, which for this example is normal with a mean of $\mu = 100$ and a standard deviation of $\sigma = 15$.

In the bottom graph ==in blue you can see a histogram of the means from these samples==. Drawn on top of the histogram is the expected normal distribution of means according to the Central Limit Theorem:

$$\mu_{\overline{x}} = \mu = 100 \ \ \ ; \ \ \  
\sigma_{\overline{x}} = \frac{\sigma_X}{\sqrt{n}} = \frac{15}{\sqrt{9}} = 5$$

You can see that the smooth curve matches the distribution of actual means. The mean of sample means in this simulation is 99.97 and the standard deviation of the means is 5.01 - pretty close to what’s expected from the Central Limit Theorem.

**In this second demonstration we’ll draw from a population that is clearly not normally distributed:**

![[Untitled 1 10.png|Untitled 1 10.png]]

This time the population is a 'Chi-squared' ($\mathcal{X^2}$) distribution. The population has a mean of 3 and standard deviation of 2.4495.

Like before, ==the blue histogram in the bottom graph shows the distribution of 1000 means of sample size 36 from this skewed population distribution==. Notice that sample means have a nice, symmetric normal-looking distribution.

The Central Limit Theorem predicts that the distribution of means should be roughly normal with a mean of $\mu_{\overline{x}} = \mu = 3$ and a standard deviation of $\sigma_{\overline{x}} = \frac{\sigma_X}{\sqrt{n}} = \frac{2.4495}{\sqrt{36}} = 0.4082$

In this simulation, the mean of these means is 2.99 which is close to the population mean, and a standard deviation of 0.4125, which is close to what's expected from the Central Limit Theorem. Like the first example, the smooth curve in the bottom graph is a normal distribution with the mean and standard deviation expected from the Central Limit Theorem. It clearly matches the distribution of sample means from the simulation.

> [!important] The Central Limit Theorem is powerful because,
> 
> **if you know that a distribution is normal, and you know its mean and standard deviation, then you know everything about this distribution.**

### When is SDM bell-shaped?

> [!important] The shape of the Sampling Distribution of the Mean (SDM) depends on the population of raw scores and the sample size
> 
> $n$.

If the population of raw scores is normally distributed, the SDM will also be normally distributed, regardless of the sample size $n$.

> [!important] When the sample size
> 
> $n$ is 30 or larger, the SDM is likely to be normal in shape, **regardless of the population distribution**.

This is due to the **Central Limit Theorem**, which states that as sample size $n$ increases, the sampling distribution of the mean approaches a normal distribution, regardless of the shape of the population distribution.

> [!important] **If the population distribution is not normal, the shape of the SDM will still approximate a normal distribution if the sample size**
> 
> $n$ **is large enough.**

### Back to the Example

> Let’s go back to our example from above, assessing the reading level of high school seniors in Rovereto.
> 
> We know the $\mu$ and $\sigma$ of our (null-hypothesis) population $X$.
> 
> $$\mu = 75,\ \ \ \sigma = 16$$
> 
> For your experiment you administer the reading test to 100 randomly selected high school seniors in Rovereto, and the consequent obtained mean of the sample $(\overline{X}_{obt}) = 72$.
> 
> $$n = 100, \ \ \ \overline{X}_{obt} = 72$$
> 
> **What is the probability of obtaining 72 (or lower) by chance assuming a random sample from the null-hypothesis population?**
> 
> With the knowledge gained from the Central Limit Theorem and the SD of the SDM we derive that, for SDM with sample $n$ of size 100:
> 
> $$\mu_{\overline{x}} = \mu = 75 \ \ \ ; \ \ \  
> \sigma_{\overline{x}} = \frac{\sigma_X}{\sqrt{n}} = \frac{16}{\sqrt{100}} = 1.6$$
> 
> We now know the mean and SD of the theoretical SDM, **we can calculate how ‘surprising’ our own sample is:** calculating the exact probability of obtaining $\overline{X}_{obt} = 72$:
> 
> $$z_{obt} = \frac{\overline{X}_{obt}-\mu}{\sigma_{\overline{x}}} =  
> \frac{72-75}{1.6} = -1.88$$
> 
> ```Python
> import scipy.stats, numpy
> 
> # Our sample, mean, standard deviation and obtained score.
> n = 100; mu = 75; sigma = 16; x = 72
> 
> # SD of the Standard Error of the Mean
> sem = sigma/numpy.sqrt(n)  # 16 over sqrt of 100
> 
> # Z normalize
> z = (x - mu) / sem  # = -1.88
> 
> # Calculate the Cumulative Distribution probability
> # This is because we are calculating an area,
> # i.e. getting 72 or lower.
> p =  scipy.stats.norm.cdf(z,0,1)
> print(f"p = {p}")
> # p = 0.03039636176526137
> ```
> 
> So, the probability of obtaining 72 or lower is quite low if one assumes that this is a random sample from the null-hypothesis population: only $\sim3\%$ are **as low or lower**.
> 
> $$p(0.03) < \alpha \rarr \text{reject H0}$$
> 
> Because this probability $p$ is lower than our set alpha $\alpha = 0.05$, we end up rejecting H0 (that was that our obtained mean was just like the population mean) and accept instead H1 (so that we are actually below the population mean.

### Implementing Z Test Using Critical Regions

The Z-test is a statistical test used to determine if there is a significant difference between sample data and a population parameter. The test relies on critical regions and critical values to decide whether to reject the null hypothesis (H0).

1. The **critical region** is the area under the curve of the sampling distribution that contains all values of the statistic which allow for the rejection of H0. This area corresponds to the chosen significance level ($α$), such as 0.05, 0.025, or 0.01.
2. The **critical value** ($z_{crit}$) is the value that bounds the critical region. For a given significance level, this value can be found using standard Z-tables or statistical software.

### Using the Critical Region

In this method, you do not need to find the exact probability of obtaining the observed Z ($z_{obt}$) or more extreme values. Instead, follow these steps:

**Determine the Critical Value (**$z_{crit}$**)**: Based on the significance level ($α$) and whether the test is one-tailed or two-tailed:

||For a one-tailed test|For a two-tailed test|
|---|---|---|
|α = 0.05|$z_{crit}$ = 1.645|$z_{crit}$ = ±1.96|
|α = 0.025|$z_{crit}$ = 1.96|$z_{crit}$ = ±2.24|
|α = 0.01|$z_{crit}$ = 2.33|$z_{crit}$ = ±2.58|
|α = 0.005|$z_{crit}$ = 2.58|$z_{crit}$ = ±2.81|

![[Untitled 2 10.png|Untitled 2 10.png]]

![[Untitled 3 9.png|Untitled 3 9.png]]

> [!important] **Compare**
> 
> $z_{obt}$ **with** $z_{crit}$: Calculate the Z score ($z_{obt}$) for your sample data. If $z_{obt}$ falls within the critical region (beyond $z_{crit}$), reject H0. If it falls inside the interval of $z_{crit}$, keep H0.

### Example of a Z-Test Implementation in Python

```Python
import scipy.stats as stats

# Given data
sample_mean = 105
population_mean = 100
population_std = 15
sample_size = 30
significance_level = 0.05

# Calculate standard error
standard_error = population_std / (sample_size ** 0.5)

# Calculate the observed Z score
z_obt = (sample_mean - population_mean) / standard_error

# Determine the critical value for a two-tailed test
z_crit = stats.norm.ppf(1 - significance_level / 2)

# Determine if we reject the null hypothesis
if abs(z_obt) > z_crit:
    print(f"Reject H0: z_obt ({z_obt}) is in the critical region (beyond {z_crit})")
else:
    print(f"Fail to reject H0: z_obt ({z_obt}) is not in the critical region")

# Output the results
print(f"z_obt: {z_obt}, z_crit: {z_crit}")
```

This example demonstrates how to perform a Z-test using critical regions and critical values in Python. The calculated Z score is compared against the critical value to decide whether to reject the null hypothesis. The method ensures a structured approach to hypothesis testing by defining the rejection zones based on the significance level.

### Summary of Z-test

1. Applicable when the study involves a _single_ sample mean;
2. The parameters of the population parameters reflecting the null (null-hypothesis population) are known;
3. The sampling distribution of the mean should be normally distributed.
    1. This will depend on the sample size used in the particular Z test.

## Sample Problems

> [!important] Remember:
> 
> $$z_{obt} = \frac{\overline{X}_{obt}-\mu}{\sigma_{\overline{x}}} =  
> \frac{\overline{X}_{obt}-\mu}{\sigma_{x} / \sqrt{n}}$$
> 
> $$\alpha = 0.05  
> \begin{cases}  
> \text{one-tailed test} & z_{crit} = 1.645 \\  
> \text{two-tailed test} & z_{crit} = ±1.96  
> \end{cases}$$

Problem 1:

A university president believes that, over the past few years, the average age of students attending his university has changed. To test this hypothesis, an experiment is conducted in which the age of 150 students who have been randomly sampled from the student body is measured. The mean age is 23.5 years. A complete census taken at the university a few years before the experiment showed a mean age of 22.4 years, with a standard deviation of 7.6.

- What is H1? Directional or not?
- What is the null hypothesis?
- Use the appropriately-tailed test, $\alpha = 0.05$ to evaluate H1

  

Problem 2:

A gasoline manufacturer believes a new additive will result in more miles per gallon. Previously, a large number of mileage measurements on the gasoline without the additive have been made by the company under rigorously controlled conditions for thousands of cars. The results show a mean of 24.7 miles per gallon and a standard deviation of 4.8. Tests are conducted on a new sample of 75 cars using the gasoline to which the additive has been added. The sample mean equals 26.5 miles per gallon.

- Set $\alpha=0.05$.
- Phrase the appropriate H0 and H1
- Construct the test
- Draw conclusions