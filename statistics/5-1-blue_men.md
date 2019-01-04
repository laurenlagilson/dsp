[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> The percentage of men within this range is 34.21%, see code below:  
```{python}
import scipy.stats

# We want just men - so use mu = 178 (Mean) and sigma = 7.7 (StD)
mu = 178
sigma = 7.7

# Generate normal dist using mu and sigma
normdist = scipy.stats.norm(loc=mu, scale=sigma)

# Change range into cm to match data
lowcm = 177.8
highcm = 185.4

# Get percentiles for low and high range
lowper = normdist.cdf(lowcm)
highper = normdist.cdf(highcm)

# Percentage of men in this range
percentage = (highper - lowper) * 100
print(f"{percentage.round(2)}%")
```
