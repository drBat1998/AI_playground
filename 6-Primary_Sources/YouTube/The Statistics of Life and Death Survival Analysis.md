Title: The Statistics of Life and Death Survival Analysis
Author: [[]]
Tags: #youtube #statistics 


# Notes
[[survival analysis]]
The surcical function
S(t) = P(T> or = t) - survival function equal to probability to survive the poin of time or longer.

Kaplan and Meier proposed using the conditional probability P(A|B)
P(T> or = 7) => P(T> or = 5) x P(T> or = 7, and T> or = 5), probability survive at or past day 5 and conditional probability survive bothe 5 and 7 day. 
if all live before day 5, the formula would look like
P(t>=7) = (1 - number die at day 7/number alive at day 5)
![[Screenshot 2025-11-24 at 11.25.36.png]]
[[Kaplan-Meier curve]]

Hazard - the probability of the even would happen in short period of time.
[[hazard function]]
![[Screenshot 2025-11-24 at 11.27.29.png]]

[[the proportional hazards model]]
![[Screenshot 2025-11-24 at 11.30.18.png]]
Cox
baseline hazard, when all the covariates equal zero (control)
e^Xb - change the hazard
# Links
https://youtu.be/C5BZA-0dloU?si=pFCsxLn54EI40CwP