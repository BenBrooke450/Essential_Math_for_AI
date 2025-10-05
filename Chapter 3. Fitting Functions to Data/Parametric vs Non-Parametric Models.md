

# Parametric vs Non-Parametric Models

---

## 1. **Parametric Models**

### Definition:

Parametric models assume that the data follows a certain **fixed form** (distribution or function), and the model is fully described using a **finite set of parameters**.
Once parameters are learned, the model cannot become more complex regardless of how much data you have.

### Characteristics:

* **Fixed number of parameters**: Complexity does not grow with more data.
* **Strong assumptions**: Assumes a specific relationship between features and output (like linearity, normality, etc.).
* **Fast to train & predict**: Because only a few parameters are learned.
* **Risk of bias**: If assumptions are wrong, model may underfit.

### Examples:

* **Linear Regression** → assumes relationship is linear (`y = mx + b`).
* **Logistic Regression** → assumes a sigmoid/logit link.
* **Naïve Bayes** → assumes independence among features.
* **Neural Networks (with fixed architecture)** → number of parameters fixed by design.

### Analogy:

It’s like fitting a straight line to data → you only need slope & intercept. Even if you collect more data, the model stays a line.

---

## 2. **Non-Parametric Models**

### Definition:

Non-parametric models **do not assume a fixed form**. Instead, they let the model complexity grow with the data.
They can capture more complex relationships, but often require more data and computation.

### Characteristics:

* **Number of parameters is not fixed** → grows with training data.
* **Flexible**: Can approximate almost any function.
* **Less bias, higher variance**: Need careful regularization or tuning.
* **Computationally expensive**: Because complexity grows with data size.

### Examples:

* **k-Nearest Neighbors (kNN)** → stores all training data and makes decisions at query time.
* **Decision Trees** → can grow very deep with data.
* **Random Forests / Gradient Boosted Trees** → ensemble of trees (non-parametric by nature).
* **Gaussian Processes** → define distributions over functions, very flexible.

### Analogy:

It’s like drawing a curve that perfectly follows your data points. As you add more data, the curve adapts and becomes more detailed.

---

## 3. **Comparison Table**

| Aspect               | Parametric Models                            | Non-Parametric Models                    |
| -------------------- | -------------------------------------------- | ---------------------------------------- |
| **Assumptions**      | Strong (e.g., linearity, normality)          | Few to none                              |
| **Parameters**       | Fixed, independent of dataset size           | Grow with data                           |
| **Flexibility**      | Less flexible (risk of underfitting)         | Very flexible (risk of overfitting)      |
| **Data Requirement** | Works with small datasets                    | Needs large datasets                     |
| **Computation**      | Fast (few parameters)                        | Slower (depends on dataset size)         |
| **Examples**         | Linear/Logistic Regression, Naïve Bayes      | kNN, Decision Trees, Random Forests, GPs |
| **Generalization**   | May struggle if true relationship is complex | Can capture complex patterns             |

---

## 4. **When to Use What?**

* **Parametric**:

  * When data is small.
  * When the underlying relationship is simple or well-understood.
  * When speed is critical.
  * Example: Predicting house prices with only a few features using Linear Regression.

* **Non-Parametric**:

  * When you have lots of data.
  * When the relationship is complex or unknown.
  * When accuracy is more important than speed.
  * Example: Image classification with deep decision trees or kNN.

---

## 5. **Example Walkthrough**

### Parametric: Linear Regression

```python
from sklearn.linear_model import LinearRegression

X = [[1],[2],[3],[4],[5]]
y = [2,4,6,8,10]

model = LinearRegression()
model.fit(X,y)

print(model.coef_, model.intercept_)  # slope = 2, intercept = 0
```

* Fixed two parameters: slope & intercept.
* Works fine if data is linear, but fails if data is curved.

---

### Non-Parametric: k-Nearest Neighbors

```python
from sklearn.neighbors import KNeighborsRegressor

X = [[1],[2],[3],[4],[5]]
y = [2,4,6,8,10]

model = KNeighborsRegressor(n_neighbors=2)
model.fit(X,y)

print(model.predict([[3.5]]))  
```

* Stores **all training data**.
* Prediction depends on neighbors — more data = more stored complexity.
* Flexible, can fit nonlinear trends.

---

**Key Takeaway:**

* **Parametric models** → Simple, fast, low data requirement, but inflexible.
* **Non-parametric models** → Flexible, powerful with large data, but computationally heavy.

