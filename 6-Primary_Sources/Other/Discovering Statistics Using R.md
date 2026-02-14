Title: Discovering Statistics Using R
Author: [[]]
Tags: #statistics #other 


# 1. Why is my evil lecturer forcing me to learn statistics?
The basic research process consists of 
1. Initial observation or research question
2. Generate theory 
3. Generate hypothesis = identify variables
4. Collect data to test theory = measure variables
5. Analyse data 
6. Change or modify the theory

A hypothesis testing is applied only to scientific statements that could be confirmed by empirical evidence.

-  Independent variable (cause): A variable thought to be the cause of some effect. This term is usually used in experimental research to denote a variable that the experimenter has manipulated.
- Dependent variable (effect): A variable thought to be affected by changes in an independent variable. You can think of this variable as an outcome.


1. Categorical (entities are divided into distinct categories):
	1. Binary variable: There are only two categories (e.g., dead or alive).
	2. Nominal variable: There are more than two categories (e.g., whether someone is an omnivore, vegetarian, vegan, or fruitarian).
3. Ordinal variable: The same as a nominal variable but the categories have a logical order (e.g., whether people got a fail, a pass, a merit or a distinction in their exam).
4. Continuous (entities get a distinct score): 
	1. Interval variable: Equal intervals on the variable represent equal differences in the property being measured (e.g., the difference between 6 and 8 is equivalent to the difference between 13 and 15).
	2. Ratio variable: The same as an interval variable, but the ratios of scores on the scale must also make sense (e.g., a score of 16 on an anxiety scale means that the person is, in reality, twice as anxious as someone scoring 8).

Validity - instrument measures what they intend to measure.
- criterion validity 
- content validity

Reliability - consistently measure 

Correlational or cross-sectional research (where we observe what naturally goes on in the world without directly interfering with it)  
Experimental research (where we manipulate one variable to see its effect on another)

David Hume (see Hume, 1739–40, 1748, for more detail),11 an influential philosopher, said that to infer cause and effect:
(1) cause and effect must occur close together in time (contiguity); 
(2) the cause must occur before an effect does; and 
(3) the effect should never occur without the presence of the cause. 

These conditions imply that causality can be inferred through corroborating evidence: cause is equated to high degrees of correlation between contiguous events.

Confounds (confounding variables) are variables that sit between "cause" and "effect"

two methods of data collection:
	between-groups, between-subjects, or independent design
	within-subject or repeated-measures design

Two types of variation
1. Systematic variation: This variation is due to the experimenter doing something to all of the participants in one condition but not in the other condition.
2. Unsystematic variation: This variation results from random factors that exist between the experimental conditions (natural differences in ability, the time of day, etc.).

A good way to deal with unsystematic variation is randomization.


## Analysing data
1. Frequency distributions
2. the center of a distribution
3. the dispersion in a distribution

There are two main ways in which a distribution can deviate from normal: (1) lack of symmetry (called skew) and (2) pointyness (called kurtosis).

A skewed distribution can be either positively skewed (the frequent scores are clustered at the lower end and the tail points towards the higher or more positive scores) or negatively skewed (the frequent scores are clustered at the higher end and the tail points towards the lower or more negative scores).
![[Screenshot 2024-09-29 at 18.22.17.png]]
A distribution with positive kurtosis has many scores in the tails (a so-called heavy-tailed distribution) and is pointy. This is known as a leptokurtic distribution. In contrast, a distribution with negative kurtosisis is relatively thin in the tails (has light tails) and tends to be flatter than normal. This distribution is called platykurtic.
![[Screenshot 2024-09-29 at 18.22.26.png]]

The center of a distribution
The **==mode==** is simply the score that occurs most frequently in the data set.
Another way to quantify the center of a distribution is to look for the middle score when scores are ranked in order of magnitude. This is called the ==median==.
To calculate the ==mean== we simply add up all of the scores and then divide by the total number of scores we have.

The dispersion in a distribution
	==range== - The easiest way to look at dispersion is to take the largest score and subtract from it the smallest score. One problem with the range is that because it uses only the highest and lowest score it is affected dramatically by extreme scores.
	==interquartile range== - 50 % of data in the middle, calculated by subtraction of upper and lower 25% of data.

Using statistics to go beyond the data.
- by using the probability distribution
- we new probability of event inside normal distribution with a mean of 0 and a standard deviation of 1. 
- we could convert our distribution to a normal one using z-scores.
- First, to center the data around zero, we take each score and subtract from it the mean of all scores 
- ![[Screenshot 2024-09-29 at 21.24.10.png]]

# 2. Everything you ever wanted to know about statistics
Statistical models use real-world data to contract the model of reality which could be used to test hypothesis.

The degree of representation of the world by a model called "fit"

The majority of models and tools use linear approaches, so they could be inappropriate for specific data.


Population can be used narrowly, for example, all male cats are called Bob. But even in this case, you have no access to all these cats, to solve this problem, you can use ==sample==, test your hypothesis, and then infer the data and knowledge to the population as a whole. The bigger the sample the more reliable conclusion we can make.

Simple statistical models
- mean is an example of a statistical model, it is a hypothetical value created to summarize the data
- In order to determine the fit, we could find:
	- deviance - lines that represent the difference between the observation and our model and can be thought of as the error in the model. To calculate deviance we could subtract the mean from the value.![[Screenshot 2024-09-30 at 22.15.31.png]]
	- sum of squared errors is better than just sum of deviance (the sum always equals 0), but the value depends on the amount of data ![[Screenshot 2024-09-30 at 22.15.49.png]]
	- variance - solve the problem in sum of squared errors by dividing it by the number of observations minus one. The only problem with variance is that units are squared. ![[Screenshot 2024-09-30 at 22.40.32.png]]
	- standard deviation is simply the square root of variance. So, a small SD shows a good fit of the mean, and otherwise, a large SD indicates a bad fit of the model. 

degrees of freedom - you can select "order" for most observations except the last, the last observation has no choice. In statistical terms, the degrees of freedom relate to the number of observations that are free to vary.


Standard error
1. Multiple samples from the population could be taken. 
2. In the samples, the mean (${\bar {x}}$) is different from the population mean($μ$) 
3. To illustrates sampling variatio we could use sampling distribution. Sampling distribution is simply the frequency distribution of sample means from the same population. 
4. Standard error of the mean (SE) is the standard deviation of sample means. 
5. Therefore, the standard error could be calculated by taking the difference between each sample mean and the overall mean, squaring these differences, adding them up, and then dividing by the number of samples. Finally, the square root of this value would need to be taken to get the standard deviation of sample means, the standard error.


When sample is large enough?
- 30
- as samples get large (usually defined as greater than 30), the sampling distribution has a normal distribution with a mean equal to the population mean, and a standard deviation: ![[Screenshot 2024-10-12 at 17.32.47.png]]
- When the sample is relatively small (fewer than 30) the sampling distribution has a different shape, known as a t-distribution, which we’ll come back to later.

Confidence intervals are boundaries within which we believe the true value of the population mean will fall. 
1. 95 or 99 % confidence intervals mean that if we'd collected 100 samples, mean from 95 of these samples fall in this range. 
2. Convert our values to z ones :
	1. ![[Screenshot 2024-10-12 at 17.46.41.png]]
	2. 95% of z-scores fall between −1.96 and 1.96
	3. ![[Screenshot 2024-10-12 at 17.47.04.png]]
	4. ![[Screenshot 2024-10-12 at 17.47.33.png]]
	5. ![[Screenshot 2024-10-12 at 17.49.27.png]]
3. If the confidence interval is small than the sample mean represents the population mean more or less correctly and otherwise. 
4. To calculate the confidence intervals in small samples the t-distribution is used.

### 2.6 Using statistical models to test research questions
Hypotheses and criteria for effect sifnificants have to be dicided before collecting the data. 

**post hoc tests** is a way of research cheating, when hypothesis are changing after data has been colected. 

Why do we use .05?
- The significance testing that we use today is a blend of Fisher’s idea of using the probability value p as an index of the weight of evidence against a null hypothesis, and Jerzy Neyman and Egron Pearson’s idea of testing a null hypothesis against an alternative hypothesis
- Fisher acknowledged that the dogmatic use of a fixed level of significance was silly: ‘no scientific worker has a fixed level of significance at which from year to year, and in all circumstances, he rejects hypotheses; he rather gives his mind to each particular case in the light of his evidence and his ideas’(Fisher, 1956)

Test statstics 
The simplest way, therefore, to test whether the model fits the data, or whether our hypothesis is a good explanation of the data we have observed, is to compare the systematic variation against the unsystematic variation. In doing so we compare how good the model/hypothesis is at explaining the data against how bad it is (the error):
	test statistic = variance explained by the model/variance not explained by the model
Then, we could estimate how likely this test statistic would occur randomly. 

What we can and can’t conclude from a  significant test statistic
1. The importance of an effect
	If we accept the experimental hypothesis as true, we can not evaluate the importance of an effect. Very small effects can be "significant" just because huge number of samples. 
2. Non-significant results: if we reject the alternative hypothesis, it does not mean that the null hypothesis is true. All that a non-significant result tells us is that the effect is not big enough to be anything other than a chance finding – it doesn’t tell us that the effect is zero
3. Significant results: Does not state that the alternative hypothesis is true, it states that the probability of the alternative hypothesis is true is larger. 

A statistical model that test a directional hypothesis is called a ==one-tailed test==, whereas one testing a non-directional hypothesis is known as a ==two-tailed test.== 
In the case of a two-tailed test, we have three possible outcomes - positive, negative, and zero relationships. Zero relationship is a null hypothesis. In order to look into both ways, we split .05 probability into two .025.

Type I error -  we believe that something is true but it is not. a-level
Type II error - we believe something is false but it is not. b-level - Cohen (1992) suggests that the maximum acceptable probability of a Type II error would be .2 (or 20%).
Although we know that as the probability of making a Type I error decreases, the probability of making a Type II error increases, the exact nature of the relationship is usually left for the researcher to make an educated guess

Effect sizes: the most common measures of effect size are [[Cohen's d]], Pearson's correlation coefficient r, and the odds ratio. 
The effect size in a population is intrinsically linked to three other statistical properties: (1) the sample size on which the sample effect size is based; (2) the probability level at which we will accept an effect as being statistically significant (the α-level); and (3) the ability of a test to detect an effect of that size (known as the statistical power, not to be confused with statistical powder, which is an illegal substance that makes you understand statistics better).

Calculate the power of a test: Given that we’ve conducted our experiment, we will have already selected a value of α, we can estimate the effect size based on our sample, and we will know how many participants we used. Therefore, we can use these values to calculate β, the power of our test. If this value turns out to be .8 or more we can be confident that we achieved sufficient power to detect any effects that might have existed, but if the resulting value is less, then we might want to replicate the experiment using more participants to increase the power.

Calculate the sample size necessary to achieve a given level of power: Given that we know the value of α and β, we can use past research to estimate the size of effect that we would hope to detect in an experiment. Even if no one had previously done the exact experiment that we intend to do, we can still estimate the likely effect size based on similar experiments. We can use this estimated effect size to calculate how many participants we would need to detect that effect (based on the values of α and β that we’ve chosen).

Based on Cohen (1992), we can use the following guidelines: if we take the standard α-level of .05 and require the recommended power of .8, then we need 783 participants to detect a small effect size (r = .1), 85 participants to detect a medium effect size (r = .3) and 28 participants to detect a large effect size (r = .5).
# 3. The R environment
concatenate function or c()
```r
metalica <- c("Rob","Bob")
```
data.frame()
```r
metalica <- data.frame(Name = metalicaNames, Age = meallicaAges)
```
$ to choose the variables
```r
metalica$Age
```
Operator 
Exponentiation (i.e., to the power of, so, x^2 or x\*\*2 is x2, x^3 is x3, and so on)
< Less than
<= Less than or equal to
!= Not equal to
x | y x OR y (e.g., name == “Lars”|“ James” means ‘the variable name is equal to either Lars or James’)
x & y x AND y (e.g., age == 47 & name == “ James” means ‘the variable age is equal to 47 and the variable name is equal to James’)
```r
metallica$fatherhoodAge<- metallica$Age − metallica$childAge
```
for categorical variables, we could use levels()
```r
levels(job) <- c("Students","Lecturer")
```

# Links