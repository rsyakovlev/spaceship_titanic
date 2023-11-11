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

### Variables
- `PassengerId` - A unique Id for each passenger. Each Id takes the form gggg_pp where gggg indicates a group the passenger is travelling with and pp is their number within the group. People in a group are often family members, but not always.
- `HomePlanet` - The planet the passenger departed from, typically their planet of permanent residence.
- `CryoSleep` - Indicates whether the passenger elected to be put into suspended animation for the duration of the voyage. Passengers in cryosleep are confined to their cabins.
- `Cabin` - The cabin number where the passenger is staying. Takes the form deck/num/side, where side can be either P for Port or S for Starboard.
- `Destination` - The planet the passenger will be debarking to.
- `Age` - The age of the passenger.
- `VIP` - Whether the passenger has paid for special VIP service during the voyage.
- `RoomService`, `FoodCourt`, `ShoppingMall`, `Spa`, `VRDeck` - Amount the passenger has billed at each of the Spaceship Titanic's many luxury amenities.
- `Name` - The first and last names of the passenger.
- `Transported` - Whether the passenger was transported to another dimension. This is the target, the column you are trying to predict.

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
