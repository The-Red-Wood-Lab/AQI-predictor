# AQI Predictor Model

This project aims to predict the Air Quality Index (AQI) using a combination of data analysis, advanced imputation techniques, and machine learning algorithms. The steps and methodologies employed in this project are outlined below.

## 1. Dataset Analysis and Outlier Detection

### 1.1 Dataset Analysis
We initiated the project by thoroughly analyzing the dataset. The objective was to understand the underlying structure, distribution, and key characteristics of the data. This involved examining the various features, identifying any correlations, and detecting potential issues that might hinder model performance.

### 1.2 Outlier Detection
Outliers, which are data points that deviate significantly from other observations, were identified using **box plots**. Box plots provide a visual representation of the data's distribution and highlight extreme values that could skew the results. Addressing outliers is crucial to ensure the robustness of the machine learning models.

## 2. Handling Missing Data with MICE Technique

### 2.1 Introduction to MICE
To address missing data, we employed the **Multiple Imputation by Chained Equations (MICE)** technique. MICE is an advanced statistical method that fills in missing values by generating multiple imputations, which are then used to create a complete dataset. This approach accounts for the uncertainty associated with missing data and helps in producing more reliable models.

### 2.2 Iterative Imputation with Different Regression Techniques
Three regression techniques were used as iterative imputers within the MICE framework:

- **Ridge Regression:** This method adds a regularization penalty to the magnitude of the coefficients, helping to prevent overfitting and improve model generalization.
- **Bayesian Regression:** Bayesian Regression applies Bayes' theorem to update the probability distribution of the model parameters based on observed data, allowing for a more flexible modeling approach.
- **Elastic-Net Regression:** A hybrid of Ridge and Lasso regression, Elastic-Net applies penalties to both the magnitude and the absolute value of the coefficients, making it effective for datasets with correlated predictors.

### 2.3 Data Splitting and Imputation Process
- The original dataset was split into **90% training data** and **10% test data**.
- The MICE technique was applied to the 90% training data separately using Ridge, Bayesian, and Elastic-Net regression techniques as iterative imputers.
- Each 90% training dataset was further split into **80:20 ratio** for training and testing, respectively, resulting in six different datasets:
  - **Three training datasets** (one for each regression technique).
  - **Three testing datasets** (corresponding to each of the training datasets).
- These datasets were saved as CSV files for further analysis.

## 3. Model Prediction and Evaluation

### 3.1 Machine Learning Algorithms Used
To predict AQI, we implemented three machine learning algorithms:

- **Decision Tree:** A simple yet powerful model that splits the data into subsets based on feature values, forming a tree-like structure.
- **Random Forest:** An ensemble learning technique that constructs multiple decision trees and aggregates their predictions, enhancing accuracy and reducing the risk of overfitting.
- **Gradient Boosting:** An iterative ensemble method where models are built sequentially, each new model correcting errors made by the previous ones, leading to highly accurate predictions.

### 3.2 Model Training and Testing
- Each algorithm was trained and tested on the datasets imputed with Ridge, Bayesian, and Elastic-Net regression techniques.
- The performance of the models was evaluated on the testing datasets to determine their accuracy in predicting AQI.

### 3.3 Key Findings
- Among the three algorithms, the **Random Forest** model yielded the highest accuracy when tested on the Ridge Regression-imputed dataset.
- This suggests that the combination of Random Forest and Ridge-imputed data is the most effective approach for predicting AQI in this project.

## Conclusion
The AQI Predictor Model project showcases the application of data preprocessing, imputation techniques, and machine learning algorithms to address real-world problems. By employing the MICE technique for missing data and rigorously evaluating different models, we identified that the Random Forest algorithm, coupled with Ridge-imputed data, provides the most reliable AQI predictions.

## Getting Started
To replicate this project, follow these steps:

1. Clone the repository.
2. Install the required dependencies.
3. Use the provided CSV files or your own dataset to train and test the models.
4. Run the scripts to perform data analysis, imputation, and prediction.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
