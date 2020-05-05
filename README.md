# Kaggle Competition - Titanic Survival Prediction

The purpose of this repository is to demonstrate the entire process of creating a Maching Learning model from begining to end. The final result ranks among top 20% in Kaggle. Large amount of `"good"` Kaggle results are coming from people using answer keys from this [website](https://www.encyclopedia-titanica.org/titanic-survivors/). So the actual ranking is much higher than top 20%. Models tested include __Logistic Regression, XGBoost, Random Forest, and Support Vector__/

__The notebook covers the following important topics__
* __`EDA`__: explore and understand the overall data
    1. Data size
    2. Missing data
    3. Data distribution
    4. Correlation matrix


* __`Feature Engineering`__: Understand the relationship between each variable and target labels. Engineer features that is `generalizable` with optimal `predictive power`
    1. `Age` and `Fare`: Both are predictive but very sparse. Tested various cutoff points to best group data into buckets
    2. `Name`: Name by itself is not useful. Parse the name to obtain prefix (e.g. Mr, Miss, Ms)
    3. `Cabin`: Parse the Cabin grade (e.g. A, B, C ...) 
    4. `Number of siblings, spouse, parent, child on board`: People with 1 relative has much better survival rate. However, people with 2+ relatives shows lower survival rate which is counter intuitive. There is not a lot of data points for people with 2+ relative. So result could be due to random noise. At the end, I just group people into two groups, have or don't have relative on board.


* __`Machine Learning Pipline`__: Create a `data transformer class` to perform all the above feature engineering steps which can be incorporated into ML Pipline. With the pipeline, I don't need to perform feature engineering on train data, dev data, and test data seperately. Instead, the model will perform feature engineering automaticlly before `fit` and `predict`.


* __`Hyperparameter Tuning for (Logistic Regression, XGBoost, Random Forest, Support Vector)`__: 
    1. `GridSearch`: perform gridsearch to obtain optimal hyperparameters that optimized for `accuracy` which is kaggle's evaluation metrics
    


* __`Error Analysis: Discussion on Bias vs Variance`__: 
    1. Why the model has high bias and variance
    2. Perform error analysis on both `test data` and `dev data` to understand where the model fall short
    3. Important findings include: Age are bucketed into too many buckets which was not able to capture overall trend. Cabin has too many group with low amount of data.


* __`Revisit Feature Engineering and Model Tuning`__:
    1. Updated feature engineering based on error analysis
    2. Retrain model with updated data
    