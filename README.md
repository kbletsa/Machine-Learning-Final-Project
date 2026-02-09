# Data Overview

The analysis utilizes the train_hh_features.csv dataset, which contains records for 104,234 households . Each record represents a unique household identified by hhid .

The features are categorized into three main groups:

Demographics: Includes characteristics such as the gender of the head of the household (male), the total household size (hsize), and the number of children in various age groups . These variables provide insight into household structure and economic vulnerability .

Economic Indicators: The primary variable is consumption per person in purchasing power parity (utl_exp_ppp17), which serves as the core metric for poverty estimation and standard of living .

Consumption Habits: A significant portion of the dataset consists of binary variables indicating whether a household consumed specific food items . These act as proxies for economic status and quality of life .

# Algorithms

Preprocessing was consistent across all models, involving data cleaning, handling missing values, and encoding categorical features . Four distinct approaches were implemented:

1. Random Forest

Approach: An ensemble learning method using Bagging to create multiple decision trees .

Implementation: Hyperparameters such as the number of trees and maximum depth were tuned to reduce overfitting and improve generalization .

Key Advantage: It provides feature importance indicators and handles high-dimensional data well .

2. Gradient Boosting

Approach: An ensemble technique where decision trees are trained sequentially, with each new tree correcting the errors of the previous ones .

Implementation: Key parameters included learning rate, tree depth, and iterations . Cross-validation was performed per survey to test generalization across different data distributions .

Key Advantage: Efficient for structured data with complex, non-linear relationships .

3. Support Vector Regression (SVR)

Approach: Selected for its ability to model non-linear relationships and its robustness against outliers .

Implementation: Due to high computational costs, hyperparameter tuning was conducted on a random subset of the training data, while the final model was trained on the full set .

4. Deep Learning (MLP)

Approach: A Multi-Layer Perceptron (MLP) neural network where input data passes through hidden layers with non-linear activation functions .

Implementation: The network was trained using the AdamW optimizer and backpropagation . A fine-tuning stage was applied where the loss function was modified to account for poverty rates per survey .
