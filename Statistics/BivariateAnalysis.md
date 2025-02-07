### 2 Quantitative Variables
* Scatter plot - Correlation
* Line Graph - X-axis is time usually

##### Covariance 
Variance between 2 variables. Indicates the extent to which two random variables change in tandem. Lies between -∞ and +∞. </br>
Cov(X,Y) = Σ(Xi-Xavg)(Yi-Yavg) / (n-1) </br>

##### Correlation
Correlation refers to the scaled/Normalized form of covariance. Measure used to represent how strongly two random variables are related. Indicates the extent to which two variables move together. Lies between -1 and +1. Not influenced by change of scale and dimensionless.  </br>
Pearson's R
Corr(X,Y) = Cov(X,Y)/XstdDev.YstdDev  </br>

### 2 Categorical Variables
* Cross Table - Freq or % 
* Stacked bar plot - Freq or %
* Chi-square test
* Correlation - Cramer's V is measure of Association between 2 Categorical Vars. Norminal variation of Pea

##### Chi-square test - Significance test of association between 2 Cat vars
chi square formula chisquare = Σ( (Obs-Expected)^2 / Expected )
* p < 0.05 - Variables have association
* But as sample size goes up, p-value gets smaller but Cramer's V stays same. So, Cramer's V is chosen

##### Cramer's V - Measures Strength of Association between 2 Categorical Vars. 
* Output ranges from [0,1], where 0 means no association and 1 is full association. (Unlike correlation, there are no negative values, as there’s no such thing as a negative association. Either there is, or there isn’t)
* Like correlation, Cramer’s V is symmetrical — it is insensitive to swapping x and y. 
  * curse of symmetry - Extracting output of 1 var using another variable is lost in symmetrical measurement

##### Theil’s U - Asymmetric measure of association between categorical vars
https://towardsdatascience.com/the-search-for-categorical-correlation-a1cf7f1888c9 </br>
Theil’s U, also referred to as the Uncertainty Coefficient, is based on the CONDITIONAL ENTROPY between x and y — or in human language, given the value of x, how many possible states does y have, and how often do they occur. 
* Output ranges from [0,1], but unlike Cramer’s V, it is asymmetric, meaning U(x,y)≠U(y,x) (while V(x,y)=V(y,x), where V is Cramer’s V)


### Quantitative & Categorical Variables
* Box plot comparision between the groups of Categorical variables
* T-test
* Anova
* Correlation Ratio - eta

##### Correlation Ratio
https://towardsdatascience.com/the-search-for-categorical-correlation-a1cf7f1888c9 </br>
* It is defined as the weighted variance of the mean of each category divided by the variance of all samples
* Given a continuous number, how well can you know to which category it belongs to?
* Output ranges from [0,1]



