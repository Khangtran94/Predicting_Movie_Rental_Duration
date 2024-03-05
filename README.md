# *Predicting Movie Rental Duration*

![Untitled](https://github.com/Khangtran94/Predicting_Movie_Rental_Duration/assets/146164801/9c8ed226-4f6c-4bc9-97a5-ca36529591c1)

* Using Machine Learning techniques to predict the number of days a customer will rent a DVD for.
* The model will help the company become more efficient inventory planning.

## Target goals:

A regression model which yeilds a MSE is less than or equal to 3 on a test set.

### Methods Used:
* Machine Learning
* Predictive Modeling
* Feature Extraction
* Model Linear Regression
* Hyperparameter tuning
* Model Random Forest
* Model Evaluation

### Technologies
* Python / Jupyter Notebook
* Pandas, sklearn

# Dataset information:
The dataset has **15861 rows** and **15 columns**.

![Untitled](https://github.com/Khangtran94/Predicting_Movie_Rental_Duration/assets/146164801/ec5448fc-da9f-4837-a1dd-d927661a12d4)

![Untitled](https://github.com/Khangtran94/Predicting_Movie_Rental_Duration/assets/146164801/8d158057-b473-40a1-9d51-bddee7261bd9)

## Step by step:
### 1. Getting the number of rental days:
* Rental Length = Return Date - Rental Date
* Rental Length: How many days a DVD has been rented by a customer.

### 2. Adding dummy variables using the "special features" column.
* By create two more columns:
  - Deleted_Scenes: Value 1 equal to the movie if it has the deleted scenes.
  - Behind_the_Scenes: Value 1 equal to the movie if it has the behind the scenes.

### 3. Drop columns:
* These are the columns we don't need for further analysis:
  - **special_features**: because we used the value in this column to create dummy variables for the other 2 columns.
  - **rental_date**: We use it to calculate rental_length.
  - **return_date**: We use it to calculate rental_length.
Therefore, the dataset will become:

![Untitled](https://github.com/Khangtran94/Predicting_Movie_Rental_Duration/assets/146164801/2bb7743e-6e3d-474b-9ad7-b69cbe4a4b9e)

### 4. Define Feature and Target:
* Feature: all columns except **rental_length_days**
* Target: **rental_length_days**

### 5. Executing a train-test split:
* Train set: 80%
* Test set: 20%

### 6. Performing feature selection then use the Linear Regression to predict the data:
* Using Lasso to identify the features with the best prediction power for the target variable.
![Untitled](https://github.com/Khangtran94/Predicting_Movie_Rental_Duration/assets/146164801/79505c4f-7088-4827-8a28-7c9b345c3cf6)

* This reveals the feature importance values, where positive values indicate a positive contribution to the model's effectiveness.
* It also highlights that three features **("amount", "amount_2" and "length_2")** have the most significant influence on the model's performance.
* We use the Linear Regression combined with the feature importance.

### 7. Hyperparameter tuning for RandomForest:
* n_estimators: *from 1 to 100* number of decision trees that will be grown and combined in the ensemble. 
* max_depth:    *from 1 to 10*  parameter controls the maximum depth of each individual decision tree in the forest.
* After hyperparemter tuning: the best parameter is:
  - n_estimator = 51
  - max_depth = 10
  
## Compare the Mean Squared Error (MSE) between two models: 

![Untitled](https://github.com/Khangtran94/Predicting_Movie_Rental_Duration/assets/146164801/32d2c6da-fa1e-4e8e-b60b-a89cdf4740c1)

* Conclusion: Random forest gives lowest MSE and satisfied the request from a DVD rental company.


