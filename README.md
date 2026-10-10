# Machine-Learning-Based-Tuberculosis-Risk-Prediction-for-Early-Screening

📌 Project Overview
Tuberculosis (TB) is a major infectious disease where early identification and screening can support timely clinical assessment. This project develops a machine learning-based predictive model to identify whether a patient is likely to be classified as TB Suspected or Not Suspected based on clinical, demographic, health, and exposure-related attributes.
The project follows an end-to-end Predictive Modelling / KDD (Knowledge Discovery in Databases) workflow, including data understanding, preprocessing, exploratory analysis, model development, evaluation, and explainability.
Note: This project is developed for academic and educational purposes. The model is not a medical diagnostic system and should not be used to diagnose or treat tuberculosis.

🎯 Problem Statement
To develop a machine learning model that predicts TB risk using clinical and demographic data, supporting early screening and further clinical assessment.
Objective
To develop a machine learning model that predicts TB risk using clinical and demographic data, supporting early screening and further clinical assessment.

📊 Dataset
The dataset used in this project is a TB-related dataset obtained from the supplementary data associated with a PeerJ Computer Science research study.
Dataset Details
- Total usable records: 760
- Target variable: Prediction
- Target classes:
  - TB Suspected — 392 records
  - Not Suspected — 368 records
Feature Categories
Respiratory Indicators
- Cough
- Cough Duration
- Cough Type
- Mucus
- Chest Pain
- Breathe State
Clinical Indicators
- Body Temperature
- Chills
- Pulmonary Effusion
- ESR Value
Health and Exposure Factors
- Diet
- Physique
- Energy Adequacy
- Smoking
- Crowding
- Exposed
Patient ID was excluded from model training because it is an identifier rather than a predictive feature. Empty/irrelevant columns were also removed during data cleaning.
🔄 Predictive Modelling / KDD Workflow
The project follows these major stages:
Problem Identification
        ↓
Data Collection
        ↓
Data Understanding
        ↓
Data Cleaning
        ↓
Feature Transformation
        ↓
Exploratory Data Analysis
        ↓
Train-Test Split
        ↓
Model Development
        ↓
Model Comparison
        ↓
Model Evaluation
        ↓
Explainability using SHAP
        ↓
TB Risk Prediction

🧹 Data Preprocessing
The following preprocessing steps were performed:
1. Loaded the dataset using Pandas.
2. Inspected the dataset structure and feature values.
3. Removed irrelevant empty columns.
4. Removed Patient ID from the modelling features.
5. Converted Cough Duration into a numerical format.
6. Encoded the target variable:
   - Not Suspected → 0
   - TB Suspected → 1
7. Applied One-Hot Encoding to categorical features.
8. Used scaling for models where required.
9. Divided the data into training and testing sets using a 70:30 stratified split.
10. Used random_state=42 for reproducibility.
🔍 Exploratory Data Analysis
Exploratory Data Analysis was performed to understand:
- Dataset structure
- Target class distribution
- Feature distributions
- Missing values
- Relationships between variables
- Feature importance
Visualizations were generated using Python-based data visualization libraries.
🤖 Machine Learning Models
Multiple classification algorithms were developed and compared:
1. Logistic Regression
2. Decision Tree
3. Random Forest
4. AdaBoost
5. Gaussian Naive Bayes
6. Multi-Layer Perceptron (MLP)
After comparison, Random Forest was selected as the final model based on its overall predictive performance.
🏆 Final Model
Random Forest Classifier
The final Random Forest model was configured with:
- n_estimators = 300
- class_weight = "balanced"
The model was selected because it provided strong performance on the structured tabular dataset and supported feature-importance and SHAP-based interpretation.
📈 Model Evaluation
The final Random Forest model achieved the following results on the test dataset:
Metric	Score
Accuracy	94.74%
Precision	92.74%
Recall	97.46%
F1-Score	95.04%
ROC-AUC	98.65%


Confusion Matrix
	Predicted Not Suspected	Predicted TB Suspected
Actual Not Suspected	101	9
Actual TB Suspected	3	115


The model correctly identified 115 TB Suspected cases and 101 Not Suspected cases in the test set.
🧠 Explainable AI using SHAP
SHAP (SHapley Additive exPlanations) was used to provide an interpretation of the Random Forest model's predictions.
SHAP helps identify which input features contributed to a particular model prediction.
Examples of features appearing among the important SHAP contributions include:
- Cough Type
- Cough Duration
- Mucus
- ESR Value
- Chest Pain
- Chills
- Cough
SHAP explanations describe the model's behaviour and feature contributions. They should not be interpreted as proof of medical causation.

🖥️ Interactive Prediction Dashboard
A Gradio-based interactive dashboard was developed as part of the project.
The dashboard allows users to:
- Enter patient-related clinical and demographic information
- Generate a TB risk prediction
- View the model-estimated probability
- View the risk category
- Examine SHAP-based explanations
- View clinical action guidance
- Reset or load a demonstration case
Example Demonstration
For the high-risk demonstration input, the model produced:
Prediction: TB Suspected
Model-estimated probability: 99.83%
Risk category: HIGH RISK
The 99.83% value is a model-estimated probability for the specific demonstration input and does not represent a clinical diagnosis or a patient's actual probability of having TB.
🛠️ Technologies Used
- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- SHAP
- Gradio

📌 Key Findings
- The project successfully implemented an end-to-end predictive modelling workflow.
- Six machine learning algorithms were developed and compared.
- Random Forest was selected as the final model.
- The final model achieved 94.74% accuracy and 97.46% recall on the test set.
- SHAP was used to improve model interpretability.
- A Gradio dashboard was developed to demonstrate interactive TB risk prediction.
- The system is intended to support early screening, not replace clinical diagnosis.
  
🔮 Future Scope
Future improvements could include:
- Training on larger and more diverse datasets.
- External validation using independent datasets.
- Incorporating additional clinically relevant variables.
- Monitoring model performance over time.
- Improving explainability and user interaction.
- Clinical validation before considering any real-world deployment.
  
👩‍💻 Author
Shreyasi Gidmare
B.Tech Computer Science & Engineering
Honours – Artificial Intelligence & Machine Learning
Symbiosis Institute of Technology, Nagpur
📚 Reference
The dataset and research context are based on the PeerJ Computer Science study and its supplementary materials used for this academic project.
