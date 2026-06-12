# SpaceX Launch Success Prediction & Site Analysis

An end-to-end data science project that collects, processes, and models SpaceX launch data to predict mission success and identify optimal launch site characteristics. The project culminates in an interactive Plotly Dash dashboard for exploratory analysis.

---

## Project Overview

This project works through a complete data science pipeline — from raw data acquisition through machine learning modelling and interactive visualization. The central questions:

- What factors influence SpaceX launch success?
- Which launch sites show the highest success rates?
- Can launch outcome be reliably predicted from mission parameters?

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
| `Machine Learning Predictive.ipynb` | Classification models to predict launch success |
| `spacex_dash_app.py` | Interactive Plotly Dash web application |

---

## Interactive Dashboard

`spacex_dash_app.py` is a Plotly Dash app providing dynamic, filterable views of the launch dataset.

**Features:**
- Launch site dropdown — filter by individual site or all sites
- Pie chart — success rate breakdown per site
- Payload range slider — filter by payload mass (0–10,000 kg)
- Scatter plot — payload mass vs launch outcome, coloured by booster version
- All charts update dynamically via Dash callbacks

**Run locally:**

```bash
pip install pandas dash plotly
python spacex_dash_app.py
# Open http://127.0.0.1:8050
```

---

## Machine Learning

The predictive notebook trains and evaluates multiple classifiers on engineered launch features:

- Logistic Regression
- Decision Tree
- K-Nearest Neighbors
- Support Vector Machine (SVM)

Models are compared by accuracy, confusion matrix, and cross-validation score. GridSearchCV is used for hyperparameter tuning.

---

## Skills Demonstrated

| Area | Details |
|---|---|
| Data Collection | SpaceX REST API consumption, HTML web scraping (BeautifulSoup) |
| SQL | Analytical queries for EDA on structured launch records |
| Data Cleaning | Null handling, type normalisation, feature engineering with pandas/numpy |
| Exploratory Analysis | Statistical summaries, correlation analysis, matplotlib/seaborn visualizations |
| Geospatial Analysis | Launch site proximity and geographic feature extraction |
| Machine Learning | Binary classification, cross-validation, hyperparameter tuning (scikit-learn) |
| Interactive Visualization | Multi-component Dash app with live callbacks (Plotly/Dash) |

---

## Tech Stack

- **Language:** Python
- **Data:** pandas, numpy
- **Visualization:** matplotlib, seaborn, plotly
- **Dashboard:** Dash
- **Machine Learning:** scikit-learn
- **Data Access:** requests, BeautifulSoup, SQL
- **Environment:** Jupyter Notebooks

---

## Related

- **[acieral-kairos-bot](https://github.com/RDavidZ/acieral-kairos-bot)** — Production algorithmic trading system: XGBoost entry and exit models trained on 7+ years of multi-timeframe forex/index data, walk-forward validated, and running live on OANDA.
