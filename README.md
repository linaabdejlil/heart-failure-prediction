# Heart Failure Prediction Model Documentation

## **Objective**
The goal of this project is to build a machine learning model that predicts whether a patient has a heart problem or not based on clinical data. This project uses various machine learning algorithms and compares their performance to determine the most suitable model for deployment.

---

## **Dataset Overview**

### **Dataset Name**: Heart Failure Prediction
### **Key Features**:
- **Age**: Patient's age.
- **Sex**: Gender of the patient.
- **ChestPainType**: Type of chest pain (e.g., Typical, Atypical, Non-anginal, Asymptomatic).
- **RestingBP**: Resting blood pressure (mm Hg).
- **Cholesterol**: Serum cholesterol level (mg/dl).
- **FastingBS**: Fasting blood sugar (1 if > 120 mg/dl, 0 otherwise).
- **RestingECG**: Resting electrocardiogram results.
- **MaxHR**: Maximum heart rate achieved.
- **ExerciseAngina**: Exercise-induced angina (1: Yes, 0: No).
- **Oldpeak**: ST depression induced by exercise relative to rest.
- **ST_Slope**: Slope of the peak exercise ST segment.
- **Target**: 1 if the patient has a heart problem, 0 otherwise.

---

## **Workflow**

### **1. Data Preprocessing**
- Imported libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, and `scikit-learn`.
- Handled missing values and verified data integrity.
- Performed label encoding for categorical variables (e.g., `ChestPainType`, `RestingECG`, `ST_Slope`).
- Scaled numerical features using `StandardScaler` to standardize data.

### **2. Exploratory Data Analysis (EDA)**
- **Correlation Heatmap**: Visualized relationships between features and the target variable.
- **Distribution Plots**: Identified skewed features and balanced target distribution.

### **3. Feature Selection**
- Used **Recursive Feature Elimination (RFE)** to identify the most impactful features:
  - Selected Features: `ChestPainType`, `Cholesterol`, `MaxHR`, `Oldpeak`, `ST_Slope`.

---

## **Modeling and Results**

### **Algorithms Tested**:
1. **Logistic Regression**:
   - Accuracy: 87%
   - ROC-AUC: 0.90
   - High recall (93%), minimizing false negatives.

2. **Random Forest**:
   - Accuracy: 88%
   - ROC-AUC: 0.93
   - High precision (87%) and recall (92%).

3. **XGBoost**:
   - Accuracy: 87%
   - ROC-AUC: 0.87
   - Balanced precision (92%) and recall (85%).

4. **Voting Classifier (Ensemble)**:
   - Accuracy: 89%
   - ROC-AUC: 0.89
   - Combines strengths of Logistic Regression, Random Forest, and XGBoost.

5. **Hyperparameter Tuning**:
   - Used `RandomizedSearchCV` for Random Forest and XGBoost.
   - Optimized parameters improved accuracy and ROC-AUC.

---

## **Final Model**
### **Voting Classifier (Ensemble)**:
- Selected for its robust performance and ability to balance precision and recall.
- Final metrics:
  - Accuracy: 89%
  - ROC-AUC: 0.89
  - Confusion Matrix: [[68, 9], [12, 95]]

---

## **Future Improvements**
1. **Model Interpretability**:
   - Use SHAP or LIME to explain predictions, especially for medical diagnostics.
2. **Additional Data**:
   - Include more clinical variables to improve prediction accuracy.
3. **Deployment**:
   - Save the model using `joblib` or `pickle`.
   - Build an API using Flask/Django to deploy the model.
   - Integrate with a front-end UI for user interaction.
4. **Continuous Monitoring**:
   - Monitor real-world performance and retrain the model as needed.

---

## **Conclusion**
This project demonstrates the development of a robust machine learning pipeline for heart disease prediction. The Voting Classifier is recommended as the final model due to its strong performance metrics and balanced predictions. Further steps include deployment and integrating model interpretability techniques for real-world use.

