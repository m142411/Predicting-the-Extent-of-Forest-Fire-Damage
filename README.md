#  Predicting the Extent of Forest Fire Damage

##  Project Overview

This project aims to build an advanced **Regression Model** to accurately predict the burned area (`area`) resulting from forest fires. The model utilizes meteorological data, Fire Weather Index (FWI) components, and geographic location to assess potential damage. The project's main focus was overcoming significant data challenges, particularly the severe data imbalance, to ensure the model could accurately predict large, high-impact fire events.

---

##  Methodology and Objectives

### **Core Challenges**
* **Severe Data Imbalance:** The vast majority of data points recorded an `area` close to zero. This imbalance caused initial models to achieve deceptively good RMSE scores by simply predicting very small values.
* **Skewness:** The target variable (`area`) was highly skewed, necessitating immediate transformation.

### **Key Strategies Implemented**

| Step | Technique | Rationale |
| :--- | :--- | :--- |
| **1. Skewness Treatment** | **Log Transformation** (`np.log1p`) | Applied to the `area` variable to normalize its distribution and stabilize model training. |
| **2. Feature Engineering** | One-Hot Encoding | Applied to categorical features (`month`, `X`, `Y`) to prepare them for the model. |
| **3. Imbalance Correction** | **Oversampling** | The most critical step. Artificially increased the representation of rare, large-fire events to force the model to learn their patterns. |
| **4. Final Model** | **XGBoost Regressor** | Selected for its proven power and flexibility in handling complex, non-linear regression problems. |

---

##  Final Results

The oversampling strategy proved to be the project's turning point, leading to a dramatic improvement in performance.

* **Quantitative Improvement (RMSE):**
    * The final **RMSE on the test set dropped to 3.765**, a massive reduction compared to the initial models.
* **Qualitative Success:**
    * The model's behavior fundamentally changed. It is no longer "playing it safe" and is now successfully predicting **significant, non-zero fire areas**.
    * The model exhibits a slight tendency to **overestimate** the damage, which is a desirable trait in a risk-assessment tool, prioritizing caution over underestimation.

---

## 📁 Project Structure
EstimatingDamageFromForestFire/
├── dataset_ForestFire/              
│   ├── forestfires.csv               
│   └── forestfires.names.txt         
├── figure/                          
├── Forest_Fire_Prediction_Model.ipynb 
└── requirements.txt                  
