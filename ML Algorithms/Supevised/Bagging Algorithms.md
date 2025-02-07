### Links
https://www.analyticsvidhya.com/blog/2016/04/complete-tutorial-tree-based-modeling-scratch-in-python/#eight


### Random Forest
* Bootstrap sampling/Bagging - sampling of the input data with replacement. One-third of data is not used for training and set aside called out of bag samples.
* Bias remains same as that of a single decision tree
* Pasting - Term used when data or variables are samples without replacement
* Random Forest is a versatile machine learning method capable of performing both regression and classification tasks but it does not give precise continuous nature predictions. In case of regression, it doesn’t predict beyond the range in the training data, and that they may over-fit data sets that are particularly noisy.
* It also performs dimensional reduction methods, treats missing values, outlier values. 
* It has an effective method for estimating missing data and maintains accuracy when a large proportion of the data are missing.
* It has methods for balancing errors in data sets where classes are imbalanced.
* A group of weak models combine to form a powerful model. Predictions are made on the test sample (test sample is passed through each individual tree) based on aggregating the results from each individual tree
* Handles large data set with higher dimensionality.
* It usually has high accuracy on the training population and hence might over fit the model on the data.
##### Random Forest is a poor choice when
* Random forests don't train well on smaller datasets
* There is a problem of interpretability with random forest.
* Time taken to train random forests may sometimes be too huge as you train multiple decision trees
* In the case of a regression problem, the range of values response variable can take is determined by the values already available in the training dataset.

### Regularized Greedy Forests
https://arxiv.org/pdf/1109.0887.pdf
https://github.com/RGF-team/rgf/tree/master/python-package
* These produce less correlated predictions and do well in ensemble with other tree boosting models.
* RGF performs 2 steps:
  * Finds the one step structural change to the current forest to obtain the new forest that minimises the loss function (e.g. Least squares or logloss)
  * Adjusts the leaf weights for the entire forest to minimize the loss function


### Bagging Meta-estimator
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.BaggingClassifier.html#sklearn.ensemble.BaggingClassifier
* Bagging meta-estimator is an ensembling algorithm that can be used for both classification and regression (BaggingRegressor).
* Bootstrapping with all features

### Extra Trees
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.ExtraTreesClassifier.html#sklearn.ensemble.ExtraTreesClassifier

### Random Trees Embedding
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomTreesEmbedding.html#sklearn.ensemble.RandomTreesEmbedding














