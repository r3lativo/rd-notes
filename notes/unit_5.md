---
Date: 2024-03-19
Reviewed: true
week_lec: 5.2
---
- [[#The Normal Distribution]]
    - [[#Why is the Normal Curve important?]]
    - [[#Characteristics of Normal Curve]]
    - [[#68-95-99 rule]]
- [[#Standard Scores (Z-scores)]]
    - [[#Definition]]
    - [[#Why is z-score useful?]]
    - [[#Some features of Z-scores]]
    - [[#Example: Finding area (percentile) given Raw Score]]
    - [[#Looking up in a Z table explained]]
    - [[#Historically important skills]]
    - [[#From percentile to Score estimate via Z]]
- [[#Probability]]
- [[#Logical Probability]]
    - [[#First law of probability]]
        - [[#Probability of an event not occurring]]
        - [[#Disjoint events]]
        - [[#Not-Disjoint events]]
        - [[#Disjoint-ness]]
        - [[#Independence]]
    - [[#Second law (”Or”) rule for disjoint events]]
        - [[#The “OR” rule and exhaustive events]]
        - [[#Conditional probability]]
        - [[#The “AND” (Multiplication) rule of probabilities for independent events]]
        - [[#Example: Combining Multiplication and Addition]]
        - [[#Random Sampling]]
        - [[#Talking probabilistically about continuous distributions]]

---

## The Normal Distribution

> [!important] Objectives: what is a normal curve; what is a Z score; how to compute a Z score; how to use a Z score to compute the percentage of scores falling above, over or between two raw scores.

### Why is the Normal Curve important?

The Normal Curve holds significance for several reasons in behavioral research:

Many variables in behavioral research, such as height, weight, and intelligence, tend to follow a distribution that approximates the Normal Curve. This makes it a **frequently encountered distribution in data analysis**.

The (theoretical) distribution of mean values obtained from repeated sampling, known as the **sampling distribution of sample-means**, tends to follow a normal distribution. This distribution has valuable statistical properties, making it essential for various statistical tests and analyses.

The Normal Curve has several **useful statistical properties**, such as being symmetric and characterized by its mean and standard deviation. These properties facilitate statistical inference and hypothesis testing, making the Normal Curve a foundational concept in statistical analysis.

### Characteristics of Normal Curve

> [!important] ==**A Normal Curve is a bell-shaped theoretical distribution**==
> 
> : our data may approximate it, but never exactly match it.

It can be plotted if you insert many parameters:

$$Y = {N\over {\sqrt {2\pi\sigma} } }e^ {-(X-\mu) ^2/2\sigma^2}$$

Where:  
$Y$ = frequency of a given value of X*  
$X$ =any score in the distribution  
$\mu$ mean of the distribution  
$\sigma$ standard deviation of the distribution  
$N$ = total frequency of the distribution  
$\pi$ = a constant of 3.1416  
$e$ = a constant of 2.7183

Its inflection points are +/- 1$\sigma$ from $\mu$

The asymptotes (tail-ends) of a perfect curve never arrive at Y = 0

The point at which it is symmetrical is where the mean, median and mode fall

---

> [!important] In a Normal Curve,
> 
> **inflection points** (points on the curve where the direction of curvature changes) occur at distances of ±1 standard deviation ($\pm \sigma)$ from the mean ($\mu)$. _At these points, the curve changes from curving upwards to curving downwards, or vice versa._

![[Untitled 30.png|Untitled 30.png]]

The **asymptotes** (tails) of a (perfect) Normal Curve extend infinitely in both directions, approaching but never reaching the horizontal axis. _This means that extreme values are theoretically possible but become increasingly improbable as they move away from the center of the distribution._

The Normal Curve is **perfectly symmetrical around its center point**, which is also the **mean, median, and mode of the distribution**. _This symmetry indicates that the data is evenly distributed around the central value, with equal probabilities of observations falling on either side._

### **68-95-99 rule**

> [!important] For normal distributions, there is a certain proportion of values (area) that falls around the mean for every 1σ unit. Almost all values fall within ±3σ for a normal distribution.
> 
> **This distribution is described by the 68-95-99 rule.**

Cumulatively, we can see that:

- Within ±1 standard deviation from the mean, roughly 68.27% of the data falls.
- Within ±2 standard deviations from the mean, roughly 95.45% of the data falls.
- Within ±3 standard deviations from the mean, roughly 99.73% of the data falls.

![[Untitled 1 19.png|Untitled 1 19.png]]

34.13% of the area falls between μ, and μ + 1σ

==13.59% falls between [μ + 1σ] and [μ + 2σ]==

==2.15% falls between [μ + 2σ] and [μ + 3σ]==

> [!important] 34.13% +
> 
> ==13.59%== + ==2.15%== = 49.87%

Trying to compute it for both sides (±σ):  
(x2 → 68 + 27 + 4)  
**68**; 68 + 27 = **95**; 95 + 4 = **99**  
49.87% x 2 (the other side) = **99.73%**

> [!important] This rule provides a quick and reliable way to understand the distribution of values in a normal distribution, highlighting the concentration of data around the mean and the spread as we move further from the mean.

> **Example**: We have IQ data from 10,000 people. Its mean (μ) is 100 and standard deviation (σ) is 15. What IQ would have a person that is 1σ above the mean? 3σ? A person has an IQ of 120. How many σs is she/ he above the mean?  
>   
> **Resolution:** taking for granted that such data will plot a Normal Curve, we can use the rule above to answer the questions. A person that is 1σ above the mean, will have IQ 100+σ, which is 100+15, so 115. A person 3σ above the mean will then be 145. Instead, if a person has IQ 120, they will be around 1.33σ above the mean.

> Here another **example with male heights**. We know that the mean is at 70 inches, and that the standard deviation is of 4 inches. We can deduce that a person 1σ above the mean is 74 inches. We can also deduce that the probability of seeing someone with a height between 70 and 74 inches is 34% (area in blue) - more about probability later on.

![[Untitled 2 17.png|Untitled 2 17.png]]

> Here’s another example: we have IQ data from 10,000 people. It's mean $\mu$ = 100 and $\sigma$ = 16. **How can we use the normal distribution to calculate the Percentile Rank of a value such as 132?**

> [!important] **Percentile Rank**
> 
> : the percentage of scores below a given value. For example, if a score is at the 75th percentile, it means that 75% of the scores fall below it.

Given what we know, 132 is 2σ above the mean; meaning 47.72% of scores are between this value and the mean. **Hence, the Percentile Rank is** (50% + 47.74% =) **97.72**.

## Standard Scores (Z-scores)

> [!important]
> 
> Transforming a score into a unit of Standard Deviation is the core idea, because once we are in SD-units, we can calculate areas under the curve.

### Definition

> [!important] The
> 
> **Z-score** is a standardized score that represents **how many standard deviations a particular data point is from the mean of the distribution**. It's calculated by subtracting the mean from the data point and then dividing by the standard deviation:
> 
> $$z = \frac{X-\overline{X}}{s} \text{ for sample};  
> \quad  
> z = \frac{X-\mu}{\sigma} \text{ for population}$$

> For example, if a data point has a Z-score of 1, it means it's one standard deviation above the mean; a Z-score of -1 indicates it's one standard deviation below the mean.

> [!important] **Z-scores allow us to compare data points from different distributions on a common scale**
> 
> , making it easier to interpret and analyze data across various contexts. They also help identify outliers and understand the relative position of a data point within its distribution.

More precisely, a **Standard (Z) Score** is the transformed score that designates the distance of the score from the mean in units of standard deviation.

> Going back to our example: $z = \frac{X - \mu}{\sigma} = \frac{132-100}{16} = 2.00$  
> Where X is our value, $\mu$ is our mean, and $\sigma$ is our standard deviation. Our Z Score is then 2.

This is, of course, evident: if the mean is 100 and the SD is 16, a value of 132 will be (16x2) away from the mean! So, the Z Score is just a fancy name for this meaningful standard deviation.

> [!important] The conversion of
> 
> **raw score*** to Standard (Z) score is called **Score Transformation**. You might also see Normalization.

> [!important] A
> 
> **raw score** refers to the original, unprocessed value of a data point. It's the direct measurement or observation obtained from a study before any transformations or adjustments are applied.

### Why is z-score useful?

Z-scoring is valuable for several reasons. In the past, it enabled **quick determination of a score's percentile rank**. Nowadays, some tools and libraries let us just write `pnorm(132,100,16)` to swiftly output percentile values (in this case, `0.977`).

Z-scores also facilitate **comparisons across distributions**, e.g. for assessing differences like male versus female weightlifters. With just the mean and standard deviation, one can **easily evaluate how unusual an observation is** and **identify outliers**.

Moreover, when comparing scores measured on different scales with different means and standard deviations, **Z-scoring is crucial for accurately computing correlations**.

### Some features of Z-scores

> [!important] Z-scores preserve the shape of the original distribution but scale it linearly.
> 
> **Consequently, Z-normalization does not yield a normally-shaped distribution.**

Transforming a distribution to Z-scores results in a new distribution with a mean of 0 and a standard deviation of 1. This transformation yields results in units of standard deviation because **original scores can be seen as composed of the mean and a deviation component**.

> For instance, an original score 1σ above the mean (μ) becomes a Z-score of 1.
> 
> $$z = \frac{(\mu + 1\sigma) - \mu}{\sigma} = 1$$

### Example: Finding area (percentile) given Raw Score

Let’s stay in the realm of IQs. Given the raw score, find the area under the curve. What is the percentile rank of 135 given a population with mean of 100 and σ = 15?

You can convert to Z and look up in Z table:

$z = \frac{X - \mu}{\sigma} = \frac{135-100}{15} = \frac{35}{15} = 2.33$

`pnorm(135,100,15)` will output `0.9901` : our raw score is in the 99th percentile rank.

  

![[Untitled 3 14.png|Untitled 3 14.png]]

### Looking up in a Z table _explained_

> [!important] Looking up in a Z table involves
> 
> **finding the area under the standard normal curve associated with a particular Z-score**.

> [!important] **Z tables**
> 
> , also known as standard normal tables or Gaussian tables, **provide pre-calculated values of the cumulative distribution function (CDF) for the standard normal distribution**.

To use a Z table:

1. Locate the row corresponding to the integer part of the Z-score.
2. Locate the column corresponding to the second decimal place of the Z-score.
3. The value at the intersection of the row and column represents the area under the curve up to that Z-score.

> For example, if you have a Z-score of 1.96, you would locate the row for 1.9 and the column for 0.06 to find the corresponding value, which is approximately 0.9750. This value indicates that approximately 97.50% of the area under the standard normal curve lies below a Z-score of 1.96.

### Historically important skills

Assuming the distribution is normal, Identify the area under the curve for any score (between 80 and 120).

Apply Z-scoring formula, $z = {X-\mu \over{\sigma}}$, look up Z-value in Z-table.

`pnorm(120,100,15) - pnorm(80,100,15)` will output `0.818` .

![[Untitled 4 11.png|Untitled 4 11.png]]

### From percentile to Score estimate via Z

You can use the `norm.ppf()` function from the `scipy.stats` module in Python to calculate the Z-score corresponding to a given percentile.

For Z-distributions; mean = 0; SD = 1:

```Python
from scipy.stats import norm

# For Z-distributions:
mean=0; sd=1
# Percentiles for the Z-distribution (1%, 2,5%, and 5%)
percentiles = [0.01, 0.025, 0.05]

# Calculate the Z-scores corresponding to the percentiles
z_scores = [norm.ppf(p, loc=0, scale=1) for p in percentiles]

# Print the calculated Z-scores
print("Z-scores for the given percentiles:")
for p, z in zip(percentiles, z_scores):
    print(f"Percentile: {p}, Z-score: {z}")    

"""
OUTPUT
Z-scores for the given percentiles:
Percentile: 0.01, Z-score: -2.3263478740408408
Percentile: 0.025, Z-score: -1.9599639845400545
Percentile: 0.05, Z-score: -1.6448536269514729
"""
```

> [!important] This code snippet uses
> 
> `norm.ppf()` to calculate the Z-scores for the given percentiles and then uses the calculated Z-scores to estimate the actual scores corresponding to those percentiles. Adjust `mean` and `sd` according to your specific distribution parameters.

With these, we can estimate the actual scores that match those percentile. Example: what score corresponds to the lowest 2.5% and the top 5% of IQ scores?

Lowest 2.5%: $-1.96 = \frac{X-100}{16}\ [69]$

Top 5%: $1.64 = \frac{X-100}{16}\ [126]$

## Probability

> [!important] **Probability measures the likelihood of an event occurring, ranging from 0 to 1**
> 
> . It's often represented as decimal values rather than percentages. We can assess **probabilities subjectively** based on _feelings_ about events, **or calculate them logically**.

> [!important] **Logical probability**
> 
> applies when it is possible to calculate probability from logical principles. There is no need for observation. _E.g., what is the probability that a fair coin will come down on 'heads'?_

The Probability of occurrence of an event is calculated as:

$$p = {\text{Number of ways a desired outcome can occur} \over{\text{Total number of possible outcomes}}}$$

Examples include determining the chance of being chosen randomly from a group, selecting a specific item from a set of options, or identifying the likelihood of an attribute within a population.

# Logical Probability

When dealing with probability, dices are usually used as an example. A fair dice is a perfect theoretical dice, whose probability to land on any side is equal.

> Example: what is the probability that a fair dice will fall on the number 2? on an Even number? p(dice is 2) = 1/6; p(even) = 3/6 = 1/2

## First law of probability

> [!important] For any event A, its probability is between 0 and 1 inclusive.

$$\forall A, \ P(A): 0 \leq P(A) \leq 1$$

### Probability of an event not occurring

> [!important] The
> 
> **probability that an event does not occur** is 1 (certainty) minus the probability that it does occur.

$$P(\lnot A) = 1 - P(A)$$

Which also allows us to calculate P(A) as $P(A) = 1 - P(\lnot A)$, which is useful when it is easier to calculate the complement of the event than the event itself.

![[Untitled 5 8.png|Untitled 5 8.png]]

Space representation of the probability of A and not A

### Disjoint events

> [!important] If two events cannot occur at the same time they are called
> 
> **disjoint** or **mutually exclusive**. Their intersection is 0:

$$P(A \land B ) = 0 \\ P (A \cap B) = 0$$

> Examples of disjoint A/B events: a coin falling on either heads or tails.

![[Untitled 6 7.png|Untitled 6 7.png]]

### Not-Disjoint events

> [!important] If there is some event that would satisfy conditions for both A and B, so that the event can occur at the same time, the events are not disjoint

$$P (A \cap B ) > 0$$

> Non-disjoint events are for example:
> 
> - drawing a card that is a queen (A) and also a red suit (B)

![[Untitled 7 3.png|Untitled 7 3.png]]

### Disjoint-ness

> [!important] Two disjoint events
> 
> **are not independent** because one rules out the other.

Disjoint: $P(A \cap B) = 0$

Let's take the simplest situation possible as a counterexample. Let A be the event that a fair coin lands heads and let B the event that the coin lands tails.

$$A∩B=\empty ⟹ P(A∩B)=0≠P(A)P(B)=\frac12⋅\frac12$$

### Independence

> [!important] Two Independent events can occur together, but one does not provide information on the other. The occurrence of one has no effect on the probability of occurrence of the other. So:

$$P(A \cap B ) = P(A) * P(B) \\  
P(A | B) = P(A)$$

- The intersection between P(A) and P(B) is their multiplication.
- The probability of A given B is simply A, because they are independent events.

## Second law (”Or”) rule for disjoint events

The OR rule describes the probability of occurrence of any one of several possible events.

**For disjoint two-event case**: the probability of event A **_or_** event B occurring is given by their union, which is calculated adding up their probabilities.

$$P(A \lor B) = P(A \cup B) = P(A)+P(B)$$

> [!important] The general form of of the second law (OR rule)
> 
> **allows for non-disjoint events**

**For a two-even case**: The probability of event A or event B occurring is given by the probability of A plus the probability of B, minus their probability combined (intersection of events).

$$P(A \lor B) = P(A)+P(B) - P(A \cap B)$$

### The “OR” rule and exhaustive events

In scenarios where all possible events are known, such as dice or coin throws, we deal with exhaustive events. Examples of these domains are: dice throw; coin throw….

> [!important] A set of events is
> 
> **exhaustive if the set includes all of the possible events**.

When a set of events is **both exhaustive and mutually exclusive**, the sum of the individual probabilities of each event in the set must equal 1.

$$p(A) +p(B)+p(C)+ \dots +p(Z)=1.00$$

This principle is often applied when analyzing different categories of variables, allowing estimation of missing values based on the probabilities of other events.

> **Quiz time**: There are 4 blood types. P(0, B, AB) = (0.44, 0.10, 0.04) given. P(A)?  
> P(A) = 1 - [P(0) + P(B) + P(AB)] = 1 - (0.44 + 0.10 + 0.04) = 1 - 0.58 = **0.42**

### Conditional probability

> [!important] **For non-disjoint events A and B**
> 
> , the conditional probability of event A given that event B occurred, denoted as $P(A|B)$, can be calculated using the formula:
> 
> $$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

![[Untitled 8 3.png|Untitled 8 3.png]]

This formula represents the probability of both events A and B happening together divided by the probability of event B occurring. **It provides a way to quantify the likelihood of event A occurring under the condition that event B has already occurred.**

> [!important] **For independent events A and B**
> 
> , the probability that event A occurred given that event B occurred is indeed the same as the probability of event A alone. In other words:
> 
> $$P(A|B) = P(A)$$

This holds true because the occurrence of event B does not influence the probability of event A occurring, given that the events are independent. Therefore, the conditional probability of event A given event B is equal to the probability of event A alone.

### The “AND” (Multiplication) rule of probabilities for independent events

> [!important] The AND (Multiplication) rule of probabilities for independent events states that the probability of both event A and event B occurring is equal to the product of their individual probabilities. In other words, for independent events A and B:
> 
> $$P(A \cap B) = P(A) \times P(B)$$

This formula represents the joint probability of both events occurring simultaneously.

> For example, if you throw a coin twice, how likely is it that in both times it will fall on Heads?
> 
> $$P(HH)=0.5 \times 0.5 = 0.25$$
> 
> We can work out all possible events that could have occurred (image on the right).

![[Untitled 9 3.png|Untitled 9 3.png]]

> [!important] This rule applies
> 
> **when the occurrence of one event has no influence on the probability of the other event occurring**.

### Example: Combining Multiplication and Addition

Some cases will necessitate using both Multiplication and Addition rules.

To find the probability that the sum of the numbers on two fair dice equals 11, we can break down the problem into two options:

1. **Option1 -** Dice1: 6; Dice2: 5
2. **Option2 -** Dice1: 5; Dice2: 6

Within each option, the events (outcome of the first dice and outcome of the second dice) are independent. Therefore, the probability of each option can be calculated using the Multiplication rule: $P(\text{Option1}) = P(\text{Dice}1 = 6) \times P(\text{Dice}2 = 5)$

Same holds true for Option2.

> [!important] Both options are mutually exclusive, meaning that they cannot occur simultaneously. Therefore, we can use the Addition rule to find the total probability:

### Random Sampling

> [!important] A random sample is
> 
> **a subset of a population** chosen in a way that ensures every possible sample of a specific size has an **equal likelihood of being selected**. Additionally, **each member of the population has an equal chance of being included in the sample**.

> [!important] This approach supports
> 
> **generalization** and **representativeness** of the sample.

Conversely, non-representative samples, discussed in the context of sampling biases, deviate from these principles.

> The problem with taking such a random sample is the doability: taking a random sample from the entire Italian population can be very hard, as it is practically hard to reach to every single person and ensuring an equal likelihood. The most similar thing to this are the researches done by ISTAT (in Italy) - which however prove to be very expensive.

### Talking probabilistically about continuous distributions

Until now we discussed **assigning probability values to discrete events** or their combinations. When dealing with **continuous distributions***, we use the normal distribution to assign probabilities to specific values.

> [!important] In this context, "
> 
> **continuous distributions**" refer to probability distributions where the random variable can take on any value within a range. Unlike discrete distributions, which involve distinct, separate values, **continuous distributions involve an infinite number of possible values within an interval**. _Examples of continuous distributions include the normal distribution, uniform distribution, and exponential distribution._

To find the probability of an event A with a continuous distribution, we calculate the area under the curve corresponding to A and divide it by the total area under the curve.

$$p(A) = \frac{\text{Area under the curve corresponding to }A}{\text{Total area under the curve}}$$

> For example, if we're randomly sampling from a normal population with a **mean of 120** and a **standard deviation of 8**, and we want to find the **probability that a person will have a IQ of 127 or above**, we need to calculate the area under the curve for values greater than or equal to 127 and divide it by the total area under the curve. This will give us the probability of the event occurring.
> 
> We can use the cumulative distribution function (CDF) of the normal distribution to find this probability. In Python, we can use the `scipy.stats.norm.cdf()` function from the SciPy library. Let's perform the calculation in Python:
> 
> ```Python
> from scipy.stats import norm
> 
> # Parameters of the normal distribution
> mean = 120
> std_dev = 8
> 
> # Value of interest
> value_of_interest = 127
> 
> # Calculate the probability using the cumulative distribution function (CDF)
> probability = 1 - norm.cdf(value_of_interest, loc=mean, scale=std_dev)
> 
> print("Probability that a person will have a value of 127 or above:", probability)
> 
> """
> OUTPUT
> Probability that a person will have a value of 127 or above: 0.19078695285251068
> """
> ```