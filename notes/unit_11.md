---
Date: 2024-04-23
Reviewed: true
week_lec: 9
---
- [[#Recap about t-test]]
- [[#Family-wise Error]]
- [[#ANOVA (Analysis of Variance)]]
    - [[#The sampling distribution F]]
        - [[#The F test]]
        - [[#Generation of a Sampling Distribution of F]]
        - [[#Evaluating the F-Statistic]]
        - [[#Hypothesis testing in one-way ANOVA]]
    - [[#Variance partitions]]
        - [[#What variance is analyzed in an ANOVA?]]
        - [[#Within-groups variance estimate @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')sW2s^2_WsW2​﻿]]
        - [[#Between-groups variance estimate @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')sB2s^2_BsB2​﻿]]
        - [[#Formula summary]]
        - [[#The F-ratio in relation to SB and SW]]
        - [[#Compare F_obt to F_crit]]
        - [[#Assumptions underlying ANOVA]]
    - [[#Understanding via an example]]
    - [[#Practice Problem]]
    - [[#Effect Sizes]]
        - [[#Eta squared @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')η2\eta^2η2﻿]]
        - [[#Omega squared @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')ω2\omega^2ω2﻿]]
    - [[#After the ANOVA: pair-wise comparisons]]
        - [[#A-priori (pre-planned) comparisons]]
        - [[#Post-hoc comparisons]]

---
{% raw %}

### Recap about t-test

T-test derives its name from the fact that we obtain a t-value and check whether it is surprising or not. After obtaining a value, we test it: no difference between $\overline{x}_1$ and $\overline{x}_2$ leads to the null hypothesis.

$$t_{obt} =  
\frac  
{\overline{x}_1 - \overline{x}_2}  
{\sqrt{({{SS_1 + SS_2} \over{(n_1 - 1) + (n_2 - 1)}})({1\over{n_1}} + {1\over{n_2}})}}$$

**How do we evaluate if the t-test is compatible with the data obtained and/or surprising?** With the t-table, that tells you at which point the t-value is not so compatible with the null hypothesis.

**The actual reference is the t-distribution**, which tells us how probable it is to obtain each t-value.

> [!important] Null hypothesis as specifying a distribution against which you are comparing your statistics

**The context of application of t is two means**: this is a big limitation, as in some cases we want to test something more general, like when we have more than two conditions, and check whether there is a correlation.

### Family-wise Error

> [!important] You might think that we could just run a bunch of independent measures t-tests to see which pairs of mean are significantly different.
> 
> **The problem is the issue of ‘multiple comparisons’. I**f there are multiple tests, the probability of rejecting _one or more_ of these tests becomes greater than $α$.

If there are $k$ levels, then there are $m = \frac{k(k-1)}{2}$ possible pairs. If H0 is true, then the probability of failing to reject any test is $1 - \alpha$. With $m$ tests, the probability of failing to reject all of them (if they're independent) is $(1 - \alpha)^m$. So the probability of rejecting one or more is the opposite of failing rejecting all of them: $1 - (1 - \alpha)^m$.

> For example, if we let $\alpha = 0.05$ and we have 3 levels:
> 
> $$1 - (1 - \alpha)^m = 1 - (1 - 0.05)^3 = 0.1426$$
> 
> Which is way higher than $\alpha = 0.05$. This probability grows quickly with the number of levels. For an experiment with 10 levels:
> 
> $$1 - (1 - \alpha)^m = 1 - (1 - 0.05)^{10} = 0.4013$$

It’s just how randomness and chance work. The more tests, the less the significance. This is a ==false positive==.

Another problem could be a ==false negative==, where rather than each single test passing a threshold of x, …we have to have an adjusted threshold and we could end up with a threshold so low that none of our tests passes it.

> [!important] **ANOVA comes in our help**
> 
> in these cases.

# ANOVA (Analysis of Variance)

> [!important] The Analysis of Variance (ANOVA) is way of
> 
> **comparing all of the means to each other with one test**, thereby **avoiding familywise error**.

The drawback is that if there is a significant difference between the means, the test doesn’t tell you _how_ they are different. They all could be a little different from each other, or one of the means could be very different from the others.

## The sampling distribution F

### The F test

In hypothesis testing, we've learned about the Z and T tests, which focus on comparing means. The F test, and the Analysis of Variance (ANOVA), are different because they compare variances instead of means.

> [!important] The F test is used to
> 
> **compare two variances to see if they come from the same population**. Essentially, it measures if the variances of two samples are significantly different through a ratio:
> 
> $$F_{obt} = \frac{\text{Variance-estimate 1 of } \sigma^2}{\text{Variance-estimate 2 of } \sigma^2}$$
> 
> If the F ratio is _significantly different from 1_, it suggests that the variances are not equal, indicating a significant effect or difference.

> **Example:** Imagine you have two groups of plants, and you want to compare the variability in their heights after applying different fertilizers.
> 
> - **Group 1**: Fertilizer A
> - **Group 2**: Fertilizer B
> 
> You measure the heights and calculate the variances for each group:
> 
> - Variance of Group 1 (Fertilizer A): 4
> - Variance of Group 2 (Fertilizer B): 2
> 
> The F test ratio would be:
> 
> $$F_{obt} = \frac{4}{2} = 2$$
> 
> This $F_{obt}$ will be compared to an $F_{crit}$ (look at _Evaluating_ chapter).

### Generation of a Sampling Distribution of F

Creating fake data is a very powerful way of testing out your analysis methods. Sampling distribution of F can be generated empirically by:

1. Take samples $n_1$ and $n_2$ from the same population
2. For each of the samples’ variance $s^2$, estimate population variance $\sigma^2$
3. Calculate the F ratio $F_{obt} = \frac{\text{Variance-estimate 1 of } \sigma^2}{\text{Variance-estimate 2 of } \sigma^2}$
4. Repeat with all possible samples

> [!important] **Definition**
> 
> : the **sampling distribution of F** gives all the possible F values along with the $p(F)$ for each value, assuming sampling is random from the population.

### Evaluating the F-Statistic

As seen above, the F-statistic is calculated as the ratio of two variances. In the context of hypothesis testing, **we compare this statistic to a theoretical F-distribution** (so we will have an $F_{crit}$) to decide whether the observed ratio of variances is significant or not.

> [!important] The
> 
> **F-distribution is a family of curves** that depend on the degrees of freedom ($df$) for the numerator and the denominator variances. These curves **show the expected distribution of F-statistics under the null hypothesis.**

**The shape of the F-distribution** is determined by the **degrees of freedom** associated with the two variance estimates. Specifically, the numerator degrees of freedom ($df_1$) and the denominator degrees of freedom ($df_2$).

- $df_1$ (numerator): $n_1 - 1$
- $df_2$ (denominator): $n_2 - 1$

The steps to take to evaluate the F-statistic are:

1. **Calculate the F-Statistic**: Compute the ratio of the two variances.
2. **Determine Degrees of Freedom**: Identify the degrees of freedom for the numerator (df1) and the denominator (df2).
3. **Critical Value**: Find the critical value $F_{crit}$ from the F-distribution table using df1, df2, and the chosen significance level (e.g., 0.05).
4. **Compare**: Compare the obtained F-statistic $F_{obt}$ to the critical value $F_{crit}$:
    
    1. If the F-obtained is greater than the critical value, the null hypothesis is rejected.
    2. If the F-obtained is less than or equal to the critical value, we fail to reject the null hypothesis.
    
    $$F_{obt} > F_{crit} \rarr H1 \\  
    F_{obt} \le F_{crit} \rarr H0$$
    

> [!important] Depending on the sample size
> 
> $n$, you will evaluate different F-distributions.

The F-distribution looks like:

![[Untitled 27.png|Untitled 27.png]]

We can notice that:

1. **All values are positive** - that’s because we’re working with variances which are always positive.
2. It is **strongly positively skewed**.
3. **The mean of the distribution is around 1** - this should make sense, since this is the expected ratio if H0 is true.

**The F-distribution allows us to evaluate how surprising our obtained F-statistic is under the null hypothesis**. By comparing the F-obtained $F_{obt}$ to the critical value $F_{crit}$ from the F-distribution table, we can decide whether the observed variance ratio is significant or could have occurred by chance.

### Hypothesis testing in one-way ANOVA

> [!important] One-way ANOVA allows analyzing potential differences between
> 
> **two or more experimental conditions in a single test, based on the F-ratio.**

In one-way ANOVA there is _a single factor_ and levels are assigned to _independent groups $k$_. Participants are randomly sampled from population; then randomly assigned to groups. Often each group is assigned to a different level of IV.

> [!important] The ability to determine whether the groups differ or not
> 
> **allows for better control of** ==**Type-I error**== as compared to multiple pair-wise comparisons

- **H0**: the populations means of all conditions are equal throughout the groups $k$
- **H1**: it is not the case that the population means of all conditions are equal (roughly, there is **at least one pairwise difference**).

$$\text{Hypotheses}  
\begin{cases}  
H0: \mu_1 = \mu_2 = \mu_3 = \dots = \mu_k\\  
H1: \text{at least one mean differs from the others}  
\end{cases}$$

> [!important] In addition:
> 
> **independently of H0 or H1**, it is assumed that **the Independent Variables (IV) will only impact means** $\mu$ **values**, but not the variance of the populations $\sigma^2$:
> 
> $$\sigma^2_1 = \sigma^2_2 = \dots = \sigma^2_k$$

> [!important] The ANOVA evaluates if the Independent Variables (IV) impacts conditions means of 2+ conditions by
> 
> **evaluating the relative dispersion of the group means**.

## Variance partitions

As we have seen above, the one-factor ANOVA compares means across at least two groups, and **in particular that it is about comparing the variances** _**between**_ **the means across the groups to the mean of the variances** _**within**_ **each group.**

While this intuition is useful, it’s not a practical way to calculate F-statistics from your data, mostly because it doesn’t deal with differences in sample sizes between groups, and doesn’t help to understand more complicated experimental designs.

Here we will break down the concepts of sums-of-squared deviations from means.

### What variance is analyzed in an ANOVA?

> [!important] **Variability (**
> 
> $SS$ **- Sum of Squares)** is the raw measure of how much data points differ within and between groups.
> 
> **Variance Estimate (**$s^2$**)** is a standardized measure of this variability, used to compare within-group and between-group differences.
> 
> **ANOVA’s goal** is to determine if the variability between groups is greater than what we would expect by chance, using the F-statistic.

We have different independent groups (at least three groups to run an ANOVA): **the total variability in the entire data set is referred to as Total Sums of Squares** $SS_T$ and it is partitioned into:

1. **Variability** that exists on average **withing each of the groups** $SS_W$;
2. **Variability** that exists **between groups** $SS_B$.

$$SS_T = SS_W + SS_B$$

Moreover:

1. $SS_W$ is used to produce a **within-group variance estimate** $s^2_W$
2. $SS_B$ is used to produce a **between-group variance estimate** $s^2_B$

Both of these are treated as estimates of population variance. The principle:

> [!important] If the groups not differ and the division to groups is 'arbitrary', then the variance of values within each group should be similar to variance between groups. Evaluated by:
> 
> $$F_{obt} = \frac  
> {\text{Between-groups variance estimate }(s^2_B)}  
> {\text{Within-groups variance estimate }(s^2_W)}$$

> [!important] **Decision rule: If**
> 
> $F_{obt} \ge F_{crit}$**, reject H0**

### Within-groups variance estimate $s^2_W$

> [!important] Conceptually, select each group, compute sum of squared differences from mean, then compute weighted mean of all groups. This is one approach to estimating population variance. Produces weighted estimate of H0 population variance,
> 
> $\sigma^2$.

The **within-group variance estimate** $s^2_W$ is the computed as:

$$s^2_W = \frac  
{\red{SS_1 + SS_2 + \dots + SS_k}}  
{{(n_1-1) + (n_2-1) + \dots + (n_k-1)}}=  
\frac  
{\sum_i^k(X_i - \overline{X})^2}  
{N-k} = \frac{SS_W}{df_W}$$

The numerator is referred to as ==**SS-within**==; the denominator is the degrees of freedom $df$ for $s^2_W$.

$$df_W = N - k$$

Where:

- $k$ = number of groups
- $n_k$ = number of subjects in group $k$
- $SS_k$ = sum of squares of group $k$
- $N$ is the total number of participants ($n_1 + n_2 + \dots + n_k$)

### Between-groups variance estimate $s^2_B$

> [!important] The between-groups variance estimate
> 
> $s^2_B$ is a separate and independent estimate we derive for population variance. It is **conceptually independent of** $s^2_W$ **and based on dispersion (variance)** _**across groups**_**.**

How do we go from means of groups $\mu_k$ to estimate of variance $\sigma^2$? **We “reverse engineer” it.**

We know that **when population variance** $\sigma^2$ **is known**, the variance of the means ($\red{\sigma^2_{\overline{x}}}$) is: $\sigma^2/n$. Rearranging we can derive that: $\sigma^2 = n \times \red{\sigma^2_{\overline{x}}}$. So knowing the variance of means $\sigma^2_{\overline{x}}$ would have allowed determining the variance $\sigma^2$.

$$\sigma^2_{\overline{x}} = \sigma^2/n \quad \Rarr \quad \sigma^2 = n \times \red{\sigma^2_{\overline{x}}}$$

> [!important] We can
> 
> **estimate** the variance of means $\red{\sigma^2_{\overline{x}}}$ using the variance of the means of each of the $k$ groups (which according to H0 are sampled from the same population)!

We will use **the variance of the sampling distribution of the mean** $\blue{s^2_{\overline{x}}}$ to estimate the variance of means of the population $\red{\sigma^2_{\overline{x}}}$.

$$\blue{s^2_{\overline{x}}} = \frac  
{\Sigma(\overline{X} - \overline{X}_G)^2}  
{k - 1}$$

Where $\overline{X}_G$ (sometimes $\overline{\overline{X}}$) is the **grand mean**, that is the overall mean of all the scores combined.

Now we can construct a **between-groups estimate of the population variance** $s^2_B$:

$$s^2_B =  
\frac  
{\orange n \times \Sigma(\overline{X} - \overline{X}_G)^2}  
{k - 1}  
=  
\frac  
{{SS_B}}  
{df_B}$$

> [!important] When there are the same number of participants in each group, we can simplify the formula into
> 
> $s^2_B = \orange n \times \blue{s^2_{\overline{x}}}$.

### Formula summary

Within-group variance estimate:

$$s^2_W = \frac  
{\red{SS_1 + SS_2 + \dots + SS_k}}  
{{(n_1-1) + (n_2-1) + \dots + (n_k-1)}} =  
\frac  
{\sum_i^k(SS_{i})}  
{N-k} = \frac{SS_W}{df_W}$$

where:

- $k$ = number of groups
- $n$ = number of participants per group
- $N$ = total number of participants ($n_1 + n_2 + \dots + n_k$)
- $df_W = N - k$

---

Between-group variance estimate:

$$s^2_B =  
\frac  
{\orange n \times \Sigma(\overline{X} - \overline{X}_G)^2}  
{k - 1}  
=  
\frac  
{{SS_B}}  
{df_B}$$

where:

- $\overline{X}$ = mean of the group
- $\overline{X}_G$ = grand mean, overall mean of all the scores combined
- $df_B = k - 1$

---

**Summary of degrees of freedom**

- For $s^2_B, df_B = k - 1$
- For $s^2_W, df_W = N - k$
- For total sums of squares $SS_T, df_T = N-1$

> [!important] Notice that just like the sums of squares, the degrees of freedom also add up:
> 
> $$df_T = df_B + df_W \\  
> N - 1 = (k - 1) + (N - k)$$

### The F-ratio in relation to SB and SW

The impact of the Independent Variables (IV) should be on SB (increasing SS), not on SW) → **the greater the impact of IV, the greater F**.

$$F = \frac{s^2_B}{s^2_W}$$

### Compare F_obt to F_crit

In the end you compare the obtained F with the critical F using a table.

### Assumptions underlying ANOVA

The populations from which samples are drawn…

1. are **normally distributed;**
2. have **equal variances.**

> [!important] The ANOVA is relatively robust against violations of these assumptions.

This robustness means that ANOVA can get relatively precise estimates of $F_{obt}$ and particularly of the degrees of freedom $df$ associated with estimate for between $s^2_B$ and estimate for within $s^2_W$ even if these two assumptions are violated.

## Understanding via an example

You always had the intuition that students in the front are more ambitious and engaged, so perhaps they are doing better in school compared to the students that sit in the middle or back of the class. Let’s go to some survey data and see if there is a difference in the student’s GPA at your university when we **divide the class into groups based on where they like to sit in the classroom**.

- Our Dependent Variable (DV) is students’ GPA (ratio scale), that we observe and take means of. It is the outcome that we are measuring to see if it differs across the levels of the independent variable.
- Our Independent Variable (IV) is where students’ like to sit in class (nominal scale) which we use to group our students. It is referred to as a 'factor' in ANOVA, and **the different seating preferences are the levels of this factor.**

Here’s the table:

||**n**|**mean**|SD|SEM|
|---|---|---|---|---|
|**Near the front**|47|3.54|0.34|0.05|
|**In the middle**|71|3.51|0.30|0.04|
|**Toward the back**|32|3.35|0.43|0.08|

The means do differ, but it’s hard to see by how much compared to the standard errors. Let’s use this table to make a bar plot of the means with error bars set to ± one standard error of the mean:

![[Untitled 1 16.png|Untitled 1 16.png]]

If we call our dependent measure $X$, let $X_{ij}$ be the $i$-th data point in level $j$. Let $k$ be the number of levels, so $j$ will range $1$ to $k$. Let $n_j$ be the sample size for level $j$, so $i$ will range from $1$ to $n_j$.

Let $\overline{X}_j$ be the mean for level j, and let $\overline{\overline{X}}$ (or $\overline{X}_G$) be the grand mean, which is the mean of the entire data set.

Consider the plot below which shows a bar graph of our survey data, but with each data point shown individually. First, I’ve picked out a single data point, $\red{X_{ij}}$. The mean of the level that it came from, $\green{\overline{X}_j}$ and the grand mean, $\blue{\overline{\overline{X}}}$.

![[Untitled 2 15.png|Untitled 2 15.png]]

Consider how far our chosen data point is away from the grand mean: $X_{ij} - \overline{\overline{X}}$. We can separate this difference, or deviation into two parts:

$$\red{X_{ij}} - \blue{\overline{\overline{X}}} = (\red{X_{ij}} - \green{\overline{X}_j}) + ( \green{\overline{X}_j} - \blue{\overline{\overline{X}}})$$

> [!important] Read as: the deviation between
> 
> ==any data point== and ==the grand mean== is the sum of the deviation between ==that point== and ==the level’s mean==, and the deviation between ==the level’s mean== and ==the grand mean==.

- The first term is called _sums of squares total_. We assume that we’re summing across the whole data set.
- The second term is called _sums of squared within._ It’s called _within_ because it’s the sum of squared of the deviations of the mean _within_ each level.
- The last term is called _sums of squared between_. If you look at the inner sum, it’s the sum of $n_j$ values of the same thing for each level.

$$SS_T =  
{\displaystyle\sum_{ij}} (X_{ij} - \overline{\overline{X}})^2  
\\  
SS_W =  
{\displaystyle\sum_{ij}} (X_{ij} - \overline{X}_j)^2  
\\  
SS_B =  
{\displaystyle\sum_{j}} n_j( \overline{X}_j - \overline{\overline{X}})^2$$

Remember in the last chapter, where we discussed ANOVA as the ratio of the variance between groups and the variance within each group. The _between_ partition is a measure of the variability across the means, which will be part of the numerator of the F-statistic. The _within_ partition is a measure of the variability within each level and will contribute to the denominator of the F-statistic.

**All we need to do is divide each of these sums of squares by their degrees of freedom and we can get variances.**

||$df$|$SS$|Var $s^2$|$F$|
|---|---|---|---|---|
|Between|𝑘−1|${\displaystyle\sum_{j}} n_j( \overline{X}_j - \overline{\overline{X}})^2$|$\Large \frac{SS_B}{df_B}$|$\Large \frac{s^2_B}{s^2_W}$|
|Within|𝑁−𝑘|${\displaystyle\sum_{ij}} (X_{ij} - \overline{X}_j)^2$|$\Large \frac{SS_W}{df_W}$||
|Total|𝑁−1|${\displaystyle\sum_{ij}} (X_{ij} - \overline{\overline{X}})^2$|||

For our example:

||$df$|$SS$|Var $s^2$|$F$|**p-value**|
|---|---|---|---|---|---|
|Between|2|0.7922|0.3961|3.3343|0.0384|
|Within|147|17.4631|0.1188|||
|Total|149|18.2553||||

Using APA format and $α = 0.05$, we can say:

There is a significant difference between the GPAs at UW across the 3 levels of where students like to sit. F(2,147)=3.3343, p = 0.0384

## Practice Problem

TODO

  

## Effect Sizes

There are two ways of quantifying the effect sizes in the context of ANOVA.

- Eta squared $\eta^2$
- Omega squared $\omega^2$

### Eta squared $\eta^2$

Eta squared $\eta^2$ is an effect-size measure for one-way independent groups ANOVA. It is a more biased value than $\omega^2$, but it is easier to calculate: it is the proportion of the total sums of squares that is attributed to the difference between the means.

$$\eta^2 = \frac{SS_B}{SS_T}$$

It is a proportion that ranges between zero and one:

- If $\eta^2 = 0$, then $SS_B = 0$. This means that there is no variance between the means, which means that **all of our means are the same**.
- If $\eta^2 = 1$, then $SS_B = SS_T$, which means that $SS_W = 0$. That means that there is no variance within the groups, and all of the total variance is attributed to the variance between groups.

> [!important] $\eta^2$ is simple, commonly used, but **tends to overestimate effect size for larger number of groups**. That’s because $SS_B$ grows with the number of groups which is a problem because effect sizes shouldn’t depend on your experimental design.

### Omega squared $\omega^2$

Omega squared $\omega^2$ corrects for biases in $\eta^2$ by **taking into account the number of groups**. The formula isn’t very intuitive: it's the **variance between groups out of the total variance:**

$$\omega^2 = \frac{\sigma^2_B}{\sigma^2_B + \sigma^2_W} = \frac{\sigma^2_B}{\sigma^2_T}$$

Because we never know the _real_ population variances, we compute the **estimated omega** via the **estimated variances**:

$$\hat{\omega}^2 = \frac{SS_B - (k-1) \times s^2_W}{SS_T + s^2_W} = \frac{SS_B - df_B \times s^2_W}{SS_T + s^2_W}$$

We have **stratified levels of strength for effect sizes for ANOVAs** and very often to report just the F-values of the ANOVA will be not sufficient.

> [!important] APA standards today require - in addition to the P-value and the F-value - to report some indicators of the effect sizes, such as omega squared
> 
> $\omega^2$.

The typical interpretation of the omega squared $\omega^2$ values are:

$$\begin{array}{|c|c|}  
\hline  
\bold{{Effect\ Size}} & \bold{Description} \\  
\hline  
0.01 - 0.05 & \text{Small effect} \\  
\hline  
0.06 - 0.13 & \text{Medium effect} \\  
\hline  
\ge 0.14 & \text{Large effect} \\  
\hline  
\end{array}$$

The effect size in a way captures how effective your manipulation is.

## After the ANOVA: pair-wise comparisons

A significant F-value suggests that not all conditions are drawn from the same population. Given that we often have more than two conditions, **how do we determine which differ from each other?** With three conditions we already have 3 pair-wise tests, each with its own $\alpha = 0.05$ to account for ==**Type I errors**==**.**

But if you do three comparisons, as we have seen in the , you increase the probability of false positives to around 0.15.

> [!important] This is
> 
> **still inferential statistics** and we cannot limit ourselves to just describing the data. The way of approaching **Multiple comparisons** has traditionally been divided into whether those were specified **a-priori (pre-planned)** or conducted **post-hoc** after observing the data.

### A-priori (pre-planned) comparisons

**A-Priori tests are hypothesis tests that you planned on running before you started your experiment.** Since there are many possible tests we could make, setting aside a list of just a few specific a-priori tests lets us correct for a much lower familywise error rate.

> [!important] ANOVA tells you that there is a difference, but it does not tell you
> 
> _where_ it is!

We can merge our ANOVA results within a usual two-sample t-test, **substituting the estimate for population variance with the relevant estimate from the ANOVA.**

$$t_{obt} =  
\frac  
{\overline{x}_1 - \overline{x}_2}  
{\sqrt{\red{({{SS_1 + SS_2} \over{(n_1 - 1) + (n_2 - 1)}}})({1\over{n_1}} + {1\over{n_2}})}}$$

So ==**the red part**== in the t-test becomes for example the **withing group variance estimate** $s^2_W$:

$$t_{obt} =  
\frac  
{\overline{x}_1 - \overline{x}_2}  
{\sqrt{\red{s^2_W}({1\over{n_1}} + {1\over{n_2}})}}$$

> [!important] In this case, we
> 
> **evaluate** $t_{obt}$ **against** $t_{crit}$ **with** $df$**s related to** $s^2_W$**, which is** $df_W = N - k$**.**

### Post-hoc comparisons

**Post-hoc tests are hypothesis tests that you run after looking at your data.** For example, you might want to go back and see if there is a significant difference between the highest and lowest means. Under the null hypothesis, the probability of rejecting a test on the most extreme difference between means will be much greater than $α$**.** Or, perhaps we want to go crazy and compare all possible pairs of means.

- **Bonferroni correction** is the most conservative. It divides alpha $\alpha$ by number of tests; each test must pass a critical value matching alpha/number of tests level. It controls for family-wise or experiment- wise error rate at 0.05, meaning that the overall probability of the experiment, including all tests, should be below .05.
    
    > [!important] You multiply each p-value for the number of t-test, and you check whether the p-value is still significant
    > 
    > $$\text{each }p_{value} \times \text{number of total t-test}$$
    
- **Tukey's Honestly Significant Difference** is based on what kind of difference are surprising and what kind are not. It uses the **Q statistic**, which is a sampling distribution based on sampling $k$ samples and describing the difference between the highest and lowest means sampled.
    
    > [!important] This method is less conservative than Bonferroni and
    > 
    > **protects better against the** ==**Type II errors**==.

{% endraw %}
