# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Alaa Mohamed

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The initial predictions did not have negative values so I did not change anything. However, the count variable can not be of negative value and therefore any negative values need to be set to zero before submission. I did this step during the next two requirements in feature creation and hyperparamter tuning.

### What was the top ranked model that performed?
The top ranked model was WeightedEnsemble_L3 which is a weighted combination of different models with score value of -50.614.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
During EDA I examined the features' data types and made some necessary conversions like converting some features to datetime and category. I visualized the features' histogram for better understanding the data and some insights. For example, bike sharing increases during working days. Also, temp and a temp features are nearly normally distributed.
I added new features from the datetime, converting it into separate month, hour, and day. 

### How much better did your model preform after adding additional features and why do you think that is?
The feature creation step improved the performance. The training RMSE changed from -50.614 using the original data to -29.30 with some new features. Also, on Kaggle submission the score improved significantly from 1.77 to 0.80.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
While the RMSE during training worsened a little with value of 34.09. I noticed improvements in the kaggle testing score. Which suggests that the model is generalizing to unseen data better. However, I believe trying different combinations are ought to improve the RMSE as well.

### If you were given more time with this dataset, where do you think you would spend more time?
I would spend more time on data preparation and feature engineering. Since, Autogluon handles most of the hyperparameter tuning and model stacking internally. I believe the spending more time on data is more important and have significant improvements like we have seen in the second requirement.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|    | model        | hpo1                                         | hpo2                                                                    | hpo3                                                         |   score |
|---:|:-------------|:---------------------------------------------|:------------------------------------------------------------------------|:-------------------------------------------------------------|--------:|
|  0 | initial      | default                                      | default                                                                 | default                                                      |    1.77 |
|  1 | add_features | default                                      | default                                                                 | default                                                      |    0.8  |
|  2 | hpo          | GBM: num_boost_round: 100, num_leaves[26,66] | NN: num_epochs:10, learning_rate:[1e-4, 1e-2], dropout_prob: [0.0, 0.5] | XGB: n_estimators[100:500], max_depth[6,10], eta: [0.01,0.3] |    0.49 |

### Create a line plot showing the top model score for the three (or more) training runs during the project.


![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.


![model_test_score.png](img/model_test_score.png)

## Summary

The project shows the benefit of AutoMl and specifically AutoGluon in creating ML models. The framework provides fast, easy-to-use AutoML framework which aids in determining the best model for usage. Also, the importance of EDA and feature engineering were shown in producing a robust generalizable ML model. As well as hyperparameter tuning, and how they both can boost the performance to reach the desired performance.
