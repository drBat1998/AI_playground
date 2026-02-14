Title: Survival Analysis Basics
Author: [[]]
Tags: #other #programming #R 


# Notes
Survival analysis corresponds to a set of statistical approaches used to investigate the time it takes for an event of interest to occur.

Basic methods:
1. Kaplan-Meier - visualize survival curves
2. Log-rank test ot compare the survival curves
3. Cox proportional hazards regression to describe the effect of variables on survival.

Basic concepts
1. Survival time and event
2. Censoring
3. Survival function and hazard function

Survival time and type of events in cancer studies
There are different types of events, including:
Relapse
Progression
Death

The time from ‘response to treatment’ (complete remission) to the occurrence of the event of interest is commonly called survival time (or time to event).

The two most important measures in cancer studies include: 
1) the time to death; and 
2) the relapse-free survival time, which corresponds to the time between response to treatment and recurrence of the disease. It’s also known as disease-free survival time and event-free survival time.

Censoring
As mentioned above, survival analysis focuses on the expected duration of time until occurrence of an event of interest (relapse or death). However, the event may not be observed for some individuals within the study time period, producing the so-called censored observations.

Censoring may arise in the following ways:
1. a patient has not (yet) experienced the event of interest, such as relapse or death, within the study time period;
2. a patient is lost to follow-up during the study period;
3. a patient experiences a different event that makes further follow-up impossible.
This type of censoring, named right censoring, is handled in survival analysis.

Survival and hazard functions
Two related probabilities are used to describe survival data: the survival probability and the hazard probability.

The survival probability, also known as the survivor function S(t), is the probability that an individual survives from the time origin (e.g. diagnosis of cancer) to a specified future time t.

The hazard, denoted by h(t), is the probability that an individual who is under observation at a time t has an event at that time.

Note that, in contrast to the survivor function, which focuses on not having an event, the hazard function focuses on the event occurring.

Kaplan-Meier survival estimate
The Kaplan-Meier (KM) method is a non-parametric method used to estimate the survival probability from observed survival times (Kaplan and Meier, 1958).

The survival probability at time ti, S(ti), is calculated as follow:
Where,
S(ti) = S(ti-1)(1- (di/ni))
S(ti−1) = the probability of being alive at ti−1
ni = the number of patients alive just before ti
di = the number of events at ti
t0 = 0, S(0) = 1
The estimated probability (S(t)) is a step function that changes value only at the time of each event. It’s also possible to compute confidence intervals for the survival probability.

The KM survival curve, a plot of the KM survival probability against time, provides a useful summary of the data that can be used to estimate measures such as median survival time.

We’ll use two R packages:
survival for computing survival analyses
survminer for summarizing and visualizing the results of survival analysis
Install the packages
```R
install.packages(c("survival", "survminer"))
library("survival")
library("survminer")
```
We’ll use the lung cancer data available in the survival package.
```R
data("lung")
head(lung)

```
inst: Institution code
time: Survival time in days
status: censoring status 1=censored, 2=dead
age: Age in years
sex: Male=1 Female=2
ph.ecog: ECOG performance score (0=good 5=dead)
ph.karno: Karnofsky performance score (bad=0-good=100) rated by physician
pat.karno: Karnofsky performance score as rated by patient
meal.cal: Calories consumed at meals
wt.loss: Weight loss in last six months

Compute survival curves: survfit()
We want to compute the survival probability by sex.
The function survfit() [in survival package] can be used to compute the Kaplan-Meier survival estimate. Its main arguments include:
a survival object created using the function Surv()
and the data set containing the variables.
To compute survival curves, type this:
```R
fit <- survfit(Surv(time, status) ~ sex, data = lung)
print(fit)
```
n: total number of subjects in each curve.
time: the time points on the curve.
n.risk: the number of subjects at risk at time t
n.event: the number of events that occurred at time t.
n.censor: the number of censored subjects, who exit the risk set, without an event, at time t.
lower,upper: lower and upper confidence limits for the curve, respectively.
strata: indicates stratification of curve estimation. If strata is not NULL, there are multiple curves in the result. The levels of strata (a factor) are the labels for the curves.
```R
d <- data.frame(time = fit$time,
                  n.risk = fit$n.risk,
                  n.event = fit$n.event,
                  n.censor = fit$n.censor,
                  surv = fit$surv,
                  upper = fit$upper,
                  lower = fit$lower
                  )
head(d)
```
Visualize survival curves
We’ll use the function ggsurvplot() [in Survminer R package] to produce the survival curves for the two groups of subjects.

It’s also possible to show:
1. the 95% confidence limits of the survivor function using the argument conf.int = TRUE.
2. the number and/or the percentage of individuals at risk by time using the option risk.table. Allowed values for risk.table include: 
	1. TRUE or FALSE specifying whether to show or not the risk table. Default is FALSE.
	2. “absolute” or “percentage”: to show the absolute number and the percentage of subjects at risk by time, respectively. Use “abs_pct” to show both absolute number and percentage.
3. the p-value of the Log-Rank test comparing the groups using pval = TRUE.
4. horizontal/vertical line at median survival using the argument surv.median.line. Allowed values include one of c(“none”, “hv”, “h”, “v”). v: vertical, h:horizontal.

``` R
# Change color, linetype by strata, risk.table color by strata
ggsurvplot(fit,
          pval = TRUE, conf.int = TRUE,
          risk.table = TRUE, # Add risk table
          risk.table.col = "strata", # Change risk table color by groups
          linetype = "strata", # Change line type by groups
          surv.median.line = "hv", # Specify median survival
          ggtheme = theme_bw(), # Change ggplot2 theme
          palette = c("#E7B800", "#2E9FDF"))

```
# Links
https://www.sthda.com/english/wiki/survival-analysis-basics