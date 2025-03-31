---
Date: 2024-02-27
Reviewed: true
week_lec: 2.2
---
- [[#Measurement]]
    - [[#Understanding measurement]]
    - [[#Effective Measurement and Noise]]
    - [[#Sciences of measuring relations in nature]]
    - [[#Know your instruments]]
    - [[#Precision and Accuracy]]
    - [[#Sources of noise]]
- [[#Measurement in human context]]
    - [[#Reliability]]
    - [[#Classical Test Theory (CTT)]]
    - [[#Reliability Explained]]
- [[#Parallel tests]]
    - [[#Test-Retest Reliability (Stability Reliability)]]
    - [[#Alternate-Form Reliability]]
    - [[#Internal Consistency Reliability (Based on a Single Test)]]
- [[#Variables]]
    - [[#Conceptual and Operational Variables]]
    - [[#Understanding operationalization as a reader]]
- [[#Levels of Measurement]]
    - [[#Types of Data Measurement]]
    - [[#Assigning labels to measurements]]
    - [[#1. Nominal variables (AKA categorical/qualitative)]]
    - [[#2. Ordinal variables]]
    - [[#3. Interval variables]]
    - [[#4. Ratio scales]]
    - [[#Example: variables in the context of experiments]]
    - [[#Independent Variable (IV)]]
    - [[#Dependent Variable (DV) (AKA outcome)]]
    - [[#Table Recap IV and DV]]

---

## Measurement

### Understanding measurement

> [!important] Understanding measurement is vital because it's our primary method of testing hypotheses -
> 
> **it's all about the values we gather.**

It's crucial to recognize that a particular instrument doesn't dictate the type of data we collect. For instance, let's consider eye tracking. When optimizing our procedure, we might look at measurements like pupillometry or scan-path.

**What truly matters is our ability to choose which type of data to focus on while using a specific instrument**. To make that decision, we need to understand which instrument produces the most suitable data for our purposes.

### Effective Measurement and Noise

> [!important] Effective measurement
> 
> **sets the stage for effective hypothesis testing**.

Considerations about **noise** are crucial here. If you gather poor-quality data, you'll likely end up with poor-quality results.

$$\text{Garbage in} \rarr \text{Garbage out}$$

> [!important] **Noisy measurements**
> 
> , ones containing a lot of random variation or inconsistency, **can lead to an increase in** ==**Type-II errors**==. These errors occur when you miss detecting a true effect or relationship in the data due to the noise.

When conducting research, **we typically** ==**measure values**== **that represent specific quantities of interest.** These values can be either directly obtained or derived from collected data.

> For example, you might **directly measure** acoustic energy collected every half-second. However, your actual interest might lie in **derived values**, such as the mean acoustic energy over a 15-minute period.

We can also ==**measure relationships**== between different things. Imagine you're trying to figure out if there's a connection between two concepts. To do this, you'd look at how changes in one thing might affect the other.

> For example, let's say you're studying how exercise impacts mood. You'd want to consider other factors that could influence mood, like sleep or stress levels. These are your control variables. Then, you would vary the amount of exercise people get (the independent variable) and see how it affects their mood (the dependent variable), while keeping everything else constant.

> [!important] Effective measurement allows us to understand how changes in one thing can affect another, helping us grasp the relationship between different factors.

### Sciences of measuring relations in nature

There are field that are only interested in independent variables and other to dependent.

Example: what is the relationship between the speed of sound and air temperature for different types of air pressure? About this, there is actually a book from 1965, **and this book is just a set of tables**, there is no text into it!

> [!important] Measurement and its documenting can be very important.

### Know your instruments

Even when measuring non-biological system, source of noise and variance will produce different values for different measurement.

**Example: Measuring a rolling ball**  
  
A very simple example of a measuring context: as shown by the results, most of the measurements are around 0.3 seconds; **the surprising thing is that we can have a quite big difference inside various trails of the same condition (from 0.28 to 0.35)**. What causes this variance? We have a source of noise that produces different values at each trial.

![[Untitled 20.png|Untitled 20.png]]

Measurements of time for a ball to descend a channel with and without lubricant.

> [!important] This will be relevant when actually testing and measuring things

> Another example from the professor: testing a person to press a button with a USB keyboard could lead to problems into accuracy as USB have some latency between when the key is pressed and when the input is collected: a better approach could be replacing the keyboard with something more precise.

> [!important] Know your instruments and know what to expect when changing stuff! Not all ‘improvements’ are actually so.

### Precision and Accuracy

Let’s look at the difference between precision and accuracy:

- **Precision refers to how reproducible a measurement is.** When values cluster tightly together over repeated measurements, we say the measurement has high precision. Precision is typically reported using a measure of spread.
    
    > [!important] Precision heavily relies on the
    > 
    > **quality of the instrument** being used.
    
- **Accuracy describes the average difference between the measured value and the true or standard value.** Offset errors are consistent regardless of the magnitude of the input signal, while gain errors vary with the magnitude of the input signal.
    
    > [!important] The accuracy of a measurement can be understood by comparing the average of repeated measures with a
    > 
    > **gold standard** or true value.
    

When measuring very subtle effects at the limits of an instrument's capability, it's essential to consider factors such as resolution and sensitivity.

- **Resolution** is the smallest **portion** of the signal that can be **observed**.
- **Sensitivity** is the smallest **change** in the signal that can be **detected**.

> [!important] **Ideally, have both high accuracy and high precision.**

  

![[Untitled 1 9.png|Untitled 1 9.png]]

_As archers age, they may need to adjust their aim due to changes in eye-hand coordination. This adjustment can result in consistent grouping of shots, indicating good precision. However, their shots may consistently miss the intended target, leading to poor accuracy._

When there's a **systematic bias**, like an offset, but the precision of measurements is high (low accuracy but high precision), **we can still make conclusions about relative differences**. For example, we can say that gazes were consistently higher vertically in condition A compared to condition B. **However, we can't draw conclusions that rely on absolute references**, such as exact gaze coordinates, because of the potential bias in the measurements.

> [!important] I.e.: HIGH systematic bias + LOW accuracy + HIGH precision = possible to make conclusions about RELATIVE differences, but no ABSOLUTE.

> If i have an eye tracker that is really imprecise, it will never give me that the fixation point is what i expect it to be (e.g., (0,0)). All my measurement will be shifted of, for example, 10 pixels, but i still can draw conclusions about **relative differences** from data as there is a systematic bias (offset) but high precision. We won’t be able, however, to draw conclusion that need **absolute** reference.

### Sources of noise

**Random error**: This happens when measurements vary each time, maybe due to things like electrical fluctuations. **It can be lessened by averaging**.

> For instance, when using a ruler to measure, the precision depends on how many lines are on the ruler. So, taking multiple readings helps to balance out the errors.

**Systematic error**: Unlike random errors, these errors don't go away with repeated measurements because there's a problem with the measuring tool itself. Offset errors can be **fixed with a calibration process**, which means adjusting the measurement tool to make it more accurate.

$$\text{Random Error → Average} \qquad \text{Systematic Error → Calibrate}$$

## Measurement in human context

### Reliability

> [!important] **Reliability**
> 
> is the consistency of a measure. It answer the question: **does it produce similar results when under the same exact conditions?**

In fields like psychology, linguistics, and neuroscience, we often collect data from people. It's crucial to have reliable measurements when studying human behavior.

> [!important] Know the reliability of your measure!

> For instance, in neuroscience, researchers study if there are differences between people. They conduct experiments, gather data on how each person performs, and then explore if certain brain areas are linked to these results.
> 
> The challenge here is with the reliability of the data. Brain data tends to be precise, but behavioral data can be less so. If the same people take the same test again later, there might be slight differences in the data. But **how much difference is too much?** If it's too big, linking behavioral data to brain data (which doesn't change much) can lead to different conclusions. Our behavioral data can be noisy and not very precise. So, it's important to know how reliable our measurements are, which is often overlooked.

> [!important] Low reliability → less useful data.

### Classical Test Theory (CTT)

Classical Test Theory is a psychometric theory that predicts Ψ (psychological) testing. It takes the **overall measure (**$X$**)** (e.g., 85 on exam) as sum of **true score (**$T$**)** and **error (**$E$**)**.

$$X =T+E$$

> Imagine you're taking a multiple-choice test. Sometimes you know the answers for sure, but sometimes you might guess. In this theory, your true score is what you really know, and the rest is influenced by guessing.

We want to measure $T$, but the **True Score is a theoretical value** and cannot be observed directly. **It is the expected value if the test was applied infinite times.**

In Classical Test Theory (CTT), the consistency of test scores is called reliability.

> [!important] **Reliability**
> 
> is reduced when $E$ is large in relation to $T$. The test is inconsistent because the score does not reflect what it needs to measure, due to error.

> **Example:** Imagine we're trying to link behavioral scores with the thickness of the frontal cortex. We give the same test twice, a month apart, and look at the scores for each person.
> 
> 1. **Case 1:** If someone gets the **exact same score both times**, it shows perfect reliability. The scores match up perfectly, which is what we want.
> 2. **Case 2:** Even if the **scores are different each time**, if **there's some consistency between them**—for example, someone who scored low the first time scores low again—that's still useful. Maybe there's something external affecting the scores, like the lighting, or maybe just retaking the test helped them improve a bit.
> 3. **Case 3:** But if the **scores are totally different**, we can't trust the data. They're too far apart to be reliable. What's important here is the correlation between the two sets of measurements, not whether they're exactly the same.

### Reliability Explained

> [!important] In CTT, we talk about
> 
> **reliability** as **how much the true scores** ($T$, cannot be directly observed) **vary compared to the actual scores** ($X$, directly observed).

The **reliability coefficient ‘**_**rho’**_ **(**$\rho$**)** is defined as **the ratio of** _**true score**_ **variance to the total variance of test scores**:

$$\rho^2_{XT} = \frac{\sigma^2_T}{\sigma^2_X}$$

Where: $\rho$ = reliability, $\sigma^2$ = variance, $X$ = measured-score, $T$ = true-score, $E$ = error

Another way to look at it is to consider the variance of true scores compared to the sum of the variances of true scores and errors. $\rho^2_{XT} = \frac{\sigma^2_T}{\sigma^2_T + \sigma^2_E}$

> [!important] Reliability is maximal (1) when Error
> 
> $E$ is 0; lower otherwise.

This value can be estimated with three different sorts of _**parallel tests**._

## Parallel tests

- Test-Retest Reliability
- Alternate-Form Reliability
- Internal Consistency Reliability

### **Test-Retest Reliability (Stability Reliability)**

Imagine giving the same test to a group of people twice. If the test is reliable, the variation in the true scores (how much people actually know) and the error (mistakes or inconsistencies) should be similar both times. This method is commonly used in psychology and neuropsychology.

> [!important] Test-Retest tells us
> 
> **whether the results change over different testing occasions**, helping us understand the consistency of measurements over time.

### **Alternate-Form Reliability**

Here, the goal is to create two different tests or measures that assess the same thing. These tests should be similar in content, so answering a question on one test should give the same score as answering a similar question on the other test.

> For example, comparing 2x3 with 3x2.

While this can be useful, **it's challenging to ensure that the tests are truly equivalent**, especially in fields like emotional assessment where content may vary. However, it can be more efficient because both scores are obtained in one session.

> [!important] Alternate-Form Reliability
> 
> **s**hows us **the impact of using slightly different versions of the test on the results**, giving insight into how interchangeable these versions are.

### **Internal Consistency Reliability (Based on a Single Test)**

- **Split-Half Method**: Here, we split the test into two halves for each participant, maybe dividing questions into odd and even. Then, we see if scores from the two halves are consistent across participants.
    - However, this method can underestimate reliability and give different results depending on how the items are split.
- **Coefficient Alpha**: This is like an advanced version of the split-half method, and requires _item-level_ analysis. It calculates the internal consistency by considering all possible ways of splitting the test.
    - It's important to do because it doesn't cost extra time and gives valuable insights into the reliability of the test.

> [!important] Internal Consistency Reliability explores how the mix of different types of questions or items affects the overall assessment,
> 
> **revealing how well the items in the test measure the same underlying concept**.

## Variables

Variables change depending from the context; in psychology a variable is any dimension on which we can partition meaningful differences; i.e. specify changes in values.

A variable has to have at least two different levels (categories, numeric values…).

> [!important] How many unique values can be instantiated for this level

> For example, gender, grade-point-average, stress levels, or intelligence are all variables. Sentence difficulty is another example—it's interesting because we can adjust or manipulate it.

### Conceptual and Operational Variables

**Conceptual variables** are the theoretical aspects we're interested in, like the impact of fatigue or the quality of food. We break these down into different levels to understand conceptual variation. These variables are more abstract than any specific measure we use to quantify them.

**Operational variables**, on the other hand, are the measurable dimensions we use to quantify the conceptual variables.

> [!important] **Operationalization**
> 
> is **the process of matching an objectively measurable dimension to the theoretical concept**, and it's important to evaluate the quality of this match before collecting data.

> For example, let's say we want to measure the quality of reading comprehension. We can use different operational measures, like accuracy in answering questions or how often someone looks back at what they've read.

> [!important] **Don't assume**
> 
> your ideas about conceptual or operational variables are correct. **Test them -** different operational measures might not always correlate. If they don't, it could indicate a **lack of clarity** about the concept itself.

### Understanding operationalization as a reader

Sometimes it is hard to understand what is the relation between the conceptual variable and the operational one: we might have to figure them out on our own.

> **Example:** To evaluate whether there is a sensitive period for “reorganization of language in blind” we examined “connectivity between brain areas in frontal and temporal regions”.
> 
> - **Conceptual variable**: a specific time period during which the brain undergoes significant changes related to language processing in blind individuals.
> - **Operationalization**: quantify the strength or degree of connections between specific brain regions, specifically those in the frontal and temporal lobes.
> - **Measures**: neuroimaging techniques such as functional magnetic resonance imaging (fMRI) to assess the strength and organization of neural connections in these areas.

## Levels of Measurement

### Types of Data Measurement

Different variables may consist of different data types.

1. **Categorical Data**: This involves labeling observations into specific groups or categories. Each observation is assigned a text label. For example, "sex" could be categorized as "male" or "female."
2. **Numerical Data**: These data types are associated with numbers. Within numerical data, we have two subtypes:
    - **Continuous**: These values can vary across a wide range without clear limits on the number of different values. For instance, body temperature measured in Celsius units.
    - **Discrete**: These values are more precise and countable, like the number of apples (1, 2, 3...).

> **Examples**:
> 
> - **Categorical**: Sex (male, female), Gender identity (male, female, trans)
> - **Numerical**:
>     - **Continuous**: Body temperature in Celsius
>     - **Discrete**: Age in years (1, 2, 3...)

### Assigning labels to measurements

> [!important] Scientists use
> 
> **four levels of measurement to describe different types of variables**. Each level offers different opportunities for statistical analysis and sensitivity in drawing conclusions.

When designing studies, it's crucial to **choose variables that allow for more sensitive analysis**.

> For example, if you're investigating whether people prefer ice cream or cake on hot days, you could measure preference by having them make a binary choice (choose one or the other) or by using another measure to gauge preference. The choice of measurement method can affect the sensitivity of your analysis and the conclusions you draw.

The four levels of measurement, from the least to the most informative:

1. **Nominal (Categorical)**: This level involves categorizing data into groups without any specific order or hierarchy. _Examples include country of residence and political party affiliation._
2. **Ordinal**: Data at this level can be ranked or ordered, but the differences between values may not be consistent. _Examples include race rankings, class positions, and educational attainment levels (BA, MA, PhD)._
3. **Interval**: Here, data are measured on a scale where the differences between values are consistent, but there is **no true zero point***. _Examples include temperature measurements and some rating scales in questionnaires._
4. **Ratio**: This is the most informative level, with data measured on a scale where both the differences between values and the presence of a **true zero point*** are meaningful. _Examples include weight, speed, years of education, and accuracy measurements._

> [!important] **True zero point**
> 
> : a value on a measurement scale that represents the absence of the measured quantity: variables like weight and height (_**ratio**_) have a true zero point (0kg is no weight); instead in temperature (_**interval**_) like Celsius, zero is just a point on a scale - and not the absence of temperature.

In psychology, we collect various types of data across different disciplines, coding them by different variables depending on the research question and the type of analysis we want to conduct.

||Categorical or Numerical?|Hierarchical|Consistent-scale|True zero point|
|---|---|---|---|---|
|Nominal|**Categorical**|❌|❌|N.A.|
|Ordinal|**Categorical**|✅|❌|N.A.|
|Interval|**Numerical**|✅|✅|❌|
|Ratio|**Numerical**|✅|✅|✅|

### 1. Nominal variables (AKA categorical/qualitative)

> [!important] Nominal variables are categories that
> 
> **don't have a relative relationship or inherent order** between them.

Each observation falls into only one category, and the **categories are**:

- **Exclusive**, so that variables have to consist of a number of non-overlapping categories;
- **Exhaustive** with respect to the measured values: all observations must fall into one of the categories.

> [!important] All variables, regardless of type, must consist of non-overlapping categories, and each observation must belong to only one category.

> Let’s say I am trying to understand the distribution of languages daily used in Bolzano. My questionnaire includes, for ”daily-use language” question: Italian, German. **Problems? →** We will very soon fall into some other language (in this case, our nominal variables).

> [!important] In some cases, we might assign nominal categories numbers for convenience, like 1 or 0, known as
> 
> **Dummy Coding**. These numbers are arbitrary labels and don't imply any inherent order. This coding allows for certain types of analyses like correlation or regression.

In statistics, we use nominal variables both descriptively and inferentially.

- **Descriptive Analysis**: We often examine the relative frequencies of categories within nominal variables.
- **Inferential Analysis**: Nominal variables are used in various ways:
    - **Co-occurrence**: When participants are classified based on multiple categorical variables, we use contingency tables and chi-square tests to analyze relationships. _For example, we might compare the number of right-handed vs. left-handed men and women._
    - **Predicting Nominal Variables**: We can use multiple continuous variables to predict a nominal outcome (_like Alzheimer's disease: yes/no_) using logistic regression. This method can also be extended to predict outcomes with more than two options.
    - **Predictive Variable**: Nominal variables can also serve as predictors or independent variables in predictive modeling.

### 2. Ordinal variables

> [!important] Ordinal variables are those where we can rank the categories. Each category is separate (
> 
> **mutually exclusive**), has a **logical order**, and represents different amounts of something.

> For instance, when we measure "agreement," we might use a scale like "strongly agree," "agree," "disagree," and "strongly disagree." Similarly, for "education," we could have categories like High school, Bachelor's, Master's, and PhD.

With ordinal variables we have **no fixed distance,** which means that we can tell which category is higher or lower, but we can't say how much more one category is than another.

> For example, we know first place is higher than second, but we can't say how much better it is. This makes it tricky to compare the differences between categories.

> [!important] Ordinal variables allow us to use statistical measures like mode, median, and rank-order correlations to analyze data.

### 3. Interval variables

> [!important] Interval variables are those where
> 
> **each measurement is assigned a number**, not just a category label as we have seen until now. They share similarities with ordinal variables in that they are **exclusive** and **exhaustive**, but they go further by having a **known relationship between the categories**.

In interval variables, there's **a dimension of measurement underlying the categories:** a classic example is temperature. However, interval variables **lack a meaningful zero point** (look at True Zero Point explanation above), and we can't make statements about ratios.

> For instance, with temperature we can't say something is "twice as hot" as something else, or that “it has no temperature” (but we can do so with weight, which is a ratio scale).

> [!important] In analyzing interval variables, we can use descriptors like range, median, and mode. Mean and standard deviation can also be used if there are enough data points and the scale is non-discrete.

### 4. Ratio scales

> [!important] Ratio scales are similar to interval scales, but they have an extra feature: a
> 
> **meaningful zero point**. Moreover, on a ratio scale it's **not possible to have values below zero**.

> Examples include weight, speed, velocity, percentage errors, years of education, and the number of apples in a bag.

**Ratio scales offer the most detailed information,** making it possible to calculate the mean and measures of spread accurately. It's important to note that **both discrete and continuous variables can have ratio scales.**

Here a working example where we can see all kinds of variables:

||ID|Sex|Edu (years)|Degree|Heart Rate|
|---|---|---|---|---|---|
||1|M|12|High School Diploma|65|
||2|F|13|High School Diploma|73|
||3|F|16|B.A.|75|
|**Type**|_Nominal (dummy)_|_Nominal_|_Ratio_|_Ordinal_|_Ratio_|

### Example: variables in the context of experiments

In a psychology experiment, we manipulate certain aspects to see their effect on behavior or brain function. **Let's consider an example focusing on judgments of words.**

> We aim to manipulate the depth of processing using two operational variables: semantic judgment and phonological judgment. These variables involve two types of independent variables: whether the words relate to animate/inanimate objects and whether they start with a consonant or a vowel. Participants are asked to memorize words under these conditions, and we measure how many words they can recall successfully, which is our dependent variable.

**To recap the above text, we have:**

- Conceptual variable: Depth of processing
- Operational variable: Semantic vs. phonological judgment
- Independent variables: Animate/inanimate objects vs. starting with consonant/vowel
- Dependent variable: Number of successfully recalled words.

### Independent Variable (IV)

> [!important] **The independent Variable (IV) is the aspect we manipulate**
> 
> , often believed to have a causal effect on another variable.
> 
> - It **needs to vary** during the study, meaning it has different levels or values, not just a constant.
> - The researcher has **complete control over it in controlled experiments**.

> For example, we might put a hand in warm or cold water to measure the autonomic response, or we could use different amounts of fertilizer to observe the impact on tomato size.

In **natural experiments** (different from controlled experiments), the independent variable might not be under the researcher's control. For instance, they might observe if sunny or cloudy days (IV) lead to different self-ratings of happiness (DV), or if tomatoes grow faster (DV) on cold versus warm days (IV).

> **Example from prof.** In the ABCD study, researchers relocated children, with one group experiencing the trauma of a hurricane. Later, they examined the impact of this traumatic event on brain structure. Similarly, during the COVID pandemic, researchers compared the brain structures of individuals who contracted COVID-19 with those who didn't.

> [!important] The independent variable allows researchers to
> 
> **draw causal conclusions**.

### Dependent Variable (DV) (AKA outcome)

> [!important] The
> 
> **Dependent Variable (DV)**, also known as the **outcome** variable, is the result of one or more independent variables and their potential interactions. It's common to collect multiple dependent variables in a study.

In a **true experiment**, the independent variable IV is manipulated and fully controlled by the experimenter, while **the dependent variable DV is measured**. The goal is to determine whether the independent variable affects the dependent variable while accounting for other possible explanations.

$$\text{True experiment}  
\begin{cases}  
\text{Manipulate IV} \\  
\text{Measure DV}  
\end{cases}$$

**In some non-experimental studies, both the independent and dependent variables are measured**. For example, in brain research, scientists might study patterns of activity preceding movement in different directions or brain activity predicting whether a stimulus is perceived. In such cases, the independent variable is typically the one that occurs earlier in time, as cause and effect can't be reversed.

> [!important] It's always beneficial to gather as much data as possible (about behavior).

Independent variables are often categorical, though not always nominal, while dependent variables are typically ratio but could also be categorical. If possible, it's preferable to use parametric independent variables.

> [!important] Remember, an experiment should have at least one independent variable.

### Table Recap IV and DV

Here's a table recap for Independent Variable (IV) and Dependent Variable (DV):

||Control|Measurement|Variability|Example|Type|
|---|---|---|---|---|---|
|**Independent Variable (IV)**|✅ Researcher-controlled (in controlled experiments)|❌ Not measured, manipulated|Needs to vary (different levels or values)|Amount of fertilizer used, cold or hot water|Often categorical, preferably parametric|
|**Dependent Variable (DV), a.k.a. Outcome**|❌ Not controlled by researcher|✅ Measured to observe effects of IV|Not required to vary, observed effect|Tomato size, self-ratings of happiness|Typically ratio, can be categorical|