---
Date: 2024-06-10
Reviewed: true
---
- [[#Correlation and Regression]]
    - [[#What is a Correlation]]
    - [[#Correlation does not imply Causation]]
        - [[#Case 1: Mediating / Omitted Variables]]
        - [[#Case 2: Sampling Bias]]
    - [[#Quantify Correlations?]]
        - [[#Contexts of applications]]
        - [[#A linear function]]
    - [[#Regression vs. Correlation]]
    - [[#Descriptive Stats: Regression and Correlation]]
        - [[#Develop the example]]
        - [[#Linear Regression Equation]]
        - [[#Defining a good prediction]]
        - [[#Getting at @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')bbb﻿ in the regression equation]]
        - [[#Relation between r and MSE]]
        - [[#Interpreting the Correlation Coefficient in context of Regression]]
        - [[#When to use linear regression instead of ANOVA or t-test?]]
        - [[#Linear vs. non-linear problems]]
        - [[#Relation between @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')rrr﻿ and proportion of variance accounted by linear regression]]
        - [[#Regression when using raw scores]]
    - [[#Regression from Perspectives of Sums of Squares]]
        - [[#Elaboration: @import url('https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.16.9/katex.min.css')SSTSSTSST﻿]]
    - [[#Using Regression and Correlation]]
        - [[#Further consideration for using Regression]]
    - [[#Regression Analysis]]
        - [[#Sanity Checks]]
        - [[#Significance of Beta (β)]]
        - [[#Quantifying our certainty in beta]]

---

# Correlation and Regression

You’ll often hear the words ‘correlation’ and ‘regression’ in the same context. They are essentially the same thing - both are about the relation between one or more independent variables and a dependent variable.

> _Prof’s POV_: One of the main problem with regression is that is seems very complicated and remote but it should be he tool that we use most often - lack of knowledge could lead to using t-test and ANOVA more than required.

## What is a Correlation

> [!important] Correlation is
> 
> **any statistical relationship**, random or not, **between two random variables**.

In the broader sense, it is any statistical association, though it is commonly regarded as the degree to which a pair of variables are ==**linearly related**==. In general, when we talk about correlation we talk about the relation between variable Y and X that can be described roughly as following a straight line.

> Familiar examples of dependent phenomena include the correlation between the Hight of parents and their Children.

## Correlation does not imply Causation

> [!important] There is no direct inference of the fact that we have correlation AND causation.

In some cases, variable X (our Independent Variable that we control) causes changes in variable Y (Dependent Variable that we observe): this is the essence of **empirical experiments**.

> [!important] In an experiment, we are trying to establish a correlation between the two variables.

**In real life situations, inferring causation is more difficult**. Sometimes we can observe some event looking for correlated variables and establish causation by looking at temporal occurrences and co-occurrences.

> [!important] Partly due to all of this, people say that
> 
> **observing a correlation is** _**necessary**_ **but** _**not sufficient**_ **for inferring Causation.**

We infer that:

- We can have correlated variables that are not causing each other
- **If there is a causal relationship in the world, it is also manifested in a correlation.**

### Case 1: Mediating / Omitted Variables

In some cases, Variables X and Y - let’s say, Grades and Happiness - show a strong correlation/association, **but the relationship is in reality mediated by a hidden variable**.

![[Untitled 23.png|Untitled 23.png]]

It could be that higher grades (X) do not directly increase happiness (Y), but instead increase Self-Esteem (A), that in turn increases happiness. Maybe increasing grades do not always work.

![[Untitled 1 12.png|Untitled 1 12.png]]

Let’s make a study about it: check whether receiving a high grade will make people more happy. If everyone takes 30/30 and happiness does not increases, the correlation is not there and could be mediated. We would have successfully broken the hidden association between Grades and Self-Esteem (A).

> [!important] **Structural equation modelling (**
> 
> [Structural equation modeling - Wikipedia](https://en.wikipedia.org/wiki/Structural_equation_modeling)) is what we may need if we find ourselves in such a situation.

> If you compute the correlation between: (X and A, A and Y, X and Y), how much do these explain the correlation between X and Y? Almost all the correlation between X and Y is accounted for by how much X explains A and how much A explains Y.

### Case 2: Sampling Bias

We saw this in the example of a bilingual school associated to success on a math tests.

We said that there could be a third variable that could explain it, namely a higher Socio-Economical Status (SES), which will lead these kids to more stimuli, more demanding contexts, etc.

> [!important] Formally, the sampling bias is something that mediates the relationship between two variables and it is explainable by the choices made in taking our sample-population.

In our case, if the role of SES is removed, for example with random picking from the population (**random sampling**) and putting kids in the school or not (**random assignment**), we can actually remove this bias.

> [!important] Dealing with a bias will mean that we can see its influence on our variables.

## Quantify Correlations?

To this point we studied how to find evidence for statistical relations between variables using various statistical tests (t-test, ANOVA…). Our Y was categorical (group, condition) and our X was often continuous (grades, reading times).

> [!important] Correlation instead allows us to
> 
> **make a prediction about the value of Y from value of X**, and can be used when X is a continuous variable.

> Given a certain medical record, how likely is it that the person will develop a certain type of illness?

> [!important] Does knowing values of X reduce our uncertainty about values of Y? And if so, by how much?

### Contexts of applications

X and Y are continuous numerical variables. For each X score there is a distribution of Y scores.

> [!important] We are interested in one of three questions:
> 
> 1. Is there a statistical **relationship** that allows predicting values of Y from X?
> 2. How **strong** is the statistical relationship?
> 3. Can we formulate a **rule** for predicting Y from X? How good is the rule? Can it **generalize**?

> Think about Neural Networks: they look for correlations. they see if based on something X they can assign a value a label Y (e.g.: understand if a brain is of a male of female from brain scans, or decoding letters from images…)

> [!important] **Generalize**
> 
> : I want to prove that I understood something about the world. I can do so by starting a completely new observation (in ML, out of the training data) and see if my rule of correlation is able to find patterns in the wild.

**This is becoming the founding value to see whether a correlation is valid or not.**

> [!important] Generalizing here refers to
> 
> **internal validity**: do you have enough data to develop a rule that applies also outside of your sample?

### A linear function

> [!important] When pairs of X,Y values have a relationship that can be plotted as a straight line, this is called a
> 
> **linear function** (Y is a linear function of X).

$$y = bx + a$$

Where $b$ and $a$ are two constant numbers

## Regression vs. Correlation

Regression and correlations problems are two different approaches for studying linear relationships.

> [!important] ==**Regression**==
> 
> is the natural way **to evaluate the statistical relation between X and Y** where X is continuous. It is a natural extension of ANOVA where X is continuous, and (in psychology) X is an Independent Variable (IV). Very often, Y is continuous as well.

**Regression VS ANOVA**:

- Regression answers to what extent the relationship is linear.
- **ANOVA cares about** the sum of squares within and between (**whether the column means differs from each other**) but not if the relationship between the variable is linear.

Regression is a very good extension of ANOVA and opens the doors for running particular kinds of designs.

> [!important] ==**Correlation**==
> 
> : **there is no clear distinction between an IV and a DV**. I have two measure of variables but we do not control them. Since we do not control them, we don’t know their range! We do not know the upper and lower boundary.

> Typical application context: A sample of $n$ individuals is drawn, and each person represents a one specific combination of X, Y values. Correlation problems ask whether Y can be predicted from X or X predicted from Y using a linear rule. If the correlation is significant, this does not mean we think there is any impact of one variable on the other

> [!important] If the correlation is significant, this does not mean we think there is any impact of one variable on the other

> [!important] For practical purposes however,
> 
> **regression and correlation are sometimes used interchangeably and share some conceptual foundation**: descriptive stats and finding a linear rule are similar.

We use:

- Regression to predict
- Correlation to check whether X and Y variate together

## Descriptive Stats: Regression and Correlation

> Example: A teacher is interested in predicting relative performance in Bachelor's math class from high school grades.
> 
> - For each student the teacher has the mean high school grade in all math
> - At the end of course, the teacher wants to see what is the relation

To evaluate this

1. **Normalization**: we are interested in higher grades and o so in relative and not absolute values. We can normalize our x variables and our y variables into z-scores.
2. **Solve a Linear equation**: we try to solve a linear equation (function): $Z'(y) = b \times Z(x) + a$; 'b' and 'a' are constants
    1. Z’(y) I is the predicted Y score for a given X score. Z'(y) is the predicted Y score for a given X score.

> [!important] We are not trying to perfectly imitate our dataset: instead, solve the equation that best reflects the relation. This equation is called the
> 
> **linear regression equation**.

### Develop the example

We have 80 people, and we have the math grade in the bachelor and in high school.

|person|BA grade|HS grade|
|---|---|---|
|1|28|70|
|2|…|…|
|…|…|…|
|80|23|65|

Converting to Z score:

$$Z = \frac{X_i - \overline{X}}{\sigma}$$

We are going to get the **mean** of the BA, of the HS, of the standard deviation of BA, of the SD of the HS… we will plug these score into the above equation into the appropriate way.

Each column is going to be converted into z-values. They will have a mean of 0 and a SD of 1, (mathematical necessity).

> [!important] Z values above 0 will be higher than the mean, whatever column we find in! We basically converted these different grades into the same scale.

**Now we can ask ourselves: is it the case that people that have a z score above 0 in BA will also have such a z score in HS?** If so for most people, we can say that there is a pretty good consistency between these scores.

What would happen instead if those above…

||HS > 0|HS < 0|
|---|---|---|
|BA > 0|40|0|
|BA < 0|0|40|

Here we can see that there is strong evidence!!!

  

||HS > 0|HS < 0|
|---|---|---|
|BA > 0|20|20|
|BA < 0|20|20|

In such a situation instead we could say that there is no correlation in grades in BA or HS.

  

> [!important] But, in doing so we would
> 
> **lose some information** (the actual grades of each student).

### Linear Regression Equation

Because of this, we see if we can solve a **linear equation** (function):

$$z^{'}_y = bz_x+a$$

> [!important]
> 
> Connecting the dots from ML: $b$ will be the ‘slope’ and $a$ will be the crossing point on the y-axis. What changes here is that we have z-scores.

- $z^{'}_y$ is the predicted Y score for a given X score. In the TRUE data, a certain X score may be associated with more than one Y, but in this equation, each X score predicts only one Y score.
- **We are not trying to perfectly imitate our dataset**: instead, solve the equation that best reflects the relation. **We are looking for the best approximation**.

> Example: if the program of BA is the same of HS, and we say that people do not forget anything, they will have theoretically the same exact score. The linear equation will be perfect.

Of course this is not how the world works: this equation will not give us the exact state of things but it can go very close.

![[Untitled 2 12.png|Untitled 2 12.png]]

Horizontal/ Vertical lines: values for z(x) and z(y); the actual data

The line: indicates the ONLY values allowed according to Z'(y) from the regression equation.

> In our example, x-axis will be the HS grades, while the y-axis will be the BA grades. Our values will then show up on the graph as a scatter plot. To make it consistent to what we talked above, we also assume that we normalized everything into Z scores.

> [!important] The set of predicted values will be on a line, and the line will be our best approximation of the correlation existing between the x-axis and y-axis values. We are somehow
> 
> **compressing the original raw data into a line**, and it is a valuable concept that could help us generalize outside our training (talking in ML).

Of course even in the best case our line won’t spot each and every single value - mainly because they do not form a line. This is why the concept of **Error** also comes in hand. For each $z_x$, the error is the distance between $z_y$ and $z^{'}_y$ - that is to say between the real $y$ and the predicted $\hat y$.

$$e = (z_y - z'_y)$$

The error will tell us how good our prediction is. So **the smaller the error, the better the solution** - because there are multiple solutions.

> Our line here will reflect the correlation between BA and HS grades. If this function really predicts this correlation, we could use it to accept or refuse people in an MA based on it (for example).

> [!important] But how do we know whether it really works outside of our data? We have to test it with new data and see if it generalize good enough: this is called
> 
> **out of sample generalization**.

### Defining a good prediction

There are many way to define a a regression equation that “predicts well”, and in any case here we take in consideration the distance between $y$ and predicted $\hat y$. We care about:

- how often it exactly predicts z(y)
- the mean of the error distances (absolute value of errors)
- the ==**Mean Squared Error (MSE)**==

> [!important] Different definitions of “best prediction” will produce different regression lines that minimize errors defined that way. The criterion we use is the
> 
> **least squares criterion**: the average squared error in prediction should be as small as possible.

If we have $N$ individuals (or observations), rotating over each observation $i$, we want to find a line that minimizes this expression: this is the **Mean Squared Error (MSE).**

$$MSE = \frac{\Sigma_i(Z'_{Yi}-Z_{Yi})^2}{N}$$

### Getting at $b$ in the regression equation

> [!important] $b$
> 
> **is what we use to minimize the error** in order to have the best results - also known as _the slope_.

If predicting z-scores, the regression equation will be simple, as $a$ will end up being 0 (that is, the intercept of the line will be on the origin 0,0). This is because a regression must pass through the point which is the mean of the 2 variables)

$$⁍$$

> [!important] So we are trying to minimize the
> 
> **multiplier of x**, whatever it may be called

Using different $b$ values will produce different magnitudes of square errors. The value of $b$ that minimizes the least squares error is the average of products of standard scores for the datasets.

> [!important] $b$
> 
> is higher when $\pm z_y$ appear with $\pm z_x$. i.e., a lot of matches will lead to same signs. **The more you have agreement in signs, the higher** $b$ **becomes, and the better the equation.**

The point here is that we could compute b just by using Y and X values.

> [!important] **When X and Y are Z normalized**
> 
> as here, the (best) $b$ is also, mathematically, the ==**correlation coefficient**== ==$r_{xy}$==**,** which we'll discuss later.
> 
> $$b = r_{XY}$$

For this reason, we can rewrite the formula as:

$$Z_y' = r_{XY}Z_X$$

where $r_{XY}$ is the Pearson correlation between x and y.

### Relation between r and MSE

The **Mean Squared Error (MSE) is at its smallest when** $b$ **equals** $r$ - moreover, at that point MSE will be equal to $1-r^2$.

$$\text{if } b = r \rarr min(MSE) = 1-r^2$$

> [!important] We therefore say that taking
> 
> $b = r$ gives the lowest/least MSE in linear prediction **for standard scores**.

The (standard) error - that is, with minimal MSE obtained by a b - captures how well we predict Z(y) from Z(x) and it is expressed as:

$$S_{ZyZx} = \sqrt{1-r^2_{XY}}$$

Read in plain English as: ==the sample standard error of estimate for predicting standard scores is the square root of one minus the squared correlation coefficient== ==$r$== ==of== ==$XY$====.==

> [!important] The larger
> 
> $r$, the smaller the std. err. of the estimate. The variance of the estimate is just the square root of this expression, $SE^2$. IM NOT SURE ABOUT THIS

> Working with squared distance does not allow us to really work out with the data and understand them.

### Interpreting the Correlation Coefficient in context of Regression

Remember, the best prediction on least squares for Z-normalized scores:

$$Z' = r_{XY}Z_X$$

Some observations:

1. By definition, r ranges between -1 and 1 (**will discuss when presenting covariance).**
2. When $r$ is 0, we predict Z(Y)=0 for any X score; that is, we predict the Mean of Y.
    1. Always when dealing with z-normalized data, When there is no correlation between the Xs and the Ys, the formula is always going to give us 0 meaning that there is no correlation. Our prediction will look like a flat line. For each x we will just predict the mean of y. This means that we assign to y the value that is closest to all the other values of y.
3. When $r$ is 0, ==the sample standard error of estimate for predicting standard scores== is equal to 1 ($S_{ZyZx} = \sqrt{1-r^2_{XY}} = 1)$.
    1. So the Variance of the errors is also 1, meaning that we didn’t reduce any of the variables into the error.
    2. Conversely, if $r$ is 1, so it predicts our data perfectly, there is no error of estimate. correlation is perfect so the regression has no error whatsoever.
4. Because of point 1, **predicted Y values are always “less extreme” than the X values.** In the end what we do is multiply by a fraction, and we will consequently end up with a smaller, condensed value.
    
    > [!important] The prediction in this sense is always ‘pushed’ towards the mean of Y.
    > 
    > **Remember that we are always in a Z domain!**
    

![[Untitled 3 11.png|Untitled 3 11.png]]

$$Z' = \red r_{XY}Z_X$$

$\red r$ can be treated as conversion factors between units of Standard Deviation (SD): **how many SDs of Y do we change for each SD of X**.

Graphically, $r$ is the slope of the line $\frac{Z'_y}{Z_x} = \tan(\theta) = r$.

### When to use linear regression instead of ANOVA or t-test?

Imagine we are looking for some kind of pattern in our data. Can we do linear regression when having e.g. participants assigned to different conditions on a scale?

Yes, as long as you can normalize (_right? not sure_)

|weight kg|height cm|
|---|---|
|64|165|
|90|190|
|…|…|
|n|n|

$$y = ax+b$$

> [!important] I can build the regression model that predicts y given x.

**Example**: Can we apply regression to predict the height given a weight? Yes, y-axis would be the height and the x-axis the weight.

An example of very simple solution could be $y = 3x+0$…

Once we have some kind of linear expression, we have to test our model: how good is it outside the training data? To know whether a solution is able to generalize we have to try to predict from new data, so to be sure that we did not **fit the model to the data**. So we apply the same formula to new data and see if it still works (and how good it is…).

It is important to emphasize that having a model that fits to the data is not sufficient. A model that can perfectly predict data from training is just overfitted - we have some ways to test how good it is like via its significance (_p value_).

We can see that it is sometimes very easy to get a fitting model, but if it doesn’t generalize to the world, it is useless really.

> [!important] A single outlier can shift the expression so strongly to have no more match to prediction.

### Linear vs. non-linear problems

**To use a linear model, you should at least be certain that the response you are working with does actually follow a line shape**, and not a u-shape or whatever. In that case we might assume a parabolic relationship and try to work with a quadratic expression (where x is squared).

> [!important] By definition, the more multiplier of x you allow, the more flexible your model is, the better it performs with the given data. At the same time, risk of overfitting the data also arises. A less flexible model is better at generalizing and we should prefer that, usually.

> [!important] **When X and Y are Z normalized as here, the (best) 'b' is also, mathematically, the correlation coefficient**
> 
> $r_{xy}$**, which we'll discuss later.**

### Relation between $r$ and proportion of variance accounted by linear regression

Now that we make predictions of Y given X, how much of that variance can we account for?

> [!important] Recall that: The variance (
> 
> $s^2$ or $σ^2$) of a distribution measures the spread from the mean by using the squared distance of each observation from the mean.
> 
> $$\text{Variance } = \frac{\Sigma_{i=1}^N (X - \mu)^2}{N}$$

> [!important] **With the variance we can calculate the distance of each Y point from the mean of Ys**
> 
> . This quantifies my uncertainty in variance.

![[Untitled 4 8.png|Untitled 4 8.png]]

> [!important] if i don’t know anything about X (left in the image), the best thing I can do is to predict the mean of Y and their variance.

> [!important] If our linear model works, we want the difference between the predicted and the real data to be way smaller than the variance.

In ANOVAs, we say ways of accounting for variance explained by model, e.g., $SS_B$/$SS_T$ (For between-participant ANOVAs) or expressions such as $MS_{model}$/$MS_{error}$for within-$SS$ ANOVAs.

1. For regression, ==**the overall variance [that there is to be] explained in Z(Y) is 1 by definition**== (variance of z-normalized distribution) $s^2Z_y = 1$.
2. The variance of predicting Y from X [residuals] is: $s^2_{zyzx} = 1 - r^2_{XY}$, that is, in plain English, that ==**the square of the standard error is equal to 1 minus the square of the correlation coefficient**====.==
3. Combining 1 and 2, we have: The proportional reduction in variance is:
    
    $$\frac{ \red{s^2Z_y} - \green{s^2_{ZyZx}} }{\red{s^2Zy}} = \frac{1-(1-r^2)}{1} = r^2$$
    
    This is sometimes called ‘explained variance.’
    
    > [!important] Of the
    > 
    > ==**total variance in Y**==, we subtract ==**the variance of the 'residuals/prediction-error'**== and ==**scale by the total variance of Y**==. (more on this later when discussing Sums of Squares in regression)
    

> So if $r = 0.5$, we are explaining 25% of the variance.

### Regression when using raw scores

When using Raw rather than Z-scores, the same principles and equations hold, but instead of Z-scores, we use raw:

With Z-normalized data ($Z'_Y = r_{XY}Z_X$) the predicted y is equal to the correlation $r$ times the x. Using raw scores, we have to replace numbers to have this equation:

$$\frac{y'-\mu_y}{s_y} = r_{xy}\frac{(x-\mu_x)}{s_x}$$

> [!important] After some rearranging, we get:
> 
> $$y'= \red{b_{yx}}(x-\mu_x) + \mu_y$$
> 
> The raw score of $y'$ can be predicted by our $b$ multiplied by the difference of $x$ from its mean $\mu_x$ plus the mean of y $\mu_y$.
> 
> $$\text{with } \red{b_{yx}} = \frac{r_{xy}s_y}{s_x}$$
> 
> $\red{b_{yx}}$ (beta) is called the ==**sample regression coefficient of Y on X.**==

Mathematically, for a given set of values of X and Y, the regression lines of predicting raw scores of Y from X or predicting raw scores of X from Y **will be different**. The two resulting beta ($b_{\orange y \blue x}$ and $b_{ \blue x \orange y}$) will be different, and their slope as well $b_{\orange y \blue x} \ne b_{ \blue x \orange y}$.

$$b_{\orange y \blue x} = \frac{r_{xy}s_{\orange y}}{s_{\blue x}}  
\quad  
\ne  
\quad  
b_{ \blue x \orange y} = \frac{r_{xy}s_{\blue x}}{s_{\orange y}}$$

## Regression from Perspectives of Sums of Squares

> [!important] Part of the notes are taken from here:
> 
> [The game of increasing R-squared in a regression model (analyticsvidhya.com)](https://www.analyticsvidhya.com/blog/2021/05/the-game-of-increasing-r-squared-in-a-regression-model/)

To explain a regression problem with sums of squares, we have to introduce the coefficient of determination.

> [!important] $R^2$
> 
> or the **coefficient of determination**, defines the degree to which the variance in the dependent variable (target or response) can be explained by the independent variable (features or predictors). It can range from 0 to 1.
> 
> $$0 < R^2 < 1$$

Ideally, we would want the independent variables to explain the complete variations in the target variable. In that scenario, the $R^2$ value would be equal to 1. Thus we can say that **the higher the** $R^2$ **value, the better is our model.**

> [!important] In simple terms, the higher the
> 
> $R^2$, the more variation is explained by your input variables, and hence better is your model.

![[Untitled 5 7.png|Untitled 5 7.png]]

- The ==**Total Sum of Squares**== ==$SST$== is squared distance of each Y value from the mean of Y. Note that this relates only to variation in the Y variable, which is what we want to predict.
- The ==**Sum of Squares of the ERRROR,**== ==$SSE$==**, quantifies the part of SS in variable Y that is not explained by the regression line**. It is the Sum of Squared Deviations from each point’s Y value to points Predicted(Y) value (predicted from its X).
- The ==**Sum of Squares Regression**== ==$SSR$== is the part of SST which IS modeled by the regression line - It is computed as the part of SST that remains after removing SSE.

$$\green{SSR} = \red{SST} - \orange{SSE}$$

> [!important] What you get from
> 
> $SSR$ **is what you can explain**!!!

Now we are able to calculate the Coefficient of Determination $R^2$.

$$R^2 = \frac{SSR}{SST}$$

Consider $R^2 = (SST-SSE) / SST$:

- Rearranging the expression gives $R^2 = 1 - (SSE / SST)$
- Means that $R^2$ max value can be 1, and it is so when $SSE = 0$

> [!important] As we have seen, the best-fit line to X,Y is the line producing the lowest SSE and so also the largest
> 
> **Coefficient of Determination**

### Elaboration: $SST$

Consider Y that has values {6, 2, 1}, what is the $SST$?

What would be the sum of distance from the mean if we did not square the distances?

the mean here is 3. The sum of squares are {9, 4, 1} → 14

$$SST = ({\Sigma_iY_i-\mu})^2$$

SST: the average distances squared to the mean of Y.

> [!important] **SSE is a quantification of imprecision!**
> 
> It measures variation not captured by the regression line (prediction errors)**.**

## Using Regression and Correlation

Using both regression and correlation to analyze your sample data is perfectly fine for descriptive statistics. They help describe relationships between variables in your dataset. Specifically, they show how variables interact as if following a linear rule. This description is limited to your current dataset and may change with a different dataset or subset.

The regression model is fitted to your sample, and the regression coefficient you get is the best estimate of the beta $b$ value in the population.

> [!important] DONT STUDY SLIDE 51

### Further consideration for using Regression

> [!important] Regression is a tool, like ANOVA, for evaluating cause an effects; specifically, between an IV and DV.
> 
> $y =f(x)$ is the form we use to predict the effect from the cause.

The most common formula for regression is:

- If we have a single predicting variable this is a **univariate regression** (e.g., predicting child height from parent height).
- If we have more than one predicting variable, e.g., predicting child height from parent height and income, this is s a **multivariate regression** (where we have X1 and X2).

> [!important] In both cases, we model a linear relation between Y and X(s).

Once we 'fit' the model to the data we can take a new data point for which we have an X value and predict the Y value from it.

Terminology in the context of experimental design:

- **X**: IV, Cause, Predictor Variable, Explanatory Variable
- **Y**: DV, Effect, Outcome variable, response variable, criterion variable.

> [!important] Before doing a regression it is important to plot the joint distribution of the two variable using a scatterplot.
> 
> **If the relationship is strongly non-linear, it doesn’t make sense running a linear regression.** Start empirically.

Some people say that we need a moderately strong linear correlation before going ahead to performing regression…

**The professor does not agree: correlation is not robust against outliers**, as their influence can be very strong. For this reason, you could get strong correlations when there’s no linear relation or vice versa just because of outliers.

> [!important] Eventually, you want to
> 
> **run regression models robust against outliers.** It means that the regression algorithm is able to recognize outliers and penalize them (giving a negative weight to them).

## Regression Analysis

### Sanity Checks

Many of the sanity checks have to do with **the residuals** (or errors). A residual is the **difference between an observed value and a predicted value in regression analysis**.

$$e = y - \hat y$$

- We do an analysis of residual after running a regression, and ideally these residuals **should be normally distributed**.
- Moreover, there should be **no relation between value of residuals and value of X**, that would suggest a non-linear relation.
    
    > [!important] It would mean that our model is performing better for a particular range of X - and we do not want that: we want a model performing equally on the whole data.
    
- **Residual should** _**not**_ **show serial autocorrelation** (for time series): **you do not want the residual to correlate over time series**. ==Residuals should not suggest patterns in data==. This would suggest that there is a pattern of the data for which we are not accounting of residual.
    
    > [!important] This is a problem because we would have less independent data points, as we are unable to account for all the variables going on.
    
- Ideally, residuals should have no outliers.
- When you test the model **do not extrapolate beyond the range of X**: the model accounts for the range of X you have trained it on, and you cannot extrapolate the relation to values that are out of their range.
    
    > [!important] The only thing you know is that the model you developed holds for the range of X you had on hand.
    
    > E.g., if I’m extrapolating the height of kids in Italy, my model cannot be applied to kids in the Netherlands.
    

### Significance of Beta (β)

> [!important] WON'T ASK THIS

When performing a regression analysis, **the main focus is on testing hypotheses about the regression coefficient, Beta (β)**, rather than on how well the model predicts or the variance explained.

In the **Null Hypothesis (H0)**, the regression coefficient ($\beta_{yx}$) is equal to zero

$$⁍.$$

> [!important] This means there is
> 
> **no linear relationship between the independent and dependent variables** in the population.

Testing this hypothesis helps determine if the predictor variable has a statistically significant association with the outcome variable. If you reject the null hypothesis, it suggests that there is evidence of a linear relationship in the population.

In regression analysis, **we test hypotheses about the regression coefficient (Beta, β), not about how well the model predicts or the variance explained.**

To test this, we use the t-value formula:

$$t = \frac{r_{xy}\sqrt{N-2}}{\sqrt{1-r^2_{xy}}}$$

The t-value follows a t-distribution with $N-2$ degrees of freedom. This test can be one-tailed or two-tailed, depending on the research question.

> [!important] The model assumes any prediction is based entirely on a linear relationship. Thus, H0 means "no prediction is possible using a linear rule,"
> 
> **though non-linear relationships might still exist.**

In practice, after running the regression and computing Beta, we perform a t-test. This allows us to make conclusions about whether there is a significant linear relationship in our data.

> So, you can say: "I have run the regression and computed the beta coefficient. I have conducted a t-test to assess the significance of this coefficient. Based on these results, we can describe the linear relationship between our variables in this dataset. This relationship is specific to the current data and assumes linearity."

### Quantifying our certainty in beta

Keeping in mind that we always talk about our sample, but we are interested in the population, we ask ourselves: **what is the likely beta, given X and Y, in the population? How wrong am I?**

We can actually predict a ==**confidence interval for beta**==, that given a sample will compute what is the likely value of beta in the population - the ‘true’ beta. **You cannot assume that your beta is the one found in the population.**

> [!important] **Just remember that this beta confidence can be computed.**

The Confidence Interval is related to some quantitative features of beta:

- the residual
- the standard deviation
- the sample size $N$: more data points are better

> [!important] From the beginning of your study, think that you will need ideally these parameters to have a good confidence interval for beta.

> [!important] SLIDE 58-59 REMOVED THIS YEAR