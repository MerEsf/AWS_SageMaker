# Projects in AWS SageMaker

## Kaggle Bike Sharing Demand Prediction:

#### Goal: 
Predict the total count of bikes rented during each hour covered by the test set, using only information available prior to the rental period

#### Dataset: 
The training set is comprised of the first 19 days of each month, while the test set is the 20th to the end of the month

### 1) PCA and XG_boost:

- Ensure Training, Test and Validation data are in S3 Bucket
- Select Algorithm Container Registry Path - Path varies by region
- Configure Estimator for training - Specify Algorithm container, instance count, instance type, model output location
- Specify algorithm specific hyper parameters
- Train model
- Deploy model 
- Specify instance count, instance type and endpoint name
- Run Predictions

### 2) Amazon DeepAR:

#### a) Without dynamic features:

None of these features are used: ['season', 'holiday', 'workingday', 'weather', 'temp', 'atemp', 'humidity', 'windspeed']
Start Time From: ['datetime']
Target Feature: ['count','registered','casual']
Frequency: 'Hourly'

#### b) With dynamic features:

Dynamic features used: ['season', 'holiday', 'workingday', 'weather', 'temp', 'atemp', 'humidity', 'windspeed']
Start Time From: ['datetime']
Target Feature: ['count','registered','casual']
Frequency: 'Hourly'

### 3) Multi-layer Perceptron Regressor; Neural Network (NN):

Input Features: ['season', 'holiday', 'workingday', 'weather', 'temp', 'atemp', 'humidity', 'windspeed', 'year', 'month', 'day', 'dayofweek','hour']
Target Feature: [log1p('count')]

- Train a bike rental prediction model
- NN requires one hot encoding of categorical data
- NN also requires features to be on similar scale
- Perform one-hot encoding of all categorical features: ['season', 'holiday', 'workingday', 'weather', 'year', 'month', 'day', 'dayofweek', 'hour']
- Verify model performance


## Customer Churn Prediction with Neural Network (binary classification):

#### Goal: 
Automated identification of unhappy customers, also known as customer churn prediction
Construct an ML model of one mobile operator’s churn. After training the model, we can pass the profile information of an arbitrary customer (the same profile information that we used to train the model) to the model, and have the model predict whether this customer is going to churn

#### Dataset: 
The dataset we use is publicly available and was mentioned in the book Discovering Knowledge in Data by Daniel T. Larose

## Movie Recommender (Recommender system/ Factorization Machine):

#### Goal: Classification with SageMaker
Predict how a user would rate a particular movie

#### Dataset: 
http://files.grouplens.org/datasets/movielens/ml-latest-small.zip

Input Features: [userId, moveId]
Target Feature: rating

- Ensure Training, Test and Validation data are in S3 Bucket
- Select Algorithm Container Registry Path - Path varies by region
- Configure Estimator for training - Specify Algorithm container, instance count, instance type, model output location
- Specify algorithm specific hyper parameters
- Train model
- Deploy model - Specify instance count, instance type and endpoint name
- Run Predictions

## Assess sentiment of customer review (Sentiment analysis using Amazon Comprehend NLP Service):

#### Goal: 
Use Comprehend Service to detect sentiment

#### Dataset: Amazon Public Dataset
https://s3.console.aws.amazon.com/s3/buckets/amazon-reviews-pds/?region=us-east-1

Input: Customer Review headline and body
Output: Overall sentiment and scores for Positive, Negative, Neutral, Mixed
