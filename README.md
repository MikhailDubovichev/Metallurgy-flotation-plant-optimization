# Executive Summary

I'm uploading here a **flotation plant (metallurgy) optimization pipeline** that I built in Google Colab.  
This project involves predictive modeling for **silica content in iron ore concentrate** based on input ore quality and processing parameters from an iron ore flotation plant. The data I used here was downloaded from [Kaggle](https://www.kaggle.com/datasets/edumagalhaes/quality-prediction-in-a-mining-process/data). The dataset spans six months of observations, with sensor readings recorded at varying intervals across 22 features.

The purpose of this project is purely educational. I wanted to apply various ML techniques to real data as part of my self-study in 2024. I chose a dataset from metallurgy for several reasons:
- **Continuous process industries** (metallurgy, mining, chemicals, cement, pulp and paper, and oil refining) are often overlooked by the ML community but are ideal for predictive modeling due to vast data availability from sensors and the potential for significant financial impact (even a 1% improvement in product quality or throughput can add seven-digit numbers to EBITDA).
- Negative modeling results can often highlight areas for improvement, such as updating **Standard Operating Procedures (SOPs)** or recalibrating sensors.
- Being a **Head of Innovations at a large mining company**, I was responsible for managing the innovation portfolio, including digital assistants powered by predictive models. This project allowed me to explore the inner workings of these systems firsthand.

## Pipeline Objective

To predict the **silica content** in the final ore concentrate based on input ore quality and processing parameters.  
Such a predictive model would allow plant operators to proactively adjust process parameters (based on inflow ore characteristics) to improve product quality.

## Key Steps

1. **Data Analysis**
   - Initial exploration revealed no missing values but highlighted duplicate entries and a significant 13-day gap in the time series, likely due to plant downtime.

2. **Data Preparation**
   - The dataset was resampled to hourly intervals to align with the target variable (% Silica Concentrate), followed by handling duplicates and gaps.
   - Feature engineering steps were performed to ensure consistency and prepare the data for model training.

3. **Modeling**
   - **Random Forest**: Achieved an initial R² of 0.65. After excluding `% Iron Concentrate`, the R² dropped to 0.05.
   - **LSTM**: Improved performance to an R² of 0.52 after **tuning hyperparameters**.

4. **Additional Techniques**
   - **Feature Importance Analysis**: Identified the most influential variables affecting silica content.
   - **SHAP Analysis**: Interpreted model predictions and provided transparency.
   - **Grid Search**: Optimized hyperparameters for Random Forest and LSTM models to improve performance.

## Conclusion

Both Random Forest and LSTM models demonstrated limited predictive power, likely due to the **low quality of input ore data**.  
The dataset's accuracy should be validated with plant operators to ensure data reliability. Without accurate input data, achieving substantial improvements in predictive performance is challenging.

## Recommendation

- Improving the quality and granularity of input ore data.
- Engaging with plant operators to contextualize sensor readings and validate anomalies.
