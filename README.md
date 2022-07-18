# Charity Analysis: Neural Network and Deep Learning Models
## Overview
### Purpose of the analysis
To help Alphabet Soup, the non-profit foundation that funds organizations around the world, determine whether their donated funds will be used effectively by analyzing the dataset of their funded applicants and predicting the success of the future applicants with the use of deep learning and neural networks models. The models are created using python's tensorflow library and will be optimized to yield better accuracy. 

### Resources:
- **Programming Language:** Python (Neural Network and Deep Learning Models)
- **Libraries:** TensorFlow
- **Software platform:** Google Colaboratory
- **Raw Dataset:** charity_data.csv

## Results
### Script:
+ Original model (Deliverable 1 and 2): [AlphabetSoupCharity.ipynb](https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity.ipynb)
+ Optimized model for higher accuracy (Deliverable 3): [AlphabetSoupCharity_Optimzation.ipynb](https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_Optimzation.ipynb)
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

**3. Neither Target nor Feature Variables:** What variable(s) are neither targets nor features, and should be removed from the input data?
+ The variables that are neither target nor feature are `EIN` and `NAME` and is removed from the input data as it contains significant distinct values and might skew the model.
+ Column `NAME` will be included later in the optimization part of the model to see whether it has any influence on the performance accuracy.

### Compiling, Training, and Evaluating the Model
**1. First Neural Network Model:**

The first version of the model (in `AlphabetSoupCharity.ipynb`) contains 2 hidden layers. As there are 43 input variables, 80 neurons is selected as the initial number for the 1st hidden layer, 30 neurons is selected for the 2nd hidden layer so that it is not too overfitting but still provides plenty number of weighted parameters. The activation functions include `ReLU` for hidden layers and `sigmoid` for the output layer.

<img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_design_1.png width="80%" height="80%">
<img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_1.png width="60%" height="60%">

**2. First Model Performance:** 

**The model accuracy is 72.5%**, which does not reach the target performance of 75%.
<br /><img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_accuracy_1.png width="80%" height="80%">

**3. Model Optimizations:** 
+ Inspect the unique values of each column.
<br /><img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/df_unique_values_1.png width="30%" height="30%">

+ **1st Optimization:** 
  + Script: [Additional_AlphabetSoupCharity_Optimzation.ipynb](https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_AlphabetSoupCharity_Optimzation.ipynb)
  + The only change in the model is the input data (binned `ASK_AMT`)
  + Bucket `ASK_AMT` column which has the unique value of 8747, those whose count is less than 3 are put as "Other".
  
  <br /><img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/ask_amt_bin.png width="40%" height="40%">
  + However, this optimization does not affect the performance, the accuracy is similarly at 72.6%
  
  <br /><img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/ask_amt_accuracy.png width="80%" height="80%">
  
+ **2nd Optimization:** 
  + Script (Deliverable 3): [AlphabetSoupCharity_Optimzation.ipynb](https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_Optimzation.ipynb)
  + Include the `NAME` column as one of the feature variables to see its effect and bucket them by its count, those with less than 10 counts will be binned as "Other".
  
  <br /><img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/name_bin.png width="40%" height="40%">
  
  + Add 3rd hidden layer with 10 neurons and Relu activations function.
  + Reduce number of neurons in the 1st layer to 70 neurons.
  + The model is shown in the following image
  
  <br /><img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_design_2.png width="80%" height="80%">
  
  <img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_optimized_2.png width="60%" height="60%">
  
  + **The accuracy increase to 78.1%**, which surpasses the targeted performance.

  <br /><img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_accuracy_2.png width="80%" height="80%">
  
## Summary
From the optimizations in this analysis, the performance of the model is able to increase pass 75% if only the `NAME` columns is included in the feature variables. This implies that the name of the organization might have some influences on the success of the organization, whether the reason lies in its reputation, or the frequncy of applications. However, since the increase in performance of the optimized model with included NAME column is approximately 5.6%, slightly higher than the initial model when the NAME column is not considered, and the variability in names is considerably large, including the name as one of the features may not be a good solution for this analysis model as it might effect how the model weights the parameters and overlook other factors.

Another machine learning model which could be used to predict the success of the organization is the **Random Forest Classifier**, as it uses decision trees and combine their output to make a final classification decision, in other words, the model structure is quite similar to the deep learning model. Also, this dataset does not contain images or requires any heavy modifications, using random forest classifier model for this analysis can be a simpler and faster-processing way of predicting the success of the Alphabet Soup's funded organizations.
