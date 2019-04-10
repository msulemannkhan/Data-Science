luminol - https://github.com/linkedin/luminol

Moving Avergae Based - https://www.datascience.com/blog/python-anomaly-detection

https://github.com/rob-med/awesome-TS-anomaly-detection
 
Surveillance Algos - https://www.ml.cmu.edu/research/dap-papers/das_kdd2.pdf <br/>
https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/1472-6947-10-74 <br/>

##### Why use Surveillance algorithms
For each possible organism we have a corresponding time series. A particular disease such as an influenza outbreak, will affect the count of multiple syndromes. In this case, we need to simultaneously consider all the variables to detect the presence of an anomaly. To combine information from multiple time series we examine a novel technique which is simple but powerful. Composite time series are constructed by simple addition and subtraction of the individual time series. We search through all possible composite time series for an anomaly. Using just simple arithmetic operations like addition and subtraction provides an easy physical interpretation of the composite series. It is also able to detect anomalies sooner than other traditional methods
* Vector Auto Regression
* Vector Moving Average
* Hotelling T2 Test

* EARS algo, Farrington flexible are applied on weekly data
* CUSUM - Detect a shift in the mean of a process. CUSUM maintains a cumulative sum of deviations from a reference value r.
* Modified CUSUM - Model non-stationary time series variables
* Multivariate CUSUM





