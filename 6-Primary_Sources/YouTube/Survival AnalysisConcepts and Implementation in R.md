Title: Survival AnalysisConcepts and Implementation in R
Author: [[]]
Tags: #youtube #statistics #programming 


# Notes
Part 1 What is Censoring? - https://youtu.be/vX3l36ptrTU?si=eTJsVvLaaXuvfIkT
y = Surv(t,e) t -time, e = event 0 -no, 1 - yes
Censoring - we don't no does the event occure. 
Right censoring
Left censoring

 Part 2 Survival Function, Hazard, & Hazard Ratio - https://youtu.be/MdmWdIV5k-I?si=QP7epVQpvshuz5bW
S(t) = P(T>t) , so survival function is the probbability of survive beyound time t.

Hazard 
h(t)= P(T<t+delta| T>t), prob of dying in next few seconds given alive now.

Hazard ratio
hr = h, x=1/h,x=0, hazard of person exposud to damage compere to who is not.

Survival Function
Part 3 | Kaplan Meier vs. Exponential vs. Cox Proportional Hazards (Pros & Cons) -
https://youtu.be/K7bmmbD7KIg?si=TmnO6FDKT71qTi2D

Exponential surv S(t) = e^-haz

|     | KM model                                                                         | exponential surv                                              | Cox P.H. model                                                  |
| --- | -------------------------------------------------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| +   | simple to interpret; can estimate S(t)                                           | can estimate S(t) and hazard ration                           | Hazard can fluctuate with time; can estimate the hazzard ration |
| -   | no functional form; can not est Hazard ration; only include a few, categorical X | not always realistic, due to the assumtion of constant hazard | can not est S(t)                                                |

Kaplan Meier Model https://youtu.be/VJPPeUpyC6c?si=ReXbm-Aj-ZK9dn3s
https://youtu.be/6_AF9mMuk9E?si=p86Liy2BvXDdOn2w

```R
library("survival")

fit <- survfit(Surv(Time, Death) ~ 1, data = data)

summary(fit)

```

Exponential Model (Intro to Regression Models for Survival) https://youtu.be/T_goHnU8Eu4?si=q7z4IPDXrYplEZ5t
Poisson process (event that occur inded over time) rate = lambda = y/t
Poisson distribution 
Let y = number of occur in time t
y ~ poisson(lambda)
f(y) = e-lambda(lmda)y/y!
exponent distribute
F(t) = P(T=<t) = lambda e^-lambdat

S(t) = P(T>t) = 1- P(T<=t) = e^-lamdat
where lambda is hazard

Haz = e^exp
lm(Haz) = linear funtion

# Links
[[survival analysis]]