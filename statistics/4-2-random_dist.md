[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> **The answers to the exercise are as followed and a copy of the code posted below. Please see 4-2-random_dist_code.ipynb in the statistics folder for visualisations of the plots.**   

**Exercise 2: The numbers generated by numpy.random.random are supposed to be uniform between 0 and 1; that is, every value in the range should have the same probability. Generate 1000 numbers from numpy.random.random and plot their PMF. What goes wrong?**   
When plotting the PMF of 1000 randomly generated numbers between 0 and 1, it is impossible to identify individual PMFs visually. Therefore by plotting the CDF, we can asssess whether the distribution is uniform amongst the randomly generated numbers.  

**Part 2 - Now plot the CDF. Is the distribution uniform?**  
The distribution is uniform as demonstrated by the strong positive correlation in the plot. With more randomly generated numbers we can expected a straighter line in the plot.  

**Code presented below:**   
```{python}
import numpy as np
import nsfg
import first
import thinkstats2
import thinkplot

# Generate 1000 numbers from numpy.random.random and plot their PMF. What goes wrong?
x = np.random.random(1000)

# Calculate and plot pmf
pmf = thinkstats2.Pmf(x)
thinkplot.Pmf(pmf, linewidth=0.1)
thinkplot.Config(xlabel = 'Random number', ylabel = 'PMF')

# With so many numbers, we cannot read the PMF from the plot with ease.

# Plot CDF (Cumulative Distribution Function)
cdf = thinkstats2.Cdf(x)
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel= 'Random Number', ylabel = 'CDF')

# Clearly shows that the distribution is uniform, as there is strong positive correlation
```

