---
Date: 2024-03-26
Reviewed: true
week_lec: 6.2
---
- [[#Bernoulli and Binomial]]
    - [[#Distributions]]
    - [[#Bernoulli Distribution]]
        - [[#Random variable and probability of success]]
        - [[#Mean, variance and Probability Mass Function]]
    - [[#Binomial Distribution]]
        - [[#Mean and Variance of Binomial Distribution]]
        - [[#Probability Mass Function (PMF) of Bin. D.]]
        - [[#Obtaining values and construction of PMF for Bin. D.]]
    - [[#Some practice]]
        - [[#Six unbiased coins thrown. What is the probability that all 6 landed on heads?]]
        - [[#Six unbiased coins thrown. What is the probability that 4 or more landed on heads?]]
        - [[#Six unbiased coins thrown. What is the probability that only 1 lands on heads?]]
        - [[#What is the mean of Bin(6, 0.5)?]]
        - [[#Practice: Multiple choice exam]]
        - [[#Practice: Starbucks]]
    - [[#Approximating binomial to Normal distribution]]
    - [[#Significance and Significance-tests]]
        - [[#Significance tests]]
        - [[#Testing hypothesis with binomial distribution]]
        - [[#The binomial distribution and Sign Test]]
        - [[#Formalizing concepts: null and alternative hypotheses]]
        - [[#Decision Rule and Alpha Level in Hypothesis Testing]]
        - [[#Decisions and Errors in Hypothesis Testing]]
    - [[#Quantifying Extremeness on a Normal Distribution]]
        - [[#Why Consider a 5% Area?]]
        - [[#Determining the Extreme Zone]]
        - [[#Practical Application]]
    - [[#Calculating p-value]]
        - [[#Calculating p-value: Continuous Distributions]]
        - [[#Calculating p-value for Binomial Distributions]]
    - [[#Evaluating a result (P-value) for 1- and 2-tailed tests]]
        - [[#One-tailed tests]]
        - [[#One-Tailed Test: Binomial Example]]
        - [[#Two-Tailed Tests]]
        - [[#A P-value in relation to 1- and 2-tailed tests]]
        - [[#Common Principle for One-Tailed and Two-Tailed Tests]]

---

# Bernoulli and Binomial

### Distributions

> [!important] **Distributions serve as a crucial gateway to inferential statistics,**
> 
> enabling researchers to **organize and interpret data** effectively.

They help **organize scores for interpretation**, providing a structured overview of the values observed in a sample. **Each score in a distribution is associated with an underlying probability in the population.** These probabilities provide insight into the likelihood of observing certain values.

Distributions are often categorized based on the nature of the data being analyzed:

- **Discrete Distributions:** Associated with nominal or ordinal data where values are distinct and separate.
- **Continuous Distributions:** Often seen in interval or ratio data and may approximate a normal distribution. The normal distribution (often denoted as $N()$ ) serves as a reference point for understanding continuous distributions.

## Bernoulli Distribution

> [!important] The Bernoulli distribution
> 
> **(**$\text{Ber}$**)** captures the probability of each possible outcome in an experiment with only two possibilities, called a Bernoulli trial. It's a **discrete probability distribution** used to describe binary outcomes of a single trial, like a coin toss, a success or failure on a yes/no exam, or any other situation with two possible outcomes.

In the Bernoulli distribution, one of the outcomes is typically referred to as a "success," although this term is context-dependent and arbitrary.

### Random variable and probability of success

> [!important] The Bernoulli Distribution involves the notion of a
> 
> **random variable**, which is a variable whose values are (thought to be) determined by a random process. In the context of the Bernoulli Distribution, this random variable represents the outcome of a single Bernoulli trial.

Central to the Bernoulli Distribution is the **probability of success** denoted by $p$, where:

$$⁍$$

Success typically refers to one of the two possible outcomes of the trial. A **Bernoulli random variable** assigns the value 1 to represent success with probability $p$ , and the value 0 to represent failure with probability $1 - p$.

The distribution followed by this random variable, with the given probability of success $p$, is termed the **Bernoulli distribution**. It is denoted as $X \sim \text{Ber}(p)$. The Bernoulli distribution is then characterized by a single parameter $p$, representing the probability of success in a single trial.

### Mean, variance and Probability Mass Function

> [!important] In the Bernoulli Distribution, the
> 
> **mean** of the random variable $X$ is $p$, and its **variance** is $p \times (1 - p)$.
> 
> $$\mu(X) = p \\ \sigma^2(X) = p \times (1-p)$$

> For instance, if we consider a scenario where success is denoted as 1 and failure as 0, and the probability of success $p$ is 0.7, then the **variance** would be: $0.7 \times (1 - 0.7) = 0.21$.
> 
> The distribution from which we sample in this case is denoted as $\text{Ber}(0.7)$, indicating a Bernoulli distribution with a success probability of 0.7.

The **Probability Mass Function (PMF)** of the Bernoulli Distribution presents the relative probabilities of the different values of the random variable $X$, which are typically 1 and 0.

$$P(X = x) =  
\begin{cases}  
p & \text{if } x = 1 &\text{ success} \\  
1 - p & \text{if } x = 0 &\text{failure}  
\end{cases}$$

Where $X$ is the random variable representing the outcome, $x$ is the specific outcome (0 or 1), and $p$ is the probability of success (outcome 1).

> [!important] There are
> 
> **only two possible outcomes**, and they are **mutually exclusive** (i.e., they cannot both occur simultaneously).

> In our example, $P(1)$, the probability of observing a success, is 0.7, while $P(0)$, the probability of observing a failure, is 0.3.
> 
> ![[Untitled 25.png|Untitled 25.png]]

> [!important] The
> 
> **Bernoulli Distribution** is important because it forms **the basis for modeling and understanding binary outcomes in experiments or trials**. By describing the probabilities of success and failure, it helps in decision-making, hypothesis testing, and predicting future events.

## Binomial Distribution

> [!important] **When we repeat many Bernoulli trials, the number of successes on these trials follows a Binomial distribution (**
> 
> $\text{Bin}$**).**

Let's break down what this means: Suppose we have a Bernoulli trial sampled from $\text{Ber}(p)$, and it is repeated $n$ times. We obtain a random sample: $X_1, X_2, \ldots, X_n$, where each $X_i$ represents the outcome of the $i$th trial (either 0 for failure or 1 for success).

> [!important] The
> 
> **number of successes**, denoted as $Y$, represents how many 1s we have drawn among the $n$ trials. Mathematically, we express this as the sum of all the $X$s, which in case of success will be 1, and in case of failure will be 0.
> 
> $$Y = \sum_i^n X_i$$

> [!important] The number of successes
> 
> $Y$ follows a Binomial Distribution with probability $p$ and number of trials $n$, denoted as $\text{Bin}(n,p)$.

This means that **the probability of obtaining different magnitudes of sums** (values of $Y$) depends on two factors:

1. The probability of success on each trial, denoted as $p$.
2. The number of trials we are sampling from, denoted as $n$.

> For example, a distribution $\text{Bin}(10, 0.5)$ describes the likelihood of throwing a fair coin (where $p = 0.5)$ 10 times (where $n = 10$) and obtaining 0, 1, 2, ..., or 10 heads.

$$\text{Bin}(n,p) = \text{Bin(number of trials, probability)}$$

### Mean and Variance of Binomial Distribution

> [!important] In the Binomial Distribution, the mean and variance can be calculated with:
> 
> $$mean(Y) = n\times p \\  
> var(Y) = n\times p(1-p) = n\times p\times q$$
> 
> where $q$ is the probability of failure.

> Let's calculate the mean number of successes for two scenarios:
> 
> For $\text{Bin}(10, 0.5)$ :
> 
> - $n = 10$ (number of trials)
> - $p = 0.5$ (probability of success)
> - Using the mean formula, $\text{mean}(Y) = 10 \times 0.5 = 5$
> 
> For $\text{Bin}(10, 0.7)$ :
> 
> - $n = 10$ (number of trials)
> - $p = 0.7$ (probability of success)
> - Using the mean formula, $\text{mean}(Y) = 10 \times 0.7 = 7$

### Probability Mass Function (PMF) of Bin. D.

> [!important] In the Binomial Distribution, the
> 
> **Probability Mass Function (PMF)** calculates **the probability of obtaining a specific number of successes $y$ in a fixed number of trials $n$, given a probability of success $p$**.

The probability mass function (PMF) for a binomial distribution is calculated using the formula:

$$P(Y = y) = \frac{n!}{y!(n - y)!} p^y (1 - p)^{n - y}$$

Where:

- $n$ is the number of trials,
- $p$ is the probability of success on each trial,
- $y$ is the number of successes (the outcome we're interested in),
- $!$ denotes factorial.

> [!important] We iterate over each potential outcome
> 
> $y = 0, 1, \ldots, n$ to calculate the probability of each outcome.

> For example, for $\text{Bin}(10, 0.5)$ for a fair coin - so each side has 0.5 probability - tossed 10 times, what is the probability of getting 5 successes ($P(Y=5)$)?
> 
> $$P(Y = 5) = \red{\frac{10!}{5!(10 - 5)!}} \times \blue{0.5^5 (1 - 0.5)^{10 - 5}} = 0.246$$
> 
> - ==The left side calculates how many unique combinations there are for selecting 5 out of 10 (=252).==
> - ==The right side of the formula presents the joint probability of one particular combination of== ==$y$== ==successes and== ==$n-y$== ==failures (=0.00098).==

Once we have calculated these probabilities, we can **plot the entire PMF to visualize the distribution of possible outcomes**. This helps us understand the relative likelihood of each outcome occurring in the binomial experiment.

Here are the probabilities $P(Y = y)$ for $\text{Bin}(10, 0.5)$ calculated for different values of $y$ (from 0 to 10):

- $P(Y = 0) = \frac{10!}{0!(10 - 0)!} \times 0.5^0 \times (1 - 0.5)^{10 - 0} = 0$
- $P(Y = 1) = \frac{10!}{1!(10 - 1)!} \times 0.5^1 \times (1 - 0.5)^{10 - 1} = 0.5$
- $P(Y = 2) = \frac{10!}{2!(10 - 2)!} \times 0.5^2 \times (1 - 0.5)^{10 - 2}$
- $\vdots$
- $P(Y = 10) = \frac{10!}{10!(10 - 10)!} \times 0.5^{10} \times (1 - 0.5)^{10 - 10}$

### Obtaining values and construction of PMF for Bin. D.

In Python, you can calculate specific probabilities for the Binomial Distribution using functions from the `scipy.stats` module:

1. To obtain $P(Y = 5)$ for $\text{Bin}(10, 0.7)$, you can use the `pmf()` method:
    
    ```Python
    from scipy.stats import binom
    
    binom.pmf(5, n=10, p=0.7)
    """
    OUTPUT
    0.1029193452
    """
    ```
    
2. To obtain $P(Y \leq 8)$ for $\text{Bin}(10, 0.7)$, you can use the `cdf()` method:
    
    ```Python
    binom.cdf(8, n=10, p=0.7)
    """
    OUTPUT
    0.8506916836
    """
    ```
    

  

  

In Python, you can use the `numpy` and `matplotlib.pyplot` libraries to obtain values and construct the Probability Mass Function (PMF) for a Binomial Distribution. Here's how you can rewrite the given R code in Python:

```Python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import binom

# Calculate PMF for Binomial Distribution
y_values = np.arange(0, 11)
BinPMF = binom.pmf(y_values, n=10, p=0.7)

# Plot PMF
plt.plot(y_values, BinPMF, marker='o', linestyle='-')
plt.xlabel('Y (number of successes)')
plt.ylabel('Probability')
plt.title('Probability Mass Function for Bin(10, 0.7)')
plt.grid(True)
plt.show()
```

![[Figure_1.png]]

Output of the code above

## Some practice

> [!important] Remember that:
> 
> $$p = {\text{Number of ways a desired outcome can occur} \over{\text{Total number of possible outcomes}}}$$

### **Six unbiased coins thrown. What is the probability that all 6 landed on heads?**

Each coin has a 0.5 prob of land on head or tail. The probability that one throw lands on H is 0.5. The probability of having all of them H is 0.5^6, so 0.015625. $P(H_6) = 0.015625$

### **Six unbiased coins thrown. What is the probability that 4 or more landed on heads?**

To determine the probability that four or more out of six unbiased coins landed on heads, we can use the binomial distribution formula.

The probability of getting exactly $k$ successes (heads) in $n$ trials (coin tosses) is given by:

$$⁍$$

where:

- $\binom{n}{k}$ is the binomial coefficient, calculated as $\frac{n!}{k!(n - k)!}$
- $n$ is the number of trials (6 in this case)
- $k$ is the number of successes (heads)
- $p$ is the probability of success on a single trial (0.5 for an unbiased coin)

We want the probability of getting 4 or more heads, so we need to calculate the probabilities for getting exactly 4, 5, and 6 heads, and then sum these probabilities.

1. **Probability of getting exactly 4 heads:**
    
    $$⁍$$
    
    $\binom{6}{4} = \frac{6!}{4!(6 - 4)!} = \frac{6!}{4!2!} = \frac{6 \times 5 \times 4!}{4! \times 2 \times 1} = 15$
    
    $P(X = 4) = 15 \times (0.5)^4 \times (0.5)^2 = 15 \times (0.5)^6 = 15 \times \frac{1}{64} = \frac{15}{64}$
    
2. **Probability of getting exactly 5 heads:**
    
    $$⁍$$
    
    $\binom{6}{5} = \frac{6!}{5!(6 - 5)!} = \frac{6!}{5!1!} = \frac{6 \times 5!}{5! \times 1} = 6$
    
    $P(X = 5) = 6 \times (0.5)^5 \times (0.5)^1 = 6 \times (0.5)^6 = 6 \times \frac{1}{64} = \frac{6}{64} = \frac{3}{32}$
    
3. **Probability of getting exactly 6 heads:**
    
    $$⁍$$
    
    $\binom{6}{6} = 1$
    
    $P(X = 6) = 1 \times (0.5)^6 \times (0.5)^0 = 1 \times (0.5)^6 = 1 \times \frac{1}{64} = \frac{1}{64}$
    

**Now, sum the probabilities for getting exactly 4, 5, and 6 heads:**

$$⁍$$

$P(X \geq 4) = \frac{15}{64} + \frac{3}{32} + \frac{1}{64} = \frac{15 + 6 + 1}{64} = \frac{22}{64} = \frac{11}{32}$

So, the probability that four or more out of six unbiased coins landed on heads is:

$P(X \geq 4) = \frac{11}{32} \approx 0.34375$

**This means there is approximately a 34.38% chance that four or more of the six coins will land on heads.**

### Six unbiased coins thrown. What is the probability that only 1 lands on heads?

The probability that only one lands on H is the probability that one lands on H plus the probability that all the others land on T.

$$P(X = 1) = \binom{6}{1} (0.5)^1 (0.5)^5$$

$\binom{6}{1}$ = $\frac{6!}{1!(6-1)!} = \frac{6!}{5!} = \frac{6 \times 5!}{5!} = 6$

0.5 x 0.5^5 = 1/64

6 x 1/64 = 3/32 = **0.09375**

### What is the mean of Bin(6, 0.5)?

$$\mu \text{ of } Bin(6, 0.5) = 6 \times 0.5 = 3$$

### Practice: Multiple choice exam

> [!important] The Binomial case applies whenever an event can be classified as success or failure even it can be realized in multiple ways.

**Treat the following from a Binomial perspective:**

> A student is taking a multiple-choice exam with 15 questions. Each question has five choices. If the student guesses on each question, what is the probability of passing the test? The lowest passing score is 60% of the questions answered correctly. Assume that the choices for each question are equally likely. B(?, ?). Needs to have Z or more successes.

15 questions, 5 choices each equally likely (1/5 = 0.2). At least 7 correct.

What is the probability of getting 7 out of 15 question correct guessing?

$$P(X=7)= \binom{15}{7}(0.2)^7 (1-0.2)^{15-7} \\  
P(X = 7) ≈ 0.0138191$$

```Python
from scipy.stats import binom

# Define the parameters
n = 15   # Number of trials
p = 0.2  # Probability of success
k = 7    # Number of successes

# Calculate the probability
probability = binom.pmf(k, n, p)
print(probability)

# Same output as above, 0.013819057274880019
```

### Practice: Starbucks

> Your friend claims to be a coffee connoisseur. He always drinks Starbucks and claims no other coffee even comes close to tasting so good. You suspect he is being a little grandiose. In fact, you wonder whether he can even taste the difference between Starbucks and the local roasters coffee. Your friend agrees to the following experiment. While blindfolded, he is given six opportunities to taste from two cups of coffee and tell you which of the two cups contains Starbucks. The cups are identical the coffee is brewed identically, apart from the fact that one is made from beans supplied and roasted by Starbucks and the other by the local roaster. After each tasting of the two cups, you remove any telltale signs and randomize which of the two cups he is given first for the next trial. Believe it or not, your friend correctly identifies Starbucks on all six trials!

**How likely is this? What do you conclude?**

$$P(X=6)= \binom66 (0.5)^6 (0.5)^{6-6} = 0.015625 = 0.015\%$$

He _**is**_ a coffee connoisseur.

## Approximating binomial to Normal distribution

> [!important] **When the number of trials $N$ in a binomial distribution is sufficiently large**
> 
> , typically greater than 20 when $P = Q = 0.5$, **the binomial distribution starts to resemble a normal distribution**. This is useful because normal distributions are easier to work with and have well-known properties.

The parameters of the approximating normal distribution are as follows:

- The mean $\mu$ of the distribution is:

$$\mu = n\times p$$

- The standard deviation $\sigma$ is:

$$\sigma = \sqrt{n \times p \times q}$$

> [!important] where
> 
> $n$ number of trials, $p$ = probability of success, $q = 1-p$ probability of failure.

> [!important] To find the probability of a certain number of successes using the normal approximation, you can calculate the Z-score using the formula:
> 
> $$Z = \frac{X - \mu}{\sigma}$$

Where $X$ is the number of successes. **This Z-score tells you how many standard deviations away** $X$ **is from the mean**, allowing you to use standard normal distribution tables or software to find probabilities.

> [!important] **Lower z-score means closer to the meanwhile higher means more far away**
> 
> . If a z-score is further away from the mean in a normal distribution it means that it is a more extreme result, thus more rare to happen by chance.

> For example, let's say we flip 20 unbiased coins. We want to find the Percentile Rank of getting 18 heads.
> 
> Given:
> 
> $$\mu = 20 \times 0.5 = 10 \\  
> \sigma = \sqrt{20 \times 0.5 \times 0.5} = 2.24 \\  
> X = 18$$
> 
> We can calculate the Z-score:  
> $Z = \frac{18 - 10}{2.24} \approx 3.58$
> 
> The $z_{crit}$ for a two-tailed test with alpha set at 0.05 is $z_{crit} = \pm 1.96$
> 
> $$3.58 > 1.96 \rarr \text{Reject H0}$$
> 
> Then, we can use cumulative probability functions to find the Percentile Rank:
> 
> For the **normal** distribution:`scipy.stats.`**`norm`**`.cdf(3.58, 0, 1)` approximately 0.9998282.
> 
> For the **binomial** distribution: `scipy.stats.`**`binom`**`.cdf(18, 20, 0.5)` approximately 0.9999799

> [!important] The normal approximation works well and is quite accurate for large
> 
> _N_, but there is still a small difference due to the approximation.

The normal approximation to the binomial distribution is useful for large sample sizes as it simplifies calculations and provides results that are close to the exact binomial probabilities. However, for highly accurate results, especially when the number of trials is not extremely large, using the binomial distribution directly is preferable. This comparison shows that while the normal approximation is a good estimate, it is not perfect and small discrepancies can occur.

## Significance and Significance-tests

> [!important] A study's defined **significance level**, denoted by $\alpha$, is the probability of the study rejecting the null hypothesis H0, given that the null hypothesis is true; and the **p-value of a result**, $p$ is the probability of obtaining a result at least as extreme, given that the null hypothesis is true.
> 
> The result is statistically significant, by the standards of the study, when:
> 
> $$p \le \alpha$$

Significance arises in various contexts, particularly when we compare different entities or observe events that challenge our existing beliefs or expectations. In psychology experiments, for example, significance is crucial in determining whether observed differences in scores between experimental conditions are meaningful and attributable to the experimental manipulation.

> [!important] Significance cannot be determined solely by visual inspection of results; instead,
> 
> **formal statistical tests must be employed to evaluate the data rigorously**.

Significance becomes relevant:

1. When **comparing** products, grades, or objects on relevant dimensions, and **identifying differences in values**.
2. When **observing events that deviate from prior conceptions of the world**, prompting the question of how likely such events are given our existing understanding.

> In a Psychology experiment, two experimental manipulations produce different scores. At which point can we say that these differences are meaningful and can be related to the experimental manipulation?

### Significance tests

Significance tests are conducted within the **framework of hypothesis testing**, which involves comparing observed data to what would be expected under a specific hypothesis. This framework typically involves two competing hypotheses:

- **Null Hypothesis (H0)**: there is no effect or difference between groups; or, more generally, that any observed results could occur by chance.
- **Alternative Hypothesis (H1)**: there is an effect or difference between groups; or, more generally, that the observed results are influenced by a non-random causal relationship.

> In psychology, for example, when comparing the mean values of two conditions (C1 and C2), the null hypothesis (H0) often states that there is no difference between the conditions.

> [!important] To assess the likelihood of the observed finding under the null hypothesis, we calculate a probability known as a
> 
> _**p-value**_. More on this later on.

The p-value represents the probability of obtaining the observed results (or more extreme) if the null hypothesis were true. A low p-value indicates that the observed results are unlikely to have occurred by chance alone, leading to rejection of the null hypothesis in favor of the alternative hypothesis.

### Testing hypothesis with binomial distribution

To test whether a coin is fair or biased towards heads using the binomial distribution, we follow these steps:

1. **Set up the Null Hypothesis (H0) and Alternative Hypothesis (H1):**
    
    $$H_0: x \leq \frac12 \ \ \ \ \  
    H_1: x > \frac12$$
    
2. **Set the significance level (**$\alpha$**)**, which represents the probability of ==**Type-I error**==, also written as the probability to reject H0 given that the outcome will be true:
    - Typically, $\alpha = 0.05$, meaning we are willing to accept a 5% chance of incorrectly rejecting the null hypothesis.
3. **Identify the test statistic**: For the binomial distribution, the test statistic is the number of successes (e.g., the number of times the coin lands on heads).
4. **(Optional) Identify the critical value**: Using statistical tables or calculations, find the critical value that marks the boundary of the significance level. For example, `qbinom(0.95, 100, 0.5) = 58` marks the value below which 95% of the distribution lies.
    
    > [!important] Will discuss later
    
5. **Conduct the experiment:** Toss the coin 100 times and count the number of successes (e.g., the number of times it lands on heads). Then, calculate the probability of observing the obtained result (or a more extreme result) under the null hypothesis.

> For example, if the coin landed on heads 61 times out of 100 tosses, we calculate the probability of observing 61 or more heads out of 100 tosses under the assumption that the coin is fair $(x = 0.5)$.
> 
> This probability is $\sum_{k=61}^{100} dbinom(k, 100, 0.5) = 0.0176$.

> [!important] **If this probability is less than or equal to the significance level (**
> 
> $\alpha$**), we reject the null hypothesis** and conclude that the coin may be biased towards heads. **Otherwise, we fail to reject the null hypothesis.**

### The binomial distribution and Sign Test

> Consider a study where 10 participants were tested on impact of certain supplement pill vs. placebo) on natural caloric intake (AB repeated measures design)

In this scenario, you are considering the **Sign Test*** to evaluate whether a supplement pill has an impact on natural caloric intake compared to a placebo.

> [!important] The
> 
> **Sign Test** is a non-parametric test that assesses whether the proportion of positive differences (e.g., increase in caloric intake) is significantly different from the proportion of negative differences (e.g., decrease in caloric intake).

> You find that 9 of them increased caloric intake (to various degrees) and one decreased.

> [!important] We code positive differences with "+" and negatives with “-”, and evaluate the distribution of the two signs: Sign Test!

> Given that 9 out of 10 participants experienced an increase in caloric intake while one participant experienced a decrease, you would assign a positive sign (+) to the 9 increases and a negative sign (-) to the one decrease.

**Are we justified in thinking the supplement increased appetite?**

> Even if 9 out of 10 participants experienced an increase in caloric intake, it does not necessarily mean that the supplement pill caused this effect. To determine whether the observed result is statistically significant and not due to chance alone, you need to assess the probability of obtaining this result under the assumption that the supplement pill has no effect (null hypothesis).

If, under the null hypothesis, it is still quite likely to obtain 9 (or similarly extreme) positive signs out of 10, then we _cannot_ confidently conclude that the supplement pill increased appetite.

> [!important] In other words,
> 
> **even if the probability of obtaining the observed result is low** (e.g., 1 in 1,000,000), **we need to consider the significance level** $\alpha$ **to determine whether this probability is sufficiently low to reject the null hypothesis.**

### Formalizing concepts: null and alternative hypotheses

> [!important] It's crucial to ensure that these hypotheses are
> 
> **exhaustive** and **mutually exclusive**. This means that if the null hypothesis H0 is false, then the alternative hypothesis H1 must be true, and vice versa.

Following the previous example, we conclude that:

1. **Null Hypothesis (H0)**: the supplement has no effect on natural caloric intake.
2. **Alternative Hypothesis (H1)**: the supplement does have an effect on natural caloric intake.

> [!important] In cases where the alternative
> 
> **hypothesis is directional**, such as claiming that the supplement increases appetite, the null hypothesis serves as its counterpart. For example, the null hypothesis would state that the supplement does not increase appetite.

This helps frame the hypotheses in a clear and testable manner, allowing for precise interpretation of the results obtained from hypothesis testing procedures.

### Decision Rule and Alpha Level in Hypothesis Testing

When we evaluate the results of an experiment, we start by assessing the null hypothesis (H0). The reason we focus on H0 is that we can calculate the probability of chance events under this hypothesis, while it is more challenging to calculate probabilities for non-chance events.

> [!important] To evaluate H0, we assume it is true and calculate
> 
> **the probability of obtaining the observed result, or a more extreme result, given H0**. This probability is denoted as:
> 
> $$P(D|H0)$$

If $P(D|H0)$ is equal to or less than the alpha ($α$) level, we reject the null hypothesis.

> Consider a study where we want to test whether a supplement has an effect, using a binomial distribution.
> 
> - **Alternative Hypothesis (H1)**: The supplement has an effect ($p \le 0.05$).
> - **Null Hypothesis (H0)**: The supplement has no effect ($p > 0.5$).
> 
> Suppose we observe 9 successes out of 10 trials. We need to calculate the probability of obtaining 9 or more successes under H0.
> 
> ```Python
> from scipy.stats import binom
> 
> """
> binom.cdf(k, n, p): This function calculates the cumulative distribution function (CDF) of the binomial distribution. It gives the probability of getting k or fewer successes out of n trials with success probability p.
> """
> 
> # Calculate the cumulative probability of getting 8 or fewer successes
> prob_8_or_fewer = binom.cdf(8, 10, 0.5)
> 
> # Calculate the probability of getting 9 or more successes
> prob_9_or_more = 1 - prob_8_or_fewer
> 
> # Print the result
> print(f"Probability of getting 9 or more successes: {prob_9_or_more:.4f}")
> ```
> 
> **The result is 0.0107, which is lower than the typical alpha level of 0.05**. Therefore, we reject the null hypothesis H0 and accept the alternative hypothesis H1, concluding that the supplement likely has an effect.

### Decisions and Errors in Hypothesis Testing

When conducting hypothesis testing, two types of errors can occur:

> [!important] ==**Type II error**==
> 
> happens when **we keep the null hypothesis but we should actually reject it.** It is a f**alse negative**.

The probability of making a Type II error is denoted by beta $\beta$, and power of the test is $1 - \beta$.

> [!important] ==**Type I error**==
> 
> happens when **we reject the null hypothesis but we should actually keep it**. It is a **false positive**.

The probability of making a Type I error is denoted by the alpha $\alpha$ level, **set at the beginning of the experiment.**

When we conduct an experiment and obtain a p-value, we compare it to our alpha level:

$$\begin{cases}  
\text{if} & p \le \alpha &\text{reject H0} \\  
\text{if} & p > \alpha &\text{retain H0}  
\end{cases}$$

For instance, if we obtain $p= 0.0001 < \alpha$, we reject H0. **However, rejecting H0 does not mean we have proven H0 to be false; it simply means that our result is unlikely under H0.**

> [!important] No single experiment can reveal the absolute truth about a hypothesis.
> 
> **Replication of experiments is crucial** to confirm findings and reduce the likelihood of errors. Repeated studies provide more robust evidence regarding the validity of the null hypothesis and the alternative hypothesis.

## Quantifying Extremeness on a Normal Distribution

> [!important] In
> 
> **evaluating the null hypothesis H0**, we aim to determine whether our observed result falls within a set of results whose total, overall probability is less than or equal to the alpha level $\alpha$. This is often represented by **considering the cumulative probability of the observed result and comparing it to** $\alpha$**.**

> Consider a normal distribution with a mean ($\mu$) of 100 and a standard deviation ($\sigma$) of 15. The gray area under the curve represents the 5% of the distribution with cumulative probabilities exceeding or equaling 95%. This gray area helps us determine if an observation is significantly different from the mean under H0.

![[Untitled 1 14.png|Untitled 1 14.png]]

> [!important] Whether or not we reject an hypothesis is given by how surprising my results are, which corresponds to the area we are calculating now.

### Why Consider a 5% Area?

If there are multiple possible outcomes in this area (say, $X_1, X_2, X_3, \dots, X_n$), the sum of their probabilities should be less than or equal to 5%.

$$P(X_1) \cup P(X_2) \dots \cup X_n \le 5\%$$

This is because, according to H0, in any given experiment we can obtain any of those $X$s by chance.

> [!important] **This ensures that our false-positive rate (**
> 
> ==**Type I error**==**) is controlled at 5%,** meaning that we are limiting the probability of incorrectly rejecting H0 to 5%.

> Here’s an example:
> 
> Let's assume a distribution where the four most extreme possible values have the following probabilities: $P = (3.5\%, 3\%, 2.5\%, 2\%)$. If we decide to reject H0 when any of these four values are observed, the combined probability of these extreme values is $3.5\% + 3\% + 2.5\% + 2\% = 11\%$.
> 
> **This would set our** ==**Type I error**== **rate at 11%, which is higher than the desired 5%.**

### Determining the Extreme Zone

To see if an observation falls within this **extreme zone**, we use the **cumulative distribution function (CDF)**, represented by `pnorm` in R or `stats.norm.cdf` in Python + SciPy. Observations within this gray area are those with cumulative probabilities greater than or equal to 95%. Any observation falling within this area is considered to have a p-value less than 0.05.

### Practical Application

> For a normal distribution with $\mu = 100$ and $\sigma = 15$, **you can determine if a particular value is within the 5% extreme area by calculating its z-score and then using the CDF to find its cumulative probability**. If this cumulative probability is greater than 0.95, the observation is within the extreme 5% of the distribution, indicating that it is significantly different under H0.

Here's an example in Python using `scipy`:

```Python
import scipy.stats as stats

# Define mean and standard deviation
mu = 100
sigma = 15

# Calculate z-score for a given value
value = 130
z = (value - mu) / sigma

# Calculate cumulative probability
p_value = stats.norm.cdf(z)

print(f"Cumulative probability for value {value}: {p_value}")

# Check if the value is in the extreme 5%
if p_value >= 0.95:
    print(f"The value {value} falls within the extreme 5% of the distribution.")
else:
    print(f"The value {value} does not fall within the extreme 5% of the distribution.")
```

In this example, if `p_value` is greater than or equal to 0.95, the value is considered to be in the extreme 5% of the normal distribution.

## Calculating p-value

### Calculating p-value: Continuous Distributions

To calculate the p-value for continuous distributions using the cumulative distribution function (CDF), we often want to find the proportion of the distribution that lies above a certain value. This can be done directly using the `pnorm` function in statistical software.

- `pnorm(125, 100, 15, lower.tail=FALSE)` calculates the probability that a value from a normal distribution with a mean of 100 and a standard deviation of 15 is greater than 125. This gives a p-value of approximately 0.0478.
- Alternatively, you can calculate it as `1 - pnorm(125, 100, 15)`, which yields the same result.
- For a value of 124, `pnorm(124, 100, 15, lower.tail=FALSE)` or `1 - pnorm(124, 100, 15)` both return approximately 0.0548.

These calculations help determine the extremeness of a value under the normal distribution, informing whether to reject the null hypothesis.

### Calculating p-value for Binomial Distributions

For binomial distributions, which are discrete, the principle is similar but involves summing the probabilities of the observed outcome and all more extreme outcomes. This is because binomial distributions only take integer values, unlike the continuous normal distribution.

To evaluate the p-value for a binomial distribution, we use the `dbinom` function to calculate the probabilities and then sum these probabilities for the observed value and all more extreme values.

For example, suppose we want to find the p-value for obtaining 60 or more successes in 100 trials with a success probability of 0.5. We sum the probabilities of getting 60, 61, 62, ..., up to 100 successes:

```Python
import scipy.stats as stats

# Parameters
n = 100
p = 0.5
k = 60

# Sum the probabilities from k to n
p_value = sum(stats.binom.pmf(x, n, p) for x in range(k, n + 1))

print(f"P-value for getting {k} or more successes: {p_value:.3f}")
```

This script calculates the p-value for obtaining 60 or more successes in 100 trials, which is approximately 0.028. If this p-value is less than or equal to the alpha level (e.g., 0.05), we reject the null hypothesis (H0). Otherwise, we retain H0.

> [!important] In summary, the approach for calculating p-values differs slightly for continuous and discrete distributions:
> 
> - For continuous distributions, use the CDF to find the proportion of the distribution above the given value.
> - For discrete binomial distributions, sum the probabilities of the observed outcome and all more extreme outcomes to determine the p-value.
> 
> Both methods help assess the extremeness of the observed data and whether to reject the null hypothesis.

## Evaluating a result (P-value) for 1- and 2-tailed tests

### One-tailed tests

> [!important] One-tailed tests are used when we have a
> 
> **specific directional hypothesis**, indicating that the observations can only lead to rejecting the null hypothesis in one direction. This type of test focuses on the probability in one tail of the distribution.

When performing a one-tailed test, we designate a single area (or side) of the distribution to check for significance. This is relevant when our alternative hypothesis (H1) is directional.

> For example, if we hypothesize that the mean IQ in a university is significantly above the population mean, our hypotheses will be:
> 
> - **Null Hypothesis (H0)**: The mean IQ of the university is less than or equal to the population mean, $\overline{X} \leq \mu_0$.
> - **Alternative Hypothesis (H1)**: The mean IQ of the university is greater than the population mean, $\overline{X} > \mu_0$.
> 
> where $\mu$ is the mean IQ of the university and $\mu_0$ is the population mean.
> 
> In this scenario, any IQ result that is lower than or equal to the population mean, regardless of how extreme it is, cannot lead to rejection of H0. Therefore, we only consider the right tail of the distribution, where university mean IQs are greater than the population mean.
> 
> ![[Untitled 2 14.png|Untitled 2 14.png]]

> [!important] Calculating the p-value involves finding the probability of obtaining a result as extreme or more extreme than the observed result, in the specified direction.

### One-Tailed Test: Binomial Example

Let’s take another example, in which we want to understand whether a coin is fair or biased towards heads.

Hypotheses:

- **Null Hypothesis (H0)**: The coin is not biased towards heads, meaning the probability of getting heads, $p$, is 0.5.
- **Alternative Hypothesis (H1)**: The coin is biased towards heads, meaning the probability of getting heads, $p$, is greater than 0.5.

Consider a binomial distribution with 100 trials ($n = 100$) and a probability of success (getting heads) of 0.5 in each trial. This can be represented as $Bin(100, 0.5)$. In this context, a "success" is defined as getting heads.

We set our significance level ($\alpha$) at 0.05: once again, **this significance level represents the probability threshold for rejecting the null hypothesis.** Because H1 is directional (we are only interested in whether the coin is biased towards heads), we conduct a one-tailed test.

> [!important] The
> 
> **critical value** is the value that separates the rejection region from the non-rejection region.

For a binomial distribution with 100 trials and a significance level of 0.05, we find the critical value such that the cumulative probability from this value to the upper end of the distribution sums to 0.05. This means we are looking at the right tail of the distribution.

Let's say the critical value is 59. This implies that getting 59 or more heads in 100 coin flips has a cumulative probability of 0.05 under the null hypothesis.

![[Untitled 3 12.png|Untitled 3 12.png]]

> [!important] The
> 
> **rejection region** is the set of values where we reject the null hypothesis.

For this one-tailed test, the rejection region includes all values where the number of heads is greater than or equal to 59.

- **If the number of heads is 59 or more**: The probability of getting 59 or more heads purely by chance (under H0) is less than or equal to 0.05. Therefore, we reject the null hypothesis and conclude that the coin is biased towards heads.
- **If the number of heads is less than 59**: The probability of getting this result by chance is greater than 0.05. Therefore, we do not reject the null hypothesis and conclude that there is not enough evidence to say the coin is biased towards heads.

### Two-Tailed Tests

> [!important] In a two-tailed test, we are concerned with
> 
> **both directions of deviation** from the null hypothesis value. We test whether the observed value is either **significantly higher or significantly lower** than the null hypothesis value.

Hypotheses

- **Null Hypothesis (H0)**: The parameter of interest is equal to a specific value. For example, $H0: \overline{X} = \mu$, where $\mu$ is the population mean.
- **Alternative Hypothesis (H1)**: The parameter of interest is not equal to that specific value. For example, $H1: \overline{X} \neq \mu$.

> [!important] Let's say we set our significance level (
> 
> $\alpha$) at 0.05. **In a two-tailed test, this 5% significance level is split between the two tails of the distribution:**
> 
> - 2.5% in the lower tail (unexpectedly low values)
> - 2.5% in the upper tail (unexpectedly high values)

We can see how this reflects in determining the two critical values and their respective rejection regions:

- The lower critical value corresponds to the 2.5th percentile.
- The upper critical value corresponds to the 97.5th percentile.

> [!important] **If the test statistic falls below** the lower critical value **or above** the upper critical value, **we reject the null hypothesis.**

> **Example**: Let’s go back to our binomial distribution, where the null hypothesis is that a coin is fair ($p = 0.5$). We conduct 100 trials (flips) and want to test if the coin is biased, either towards heads or tails.
> 
> Given: $\alpha = 0.05$ (significance level), the significance level is divided into 0.025 in each tail.
> 
> For the binomial distribution $B(100, 0.5)$:
> 
> - We find the values such that the cumulative probability below the lower critical value is 0.025 and the cumulative probability above the upper critical value is 0.025.
> 
> Now, suppose these critical values are 39 (lower bound) and 61 (upper bound): Our **Lower Rejection Region** is set at fewer than 39 heads in 100 flips, while the **Upper Rejection Region**: is set at more than 61 heads in 100 flips.
> 
> $$Y \leq 39 ; Y \geq 61$$
> 
> ![[Untitled 4 9.png|Untitled 4 9.png]]
> 
> Bounds are 39 and 61

> [!important] In summary, a two-tailed test is used when deviations in either direction (higher or lower than expected) can lead to the rejection of the null hypothesis. The significance level is split between the two tails, and critical values are determined accordingly. The null hypothesis is rejected if the observed result falls in either tail of the distribution.

### A P-value in relation to 1- and 2-tailed tests

> [!important] For Two-Tailed Tests, we want to
> 
> **:**
> 
> 1. **Determine Critical Values** beyond which observations would be considered significantly unlikely under H0.
> 2. **Compare Observed Value to these critical values** to decide on the rejection of H0.

Using R, the p-value for an observation can be calculated, indicating the probability of observing that specific outcome or more extreme outcomes under H0. In a two-tailed test, if this p-value is below the significance level (commonly α = 0.05), H0 is rejected.

> **Example:**
> 
> Assume flipping a coin 100 times resulted in 60 heads. Calculating the probability of getting 60 or more heads in such a binomial distribution (B(100, 0.5)) yields:
> 
> ```R
> 		sum(dbinom(60:100, 100, 0.5)) = 0.02844397
> ```
> 
> This probability (p-value = 0.028) indicates that obtaining 60 or more heads is **sufficiently unlikely under H0 in a one-tailed** test where H0: p ≤ 0.5 and H1: p > 0.5, leading to the rejection of H0.
> 
> However, for a two-tailed test where H0: p = 0.5 and H1: p ≠ 0.5, this p-value only considers the upper tail (probability of observing more heads than expected). For a comprehensive two-tailed analysis, you would also need to consider the equivalent probability of observing an equally extreme outcome in the lower tail (fewer heads than expected). If the combined p-value (considering both tails) is below the significance level, then H0 would be rejected.

### Common Principle for One-Tailed and Two-Tailed Tests

For both one-tailed and two-tailed tests, we control the Type I error rate at 0.05. This means the rejection zones will sum to 5% of the distribution, ensuring the overall probability of a Type I error does not exceed 5%.

In practice, the rejection zone (5%) is on one side of the distribution for one-tailed tests, while for two-tailed tests the rejection zones (2.5% each are on both sides of the distribution.

> [!important] In practice, one-tailed tests are rarely used:
> 
> **if obtaining both very low or very high values would cause you to doubt H0, use a two-tailed test**

> Examples:
> 
> - A new tire-type lasts longer than an old tire-type: **can use 1-tailed test** because finding new < old doesn’t impact decision.
> - **Two-Tailed Test**: Testing if two conditions differ. Both higher and lower values are relevant.