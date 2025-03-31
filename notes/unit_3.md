---
Date: 2024-03-05
Reviewed: true
week_lec: 3.2
---
- [[#Experiments’ aims]]
- [[#Bias]]
    - [[#Sampling bias]]
    - [[#Selection bias]]
    - [[#Experimenter Expectancy Effects/Biases]]
    - [[#No stop rule Bias (inside Experimenter Expectancy Bias)]]
    - [[#Minimizing bias in Psychological studies]]
    - [[#Other biases]]
- [[#Experimental Designs]]
    - [[#Simple designs]]
    - [[#Factorial designs]]
    - [[#Extraneous variables]]
- [[#Types of designs]]
    - [[#1. Between-subject random trial design]]
    - [[#2. Within-subjects / Repeated measures]]
    - [[#3. Block Design]]
    - [[#Designs Recap]]
    - [[#Other Designs (won’t delve into these)]]
- [[#Validity]]
    - [[#Internal Validity]]
    - [[#External Validity]]
    - [[#Factors that impact internal validity🫀]]
    - [[#Factors that impact external validity 🌌]]
    - [[#Factors table summary]]
    - [[#Ecological validity]]
    - [[#Other forms of validity]]
- [[#Summary]]

---

## Experiments’ aims

> [!important] The aim of an experiment is to evaluate an hypothesis about a
> 
> **causal relationship between an Independent Variable (IV) and a Dependent Variable (DV)**. For this, all other variable apart from the IV must be controlled and kept constant.

There are different ways for manipulating IVs and quantifying the resulting impact. These are captured in different **Experimental Designs.**

A good rule of thumb is to have a **random allocation of participants**. Moreover, if different groups are allocated to different locations, the sampling has to be random.

> [!important] The key is to
> 
> **identify and control all confounding variables,** ensuring that any change in the DV can be attributed solely to manipulation of the IV.

## Bias

> [!important] A
> 
> **bias** is a ==**systematic error in the data**==; they shift the data and can produce under- or over-estimation. Biases **reduce our ability to draw valid conclusions**:
> 
> - about relationship between variables (**internal validity**)
> - about whether the results generalize to the general population outside the sample (**external validity**)

We are always interested in what happens in the population: our sample is just a sample. **What can we say on what happens in the world given our sample?** We have to bridge these two worlds with ==**inferential statistics**==, but if our sample is not representative of the population (or other error we will see) we will be biased.

We will look at:

- Sampling bias
- Selection bias
- Experimenter Expectancy Effects/Biases
- How to minimize bias

### Sampling bias

> [!important] **Sampling bias**
> 
> occurs when **the sample used in a study is not representative of the population it's meant to represent.** In other words, the sample doesn't accurately reflect the broader population, making it difficult to generalize findings.

> For instance, in studies where participants volunteer for fMRI experiments because they suspect they have a condition, or in university experiments where participants tend to be a specific subset of the population (such as educated individuals), sampling bias can occur. This can lead to findings that may not apply to the population as a whole.

### Selection bias

> [!important] **Selection bias**
> 
> occurs when **participants in different conditions have different baseline characteristics.** While it's not common in randomized studies, it can occur in quasi-experimental designs where participants aren't randomly assigned to experimental conditions.

> **Example: Does Intensive English Teaching Work Better Than Normal Teaching?**  
> Imagine we want to compare students in regular and intensive-teaching schools to see who's better at English, and thus which teaching method is more effective. In this scenario, selection bias might exist if better students are more likely to choose or be placed in the intensive English teaching program.  
> 
> This bias could make it seem like intensive teaching is more effective, even if it's not the case when similar-quality students are randomly assigned to different teaching methods.
> 
> For instance, students assigned to the bilingual program might perform better because they come from wealthier families. This could falsely suggest that bilingual teaching is superior.
> 
> To eliminate the above selection bias, we could design an experiment where children are randomly assigned to either the bilingual or normal school and then compare their results.

### Experimenter Expectancy Effects/Biases

> [!important] Experimenters or research assistants might (unknowingly) communicate information to participants. From this we derive that
> 
> **experimenter bias** refers to **actions taken consciously or unconsciously, that damage the validity of the experiment.**

This could happen by communicating expectations about the outcome of the experiment and thus altering the patient’s performance, or by collecting data without a predefined stopping rule**.**

> A famous example of **communicated expectancy** is “Clever Hans”, a horse that was said to be able to do math. However, he would answer correctly only when the investigator knew the answer.
> 
> There is even a _The Simpsons_’ episode, when Maggie seems super intelligent but actually it was Lisa giving her, unconsciously, the right answer by for example moving the head.
> 
> ![[Untitled 26.png|Untitled 26.png]]

### **No stop rule Bias (inside Experimenter Expectancy Bias**)

> [!important] Another interesting bias inside the
> 
> **Experimenter Expectancy Bias** happens when collecting data **without a pre-defined stopping rule**: a rule or condition that specifies when data collection will end.

In a paper by Simmons et al. (2011), they wanted to underly how much **anything could be significant if we have no threshold** - this paper set the standard of pre-registering an experiment to have more reliable results: from when collecting data to when evaluating them we know our own expectations.

> [!important] We cannot just go and collect “five more data” to claim that our hypothesis was correct - it is just posing ourselves in a comfortable position.

Once again, we are looking at $P(D|H_0) < 0.05$, the probability of obtaining some data given our hypothesis: if we do not have a stop rule, we have flexibility in data collection that could possibly lead us to stop when we want, when data actually point out at our hypothesis.

### Minimizing bias in Psychological studies

> [!important] We can minimize the bias in psychological studies by using
> 
> **single-blind and double-blind studies**: they involve **a certain amount of lack of knowledge**.

**Single-blind**: participants receiving a treatment do not know what treatment they are receiving - or better, they do not know what the experiment is about. _[Seen a lot of times with Bottini, as there was always a cover task that would just ‘mislead’ people perception about the experiment as to not affect results.]_

**Double-blind**: in this setting not only participants, but also the administrator of the experiment do not know assignment of participants to condition.

> [!important] **Ideally**
> 
> , treatment/condition should be not coded in data so that **even the analysis is blind**.

> **Example 1: Blind auditions in orchestra.** Candidates are situated on a stage behind a screen, and play for a jury that cannot see them. In the ‘70s and ‘80s this step alone increased the chance of a woman to advance to the finals of 50%.
> 
> **Example 2: Wines.** Blind tasting of wines lead to California wines finally come to European markets too, as wine tasters were always biased towards European’s ones.

### Other biases

> [!important] **Response bias:**
> 
> in behavioral studies, it is a tendency for participants to provide ‘agree’ response when responding to different scales (AKA acquiescence bias).

It basically means that certain people tend to agree more to given things than others. This can be addressed by posing contradictory or antonymic statements along with affirmative ones.

> [!important] In general, in the population, the tendency mean is still towards agreeing.

> We can see that people that demonstrate an acquiescence bias have RT times a bit faster than other people when agreeing with the statement - like if they do not think about it and just go with the flow.

_The inverse bias of this is that a part of population do not trust what they hear, a distrust behavior: they end up being the ones who solve problems in different ways, and so has to be with the ways in which we perceive the world_

> [!important] **Demand characteristics**
> 
> : Participants might develop an idea about what the study is about, which could impact their responses. Their theories about the study might be similar to your own!

## Experimental Designs

> [!important] The experimental design is meant to allow a researcher to
> 
> **answer the empirical research question**.

In the experiment, data will be collected in two or more conditions (levels of the IV) that are (ideally) identical in all aspects but one. Different experimental designs allow asking different sorts of questions, under different constraints

> [!important] The aim is to see whether changes (manipulation) in IV cause a change in the DV

> E.g.: measure the “level of hungriness”: take both a IV like the hours slept and the DV like how much did they eat this morning.

### Simple designs

The simplest design will contain **one factor* with as few as two levels** (in psychology usually called conditions). Other 1-factor designs can examine response measured for multiple levels of a factor.

> [!important] A
> 
> **factor** is just a way to refer to independent variable (IV) in the context of a design.

> Example: pupil dilatation and cold exposure. Let’s look at the pupil dilatation while manipulating the temperature of the water in which participants’ hands are put. We have one factor (temperature of the water) and various levels (the various temperature, e.g.: 25°C, 30°C…)

### Factorial designs

> [!important] Factorial designs have
> 
> **two or more independent variables IV (factors)**, and **at least one dependent variable DV.** The simplest form is called a **two-by-two design (2x2)** which represents 2 factors each with 2 levels. Each level of one factor is paired (”crossed”) with each level of the other.

**Advantages:**

- **More efficient and powerful** than evaluating the different levels within each factor. Moreover, we can see _whether_ and _how_ factors correlate to each other.
- This design is **more parsimonious**: one analysis can answer multiple questions.

> **Example: enjoyment of reading - morning or evening; narrative or news.** Two factors: _when_ or _what_ reading. We can study multiple questions in one design. Moreover, to study whether the enjoyment in reading is the combination of two factors, we have to study them simultaneously - doing an experiments for each factor would not have the same results.

> [!important] Some experimental questions can only be answered when taking in consideration multiple factors simultaneously.

> [!important] An
> 
> **interaction** is just “differences of differences” - so comparing factorial differences inside one. Is $\delta_1$ like $\delta_2$?

Take a look at this “OSF Preregistration” pdf: it is a very useful schema to structure your questions before starting an experiment.

![[OSF_Preregistration.pdf]]

### Extraneous variables

> [!important] **Extraneous variables are any factors**
> 
> , either psychological or physical, **that vary in a study apart from the Independent Variable (IV) and Dependent Variable (DV)**. They pose a significant risk to the interpretability of findings because they can add noise or covary with levels of the IV.

These variables **can introduce noise**, and it's crucial to consider them. For example, variations in study settings or procedures across participants can lead to differences in attention or misinterpretation.

> [!important] **Tight experimental control**
> 
> can help adjust for this.

Each extraneous variable that is not accounted for could result in **false positives** (incorrectly identifying a relationship between the IV and DV) or **false negatives** (missing a genuine effect of the IV due to confounding EVs).

> [!important] **The main risk is a resulting correlation between the IV and EV values**
> 
> which doesn’t allow dissociating their effects. Random assignment and evaluating the match of variables across groups can mitigate this risk.

## Types of designs

### 1. Between-subject random trial design

> [!important] In a between-subject random trial design, we
> 
> **randomly select participants from the same population and assign them to different treatments**. This design is commonly used when elements subjected to treatment are assumed to be homogenous, such as plants or animals, although it's more challenging to assume homogeneity with people.

> **Example:** Let's conduct an experiment with a class. We divide the class into two groups and assign each participant to either a "control" or "experimental" group. We want to investigate whether cognitive improvement differs between the groups. To ensure the comparison is valid, we must check if factors like IQ and years of education are balanced between the groups, as these could impact the results.

> [!important] Random assignment is random, of course, but even by chance you can end up with very unbalanced groups.

Extraneous variables, like IQ and years of education in our example, can introduce false positives or false negatives.

- **Advantages:** This design allows for testing multiple treatments and can be analyzed using simple statistical tests of significance.
- **Disadvantages:** Large sample sizes are necessary.

> Why? For instance, if we're testing the effect of ambience temperature (hot or cold), we'd likely need more than 40 participants per group. Having less than 20 participants per treatment group makes it challenging to find meaningful results. Larger sample size experiments are often conducted using online questionnaires, although this approach isn't suitable for all studies.

### 2. Within-subjects / Repeated measures

> [!important] In a repeated measures or within-subjects design, the same individual is observed at (at least) two different time points or under two or more different conditions.

When assigning conditions to participants, it's important to ensure they're independent of time or order to **avoid potential order effects,** such as time-of-test, fatigue, or practice effects.

> [!important] The
> 
> **order effect** is when the order of presentation of the condition has an impact on the effect of the test. _The first test could have an impact on the second one_.

Most experiments in cognitive science, such as those using fMRI, follow this design.

> **Example:** Suppose we're testing cognitive tasks where participants are shown all nouns first and then all verbs later. This order could influence results simply because of time passing or fatigue.

> [!important] The
> 
> **carry-over effect** refers to the impact of one condition on another (contrast or assimilation).

> **Example:** 18 animals were tested on 3 conditions (A, B, C). Each animal received all three conditions (with a 21-day interval between each condition to **‘washout’***). **Randomization and counterbalancing are crucial**. Animals are randomly assigned to different sequences of conditions (ABC, BCA, CAB, etc.) to minimize order effects. Counterbalancing ensures each sequence occurs an equal number of times.
> 
> ![[Untitled 1 15.png|Untitled 1 15.png]]

> [!important] **Washout periods**
> 
> are intervals between conditions that allow any effects from the previous condition to dissipate. This **minimizes carry-over effects** by allowing the participant to return to baseline before starting the next condition.

Today, more sophisticated methods of randomizing and counterbalancing are available.

> [!important] Donald Experiment (fill from the recording, around 35min):

The impact of the manipulation (reading the first text) has a great impact on the experiment (second text). These are very sensitive and implicit measure to understanding what is going on in people’s mind cognitively speaking, as explicitly speaking can be hard - giving them an implicit input and comparing it to a base can give a great insight.

### 3. Block Design

> [!important] A Block Design set up by
> 
> **pairing participants based on an Exogenous Variable (EV**): it’s used when there's a **strong suspicion that an EV will significantly impact the DV.**

It's employed when repeated measures are not feasible due to the Independent Variable (IV).

> [!important] **N.B.: different from the fMRI Block Design, where stimuli are blocked, not participants.**

> **Example:** Consider a study where participants are put into either a happy or sad mood, and their text memory is examined. Since people vary widely in their baseline mood, it's likely to interact with our manipulation. To address this, we need a design ensuring our manipulation affects people with similar baseline moods. Participants are paired based on the level of the EV (baseline mood), and conditions are randomly assigned within each pair.

This is a between-participant design. However, if randomly done in a class, there's no guarantee of a suitable baseline.

**Extra: Measuring baseline mood.** Tools like multi-item depression inventories, developed as questionnaires, are used. They lack a theoretical basis but are reliable in distinguishing responses between depressed and non-depressed individuals.

Block designs enable more sensitive statistical analysis by accounting for EVs. Each pair of participants becomes a unit of analysis.

> [!important] **Takeaway:**
> 
> Blocking an exogenous variable (EV) enhances statistical sensitivity.

### Designs Recap

Here is the table recap for the different types of designs:

||**Between-Subject Random Trial Design**|**Repeated Measures / Within-Subjects Design**|**Block Design**|
|---|---|---|---|
|**Control**|Participants are randomly assigned to different treatments|Same individual observed under multiple conditions|Participants paired based on exogenous variable (EV)|
|**Measurement**|Measures differences between groups|Observes the same subjects at different times or conditions|Randomly assigns conditions within pairs|
|**Variability**|Needs balanced extraneous variables to avoid false results|Must control for order effects and carry-over effects|Controls for EV impact on dependent variable (DV)|
|**Example**|Dividing a class into control and experimental groups to test cognitive improvement|Testing cognitive tasks with nouns first, then verbs; testing same subjects after two weeks|Studying text memory in participants put into happy or sad moods, paired by baseline mood|
|**Type**|Need large sample sizes and homogeneous subjects|Minimizes variability by using the same subjects, requires washout periods|Enhances statistical sensitivity by accounting for EVs, between-participant design|

### Other Designs (won’t delve into these)

**Association studies**: investigate causal associations

**Case studies**: Studying one or few entities using in-depth description/analysis of each case. Typical in neuropsychology. Some cases might be interesting because they are unique, or alternatively because they are a good exemplar of many such cases.

**Cross-sectional and longitudinal methods**: used in developmental research.

## Validity

Armed with idea of design, bias, variable, we will now discuss validity which will connect all the dots.

> [!important] Validity refers to the **quality of evidence or argument in relation to the construct being studied.** It encompasses a set of related properties that aim to ensure research conclusions provide the correct answer and inferential strength.

Validity serves as a _conceptual tool_ for **evaluating potential weaknesses** in a study during planning or interpretation. It's a property of the inferences drawn from the study, rather than the design or methods themselves.

> [!important] Validity is
> 
> **derived** _**given**_ **all preceding factors**, such as participants, design, and methods.

> Scientists categorize validity in various ways, with the Internal/External differentiation (Campbell, 1957) being widely accepted. However, despite differing terminology, **scientists generally agree on what constitutes threats to validity.**

We can subdivide validity into:

|   |   |
|---|---|
|Internal Validity|The study’s ability to accurately measure what it claims to be measuring|
|External Validity|How applicable the study's findings are outside of the controlled experimental|
|Ecological Validity|Ensuring that research findings are relevant, meaningful, and applicable to real-world situations|

### Internal Validity

> [!important] **Internal validity**
> 
> refers to the quality of the process by which statistical conclusions are derived. In simpler terms, it's about **ensuring that the study's results and conclusions are trustworthy.** For example, does the observed effect truly stem from the Independent Variable (IV) or from extraneous confounding variables?

> [!important] Essentially, internal validity is about
> 
> **the study's ability to accurately measure what it claims to be measuring.**

> For instance, if a study aims to determine the impact of a new teaching method on student performance, internal validity ensures that any observed changes in performance can be confidently attributed to the teaching method itself, and not to other factors like student motivation or teacher’s enthusiasm.

There's also a more restricted view of internal validity, focusing solely on whether it's justified to infer a causal relationship between the IV and DV.

> [!important] Achieving strong internal validity involves
> 
> **careful attention to the study's design, methodology, and control of extraneous variables**.

### External Validity

> [!important] **External validity**
> 
> considers the extent to which a study informs us about the phenomenon of interest in the real world. Even if a study demonstrates strong internal validity, it's crucial to **consider whether the results hold true in different contexts, populations, or situations**.

> [!important] External validity addresses the question of
> 
> **how applicable the study's findings are outside of the controlled experimental environment.**

> For instance, if a study finds that a particular therapy is effective in treating depression among college students, external validity examines whether the same therapy would be effective for different age groups, cultural backgrounds, or clinical settings.

> [!important] Ensuring strong external validity requires considering factors such as the
> 
> **representativeness of the study sample, the realism of the experimental conditions, and the ecological validity of the research methods.**

### Factors that impact internal validity🫀

Several factors can impact internal validity and influence the reliability and accuracy of study findings:

- **Failure to control for covariates** can lead to misleading conclusions: we have to ensure that reported results are not influenced by other variables.
- Researchers should avoid conducting numerous statistical tests with **no predetermined stopping rule**. This practice increases the likelihood of finding statistically significant results by chance, leading to inflated Type I error rates.
- In between-group studies, **selection bias** can occur if certain qualities make individuals more likely to be represented in one group than another. This can distort the relationship between the independent and dependent variables.
- **Failure to account for regression-to-mean effects** can lead to inaccurate interpretations of study results. This phenomenon occurs when participants' scores on a measure revert to their baseline level over time or with repeated testing.
    - For instance, let’s say you do an initial search for participants and only select some of them who have a high score in our test. The problem is that people who scored high in the beginning might end up scoring lower, and vice-versa. This happens on how we split the participants before. Chance has a greater impact that we could think - or better, people will go back to their baseline.
- **Measurement error** can distort initial test scores, pushing some high-scorers up and some low-scorers down. This can contribute to regression-to-mean effects and impact the reliability of study findings.
- **Ensuring sufficient statistical power** is crucial for detecting true effects and avoiding ==**Type II errors**== **(false negatives)**. Adequate sample sizes, reliable measures, and appropriate statistical tests are necessary to achieve sufficient power.

### Factors that impact external validity 🌌

Several factors can impact external validity and influence the generalizability of study findings beyond the specific population, setting, or time:

- **Samples of Convenience:** Recruiting participants from convenient sources can introduce self-selection bias and limit the generalizability of findings to the broader population.
    - For instance, recruiting participants in a health-food store for a study on the impact of taking Vitamins
- **Preferred Subjects:** In subject pools or other recruitment methods, certain individuals may be more likely to volunteer for studies, leading to a non-representative sample that reduces the ability to generalize findings.
- **Specificity of Cause-Effect Relationship:** It's essential to consider whether the documented cause-effect relationship is specific to the study's particular items, implementation of the treatment (IV), outcome measures, or setting. If these factors are highly specific, generalizing findings to other contexts may be limited.
- **Participant Expectations and Guessing:** If participants can accurately guess the purpose of the study or develop theories about the expected outcomes, they may alter their behavior to confirm these expectations. This can introduce bias and threaten the validity of study results.

> [!important] Including tasks that focus on different properties or aspects is crucial for minimizing the impact of participant expectations and ensuring that findings can be generalized across different conditions.

### Factors table summary

Here's a table summarizing the main concepts related to internal and external validity:

|**Aspect**|**Description**|**Factors Impacting Validity**|
|---|---|---|
|**Internal Validity**|Ensures that study results and conclusions are trustworthy, measuring what the study claims to measure.|- Failure to control for covariates  <br>- No predetermined stopping rule for statistical tests  <br>- Selection bias in between-group studies  <br>- Regression-to-mean effects  <br>- Measurement error  <br>- Insufficient statistical power (Type II error)|
|**External Validity**|Considers the extent to which study findings are applicable to the real world.|- Samples of convenience  <br>- Preferred subjects in recruitment methods  <br>- Specificity of the cause-effect relationship  <br>- Participant expectations and guessing|

### Ecological validity

> [!important] Ecological validity is a crucial aspect of research that
> 
> **assesses the extent to which findings from tests or experiments reflect real-world behaviors and experiences**. This means that researchers are interested in understanding how well the behaviors observed in controlled laboratory settings translate to behaviors observed in everyday life situations.

In **applied research**, ecological validity is **assessed by determining whether test scores** can **predict real-world functioning** (_veridicality_) and whether experimental tasks **resemble tasks encountered in daily life** (_verisimilitude_).

In the realm of **psychological assessment**, ecological validity examines the relationship between performance on neuropsychological tests and behavior observed outside the laboratory. Even if there isn't a strong theoretical basis for a test, it can still have high ecological validity if it accurately predicts real-world behavior. For example, the MMPI (Minnesota Multiphasic Personality Inventory) may lack a strong theoretical foundation, but its ability to predict real-world behaviors lends it ecological validity.

In **basic research**, ecological validity involves examining whether the context in which cognitive functions are studied mirrors their real-life application. This means considering whether experimental conditions approximate the conditions in which these functions are used in everyday life. Factors such as non-natural testing situations or unusual stimuli can impact the ecological validity of research findings.

> [!important] Ecological validity means
> 
> **ensuring that research findings are relevant, meaningful, and applicable to real-world situations**.

### Other forms of validity

**Statistical-conclusion validity**: Are our decisions about a covariance between IV and DV (yes, no) correct? (are we making type-I or type-II errors)? And are we correctly estimating the strength of the relationship?

**Construct-validity**: Is there an agreement on the meaning of the theoretical construct? Is the operationalization meaningful, especially when generating 'operational' variables for cause/effect phenomena. (some scientists include this within External validity).

> [!important] The study promised to explain something about the world but end up being so far away from it.

## Summary

In research, various biases can affect experimental results, but they can be mitigated through careful design and planning.

By employing robust designs that address issues such as sampling, proper manipulation of independent variables, and control of extraneous variables, researchers can minimize biases and draw more reliable causal conclusions from their studies.

These biases, along with other factors, are intimately connected to the concept of validity. While proper experimental designs can help alleviate some of these concerns, meticulous planning and consideration of validity are essential to ensure the credibility and robustness of research findings.