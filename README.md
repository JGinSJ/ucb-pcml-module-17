# Comparing Classifiers: Bank Marketing Dataset 🏦

Jupyter Notebook found here: [Insert link to your prompt_III.ipynb file here]

## Project Overview
This is my submission for Practical Application III (Module 17) in the UC Berkeley ML/AI Professional Certificate program. 

The goal of the project was to compare the performance of four different machine learning classifiers: 1. K-Nearest Neighbors (KNN)
2. Logistic Regression
3. Decision Trees
4. Support Vector Machines (SVM)
The project a provided a dataset from a Portuguese banking institution that contained data from 17 different telemarketing campaigns. 

The project's main business objective was figuring out which clients are actually likely to subscribe to a term deposit. By predict this the bank's call center can focus resources on good leads instead of annoying people who are most likely just going to say "no."

## Summary of Findings
* Almost 89% of the clients in this dataset did not subscribe. Because of this, using standard "Accuracy" to compare the models was a bad idea since a model could just guess "no" every time and look like it was 89% accurate. I switched the scoring metric to ROC-AUC to get a clearer picture of whether the models were actually learning.
* After tuning the hyperparameters using 5-fold Cross-Validation (GridSearchCV), Logistic Regression and Decision Trees performed the best on the test data, both scoring a ROC-AUC score of roughly 0.65.
* I had to skip running a full grid search on the Support Vector Machine (SVM). Running cross-validation on an SVM with even a small number of training rows was too computationally expensive for my laptop to handle in a reasonable amount of time, or catching fire.
* By extracting the coefficients from the Logistic Regression model I found that Students and Retirees are the targets most likely to say 'yes' to a new term deposit (highly likely to convert). The marketing team should focus the next campaign on them.
* People working in Blue-Collar, Services, and anyone with an "Unknown" credit default status, are most likely to say 'no' to a new term deposit (highly unlikely to convert). The bank should actively deprioritize calling these groups.

## Next Steps and Recommendations
If I were to take this project further for the bank's marketing team, my next steps would be:
1. For this specific baseline project, we only used the client's basic demographic info. I think the model's ROC-AUC score would jump significantly if we included the macroeconomic indicators that are available in the wider dataset.
2. I would like to try using techniques like Synthetic Minority Over-sampling Technique (SMOTE) or class-weighting to help the models learn the "yes" clients a bit better.
3. Since my laptop couldn't handle the full dataset for SVM tuning, I recommend running the grid search on the provided 10% sample file to see if a tuned SVM can actually beat the Logistic Regression model.