
**Introduction**

The healthcare claims prediction dataset from Kaggle serves as a project for our course, aimed at predicting total claims for individual patients based on their outpatient details and various health conditions over the past years. This is a regression task where we analyze a dataset designed to capture both time series trends and cross-sectional differences across patients.

**Dataset Overview**

The dataset consists of three main files located in the "Data" folder:
patient_data_train.json: Contains training data used to develop the models.
patient_data_test.json: Used for evaluating the performance of the trained models.
train.csv: Includes the target variable, TotalClaim, linked to each patientID.
There are 12 features excluding the target column, which represent patient details such as patientID, sex, age, various health conditions (Conditions.HD, Conditions.HT, Conditions.DB, Conditions.AT), and outpatient costs over the last five years. Due to the presence of many null values in the dataset, various data processing techniques were employed to handle these gaps.
Initial data exploration revealed notable distributions and correlations among features. Visualizations were employed to identify patterns, guiding the decisions made for feature handling and model selection.


**Models Trained**

Throughout the project, different machine learning models were trained using various data processing techniques to assess their performance. Below is a summary of each submission, highlighting the methods and evaluation metrics used:
Submission_1: A Linear Regression model was trained with null values replaced by zeros. Initial data analysis revealed a significant number of nulls, which necessitated specific handling techniques.
Submission_2: The dataset was modified to train Linear Regression, Lasso Regression, and Ridge Regression models. Null values in the outpatient costs were replaced with the mean difference between current and past values, while conditions columns remained unchanged.
Submission_3: Utilized the same null replacement technique as Submission 2, adding hyperparameter tuning to enhance model performance, specifically focusing on Ridge Regression.
Submission_4: Employed the same null handling for an XGBoost model, which yielded the best performance so far, achieving the lowest Mean Absolute Error (MAE) among previous submissions.
Submission_5: Introduced a Random Forest Regressor using the same null replacement method. Although its performance was decent, it did not surpass the XGBoost model in terms of MAE.
Submission_6: Examined Random Forest performance on data with nulls replaced by zeros and observed minimal deviation in model performance.
Submission_7: A CatBoost Regressor was trained, demonstrating strong performance with better MAE values compared to prior models.
Submission_8: Implemented an averaging filter combining CatBoost and LightGBM, which resulted in decent performance, though not as effective as the standalone CatBoost model.
Submission_9: Averages from XGBoost and CatBoost outputs were combined. While training performance was good, the model struggled on the testing set.
Submission_10: Evaluated the XGBoost model using standard data with nulls replaced by zeros, yielding performance similar to Submission 9.
Submission_11: Utilized Optuna for hyperparameter tuning, achieving the best results by integrating multiple models, reaching an MAE closer to 500.

**Evaluation Metrics**

The primary evaluation metric used throughout the submissions was the Mean Absolute Error (MAE), which quantifies the average absolute difference between predicted and actual values, providing insight into model accuracy. Other metrics may also be considered in future analyses to further assess model performance.

**Conclusion**

In this project, we explored various machine learning models to predict healthcare claims using a dataset characterized by significant null values and diverse patient conditions. Through multiple submissions, we implemented different data processing techniques and model architectures. Notably, the combination of LightGBM, CatBoost, and XGBoost, enhanced by a meta-model utilizing Gradient Boosting, led to the best-performing model. By employing Optuna for hyperparameter tuning, we were able to optimize the performance of these models, achieving a Mean Absolute Error (MAE) that significantly outperformed previous submissions
