# California Housing Price Prediction: A Model Comparison Study

## Project Overview
This project aimed to predict house prices using the Scikit-learn California Housing dataset while documenting the journey from basic linear models to more robust ensemble methods.


## Model Evolution, Challenges, and Results
The analysis followed an iterative approach, revealing key insights into model stability and performance across different architectures.

<img width="561" height="238" alt="image" src="https://github.com/user-attachments/assets/8d5161ba-538b-4340-a430-213055080918" />


### Iteration 1: Baseline SGD Regressor
<img width="678" height="545" alt="SGD Regressor-Actual Vs Predicted Housing Prices" src="https://github.com/user-attachments/assets/951c0f46-d6d1-4c3c-91fb-31c6c3ea3960" />

- Action: Implemented a standard linear model after feature scaling.
- Observation: Achieved a respectable (R^{2}) of 0.58, showing a foundational linear relationship between features and price.

### Iteration 2: Polynomial SGD Regressor
<img width="833" height="545" alt="SGD Regressor-Polynomial Actual Vs Predicted Housing Prices" src="https://github.com/user-attachments/assets/94b0bf78-e759-4525-a276-85b24446969b" />

- Challenges: The introduction of 2nd-degree polynomial features led to numerical instability and divergence (extreme errors). The model initially returned a very negative (R^{2}).
  <img width="853" height="468" alt="Residual Plot (Errors) for Polynomial Model" src="https://github.com/user-attachments/assets/c484e88e-9847-4676-97ca-efd3ca9e05b0" />

- Changes Implemented: Applied a much smaller learning_rate (eta0=0.0001) to stabilize the model's gradients.
- Results & Analysis: While stable, performance decreased to (R^{2}=0.51).The Residual Plot (see notebook image) visually confirmed severe bias (systematic over/underestimation) and heteroskedasticity (errors widening for expensive houses), indicating the linear formula was a poor fit for the data's complexity.

### Iteration 3: Random Forest Regressor
<img width="833" height="563" alt="Random Forest (Winner)" src="https://github.com/user-attachments/assets/759edc4d-cbdf-4524-97f8-c3022f9f0ee8" />

- Action: Switched to a non-linear, ensemble-based model that doesn't rely on gradients.
- Observation: This approach solved both the stability and bias problems immediately.
- Result: Achieved a high-performance (R^{2}) of 0.81, nearly doubling the accuracy of the best SGD model. I noted complex, non-linear interactions (e.g., specific latitude/longitude combinations) are crucial for price prediction in this dataset.

## Visual Summary
The comparative plot below (available in the linked notebook) highlights how much tighter the Random Forest predictions (Pink) are to the actual values compared to the linear models (Baseline-Purplelue/Polynomial-Green).

<img width="1990" height="590" alt="Baseline-Polynomial-RandomForest" src="https://github.com/user-attachments/assets/ef75852b-1f32-4b68-8ad2-a7c21f06e0df" />


## Further Tests and Future Work
- Feature Engineering: Focus on combining Latitude and Longitude into a single, more meaningful geographic feature.
- Hyperparameter Tuning: Use cross-validation and GridSearchCV on the Random Forest to try to reach an (R^{2}) of 0.85+
- Alternative Models: Explore XGBoost or LightGBM, which often set state-of-the-art results for this kind of structured data.

> Bonus : Which features drive California House Prices?

<img width="902" height="545" alt="Which features drive California House Prices" src="https://github.com/user-attachments/assets/c2c018aa-585b-423a-a3e8-d2532bad185d" />



