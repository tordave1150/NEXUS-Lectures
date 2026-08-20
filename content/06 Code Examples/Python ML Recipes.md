---
title: "Python ML Recipes"
type: code
tags:
  - python
  - machine-learning
  - code
created: 2026-08-08
updated: 2026-08-08
---

# Python ML Recipes

> [!warning]
> ตัวอย่างนี้เน้น workflow และ leakage prevention. ตรวจ official scikit-learn documentation สำหรับ parameter names ของ version ที่ใช้งานจริง

## Time-ordered Train/Test Split

```python
X_train, X_test = X.iloc[:split], X.iloc[split:]
y_train, y_test = y.iloc[:split], y.iloc[split:]
```

สำหรับ time series หลีกเลี่ยง random shuffle หาก future rows อาจไหลเข้า training.

## Scaling + Ridge / Lasso / Elastic Net

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import Ridge, Lasso, ElasticNet

ridge = Pipeline([
    ("scale", StandardScaler()),
    ("model", Ridge(alpha=1.0)),
])

lasso = Pipeline([
    ("scale", StandardScaler()),
    ("model", Lasso(alpha=0.01)),
])

enet = Pipeline([
    ("scale", StandardScaler()),
    ("model", ElasticNet(alpha=0.01, l1_ratio=0.5)),
])
```

Scaling อยู่ใน pipeline เพื่อให้เรียน mean/SD จาก training fold เท่านั้น

## Logistic Regression

```python
from sklearn.linear_model import LogisticRegression

clf = Pipeline([
    ("scale", StandardScaler()),
    ("model", LogisticRegression()),
])
```

อย่าเลือก threshold 0.5 โดยอัตโนมัติถ้า business cost ของ false positive/false negative ไม่สมมาตร

## K-Nearest Neighbors and SVM

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC

knn = Pipeline([
    ("scale", StandardScaler()),
    ("model", KNeighborsClassifier(n_neighbors=7)),
])

svm = Pipeline([
    ("scale", StandardScaler()),
    ("model", SVC(kernel="rbf", probability=False)),
])
```

SVM decision score ไม่ใช่ calibrated probability โดยธรรมชาติ

## Tree Ensembles

```python
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier

rf = RandomForestClassifier(
    n_estimators=500,
    random_state=42
)

gb = GradientBoostingClassifier(
    learning_rate=0.05,
    n_estimators=300,
    random_state=42
)
```

สำหรับ time-series feature table ให้ tune hyperparameters ด้วย chronological folds

## Naive Bayes

```python
from sklearn.naive_bayes import GaussianNB

nb = GaussianNB()
nb.fit(X_train, y_train)
proba = nb.predict_proba(X_test)
```

สำหรับ count/text features ให้พิจารณา MultinomialNB/CategoricalNB ตาม likelihood assumption แทน GaussianNB โดยอัตโนมัติ.

## Decision Tree, Random Forest, AdaBoost

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier, AdaBoostClassifier

base_tree = DecisionTreeClassifier(
    max_depth=5,
    min_samples_leaf=10,
    random_state=42,
)

rf = RandomForestClassifier(
    n_estimators=500,
    max_features="sqrt",
    random_state=42,
)

ada = AdaBoostClassifier(
    n_estimators=200,
    learning_rate=0.05,
    random_state=42,
)
```

Tune complexity/ensemble hyperparameters จาก validation/CV ไม่ใช่ test set.

## General Cross-validation

```python
from sklearn.model_selection import StratifiedKFold, cross_validate

cv = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
result = cross_validate(
    clf,
    X,
    y,
    cv=cv,
    scoring=["accuracy", "precision", "recall", "f1", "roc_auc"],
)
```

สำหรับ non-time-series classification สามารถใช้ stratified folds เพื่อรักษาสัดส่วน class; ถ้า observations มี temporal/group dependency ต้องใช้ splitter ที่เคารพโครงสร้างนั้น.

## TimeSeriesSplit

```python
from sklearn.model_selection import TimeSeriesSplit, cross_val_score

cv = TimeSeriesSplit(n_splits=5)
scores = cross_val_score(
    ridge,
    X,
    y,
    cv=cv,
    scoring="neg_mean_absolute_error"
)
```

ตรวจด้วยว่า feature engineering ทุกตัวถูกสร้างแบบ past-only ก่อนใช้ CV

## Related Notes

- [[Regularized Regression]]
- [[Ridge Regression]]
- [[Lasso Regression]]
- [[Elastic Net]]
- [[Logistic Regression]]
- [[Naive Bayes]]
- [[Decision Trees]]
- [[Bagging and Random Forest]]
- [[Boosting and AdaBoost]]
- [[Cross Validation]]
- [[K-Nearest Neighbors]]
- [[Support Vector Machine]]
- [[Ensemble Learning]]
- [[ML Time-Series Feature Engineering]]
