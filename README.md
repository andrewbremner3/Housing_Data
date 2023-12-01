# Housing_Data
Regression predictions from Kaggle competition [www.kaggle.com](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) where training and test data sets are provided.
The data sets are 'un-cleaned' with empty rows and fields that need to be treated in various ways.

### 1) Clean the Data
Combined the Train and Test so that all treatments are done uniformly (necessary for using dummy variables in the following steps).

Image below shows the "percent missing" of the initial data set.

<img src="./Images/PercentMissingData.png" width="800"/>

Cleaning Treatments:
* Drop rows that are outliers
* Drop rows that are nearly empty
* Fill empty fields
  * Numerical fields filled with 0
  * Object fields usually filled with 'None'
  * Average of similar values (same Neighborhood) to fill 'LotFrontage' fields
 
### 2) Use training data test protcol
The hypothesis is that the numerical fields could be good enough for a strong model. The other option is to use 'dummy' variables for the catagories or object fields.

* Numerical Data only
  * Time to run: 10.81s
  * Percent error of: 2.28%
* All Data (dummy and numerical)
  * Time to run: 96.33s
  * Percent error of: 1.28%
The extra data makes the fit take ~10x as long but has a measurably better error value.

Try a Random Forest Regression model as well.
* All Data (dummy and numerical)
  * Time to run: 0.33s
  * Percent error of: 1.32%
This model is substantially faster and has a comparable error on test set.

### 3) Final train and test
The dummy variables made the RMSE better so that is what is used for the final Elastic Net setup.
Use the entire training set to train the scaling as well as the Elastic Net model where the best parameters from the previous training were used. (Alpha = 200, l1_ratio = 1, max_iter = 10000).
The results on Kaggle show there is probably over fitting as the score is quite bad at 6.7271

A Random Forest Regression is then tried and shows substantially better results.
The score is 0.1547 which is much better thanthe Elastic Net model.

 
