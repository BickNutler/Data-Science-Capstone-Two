# Adult Census Income Prediction  
**Springboard Data Science Capstone Two**

## Overview
This project builds and evaluates machine learning models to predict whether an individual earns **more than $50,000 per year** using the UCI Adult Census Income dataset. The repository is structured for **end-to-end reproducibility**, with each intermediate artifact generated explicitly by running the notebooks in order.

---

## Key Deliverables
- **Final report:** `Final_Report.pdf`  
- **Executive slide deck:** `Executive_Slide_Deck.pptx`  
- **Full model metrics table (reproducible):** `final_model_metrics_full.csv`

---

## Data Lineage (What Creates What)
This project follows a strict pipeline. All derived files are produced by executing the notebooks below.

1. **Raw data → Cleaned dataset**  
   - Notebook: `01_Data_Wrangling.ipynb`  
   - Inputs: `raw_data/adult.data`, `raw_data/adult.test`  
   - Output: `adult_combined_cleaned.csv`

2. **Cleaned dataset → Encoded feature sets**  
   - Notebook: `02_EDA.ipynb`  
   - Input: `adult_combined_cleaned.csv`  
   - Outputs: `df_encoded_part1.csv`, `df_encoded_part2.csv`

3. **Encoded features → Train/Test datasets (8 preprocessing configurations)**  
   - Notebook: `03_Preprocessing_and_Train_Test_Build.ipynb`  
   - Inputs: `df_encoded_part1.csv`, `df_encoded_part2.csv`  
   - Output folder: `Binned_Test_Train_Data/`

4. **Train/Test datasets → Modeling + evaluation artifacts**  
   - Notebook: `04_Modelling.ipynb`  
   - Inputs: files from `Binned_Test_Train_Data/`  
   - Outputs:
     - `final_model_metrics_full.csv` (written by the notebook)
     - Figures for README: `reports/figures/`

---

## Modeling Approach
- Models evaluated:
  - **XGBoost**
  - **LightGBM**
- Hyperparameter tuning:
  - **Optuna** (Bayesian optimization)
- Metrics reported:
  - ROC AUC, Accuracy, Precision, Recall, F1, Log Loss, Average Precision
- Evaluation performed across **eight preprocessing / binning configurations**.

---

## Results Highlights
### ROC Curves for Top Models
![ROC Curves](reports/figures/roc_curves_top8.png)

### Precision–Recall Curves for Top Models
![Precision–Recall Curves](reports/figures/pr_curves_top8.png)

### Best ROC AUC by Binning Strategy and Model Type
![Best AUC by Strategy](reports/figures/best_auc_by_strategy.png)

---

## Repository Structure
```text
.
├── 01_Data_Wrangling.ipynb
├── 02_EDA.ipynb
├── 03_Preprocessing_and_Train_Test_Build.ipynb
├── 04_Modelling.ipynb
│
├── adult_combined_cleaned.csv
├── df_encoded_part1.csv
├── df_encoded_part2.csv
├── final_model_metrics_full.csv
│
├── Binned_Test_Train_Data/
│   ├── X_train_*.csv
│   ├── X_test_*.csv
│   ├── y_train.csv
│   └── y_test.csv
│
├── raw_data/
│   ├── adult.data
│   ├── adult.test
│   ├── adult.names
│   └── old.adult.names
│
├── reports/
│   └── figures/
│       ├── roc_curves_top8.png
│       ├── pr_curves_top8.png
│       ├── best_auc_by_strategy.png
│       └── roc_auc_distribution.png
│
├── Adult_Census_Income_Project_Proposal.pdf
├── Final_Report.pdf
├── Executive_Slide_Deck.pptx
├── requirements.txt
└── README.md
```

---

## How to Run (Reproduce Everything)
1. Create an environment and install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run notebooks in order:
   1. `01_Data_Wrangling.ipynb`
   2. `02_EDA.ipynb`
   3. `03_Preprocessing_and_Train_Test_Build.ipynb`
   4. `04_Modelling.ipynb`

Running the full sequence will regenerate **all intermediate CSVs** and will reproduce `final_model_metrics_full.csv`.

---

## Author
**Nicholas Butler**  
Springboard Data Science Career Track
