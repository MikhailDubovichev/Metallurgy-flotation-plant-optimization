#Executive summary

This project involves predictive modeling for silica content in iron ore concentrate based on input ore quality and processing parameters from an iron ore flotation plant. The dataset spans six months of observations, with sensor readings recorded at varying intervals (1 to 180 measurements per hour) across 22 features.

Objective:

The primary goal is to predict the silica content in the final ore concentrate to support proactive process adjustments and improve product quality.

Key Steps:

Data Analysis:

Initial exploration revealed no missing values but highlighted duplicate entries and a significant 13-day gap in the time series, likely due to plant downtime.

The dataset was segmented into two parts to address the gap, focusing the modeling efforts on the larger, post-gap segment.

Data Preparation:

The dataset was resampled to hourly intervals to align with the target variable (% Silica Concentrate), followed by handling duplicates and gaps.

Feature engineering steps were performed to ensure consistency and prepare the data for model training.

Modeling (Random Forest):

A Random Forest model was initially trained using all features. Feature importance analysis revealed that % Iron Concentrate had a disproportionately high impact on predictions.

Since % Iron Concentrate and % Silica Concentrate are measured simultaneously, this feature was excluded to prevent data leakage. After exclusion, the model's predictive power dropped significantly (R² = 0.05).

SHAP (SHapley Additive exPlanations) values were calculated to provide a more comprehensive understanding of feature contributions across different predictions. This technique confirmed that the remaining features had limited impact on the target variable.

Modeling (LSTM):

To capture temporal dependencies within the data, a Long Short-Term Memory (LSTM) model was developed.

Initial results showed modest improvement (R² = 0.29). Further parameter tuning, including adjustments to units, epochs, batch size, and learning rate, increased the performance to R² = 0.52.

Additional Techniques:

Feature Importance Analysis: Used to identify the most influential variables in the Random Forest model, providing insights into key factors affecting silica content.

SHAP Analysis: Applied to interpret model predictions and ensure transparency. SHAP values highlighted the limited predictive contributions of most features after excluding % Iron Concentrate.

Grid Search: Employed for hyperparameter optimization in Random Forest and LSTM models to systematically explore parameter combinations and improve model performance.

Conclusion:

Both Random Forest and LSTM models demonstrated limited predictive power, likely due to the low quality of input ore data. The dataset's accuracy should be validated with plant operators to ensure data reliability. Without accurate input data, achieving substantial improvements in predictive performance is challenging.

The data I used here was downloaded from the Kaggle. Below is the description of the dataframe, from the person, who uploaded it to the Kaggle:

"This is a model based on Quality Prediction in a Mining Process data, I downloaded from Kaggle: https://www.kaggle.com/datasets/edumagalhaes/quality-prediction-in-a-mining-process/data
