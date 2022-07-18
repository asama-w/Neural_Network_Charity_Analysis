# Charity_Analysis: Neural Network and Deep Learning Models
## Overview
### Purpose of the analysis
To help Alphabet Soup, the non-profit foundation that funds organizations around the world, determine whether their donated funds will be used effectively by analyzing the dataset of their funded applicants and predicting the success of the future applicants with the use of deep learning and neural networks models. The models are created using python's tensorflow library and will be optimized to yield better accuracy. 

### Resources:
- **Programming Language:** Python (Neural Network and Deep Learning Models)
- **Libraries:** TensorFlow
- **Software platform:** Google Colaboratory
- **Raw Dataset:** charity_data.csv

## Results

### Data Processing
**1. Target Variable:** What variable(s) are considered the target(s) for your model?
+ The target variable for this analysis is `IS_SUCCESSFUL` column which indicates wheter the organization is sucessful (1) or not successful (0).

**2. Features Variable:** What variable(s) are considered to be the features for your model?
+ The features variables are every column except `IS_SUCCESSFUL`, `EIN`, `NAME`, as shown in the following list:
  + `APPLICATION_TYPE	`
  + `AFFILIATION`
  + `CLASSIFICATION`
  + `USE_CASE`
  + `ORGANIZATION`
  + `STATUS`
  + `INCOME_AMT`	
  + `SPECIAL_CONSIDERATIONS`
  + `ASK_AMT`
+ Column `NAME` will be included only in the optimization of the model to see whether it has any influence on the accuracy.

**3. Neither Target nor Feature Variables:** What variable(s) are neither targets nor features, and should be removed from the input data?
+ The variables that are neither target nor feature are `EIN` and `NAME` and is removed from the input data as it contains significant distinct values and might skew the model.


