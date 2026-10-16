# TB Risk Prediction Using Machine Learning

## 📌 Project Overview

Tuberculosis (TB) is a major public health concern, and early identification of individuals at risk can support timely screening and intervention.

This project develops a **machine learning-based TB risk prediction system** using two different healthcare datasets. The datasets are analyzed **independently** to compare the performance of multiple machine learning algorithms.

The project focuses particularly on **Recall**, because in a TB screening scenario, identifying suspected TB cases is important and missing a potential case can be undesirable.

The project also includes:
- Model comparison
- Best-model selection
- Hyperparameter tuning
- Decision-threshold analysis
- Model evaluation using multiple performance metrics
- SHAP-based explainability

---

# 🎯 Objectives

The main objectives of this project are:

1. To understand and preprocess healthcare datasets related to TB risk.
2. To compare multiple machine learning classification algorithms.
3. To select the best-performing model based on **Recall**.
4. To improve the selected model through tuning and threshold analysis.
5. To evaluate model performance using Accuracy, Precision, Recall, F1-Score and ROC-AUC.
6. To provide model interpretability using SHAP.
7. To compare the predictive performance obtained from the two datasets.

---

# 📊 Datasets

Two datasets are used in this project.

## Dataset 1

Dataset 1 contains healthcare-related features used for TB risk classification.

The target variable represents whether an individual belongs to the TB-positive or non-TB class.

The dataset is processed independently and used to train and evaluate multiple machine learning models.

### Final Best Model

**Random Forest**

### Final Performance

| Metric | Score |
|---|---:|
| Accuracy | 94.74% |
| Precision | 92.74% |
| Recall | 97.46% |
| F1-Score | 95.04% |
| ROC-AUC | 98.65% |

---

## Dataset 2

Dataset 2 contains **1,794 records and 11 columns**.

Important features include:

- `age_group`
- `hiv_pos`
- `diabetes`
- `ever_smoke`
- `past_tb`
- `male`
- `hs_less`
- `two_weeks_symp`
- `num_symptoms`
- `country`

The target variable is:

- `tb`

Dataset 2 contains a categorical age-group feature, seven binary indicators, a symptom-count feature and country information.

### Target Distribution

| TB Class | Records | Percentage |
|---|---:|---:|
| Not Suspected | 986 | 54.96% |
| TB Suspected | 808 | 45.04% |

---

# 🔄 Project Workflow

The overall workflow is:

```text
Dataset
   ↓
Data Understanding
   ↓
Feature & Target Separation
   ↓
Data Preprocessing
   ↓
Categorical Feature Encoding
   ↓
Train-Test Split
   ↓
Machine Learning Model Training
   ↓
Model Comparison
   ↓
Best Model Selection
   ↓
Hyperparameter Tuning
   ↓
Threshold Analysis
   ↓
Final Model Evaluation
   ↓
Explainability using SHAP
   ↓
Dataset Comparison
   ↓
Conclusion



🧹 Data Preprocessing
The datasets were processed separately.
The preprocessing workflow includes:
- Checking dataset structure
- Checking missing values
- Understanding feature types
- Separating features and target
- Encoding categorical variables
- Splitting the data into training and testing sets
For Dataset 2, categorical features such as age_group and country were encoded before model training.
🤖 Machine Learning Models
Multiple classification algorithms were evaluated.
The models include:
- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost
- AdaBoost
- Gaussian Naive Bayes
- Neural Network / MLP
The models were compared using:
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
⭐ Model Selection Strategy
Since this is a TB screening-oriented prediction problem, Recall was given particular importance.
Recall measures the proportion of actual TB-suspected cases that are correctly identified by the model.
Therefore, the model with the strongest Recall was selected as the preferred model during baseline comparison.
Selected Models
Dataset	Selected Model
Dataset 1	Random Forest
Dataset 2	XGBoost


📈 Dataset 1 — Model Comparison
The machine learning models were compared using multiple evaluation metrics.
Random Forest achieved the strongest overall performance and was selected as the final Dataset 1 model.
Final Dataset 1 Model
Random Forest
Performance
- Accuracy: 94.74%
- Precision: 92.74%
- Recall: 97.46%
- F1-Score: 95.04%
- ROC-AUC: 98.65%
The high Recall indicates that the model identified a large proportion of the TB-suspected cases in the test set.
📈 Dataset 2 — Model Comparison
Seven machine learning models were evaluated on Dataset 2.
The baseline comparison identified XGBoost as the preferred model based on Recall.
Baseline XGBoost Performance
- Accuracy: 73.54%
- Precision: 71.61%
- Recall: 68.52%
- F1-Score: 70.03%
- ROC-AUC: 80.16%
Although AdaBoost achieved higher Accuracy, Precision and F1-Score, XGBoost was selected because Recall was the primary selection criterion.
⚙️ Dataset 2 — XGBoost Improvement
After selecting XGBoost, further improvement was explored using:
1. Hyperparameter tuning
2. Decision-threshold analysis
The purpose of threshold analysis was to study how changing the classification threshold affects the balance between Precision and Recall.
🎚️ Threshold Analysis
Different decision thresholds were evaluated.
Threshold	Accuracy	Precision	Recall	F1-Score
0.50	76.32%	75.50%	70.37%	72.84%
0.45	74.37%	71.88%	70.99%	71.43%
0.40	72.42%	67.80%	74.07%	70.80%
0.35	70.19%	63.82%	78.40%	70.36%
0.30	68.80%	61.57%	82.10%	70.37%


A threshold of 0.40 was retained as the final threshold because it provided an improved Recall while maintaining a practical Precision-Recall trade-off.
🏆 Final Dataset 2 Model
Tuned XGBoost
Final threshold:
0.40
Final Performance
Metric	Score
Accuracy	72.42%
Precision	67.80%
Recall	74.07%
F1-Score	70.80%
ROC-AUC	80.57%


Note: The baseline XGBoost ROC-AUC was 80.16%, while the final tuned XGBoost ROC-AUC is 80.57%.

🔍 Model Explainability — SHAP
SHAP (SHapley Additive exPlanations) was incorporated to improve the interpretability of machine learning predictions.
SHAP helps explain how individual features contribute to a particular prediction.
The project uses SHAP for patient-level prediction explanation in Dataset 1.
Conceptually:
Patient Features
       ↓
Machine Learning Model
       ↓
TB Risk Prediction
       ↓
SHAP Explanation
       ↓
Feature Contribution

SHAP is used as an explainability component and is not treated as an additional performance metric.
📊 Dataset 1 vs Dataset 2
Metric	Dataset 1	Dataset 2
Final Model	Random Forest	Tuned XGBoost
Accuracy	94.74%	72.42%
Precision	92.74%	67.80%
Recall	97.46%	74.07%
F1-Score	95.04%	70.80%
ROC-AUC	98.65%	80.57%


Key Observation
Dataset 1 achieved stronger predictive performance across the evaluated metrics.
Dataset 2 showed moderate performance, but its Recall was improved through XGBoost tuning and decision-threshold analysis.
The two datasets were evaluated independently and were not merged, so their performance should be interpreted within their respective dataset characteristics.
📌 Key Findings
Dataset 1
- Random Forest was selected as the final model.
- It achieved a Recall of 97.46%.
- ROC-AUC reached 98.65%.
Dataset 2
- XGBoost was selected based on Recall during baseline comparison.
- Hyperparameter tuning and threshold analysis were performed.
- A threshold of 0.40 was selected.
- Final Recall increased to 74.07%.
- Final ROC-AUC was 80.57%.
⚠️ Limitations
The project has the following limitations:
- A single train-test split was used.
- No external validation dataset was used.
- Model and threshold selection were performed within the available test-set workflow.
- Dataset 2 contains repeated/duplicate profiles that may affect evaluation.
- The two datasets have different characteristics and feature structures.
- Dataset 1 and Dataset 2 were not combined.
- Dataset 1 was not subjected to the same hyperparameter tuning procedure used for Dataset 2.
🚀 Future Scope
Future improvements could include:
- Using cross-validation for more robust model evaluation.
- Using a separate validation set for model and threshold selection.
- Testing the models on external TB datasets.
- Collecting larger and more diverse healthcare datasets.
- Performing additional feature engineering.
- Extending SHAP analysis to global feature importance.
- Applying explainability techniques to both datasets.
- Developing a user-friendly screening-support application.
- Evaluating the system prospectively in a real-world healthcare setting.
🛠️ Technologies Used
Programming
- Python
Data Processing
- Pandas
- NumPy
Machine Learning
- Scikit-learn
- XGBoost
Visualization
- Matplotlib
- Seaborn
Explainable AI
- SHAP
Development Environment
- Jupyter Notebook / Google Colab
