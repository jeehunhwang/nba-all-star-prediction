# NBA All-Star Prediction
By Jimmy Hwang

## Overview
Machine learning models were used to predict NBA All Star status using both traditional and advanced player statistics. The dataset covers the period from the NBA–ABA merger in the 1976–77 season through the 2024–25 season, with all data collected from Stathead. The goal of this project is to classify players as an All Star or not across multiple seasons. Snub cases can also be identified where an All-Star is predicted by the model but the player was not selected.

## Initial Findings
Between 1976 and 2025, the average number of All Stars per season was approximately 25, ranging from a minimum of 23 to a maximum of 29. The 1998–99 and 2011–12 lockout seasons were excluded from modeling due to significant reductions in cumulative data across key features.

## Features
| Feature | Definition |
|---------|-------------|
| **PTS** | Points per game – average number of points scored. |
| **TRB** | Total rebounds per game – includes offensive and defensive rebounds. |
| **AST** | Assists per game – measures playmaking ability. |
| **STL** | Steals per game – counts the number of times a player takes the ball away from an opponent. |
| **BLK** | Blocks per game – number of opponent shot attempts blocked. |
| **TOV** | Turnovers per game – measures ball control and mistakes. |
| **TS%** | True Shooting Percentage – efficiency metric that accounts for field goals, 3-pointers, and free throws. |
| **eFG%** | Effective Field Goal Percentage – adjusts field goal percentage to account for the added value of 3-pointers. |
| **VORP** | Value Over Replacement Player – estimates a player’s overall contribution compared to a replacement-level player. |

## Models
CART, Random Forest, and XGBoost were selected as the classification models. XGBoost showed the strongest balance between precision and recall for identifying All Stars (Class 1). While CART achieved higher recall, it sacrificed too much precision, and Random Forest achieved higher precision but missed too many actual All Stars. XGBoost maintained solid precision (0.74) and recall (0.63), resulting in the highest F1-score (0.68) for All Star predictions. This makes it the most reliable model when both correctly identifying All Stars and limiting false selections are important.

| Model         | Class 1 Precision | Class 1 Recall | Class 1 F1 | Overall Accuracy |
|---------------|-------------------|----------------|------------|------------------|
| CART          | 0.4300            | **0.8800**     | 0.5800     | 0.9300           |
| Random Forest | **0.7700**        | 0.5600         | 0.6500     | **0.9700**       |
| XGBoost       | 0.7400            | 0.6300         | **0.6800** | **0.9700**       |

## 2024-25 Snubs
One of the most interesting takeaways from the XGBoost model is how it points out some possible All-Star snubs. A few actual All-Stars came out as borderline picks according to the model. Jaren Jackson Jr. (20.1%), Jaylen Brown (18.2%), and Kyrie Irving (12.1%) were all selected, but the model wasn’t nearly as high on them. That suggests their selections may have been influenced more by reputation, narrative, team success, or other forms of statistics than by pure stats, which is fair since basketball is about more than just the numbers. Luka was one of the model’s highest-probability picks for the All-Star team, yet he wasn’t selected in reality. The main reason was his calf injury early in the season, which hurt his visibility and availability for the All-Star vote.

Meanwhile, guys like Austin Reaves (39.9%), Desmond Bane (38.7%), Zach LaVine (30.7%), Domantas Sabonis (28.5%), and Tyrese Haliburton (26.2%) didn’t make the official roster, but the model assigned them relatively high probabilities of making the team. Statistically, they even outperformed some players who made the All Star selection, which makes a strong case that they deserved a closer look. All in all, the model doesn’t just predict All-Stars well; it sparks the fun debates about who got snubbed and who maybe got a boost.

## Model Predictions: All-Stars vs. Snubs (with Color Coding)

| Player            | All_Star | Predicted_All_Star | Predicted_Prob |
|-------------------|:--------:|:------------------:|---------------:|
| Shai Gilgeous-Alexander | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9988 |
| Nikola Jokić      | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9977 |
| Anthony Edwards   | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9891 |
| Giannis Antetokounmpo | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9873 |
| James Harden      | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9721 |
| LeBron James      | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9391 |
| Jayson Tatum      | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9369 |
| Tyler Herro       | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9185 |
| Stephen Curry     | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9162 |
| Jalen Brunson     | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.9139 |
| Kevin Durant      | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.8861 |
| Karl-Anthony Towns| <span style="color:green">1</span> | <span style="color:green">1</span> | 0.8435 |
| Victor Wembanyama | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.8374 |
| Cade Cunningham   | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.8342 |
| Donovan Mitchell  | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.7470 |
| Trae Young        | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.6991 |
| Darius Garland    | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.6631 |
| Anthony Davis     | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.6271 |
| Jalen Williams    | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.6018 |
| Alperen Şengün    | <span style="color:green">1</span> | <span style="color:green">1</span> | 0.5945 |
| Luka Dončić       | <span style="color:green">1</span> | <span style="color:red">0</span> | 0.5099 |
| Pascal Siakam     | <span style="color:green">1</span> | <span style="color:red">0</span> | 0.5697 |
| Damian Lillard    | <span style="color:green">1</span> | <span style="color:red">0</span> | 0.5479 |
| Evan Mobley       | <span style="color:green">1</span> | <span style="color:red">0</span> | 0.1220 |
| Kyrie Irving      | <span style="color:green">1</span> | <span style="color:red">0</span> | 0.1218 |
| Jaren Jackson Jr. | <span style="color:green">1</span> | <span style="color:red">0</span> | 0.2018 |
| Jaylen Brown      | <span style="color:green">1</span> | <span style="color:red">0</span> | 0.1825 |
| **Austin Reaves** | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.3988 |
| **Desmond Bane**  | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.3870 |
| **Zach LaVine**   | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.3072 |
| **Domantas Sabonis** | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.2850 |
| **Tyrese Haliburton**| <span style="color:red">0</span> | <span style="color:red">0</span> | 0.2622 |
| **Derrick White** | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.2550 |
| **Devin Booker**  | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.2489 |
| **Franz Wagner**  | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.2369 |
| **Jalen Green**   | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.2150 |
| **Deni Avdija**   | <span style="color:red">0</span> | <span style="color:red">0</span> | 0.1665 |

## References:
Stathead. (2025). Stathead. Sports Reference. https://www.stathead.com/
