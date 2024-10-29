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
### large counts condition
- only applies to sampling distributions for the mean
- sample size must be greater than or equal to 30

# **1 sample z interval for population mean**
### conditions
- data must be random ([[#random sampling]])
- data must be independent ([[#10% rule]])
- data must meet the [[#large counts condition]] or already be normal
### calculations
$s = \text{standard deviation of sampling distribution}$
$stderr = \frac{s}{\sqrt n}$
$t^* = (\text{find from table B, with df = n - 1})$
> $t^*$ is required to adjust the standard error calculation, since we are using the *sample* standard deviation instead of the *population* standard deviation. $df$ stands for *degrees of freedom*.

$\overline x \pm t^* \cdot stderr$
