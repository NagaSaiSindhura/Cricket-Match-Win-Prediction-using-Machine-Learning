**Overview**

This project predicts the outcome of One Day International (ODI) cricket matches, focusing on whether the chasing team will win or lose. Using 20+ years of cricket data (2001–2024) from cricsheet.org, the system applies machine learning models—primarily Random Forest, along with XGBoost and Linear Regression—to analyze match conditions, team performance, and in-game variables. A Flask-based web application allows users to input real-time match data and get instant win predictions, providing strategic insights for analysts, teams, and cricket fans.

**Objectives**

•	Predict ODI match outcomes based on the chasing team’s performance.
•	Incorporate historical match data, including team stats, toss results, and venue details.
•	Build a real-time, user-friendly web application.
•	Deliver accurate predictions (Random Forest achieves 91.60% accuracy).

**Features**


•	Data-Driven Predictions using historical ball-by-ball and match-level data.
•	Rich Feature Engineering including:
o	Runs Left, Balls Left, Wickets Left
o	Current & Required Run Rate
o	Target Score, Batting/Bowling Teams, Venue
•	Exploratory Data Analysis (EDA) with interactive visualizations (Plotly, Seaborn).
•	Multiple Models Tested: Linear Regression, Random Forest, XGBoost.
•	Local Flask Deployment for real-time predictions.

**📂 Dataset**
Source: Cricsheet.org
Period: 2001–2024 ODI Matches
Data Types:
1.	Match-level data – Teams, venue, toss, result, player stats.
2.	Ball-by-ball data – Runs, wickets, extras, dismissals, over/ball sequence.
Final Processed Dataset (winningPred) includes:
•	BattingTeam, BowlingTeam, city
•	runs_left, balls_left, wickets_left, target
•	current_run_rate, required_run_rate
•	result (1 = win, 0 = loss)

**🔍 Methodology**

1. Data Collection & Cleaning
•	Aggregated JSON match files into structured DataFrames (df_matches, df_balls).
•	Removed redundant columns & handled missing values.
•	Cross-verified match and ball data integrity.

2. Feature Engineering
•	Calculated target scores.
•	Derived match state variables (Runs Left, Balls Left, Wickets Left, CRR, RRR).
•	Encoded categorical variables via One-Hot Encoding.

3. Exploratory Data Analysis
•	Visualizations:
o	Player of Match vs Runs/Wickets
o	Strike Rates, Sixes, Top Batsmen, Top Teams
o	Correlation Heatmap
•	Identified key patterns in match outcomes.

4. Model Training
Models Tested:

**Model	Accuracy	Precision	  Recall	 F1   Score**
Linear Regression	 84.69%	     0.33	   0.33	  0.34
Random Forest	     91.60%	     0.92	   0.90	  0.91
XGBoost	           89.07%	     0.89	   0.89	  0.89
Best Model: Random Forest – robust, interpretable, low overfitting risk.

6. Deployment
•	Flask Web App:
o	Input: Batting Team, Bowling Team, City, Runs Left, Balls Left, Wickets Left, Target.
o	Output: Win probability & predicted winner.
•	Local deployment for testing.
•	Models saved with joblib for reuse.
