# Thyroid_disease_classification

Dataset-
The dataset consists of 30 columns - 29 features and the last column has both labels and patient id. Patient id is not required for classification. Label column is separated and stored as ‘target’ in the dataframe. There are 7 continuous features, rest are categorical.

https://archive.ics.uci.edu/ml/datasets/Thyroid+Disease

### Exploratory data analysis-

Dealing with missing values-

In this dataset, the missing values are not just represented by Nan but by ‘?’. Thus, cannot be detected by df.isnull().sum(). Remove ‘?’ and replace it with median 
In TBG most of the values were null, hence replaced by zero

Converting categorical variables into numerical variables- used simple mapping

Label encoder can be used. One hot encoding is not necessary as most are binary categorical variables.

In the age column, some values were too large. Removed the respective rows.

Remove duplicate rows

Target has 32 classes. In all 9168 samples are there. 6767 belong to ‘-’ which implies no disease.

Applied chi square test to find the effect of gender on target variable.

p- value =0.83 which is greater than 0.05. Thus, Retain H0 -There is no relationship between 2 categorical variables.

Most of the data pertains to ages 40-80. From this step , the outliers in the age column were found

Correlation heatmap amongst the variables. ( nothing inferred from here. TT4 is highly correlated with other variables but no action taken)

Filter based feature selection: 

Removing constant features and quasi constant features using VarianceThreshold. Constant features are the type of features that contain only one value for all the outputs in the dataset (threshold =0) 
Correlation of each variable with the target variable is found. There should be higher dependency of the target on each feature. Six variables with highest correlation with the target variable are chosen and given to the classifier.

### Classification-
#### Without filter based feature selection

Logistic regression, SVM, KNN, Random forest were used for testing.
Random forest gave the highest accuracy with 93.93 percent. Randomized   search cv and cross validation was used and best parameters for the random forest were chosen which increased accuracy to 94.24 percent.

#### After feature selection (x-fil dataframe)
accuracy improved in Logistic regression, KNN, SVM and RF significantly. XGBoost performs best with 99.89 % accuracy.

#### Correlation based feature selection
Choosing only variables with correlation > 0.1 with target variable - x_co dataframe. 
Highest accuracy was obtained using random forest classification -92.9 %
Accuracy is almost as same as while using all the features.
This reduces time and computations needed and gives good results.
Ensemble learning models are performing well - Boosting work better.













