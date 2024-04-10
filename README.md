# Report

## Analysis Overview

**Purporse** : The main goal of this analysis is to create and, mostly, optimize a model capable of predicting which applicant, requesting a funding, has the most chances of success in their endeavours. That would help the Non Profit Funding Organization find the best applicants. Of course, throughtout that, we are mostly focused on the performance/accuracy of our model.
**Steps** : To start the process, we cleaned our data by dropping irrelevant columns and bining data containing outliers. Next, we assigned our features and target to two variables, x and y. From those variables, we split our data into train data and test data. The train data was to train our model and making it accurate while our test data was to actually see the performance of our model when given a new dataset. Our last step was to optimize the model to reach an accuracy of 75%.

## Results
Results: 
On the first try, our model gave an accuracy of 74.10% on train data and one of 72.05% on test data.
On the last optimization try, the accurcay on train data was 73.79% and 73.24% on test data.

## Data Preporcessing
Data Preprocessing
- **What variable(s) are the target(s) for your model?**
Target : the column 'IS_SUCCESSUL' was our target as it confirms if funding was a success or not.
- **What variable(s) are the features for your model?**
Features : the rest of the columns that contained information about the applicants (status, ask amount, application type, type of funding, etc.)
- **What variable(s) should be removed from the input data because they are neither targets nor features?**
We removed ID columns that have nothing to do with the description of the dataset.
## Compiling, Training, and Evaluating the Model

- **How many neurons, layers, and activation functions did you select for your neural network model, and why?**
The inital model containted 2 hidden layers, one with 80 neurons and another with 30, both using a tanh activation while the last layer had 1 neuron with a sigmoid activation.
Two layers were chose because the features were more than 10, and 80 neurons was a first guess since the features were very variate (they don't seem to have a dominance so our model would reach a better performance with iteration). The Tanh activation was chosen because the dataset is multidimensional and might not be linear. The last layer is a sigmoid one because we are facing a classification problem with a binary outcome.
- **Were you able to achieve the target model performance?**
Unfortunately, the target of 75% was not achieved.
- **What steps did you take in your attempts to increase model performance?**
The optimization is detailed in the notebook. The first try was to balance our features to have the same value_counts per categories. Unfortunately, the model performed at 69%. The second try was to increase the nods by 10, but no change came up. After multiple tries, an accuracy of 73% was achieved, using our original features, 90 neurons on the first layer, 40 on the second, 35 on a third added layer and 500 epochs.
*Detailed in the Notebook*
- tryout #1 :Before changing my model, I chose to ran it as it was, just to check the result from downsizing the following 3 features APPLICATION_TYPE, CLASSIFICATION & INCOME_AMT (the model would keep 2 hidden layers with tanh activations and 1 ouput layer with a sigmoid activation + 100 epochs). It returned an accuracy of 69% (3% less then my initial model). Mathematically speaking, I believe this is normal as we lowered the number of our explanatory variables, going against the Law of Large Numbers.
- tryout #2 :Now, I decided to compensate with this "loss" by adding an extra layer and increasing the first two layers' nods by 10. Unfortunately for me, the accuracy remained at 69%.
- tryout #3 :My next try was to run 500 epochs instead of 100. We stayed at an accuracy of 69%
- tryout #4 :My next try was to remove the binning done for the income amt. The accuracy reached 70%.
- tryout #5 :Since the accuracy didn't improve, I decided to revert back to our original binings and only apply the new hidden layer and the increase of epochs.

## Summary
Overall, the model didn't perform well. It would be recommended to study the dataset again and see how we could bin features to create columns equaly balanced and totally remove outliers instead of trying to make them fit in a bin. Next, I'd suggest to increase the layers, nods and epochs but at a decent level as it would slow the model.
