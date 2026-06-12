# SpaceX Launch Success Prediction & Site Analysis

An end-to-end data science project that collects, processes, and models SpaceX launch data to predict first-stage landing success and identify what drives it. The project covers the full pipeline from API data collection and SQL exploration through classification modelling and an interactive Plotly Dash dashboard.

---

## Key Results

| Model | Validation Accuracy | Test Accuracy |
|---|---|---|
| Decision Tree | **88.75%** | 83.33% |
| SVM | 84.82% | 83.33% |
| Logistic Regression | 84.64% | 83.33% |

All three models converged to **83.33% test accuracy**. The Decision Tree was selected as the best model based on highest validation accuracy (88.75%) with GridSearchCV best params: `criterion=entropy`, `max_depth=12`, `min_samples_split=10`.

**Key findings:**
- KSC LC-39A and VAFB SLC-4E had the highest landing success rates at **77%** each; CCAFS LC-40 was lowest at **60%**
- Higher flight numbers correlate with higher landing success — iterative hardware improvements are visible in the data
- Heavier payloads reduce landing success probability (more fuel consumed during ascent leaves less for the return burn)
- Reusable first-stage recovery cuts launch cost from ~$165M (competitors) to ~$62M

---

## Pipeline

```
Data Collection (API + Scraping)
        |
  Data Wrangling
        |
  EDA — SQL + Visualization
        |
  Launch Site Location Analysis
        |
  Machine Learning (Classification)
        |
  Interactive Dash Dashboard
```

---

## Project Structure

| File | Description |
|---|---|
| `Data Collection.ipynb` | Fetches SpaceX launch records via REST API |
| `Webscraping.ipynb` | Scrapes supplementary launch data from Wikipedia |
| `Data Wrangling.ipynb` | Cleaning, type normalisation, feature preparation |
| `EDA with SQL.ipynb` | Exploratory analysis using SQL queries |
| `EDA Data Visualization.ipynb` | Visual EDA — distributions, correlations, trends |
| `Launch Site Location.ipynb` | Geospatial analysis of launch site characteristics |
| `Machine Learning Predictive.ipynb` | Classification models to predict landing success |
| `spacex_dash_app.py` | Interactive Plotly Dash web application |

---

## Interactive Dashboard

`spacex_dash_app.py` is a Plotly Dash app for interactive exploration of the launch dataset.

**Features:**
- Launch site dropdown — filter by individual site or all sites
- Pie chart — success rate breakdown per site
- Payload range slider — 0–10,000 kg in 1,000 kg increments
- Scatter plot — payload mass vs landing outcome, coloured by booster version
- All charts update dynamically via Dash callbacks

**Run locally:**

```bash
pip install pandas dash plotly
python spacex_dash_app.py
# Open http://127.0.0.1:8050
```

---

## Machine Learning Detail

**Classifiers evaluated:** Logistic Regression, SVM, Decision Tree  
**Tuning:** GridSearchCV with cross-validation on each model  
**Evaluation:** Accuracy, confusion matrix, Jaccard score

Best SVM params: `kernel=sigmoid`, `C=1.0`, `gamma=0.032`  
Best Logistic Regression params: `C=0.01`, `penalty=l2`, `solver=lbfgs`

All three models plateau at 83.33% test accuracy, suggesting the ceiling is driven by dataset size (~100 labelled outcomes) rather than model choice.

---

## EDA Highlights (SQL)

- 4 distinct launch sites identified
- NASA CRS missions: 45,596 kg total payload across all flights
- F9 v1.0 average payload: 340.4 kg — significantly lighter than later variants
- 14 booster drone ship recoveries with payload masses between 4,000–6,000 kg
- Successful ground pad landings began May 2017

---

## Skills Demonstrated

| Area | Details |
|---|---|
| Data Collection | SpaceX REST API, HTML web scraping (BeautifulSoup) |
| SQL | Aggregation, filtering, and join queries for EDA |
| Data Cleaning | Null handling, type normalisation, feature engineering |
| Exploratory Analysis | Statistical summaries, correlation analysis, matplotlib/seaborn |
| Geospatial Analysis | Launch site proximity and geographic feature extraction |
| Machine Learning | Binary classification, GridSearchCV, cross-validation (scikit-learn) |
| Interactive Visualization | Multi-component Dash app with live callbacks (Plotly/Dash) |

---

## Tech Stack

- **Language:** Python
- **Data:** pandas, numpy
- **Visualization:** matplotlib, seaborn, plotly
- **Dashboard:** Dash
- **Machine Learning:** scikit-learn
- **Data Access:** requests, BeautifulSoup, SQL (sqlite3)
- **Environment:** Jupyter Notebooks

---

## Related

- **[acieral-kairos-bot](https://github.com/RDavidZ/acieral-kairos-bot)** — Production algorithmic trading system: XGBoost entry and exit models trained on 7+ years of multi-timeframe forex/index data, walk-forward validated, and running live on OANDA.
