<div align="center">

# 🛡️ Cybersecurity Network Traffic Analysis

### A CRISP-DM machine-learning study of network sessions

Explore network traffic, build attack-detection classifiers, and estimate session duration with supervised learning.

[![Python](https://img.shields.io/badge/Python-Jupyter%20Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Framework](https://img.shields.io/badge/Methodology-CRISP--DM-2563EB)](#-methodology)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## Project overview

This academic project applies the **CRISP-DM** process to a cybersecurity network-traffic dataset. It uses exploratory analysis and machine-learning models to investigate two tasks:

- **Classification:** predict whether a session is an `Attack` or `Benign` (`is_attack`).
- **Regression:** estimate session duration (`session_duration`) to explore its potential use in investigation prioritisation.

The dataset is described in the project as synthetic and contains 6,000 sessions. This is an educational analysis; model predictions are not a substitute for security monitoring or analyst review.

## Methodology

The notebook follows the main CRISP-DM stages:

1. **Business understanding** — frame attack detection and session-duration prediction as analysis goals.
2. **Data understanding** — inspect distributions, missing values, class balance, correlations, and protocol values.
3. **Data preparation** — normalize protocol labels, impute missing data, retain potentially meaningful outliers, engineer features, encode categories, scale numeric inputs, and split data for evaluation.
4. **Modeling** — train and compare classification and regression models.
5. **Evaluation** — assess models with classification metrics, cross-validation, confusion matrices, ROC curves, and regression metrics.
6. **Deployment / next steps** — consider how findings could inform further investigation; this repository does not provide a production deployment pipeline.

### Feature engineering

The notebook adds two domain-motivated features:

- `bytes_ratio` — sent bytes relative to received bytes.
- `failed_login_rate` — failed logins relative to login attempts.

### Models explored

| Task | Models | Evaluation examples |
| --- | --- | --- |
| Attack classification | Decision Tree, Complement Naïve Bayes, K-Nearest Neighbors, Random Forest | Accuracy, precision, recall, F1, ROC-AUC, confusion matrix, stratified cross-validation |
| Session-duration regression | Linear Regression, Ridge Regression | RMSE, MAE, R², residual analysis |

Recall receives particular attention in the classification task because missed attacks may be more costly than false alarms. Threshold changes also affect the precision/recall trade-off and should be assessed against the intended use case.

## Repository contents

```text
.
├── COMP_H2706_Full_Project_Code.ipynb  # End-to-end analysis and visualizations
├── Dataset1_even_students.csv          # Dataset used by the notebook
├── LICENSE
└── README.md
```

## Getting started

### Requirements

Python 3 with Jupyter Notebook or JupyterLab, plus the packages imported by the notebook:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

Install the dependencies with:

```bash
python -m pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Run the notebook

1. Clone or download this repository.
2. Keep `Dataset1_even_students.csv` in the same directory as the notebook.
3. Start Jupyter from the repository directory:

   ```bash
   jupyter notebook
   ```

4. Open `COMP_H2706_Full_Project_Code.ipynb` and run the cells from top to bottom.

The notebook reads the dataset using the relative filename `Dataset1_even_students.csv`. It includes data exploration, preprocessing, model training, visualizations, and results summaries. You can also [view the notebook on GitHub](COMP_H2706_Full_Project_Code.ipynb).

## Interpretation and limitations

- This is an academic, dataset-specific experiment—not a validated operational intrusion-detection system.
- Synthetic or curated data may not represent the diversity and drift of real network traffic.
- Results depend on preprocessing, split strategy, class balance, model settings, and decision thresholds. Validate any conclusions on appropriate independent data before practical use.
- A high recall can come with more false positives; select thresholds with the costs of both error types in mind.
- Do not use the notebook's predictions alone to block traffic or make incident-response decisions.

## Project context

Created for **Fundamentals of AI & Data Science (COMPH2706)** at **TU Dublin**.

## License

This project is distributed under the [MIT License](LICENSE).
