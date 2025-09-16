# NBA All-Star Prediction
By Jimmy Hwang

## Overview
Machine learning models were used to predict NBA All Star status using both traditional and advanced player statistics. The dataset covers the period from the NBA–ABA merger in the 1976–77 season through the 2024–25 season, with all data collected from Basketball Reference. The goal of this project is to classify players as an All Star or not across multiple seasons. Snub cases can also be identified where an All-Star is predicted by the model but the player was not selected.

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
