# ML_Project4-KNN-Regression-
Simple Linear Regression Analysis &amp; The Importance of Adjusted R²
This project demonstrates a complete Simple Linear Regression workflow on a synthetic dataset. It goes beyond just fitting a model; it delves into model evaluation and, most importantly, investigates a common pitfall in machine learning: the misleading nature of the R² score when adding irrelevant features. The project empirically validates why Adjusted R² is a crucial metric for model selection.

Project Overview
The goal was to build a linear regression model to predict a target variable (y) from a single feature (x). The analysis then expands to test what happens when new, unnecessary columns are added to the data, demonstrating a key concept in model interpretation.

Key Findings:

A strong initial model was built with an R² of 0.78.

Adding a completely random feature increased R² to 0.79, proving R² can be artificially inflated.

Adding a somewhat relevant feature increased R² to 0.80.

In both cases, the Adjusted R² correctly indicated a less optimal model by increasing only slightly (0.78) or not matching the rise in R² (0.79 vs. 0.80), confirming its utility.

Methodology
1. Initial Modeling & Evaluation
Data Exploration: The relationship between the two variables was visualized using a scatter plot, confirming a linear trend suitable for linear regression.

Data Preparation: The data was split into features (X) and the target (y), then divided into training and testing sets (80%/20%) with a fixed random_state=2 for reproducible results.

Model Training: A LinearRegression model from scikit-learn was trained on the training data.

Visualization: The line of best fit was plotted over the training data, providing a clear visual confirmation of the model.

Model Parameters: The slope (m or coef_) and y-intercept (b or intercept_) of the regression line were extracted.

Comprehensive Evaluation: The model was evaluated using a suite of metrics:

Mean Absolute Error (MAE): The average absolute difference between predictions and actual values.

Mean Squared Error (MSE): The average of squared differences (punishes larger errors more).

Root Mean Squared Error (RMSE): The square root of MSE, in the same units as the target variable.

R² Score: 0.78 - Represents the proportion of variance in the target explained by the feature.

Adjusted R² Score: 0.77 - Adjusts the R² score for the number of features in the model.

2. The Experiment: Testing R² vs. Adjusted R²
To demonstrate a critical weakness of R², two experiments were conducted:

Adding an Irrelevant Feature: A new column filled with purely random numbers was added to the dataset. This feature had no real relationship with the target variable.

Result: The R² score increased to 0.79, which is misleading. The Adjusted R² increased only to 0.78, providing a more honest assessment.

Adding a Semi-Relevant Feature: A new column was created by adding random noise to the original feature, making it somewhat related to the target but redundant.

Result: The R² score increased again to 0.80. The Adjusted R² also increased to 0.79 but failed to keep pace with the rise in R², signaling that the new feature's contribution might not be worthwhile.

Results and Conclusion
Model Version	Features	R² Score	Adjusted R² Score	Conclusion
Original Model	1 Relevant	0.78	0.77	Strong baseline model.
Experiment 1	1 Relevant + 1 Random	0.79	0.78	R² misleadingly increases. Adj-R² shows minimal gain.
Experiment 2	1 Relevant + 1 Noisy	0.80	0.79	R² increases. Adj-R² increases less, indicating diminishing returns.
Conclusion:
This project successfully illustrates why R² alone is an insufficient metric for evaluating model quality, especially when comparing models with different numbers of features. R² always increases or stays the same when new features are added, even if they are useless, which can lead to selecting overly complex models (overfitting).

Adjusted R² solves this problem by penalizing the score for adding irrelevant features. It is a more reliable metric for comparing models and guiding feature selection, as it only increases if the new feature improves the model more than would be expected by chance.

Technologies Used
Python

Libraries:

numpy - For numerical operations and array handling.

pandas - For data manipulation and analysis.

matplotlib & seaborn - For data visualization (scatter plots, regression lines).

scikit-learn - For machine learning (train_test_split, LinearRegression, metrics).
