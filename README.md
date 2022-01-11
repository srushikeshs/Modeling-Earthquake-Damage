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
