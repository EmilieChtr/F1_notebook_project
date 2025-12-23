# F1_notebook_project
Machine Learning project where we'll try to predict the best lap time of each driver for a given course and year.

## Project Overview
This project analyzes and predicts Formula 1 lap times using historical race data and machine learning models.  
The objective is to identify the key factors influencing lap performance and to build predictive models capable of estimating a driver’s fastest lap time for a given circuit and season.

The project follows a full data science workflow, from raw data collection to model evaluation, with an emphasis on reproducibility and methodological rigor.

## Authors
- Emilie Chatron — ESILV (MMN2)  
- Élisabeth Cognet — ESILV (MMN2)  
- Nour El Khalili — ESILV (MMN2)

## Data Source
The data comes from a public Kaggle dataset aggregating Formula 1 information across multiple seasons, combining 16 datasets including race results, lap times, drivers, constructors, and circuits.

Two additional circuit features were manually added to improve prediction performance:
- `trackTurns`
- `circuitLength`

Kaggle dataset:
https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020/data

## Repository Structure
```
.
├── data
│   ├── raw
│   └── processed
├── eda_preprocessing_notebook.ipynb
├── pred_notebook.ipynb
├── F1_ml_Cognet_Chatron_El_Khalili.pdf
└── README.md
```

### Folder Description
- `data/raw`  
  Contains the original datasets downloaded from Kaggle. These files are not modified.

- `data/processed`  
  Contains cleaned and merged datasets, as well as the train and test splits generated during preprocessing.

- `eda_preprocessing_notebook.ipynb`  
  Handles data loading, cleaning, exploratory data analysis, feature selection, and time-aware train/test splitting.

- `pred_notebook.ipynb`  
  Contains preprocessing pipelines, model training, hyperparameter tuning, and model evaluation.

- `F1_ml_Cognet_Chatron_El_Khalili.pdf`  
  Final project report detailing methodology, results, analysis, and conclusions.

## Methodology

### Data Cleaning and Feature Engineering
- Removal of irrelevant and redundant variables
- Elimination of future information to avoid data leakage
- Creation of the target variable `fastestLapTime`, defined as the minimum lap time achieved by a driver during a race
- Dimensionality reduction from over 100 initial features to a compact and relevant set

### Exploratory Data Analysis
- Univariate and multivariate analysis
- Correlation heatmaps for numerical variables
- Cramér’s V analysis for categorical features
- Identification of a structural break in 2014 due to hybrid engine regulations

### Train/Test Strategy
A time-aware train/test split was used to preserve temporal consistency.  
Two datasets were evaluated:
- Full history: 1996–2024
- Hybrid era only: 2014–2024

### Models Evaluated
- Ridge Regression
- Random Forest
- XGBoost
- CatBoost

### Evaluation Metrics
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² score

## Results
- Linear models were unable to capture the non-linear nature of Formula 1 performance
- Restricting training to the hybrid era significantly improved predictive accuracy
- Random Forest achieved the lowest MAE but showed higher variance
- **CatBoost (tuned)** was selected as the final model due to its stability, lowest RMSE, and highest R²

## Key Insights
- Circuit length and number of turns strongly influence lap times
- Street circuits are more difficult to predict due to chaotic race conditions
- The model predicts theoretical car performance rather than race strategy or driver management

## Future Improvements
- Integration of telemetry and sector-level data
- Two-stage modeling to detect abnormal laps before regression
- Inclusion of live contextual data such as weather and tire age

## GitHub Repository
https://github.com/EmilieChtr/F1_notebook_project
