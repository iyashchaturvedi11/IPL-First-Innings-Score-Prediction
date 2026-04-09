🏏 IPL First Innings Score Prediction
A Machine Learning project that predicts the first innings final score in an IPL (Indian Premier League) cricket match based on the current match situation — using historical IPL data from 2008 to 2019.
---





📌 Problem Statement
Given mid-match information (current over, runs scored, wickets fallen, recent 5-over stats, and the two teams), predict what the batting team's final first-innings score will be.
---




📂 Project Structure
```
IPL-Score-Prediction/
│
├── ipl.csv                                          # Raw dataset
├── ipl_score_prediction.py                          # Main Python script
├── First_Innings_Score_Prediction_-_IPL.ipynb       # Jupyter Notebook
├── correlation_heatmap.png                          # Generated heatmap
└── README.md                                        # Project documentation
```
---
📊 Dataset
File: `ipl.csv`
Source: IPL ball-by-ball data (Seasons 1–12, 2008–2019)
Key columns used:
Column	Description
`bat_team`	Batting team name
`bowl_team`	Bowling team name
`overs`	Current over number
`runs`	Runs scored so far
`wickets`	Wickets lost so far
`runs_last_5`	Runs in the last 5 overs
`wickets_last_5`	Wickets in the last 5 overs
`total`	Final first-innings score (target)
---



🏟️ Teams Considered
Only the 8 most consistent IPL teams were included:
Chennai Super Kings
Delhi Daredevils
Kings XI Punjab
Kolkata Knight Riders
Mumbai Indians
Rajasthan Royals
Royal Challengers Bangalore
Sunrisers Hyderabad
---
⚙️ Workflow
```
Raw Data  →  Data Cleaning  →  Feature Engineering  →  Train/Test Split
    →  Model Training  →  Evaluation  →  Prediction



```
Data Cleaning
Dropped irrelevant columns: `mid`, `venue`, `batsman`, `bowler`, `striker`, `non-striker`
Filtered to keep only the 8 consistent teams
Removed first 5 overs of every match (too early to predict)
Converted `date` from string to `datetime`
Preprocessing
One-Hot Encoding applied to `bat_team` and `bowl_team`
Train set: Seasons 1–9 (2008–2016)
Test set: Season 10 (2017)
---



🤖 Models Used
Model	Notes
Linear Regression	Best performer — used for final predictions
Decision Tree Regressor	Higher error, prone to overfitting
Random Forest Regressor	Good but slower
AdaBoost (Linear base)	Marginal improvement over Linear Regression
---


📈 Model Evaluation Metrics
Each model was evaluated using:
MAE — Mean Absolute Error
MSE — Mean Squared Error
RMSE — Root Mean Squared Error
> **Linear Regression** gave the best results and was selected for predictions.
---



🔮 Sample Predictions
Match Info	Teams	Predicted Range	Actual Score \

Season 11, Match 13 (Apr 2018)	KKR vs DD	190–205	200/9 ✅


Season 11, Match 39 (May 2018)	SRH vs RCB	136–151	146/10 ✅

Season 11, Match 50 (May 2018)	MI vs KXIP	176–191	186/8 ✅

Season 12, Match 9 (Mar 2019)	MI vs KXIP	166–181	176/7 ✅

Season 12, Eliminator (May 2019)	DD vs CSK	137–152	147/9 ✅

---
🚀 Getting Started
Prerequisites
```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```
Running the Script
```bash
git clone https://github.com/YOUR_USERNAME/IPL-Score-Prediction.git
cd IPL-Score-Prediction
python ipl_score_prediction.py
```
Using the Prediction Function
```python
#from ipl_score_prediction import predict_score

score = predict_score(
    batting_team='Mumbai Indians',
    bowling_team='Chennai Super Kings',
    overs=12.3,
    runs=100,
    wickets=2,
    runs_in_prev_5=45,
    wickets_in_prev_5=0
)
print(f"Predicted score range: {score - 10} to {score + 5}")
```
---
🛠️ Tech Stack
Tool	Purpose
Python 3	Core language

Pandas	Data manipulation

NumPy	Numerical computing

Scikit-learn

ML models

Matplotlib & Seaborn

Visualization

Jupyter Notebook	

Exploration & prototyping
---

📝 Notes
Predictions are made as a range (`predicted ± 10/+5`) since IPL scores are highly volatile.
The model is trained on Seasons 1–9 and evaluated on Season 10.
New teams introduced after Season 9 are not supported.
---


📄 License
This project is open-source and available under the MIT License.
---

