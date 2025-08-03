## Model Description

**Input:**
The model takes in features related to Airbnb listings, including numerical attributes such as minimum_nights, availability_365, and number_of_reviews, as well as categorical variables like room_type, neighbourhood, and city. Categorical variables are encoded using LabelEncoder prior to model training.

**Output:**
The output is a single numeric prediction representing the estimated price per night (in USD) for an Airbnb listing.

**Model Architecture:**
Three models were trained and evaluated:

- Linear Regression: A baseline model that assumes a linear relationship between input features and price.

- Random Forest Regressor: An ensemble model of decision trees that captures non-linear relationships and feature interactions.

- XGBoost Regressor: A gradient-boosted tree ensemble optimized using Bayesian optimisation for key hyperparameters like n_estimators, max_depth, and learning_rate.

## Performance

Performance was measured using Root Mean Squared Error (RMSE) and R² (coefficient of determination) on a held-out test dataset. The results are:

| Model      | Test RMSE (↓) | Test R² (↑)
| ----------- | ----------- |----------- |
| Linear Regression| 113.93| 0.1291 |
| Random Forest| 98.10|0.3544 |
| XGBoost|  95.71|0.3855 |


- RMSE indicates how much the predicted price deviates (on average) from the actual price.
- R² measures the proportion of variance in price explained by the model (closer to 1 is better).

XGBoost performed best with the lowest RMSE and highest R².

## Limitations

The models do not account for real-time market dynamics like seasonality or sudden changes in demand.
Performance is limited by the completeness and accuracy of the original dataset (e.g., missing or outdated entries). The models assumes static relationships between features and price, which may not hold over time or across regions.

## Trade-offs

While XGBoost yields better accuracy, it is less interpretable than linear models and requires more compute resources. 

Random Forest is more robust to outliers and non-linearities but may overfit without careful tuning.

Simpler models like Linear Regression are faster and easier to interpret but underperform on complex datasets.