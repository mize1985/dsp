[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

**Question:**
---
Using the variable totalwgt_lb, investigate whether first ba-bies are lighter or heavier than others. Compute Cohen’s d to quantify the difference  between  the  groups. How  does  it  compare  to  the  difference  in pregnancy length?



**Code:**
---
```{python}
import numpy as np
import nsfg
import first
import thinkplot
import thinkstats2
import random
import scipy.stats

preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]
firsts = live[live.birthord == 1]
others = live[live.birthord != 0]

print("Cohen's d of effect of being a first birth on birth length:",
     CohenEffectSize(firsts.prglngth,others.prglngth))

print("Cohen's d of effect of being a first birth on birth weight:",
     CohenEffectSize(firsts.totalwgt_lb,others.totalwgt_lb))

print("Cohen's d for birth weight / Cohen's d for birth length:",
     CohenEffectSize(firsts.totalwgt_lb,others.totalwgt_lb)/CohenEffectSize(firsts.prglngth,others.prglngth))

def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
```


**Output:**
---
Cohen's d of effect of being a first birth on birth length: 0.01478582021484608
Cohen's d of effect of being a first birth on birth weight: -0.045694240659125175
Cohen's d for birth weight / Cohen's d for birth length: -3.0904095948119745
