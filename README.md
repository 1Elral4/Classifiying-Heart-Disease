# Heart Disease Classifier 🫀

A machine learning project that uses logistic regression to predict the presence of heart disease in patients based on clinical features. Built using Python and scikit-learn with comprehensive data analysis and feature engineering.

## 📋 Project Overview

This project analyzes the UCI Heart Disease Dataset from the Cleveland Clinic Foundation to classify whether a patient has heart disease. The model achieves **83% accuracy** using carefully selected features and logistic regression.

## 🎯 Objectives

- Develop a binary classification model for heart disease prediction
- Perform comprehensive exploratory data analysis (EDA)
- Implement feature selection and engineering techniques
- Optimize model performance through hyperparameter tuning

## 📊 Dataset

The dataset contains **920 patient records** with the following key features:

- **Patient Demographics**: Age, sex, origin
- **Clinical Measurements**: Resting blood pressure, cholesterol levels, maximum heart rate
- **Cardiac Indicators**: Chest pain type, exercise-induced angina, ECG results
- **Target Variable**: Heart disease presence (binary: 0 = no disease, 1 = disease)

**Source**: UCI Machine Learning Repository - Cleveland Clinic Foundation

## 🔧 Technologies Used

- **Python 3.x**
- **Data Analysis**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **Machine Learning**: Scikit-learn
- **Preprocessing**: MinMaxScaler, One-Hot Encoding
- **Model Selection**: GridSearchCV, Cross-validation


## 📈 Methodology

### 1. Data Preprocessing
- **Missing Data Handling**: Removed features with high missing rates (`ca`, `thal`)
- **Data Cleaning**: Dropped observations with missing values (531/920 records retained)
- **Target Engineering**: Converted multi-class target to binary classification

### 2. Feature Selection
**Numerical Features** (correlation-based):
- `thalch`: Maximum heart rate achieved (correlation: 0.44)
- `oldpeak`: ST depression induced by exercise (correlation: 0.36)

**Categorical Features** (cross-tabulation analysis):
- `sex`: Gender
- `cp`: Chest pain type
- `restecg`: Resting electrocardiographic results

### 3. Feature Engineering
- **One-Hot Encoding**: Applied to categorical variables
- **MinMax Scaling**: Normalized all features to [0,1] range
- **Final Dataset**: 531 samples × 12 features

### 4. Model Development
- **Algorithm**: Logistic Regression
- **Train/Test Split**: 80/20
- **Hyperparameter Tuning**: GridSearchCV with 7-fold cross-validation
- **Optimization Parameters**: `class_weight`, `solver`

## 📊 Results

| Metric | Class 0 (No Disease) | Class 1 (Disease) | Overall |
|--------|---------------------|-------------------|---------|
| **Precision** | 0.85 | 0.82 | 0.83 |
| **Recall** | 0.73 | 0.90 | 0.83 |
| **F1-Score** | 0.79 | 0.86 | 0.83 |
| **Accuracy** | - | - | **83%** |

### Key Findings

- The model shows strong performance with balanced precision and recall
- High recall (0.90) for disease detection minimizes false negatives
- Feature selection based on correlation and statistical analysis proved effective

## 🔍 Feature Importance

Based on correlation analysis, the most predictive features are:

1. **Maximum Heart Rate** (`thalch`): Strong negative correlation with disease
2. **Exercise-Induced ST Depression** (`oldpeak`): Positive correlation with disease
3. **Chest Pain Type**: Asymptomatic patients show higher disease rates
4. **Gender**: Males show higher disease prevalence
5. **ECG Results**: Normal results associated with higher disease rates

## 🚧 Limitations & Future Work

### Current Limitations
- 83% accuracy may not be sufficient for clinical deployment
- Significant data loss due to missing value handling (42% of original data)
- Limited to linear relationships (logistic regression)

### Improvement Opportunities
- **Feature Engineering**: Create polynomial features for non-linear relationships
- **Advanced Models**: Try ensemble methods (Random Forest, XGBoost)
- **Data Augmentation**: Handle missing values with imputation techniques
- **Class Balancing**: Address potential class imbalance issues
- **Feature Selection**: Explore recursive feature elimination
