## **Bank Marketing Effectiveness Prediction**

### **Abstract**

Finance industry is one of the leading industries globally and has the potential to bring a huge impact in the growth of the nation. Thus, it is important to analyze the data or information that the banking sector records about the clients. This data can be used to create connections and keep professional relationships with the customers in order to target them individually for any banking schemes.

Usually, the selected customers are contacted directly through: personal contact, telephone cellular, email or any other means of contact to advertise the new services or give an offer. This kind of marketing is called direct marketing and is one of the leading marketing techniques.

Thus, in this project we trained a model that can predict that whether the client will opt for a term deposit or not using given bank-client data, data related with the last contact of the current campaign and some other useful attributes

###**Problem Statement**

The given dataset is of a direct marketing campaign (Phone Calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe to a term deposit (Target variable y).
We were provided with the following dataset:

Bank Client data:

age (numeric):

job : type of job

marital : marital status

education:

default: has credit in default?

housing: has a housing loan?

loan: has personal loan?

Related to the last contact of the current campaign:

contact: contact communication type.

month: last contact month of year.

day_of_week: last contact day of the week.

duration: last contact duration, in seconds (numeric).

Other attributes:

campaign: number of contacts performed during this campaign.

pdays: number of days that passed by after the client was last contacted from a previous campaign.

previous: number of contacts performed before this campaign.

poutcome: outcome of the previous marketing campaign.

Output variable (desired target):

y - has the client subscribed to a term deposit? (binary: 'yes','no')

###**Introduction**

Marketing is the most common method which many companies are using to sell their products, services and reach out to potential customers to increase their sales. Telemarketing is one of the most useful ways of doing marketing for increasing business and building good relationships with customers to get business for a company. It’s also important to select and follow up with those customers who are most likely to subscribe to a product or service.

There are many classification models, such as Logistic Regression, Decision Trees, Random Forest, KNN, ANN and Support Vector Machines (SVM) that can be used for classification prediction.

**Classification Approach**

After understanding the problem statement, we loaded the dataset for the following operations:

Data Exploration

Exploratory Data Analysis

Feature Engineering

Feature selection

Balancing Target Feature

Building Model


###**Dataset Exploration**

The given dataset was initially loaded for a quick overview. It was observed that our dataset contains 45211 records and 17 features. Datatypes of features was then checked and it was found that there are 7 numerical (int) and 10 Categorical (object)
datatypes among which no null values and duplicated records were found in our dataset.

###**Exploratory Data Analysis**

After data wrangling, we did univariate and multivariate analysis on features to understand their pattern and how they relate with the target class.

**Univariate Analysis**

We initially plotted the numerical features using 


All 7 numerical data types graphs were right skewed and except for ‘age’ and ‘day’ all have outliers which should be removed.

**Bivariate Analysis**

Target Class Distribution

We first plotted target class distribution and found that it is highly imbalanced with a ratio of 88.3:11.6 i.e out of 100 clients only 12 of them opted for term deposit.



We then plotted each categorical feature with the target variable to get some insights.

Age of clients

In the above plot it is clear that a majority of customers called are in the age of 30s and 40s (33 to 48 years old fall within the 25th to 75th percentiles) and for each of the target variables the age feature is not linearly separable. Thus, age will be of less importance to us.

Job type- Customers with Blue-collar, management and technician showed maximum interest in subscription. We can also observe the large variance in our data among all categories.

Marital status

Education

In comparison to primary and some unknown education, people with secondary and tertiary education were more driven towards paying term deposits in the bank. 

Housing Loan

Majority of the people had previous housing loans and thus very few of them opted for term deposit.

Personal Loan

Majority of the people had personal loans and thus very few of them opted for term deposits.

Contact

Majority of the people were contacted through cellular medium and were converted to the subscription. Thus, cellular medium of contact is more effective in comparison to telephone and other mediums.

Day

We can predict that on first, tenth and near to the end of the month people took the term deposit. This may be due to the fact that various organizations have their schedules to release salaries and then people opted to pay a deposit.

Month

During the month of May there were maximum subscriptions with relatively good subscriptions in June, July and august. During other months we can see less subscriptions and so we can combine a few of them later on.

Campaign

People were mostly contacted once who subscribed to it, while others were contacted more number of times but the conversion rate reduced after 20 we did not see any significant conversions thus we drop those observations later on.

Previous

We can see above that the majority of people were not contacted previously before this campaign and there are no significant contacts after 11 times already done.

Balance- Balance of customers is more than 1 lacs and thus we need to remove outliers as the median is very less near to 450.

Pdays- pdays have large outliers and will have to look upon more closely.

Poutcome- Looking at poutcome we can infer that the success rate was high for some unknown category.

Duration

The above box plot shows that calls with long duration have more tendency for conversion.

###**Feature Engineering**

Feature engineering is one of the important steps in model building and thus we focused more into it. We performed the following in feature engineering

**Dealing with outliers**

After looking at the plots above we removed the outliers

In duration we removed those observations with no output and duration> 2000s

In campaign we removed campaigns> 20

In previous we removed observations for previous contacts> 11

Converting categorical variables into numeric- Here we converted all categorical features to numeric and then later converted them to categories so that the model doesn't assume them as weights.

Correlation Analysis

We can see that 'pdays' and 'previous' are highly correlated features, therefore, it will be good to remove any one of them to reduce multicollinearity.

**Feature Selection**

In feature selection we took the decision very wisely so that our model is trained well enough to predict the correct output. Thus, for selecting the right features we looked at the importance of decision trees.

Feature Importance after applying decision tree

We came to conclusion that only 'marital', 'age', 'day', 'campaign', 'balance', 'new_job_o', 'previous','poutcome', 'housing', 'pdays', 'month', 'contact' are showing significant importance to be considered for model building. But from these features we removed 'previous' as this feature is showing high collinearity with pdays.

Feature Standardization Standardization typically means rescaled data to have mean of 0 and standard deviations of 1. To bring all values from independent variables in the same scale. Using a standard scalar, the independent variables are transformed.

**Fitting Different model’s**

There	are	several	classification	models available for prediction/classification. In the project we used following models for classification Algorithms

KNN

Random Forest

Logistic Regression 

XGB Classifier

**K-Nearest neighbors (KNN)**

K-Nearest Neighbor is a non-parametric supervised learning algorithm both for classification and regression. The principle is to find the predefined number of training samples closest to the new point and predict the correct label from these training samples. It’s a simple and robust algorithm and effective in large training datasets.

Following are steps involved in KNN.

Select the K value.

Calculate the Euclidean distance between the new point and training point.

According to the similarity in training data points, distance and K value, the new data point gets assigned to the majority class.


**Random Forest**

Random forest is a Decision Tree based algorithm. It’s a supervised learning algorithm. This algorithm can solve both types of problems i.e. classification and regression. Decision Trees are flexible and they often get overfitted. To overcome this challenge, Random Forest helps to make classifications more efficiently. It creates a number of decision trees from a randomly selected subset of the training set and averages the-final outcome. Its accuracy is generally high. Random forest has the ability to handle a large number of input variables.




**Logistic Regression**

Logistic Regression is a Machine Learning classification algorithm that is used to predict the probability of a categorical dependent variable. In logistic regression, the dependent variable is a binary variable that contains data coded as 1 (yes, success, etc.) or 0 (no, failure, etc.).





**Model Evaluation**

For classification problems we have different metrics to measure and analyze the model’s performance. In highly imbalanced target feature accuracy metrics don't represent the true reality of the model.

**Confusion Matrix**

The confusion matrix is a tabular form of metrics which tell us the truth labels classified versus the model predicted labels. True Positive signifies how many positive classes a model is able to predict correctly. True Negatives signifies how many negative class samples the model predicted correctly.
 

**Precision/Recall**

Precision is the ratio of correct positive predictions to the overall number of positive
predictions: TP/TP+FP. It focuses on Type 1 error.
Recall is the ratio of correct positive predictions to the overall number of positive examples in the set: TP/FN+TP

**Accuracy**

Accuracy is one of the simplest metrics to use. It’s defined as the number of correct predictions divided by the total number of predictions and multiplied by 100.

**Area under ROC Curve (AUC)**
ROC curves use a combination of the true positive rate (the proportion of positive examples predicted correctly, defined exactly as recall) and false positive rate (the proportion of negative examples predicted incorrectly) to build up a summary picture of the classification.

###**Conclusion**

Thus, we come to an end of our analysis and model building to predict if the client will subscribe to a term deposit or not. The most important takeaways are:

This sums up the classification task of the bank marketing dataset. We find that Random Forest gives us the best value for accuracy which is 0.98 while KNNClassifier gives us the second-best accuracy value. The best AUC score of 0.97 comes from RandomForest, followed by the KNN classifier.

The results of Random Forest and KNN Classifier are better while the rest of the algorithms are giving more or less the same result with minor differences.

As per algorithms, the importance of whether the client uses a cellular phone or not and the month in which the client is being called play a vital role and the strategies of the marketing campaign should be decided accordingly.

