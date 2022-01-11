# Modeling-Earthquake-Damage

## 1. Overview and Objective
Based on aspects of building location and construction aspects, our goal is to predict the level of damage to buildings caused by the 2015 Gorkha earthquake in Nepal. The damage grade is an ordinal variable where 1 represents low damage, 2 represents medium damage, and 3 represents complete distruction. 

## 2. About the Data
The dataset contains valuable information on earthquake impacts, household conditions, and socio-economic-demographic statistics. There are 38 features with respect to each buildings and damage grade label (indicating level of damage). The training data has 260k+ records.

## 3. Exploratory Data Analysis and Inferences
Below are some of the key insights from Data Exploration

#### 3.1 Correlation Plot 
There are no explicit correlation of the features with damage grade. 
![Alt text](https://github.com/srushikeshs/Modeling-Earthquake-Damage/blob/main/Visualization/Correlation_Plot.png)

#### 3.2 Distribution of Building Age
There are very few buildings which were more than 100 years old. There are buildings which are close to 1000 years old (probably some old monument. From modeling perspective, we will treat these records as outliers. 
![Alt text](https://github.com/srushikeshs/Modeling-Earthquake-Damage/blob/main/Visualization/Distribution_of_Building_Age.png)

#### 3.3 Damage Grade by Building Age
The newer buildings are less prone to severe damage then older buildings. We observe that older buildings are more likely to have severe damage. 
![Alt text](https://github.com/srushikeshs/Modeling-Earthquake-Damage/blob/main/Visualization/Damage_Grade_by_Age.png)

#### 3.4 Damage Grade by No. of Floors
We observe an ordinality in the data. As the number of floor increases the higher the chance of severe damange to the building.
The ordinality is not observed after 4 or more floor onwards as there aren't significant number of observations.
![Alt text](https://github.com/srushikeshs/Modeling-Earthquake-Damage/blob/main/Visualization/Damage_Grade_by_Floors.png)

#### 3.5 Damage Grade by Construction Material
The below chart reveals that the stronger the materials used to construct the building lesser the damage caused to it. 
![Alt text](https://github.com/srushikeshs/Modeling-Earthquake-Damage/blob/main/Visualization/Damage_Grade_by_Construction.png)

## 4. Transforming Geo-Location Information
Geo id captures the geographic region in which building exists, from largest (level 1) to most specific sub-region (level 3).
Possible values: level 1: 0-30, level 2: 0-1427, level 3: 0-12567. The combination of 3 geo ids creates two many classes for a classification model. To convert these categorical information to continous numberical value we pass the geo_level_3_id as input to a three layer Neural Network and train on output that is (geo_level_2_id and geo_level_1_id) and then extract the second hidden layer and use it as a feature in our model. The hidden layer does the feature engineering for us - it captures the important numerical information in the last layer. We extract the last hidden layer (24 nuerons) and feed it to our model as additional feature. 

## 5. Modeling
I tried various tree based models like Decision Tree, Random Forest, XGBoost, and LightGBM. XGBoost and LightGBM outperforms other models (XGBoost > LightGBM). I used LightGBM because reduced training time compared to XGBoost. 

## 6. Evaluation Metric
Used F1-micro averages as the evaluation criteria

A macro-average will compute the metric independently for each class and then take the average (hence treating all classes equally).
Whereas a micro-average will aggregate the contributions of all classes to compute the average metric. 
In a multi-class classification setup, micro-average is preferable if you suspect there might be class imbalance (i.e you may have many more examples of one class than of other classes).

## 7. Result
The tuned LightGBM yielded a F1-micro-average score of 0.7525. 
![Alt text](https://github.com/srushikeshs/Modeling-Earthquake-Damage/blob/main/Submission_Score.png)

## Future Scope
Additionally, we can try ensembling different models together to reduce the variance and improve F1 score. 
