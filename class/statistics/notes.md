# **terms**
### standard error
- standard error is represents how much a sample parameter is likely to deviate from the true population parameter
### standard deviation
- only applies to a normal distribution
- how much, on average does the data vary from the mean
- the standard deviation is the standard error of a normal distribution
### random sampling
- sample is random selected from the population
### 10% rule
- rule for independence
- sample size is no more than 10% of the population the sample is derived from
### central limit theorem
- only applies to sampling distributions for the mean
- sample size must be greater than or equal to 30

# 1 sample t interval for population mean
### use case
- sample size is less than 30
- population standard deviation is unknown
### conditions
- data must be random ([[#random sampling]])
- data must be independent ([[#10% rule]])
	- does not apply when sample is not a random sample using random assignment
- data must be normal
	- meet the [[#central limit theorem]]
	- already be normal
	- data has no outliers and is not crazy
### calculations
$s = \text{standard deviation of sampling distribution}$
$stderr = \frac{s}{\sqrt n}$
$t^* = (\text{find from table B, with df} = n - 1, \text{confidence level} = 1.0 - \alpha)$
> $t^*$ is required to adjust the standard error calculation, since we are using the *sample* standard deviation instead of the *population* standard deviation. $df$ stands for *degrees of freedom*.
> Stapplet/calculator can also be used to calculate $t^*$.

$\overline x \pm t^* \cdot stderr$
# 1 sample t test for population mean
### use case
- see [[#1 sample t interval for population mean#use case]]
### conditions
- see [[#1 sample t interval for population mean#conditions]]
### calculations

> A matched pairs difference experiment can be decomposed into a 1 sample t test for population mean with $\mu_0 = 0$.

