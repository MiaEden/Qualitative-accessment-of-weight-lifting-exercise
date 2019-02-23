
### Executive Summary
People regularly quantify how much of a particular physical activity they do, Using devices such as Jawbone Up, Nike FuelBand, and Fitbit. But rarely quantify how well they do it. 
In this project, we will use data from accelerometers on the belt, forearm, arm, and dumbell of 6 participants whom were asked to perform barbell lifts correctly and incorrectly in 5 different ways. Our goal is to predict the manner in which they did the exercise. This is the *classe* variable in the training set: 

*   A performed correctly according to specification   
*   B incorrectly throwing elbow to front  
*   C incorrectly lifting the dumbbell only halfway  
*   D incorrectly lowering the dumbbell only halfway   
*   E incorrectly throwing the hips to the front  

For more information about dataset please visit [HAR website](http://groupware.les.inf.puc-rio.br/har) - section on the Weight Lifting Exercise Dataset.  

*   [Training data](https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv)   
*   [Test data](https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv)  

### Data processing

**Read HAR data** for train and test data from working directory, folder "data".  
Check **dimension** of datasets.
Verify if there are **missing values** in the dataset columns and **percentage** to total, since the prediction algorithm will fail to work properly with missing values. Find the columns that have more than **95%** missing values, as applicable.
Remove those **100 columns that have over 95% NA** (missing values).
Remove **zero covariates** (predictors that do not contribute much in prediction, for having very little variability in them).  
Verify if **any other variable** should also be removed.  
Choose to only keep predictors related to the **basic original measurement of movement** on belt, glove, arm-band or dumbell. Will not include in the model variables related to unique identifiers, time series, or calculations such as total.

### Building the model

Take a look at **"classe"** levels (this variable predicts the manner in which exercise was performed) to confirm values.  
**Split** the train data into 70% training and 30% validation test on column class for building/ validating the model.
Since this is a **classification** prediction type and there is a **large number of variables** as predictors, we chose the **random forest** method for modeling. Random Forest grows many trees (or a forest), through bootstrap sampling (sampling with replacement). At each node, a subset of predictors m, is selected at random out of M total predictors. The best split on these m is used to split the node. And m is held constant as the forest grows. Also random forest handles well outliers and correlated variables.  
**Cross-validation** was performed inside the model so a separate test set to obtain the unbiased estimate of the test set error is not really necessary. And the **error rate** is expected to be low, due to model selected.

### Visualizing the model

Notice on charts:   

*   The highest accuracy was obtained with only 2 randomly selected predictors  
*   50 trees would be sufficient for this study  
*   Top 2 most important variables are: roll-belt and yaw-belt  

### Validating the model

Evaluate the fitted model, using it to predict classe in validation data set. Compute the confusion matrix and associated statistics to asses the preformance of the model fit.  
The **Accuracy** of our model seems very good, at **99.3%**.  Predictions look reliable.  
We now plot top 2 variables for a simple visualization of prediction.  

### Applying final model to test dataset

### Conclusions

Considering the high accuracy obtained from our model, it appears very reasonable to predict the manner in which people exercise. Sensitivity of classe A prediction is 100%. Using wearable devices or sensors to collect data and providing real-time feedback to users on how well they are performing the exercise would highly enhance work-out technique. 
