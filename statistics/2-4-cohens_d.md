[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>> **The answers to the questions are as follows (code is presented at the bottom). An ipynb can be located in statistics folder under 2-4-cohens_d_code:**

**Part 1 - Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others.**  
By assessing the mean of the first born children with the mean of later born children, the data shows that first borns tend to be lighter.  

**Part 2 - Compute Cohen’s d to quantify the difference between the groups.**   
By using the code provided in ThinkStats to calculate Cohen's d, the difference is -0.088672927072602.

**Part 3 - How does it compare to the difference in pregnancy length?**   
Again by using the provided code, the difference is 0.028879044654449883 for pregnancy length. Although these are both categorised as very small by Cohen, 1988 and Sawilowsky, 2009, the differences show a negetive result for the difference in weight and a positive result for the difference in preganancy length. This shows that the mean weight of first borns is smaller than the mean weight of subsequent births (demonstrated in part 1). However, as the result is positive for the length of pregnancy, this shows that the mean pregnancy length for first borns is longer than those of other births.  

**Code for calculations**  
```{python}
import nsfg
import thinkstats2
import math

# Cohen's d from ThinkStats
def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()
    
    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)
    
    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d

# Statement to determine effect size using Cohen, 1988 and Sawilowsky, 2009 categories
def category(cohenresult):
    if 0.01 <= abs(cohenresult) < 0.2:
        return "Very Small"
    elif 0.2 <= abs(cohenresult) < 0.5:
        return "Medium"
    elif 0.5 <= abs(cohenresult) < 0.8:
        return "Large"
    elif 0.8 <= abs(cohenresult) < 1.2:
        return "Very Large"
    elif 1.2 <= abs(cohenresult) < 2.0:
        return "Huge"
    else:
        return "Value not in correct range, check calculation"

# Load data from pregnancy file & sort live births from this
pregfile = nsfg.ReadFemPreg()
live = pregfile[pregfile.outcome == 1]

# Sort into first born children and others
first = live[live.birthord == 1]
other = live[live.birthord != 1]


# Part 1 - Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others.

firstmean = first.totalwgt_lb.mean()
othermean = other.totalwgt_lb.mean()

if firstmean > othermean:
    print('First borns are heavier')
else: 
    print('First borns are lighter')
    
# Part 2 - Compute Cohen’s d to quantify the difference between the groups. 

x = CohenEffectSize(first.totalwgt_lb, other.totalwgt_lb)

print(f"Using Cohen's d the difference is: {x}")
print(f"Descriptor: {category(x)}")

# Part 3 - How does it compare to the difference in pregnancy length?

# Calculate Cohen d for pregnancy length
y = CohenEffectSize(first.prglngth, other.prglngth)

print(f"Using Cohen's d the difference is: {y}")
print(f"Descriptor: {category(y)}")
```
