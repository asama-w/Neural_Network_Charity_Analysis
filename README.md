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
+ Column `NAME` will be included only in the optimization of the model to see whether it has any influence on the accuracy.

**3. Neither Target nor Feature Variables:** What variable(s) are neither targets nor features, and should be removed from the input data?
+ The variables that are neither target nor feature are `EIN` and `NAME` and is removed from the input data as it contains significant distinct values and might skew the model.

### Compiling, Training, and Evaluating the Model
**1. First Neural Network Model:** How many neurons, layers, and activation functions did you select for your neural network model, and why?
The first version of the model (in `AlphabetSoupCharity.ipynb`) contains 2 layers, with 80 neurons in the first layer and 30 neurons in the second layer. The activation functions include `ReLU` for hidden layers and `sigmoid` for the output layer.

<img src= to-be-put-link width="50%" height="50%">
<img src= to-be-put-link width="50%" height="50%">

**2. First Model Performance:** Were you able to achieve the target model performance?
The model accuracy is 72.5% which is below the target performance of 75%.
<img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_accuracy_1.png width="50%" height="50%">

**3. Model Optimizations:** What steps did you take to try and increase model performance?
+ 1st Attempt: bucket `ASK_AMT` column, however, the accuracy still stays around 72%.
+ 2nd Attempt: 
  + Include the name column back to the dataset to see its effect and bucket them with those with the count less than 10 will be binned as "Others".
  + Add 3rd hidden layer with 10 neurons and Relu activations function.
  + Reduce neurons in the 1st layer to 70 neurons.
  + The model is shown in the following image
  
  <img src= to-be-put-link width="50%" height="50%">
  <img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_optimized_2.png width="50%" height="50%">
  
  + The accuracy increase to 78.1%, which surpass the targeted performance.

  <img src= https://github.com/asama-w/Neural_Network_Charity_Analysis/blob/main/Additional_images/model_accuracy_2.png width="50%" height="50%">
