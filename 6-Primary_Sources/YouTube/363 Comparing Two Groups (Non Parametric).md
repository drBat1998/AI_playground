Title: 363 Comparing Two Groups (Non-Parametric)
Author: [[DigitalSreeni]]
Tags: #youtube #statistics #programming 


# Notes

Assumtion - minimal
Data type - any
More robust outline
Power - lower power generally
Compares distributions and medians

When to use non-parametric tests
1. When parametric test assumptions are violated:
	- Data is not normally distributed
	- unequal variances between groups
	- small sample sizes
	- presence of substantial outliers
2. When working with ordinal or rank data
3. When comparing shapes of distributions, not just central tendency
4. As a complementary analysis to the parametric test for robustness.

Alternative to the independent samples t-test
- [[Mann-Whitney U test]] calculation
	- sign the ranks to all values
	- sum values for each group
	- use a formula
	- ![[Screenshot 2025-08-01 at 13.23.15.png]]
	- U statistic
	- p-value
	- effect size r 
		- 0.1 - small
		- 0.3 - medium effect
		- 0.5 - large effect

A dependent non-parametric test for two groups is:
	Wilcoxon Signed-Rank test
	![[Screenshot 2025-08-01 at 13.31.42.png]]

``` python
# Mann-Whitney U test
from scipy.stats import mannwhitneyu
# Wilcoxon signed rank test
from scipy.stats import wilcoxon
# Fisher's exact test
from scipy.stats import fisher_exact
# Median test
from scipy.stats import median_test

```
![[Screenshot 2025-08-01 at 13.34.49.png]]
# Links
https://youtu.be/sc2WN0AqhIc?si=86NYsf2-I8dUepIJ