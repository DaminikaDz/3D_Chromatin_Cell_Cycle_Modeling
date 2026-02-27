# 3D Chromatin Structure Modeling for Cell Cycle Classification and Regression

# Overview

This project focuses on modeling the three-dimensional chromatin structure in the context of cell cycle progression. The main objectives were to classify cells into cell cycle phases (G1, S, G2M) and reconstruct their 3D chromatin organization based on contact data. Understanding the relationship between chromatin structure and cell cycle progression may provide insights into genome organization and cellular processes.

# Data

The project used single-cell chromatin contact data:
- contact_data_2000.zip — intra- and inter-chromosomal contacts
- train_data_2000.zip — labeled training data
- test_data_2000.zip — unlabeled validation data

# Feature Engineering

Features describing chromatin organization and cell relationships were extracted using Python (Pandas). Selected features included:
-mean, median, and standard deviation of region size within a cell
-mean, median, and standard deviation of distances between contacting regions
-number of intra- and inter-chromosomal contacts
-CDD (CIRCLET metric)

These features were merged with training labels for each cell. 

# Cell Cycle Phase Classification

Multiclass classification (G1, S, G2M) was performed using:
- Random Forest
- XGBoost
- Support Vector Machine (SVM)

Highly correlated features (>0.9) were removed to reduce redundancy. Class imbalance (G1, S) was addressed using SMOTE oversampling. Hyperparameters were optimized with Grid Search.

Evaluation metrics:
- Accuracy
- Precision, Recall, F1-score
- Confusion matrix
- Cross-validation

The best performance was achieved by the SVM classifier, with ~62% accuracy on training data and ~47% on test data, and good performance for the dominant G2M class. 

# Regression of Cell Cycle Progression

Two regression tasks were performed:

order_within_phase prediction

Tested models:
- MLPRegressor
- Linear Regression
- Decision Tree
- Random Forest
- XGBoost
- KNN

Best model: MLPRegressor

Results:
MAE: 17.49
RMSE: 3.41
R²: 0.059

order prediction

Best model: Random Forest Regressor

Results:
MAE: 9.27
RMSE: 11.41
R²: 0.174

These models were used to fill missing progression values in test cells. 


# 3D Chromatin Modeling and Visualization

The final stage involved reconstructing and visualizing chromatin 3D structure using the ChromMovie model. Three types of visualizations were generated:
- single chromosome
- single cell
- multiple cells

Examples of reconstructed chromatin structures are shown in the figures. [Project Raport (PDF)](Raport.pdf)

Authors:
Daminika Dzeranhouskaya
Szymon Kiełtyka
Jakub Miszczak
Karolina Kawulska
