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

* Exploring the disribtiuon of most frequent games by platform can immedietly show that PlayStation 2 dominate in representation, followed by Xbox360. These distributions make sense as the most of the games are from years 2003-2010 exhibited below, this can be a problem as underepresented classes can limit the predicting power of other features.

![year_dist](https://user-images.githubusercontent.com/117116368/222000772-2c5f0ceb-fe09-464f-8520-95b1cfd5ea05.png)

* I then wanted to see the relationships between Critic Scores & Global Sales based off Genre and Platform. I cut critic scores equally into three categories Low(0-33), Average(33-66), High(66+) then produced a heatmap to get a visual on which are the best selling. Generally with a high average of global sales its expected to have a high critic score but Strategy and Adventure dont share the same treatment as even with a high critic score they fall short on sales. Miscellaneous which have a hard time being categorized have high levels of global sales regardless of its critic score making it difficult to factor in its impact on critic score.

![genre_heatmap](https://user-images.githubusercontent.com/117116368/222002178-7f7bc865-955d-4afa-a499-963c556ec0b9.png)

* Alternatively to genre, platform had major differences which may be contributed to the influence on region. Xbox, PC, and PS Vita had all suffered negatively regardless of score class in comparision to the Wii, PS4, or DS as North American and European countries seemed to prefer devices that were not handheld. Nintendo had a stronghold on the market for some time but the PlayStation4 was liked globally.
 
![platform_heatmap](https://user-images.githubusercontent.com/117116368/222275076-16a11405-4772-42cc-8f37-e34b183fb54a.png)

## Modeling
* When all 6 models were evaluated on the test set after cross validation and hyperparameter tuning, the results were the following:

Multilinear Regression Model Test Score: 49.09
Lasso Regression Model Test Score 48.27
Random Forest Regression Model Test Score: 61.8
Extreme Gradient Boosting Model Test Score: 62.4
Extra Trees Regression Model Test Score 62.29
Polynomial Boosting Model Test Score: 64.56

* The predictive power of the Polynomial model performed the best, making it safe to say that the features used to predict critic score did not hold strong relatinships but needed to test to see how well they performed nontheless.

![image](https://user-images.githubusercontent.com/117116368/222280281-03b1785b-e82f-4862-8a76-ed1b6116e62f.png)

New Super Mario Bros's predicted critic score (using Linear Regression) is: [91.85603598]

New Super Mario Bros's predicted critic score (using Lasso Regression) is:[90.96478734]

New Super Mario Bros's predicted critic score (using Random Forest Regression) is:[88.52]

New Super Mario Bros's predicted critic score (using XGBoost Regression) is [89.19692]

New Super Mario Bros's predicted critic score(using Extra Trees Regression) is:[89.]

New Super Mario Bros's predicted critic score(using Polynomial Regression) is:[88.99919572]

![image](https://user-images.githubusercontent.com/117116368/222279906-be4da855-88a5-4790-a2ec-ba8fc3008158.png)

Deadly Premonition's predicted critic score (using Linear Regression) is: [74.97461603]

Deadly Premonition's predicted critic score (using Lasso Regression) is:[74.95473125]

Deadly Premonition's predicted critic score (using Random Forest Regression) is:[81.67]

Deadly Premonition's predicted critic score (using XGBoost Regression) is [79.72436]

Deadly Premonition's predicted critic score(using Extra Trees Regression) is:[81.62]

Deadly Premonition's predicted critic score(using Polynomial Regression) is:[80.16344866]

![image](https://user-images.githubusercontent.com/117116368/222280798-f48a10b1-31d5-4d3e-a36f-78a34d75d403.png)

Metal Gear Solid 2's predicted critic score (using Linear Regression) is: [80.47350615]

Metal Gear Solid 2's predicted critic score (using Lasso Regression) is:[80.74757826]

Metal Gear Solid 2's predicted critic score (using Random Forest Regression) is:[94.76]

Metal Gear Solid 2's predicted critic score (using XGBoost Regression) is [97.337105]

Metal Gear Solid 2's predicted critic score(using Extra Trees Regression) is:[96.]

Metal Gear Solid 2's predicted critic score(using Polynomial Regression) is:[93.20218338]

* Overall despite model test scores being relatively low, for 2/3 examples Polynomial and Extra Tree's were able to closely predict the critic scores.
