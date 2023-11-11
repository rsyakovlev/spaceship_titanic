# "Spaceship Titanic" kaggle challenge

An example of base Kaggle challenge solution with top 3% leaderboard result.

### Link to challenge:
https://www.kaggle.com/competitions/spaceship-titanic/

### Overview
The challenge task is to predict binary "Transported" variable - whether a passenger of Spaceship Titanic was transported to an alternate dimension or not.

### Dataset
./train.csv (8693 observations) <br>
./test.csv (4277 observations) <br>
Dataset contains 13 predictors

### Solution:
./spaceship_titanic.ipynb

### Things with highest contribution to the final result
- "PassengerId" feature is divided into 2 new features: "PassengerId_group" and "PassengerId_number"
- "Cabin" feature is divided into 3 new features: "Cabin_deck", "Cabin_num", "Cabin_side"
- "Name" is divided into 2 new features: "First Name" and "Surname"
- New feature "ServiceFeesSum" is created
- New feature "Nulls" is created
- New 1000 tf-idf features out of "Surname" feature are created and replaced by 10 most informative principal components
- Nulls for numeric features are replaced with train dataset median values
- Nulls for categorical features are replaced with 'None' so that missing values are considered as a category
- Catboost model with 1000 iterations is fitted
- Prediction threshold is set 0.51
