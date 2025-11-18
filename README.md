# QSR POS Logs Analysis

This repository contains my end-to-end analysis of Quick Service Restaurant (QSR) point-of-sale transaction logs. I used exploratory data analysis, feature engineering, visual dashboards, and simple machine learning models to surface revenue-opportunity insights (notably combo upsells and modifier offers).

Files
- notebook7008ceacdb.ipynb — the full, executed Jupyter notebook with data loading, EDA, dashboarding, feature engineering, model training, evaluation, and recommendations.
- README.md — this file.

Executive summary
- Dataset: QSR POS transaction logs (Apr–Aug 2025), 10 stores, ~30 menu items.
- Transactions analyzed: 1,743
- Total revenue (dataset): $11,625.91
- Average order value: $6.71
- Key finding: I estimate a $4k–$5k/month revenue opportunity from upselling (combos & modifiers).
- Modeling: I trained RandomForest models for combo prediction and order-value estimation (see notebook for details and evaluation).

Requirements
I used standard Python data-science packages. To run locally, I recommend:

pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyterlab

(You can drop these into a requirements.txt if you prefer.)

Data
During development I used the Kaggle dataset path:
/kaggle/input/qsr-pos-logs-hotel-menu-modifiers-and-dayparts-2025/
The notebook loads qsr_pos_logs.xlsx by default. To run locally, place the dataset in a folder and update the data-loading cell (search for pd.read_excel(...)).

How I organized the notebook
1. Setup & imports  
2. Data loading & initial exploration (shape, dtypes, missing values)  
3. Preprocessing & feature engineering (datetime features, is_combo, price & hour categories, encodings)  
4. EDA & dashboard (revenue by store/daypart, hourly patterns, top items, combo vs individual, daily trend)  
5. Key business insights (combo uplift, modifier usage, peak hours/stores)  
6. ML models (RandomForest for combo prediction and order-value estimation)  
7. Recommendations & next steps

Reproducibility notes
- Set random_state for deterministic model results if you plan to reproduce the experiments.
- Verify train/test splits and check for data leakage before using models in production (the notebook reports high accuracy; please validate).

Suggested next steps (what I would do next)
- Add requirements.txt or environment.yml for reproducibility.  
- Add a LICENSE (e.g., MIT) if I want to share this publicly.  
- Extract preprocessing and modeling into modular scripts and persist trained models with joblib.  
- Build a lightweight Streamlit/Flask demo for interactive upsell suggestions.  
- Add automated notebook runs (papermill/nbval) in CI to ensure reproducibility.

Contributing
If you want me to convert notebook sections to scripts, add a requirements.txt, create a LICENSE, or wire up CI, tell me which and I’ll prepare the changes and push them to the repo.

License
None included currently — please add a license if you want to specify reuse terms.