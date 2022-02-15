**![](https://lh6.googleusercontent.com/-qpF6VubG1HAsQSiB915zu2FRR1CEA5HkL9iZIjRgyrVj_t4r9oS6f2esZB0e3GAi2jEZ9ZRw4DmnUXJPHkXjwFDp85tKHTZCiUNU2cFBRJZrrVPIR8jQJL4s4ic06eJ-xH16uAH)**
# STEAM GAMES: USING GAME FEATURES TO PREDICT REVENUE

## Context

**What is Steam?**

Steam is a digital platform centered around PC games. Users of the platform can purchase and play games, interact with friends, and participate in a larger community of gaming enthusiasts.

**How does the store work?**

Games on the Steam store are categorized using a user-defined tagging system, which allows for greater flexibility in game categorization and recommendations. 
**![](https://lh5.googleusercontent.com/la2zWMpXxMJ65Mvr-8Y8IOwztQvcX9duzdBeHg_kJFJ8-4IZrBAjLZYU_LiW5A7k2YnO6dkdVvaRmCgjaIhmhNZQMT7f6YODRRC7lqNL3BEstV3-j4jSON9n8CwxoX_Sgq-OBtcY)**

## Objective
1. Design an effective model to predict game revenue.

2. Identify which game features are the most influential in predicting revenue.

## Data

-   Sourced from Nik Davis on [kaggle](https://www.kaggle.com/nikdavis/steam-store-games)
    
-   After cleaning, dataset contained 26,355 games and 35 features.

-   Features include info such as:
	-  a) genre
	- b) type of gameplay
	- c) season of release
	- d) average playtime.
- Target Feature: Revenue (Game Price * Avg Owners)


## Procedure
• **Tools:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-Learn, Joblib

• **Data:** After some cleaning and feature engineering, the final dataset contained 26,355 rows and 43 columns. Features included top 20 genres, style of gameplay, season of release, and playtime.

• **Modeling:** Three models (linear regression, random forest, and gradient boost) were trained, optimized with hyperparameter tuning, and evaluated based on R2, MAE, and RMSE. A best model was selected, and used to predict estimated game revenue.

**Model Metrics:**

| Model |R2 (Train)  | R2 Test | RMSE (Train) | RMSE (Test) | MAE (Train) | MAE (Test) 
|--|--|--|--|--|--|--|
| Linear Regression | 0.55 | 0.53 | 5,360,643.06 | 5,422,963.47 | 1,410,534.18 | 1,422,660.63 
| Linear Regression (Grid Search CV) | 0.55 | 0.53 | 5,360,649.75 | 5,422,949.54 | 1,410,635.20	| 1,422,649.47
| Random Forest | 0.94 | 0.67 | 1,874,654.06 | 4,576,871.91 | 257,098.75 | 672,476.00
| **Random Forest (Randomized Search CV)** | **0.95** | **0.68** | **1,834,738.39** | **4,530,477.82** | **254,405.53** | **666,622.53**
| Gradient Boost | 0.92 | 0.67 | 2,237,714.42 | 4,551,346.36 | 467,590.29 | 656,420.03
| Gradient Boost (Randomized Search CV) | 1.00 | 0.65 | 114,906.85 | 4,688,391.94 | 60,094.85 | 680,286.72

## Key Insights

Game-related features were found to have the most impact on revenue:
-   Games with Steam achievements
-   Indie games
-   RPGs (Role-Playing Games)
-   Co-op (Cooperative) games
-   Games released in summer
-   The number of tags listed in a game

## Limitations

- Distribution of revenue was heavily skewed.
	- Most games generate a fairly low revenue while some generate very high amounts.
	-  Huge disparity between median = $69,650 and mean ? $1,259,000.
- This analysis only took into account the top 20 most popular genres.
	-  In the future, it maybe worth exploring the influence of niche interests.
- Each game is evaluated independently, without considering the impact of pre-existing franchises or established studios.