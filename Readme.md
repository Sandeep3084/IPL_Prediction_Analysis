# IPL Win Prediction Model 
## Problem Statement
Predicting the outcome of IPL matches is a challenging problem due to the
dynamic and stochastic nature of cricket. Accurate real-time predictions can
benefit broadcasters, fans, and betting platforms by providing actionable insights
during live matches.

## Objectives
• Develop a machine learning system to predict the winner in a head-to-head
IPL match scenario.

• Achieve high accuracy and interpretability using logistic regression.

• Build an interactive frontend for real-time simulation and visualization.
## Scope
• Focused on second-innings predictions using historical ball-by-ball data.

• Incorporates match state, team, and venue features.

• Excludes player-level and weather data in the current version.Dataset and Preprocessing
## Dataset Description
• Source: IPL official datasets (2008–2024), including deliveries.csv (3.2GB,
ball-by-ball records) and matches.csv (15MB, match metadata).

• Structure: Each record contains features such as batting/bowling teams,
venue, runs, wickets, balls left, and match outcome.
## Exploratory Data Analysis (EDA)
• Visualized run distributions, win margins, and venue effects.

• Identified missing values and handled them using forward/backward filling.

• Detected categorical features (teams, cities, venues) for encoding.
## Preprocessing Steps
• Temporal Alignment: Matched ball-by-ball records with corresponding
match metadata.

• Feature Engineering: Calculated dynamic features including:

 Current score, runs left, balls left, wickets remaining

 Current Run Rate (CRR) and Required Run Rate (RRR)

 RRR volatility (rolling standard deviation)

• Encoding: Used OneHotEncoder for categorical variables (teams, city,
venue).

• Normalization: Applied MinMaxScaler to numerical features.

• Memory Optimization: Converted categorical columns to reduce RAM
usage by 83%.

• Train-Test Split:
 Split Ratio: 80:20
 Reproducability: random_state=42Methodology

## Machine Learning Model(s) Used
• Primary Model: Logistic Regression with L2 regularization.

• Pipeline:
o ColumnTransformer for encoding and scaling
o LogisticRegression (solver='liblinear') for classification

## Justification
•Interpretability: Model coefficients directly explain feature impact.

 Efficiency: 3x faster training compared to tree-based models.
 
 Stability: L2 regularization reduces overfitting.
 Alternatives Considered: XGBoost (higher accuracy, less interpretable),
 
LSTM (handles sequence, much slower), Ensemble methods (minor
accuracy gain, high complexity).

## Implementation Details
• Feature Set:
o Categorical: batting_team, bowling_team, city, venue
o Numerical: runs_left, balls_left, wickets, total_runs, crr, rrr,
rrr_volatility

• Training:
o Used scikit-learn’s Pipeline for reproducibility.
o Hyperparameters: learning rate = 0.001, L2 regularization = 0.85.
• Prediction:
o Model outputs win probability for the chasing team at any match state.

## Experimental Setup
Hardware/Software Used
• Hardware: Intel® Core™ i5/i7 CPU, 16GB RAM
• Software: Python 3.10+
 Libraries: pandas, numpy, scikit-learn, Dask, Streamlit
 OS: Windows 10 / Linux

## Results and Screenshots of UI
![image](https://github.com/user-attachments/assets/f124399d-d5ab-4d02-9463-02553c36f44e)

![image](https://github.com/user-attachments/assets/10134681-d0cb-431a-8db8-9d949eb22949)

![image](https://github.com/user-attachments/assets/dbcaa89c-a345-46f4-824f-1dd39129e008)

![image](https://github.com/user-attachments/assets/5d4ccdcc-b6b1-4bbe-9323-0909190ed7e2)

![image](https://github.com/user-attachments/assets/f2b6a678-2e9e-45fc-88dd-9337f12ff817)






