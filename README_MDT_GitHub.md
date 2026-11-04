# Predicting Flight Arrival Delays at Harrisburg International Airport (MDT)

**DATA 300 — Statistical & Machine Learning | Dickinson College | Spring 2026**

Team project by **Nam Nguyen, Leah Ho, and Gracie Nguyen**. See the final presentation for the team report. Individual contributions should be documented separately by each contributor.

## Project overview
Predict whether a flight departing MDT arrives **15 minutes or more late**, using U.S. Bureau of Transportation Statistics On-Time Performance data for 2020–2025. The cleaned dataset has **29,281 records** and an approximately **17.39%** positive rate.

## Methods
- Cleaning and exploratory analysis, including monthly, time-of-day, carrier, route, and previous-record delay patterns.
- Feature engineering: `DEP_HOUR`, `PREV_FLIGHT_DELAYED` (see limitations), and one-hot encodings of carrier and destination.
- Binary classification: Logistic Regression and Random Forest; precision, recall, F1, ROC-AUC, and threshold analysis.

## Results reported in the final presentation

| Model | Decision threshold | Precision | Recall | F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.4836 | 0.2417 | 0.6111 | 0.3463 |
| Random Forest | 0.4641 | 0.2743 | 0.5618 | 0.3686 |

These are **reported historical notebook results**, not independently revalidated metrics. The threshold was chosen using test labels; see `FLIGHT_PROJECT_FILE_REVIEW.md` before interpreting them as unbiased generalization estimates.

## Files
- `cleaned_flight_data_new.csv` — cleaned data used for the modeling stage.
- `fight_data_clean(3).ipynb` — cleaning and EDA; reproducing the cleaning step requires separate raw monthly BTS files.
- `LogisticRegression_final_portable.ipynb` — final LR notebook with a portable dataset path.
- `RandomForest_final_portable.ipynb` — final RF notebook with a portable dataset path.
- `DATA 300 - Flight delay ML (2).pdf` — final presentation.
- `FLIGHT_PROJECT_FILE_REVIEW.md` — detailed comparison, issues, and suggested next steps.

## Run the notebooks
Place the cleaned CSV beside both portable notebooks. Install appropriate versions of `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, and `imbalanced-learn`. Run cells in order. The Random Forest grid search can be computationally expensive. Saved results may differ across library versions and environments.

## Data source
U.S. Bureau of Transportation Statistics, Airline On-Time Performance Data. Original raw monthly files are not included. The cleaned data is a derived project dataset.

## Limitations
A single-airport dataset, class imbalance, omitted weather/congestion, possibly imperfect previous-flight feature, random rather than chronological splitting, and test-set threshold selection. Future work should add leakage-safe features, a validation set, and an independent time-based test set.
