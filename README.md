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
  * Time to run: 5.22s
  * Percent error of: 14.94%
* All Data (dummy and numerical)
  * Time to run: 50.11s
  * Percent error of: 11.65%

The extra data makes the fit take ~10x as long but has a measurably better error value.

### 3) Final train and test
The dummy variables made the RMSE better so that is what is used for the final setup.

Use the entire training set to train the scaling as well as the grid search Elastic Net model.

 
