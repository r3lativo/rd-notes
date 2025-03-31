---
Date: 2024-06-04
Reviewed: true
---
- [[#Two-way ANOVA between participants]]
    - [[#The logic]]
    - [[#Main vs interaction effects]]
    - [[#Possible results of two-way ANOVA]]
    - [[#Partitioning variance]]
    - [[#Related F-tests]]
    - [[#Constructing the variance estimates]]
        - [[#Within-cells variance estimate @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')sWC2s^2_{WC} sWC2​﻿]]
        - [[#Row-variance estimate @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')sR2s_R^2sR2​﻿]]
        - [[#Column-variance estimate]]
        - [[#Row times Column Variance Estimate]]
        - [[#Compare each F obtained to each F critical]]
    - [[#Summary]]
        - [[#Summary of formulas]]
        - [[#Summary of degrees of freedom @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')dfdfdf﻿]]
        - [[#Summary of F obtained]]
- [[#Repeated Measures (RM) ANOVA]]
    - [[#Partitioning of variance and relevant information]]
    - [[#Example: calorie intake during three seasons]]
    - [[#Constructing the variance estimates]]
        - [[#RM ANOVA @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')SSWSS_WSSW​﻿]]
        - [[#RM ANOVA @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')SSmodelSS_{model}SSmodel​﻿]]
        - [[#RM ANOVA @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')SSerrorSS_{error}SSerror​﻿]]
        - [[#RM ANOVA Population variance estimates]]

---

# Two-way ANOVA between participants

![[Untitled 24.png|Untitled 24.png]]

### The logic

A **factorial experiment** quantifies the effects of two or more factors. The resulting _treatments_ are combinations of the levels of the factors.

> [!important] A two-way ANOVA crosses
> 
> **two factors with multiple levels.**

In the simplest case, we have two factors each with two levels: a total of four possible combinations.

> Example: Does the speed of reading text (our Independent Variable IV) depend on whether it is about (1) narrative or scientific text, and (2) whether the text is read in the morning or in the evening?
> 
> In this case we have:
> 
> - Factor 1: reading hour
> - Factor 2: type of text
> 
> Let’s imagine we have participants randomly sampled and randomly assigned to 4 groups. Our table will look like:
> 
> $$\begin{array}{|c|c|}  
> \hline  
> \text{{}} & \text{Time of day} \\  
> \hline  
> \text{Text type} & \begin{array}{c|c}  
> Mn & En \\ \hline  
> Ms & Es  
> \end{array} \\  
> \hline  
> \end{array}$$
> 
> Where $M, E$ are Morning and Evening respectively, and $n, s$ are narrative and scientific respectively.

### Main vs interaction effects

The 2x2 ANOVA allows to answer three different questions:

1. Does Factor A have an effect independently of B?
2. Does Factor B have an effect independently of A ?
3. Does the impact of one factor depend on levels of the other?

The first two questions could be addressed also by the one-way ANOVA, regarding the ==**main effects**== of factor A (averaged over the levels of factor B) and of factor B (averaged over the levels of factor A).

> [!important] **The 2x2 ANOVA specifically allows to answer the third question about the**
> 
> ==**interaction effect**== which occurs when the effect of one factor depends on the levels of the other factor.

The main effects of a factor can be better understood by relating to **collapsing** one effect onto another: for example, we could take the factor of time of the day and collapse it onto the factor of type of text (ignoring then whether it is a narrative or a scientific text) or vice versa. **The main effect of one factor ignores the levels of the other factors**.

The interaction effect instead is defined as the dependency of the effect of one factor on the other. In particular, this interaction is defined as the difference between differences. _Does the difference between reading narrative vs scientific in morning differ from the difference between reading narrative vs scientific in evening?_

Once these differences are computed, we verify whether the difference between these two differences is stable or variable in relation to the levels of the factors. In practice, we look at whether these two differences are equal or not.

> [!important] The main advantage of the two-way ANOVA is that it allows to do many experiments in a single design and to calculate the interactions between factors.

### Possible results of two-way ANOVA

There could be different possible combinations of results after a two-way ANOVA (2x2):

1. No significant effect (neither main nor interaction)
2. Only one or two main effects
3. Only an interaction effect
4. One or two main effects and an interaction.

### Partitioning variance

While in one-way ANOVA we have two terms (the independent estimates of the population variance, namely $s^2_W$ and $s^2_B$), here we have **four types of variance that estimate the variance of the null hypothesis population:**

$$\large s^2_{WC} \quad s^2_R \quad s^2_C \quad s^2_{RC}$$

Looking back at our table can be helpful now:

We’ve organized statistics in a 2x2 matrix for which the factor ’text type’ varies across  
the rows and the factor ’time of day’ varies across the columns.  

> [!important] We therefore call ’
> 
> **text type**’ the **row factor** and ’**time of day**’ the **column factor**.

$$\begin{array}{|c|c|}  
\hline  
\text{{}} & \text{Time of day} \\  
\hline  
\text{Text type} & \begin{array}{c|c}  
Mn & En \\ \hline  
Ms & Es  
\end{array} \\  
\hline  
\end{array}$$

1. $s^2_{WC}$ is **the variance estimated within each treatment/condition.** _(Variance within the cells.)_
2. $s^2_R$ is the **Row variance estimate**, sensitive to differences in the row mean. _(Variance in the row collapsing across the columns - narrative vs. scientific.)_
    1. It is similar to estimate of sum of squares between $s^2_B$ in one-way ANOVA: we have a mean of one group and a mean of the other group and we estimate how far they are.
3. $s^2_C$ is the **column variance estimate**, sensitive to differences in column means. _(Variance in the column collapsing across the rows (morning vs. evening.)_
4. $s^2_{RC}$ is the **row by column variance estimate**, for interaction.

> [!important] All of these are
> 
> ==**independent**== **estimates of the population variance**.

### Related F-tests

This leads to three related F-tests that we compute in the factorial design:

$$\large  
F_{R} = \frac{s^2_R}{s^2_{WC} }  
\quad  
F_{C} = \frac{s^2_C}{s^2_{WC} }  
\quad  
F_{RC} = \frac{s^2_{RC}}{s^2_{WC} }$$

We have three obtained F-values; **the first two target the main effect, while the third one targets the interaction between factors.**

## Constructing the variance estimates

Let’s say we work with this data:

||**Morning, narrative**|**Morning, scientific**|**Evening, narrative**|**Evening, scientific**|
|---|---|---|---|---|
||1|4|6|8|
||7|12|6|5|
||9|5|2|5|
||4|8|8|6|
||5|6|6|9|
||6|6|6|11|
||2|8|2|7|
||5|6|5|9|
||1|9|9|7|
|**Mean**|**4.4444**|**7.1111**|**5.5556**|**7.4444**|

We’ve organized statistics in a 2x2 matrix for which the factor ’text type’ varies across  
the rows and the factor ’time of day’ varies across the columns.  

> [!important] We therefore call ’
> 
> **text type**’ the **row factor** and ’**time of day**’ the **column factor**.

$$\begin{array}{|c|c|}  
\hline  
\bold{{}} & \text{Time of day} \\  
\hline  
\text{Text type} & \begin{array}{c|c}  
Mn & En \\ \hline  
Ms & Es  
\end{array} \\  
\hline  
\end{array}  
\Rarr  
\begin{array}{|c|c|}  
\hline  
\bold{Means} & \text{Time of day} \\  
\hline  
\text{Text type} & \begin{array}{c|c}  
4.4444 & 5.5556 \\ \hline  
7.1111 & 7.4444  
\end{array} \\  
\hline  
\end{array}$$

We will have:

- $i$ for cell in row $r$
- $j$ for cell in column $c$
- $X$ for cell variable
- $\overline{X}$ for mean cell variable (of row or column)
- $\overline{\overline{X}}$ for grand mean (total mean)

### Within-cells variance estimate $s^2_{WC}$

> [!important] Axiom:
> 
> **The variance within each cell is not impacted by the IV.** This is why we use it as a standard for comparison.

> [!important] The Within-cells variance estimate
> 
> $s^2_{WC}$ is calculated by the ratio of the sum of squared deviation within cell $SS_{WC}$ over the degrees of freedom within cell $df_{WC}$.
> 
> $$s^2_{WC} =  
> \frac{SS_{WC} }{df_{WC} }$$

We first want to calculate the **sum of squared deviation within cell** $SS_{WC}$**,** which is the sum of squared deviation of each cell from the mean of the cel**l** that it belongs to. **We’ll get four** $SS_{WC}$ **in this case,** as we have a 2x2 table.

$$SS_{WC} = \sum_i^r \sum_{j}^{c} (X_{ij} - \overline{X}_{ij})^2$$

> [!important] **Why is**
> 
> $\red{\overline{X}_{i}}$ **also a mean?** If it’s just a cell, shouldn’t it be a simple value like in the one-factor ANOVA? No, since here in each cell we have **the mean of all the participants for that precise condition** (for example, for the $Mn$ condition).

For our example, we will have:

$$\begin{array}{|c|c|}  
\hline  
SS_{WC} & \text{Time of day} \\  
\hline  
\text{Text type} & \begin{array}{c|c}  
60.2222 & 44.2222 \\ \hline  
46.8889 & 32.2222  
\end{array} \\  
\hline  
\end{array}$$

Then we Determine the **degrees of freedom within,** $df_{WC}$, by subtracting the number of groups from the total number of observations.

$$df_{WC} = N - r \times c$$

So the final formula for the within-cell variance estimate can be written as:

$$s^2_{WC} =  
\frac{SS_{WC} }{df_{WC} }  
=  
\frac{\sum_i^r \sum_{j}^{c} (X_{ij} - \overline{X}_{ij})^2}{N - r \times c}$$

### Row-variance estimate $s_R^2$

Here we want to collapse (merge) across columns to obtain one group per row.

1. Calculate by distance between row mean and global mean, then multiply by observation per row
2. Determine the degrees of freedom between row
3. Divide $SS_R$ by $df_R$ to get the between row variance estimate, $s^2_R$.

So the final formula for the between row variance estimate can be written as:

$$s^2_R =  
\frac{SS_R}{df_R}  
=  
\frac  
{\sum_{i=1}^r n_i \times  
(\overline{X}_{i} - \overline{\overline{X}})^2}  
{r-1}$$

### Column-variance estimate

Compute exactly as for row-variance, but now averaging over the rows, and considering each column as single group

$$s^2_C = \frac{SS_C}{df_C} = \frac  
{\sum_{j=1}^c n_j \times  
(\overline{X}_{j} - \overline{\overline{X}})^2}  
{c-1}$$

### Row times Column Variance Estimate

> [!important] The
> 
> **Row times Column Variance Estimate** is quantified by **the distance of each treatment cell from the Grand mean**, ==after that the variability due to factors A and B has been removed==.

$$\begin{array}{|c|c|}  
\hline  
\text{{}} & \text{Time of day} \\  
\hline  
\text{Text type} & \begin{array}{c|c}  
Mn & En \\ \hline  
Ms & Es  
\end{array} \\  
\hline  
\end{array}$$

1. Calculate the Sum of Squares Row by Column $SS_{RC}$:
    
    $$SS_{RC} = n_{cell11} \times (\overline{X}_{cell11} - \overline{\overline{X}})^2 + n_{cell12} \times (\overline{X}_{cell12} - \overline{\overline{X}})^2 + \dots + n_{cellrc} \times (\overline{X}_{cellrc} - \overline{\overline{X}})^2 \blue{- SS_R - SS_C}$$
    
    We can rewrite it as:
    

$$SS_{RC} =  
\LARGE(  
\normalsize  
\sum_{i=1}^{r} \sum_{j=1}^{c} \orange n_{ij} \times(\overline{X}_{ij} - \overline{\overline{X}})^2  
\LARGE)  
\normalsize  
\blue{- SS_R - SS_C}$$

> [!important] remember that
> 
> $\orange n$ will vary depending on group size!

1. The degrees of freedom here are:

$$df_{RC} = (r-1)\times(c-1)$$

1. Divide to get the row by column variance estimate:
    
    $$s^2_{RC} = \frac{SS_{RC}}{df_{RC}} =  
    \frac  
    {  
    \LARGE(  
    \normalsize  
    \sum_{i=1}^{r} \sum_{j=1}^{c} n_{ij} \times(\overline{X}_{ij} - \overline{\overline{X}})^2  
    \LARGE)  
    \normalsize  
    \blue{- SS_R - SSC}  
    }  
    {(r-1)\times(c-1)}$$
    

### Compare each F obtained to each F critical

Compare each F obtained to each F critical.

## Summary

### Summary of formulas

$$s^2_{WC} =  
\frac{SS_{WC} }{df_{WC} }  
=  
\frac{\sum_i^r \sum_{j}^{c} (X_{ij} - \overline{X}_{ij})^2}{N - r \times c}$$

$$s^2_R =  
\frac{SS_R}{df_R}  
=  
\frac  
{\sum_{i}^r n_i \times  
(\overline{X}_{i} - \overline{\overline{X}})^2}  
{r-1}$$

$$s^2_{RC} = \frac{SS_{RC}}{df_{RC}} =  
\frac  
{  
\LARGE(  
\normalsize  
\sum_{i}^{r} \sum_{j}^{c} n_{ij} \times(\overline{X}_{ij} - \overline{\overline{X}})^2  
\LARGE)  
\normalsize  
\blue{- SS_R - SSC}  
}  
{(r-1)\times(c-1)}$$

### Summary of degrees of freedom $df$

||$df$|
|---|---|
|Within variance|$N- (r \times c)$|
|Row variance|$r-1$|
|Column variance|$c-1$|
|Row by Column variance|$(r-1)\times(c-1)$|
|Total|$N-1$|

### Summary of F obtained

$$\large  
F_{R} = \frac{s^2_R}{s^2_{WC} }  
\quad  
F_{C} = \frac{s^2_C}{s^2_{WC} }  
\quad  
F_{RC} = \frac{s^2_{RC}}{s^2_{WC} }$$

# Repeated Measures (RM) ANOVA

![[Untitled 1 13.png|Untitled 1 13.png]]

> [!important] Repeated Measures (RM) ANOVA is a method that allows us to evaluate
> 
> **patterns in data where multiple dependent measures are collected per person**. Each subject is tested more than one time **on all levels of each factor**.

It can be used when a factor has more than one level (discussed) and when multiple factors are crossed, all presented to each participant.

> [!important] In RM ANOVA
> 
> **we are** _**not**_ **interested in how participants differ between them (**$s^2_B$**)**: we ignore that variance. ==**We are interested in how they differ within (**====$s^2_W$====**)**==, that is to say, how they differ in the first and second test (since we are repeating test on them).

This is equivalent to saying we would mean normalize each participant's score so each participant had mean scores of 0. In this way they’ll have the same baseline and it’s easier to compare them.

### Partitioning of variance and relevant information

![[Untitled 2 13.png|Untitled 2 13.png]]

$SS_{model}$ is the sums of squared deviation of each model from the grand mean, and is exactly the source of variability that we want to remove from our analysis.

> [!important] _**Model**_
> 
> is here the **experimental condition**, or Independent Variable (IV). It’s the variance that can be attributed to the experiment.

For repeated measures ANOVA we do this by literally subtracting $SS_{model}$  
from $SS_W$ in the original independent measures ANOVA. We call this new sums of squared $SS_{error}$.

$$SS_{error} = SS_W - SS_{model}$$

So to recap:

1. $SS_B$. ==**Ignored**==
2. $SS_W$. ==**Informative**==. It relates to **the variance of each participant**. We partition it into:
    1. $SS_{model}$ (==**condition sensitive**==): **variance explained by the model**
    2. $SS_{error}$: **what we cannot account for by the model**

||$SS_B$|$SS_W$|$SS_{model}$|$SS_{error}$|
|---|---|---|---|---|
|$df$|$n-1$|$n \times (k-1)$|$k-1$|$(n-1) \times (k-1)$|

- $n$ = number of participants
- $k$ = number of conditions (or treatments)

> [!important] The relevant information is in
> 
> $SS_{model}$ and $SS_{error}$. On the null hypothesis, these should be equivalent.
> 
> $$H0: SS_{model} \approx SS_{error}$$

### Example: calorie intake during three seasons

|Participant|summer|winter|spring|mean($i$)|
|---|---|---|---|---|
|1|1700|2080|2000|**1926**|
|2|1700|1750|1600|**1683**|
|3|2000|2100|1600|**1900**|
|4|1500|1900|1800|**1733**|
|mean ($j$)|**1725**|**1957.5**|**1750**||

- $n$ denotes the number of subjects
- $k$ denotes the number of variables
- $X_{ij}$ the notes the score of subject $i$ on variable $j$
    - $X_{1,2} = 2080$
- $\overline{X}_{i.}$ denotes the mean for the subject $i$
    - $\overline{X}_{2.} = 1683$
- $\overline{X}_{.j}$ denotes the mean of variable $j$
    - $\overline{X}_{.3} = 1750$
- $\overline{\overline{X}}$ denotes the grand mean

## Constructing the variance estimates

### RM ANOVA $SS_W$

> [!important] For each subject
> 
> $i$ and condition (column) $j$, **sum the squared distances between each value related to that participant for each condition** $X_{ij}$ **and that subject's mean** $\overline{X}_i$.

$$SS_W = \sum_{i=1}^{n} \sum_{j=1}^{k} {({{X}_{ij}} - {\overline{X}_{i.}})^2}$$

Greater $SS_w$ indicates potential for larger effects of the Independent Variable IV.

> [!important] Ideally, and in the limit, all
> 
> $SS_W$ variance is attributable to the IV.

But this is not so, usually, and that is why we check how much of it is explicable by our model and how much not (the error).

### RM ANOVA $SS_{model}$

> [!important] For each condition (column)
> 
> $j$, **multiply the number of participants** $n$ **by the sum of the squared distances between the mean of the condition** (independently of the participant) $\overline{X}_j$ **and the grand mean** $\overline{\overline{X}}$.

$$SS_{model} = n \times \sum_{j=1}^k (\overline{X}_{.j} - \overline{\overline{X}})^2$$

> [!important] $n$
> 
> is small because the number of participants is the same for each condition (because in fact we are repeating measurements through them).

**These SS capture variances attributable to levels of the factor**, independent of deviations within participants.

> [!important] The multiplication is done only once, outside the sum!

### RM ANOVA $SS_{error}$

> [!important] The error variance is defined as
> 
> **whatever portion of the variance within participants that the model could not account for**. Or, the variance not explained by the IV.

$$SS_{error} = SS_W - SS_{model}$$

> [!important] Null Hypothesis: SS model and SS error should be similar.
> 
> $$H0: SS_{model} \approx SS_{error}$$

### RM ANOVA Population variance estimates

We work with two variance quantities:

- The estimated variance of the model
    
    - The $df$ of the model is the number of condition minus one
        
        > [!important] The model is
        > 
        > **condition sensitive**, so the degrees of freedom are taken from that.
        
    
    $$s^2_{model} = \frac{SS_{model}}{df_{model}} = \frac  
    {n \times \sum_{j=1}^k (\overline{X}_{.j} - \overline{\overline{X}})^2}  
    {k-1}$$
    
- The estimated variance of the error
    
    - The $df$ of the error is the number of participants minus one times the number of conditions minus one
    
    $$s^2_{error} = \frac{SS_{error}}{df_{error}} = \frac  
    {SS_W - SS_{model}}  
    {(n-1) \times (k-1)}$$
    
- Evaluate:
    
    $$F = \frac{s^2_{model}}{s^2_{error}}$$
    

> [!important] The higher the model and the lower the error, the more significant our result.