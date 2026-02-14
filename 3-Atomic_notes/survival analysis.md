Title: Survival ainalysis
tags: #atomic_note


# Notes
Basic concepts:

Survival time - the time from the start to the end of the experiment.

Event is a binary thing that tells whether the cell has died or not. 

Censoring is when the cell survives longer than the experiment is going, so we can not tell does the cell survives or not. Event = 0, survival time = last minutes of experiment.

Survival function (S(t)) is the possibility of the cell being alive.  S(0), the start, where all cells are alive. S(t) always decreases.

Hazard function (h(t)) is the probability of death rate. If the h(t) is low, the cells die slowly, and the curve changes to the right. If the h(t) is high, the cells die fast. 

Kaplan-Meier survival estimate
The Kaplan-Meier (KM) method is a non-parametric method used to estimate the survival probability from observed survival times 
S(ti​)=S(ti−1​)×(1−di/ni​​)
Survival at time t_i = survival before that time × (probability NOT to die at t_i).

The KM survival curve is the step function. If the cells haven't died, survival is flat; if the cell dies, the line would decrease, the bigger the decrease, the more cells had died. 
KM includes censored observations in the risk set up to the time they are censored, but censored observations do not cause drops in the survival curve.

# Links
[[Survival Analysis Basics]]

[[Survival AnalysisConcepts and Implementation in R]]