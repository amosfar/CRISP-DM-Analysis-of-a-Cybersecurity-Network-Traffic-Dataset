# CRISP-DM-Analysis-of-a-Cybersecurity-Network-Traffic-Dataset
# CRISP-DM Analysis of Cybersecurity Network-Traffic Data

An individual data mining and machine learning project built for the **Fundamentals of AI & Data Science (COMPH2706)** module at TU Dublin[cite: 3].

## 📌 Project Overview
This project applies the **CRISP-DM** framework to a synthetic cybersecurity network-traffic dataset containing 6,000 sessions and 19 features[cite: 3]. The objective is to assist a targeted financial organisation through two analytical goals[cite: 3]:
1. **Classification:** Predicting whether a network session is an attack (`is_attack`) to enable early, automated threat detection[cite: 3].
2. **Regression:** Predicting session duration (`session_duration`) as a proxy for attacker persistence to prioritize incident response triage[cite: 3].

---

## 📂 Dataset & Preprocessing Pipeline
* **Dataset Size:** 6,000 network sessions, 19 features, and 2 target variables[cite: 3].
* **Class Imbalance:** 74.7% Benign sessions vs. 25.3% Attack sessions[cite: 3].
* **Data Cleaning & Preprocessing:**
  * **Protocol Normalization:** Resolved mixed-case inconsistencies (e.g., `"tcp"` to `"TCP"`, `"Udp"` to `"UDP"`)[cite: 3].
  * **Imputation:** Applied mode imputation for categorical missing values and median imputation for numeric attributes (robust to skewed data)[cite: 3].
  * **Outlier Handling:** Retained extreme values as critical behavioral indicators rather than treating them as noise[cite: 3].
  * **Feature Engineering:** Constructed domain-informed attributes (`bytes_ratio` and `failed_login_rate`) to capture advanced threat signals[cite: 3].
  * **Scaling & Splitting:** Performed an 80/20 stratified split prior to resampling, utilizing `StandardScaler` and `MinMaxScaler` appropriately for different algorithms[cite: 3].

---

## 🤖 Modeling & Evaluation

### Classification Models
Evaluated multiple eager and lazy learning algorithms using an 80/20 train-test split and 5-fold stratified cross-validation[cite: 3]:
* **Decision Tree (Baseline & Enhanced):** The simple depth=3 baseline achieved the highest F1 score (0.459) and AUC (0.671) while remaining fully interpretable via IF-THEN rules[cite: 3].
* **Naïve Bayes (ComplementNB):** Utilized Laplace smoothing ($\alpha = 1$) to handle missing attribute-class probabilities[cite: 3].
* **K-Nearest Neighbors (KNN):** Tuned $k=3$ via the Elbow Method, testing both Manhattan and Euclidean distance metrics[cite: 3].
* **Random Forest & Threshold Tuning:** Demonstrated the danger of relying on accuracy with imbalanced data; lowered the default decision threshold from $t=0.50$ to $t=0.20$ to dramatically boost recall from $2.3\%$ to $82.9\%$ for critical security triage[cite: 3].

### Regression Models
* **Linear & Ridge Regression ($\alpha = 10$):** Attempted to predict session duration, yielding an $R^2$ of 0.462 and an RMSE of 12.22 minutes, indicating that session duration is moderately predictable from network metrics alone[cite: 3].

---

## 🚀 Code & Notebook Reference
The complete Python code, data preprocessing pipeline, classification/regression models, and visualizations are available in the Google Colab notebook[cite: 3]:
* 👉 [Google Colab Notebook Link](https://colai.research.google.com/drive/17vjSrPGQlT7Nwu-zkFWlNHBsDfdB_eLh?usp=sharing)[cite: 3]
* *Note: Ensure `Dataset1_even_students.csv` is placed in the working directory before execution.*[cite: 3]

---

## 👤 Author
* **Amos Farcau** (Student ID: B00169532)[cite: 3]
* **Module:** Fundamentals of AI & Data Science (COMPH2706) – TU Dublin[cite: 3]
