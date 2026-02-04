# California Housing Price Prediction: A Model Comparison Study

## Project Overview
This project aimed to predict house prices using the Scikit-learn California Housing dataset while documenting the journey from basic linear models to more robust ensemble methods.


## Model Evolution, Challenges, and Results
The analysis followed an iterative approach, revealing key insights into model stability and performance across different architectures.

<img width="561" height="238" alt="image" src="https://github.com/user-attachments/assets/8d5161ba-538b-4340-a430-213055080918" />


### Iteration 1: Baseline SGD Regressor
- Action: Implemented a standard linear model after feature scaling.

- Observation: Achieved a respectable (R^{2}) of 0.58, showing a foundational linear relationship between features and price.

### Iteration 2: Polynomial SGD Regressor
- Challenges: The introduction of 2nd-degree polynomial features led to numerical instability and divergence (extreme errors). The model initially returned a very negative (R^{2}).
- Changes Implemented: Applied a much smaller learning_rate (eta0=0.0001) to stabilize the model's gradients.
- Results & Analysis: While stable, performance decreased to (R^{2}=0.51).The Residual Plot (see notebook image) visually confirmed severe bias (systematic over/underestimation) and heteroskedasticity (errors widening for expensive houses), indicating the linear formula was a poor fit for the data's complexity.

### Iteration 3: Random Forest Regressor
- Action: Switched to a non-linear, ensemble-based model that doesn't rely on gradients.
- Observation: This approach solved both the stability and bias problems immediately.
- Result: Achieved a high-performance (R^{2}) of 0.81, nearly doubling the accuracy of the best SGD model. I noted complex, non-linear interactions (e.g., specific latitude/longitude combinations) are crucial for price prediction in this dataset.

## Visual Summary
The comparative plot below (available in the linked notebook) highlights how much tighter the Random Forest predictions (Green) are to the actual values compared to the linear models (Blue/Violet).

## Further Tests and Future Work
- Feature Engineering: Focus on combining Latitude and Longitude into a single, more meaningful geographic feature.
- Hyperparameter Tuning: Use cross-validation and GridSearchCV on the Random Forest to try to reach an (R^{2}) of 0.85+
- Alternative Models: Explore XGBoost or LightGBM, which often set state-of-the-art results for this kind of structured data.




