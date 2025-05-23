# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### STELLAH ANGULU

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The initial output from the predictor had to be formatted to include only the `datetime` and `count` columns in the correct order and format. Additionally, the file had to be saved as a CSV with no index and matched the sample submission format exactly to avoid submission errors.

### What was the top-ranked model that performed?
The top-ranked model in the initial training used AutoGluon’s `"best_quality"` preset, which ensembles various algorithms. Typically, LightGBM models perform well in this setup, but the specific leaderboard output can confirm the top performer.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find, and how did you add additional features?
Exploratory analysis revealed strong time-based patterns in the demand for bikes, such as the hour of the day, day of the week, and weather conditions. New features were added by extracting datetime components (hour, weekday) and incorporating them into the training set, which significantly improved model performance.

### How much better did your model perform after adding additional features, and why do you think that is?
The RMSE improved from **1.74594** to **0.73588**, a substantial gain. The improvement came from the model's ability to leverage new, relevant information that better explained the variance in bike demand.

## Hyperparameter tuning
### How much better did your model perform after trying different hyperparameters?
The Kaggle score remained 0.73588, identical to the model with added features but without tuning. This suggests that while tuning may be beneficial, the feature engineering had a far greater impact in this case.

### If you were given more time with this dataset, where would you spend more time?
I would explore:

- More granular weather features or external data (e.g., holidays).

- Feature interactions and polynomial features.

- Ensembling strategies or stacking.

- Advanced HPO (e.g., Bayesian optimization or longer tuning times).


### Create a table with the models you ran, the hyperparameters modified, and the Kaggle score.
### Model Performance Table

| model        | hpo1           | hpo2            | hpo3             | score   |
|--------------|----------------|------------------|------------------|---------|
| initial      | -              | -                | -                | 1.74594 |
| add_features | -              | -                | -                | 0.73588 |
| hpo          | max_depth=15   | n_estimators=100 | extra_trees=True | 0.73588 |


### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.




### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary
This project demonstrated how feature engineering can have a larger impact than hyperparameter tuning. Using AutoGluon allowed for rapid model development, and even with minimal tuning, significant performance improvements were achieved through thoughtful feature design.
