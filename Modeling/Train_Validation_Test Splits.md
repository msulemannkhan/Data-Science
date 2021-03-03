### Links
Train a new model on all available data https://machinelearningmastery.com/train-final-machine-learning-model/ <br/>
Train-Validation-Test https://towardsdatascience.com/train-validation-and-test-sets-72cb40cba9e7 <br/>
DONT split Train & Test based on Time https://discuss.analyticsvidhya.com/t/is-it-wise-to-split-training-and-test-dataset-based-on-time-year/2967/4 <br/>
Split data coming from DIFFERENT distributions https://www.kdnuggets.com/2019/01/when-your-training-testing-data-different-distributions.html <br/>
TEST nor VALIDATION set should never be undersampled or over-sampled. Only Training data should be over-sampled/under-sampled https://kiwidamien.github.io/how-to-do-cross-validation-when-upsampling-data.html <br/>


### Avoid Common Errors 
* Lack of generalization - Create 3 identically distributed Machine Learning data sets such that it is repeatable
* Use stratify and random state options
* Repeatable Datasets - use farm_fingerprint function on dates etc
https://cloud.google.com/bigquery/docs/reference/standard-sql/hash_functions <br/>
https://github.com/GoogleCloudPlatform/training-data-analyst/blob/master/courses/machine_learning/deepdive2/launching_into_ml/solutions/repeatable_splitting.ipynb <br/>
https://github.com/sandhyaparna/training-data-analyst/blob/master/courses/machine_learning/deepdive/02_generalization/create_datasets.ipynb  <br/>
https://googlecoursera.qwiklabs.com/focuses/25429?locale=en <br/>
* Use Train dtaa for EDA but apply Cleaning & Pre-processing on both train & test data 
* Healthcare Data splitting challenges
  * Patient Overlap - When patient comes twice and have 2 xrays and wears a necklace both the times, but we feed one of the xray into Train and other into Test, there is a high possibility of memorization of unique aspects like necklace in this case and makes the prediction similar to label in Train set. Make sure that a patients xrays are all in either Train set or Test set but not distributed across both Train & Test. SPLIT BY PATIENT.
  * Set sampling - Stratified sampling to get label=1 even when it is rarely occuring. AI for Medical Diagnosis video suggests to take 50% observations of label=1, 50% observations of label=0 for both Test and Validation set (Validation set should reflect the same sampling distribution seen in Test set) and all the remaining observations as Training set. This ensures that the model will have sufficient numbers to get a good estimate of the performance of the model on both non-disease and on disease samples. https://www.coursera.org/learn/ai-for-medical-diagnosis/lecture/iiAK1/sampling
  * Ground Truth - Consensus voting i.e Humans are asked to determine the outcome and majority voting is used. Use additional medical testing.

### Splitting
* Split data into Train & Test - Stratified splits if the data is imbalanced
* Train data is used for development + selection of models. Test set is used to report results. Train data is split into train & Validation, train is used for development, validatiion is used for tuning & selection of models. When Train is split into Train & Validation multiple times, it is called cross-validation
* Train set can be called development set
* Validation can be called tuning set (hyper paramter tuning is performed based on test data) or dev set
* Test set is called holdout or validation set
* Use Train data to perform cross-validation. A seperate Test set makes more sense when you use cross-validation or manully change the model hyperparameters based on the results of your model on the validation set. 
* Size of validation set within cross-validation is dependent on the overall data and model that you are training. Some models need substantial data to train upon, so in this case you would optimize for the larger training sets. Models with very few hyperparameters will be easy to validate and tune, so you can probably reduce the size of your validation set, but if your model has many hyperparameters, you would want to have a large validation set as well(although you should also consider cross validation). Also, if you happen to have a model with no hyperparameters or ones that cannot be easily tuned, you probably don’t need a validation set too! Factors that determine the amount of training data required to train a machine learning model: 
  * The complexity of the problem. Does the relationship between the input features and the target variable follow a simple pattern or is it complex and nonlinear?
  * Precision requirements. If you only need a 60% success rate for your problem, less training data is needed than if you need to achieve a 95% success rate.
  * The dimensionality of the functional space. If only two input features are available, less training data will be needed than if there were 2000 features.

* A final deployement model is built based on both Train & Test but we report only Test set performance to finally show how a model is performing
* Can be done in 3 ways - https://www.coursera.org/learn/competitive-data-science/lecture/0jtAV/data-splitting-strategies
  * Random, Rowwise
  * Timewise - Rossmann store sales competition, Grupo Bimbo inventory demand competition
  * By ID -  Intel and MumbaiODT Cervical Cancer Screening competition kaggle, Nature Conservancy fisheries monitoring competition
  * Combined - Rental Prices Deloitte Kaggle eg


### Schemes
* Holdout scheme:
  * Split TRAIN data into two parts: partA and partB.
  * Fit the model on partA, predict for partB.
  * Use predictions for partB for estimating model quality. Find such hyper-parameters, that quality on partB is maximized.
  * If we have enough data, and we're likely to get similar scores and optimal model's parameters for different splits, we can go with Holdout
  
* K-Fold scheme:
  * Split train data into K folds.
  * Iterate though each fold: retrain the model on all folds except current fold, predict for the current fold.
  * Use the predictions to calculate quality on each fold. Find such hyper-parameters, that quality on each fold is maximized. You can also estimate mean and variance of the loss. This is very helpful in order to understand significance of improvement.
  * If on the contrary, scores and optimal parameters differ for different splits, we can choose KFold approach. 
  
* LOO (Leave-One-Out) scheme:
  * Iterate over samples: retrain the model on all samples except current sample, predict for the current sample. You will need to retrain the model N times (if N is the number of samples in the dataset).
  * In the end you will get LOO predictions for every sample in the trainset and can calculate loss.
  * if we too little data, we can apply leave-one-out.
  
### Stratified Sampling
* Small data
* Imbalanced data
* MultiClass classification

### Cause of diff scores and Optimal parameters
* Too little data
* Too diverse & inconsistent data
* we encounter situations which are more like the following case. Consider that now train consists not only of women, but mostly of women, and test, vice versa. Consists not only of men, but mostly of men. - The main strategy to deal with these kind of situations is simple. Again, remember to mimic the train test split. If the test consists mostly of Men, force the validation to have the same distribution. In that case, you ensure that your validation will be fair.




