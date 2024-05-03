# Predictive modeling (XGBoost & Logistic-Regression) with Object-Oriented-Programming (OOP) using Python/SQL
## UCI MSBA in collaboration with AbbVie Capstone Project:
Utilizing Python and SQL to forecast disease progression in patients through advanced analysis of medical record datasets (Condition-to-Condition Prediction), considering condition sequence as a factor (time series concept).

## Goal:
To optimize pharmaceutical production and improve individual healthcare strategies by leveraging extensive datasets of patient medical records.

## About the Object-Oriented-Programming (OOP) codes:
The document contains multiple functions relevant to data preprocessing, visualization, and analysis within a Python environment, focusing primarily on handling event sequences and statistical modeling.

* Filter Simultaneous Events:
  This functionality filters and combines simultaneous events based on their dates. It produces a dataframe sorted by person_id and event_date, which can then be used for further analysis.
* Distribution Visualization:
  A function designed to visualize the distribution of categories within a specific column of a dataframe, allowing users to understand the dataset's composition better.
* Individual Patient's Event Sequence Visualization:
  This feature enables the visualization of the event sequence for a single individual, identified by person_id, by displaying the journey through different events in a dataframe format.
* Condition Pair Generation:
  A method for generating condition pairs from event sequences, allowing for a detailed analysis of condition transitions.
* Significant Event Filter:
  Provides functionality to identify significant events based on a predefined ratio setting, aiding in the distinction between common and rare events for focused analysis, and filter out those rare.
* Event Sequence Construction:
  A process for constructing an event sequence dataframe, including condition pairs and the last event for each person_id, enabling a comprehensive view of event transitions.
* Focus Event Analysis:
  This function allows users to focus on specific events, adjusting the analysis to concentrate on particular areas of interest within the event sequence data.
* XGBoost Feature Importance Visualization:
  Offers a way to visualize and understand the importance of different features in an XGBoost model by plotting the top n features based on their importance scores obtained from the model.
* Predictive Modeling and Evaluation:
  Includes importing necessary packages and setting up a predictive model using sklearn, xgboost, and other statistical modeling tools. It involves data splitting, model training, and evaluation metrics like accuracy, F1 score, and recall.

***
***
***

## OOP Usage Example and Results 【Data Preprocess】
##### Original data looks like this (Cancer Patient data):
<img width="477" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/10270e7a-45c3-4a01-ac58-1d8a5b0a3664">


##### First import the package:
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/45bdb5f2-c28d-4d31-b576-b87858318353)

##### Use the class "preprocess" and start with using the "Filter Simultaneous Events" function:
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/f6148944-e501-447a-af21-997b5e1c20ea)


##### The data will combine those events that are recorded on the same date into one using "+"
<img width="425" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/38b63eb2-d2c0-457c-9475-32b2e745685f">

##### The "Distribution Visualization" function (0.01 is adjustable)
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/0e3f6ec6-4f4b-4f19-8c8d-7a954446392d)

##### "Significant Event Filter" (0.01 is adjustable)
<img width="417" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/8f61910b-3aed-4403-bd35-fd383d084a50">

##### "Individual Patient's Condition Journey" (Pick whatever patient to conduct specific analysis) 【dataframe】
<img width="457" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/b4e0e7b6-c54d-4b65-9a94-3c0d9b9dfa92">

#####
<img width="402" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/1738d55a-d277-42d7-a0ac-772b89ac1443">


##### "Individual Patient's Condition Journey" (Pick whatever patient to conduct specific analysis) 【nodes graph】
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/7120556b-6778-4a09-9e30-d2467a768441)

##### Create a condition sequence for each patient (in columns way)
<img width="1139" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/367fb000-9fcf-46a3-b81f-aeea4212a857">


##### Filter out those patients who have a short condition journey (2500 is adjustable)
<img width="1136" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/4e102933-7a63-4691-820c-cf4fbdf52def">

##### See the distribution of those picked (2500) patients' last conditions
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/b1c0e716-429a-4247-97f6-190df8e9818d)

##### Generate condition pairs (2 conditions paired as one) using "combinations" for each patient, and record the starting and weighted (avg) position of the pairs
<img width="736" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/9dc1a124-6007-4c14-8358-baa6ecfd0aed">

##### Calculate the average position of the same condition pairs (since the same one may appear multiple times in a patient's journey) for each patient
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/e4e34ec2-8eca-422f-a2f7-c409b2f9c567)
##### 0 means the pair doesn't exist in that patient, any value higher than 0 means there is at least one appearance of the pair in that patient's journey
##### The data frame for the starting position:
<img width="1121" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/b58bc750-baa6-4116-b9d1-cf2d398e760d">

##### The data frame for the weighted position:
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/732313bf-e586-459d-a01e-a4685dc7e7cd)

#####
<img width="1123" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/12ae7493-6d7e-439c-b44f-c990cdc40173">

***
##### One thing of note is that I also make the position into categorical data (which 1 means the position is in the early 25% of the patient's journey, 2 means 25%~50%, 3 means 50%~75%, 4 means the latest 25%. 0 still means there is no appearance of that pair)
<img width="1124" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/419a0402-0b36-4f2d-83f5-8251417a4e81">

#####
<img width="1124" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/3d5fcd54-57df-43a8-b147-6cf15f6a51fc">

***
***
***
## OOP Usage Example and Results 【Data Splitting and Model Building】
##### The package includes function that allow users to split data and train models (XGBoost and Logistic-Regression).
### Let's first take a look at the XGBoost model building.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/bd4fd71c-cbe0-4849-9b0d-06b2541dc5a1)
##### The result of the model on the "starting position" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/92f923fc-e3b5-4b42-92fb-441e6ad0106b)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/6f8877fa-d592-43d3-9a28-11c880a335b7)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/59003a17-c7ff-4320-ace1-ea86b4d2515b)
##### What are the condition pairs that are important for the model to make predictions? (10 is adjustable, if you want to see more important pairs)
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/1a874e1c-e691-4d3b-aa6f-1b3b915dd780)

##### The result of the model on the "starting position part" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/1bddadaa-93aa-4752-8986-2d50f2792839)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/91518ef7-6565-4e4d-9c7a-76c535164f1f)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/40011a54-0244-462f-9e31-c8a0a8beecce)
##### What are the condition pairs that are important for the model to make predictions?
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/9144cfea-c369-4d36-8d32-0f756adfbe17)

##### The result of the model on the "weighted position" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/5e301a99-cb91-4574-a9d3-39c8f31a0130)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/2a377bf1-3d80-4ed4-9001-eaf0069e8b4b)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/e05318fe-baa6-4225-a718-a98f0fbfc540)
##### What are the condition pairs that are important for the model to make predictions?
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/a8cae591-b2d3-497f-93b5-8141e4ec2682)

##### The result of the model on the "weighted position part" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/5329e204-2961-409d-baf5-b6a6d7669928)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/2684e172-a5dd-4881-a804-d175e7a6654d)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/2e0e2b7e-8480-402c-9d01-9cd972e84d20)
##### What are the condition pairs that are important for the model to make predictions?
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/eb08df2b-824e-44b6-ab9d-e1e14ce234b1)

***

### How about the Logistic-Regression model building?
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/eeed8505-a9c9-4ba3-ae3d-edebb4884364)
##### The result of the model on the "starting position" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/adab3c99-b952-4ea8-9a91-54a557e49dae)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/152aca29-4c7a-42a1-af00-f51f7fb0d4c4)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/a6f47e26-b762-4aff-a138-bb93ec8f3f36)
##### What are the condition pairs that are important for the model to make predictions? (10 is adjustable, if you want to see more important pairs)
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/5ab13028-5c8f-437b-92be-94888512b2f1)

##### The result of the model on the "starting position part" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/5de9092a-cf86-4e6b-a96b-c54d6cb29d89)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/51d692a8-e790-4c7e-b125-0d60c9372fb7)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/1b050dfe-6fb2-4107-bd63-c6c89331d084)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/5c68089a-767a-4086-9ef4-0ef4e61018fd)
##### What are the condition pairs that are important for the model to make predictions?
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/96944d4d-a490-4e4f-819d-6901fff22a15)


##### The result of the model on the "weighted position" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/6b3ce75e-4a63-4885-a2ec-a67e0703b9b9)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/99a46df5-2dff-42e7-8d48-6f16a7e27df2)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/26983677-2222-469f-9754-12a7667727b7)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/52783c93-e45d-4868-9cbd-08a867f5c525)
##### What are the condition pairs that are important for the model to make predictions?
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/e50496ec-ea95-4f3d-9f05-60525900261c)


##### The result of the model on the "weighted position part" data.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/06da16a9-db79-4ac6-943b-8729062b78c8)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/bf6bd0b4-f75a-4868-9ddb-35ba397a0d9c)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/3d29fefc-a7bd-4ebf-a7e8-27ad37aa29cc)
#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/37ab1833-de5d-47cf-95b9-6c9388ba5baa)
##### What are the condition pairs that are important for the model to make predictions?
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/0e510661-b900-4969-ab44-9aa8ad0fbb0f)


***
***
***
## OOP Usage Example and Results 【Making predictions on new data】
##### There are functions that allow users to use the trained models to make predictions on new dataset.
##### The data preprocessing parts are almost the same.
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/1172f217-c27c-442e-aac5-5ad1ef4192e1)

##### The model will take in the preprocessed new data as input and make predictions.
##### Below is the result of the model "XGBoost trained by position / position part data" (based on which one you put in when calling the class) 【Here I used XGBoost trained by starting position part / weighted position part data】:
<img width="286" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/e33a21f3-4be4-4a58-b0d9-ed9695395510">
<img width="272" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/6653ffe5-89af-4c72-be77-696fd1045f09">

##### And Below is the result of the model "Logistic-Regression trained by position / position part data" (based on which one you put in when calling the class) 【Here I used Logistic-Regression trained by starting position part / weighted position data】:
<img width="281" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/49b24f65-30b5-4269-b1e4-a4e10185b9c4">
<img width="277" alt="image" src="https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/904f8708-db92-4067-bf07-466c5922bcdf">

##### Take a look at the visualizations of the difference in predicitons for each model:
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/8e0025aa-0dd2-441c-aab9-11b04c1aa185)

#####
![image](https://github.com/PingYenC/Predictive-modeling-with-Object-Oriented-Programming/assets/164700831/e8721f15-dd04-40d8-96fc-fccd641dbc35)
