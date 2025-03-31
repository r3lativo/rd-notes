---
Date: 2024-06-04
Reviewed: true
---
- [[#Types of Association]]
    - [[#Categorical/Categorical association]]
    - [[#Continuous/Continuous association]]
        - [[#Linear correlations]]
        - [[#Non-linear associations]]
    - [[#Categorical/Continuous association]]
    - [[#Chi Squared @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')χ2\chi^2χ2﻿ Test]]
        - [[#Step 1: The Hypotheses]]
        - [[#Step 2: The null-hypothesis (aka, expected) distribution]]
        - [[#Step 3: Obtain difference between Observed and Expected Data]]
        - [[#Distribution of chi-squared @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')χ2\chi^2χ2﻿ stat]]
        - [[#Interpretation of chi-squared @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')χ2\chi^2χ2﻿ stat]]
        - [[#Requirements for conducting a ‘sane’ chi-squared @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')χ2\chi^2χ2﻿ test]]
        - [[#Effect Size related to a 2x2 chi-squared @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')χ2\chi^2χ2﻿ test]]
    - [[#Odds Ratio]]

---

# Types of Association

> [!important] Up until now we talked about difference -
> 
> **now we are interested into associations**.

> [!important] **Associations can exist between many types of variables**
> 
> . We start by considering: What is the association between variables? What is the first variable and the second variable?

Many tests are not directional, like correlation.

At the most generic level, **we can distinguish the type of association by looking at what the variables are:**

- **Categorical/Categorical**: _is gender associated with handedness?_
- **Categorical/Continuous**: _is gender associated with height? (Teso: is spam or not?)_
- **Continuous/Continuous**: _is income associated with self-rated happiness?_

In each of these cases, different methods exist for **quantifying the strength of associations**.

|Var 1|Var 2|Method|
|---|---|---|
|Categorical|Categorical|**Chi-Squared** $\chi^2$ **test**|
|Categorical|Continuous|**Regression**|
|Continuous|Continuous|**Pearson or Spearman correlation**|

We can think of the the context where we evaluate correlation in terms of **predictive information**: does knowing the value of one variable provide information - and consequently reduces uncertainty - about the value of another? This applies for all cases.

## Categorical/Categorical association

> [!important] Associations between levels of two categorical variables examine the
> 
> **joint occurrence of levels of the two variables.**

The simplest way in which to evaluate the association is when each of the two variables has two levels, like “gender” and “handedness”: we then go on and re-arrange the sample-data in a co-occurrence or **contingency table**.

||Right Handed|Left Handed|
|---|---|---|
|Male|40|15|
|Female|60|45|

> [!important] The co-occurrence table capture all the possible combination of the two variables.

## Continuous/Continuous association

It can be useful to think about what the association look like before talking about which method to apply to analyze them. **Always plot the data before any type of statistical test.**

> [!important] When dealing with two sets of continuous data, we find ourselves basically in two different possibilities of correlation:
> 
> **linear or non-linear.**

### Linear correlations

**Linear correlations** are captured by the **shape of a joint distribution**: which values on variable X tend to be associated with values on variable Y?

> [!important] When two variables are correlated (
> 
> $Y = ax +b$), an increase in X tends to be followed by a systematic increase/decrease in Y.

Plotting the relation between the two variables using scatter plot, we can describe each observation as a point (value of one variable and value of the other, x and y). **We have as many dots as observations.**

![[Untitled 29.png|Untitled 29.png]]

Linear correlations

The dot patterns create a cloud with a particular direction or shape based on the relation between the variables, and we are able to identify any possible association.

### Non-linear associations

Two continuous variables can have **non-linear associations**. Informally: specific ranges of (X, Y) variables tend to disproportionately occur together. The number above each figure shows the strength of this constraint.

![[Untitled 1 18.png|Untitled 1 18.png]]

Examples of linear and non-linear associations. The number above each figure shows the strength of this constraint.

## Categorical/Continuous association

When dealing with Categorical/Continuous associations, we usually **predict the categorical value**, and in the minimum case it has two levels. _For example, given some continuous data we predict if someone is male or female._

Given:

$$Y = \text{Categorical} \quad X = \text{Continuous}$$

**Logistic regression** lets us predict class probability ($Y$) from data ($X$). Practically, we may have more than one predictive variable.

## Chi Squared $\chi^2$ Test

> [!important] The aim of the Chi-squared
> 
> $\chi^2$ test is to **quantify the association between the levels of categorical variables**. Typically we have 2 variables with 2 levels, using a two-way table.

**Two-way (aka cross-tabulation) tables communicate counts**: the frequency of people/observations that present a certain combination of values of the two levels. **Each person/observation can contribute to only one cell in the two-way table.**

> [!important] For purposes of computation, beyond the raw co-occurrence counts, we also add
> 
> **row and column sums**.

||Right Handed|Left Handed||
|---|---|---|---|
|Male|40|15|55 (35%)|
|Female|60|45|105 (67%)|
||100 (63%)|60 (37%)|**160 (total)**|

### Step 1: The Hypotheses

Using our example in which we compare gender and handedness, we will have:

- H0: there is **no significant association** between a person’s gender and handedness
    - the distribution of males over the right-/left-handed cells is the same as the distribution of females over those same cells.
- H1: there is a significant association between gender and handedness

$$\begin{cases}  
H0: & \text{no significant association}  
\\  
H0: & \text{significant association}  
\end{cases}$$

### Step 2: The null-hypothesis (aka, expected) distribution

The **null hypothesis (joint) expected distribution** of the two variables indicates what the distribution would have been like if there was no association between the variables. That is, it presents theoretical counts if H0 is true.

> [!important] We know the marginal counts for each category (M/F, R/L).
> 
> **How do we get the expected counts?**

For example, assuming the proportion of left and right-handed is the same in males and females, **how many of males should be left handed**? We can answer this by multiplying the total males by the total left-handed divided the total people:

$$\frac{M_{tot} \times L_{tot}}{Total} =  
\frac{55 \times 60}{160} \approx 21$$

Going on with this process for each cell (so $\frac{M_{tot} \times R_{tot}}{Total} , \frac{F_{tot} \times L_{tot}}{Total} , \frac{F_{tot} \times R_{tot}}{Total}$) we can create a new table with the **expected counts based on H0:**

![[Untitled 2 16.png|Untitled 2 16.png]]

We should do it with proportions (so, $\frac{0.35 * 0.37}{1}$) but **working with raw values can be slightly easier**.

> [!important] There are many combinations of 4-cell
> 
> **values** consistent with the exact same **proportional marginals**.
> 
> ![[Untitled 3 13.png|Untitled 3 13.png]]

### Step 3: Obtain difference between Observed and Expected Data

The chi-squared $\chi^2$ is based on **quantifying the difference between our observed count and the expected count**. It’s computed by taking observation for each row and column, subtracting for each cell the the expected value $E$ from the observed value $O$, then squaring it and dividing for the expected value.

$$\chi^2 = \sum_i \sum_j \frac{(O_{ij} - E_{ij})^2}{E_{ij}}$$

Where:

- $O$ is Observed value
- $E$ is Expected value

> [!important] We get a single value for a chi-squared
> 
> $\chi^2$.

### Distribution of chi-squared $\chi^2$ stat

Just like the z and t distributions, the $\chi^2$ distribution has a known ‘parametric’ shape, and therefore has known probabilities and areas associated with it.

The chi-squared $\chi^2$ distributions are a family of distributions that take **only positive values** and are **skewed to the right**. A particular chi-squared distribution is specified by giving its degrees of freedom $df$.

![[Untitled 4 10.png|Untitled 4 10.png]]

- A $\chi^2$ value of 6 with a $df$ of 1 will be significant
- A $\chi^2$ value of 6 with a $df$ of 8 will _**not**_ be significant

> [!important] Notice how the shape of the distributions spread out and change shape with increasing degrees of freedom. This is because as we increase
> 
> $df$, and therefore the number of squared z-scores, the sum will on average increase too.

The chi-squared test for a two-way table with $r$ rows and $c$ columns uses critical values from the chi-square distribution with degrees of freedom;

$$df_{\chi^2} = (r-1)(c-1)$$

> [!important] Frequently,
> 
> $df = 1$ as most of the time we have a 2x2 test.

The **P-value** is the area under the density curve of this chi-square distribution to **the right of the value of the test statistic**.

> [!important] Whether or not our
> 
> $\chi^2$ will be surprising depends on the $df$s.

This makes sense, as if we look back at the equation, we see that **the more cells we have, the larger the chi-squared** $\chi^2$ **is going to be**. There is nothing that normalizes the number of cells. Larger degrees of freedom are potentially associated with larger chi-squared values.

### Interpretation of chi-squared $\chi^2$ stat

Interpretation is not straightforward:

- **For 2x2 cases**, we can evaluate the **Odds Ratio** (later on);
- **For tables with more cells**, we can compute the deviation of each cell from the expected values and see whether there are cells that depart more strongly than others from the expected values (or whether they are as we expect them to be).

### Requirements for conducting a ‘sane’ chi-squared $\chi^2$ test

The chi-squared test is an approximate method: **larger counts produce more accurate results**. Therefore, it is important to check that the counts are large enough to result in a trustworthy p-value. Fortunately, **the chi-squared approximation is still accurate for very modest counts**.

> [!important] Recommended rule of thumb:
> 
> **all four expected counts in a 2x2 table should be 5 or greater.**

### Effect Size related to a 2x2 chi-squared $\chi^2$ test

The chi-squared can be used for any tabled data (again: a person's data impacts values of only one cell). **It shows an association between two variables and used for hypothesis testing**.

The chi-squared does not describe how strong the association is. For this, we need a measure of effect size: The ==**Odds Ratio**==. It is easily applied to 2x2 tables (though can be extended to more; _**not discussed**_).

## Odds Ratio

> [!important] The Odds of something happening is
> 
> **how much more is it likely to happen vs. not happen.**

$$\text{Odds ratio} = \frac{P(x)}{1-P(x)}$$

So, if $x$ has a probability of happening of $P(x) = 0.6$, the Odds of $x$ are:

$$⁍$$

The term is often used when the probability of events ‘occurring’, or ‘success’, is quantified:

- Odds = P(event) / P(not event)
- Odds = P(success) / P(failure)

> [!important] In practice, we just count frequency of success/failure in sample and divide one by the other.

||Right Handed|Left Handed||
|---|---|---|---|
|Male|40|15|55 (35%)|
|Female|60|45|105 (67%)|
||100 (63%)|60 (37%)|**160 (total)**|

Taking back our table from before, we might ask ourselves **what are the odds of being Right Handed if one is Male, or Female, and how different these odds are:**

- Odd RH male = 40/15 = 2.66
- Odd RH female = 60/45 = 1.33
- **The** ==**odds ratio (OR): 2.66 / 1.33 = 2**==

> [!important] In our sample, the odds of being right-handed are twice as large for Male as they are for Females.

It’s evident that **if the Odds Ratio (OR) is equal to 1**, then the relative likelihood of the event is equivalent in both circumstances, and we say that **there is no dependency between the circumstance** (male/female) **and the variable of interest** (RH/LH)**.**

**How do we know if OR departs significantly from 1?** There are two ways:

1. Creating a Confidence Interval for the OR. If the CI includes 1, there’s nothing very interesting here. $95\%\ CI = e^{[\ln(OR) \pm 1.96 \sqrt{(\frac1a + \frac1b+ \frac1c + \frac1d)}]}$
2. Using the **Fisher Exact Test**, which let us set up **specific hypotheses about the OR** (two-sided or one-sided) and provides better flexibility.