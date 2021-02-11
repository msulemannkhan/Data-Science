Machine learning problem: Goal of ML is to discover patterns and relationships in data
* what is being predicted, what data is needed. 
* What are some key actions to collect, analyze, predict, and react to the data or predictions? Remembering that different input features might require different kinds of actions. what data are ee analyzing, what data are we predicting? what data are we reacting to?
* What is the API for the problem during production/prediction? Who will use the service? How were they doing it today? 
* Best use case would be to start with a problem for which you are doing manual data analysis today - Think about, what are some of the benefits to replacing parts of that application with machine learning? What kinds of data would you collect if you wanted to do this? Are you collecting the data today? If not, why not?

Things to take care of: <br/>
* Avoid TRAINING SERVING SKEW - Data that is used in batch process should be same as the data stream - Use same code that was used to process historical data during training and reuse it during predictions.
* Performance metric during Training - Scaling to a lot of data
* Performance metric during Prediction - Speed of response
* Magic of ML comes with quantity and not complexity
* simplify user input in APIs
* In GCP, You can process unstructured data through an ML API and take the reults of the ML API as thr input to your chose model

ML Effort Allocation
* Defining KPIs
* Collecting Data - More time
* Building infrastructure - More time
* Optimizing ML Algo - Not as much time as assumed
* Integration 

Path to ML:
* Individual Contributor
* Delegation - Adding more people
* Digitization - Automation
* Big Data and Analytics - operational or user 
* ML - predictions, etc
 <br/>

MLOps:
* Test & validate data, data schemas, code,components and modesl
* Consider the whole systeme and ML training pipeline
* Deploy code, constantly monitor, retrain, serve the model
* Continuous integration, continuous deployment and continuous training


