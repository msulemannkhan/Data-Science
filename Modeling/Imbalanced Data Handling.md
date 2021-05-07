### Links
https://towardsdatascience.com/model-performance-cost-functions-for-classification-models-a7b1b00ba60 <br/>
https://www.kdnuggets.com/2016/08/learning-from-imbalanced-classes.html <br/>
https://www.kdnuggets.com/2017/06/7-techniques-handle-imbalanced-data.html <br/>
https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/ <br/>
https://www.analyticsvidhya.com/blog/2017/03/imbalanced-classification-problem/ <br/>

TEST nor VALIDATION set should never be undersampled or over-sampled. Only Training data should be over-sampled/under-sampled <br/>
Perform oversampling during cross-validation, i.e. for each fold, oversampling is performed before training, and this process is repeated for each fold.- https://www.researchgate.net/publication/328315720_Cross-Validation_for_Imbalanced_Datasets_Avoiding_Overoptimistic_and_Overfitting_Approaches <br/>

### Disadvantages of Imbalanced data set:
A few classifier algorithms have bias towards classes that have more number of instances.They tend to only predict the majority class data.
The features of the minority class are treated as noise and are often ignored. Thus, there is a high probability of misclassification of the minority class as compared to the majority class.

## Techniques
* Do Nothing and use models that can handle imbalance like XGBoost
* In NLP, translate sentence from English to different language and then back to English. This way same sentence will be written using different words. Input text  – “warning for using windows disk space”. Data Augmented text – “Warning about using Windows storage space”
* Sampling - Perform oversampling during cross-validation, i.e. for each fold, oversampling is performed before training, and this process is repeated for each fold. (OR) Perform oversampling only on Train data and not on Validation & Test
  * Oversample the minority class - SMOTE, ADASYN https://medium.com/coinmonks/smote-and-adasyn-handling-imbalanced-data-set-34f5223e167   https://www.researchgate.net/publication/328315720_Cross-Validation_for_Imbalanced_Datasets_Avoiding_Overoptimistic_and_Overfitting_Approaches
    * SMOTE, ADASYN, Borderline-SMOTE, Safe-Level-SMOTE, SMOTE+TL, SMOTE+ENN, ADOMS, CBO, AHC, MWMOTE, SPIDER
  * Undersample the majority class.
  * Synthesize new minority classes - ROSE & DMwR packages in R.
  * Build n models that use all the samples of the rare class and n-differing samples of the abundant class. Eg: Given that you want to ensemble 10 models, you would keep e.g. the 1.000 cases of the rare class and randomly sample 10.000 cases of the abundant class. Then you just split the 10.000 cases in 10 chunks and train 10 different models.
  * Above appraoch of ensembling can be fine-tuned by playing with the ratio between the rare and the abundant class. The best ratio  heavily depends on the data and the models that are used. But instead of training all models with the same ratio in the ensemble, it is worth trying to ensemble different ratios.  So if 10 models are trained, it might make sense to have a model that has a ratio of 1:1 (rare:abundant) and another one with 1:3, or even 2:1.
* Anomaly Detection
* Adjust the decision threshold.
* Adjust the class weight (misclassification costs) - Weighted logloss & 
* Modify an existing algorithm to be more sensitive to rare classes.
* Cluster the abundant class - Instead of relying on random samples to cover the variety of the training samples, he suggests clustering the abundant class in r groups, with r being the number of cases in r. For each group, only the medoid (centre of cluster) is kept. The model is then trained with the rare class and the medoids only.
* Class weights in model.fit

### SMOTE
* Synthetic data generation to increase the number of samples in the minority class.
* First it finds the n-nearest neighbors in the minority class for each of the samples in the class . Then it draws a line between the the neighbors an generates random points on the lines.
* In the below case 5 nearest neighbours close to x1 are identified and sysnthetic samples are generated on each of the lines between x1,x2; x1,x3; x1,x4; x1,x5; x1,x6
![](https://cdn-images-1.medium.com/max/800/1*6UFpLFl59O9e3e38ffTXJQ.png)

### ADASYN 
* Its a improved version of Smote. What it does is same as SMOTE just with a minor improvement.
* After creating those sample it adds a random small values to the points thus making it more realistic. In other words instead of all the sample being linearly correlated to the parent they have a little more variance in them i.e they are bit scattered.

### Tomek Links - under sampling
https://www.analyticsvidhya.com/blog/2020/07/10-techniques-to-deal-with-class-imbalance-in-machine-learning/
Tomek links are pairs of very close instances but of opposite classes. Removing the instances of the majority class of each pair increases the space between the two classes, facilitating the classification process.
Tomek’s link exists if the two samples are the nearest neighbors of each other

### ENN (Edited Nearest Neighbour) - undersampling technique 
It removes the instances of majority class on the border or boundary whose predictions made by the KNN algorithm are different from the other majority class points.

### Imabalanced data handling - Oversampling & Undersampling combined
https://towardsdatascience.com/stop-using-smote-to-handle-all-your-imbalanced-data-34403399d3be
* SMOTE with ENN
* SMOTE with Tomek

### SMOTE with Tomek
https://towardsdatascience.com/stop-using-smote-to-handle-all-your-imbalanced-data-34403399d3be </br>
For an imbalanced dataset, first SMOTE is applied to create new synthetic minority samples to get a balanced distribution. Further, Tomek Links is used in removing the samples close to the boundary of the two classes, to increase the separation between the two classes. </br>
Implementation: from imblearn.combine import SMOTETomek

### SMOTE with ENN
https://towardsdatascience.com/stop-using-smote-to-handle-all-your-imbalanced-data-34403399d3be </br>
First SMOTE is applied to create synthetic data points of minority class samples, then using ENN the data points on the border or boundary are removed to increase the separation of the two classes.


### Evaluation Metrics
* Always test(Test set) on original distribution 
* ROC-AUC, Precision-Recall, Lift or Gain curves, F1 score, MCC(Corr coeff between observed & predicted binary classifications.
* Decision threshold on predict_proba
* Accuracy is not a valid measure of model performance in case of imbalanced data as if True outcomes is just 5% of the whole population, even if all predicted as False, the accuracy will still be 100-5=95%





