# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### SAIYAM ARORA

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
When the initial predictions were submitted, it was realized that there were negative values in the predictions. Since the predictions represent counts, negative values are not meaningful in this context. Therefore, the negative values were clipped to zero using the clip(lower=0) function to ensure all predictions are non-negative before submitting the results.

### What was the top ranked model that performed?
In my case the top performing model was WeightedEnsemble_L as it produced the highest scores and gave promising results.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The exploratory data analysis involved visualizing the data using histograms, time series plots, and a correlation heatmap. The analysis provided insights into the distribution of features and their relationships.
To add additional features, I created new features based on the existing data. Specifically, I extracted hour, day, and month from the datetime column. I also created new categorical features such as time_of_day, temp_category, wind_category, humid_category, and atemp_category. These new features were derived based on certain conditions or ranges in the original features.

### How much better did your model preform after adding additional features and why do you think that is?
Earlier without additional features, model WeightedEnsemble_L had score of 2.36 but after additional features being added it was about 2.65 and there was this rise because of new features influencing the model and giving out a better performance, also we had dropped unnecessary columns.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
There wasn't much spike when I tried tunning hyperparameters only a slight change from 0.56479 to 0.56478 was observed.

### If you were given more time with this dataset, where do you think you would spend more time?
If given more time with this dataset, additional focus could be given to the following areas:
Exploratory Data Analysis: Further analyzing the relationships between variables, identifying outliers, and understanding any temporal patterns in the data.
Feature Engineering: Exploring more potential features that can capture the underlying patterns and relationships in the data. This could involve domain knowledge, extracting time-based features, interaction terms, or transforming variables.
Model Selection and Ensemble: Trying out different models and ensemble techniques to see if combining multiple models can further improve the predictive performance.
Hyperparameter Tuning: Experimenting with more hyperparameter configurations, exploring different search algorithms or strategies, and performing more fine-grained tuning to optimize model performance.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|default|default|default|1.84435|
|add_features|default|default|default|0.56479|
|hpo|'CAT': {'iterations': 10000}|'GBM': num_boost_round=100, num_leaves(lower=26, upper=66, default=36)|scheduler: local, searcher: bayesopt|0.56478

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](img/model_test_score.png)

## Summary
In this project, we followed the ML lifecycle and performed the following steps:

Problem: The goal was to optimize the utilization of data in the bike sharing industry and leverage external information to gain business advantages.

Business Objective: The objective was to predict bike sharing demand based on various factors using the available data.

Data Acquisition: We obtained the data from the "Bike Sharing Demand" Kaggle competition.

Data Analysis: We analyzed the data by describing, visualizing, and modifying it using libraries such as Pandas, Matplotlib, and Seaborn.

Model Building: Initially, we built models without any preprocessing using the Autogluon AutomML library. Later, we enhanced the models by creating new features and tuning hyperparameters.

Model Testing: We tested the models by submitting our predictions to Kaggle and evaluated their performance based on the obtained score.
