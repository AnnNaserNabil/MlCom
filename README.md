# MLCom - Automated ML Model Benchmarking Library

## 📌 Overview
MLCom is a Python package designed to automate the training, comparison, and evaluation of multiple machine learning models for **classification, regression, and clustering tasks**. It simplifies the **preprocessing, model selection, and performance analysis** process for both beginners and advanced users.

## 🚀 Features
✅ **Automated model benchmarking** – Compare multiple models with minimal effort.  
✅ **Flexible preprocessing** – Choose between automatic or manual feature engineering.  
✅ **Performance visualization** – Generate insightful plots for model comparison.  
✅ **Customizable feature handling** – Supports missing value imputation, scaling, and encoding.  
✅ **Multi-model training** – Supports **Random Forest, Gradient Boosting, XGBoost, LightGBM, CatBoost**, and more.

---
## 📥 Installation

### **1️⃣ Install MLCom**
```bash
git clone https://github.com/AnnNaserNabil/MLCom.git
cd mlcom
pip install -r requirements.txt
```

### **2️⃣ Install MLCom as a package** (Optional)
```bash
pip install -e .
```

---
## 🛠️ Usage Guide

### **🔹 1. Load Dataset**
You can load a dataset from a CSV file or a Pandas DataFrame.
```python
from mlcom.data_loader import load_data

data = load_data("data.csv")  # Load from CSV file
```

### **🔹 2. Preprocess Data**
MLCom allows you to either **automatically** process data or **manually engineer features**.
```python
from mlcom.preprocess import preprocess_data

# Automatic Preprocessing
X, y = preprocess_data(data, target_column="label", auto=True)

# Manual Feature Engineering
manual_features = data.copy()
manual_features["new_feature"] = manual_features["existing_feature"] ** 2
X, y = preprocess_data(data, target_column="label", auto=False, manual_features=manual_features)
```

### **🔹 3. Split Data**
```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

### **🔹 4. Train Multiple Models**
MLCom supports training and evaluating multiple machine learning models.
```python
from mlcom.model_train import train_models

results = train_models(X_train, y_train, X_test, y_test)
```

### **🔹 5. Compare Models**
```python
from mlcom.model_compare import compare_models

compare_models(results)
```

### **🔹 6. Visualize Performance**
```python
from mlcom.visualization import plot_results

plot_results(results)
```

---
## 📌 Supported Models
MLCom supports the following machine learning models out of the box:

- **Tree-based models:** Random Forest, Gradient Boosting, XGBoost, LightGBM, CatBoost, Extra Trees, AdaBoost, Decision Tree
- **Linear models:** Logistic Regression
- **Support Vector Machines:** SVC
- **Instance-based learning:** K-Nearest Neighbors (KNN)
- **Naive Bayes Classifier**
- **Neural Networks:** Multi-layer Perceptron (MLPClassifier)

---
## 🔥 Example: Using MLCom with the **California Housing Prices Dataset**

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.datasets import fetch_california_housing
from mlcom.preprocess import preprocess_data
from mlcom.model_train import train_models
from mlcom.model_compare import compare_models
from mlcom.visualization import plot_results

# Load dataset
data = fetch_california_housing()
california_df = pd.DataFrame(data.data, columns=data.feature_names)
california_df['target'] = data.target  # House price target variable

# Preprocess data
X, y = preprocess_data(california_df, target_column='target', auto=True)

# Split dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train models
results = train_models(X_train, y_train, X_test, y_test)

# Compare models
compare_models(results)

# Visualize results
plot_results(results)
```

---
## 🧪 Running Tests
To ensure everything is working correctly, run the test suite:
```bash
pytest tests/
```

---
## 🔄 Future Enhancements
- **Deep learning support** (TensorFlow & PyTorch models)
- **Custom metric selection** (AUC, precision, recall, RMSE, etc.)
- **Hyperparameter tuning integration**
- **Web-based UI for interactive benchmarking**

---
## 📜 Conclusion
MLCom is a powerful tool for benchmarking machine learning models effortlessly. It automates model training, comparison, and visualization while providing flexibility for advanced feature engineering.

🚀 **Try MLCom now and simplify your ML workflows!** 🚀

