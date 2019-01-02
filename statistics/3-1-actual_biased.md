[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> Please refer to 3-1-actual_biased_code.ipynb in the statistics folder for visualisation of the plots. However, a copy of the code is posted here.
```{python}
import math
import nsfg
import thinkstats2
import thinkplot

# Read in file
file = nsfg.ReadFemResp()

# Part 1 - Use the NSFG respondent variable NUMKDHH to construct the actual distribution for the number of children 
# under 18 in the household.
# pmf = probability mass function 

pmf = thinkstats2.Pmf(file.numkdhh, label = 'actual')

# Plot distribution 
thinkplot.Pmf(pmf)
thinkplot.Config(xlabel = 'No. of children', ylabel = 'PMF')

# Part 2 - Now compute the biased distribution we would see if we surveyed the children and asked them how many 
# children under 18 (including themselves) are in their household.

# define BiasPmf function from ThinkStats book
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label = label)
    
    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
    new_pmf.Normalize()
    return new_pmf

# Create biased pmf using function & plot
biased_pmf = BiasPmf(pmf, label='biased')
thinkplot.Pmf(biased_pmf)

# Part 3 - Plot the actual and biased distributions, and compute their means. As a starting place, you can use chap03ex.ipynb.

thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Show(xlabel='Number of children', ylabel='PMF')

# Compute means 
print(f"The actual mean is: {pmf.Mean()}")
print(f"The biased mean is: {biased_pmf.Mean()}")
```
