# QSR POS Logs Analysis

A data analysis and ML notebook that explores Quick Service Restaurant (QSR) point-of-sale transaction logs to surface revenue optimization opportunities, build simple predictive models (combo upsell predictor and order value estimator), and produce business-facing dashboards.

This repository contains a single executed Jupyter notebook:
- notebook7008ceacdb.ipynb — end-to-end analysis: data loading, preprocessing, EDA, dashboarding, business insights, and ML modeling.

I reviewed the notebook and wrote this README to help you understand, reproduce, and extend the work.

## Highlights / Executive Summary (from the notebook)
- Dataset: QSR POS transaction logs (April–August 2025), 10 stores, ~30 menu items.
- Rows analyzed: 1,743 transactions
- Total revenue in dataset: $11,625.91
- Average order value: $6.71
- Key finding: Identified an estimated $4k–$5k/month revenue opportunity (primarily via combo upselling and modifier offers).
- Models used: RandomForestClassifier and RandomForestRegressor (combo prediction and order value estimation). The notebook reports very high classification accuracy for the combo predictor (notebook claims 100%).

> Note: The notebook includes full EDA, visual dashboard generation, feature engineering, and model training/evaluation. Review model evaluation cells carefully if you intend to use the models in production.

## Files
- notebook7008ceacdb.ipynb — main analysis notebook (contains everything: data loading, EDA, feature engineering, dashboards, insights, and ML models).

## Data
The notebook expects the dataset in the Kaggle input path used during development:
- /kaggle/input/qsr-pos-logs-hotel-menu-modifiers-and-dayparts-2025/
  - qsr_pos_logs.xlsx (also CSV/JSON/SQLite variants appear in the notebook environment)

If you want to run locally, place the dataset files into a folder and update the path referenced in the notebook (search for df = pd.read_excel(...)).

## Requirements
The notebook uses common data science libraries. Install locally using pip:

```bash
python -m pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyterlab
```

Optionally create a requirements.txt with the following (example):

```
pandas
numpy
matplotlib
seaborn
scikit-learn
openpyxl
jupyterlab
```

## How to run

Option A — Run on Kaggle (recommended, since the notebook uses Kaggle input paths)
1. Upload the dataset to a Kaggle dataset or use the original Kaggle dataset referenced in the notebook.
2. Open the notebook in a Kaggle kernel (the data path will already match).
3. Run cells top-to-bottom.

Option B — Run locally
1. Clone this repo:
   ```bash
   git clone https://github.com/shahan24h/qrs_pos_logs_analysis.git
   cd qrs_pos_logs_analysis
   ```
2. Install required packages (see Requirements).
3. Edit the data-loading cell in notebook7008ceacdb.ipynb to point to your local dataset path (e.g., `data/qsr_pos_logs.xlsx`).
4. Start Jupyter and open the notebook:
   ```bash
   jupyter lab
   # or
   jupyter notebook
   ```
5. Run all cells.

## Notebook structure (high level)
1. Setup & imports — pandas, numpy, matplotlib, seaborn, sklearn, etc.
2. Data loading — reads the Excel (and prints available files in /kaggle/input).
3. Dataset overview — summary stats, missing values, sample rows.
4. Preprocessing & feature engineering — datetime parsing, hour/day/month features, is_combo, modifiers, price categories, label encoding.
5. EDA & Dashboard — revenue by store, revenue by daypart, hourly patterns, top menu items, combo vs individual comparison, daily revenue trend, etc.
6. Key business insights — store and product-level insights, modifier usage, combo uplift analysis.
7. ML Modeling — Random Forest models for combo prediction and order value estimation; evaluation metrics and demonstrations.
8. Actionable recommendations — suggested upsell strategies and next steps.

## Key cells & search terms
- Data loading: look for `pd.read_excel('/kaggle/input/.../qsr_pos_logs.xlsx')`
- Feature engineering: look for `is_combo`, `hour_category`, `price_category`
- Models: `RandomForestClassifier` and `RandomForestRegressor`
- Dashboard: plotting code that creates a 3x3 figure of analytics

## Reproducing the ML experiments
- The notebook uses sklearn's RandomForest implementations and standard metrics (accuracy_score, MAE, MSE, R^2).
- To reproduce, ensure deterministic behavior by setting random_state in model constructors and numpy random seed where appropriate.
- Inspect train/test split and cross-validation cells to validate the reported metrics.

## Suggested next steps / improvements
- Add a requirements.txt and/or environment.yml for reproducible environments.
- Add a small data loader utility or configuration cell so the notebook can find the dataset without manual edits.
- Add model persistence (joblib) and a minimal inference script or dashboard (Streamlit/Flask) for interactive upsell suggestions.
- Validate the ML model claims (100% accuracy is unusual) by reviewing train/test splits, leakage, and class balance.
- Add tests for preprocessing steps and a CI workflow to run static checks on the notebook (nbval or papermill for automated runs).
- Consider adding a LICENSE file if you want to publish this work with explicit reuse terms.

## Contributing
If you'd like help improving this repository (packaging, reproducibility, model validation, or converting the notebook into modular scripts), open an issue or submit a PR. Describe the change, include reproducible steps, and reference the notebook sections affected.

## License
No LICENSE file was found in the repository during my review. If you want others to reuse or contribute, please add an explicit license (e.g., MIT, Apache-2.0).

---

If you want, I can:
- Draft a requirements.txt based on the notebook imports.
- Convert key notebook sections to modular Python scripts (data preprocessing, EDA, modeling) and add a simple CLI.
- Create a concise one-page executive summary (PDF or Markdown) extracted directly from the notebook outputs.

Tell me which of the above you'd like next and I'll prepare the files.