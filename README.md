# Weather Summary Classification

## 📌 Project Overview
This project develops a robust multi-class classification machine learning model to predict the **Daily Summary** of weather conditions. By analyzing various meteorological parameters, this model aims to improve forecasting automation, which can aid decision-making in agriculture, transport, and disaster management.

## 📊 Dataset
* **Source:** Szeged, Hungary Weather History (2006–2016)
* **Size:** 96,453 hourly observations and 12 original columns.
* **Target Variable:** `Daily Summary` (Multi-class).
* **Imbalance Handling:** The dataset is heavily imbalanced. Rare classes (< 50 samples) were removed, and the **SMOTE** (Synthetic Minority Over-sampling Technique) algorithm was applied to balance the training distribution.

## 🛠️ Data Preprocessing & Feature Engineering
* **Missing Values:** Median imputation for numerical features; missing `Precip Type` filled as "none".
* **Data Leakage Prevention:** Dropped the `Summary` column to prevent target leakage. 
* **Feature Engineering:**
  * `Temp_Diff`: Difference between Apparent Temperature and Actual Temperature (captures wind chill/humidity effects).
  * `Wind_Humidity`: Product of Wind Speed and Humidity (proxy for precipitation intensity and comfort index).
* **Scaling:** Applied `StandardScaler` to all numerical features.

## 🤖 Modeling & Evaluation
Seven classification algorithms were trained and evaluated on a held-out test set (20%). Tree-based ensemble models showed the best performance.

| Algorithm | Accuracy | Precision | Recall | F1 Score |
| :--- | :--- | :--- | :--- | :--- |
| **Random Forest (Best)** | **~88–91%** | **~87–90%** | **~88–91%** | **~87–90%** |
| Gradient Boosting | ~85–88% | ~84–88% | ~85–88% | ~84–88% |
| SVM (RBF Kernel) | ~82–85% | ~81–84% | ~82–85% | ~81–84% |
| K-Nearest Neighbors | ~78–82% | ~77–81% | ~78–82% | ~77–81% |
| Logistic Regression | ~72–76% | ~71–76% | ~72–76% | ~71–75% |

### Key Findings
* **Top Predictors:** `Temperature (C)`, `Apparent Temperature (C)`, and the engineered `Temp_Diff` were the most significant features for predicting weather summaries.
* **Hyperparameter Tuning:** GridSearchCV revealed that a deeper tree (`max_depth=None`) with more estimators (`n_estimators=200`) maximized Random Forest performance.

## 🚀 Future Scope
* Sequence modeling using deep learning architectures like LSTMs or Transformers.
* Deployment of the best model as a REST API for real-time classification.
* Development of a Power BI dashboard to visually monitor predictions.

---
*Course: B.Tech CSE – Data Science (4th Semester)*  
*Institution: Ganga Institute of Technology & Management, Kablana*
