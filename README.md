# Module17

This is a short summary of the work involved in this project. There are 5 parts to the Jupyter Notebook.
•	Business understanding
•	Data understanding
•	Data preparation
•	Modeling
•	Conclusion
There are a total of 5 files in this repository (1 readme.md; 1 jupyter notebook – Practical Application #3.ipynb in the Notebook folder and 3 images in the images folder)
The notebook can be found at: 
https://github.com/sinclaireric77/Module17/tree/main/Notebook/Practical Application #3.ipynb

1st part – Business understanding
Are there qualitative or quantitative parameters that affect a person contacted by a marketing campaign to open an account with the bank?
We will look at the database a Portuguese bank with multiple marketing campaigns and try to find relationships between the customer opening a bank account and various other features. We will also look at patterns in the data to try to create a model that can predict opening the account based on those features.
2nd part – Data understanding
The second part consists of understanding how the data is structured so we can work on target features and clean the data that is necessary for our analysis. Here, success will be our target (‘y’) and the rest of the features will be data we will apply different models on.
3rd part – Data Preparation
-	Converted 4 columns yes/no to 1/0 and then to numeric (default, housing, loan, y)
-	Unknowns appear in 3 columns.
o	Default seems to have only 3 “y” values and 8597 unknowns.
o	This column is useless really, so I removed it completely.
-	As for the other 2, there were 990 unknowns on close to 40k records, so I removed those rows.
4th part – Modeling 
In this section, I took 2 different approaches with 4 models each (Logistic Regression, Decision Tree, KNN and Support Vector Machine):
-	1st Approach: Simple models with the most colinear features that are numeric only.
-	2nd Approach: I added all the categorical features and did a grid search on all 4 classifiers.
All the above were ran with a standard scaler function in a pipeline.
1st Approach – Results
The features that had the most positive or negative correlation with our target feature were duration, pdays, emp.var.rate, euribor3m and nr.employed. So I used those to create the 4 models. Here are the results:

![image](https://github.com/sinclaireric77/Module17/assets/160784197/ad3423f3-1f6d-43ed-853e-fd2126053dc4)


The best model ended up being the Support Vector Machine with a 91.06% accuracy. Note also that it was the slowest and used a lot of processing.

2nd Approach – Results
After I added all the categorical features, I ran a Grid Search on all 4 models once again and here are the results:

![image](https://github.com/sinclaireric77/Module17/assets/160784197/539dd6cf-96aa-44bc-b4fb-a9c5292affdd)

 
Once again SVM seems to have the highest accuracy, but to what extent? The processing time is through the roof, and we get only a marginal increase in accuracy.
I also looked at other performance metrics (recall & precision) with a confusion matrix and probabilities of 0.3 and 0.7 but the improvements were minimal, so we kept accuracy as our measure of model performance.
5th part – Conclusion
So, our best model in this exercise is the support vector machine model with a 91.15% accuracy and a Kernel RBF. However, it comes at great cost as it is the slowest model. It is 75 times slower than the decision tree that got us very close with 90.93% accuracy.

