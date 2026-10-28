# Lung Cancer Survival Prediction

This project explores lung-cancer patient data and builds a machine-learning model to estimate the probability that a patient survives. It includes data cleaning, exploratory data analysis, model comparison, and a simple Tkinter desktop GUI for making predictions.

> **Important:** This project is for educational and demonstration purposes only. The predictions are not medical advice, are not clinically validated, and must not be used to diagnose or treat patients.

## Project contents

```text
.
├── data/
│   ├── lung_cancer_dataset.csv
│   ├── lung_cancer_dataset_cleaned.csv
│   └── best_survival_model.joblib
└── notebooks/
    ├── Data_cleaning.ipynb
    ├── EDA.ipynb
    ├── Model_building.ipynb
    └── GUI.ipynb
```

### Data

- `lung_cancer_dataset.csv` is the original dataset.
- `lung_cancer_dataset_cleaned.csv` contains the transformed features used for modelling.
- `best_survival_model.joblib` contains the trained model pipeline and the metadata required by the GUI.

The dataset contains demographic, lifestyle, clinical, diagnostic, treatment, and survival-related variables. The target variable is `Survived`.

## Workflow

1. `Data_cleaning.ipynb` cleans text and date fields, converts binary values to `0`/`1`, encodes selected categorical variables, removes excluded features, and saves the cleaned dataset.
2. `EDA.ipynb` summarizes the data, checks missing values, and explores relationships between features and survival.
3. `Model_building.ipynb` prepares the features, compares baseline, logistic regression, random forest, and gradient boosting models, evaluates them with holdout and cross-validation metrics, and saves the selected pipeline to `data/best_survival_model.joblib`.
4. `GUI.ipynb` loads the saved model and opens a Tkinter interface for entering patient information and displaying an estimated survival probability.

## Requirements

Python 3.10 or newer is recommended. Install the main dependencies with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn joblib jupyter openpyxl
```

Tkinter is also required to run the GUI. It is included with most standard Python installations. On some Linux systems, install it through the operating system package manager, for example `python3-tk`.

## Running the project

From the project root, start Jupyter:

```bash
jupyter notebook
```

Open the notebooks in the following order if you want to reproduce the workflow:

1. `notebooks/Data_cleaning.ipynb`
2. `notebooks/EDA.ipynb`
3. `notebooks/Model_building.ipynb`
4. `notebooks/GUI.ipynb`

The model-building notebook should be run before the GUI if `data/best_survival_model.joblib` does not already exist. Run the GUI notebook from the `notebooks` directory, or use its path-handling fallback when running from the project root.

## Model output

The saved `.joblib` file includes:

- the fitted preprocessing and prediction pipeline;
- the selected model name;
- the expected input columns;
- numeric and categorical feature metadata; and
- cross-validation results.

The current bundled model is a Random Forest pipeline with 31 expected input columns.

## Notes and limitations

- Model performance depends on the supplied dataset and may not generalize to real clinical populations.
- The dataset and model should not be interpreted as clinically validated evidence.
- The GUI provides an estimate, not a diagnosis or prognosis from a medical professional.
- Re-running the cleaning or model notebooks may overwrite the cleaned dataset or saved model artifact.

