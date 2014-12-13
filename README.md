stata-last-ass
==============


*Question 1
reg ahe age
dis _b[_cons]
dis _b[age]
*As worker age increases by 1 year, on average the average hourly earning of the worker will go up by 0.60$

*Question 2
sca Bob = _b[age]*26 + _b[_cons]
dis Bob
sca Alexis = _b[age]*30 + _b[_cons]
dis Alexis

*Question 3
*Only 2.9% of the variation in average hourly earnings is explained by my model.
*No, age does not account for a large fraction of the variation in earnings across individuals.

*Question 4
reg ahe age if bachelor == 0
reg ahe age if bachelor == 1

*Question 6
reg ahe age female bachelor
dis _b[age]
*As worker age increases by 1 year, on average the average hourly earning of the worker will go up by 0.59$

*Question 7
*The results from the regression in (6) is not too substantively different from the results in (1)
*However, because the coefficient on age does change by 0.01$, we can conclude that the regression in (1) does suffer from omitted variable bias

*Question 8
sca Bob = _b[age]*26 + _b[_cons]
dis Bob
sca Alexis = _b[age]*30 + _b[female] + _b[bachelor] + _b[_cons]
dis Alexis

*Question 9
*Yes, gender and education are determinants of earnings. 
*The coefficient for both are very statistically significant with t-values > 4 for both.

*Question 10
graph twoway (lfit ahe age) (scatter ahe age)
graph rename Figure_1

*Question 11
gen logahe = log(ahe)
gen agesquared = age^2

reg logahe age female bachelor
sca fivetosixone = _b[age]*26 - _b[age]*25
dis fivetosixone
sca threetofourone = _b[age]*34 - _b[age]*33
dis threetofourone

*Question 12
reg logahe age agesquared female bachelor
sca fivetosix = _b[age]*26 + _b[agesquared]*26^2 - _b[age]*25 - _b[agesquared]*25^2
dis fivetosix
sca threetofour = _b[age]*34 + _b[agesquared]*34^2 - _b[age]*33 - _b[agesquared]*33^2
dis threetofour

*Question 13
clear

exit
