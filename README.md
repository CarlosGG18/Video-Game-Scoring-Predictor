# Video-Game-Critic-Score-Predictor
<img src='https://user-images.githubusercontent.com/117116368/212447253-3863502a-7a43-43be-bfb7-1e716b307404.jpg' width = "500" height ="400">

The video game phenomenon has been evergrowing since the introduction of ***Pong*** back in 1958 and continues to be one of the leading revenue driving markets, bringing in about $90.1 Billion in revenue in 2022 in the United States alone. Since 2020 gamers have been climbing the world domination ladder with over 2.7 billion users worldwide and to put it in perspective the world population is at 7.8 billion ~ **35% of the worlds population are gamers, LETSSS GOOOO** 

Seriously though, this project will incorprate multiple machine learning models to accurately predict crictic scores and appropriately vizualize worldwide sales and trends. My dataset is from [Kaggle's dataset](https://www.kaggle.com/datasets/sidtwr/videogames-sales-dataset?select=Video_Games_Sales_as_at_22_Dec_2016.csv) containing over 16,000 video game records, but after cleaning left with a little over 6,000

## Table of Contents
* [Cleaning](#Cleaning)
* [EDA](#EDA)
* [Models](#Models)
* [Predictions](#Predictions)

## Cleaning

The dataset consists of 16500 games from years 1985 through 2015, the data contains information on Release Year, Genre, Publisher, NA Sales, EU Sales, JP Sales, Other Sales, Global Sales, Critic Score, Critic Count, User Count, Developer, and Rating. After removing NaNs/Null values 6825 games remained in the dataframe, which can be added to in the future through Steam API.

Data types were mainly correct with the exception of year of release. Genre, Rating, and Platform had been transformed into categoricals in order for models to accept value for example:

After passing column ["Genre"] through LabelEncoder(): 

Categorical value ['Action'] is replaced with numerical value [0]
Categorical value ['Adventure'] is replaced with numerical value [1]
Categorical value ['Fighting'] is replaced with numerical value [2]
Categorical value ['Misc'] is replaced with numerical value [3]
Categorical value ['Platform'] is replaced with numerical value [4]
Categorical value ['Puzzle'] is replaced with numerical value [5]
Categorical value ['Racing'] is replaced with numerical value [6]
Categorical value ['Role-Playing'] is replaced with numerical value [7]
Categorical value ['Shooter'] is replaced with numerical value [8]
Categorical value ['Simulation'] is replaced with numerical value [9]
Categorical value ['Sports'] is replaced with numerical value [10]
Categorical value ['Strategy'] is replaced with numerical value [11]

## EDA
![platform_dist](https://user-images.githubusercontent.com/117116368/222000155-0b08ce33-1cc6-4796-b95c-1f26db861f39.png)

* Exploring the disribtiuon of most frequent games by platform can immedietly see that PlayStation 2 games dominate in representation, followed by Xbox360. These distributions make sense as the most represented games are from years 2003-2010 as seen in the distribution plot below.

![year_dist](https://user-images.githubusercontent.com/117116368/222000772-2c5f0ceb-fe09-464f-8520-95b1cfd5ea05.png)

* I then wanted to see the relationships between Critic Scores & Global Sales based off Genre and Platform. I cut critic scores equally into three catigories (Low, Average, High) then produced a heatmap to get a visual on which are the best selling.

![genre_heatmap](https://user-images.githubusercontent.com/117116368/222002178-7f7bc865-955d-4afa-a499-963c556ec0b9.png)

