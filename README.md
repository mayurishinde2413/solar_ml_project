# Solar Power Forecasting Using Random Forest and XGBoost

## Project Overview

Solar energy generation depends on environmental factors such as solar radiation, temperature, and humidity. These variations make it challenging to predict future solar power output accurately.

This project uses Machine Learning regression algorithms — **Random Forest Regressor** and **XGBoost Regressor** — to predict the next hour's average solar power using historical power generation, weather measurements, and time-based features.

## Objectives

- Analyse solar power generation and weather data.
- Clean and preprocess the dataset.
- Convert five-minute readings into hourly averages.
- Create lag features and time-based features for forecasting.
- Train Random Forest and XGBoost regression models.
- Compare model performance using R² score, MAE, and RMSE.
- Identify a suitable model for short-term solar power forecasting.

## Dataset

**Source:** [DKA Solar Centre — Alice Springs](https://dkasolarcentre.com.au/download?location=alice-springs)

The dataset contains solar power generation and weather observations recorded at five-minute intervals.

For this project, the latest 100,000 rows were selected from the original Excel file.

- Records selected initially: 100,000
- Records remaining after initial data cleaning: 99,987
- Sampling interval: 5 minutes
- Forecasting interval: Next hour
- Target variable: Next hour's average `Active_Power`

The data was resampled into hourly averages before feature engineering.

### Features Used

| Feature | Description |
|---|---|
| `Active_Energy_Delivered_Received` | Active electrical energy delivered or received |
| `Current_Phase_Average` | Average electrical current across phases |
| `Weather_Temperature_Celsius` | Ambient temperature |
| `Weather_Relative_Humidity` | Relative humidity |
| `Global_Horizontal_Radiation` | Solar radiation received on a horizontal surface |
| `Diffuse_Horizontal_Radiation` | Diffuse solar radiation |
| `Wind_Direction` | Wind direction measurement |
| `Weather_Daily_Rainfall` | Daily rainfall measurement |
| `power_lag_1` | Current hour's average power |
| `power_lag_2` | Previous hour's average power |
| `power_lag_3` | Average power from two hours earlier |
| `hour` | Hour of the day |
| `month` | Month of the year |

**Target:** `target`, representing the next hour's average `Active_Power`.

Columns with excessive missing values were excluded where necessary.

## Technologies and Libraries

- Python
- JupyterLab / Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- OpenPyXL

## Methodology

1. **Data Loading:** Load solar generation and weather data from an Excel file.
2. **Data Cleaning:** Check missing values and duplicate timestamps, remove unsuitable columns, and handle remaining missing values.
3. **Resampling:** Convert five-minute observations into hourly averages.
4. **Feature Engineering:** Create lag features and time-based features.
5. **Target Creation:** Shift `Active_Power` to obtain the next hour's average power as the prediction target.
6. **Train-Test Split:** Split the data chronologically into 80% training data and 20% testing data, without shuffling.
7. **Model Training:** Train Random Forest and XGBoost regression models.
8. **Evaluation:** Compare the models using training and testing R² scores, MAE, and RMSE.
9. **Visualisation:** Plot actual versus predicted solar power values.

## Model Performance

The following results were obtained during model evaluation:

| Metric | Random Forest | XGBoost |
|---|---:|---:|
| Training R² | 99.65% | 98.89% |
| Testing R² | 97.85% | 97.97% |
| Test MAE | 0.258 | 0.262 |
| Test RMSE | 0.615 | 0.598 |

### Results and Observations

- Both models achieved strong testing R² scores.
- Random Forest achieved a slightly lower MAE of 0.258.
- XGBoost achieved a slightly higher testing R² of 97.97%.
- XGBoost also achieved a lower RMSE of 0.598.
- Based on testing R² and RMSE, XGBoost is the preferred model in this experiment, although both models performed similarly.

*Note: MAE and RMSE are expressed in the same units as the target variable, `Active_Power`.*

## How to Run the Project

1. Clone or download the project repository.
2. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn xgboost openpyxl jupyterlab
   ```

3. Place the dataset Excel file in the appropriate project directory.
4. Open a terminal in the project directory.
5. Launch JupyterLab:

   ```bash
   jupyter lab
   ```

6. Open the project notebook and run the cells in order.

## Limitations

- The experiment uses only the latest 100,000 rows of the original dataset.
- The models were evaluated using a single chronological train-test split.
- Using current-hour weather measurements assumes those measurements are available at prediction time; a practical advance forecast may require weather forecasts instead.
- Model performance may vary across locations, seasons, and datasets.
- The reported metrics should be validated on additional periods before real-world use.

## Future Scope

- Perform hyperparameter tuning to improve forecasting performance.
- Compare results with baseline forecasting methods.
- Incorporate weather forecasts for more realistic advance prediction.
- Test the models on additional time periods and solar installations.
- Explore longer forecasting horizons and renewable energy management applications.

## Conclusion

This project demonstrates how Random Forest and XGBoost can be used for short-term solar power forecasting. Both models achieved strong predictive performance on the test data. Random Forest produced a slightly lower MAE, while XGBoost achieved a slightly higher testing R² and a lower RMSE. These results highlight the potential of machine learning for analysing solar generation patterns and supporting renewable energy planning.

## Author

**Mayuri Shinde**  
Third-Year Computer Engineering Student  
JSPM's Rajarshi Shahu College of Engineering, Tathawade, Pune

---

*Academic mini-project developed using Python and Machine Learning.*
