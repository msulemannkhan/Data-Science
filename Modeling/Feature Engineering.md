### Links
Techniques by kind of Data https://github.com/dipanjanS/practical-machine-learning-with-python/tree/master/notebooks/Ch04_Feature_Engineering_and_Selection <br/>
https://www.kdnuggets.com/2018/12/feature-building-techniques-tricks-kaggle.html <br/>
https://towardsdatascience.com/understanding-feature-engineering-part-1-continuous-numeric-data-da4e47099a7b <br/>
https://medium.com/open-machine-learning-course/open-machine-learning-course-topic-6-feature-engineering-and-feature-selection-8b94f870706a <br/>

### What makes a good feature?
* Be related to the objective - Have a reasonable hypothesis on why a feature is related to the problem we are solving
* Be know at prediction-time - If data is delayed by n hrs, we have train the data as of n hrs ago. eg-collection date time vs Created date time. Real-time modeling should be based on only Created DateTime and not collection date time as data need to eb available at prediction-time and data is available only at CreatedDateTime and not CollectionDateTime
* Be numeric with meaningful magnitude - Neural networks are weighing and adding machines. Ordinal is not numeric either. Auto-encoding or embedding is used to convert character vars to meaningful numerics
* Have enough examples - Rule of Thumb is to have atleast 5 examples of any particular value before we use it in the model. Eg-For each category of a variable there should be atleast 5 values of Prediction=0 & Prediction=1. For a numeric value - discretize bands and see if there are atleast 5 examples of each in that particular bin
* Bring human insight to problem 
</br>
Handling diff features: https://github.com/tensorflow/docs/blob/master/site/en/r1/guide/feature_columns.md


### Feature Crosses
Feature crosses memorize data but goal of ML is generalization. Feature crosses memorize and only work on large datasets. Large the data, more powerful the feature crosses are
* Brings power of non-linearity to linear models as feature crosses eg-x1x2 or x1^2 are non-linear
* Crossing is only possible with categorical or discretized columns.
* If var1 has 3 categeories, Var2 has 5 categories, the number of features crosses=15 categories. But if we mention less number of hash buckets, it can help us control sparsity & collisions where a group of a few feature crosses fall into 1 hash bucket. To increase sparsity u can choose 2N hash buckets, to dec u can choose sq root N
* Embedding - Instead of just one-hot encoding of feature crosses i.e 15 combination as in above example. Pass them through a dense layer that creates embedding. Embeddings are real valued numbers because they are weighted some of the feature crosses and the weights that go into the embedding layer are learned from the data. 

### Numeric
When data is missing in the Numeric column - For that column create a new extra column to identify if the data is missing or not. If data is missing then 1 otherwise 0
* Values as it is
* Unique Counts/Freq
* Binning
* Binarize based on a cut-off
* Rounding off - High precision may not be required
* Fraction part of a numeric value
* Interaction between variables
* Binning
* Transformation - log, box-cox, rank
  * Log transformation works on only +ve values
  * Box-Cox works on only +ve values (can be used on 0 & -ve values using a constant value)
  * Yeo-Johnson Power Transformations (extension of Box cox transformation that allows for 0 and -ve values) code: PowerTransform and setting the “method” argument to “yeo-johnson” 
* Scaling - Imp for non-tree based models - Linear, Logitic, Neural Nets, KNN, K-Means, SVM. Without feature scaling, gradient descent will require a lot more steps to reach the minima. Feature scaling is not mandatory to scale the features before training a decision tree or random forest model because their cost function (Gini index, Entropy etc.) is not distance-based. Decision Tree is only splitting a node based on a single feature, it is not influenced by other features
  * Fit the scaler on the training data and then use it to transform the testing data
  * To [0,1] - MinMaxScaler/Normalization - Normalization is good to use when you know that the distribution of your data does not follow a Gaussian distribution. This can be useful in algorithms that do not assume any distribution of the data like K-Nearest Neighbors and Neural Networks.
  * StandardScaler - Mean 0, stdv 1 - Standardization, on the other hand, can be helpful in cases where the data follows a Gaussian distribution. However, this does not have to be necessarily true. Also, unlike normalization, standardization does not have a bounding range. So, even if you have outliers in your data, they will not be affected by standardization. For SVM, try using StandardScaler as SVM with RBF kernel assumes that all the features are centered around zero and variance is of the same order </br>
  Although normalization via min-max scaling is a commonly used technique that is useful when we need values in a bounded interval, standardization can be more practical for many machine learning algorithms. The reason is that many linear models, such as the logistic regression and SVM, [...] initialize the weights to 0 or small random values close to 0. Using standardization, we center the feature columns at mean 0 with standard deviation 1 so that the feature columns take the form of a normal distribution, which makes it easier to learn the weights. Furthermore, standardization maintains useful information about outliers and makes the algorithm less sensitive to them in contrast to min-max scaling, which scales the data to a limited range of values.
  * Robust Scalar: Based on Q1 & Q3
* Normalization using Standard Deviation
* Log based feature/Target: use log based features or log based target function

* Log Transformer
  * Helps with skewness
  * No predetermined range for scaled data
  * Useful only on non-zero, non-negative data
* Min-Max Scaler or Normalization
  * Rescales to predetermined range [0–1]
  * Doesn’t change distribution’s center (doesn’t correct skewness)
  * Sensitive to outliers
* Max Abs Scaler
  * Rescales to predetermined range [-1–1]
  * Doesn’t change distribution’s center
  * Sensitive to outliers
* Standard Scaler
  * Shifts distribution’s mean to 0 & unit variance
  * No predetermined range
  * Best to use on data that is approximately normally distributed
* Robust Scaler
  * 0 mean & unit variance
  * Use of quartile ranges makes this less sensitive to (a few) outliers
  * No predetermined range
* Power Transformer
  * Helps correct skewness
  * 0 mean & unit variance
  * No predetermined range
  * Yeo-Johnson or Box-Cox
  * Box-Cox can only be used on non-negative data

### Categorical 
https://towardsdatascience.com/all-about-categorical-variable-encoding-305f3361fd02 <br/>
![](https://miro.medium.com/max/2100/0*NBVi7M3sGyiUSyd5.png)
* Encoding - One-hot encoding: This approach can be adopted for any machine learning algorithm that looks at ALL the features at the same time during training. For example, support vector machines and neural networks as well and clustering algorithms. In tree-based methods, we will never consider that additional label if we drop. Thus, if we use the categorical variables in a tree-based learning algorithm, it is good practice to encode it into N binary variables and don’t drop.
* When data is missing in the category column - A 5 category var usually gets 5 binary columns of one-hot encoding. But if there are missing values then 6 binary variables needs to be created
* High Cardinal categorical features - 
  * When dealing with a binary target: https://www.kdnuggets.com/2016/08/include-high-cardinality-attributes-predictive-model.html <br/>
    Pi = number of positive labels within each category of Categorical Var <br/>
    Ni = number of negative labels within each category of Categorical Var <br/>
    * (Pi / Ni)
    * Supervised Ratio: (Pi / Freq of a category of a categorical var).If training set consists of 100 customers in ZIP code 10009, 5 of which churned (so Pi=5 and Ni=95) then the transformed value is 0.05. 
    * Weight of evidence - WOE equation = ln( (Pi/Total Positive Labels)/(Ni/Total Negative Labels) ) = ln(Event%/NonEvent%)
    * Information Value (IV) = Σ (Event% - NonEvent%) * WOE   
  * Way Catboost deals with categories - https://catboost.ai/docs/concepts/algorithm-main-stages_cat-to-numberic.html
  * Embeddings  
* Cyclical Features - day, week, month, year
  * CosSin encoding
  
### Binary Variables


### Date and Time
* Time passed since a particular event -  Time passed after last holiday
* Time/Days left until next holidays
* Diff between dates
* Day of the week
* Month of Booking
* Year of Booking
* Time based Features like "Evening", "Noon", "Night", "Purchases_last_month", "Purchases_last_week" etc.
* Is weekend or not
* Was the date the end of a quarter?, Was the day a holiday?, Were the Olympics/Rare events taking place on said date?
* cash withdrawals can be linked to a pay day; the purchase of a metro card, to the beginning of the month.
* In general, when working with time series data, it is a good idea to have a calendar with public holidays, abnormal weather conditions, and other important events.
* There also exist some more esoteric approaches to such data like projecting the time onto a circle and using the two coordinates.
def make_harmonic_features(value, period=24):
    value * = 2 * np.pi / period 
    return np.cos(value), np.sin(value)

from scipy.spatial import distance
euclidean(make_harmonic_features(23), make_harmonic_features(1)) 
result: 0.517


### Time Series
Generates automatic feature engineering for time series data - https://github.com/blue-yonder/tsfresh <br/>
https://tsfresh.readthedocs.io/en/latest/text/list_of_features.html <br/>
* lag features - 1,2,3,5,12 months - https://github.com/anhquan0412/Predict_Future_Sales/blob/master/generate_lag_features.ipynb
* Holiday Boolean features 

### Web data
* operating system
* Is mobile or not
* Browser
* lag behind the latest version of the browser
* Did user viisted the website previously?
* Count of user views
* number of distinct docs visited by user


### Geographic data - Lat, Lon
* Haversine Distance Between the Two Lat/Lons
* Manhattan Distance Between the two Lat/Lons
* Bearing Between the two Lat/Lons

* Distances (great circle distance and road distance calculated by the routing graph)
* Number of turns with the ratio of left to right turns, number of traffic lights, junctions, and bridges 
* Complexity of the road - graph-calculated distance divided by the GCD
* 
* Proximity of a point to the subway
* Number of stories in the building
* Distance to the nearest store
* Number of ATMs around, etc. 
* Height above sea level, etc. 

### Search based data
* Attribute Features
  * Whether the product contains a certain attribute (brand, size, color, weight, indoor/outdoor, energy star certified …)
  * Whether a certain attribute matches with the search term
* Meta Features
  * Length of each text field
  * Whether the product contains attribute fields
  * Brand (encoded as integers)
  * Product ID
* Matching
  * Whether search term appears in product title / description / attributes
  * Count and ratio of search term’s appearance in product title / description / attributes
  * Whether the i-th word of search term appears in product title / description / attributes
* Text similarities between search term and product title/description/attributes
  * BOW Cosine Similairty
  * TF-IDF Cosine Similarity
  * Jaccard Similarity
  * Edit Distance
  * Word2Vec Distance (I didn’t include this because of its poor performance and slow calculation. Yet it seems that I was using it wrong.)

### Sales Transactional Data
* Most recent transaction related details - when did he buy, what did he buy etc
* Freq
* Monetary
* Average Time Difference between transactions
* Average number of Transactions per month
* Sales
* Number of Disinct Items
* Total number of Transactions
* Percantage of Discounted transactions - total discounted trans/Total Trans
* Maximum Discount Amount
* Total Discount Amount
* Identify first transaction - first. In SAS
* Maximum Sales value
* Minimum Sales Value
* Difference between Time period end date and Last transaction date
* Most Recent Transaction's Sales value
* Average Transactional Value = sales/transactions
* Average items per transaction= Quantity Sold/Transactions
* Volume - Quantity Sold
* Tenure of a Customer (based on their Start Date)
* Age of the firm
* Number of Employees
* Size of the firm (Revenue)
* Location
* Frequent mode of purchase - website/Sales person/ phone
* Participation in Events
* Distance in miles between prospect location and event location

### Ride-sharing - Trips Forecast
* App views
* Riders
* Temperature
* Wind Speed
* Wind Bearing



### Automated Feature Engineering - Deep Feature Synthesis
https://docs.featuretools.com/automated_feature_engineering/afe.html#

* Featuretools module in python - Deep feature synthesis
* 

    
    
    
    





