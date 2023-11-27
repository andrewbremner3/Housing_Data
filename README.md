# Housing_Data
Regression predictions from Kaggle competition [Link text](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) where training and test data sets are provided.
The data sets are 'un-cleaned' with empty rows and fields that need to be treated in various ways.

### 1) Clean the Data
Combined the Train and Test so that all treatments are done to the train and test.
Various Treatments:
* Drop rows that are outliers
* Drop rows that are nearly empty
* Fill empty fields that are numerical with 0 and objects with 'None'
  * test
* Use average of similar values to fill 'LotFrontage' fields
 
Housing Data set for regression tests
