# Credit Line Increase Model Card
### Basic Information
* **Person or organization developing model**: 
* Prithak Kumar Bhattacharyya, `pkbhatta_5@gwmail.gwu.edu`
* Ziyad Maknojia, 'zam@gwmail.gwu.edu'
* Jenny Choi, 'jihyechoi@gwmail.gwu.edu'
* Kaixu Yu, 'kyutony98@gwmail.gwu.edu'
* **Model date**: August, 2021
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [DNSC_6301_Example_Project.ipynb](https://nbviewer.jupyter.org/github/jphall663/GWU_DNSC_6301_project/blob/main/DNSC_6301_Example_Project.ipynb)
* **Model implementation code**: [DNSC_6301_Example_Project.ipynb](DNSC_6301_Example_Project.ipynb)

### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Students in GWU DNSC 6301 bootcamp.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

### Training Data
* Data dictionary: 
| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |
* **Source of training data**: GWU Blackboard, email `pkbhatta_5@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500
  * Columns: 20
 
### Test Data
* **Source of test data**: GWU Blackboard, email `pkbhatta_5@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

### Model Details
* **Columns used as inputs in the final model**: 'LIMIT_BAL', 'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1', 'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6', 'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Column(s) used as target(s) in the final model**: 'DELINQ_NEXT'
* **Type of model**: 'Decision Tree' with an accuracy of ~75%
* **Software used to implement the model**: Python
* **Version of the modeling software**: 3.7.11
* **Hyperparameters or other settings of the model**: ccp_alpha=0.0, class_weight=None, criterion='gini', max_depth=6, max_features=None, max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None,min_samples_leaf=1, min_samples_split=2, min_weight_fraction_leaf=0.0, presort='deprecated', random_state=12345, splitter='best'

### Ethical considerations:
* **Math issues**:
* Some of the inputs or outputs might be hard to understand based on mathematical considerations, if not understanding the meaning of the variables first

* **Software Problems**:
* The version of Google Colab might have an impact on the outputs and the graphs might have few discrepancies

* **Real World Risks**:
* If this model is used to make business decisions, it might not be accurate due to the variable importance measure and can severly impact the outcome
* The model consists of bias based on Gender and Race which can be considered as a severe discriminating factor, though efforts were made to overcome them


* **Unexpected things happening on the model or results**:
* The output of the variable "race" is correlated to the predictions, which is a model bias and has an impact on the output i.e. accuracy 

### Quantitative analysis:
* **Metrics used to evaluate the final model**:
* Confusion metrics
* AUC graphs

* **The final values of the metrics for all data**:
* Training data: 78.37%
* Validation data: 74.96%
* Test data: 74.38%

* **Plots in the model**:
*	Histograms
*	Correlation heatmap
*	Line plots showing 
*	Bar chart

* **Comparison between different models**:
* For the model comparison, we implemented the Support Vector Machines(SVM) and found that it learnt more about the 0's in the target varibale than the 1's as the data consists of more 0's
* The accuracy for predicting the 0's was approximately 77% and that for the 1's was 50% 
* The decision tree out-performed the Support Vector Machines
