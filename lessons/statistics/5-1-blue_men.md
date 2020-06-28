[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

**Question:**
---
In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters μ= 178 cm and σ= 7.7 cm for men, and μ= 163 cm and σ= 7.3 cm for women. In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range?  Hint:  usescipy.stats.norm.cdf.



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

mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
low = dist.cdf(177.8)    # 5'10"
high = dist.cdf(185.4)   # 6'1"
low, high, high-low
```


**Output:**
---
(0.48963902786483265, 0.8317337108107857, 0.3420946829459531)



**Explanation:**
---
0.4896 of the male population is shorter than 5'10", and 0.8317 of the male population its shorter than 6'1".
The difference between those numbers (~34%) is the portion of the male population between those heights. 