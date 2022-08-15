# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Yalu Su

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: In order to submit the result and get a score from Kaggle, all negative predictions need to set as 0.

### What was the top ranked model that performed?
TODO: At initial training, the top ranked model is WeightedEnsemble_L3, an esembemle of all models, which followed by RandomForestMSE_BAG_L2.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO:
1.From histgrams, I can see 'season', 'holiday', 'workingday' and 'holiday' should have data type as category.
2.In the heatmap, only temp and atemp have strong correlation.
3.Additional features 'day' and 'hour' are created from 'datetime'.
4.Additional featured 'wind_cat', 'windspeed_cat' and 'temp_cat' are grouped to different category levels based on the actual values. 

### How much better did your model preform after adding additional features and why do you think that is?
TODO: Kaggle score of MSE goes from 1.80810 to 0.65845 as additional features catch more information and better explain the relationedship between features and bike demand.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: For the same train and test dataset, the finanl Kaggle score improved from 0.65845 to 0.55424.

### If you were given more time with this dataset, where do you think you would spend more time?
TODO: 
1.For EDA, could perform PCA for dimention reduction and comepare the result.
2.For tunning, could try more parameters in addition to light GBM and neural network.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|initial|default vals|default vals|default vals|1.80810|
|add_features|default vals|default vals|default vals|0.65845|
|hpo|"Neural Network 'num_epochs': 10,'learning_rate':(1e-4, 1e-2, default=5e-4, log=True),
             'activition':('sigmoid','relu', 'leaky-relu', 'tanh'),
             'dropout_prob':(0.0, 0.5, default=0.1)"|"GBM 'num_boost_round': 100, 'num_leaves': (lower=26, upper=66, default=36)"|default vals|0.55424|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: 

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary
TODO: In the model_train_score line plot, it shows the best model in hpo performs worse than the best model in add_features_model. However, in the model_test_score line plot, it shows the best model in hpo performs better than the best model in add_features_model. A possible reason could be the add_features model is overfitting, whereas hpo has penalty parameters to prevent overfitting, such as drop_out probality. In summary, even AutoGluon is a grate AutoML tool, it's better be used as a starting point of a ML project and improve model performance through hyperparameter tuning. Apart from that, we can see the importance of performing data engineering in a ML project.
