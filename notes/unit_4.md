---
Date: 2024-03-12
Reviewed: true
week_lec: 4.2
---
- [[#Introduction]]
    - [[#What falls under “statistics”]]
    - [[#Notation]]
    - [[#Understanding Simple Statistics]]
- [[#Measures of central tendency]]
    - [[#The Mean]]
    - [[#The Median]]
    - [[#The Mode]]
    - [[#General Guidelines: when to use what]]
- [[#Measures of spread (dispersion)]]
    - [[#Range-based measures]]
    - [[#Mean absolute Deviation (MAD) (rarely used)]]
    - [[#Variance, Estimated Variance and Sum of Squares]]
    - [[#Standard Deviation]]
- [[#Frequency Distributions]]
    - [[#Histogram function]]
    - [[#Other views of frequency distributions]]
    - [[#Percentiles]]
- [[#Describing Data with Graphs]]
    - [[#Single Variables]]
        - [[#Bar graphs]]
        - [[#Box and Whiskers]]
        - [[#Histogram]]
        - [[#Bar graph vs histogram]]
    - [[#Multiple Variables]]
        - [[#Stacked bar graph]]
        - [[#Scatter plots]]

---

> [!important] We now move into Statistics.
> 
>   
> The entire point of Descriptive Statistics is giving us tools to be able to describe data, to let them tell the story they have to tell. **We want to go from data, to information, to knowledge.**

## Introduction

### What falls under “statistics”

> [!important] “Statistics is a branch of mathematics dealing with data collection, organization, analysis, interpretation and presentation.” - Wikipedia

In studying, we differentiate **Descriptive** from **Inferential** statistics:

> [!important] **Descriptive Statistics**
> 
> focuses on **summarizing and describing features of the data**. It involves techniques for organizing, summarizing, and presenting data in a meaningful way. It allows us to **understand patterns** without generalizing beyond the sample.

Common descriptive statistics include:

- measures of central tendency (e.g., mean, median, mode)
- measures of variability (e.g., range, variance, standard deviation)
- graphical representations (e.g., histograms, scatter plots).

> [!important] **Inferential Statistics**
> 
> involves the process of making inferences and **drawing conclusions about populations based on sample data**, test hypothesis and make predictions.

Techniques in inferential statistics include:

- hypothesis testing
- confidence intervals
- regression analysis
- analysis of variance (ANOVA)

> [!important] **Descriptive is important**
> 
> : It is _almost_ useless to just describe results of statistical test without communicating _summary_ data patterns.

Complex descriptive methods, such as multidimensional scaling, clustering, and principal component analysis (PCA), offer deeper insights into the structure and organization of data, enhancing researchers' understanding of complex datasets.

### Notation

- Variables are represented by Roman capital letters, like $X$ or $Y$. For example, $X$ can represent "age".
- $N$ indicates the total number of values in a distribution.
- Different values of a variable are labeled with subscripts. For instance, $X_i$ represents the _$i$-_th score, where _$i$_ ranges from $1$ to $N$.
- Summation is common, denoted by the symbol sigma ($\Sigma$). It means adding up all the values of a variable from _i_ equal to $1$ up to _$N$_. This is expressed as $\sum^N_{i=1} X_i$.

**NOTE**:

- Sometimes we need to sum the squares of the values, which is written as $\Sigma X^2 = X^2_1 + X^2_2 + X^2_3 + \dots + X^2_N$.
- At times, we may need to square the sum of values, denoted as $(\Sigma X)^2 = (X_1 + X_2 + X_3 + \dots + X_N)^2$.

### Understanding Simple Statistics

When scientists discuss statistics (like z-statistics, 1t-statistics…), they're referring to a mathematical concept rather than a specific method. In this context, "statistics" means the algorithm or mathematical property used in analysis.

> [!important] **Describing Data Features:**
> 
> We often need to summarize a large set of numbers succinctly. Measures of central tendency and dispersion help us achieve this:

Measures of **Central Tendency** answer which is the most typical value:

1. **Mean**: the average value.
2. **Median**: the middle value when numbers are arranged in order.
3. **Mode**: the most frequently occurring value.

Measures of **Dispersion** describe the extent to which the rest of the values vary around this central/typical value:

1. **Interquartile Range**: the range between the first and third quartiles.
2. **Variance**: the average of the squared differences from the mean.
3. **Standard Deviation**: the square root of the variance, indicating the average distance of values from the mean.

Let’s look at them one by one.

## Measures of central tendency

![[Untitled 33.png|Untitled 33.png]]

[Python Statistical Analysis: Measures of central tendency and… – Towards AI](https://towardsai.net/p/machine-learning/python-statistical-analysis-measures-of-central-tendency-and-dispersion)

### The Mean

In normal language, we use the term 'average' for what is technically the mean.

> [!important] To calculate the mean, we need to sum all values and divide by number of values (arithmetic mean; most commonly used).
> 
> $$\text{Mean formula : } \overline{x} = {\Sigma x\over{N}}$$

You'll see $\overline{x}$ when describing sample-mean and $\mu$ when referring to mean of populations scores.

```Python
import numpy as np

# Generate random values from a normal distribution
my_values = np.random.normal(size=10)

# Round the values to two decimal places
my_values = np.round(my_values * 10, 2)

# Calculate and print the mean
print("The mean is:", np.mean(my_values))
```

The mean, despite its common usage, isn't necessarily a directly observed value but is rather a statistical calculation derived from the sum of all values divided by the total count. This means that it **might not correspond to any measured value**.

**In inferential statistics, it is frequently employed to analyze and test population parameters**, providing insights into the characteristics of a larger group based on a sample.

Conceptually, the mean can be likened to the **balancing point in weight**, situated at the center of values. It maintains an equilibrium, with equal distance from values both above and below it, expressed mathematically as: $\sum (X_i - \overline{X})=0$

> [!important] While the mean is highly sensitive and accurately reflects central tendencies, it's also **particularly susceptible to the influence of outliers** or extreme scores, more so than other measures like the median or mode.

For symmetric distributions (see the “Old Faithful Wait Times” example) the mean serves as a robust descriptor of the dataset's typical value, offering significant descriptive strength in such scenarios.

**Technical facts**

In technical terms, **altering even a single value within a sample will inevitably alter the mean**, given that the sum used to calculate it changes accordingly.

The act of adding or removing numbers from a dataset will also invariably shift the mean, except in the rare scenario where the added or removed number happens to be exactly equal to the mean itself.

> [!important] Mathematically, the mean is the number that minimizes the sum of the squared deviations from all other values within the dataset, expressed as
> 
> $\sum(Xᵢ - \overline{X})²$.

In the context of repeatedly sampling from a population, it's essential to note that while the mean may vary slightly from sample to sample, it tends to exhibit less variation compared to the median or mode. **This characteristic makes it the measure of central tendency** ==**least susceptible to sampling variation**== **over multiple iterations.**

> [!important] Mean, commonly referred to as average: can be different from any observed value; the most stable over multiple iterations.

### The Median

> [!important] The Median of a set of values divides the distribution exactly in half, with 50% of the scores above and 50% below.
> 
> **It is less influenced by extreme values (outliers) and more by the number of scores.**

To calculate it, you arrange the numbers from lowest to highest and find the middle score. If there's an even number of samples, you take the average of the two middle numbers.

Median Odd data:

$$(\frac{n+1}{2})^{th} \text{ observation}$$

Median Even data:

$$\frac{\frac{n^{th}}{2} \text{ obs.} + (\frac{n}{2} + 1)^{th} \text{obs.}}{2}$$

> **Odd data example**: Let's say we have a small dataset representing the ages of a group of people: 20, 25, 30, 35, and 40. To find the median, we first arrange these numbers in ascending order: 20, 25, 30, 35, 40. Since we have an odd number of values (5), the median is simply the middle number, which is 30.

> **Even data example**: Now, let's consider another dataset with an even number of values: 10, 15, 20, 25, 30, and 35. Again, we arrange these numbers in ascending order: 10, 15, 20, 25, 30, 35. Since we have six values this time, we need to find the average of the two middle numbers, which are 20 and 25. So, the median is (20 + 25) / 2 = 22.5.

> [!important] In both cases, the median represents the midpoint of the dataset, dividing it into two equal parts.

The median has several **advantages**:

1. It is **less influenced by outliers compared to the mean**, making it a more robust measure of central tendency.
2. It may provide a **better representation of skewed data**, even when there are no outliers.
3. It **can be used with ordinal variables**, where the distances between levels are not equal, whereas the mean cannot.

However, the median also has its **limitations**:

1. It **does not take into account the exact values of all items in the dataset**, which can lead to loss of information.
2. It **cannot be used in estimating population parameters**, unlike the mean, which can be utilized for this purpose.

  

> [!important] Median: less influenced by outliers, can be used with ordinal variables; can lead to loss of information.

### The Mode

> [!important] The Mode is employed with
> 
> **nominal scales** and **indicates the category with the highest frequency**. It's generally considered **the least precise measure of central tendency.**

It's helpful when there are two distinct sets of values (bimodal distributions), such as a U-shaped distribution. To find two modes, the data may need to be grouped into classes. However, it cannot be utilized to estimate population parameters, unlike the mean.

### General Guidelines: when to use what

Here's a simpler breakdown of when to use each measure of central tendency:

- **Mean** is the average. Use it for continuous measurements unless there's a specific reason not to. Avoid using it for ordinal scales, though, where the distances between categories may not be equal. It's a good choice for data that follows a normal distribution.
- **Median** is the middle score in ordinated values of a dataset. Choose this when dealing with skewed distributions or when outliers are present. It's less influenced by extreme values, making it better for representing the center of such distributions.
- **Mode** is the most common value in the dataset, and is useful for describing typical values. **It is the peak point in skewed distribution**. Opt for the mode when dealing with discrete variables, like counts or categories.
    - For example, if you're looking at the number of children in families, the mode would give you the most typical family size.

> [!important] When dealing with bell-shaped distributions, the mean, median, and mode will be similar.

However, in distributions with long tails due to low-value outliers (negative skew) or high-value outliers (positive skew), the median provides a better representation of the typical value. In negatively-skewed distributions, the mean is lower than the median.

![[Untitled 1 21.png|Untitled 1 21.png]]

## Measures of spread (dispersion)

Measures of spread tell us **how data points are spread out from the center**. They show the shape of the data distribution and include various measures like Inter-quartile range, mean deviation, variance, and standard deviation.

![[Untitled 2 19.png|Untitled 2 19.png]]

[Python Statistical Analysis: Measures of central tendency and… – Towards AI](https://towardsai.net/p/machine-learning/python-statistical-analysis-measures-of-central-tendency-and-dispersion)

### Range-based measures

> [!important] Range-based measures describe the spread of data based on the
> 
> **Range**, which is the difference between the largest and smallest observations, plus one to account for rounding errors.
> 
> $$\text{data\_range = max\_{data} - min\_{data}} + 1$$
> 
> They are **very sensitive to outliers**.

> [!important] The
> 
> **Inter-Quartile Range** (IQR) measures the spread between the 25th and 75th percentile values of the data distribution and is less sensitive to outliers.

In the below example, we have a set of data representing some observations. We calculate the range by subtracting the smallest observation from the largest and adding 1. Then, we calculate the IQR by finding the 25th and 75th percentile values (the lower and upper quartiles) and taking the difference between them. Finally, we print out the calculated range and IQR.

```Python
# Sample data
data = [12, 15, 18, 20, 22, 25, 30, 35, 40, 50, 55]

# Calculate the range
data_range = max(data) - min(data) + 1

# Calculate the InterQuartile Range (IQR)
sorted_data = sorted(data)
n = len(sorted_data)
lower_quartile_index = int(0.25 * n)
upper_quartile_index = int(0.75 * n)
iqr = sorted_data[upper_quartile_index] - sorted_data[lower_quartile_index]

print("Data Range:", data_range)
print("InterQuartile Range (IQR):", iqr)
```

### Mean absolute Deviation (MAD) (_rarely used_)

> [!important] The Mean Absolute Deviation (MAD) represents the
> 
> **average absolute distance of each observation from the mean of the distribution**.

To calculate it, subtract the mean from each observation and compute its absolute, sum them up, and then divide by the total number of observations.

$$MAD = \frac{ \Sigma | x- \overline{x}|}{N}$$

> [!important] MAD is
> 
> **not suitable for estimating population parameters** and ==**isn't commonly used for statistical inference due to its limitations.**== Moreover, it requires the absolute function to measure distance regardless of direction: another approach is squaring the difference of each value from the mean.

### Variance, Estimated Variance and Sum of Squares

> [!important] The
> 
> **variance of a distribution (**$σ^2$**)** measures the spread from the mean by using the squared distance of each observation $X_i$ from the mean $\mu$ and the dividing for the sample size $N.$
> 
> $$\sigma^2 = \frac{\sum_{i=1}^N (X_i - \mu)^2}{N}$$

Any software will calculate these days, but if stuck; the rapid form is: $\frac{\sum X_i^2}{N} - \mu^2$

> [!important] The
> 
> **estimated population variance** $s^2$, used for samples (which is the common case for us) the formula differs slightly.
> 
> $$s^2 = \frac{\sum_{i=1}^N (X - \blue{\overline{x}})^2}{\red{N-1}}$$
> 
> Here, ==$\overline{x}$== ==represent the mean of our sample== (and not of the population. Moreover, ==we divide by the sample size== _==minus one==_ ==because we are estimating.==

> [!important] The numerator (upper part) of the Variance equation is called
> 
> **Sum of Squares** or **Sum of squared deviations**
> 
> $$SS = \sum_{i=1}^N (X_i - \mu)^2$$

### Standard Deviation

> [!important] **The variance is a squared value**
> 
> which sometimes can be not very telling when compared to our data. To obtain a measure of deviation that is non-squared, we take the square root of the variance. This is the ==**Standard Deviation**==.

For the population (typically not available): $\sigma = \sqrt{\frac{\Sigma (X - \mu)^2}{N}}$

For a sample, and **what you should typically use**:

$$s = \hat \sigma = \sqrt{\frac{SS}{N-1}} = \sqrt{\frac{\sum(X - \overline{X})^2}{N-1}}$$

```Python
# Sample data
data = [10, 12, 15, 18, 20]

# Calculate the mean
mean = sum(data) / len(data)

# Calculate the squared differences from the mean
squared_diff = [(x - mean) ** 2 for x in data]

# Calculate the variance
variance = sum(squared_diff) / len(data)

# Calculate the standard deviation (square root of the variance)
standard_deviation = variance ** 0.5

print("Standard Deviation:", standard_deviation)

# Output
# Standard Deviation: 3.687817782917155
```

The standard deviation has several properties:

1. It indicates **how spread out the data points are relative to the mean of the distribution.**
2. Unlike some other measures, the standard deviation takes into account the deviation of each individual data point from the mean, making it **sensitive to variations within the dataset**.
3. **Extreme values (outliers) in the dataset can have a notable impact** on the standard deviation, affecting its value.

Similar to the mean, the standard deviation tends to be **relatively stable** even with changes in the sample data. This stability makes it a preferred measure of dispersion compared to measures like range, which can fluctuate more with different samples.

## Frequency Distributions

> [!important] A Frequency Distribution presents score values and their frequencies of occurrence. It allows us to understand
> 
> **how often each value occurred.**

```Python
from collections import Counter

# Define the list of scores
my_scores = [82, 92, 75, 76, 90, 74, 67, 86, 81, 63, 46, 62, 99, 93, 58, 54, 82, 82, 66, 73, 79,
             95, 57, 76, 93, 86, 80, 89, 76, 76, 63, 74, 94, 96, 77, 65, 79, 60, 56, 72, 82, 70,
             67, 79, 71, 77, 52, 76, 68, 72, 88, 84, 70, 83, 93, 76, 82, 96, 87, 69, 89, 77, 81,
             87, 65, 77, 72, 56, 78, 78]

# Create a frequency table using Counter
score_counts = Counter(my_scores)

# Print the frequency table
print("Score\tFrequency")
for score, count in score_counts.items():
    print(f"{score}\t{count}")
```

  

![[Untitled 3 16.png|Untitled 3 16.png]]

For individual, discrete scores, the frequency distribution simply counts how many times each score appears. **Frequency distributions can also be applied to grouped scores**, where scores are grouped into intervals or bins: you divide your observations into equal-sized bins and count how many entries fall into each bin.

Histogram functions naturally compute frequency distributions within intervals.

### Histogram function

> [!important] A histogram is a way to form a new distribution: you don’t even need to plot the histogram, but it is more of a way to understand data in a different way.

```Python
import numpy as np
import matplotlib.pyplot as plt

# Define the list of scores
my_scores = [82, 92, 75, 76, 90, 74, 67, 86, 81, 63, 46, 62, 99, 93, 58, 54, 82, 82, 66, 73, 79,
             95, 57, 76, 93, 86, 80, 89, 76, 76, 63, 74, 94, 96, 77, 65, 79, 60, 56, 72, 82, 70,
             67, 79, 71, 77, 52, 76, 68, 72, 88, 84, 70, 83, 93, 76, 82, 96, 87, 69, 89, 77, 81,
             87, 65, 77, 72, 56, 78, 78]

# Define histogram properties
bin_edges = np.arange(45, 101, 5)

# Create the histogram
hist, bins = np.histogram(my_scores, bins=bin_edges, density=False)

# Print the bin edges and counts
print("Bin Edges:", bins)
print("Counts:", hist)

# Plot the histogram
plt.hist(my_scores, bins=bin_edges, density=False, edgecolor='black', alpha=0.7)
plt.xlabel('Scores')
plt.ylabel('Frequency')
plt.title('Histogram of Scores')
plt.grid(True)
plt.show()
```

![[Untitled 4 12.png|Untitled 4 12.png]]

As you see here, each bean gets a bar, and each bar describe some significance of the values.

### Other views of frequency distributions

Once we understand frequency distributions, we can explore them further with these additional views:

- **Relative Frequency Distribution**: This shows the proportion of the total number of scores that occur in each interval. It helps us understand the distribution of scores relative to the total.
- **Cumulative Frequency Distribution**: Here, we see the number of scores that fall below the upper real limit of each interval. It gives us a sense of the accumulation of scores as we move through the distribution.
- **Cumulative Percentage Distribution**: Similar to cumulative frequency distribution, but instead of counts, it indicates the percentage of scores that fall below the upper real limit of each interval. This helps us understand the distribution in terms of percentages.
- **Upper Real Limit for Integers**: For intervals involving whole numbers, the upper real limit is the upper value of the interval plus 0.5. This adjustment helps ensure that each score is counted correctly within its interval.

### Percentiles

> [!important] A
> 
> **percentile** or **percentile point**: the n-th percentile of a variable is the value that cuts off the first n-percent of the data values when the variables are sorted in ascending order.

A score value is greater than $X\%$ of the scores of people taking the test is said to be at the $X$th percentile

> **Example**: The 50th percentile (often denoted as $P_{50}$) is the value below which 50% of the data falls. In other words, it divides the data into two halves, with half the data falling below this value and half falling above.

> [!important] **Percentile Rank**
> 
> is the percentage of scores below a given value.

> **Example**: if a score is at the 75th percentile, it means that 75% of the scores fall below it.

# Describing Data with Graphs

## Single Variables

A graph has two axes: vertical and horizontal. The vertical axis is called the ordinate, or Y-axis, and the horizontal axis is the abscissa, or X-axis. In traditional graphs, the independent variable (IV) is plotted on the X-axis, while the dependent variable (DV) is plotted on the Y-axis.

For **frequency distributions**, the score values are usually plotted on the X-axis, with their corresponding frequencies or counts plotted on the Y-axis.

- **Labels and Titles**: Axes should be labeled, and the graph should have a clear title. Consider adding a caption for further clarity.
- **Intersection at 0**: Unless there's a specific reason not to, axes should intersect at 0 to maintain accuracy.

Common graph types for single variables include bar graphs, box-and-whisker plots, and histograms. Each serves different purposes and offers unique insights into the data.

### Bar graphs

In a Bar graphs, the values are represented by the height (or length) of the bars. They are used to display variables on a **nominal or ordinal scale**.

- Start the scale (on the Y-axis) at 0 unless there are good reasons not to do so - and if so, mark the deviation from 0 using a scale-break.
- Use _linear scale_ unless special circumstances call for another

> [!important] All of this is to ensure interpretability of the graph and avoid “forging interpretations”

![[Untitled 5 9.png|Untitled 5 9.png]]

### Box and Whiskers

The Box and Whiskers visualization can be very expressive as they present a five-number summary: min, max, upper-Quartile, lower-Quartile, and median. Moreover, outliers are also shown, if they exist.

Their function is to **capture the central tendency (mean), the range, and the distribution symmetry.**

![[Untitled 6 8.png|Untitled 6 8.png]]

How to read a box plot

We can see that the median is the central (black) line in the box; the length of the box instead indicates the variance. The symmetry* can be understood as position of median to upper and lower Quartile.

> [!important] **Symmetry**
> 
> here refers to the distribution of data points around the median. If the data is symmetrically distributed, it means that the values are evenly distributed on both sides of the median.

The **whiskers** of the plot refer to the minimum and maximum values that are **not considered outliers**. Whisker size is not fixed but shows most extreme values within range. Values that exceed the whiskers are considered outliers.

### Histogram

Histograms are visual representations used to display the distribution of variables, particularly those measured on interval or ratio scales. Histograms are suitable for visualizing data with **continuous scales on both axes**.

The **horizontal axis** of a histogram represents class intervals or ranges of values. The **height of each bar** on the histogram corresponds to the frequency or count of observations falling within each class interval.

Since the **intervals are continuous**, the vertical bars in a histogram touch each other, unlike bar graphs where they are spaced apart.

Histograms provide a visual summary of the distribution of data, allowing us to quickly assess patterns, central tendency, and variability. They are particularly useful for identifying the shape of the distribution and detecting any outliers or unusual patterns in the data.

  

![[Untitled 7 4.png|Untitled 7 4.png]]

### Bar graph vs histogram

The main difference between a bar graph and a histogram lies in the type of data they represent.

A **bar graph** is used to display categorical data, where each category is represented by a separate bar. The bars are usually spaced apart, and there's no inherent order to the categories.

On the other hand, a **histogram** is used to represent the distribution of numerical data, particularly when it's measured on interval or ratio scales. Instead of separate categories, histograms use continuous intervals or ranges of values on the horizontal axis. The height of each bar represents the frequency or count of observations falling within each interval. Unlike bar graphs, the bars in a histogram touch each other because the intervals are continuous.

> [!important] While bar graphs are suited for categorical data with distinct categories, histograms are designed for numerical data with continuous intervals, providing a visual summary of the distribution of values.

## Multiple Variables

When describing data with graphs involving multiple variables, we aim to visually represent relationships between these variables.

### Stacked bar graph

For instance, in analyzing car data, we might be interested in various factors such as model, cylinder count, weight, gear type, and fuel efficiency (e.g., km per liter). Using graphs helps us avoid cluttered tables and better understand connections within the data.

For example, we can create a graph where the number of cars (Y-axis) is plotted against the number of gears (X-axis, categorical). Additionally, we can represent the engine block type (straight or V-shaped) using different colors. This allows us to visualize how the number of gears correlates with the number of cars while also identifying any trends related to engine block types. Such graphical representations provide a clearer understanding of the data and facilitate insights into the relationships between multiple variables.

![[Untitled 8 4.png|Untitled 8 4.png]]

### Scatter plots

Another interesting way of visualizing data is with **scatter plots**, in which we display the value of two sets of data on two dimensions: each dot represents an observation. The position on the x-y axis represents the values of the observation.

![[Untitled 9 4.png|Untitled 9 4.png]]