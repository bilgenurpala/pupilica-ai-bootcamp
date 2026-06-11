# 02 — Machine Learning

<div align="center">

[![Machine Learning](../assets/machine_learning_banner.png)](../README.md)

</div>

> My notes from the machine learning and mathematical foundations sessions of the Pupilica AI Bootcamp.
> Instructor's repo: [turkiyeyapayzekaakademisi/Machine-Learning](https://github.com/turkiyeyapayzekaakademisi/Machine-Learning)

---

## What's in this folder

| File / Resource | Action / Type | Description |
|:---|:---|:---|
| `Machine_Learning_Training.ipynb` | [![Notebook](https://img.shields.io/badge/Jupyter-Notebook-blue?logo=jupyter&style=flat-square)](./Machine_Learning_Training.ipynb) | Follow-along notebook for core models, clustering, and tuning |
| `Mathematics_of_Machine_Learning.ipynb` | [![Math Notebook](https://img.shields.io/badge/Jupyter-Math%20Notebook-purple?logo=jupyter&style=flat-square)](./Mathematics_of_Machine_Learning.ipynb) | Newly created notebook covering Linear Algebra, Optimization, and Statistics |
| `customer_data_ml_practice.csv` | [![Practice Dataset](https://img.shields.io/badge/CSV-Practice-lightgrey?logo=pandas&style=flat-square)](./customer_data_ml_practice.csv) | Translated customer dataset used for preprocessing & scaling exercises |
| `feature_engineering_practice.csv` | [![Features Dataset](https://img.shields.io/badge/CSV-Features-lightgrey?logo=pandas&style=flat-square)](./feature_engineering_practice.csv) | Translated dataset containing features for selection exercises |

---

## Topics Covered & Methodologies

### 1. Data Preprocessing for ML (Avoiding Data Leakage)
A robust preprocessing pipeline is required to prepare clean matrices for models:
- **Encoding Categorical Columns**: 
  - *Label Encoding*: Maps categories to ordinal integers (best for tree-based models like Decision Trees where scale doesn't matter).
  - *One-Hot Encoding*: Explodes $C$ categories into $C-1$ binary columns (critical for distance-based or linear models like KNN and Logistic Regression).
- **Feature Scaling**: 
  - *Standardization (StandardScaler)*: Centers data around zero with unit variance. Recommended for models assuming normal distribution:
    $$z = \frac{x - \mu}{\sigma}$$
  - *Normalization (MinMaxScaler)*: Bounds values between $[0, 1]$. Essential for distance-based models sensitive to scaling:
    $$x_{\text{scaled}} = \frac{x - x_{\text{min}}}{x_{\text{max}} - x_{\text{min}}}$$
- **Data Leakage Prevention**: **Crucial rule** — split dataset into train/test splits *before* fitting encoders or scalers. Only fit on training data, then transform both train and test.

### 2. Feature Engineering
Creating high-signal numerical representations from existing attributes:
- **Interaction/Ratio Terms**: e.g., Combining age and experience:
  $$\text{experience\_ratio} = \frac{\text{experience\_years}}{\text{age}}$$
- **Correlation Filtering**: Dropping features showing minimal correlation with the target variable, keeping features with high predictive signals.

### 3. Decision Trees
A supervised classification and regression model. Splitting decisions are governed by node impurity metrics:
- **Gini Impurity**:
  $$Gini(D) = 1 - \sum_{i=1}^C p_i^2$$
- **Entropy**:
  $$Entropy(D) = -\sum_{i=1}^C p_i \log_2 p_i$$
- **Pruning**: Restricting tree growth (using `max_depth` or `min_samples_split`) prevents overfitting to training data.

### 4. K-Means Clustering
An unsupervised clustering algorithm.
1. **Initialize**: Choose $k$ centroids randomly or via `k-means++`.
2. **Assign**: Assign each data point $x_i$ to the nearest centroid $\mu_j$ based on Euclidean distance.
3. **Update**: Move each centroid to the mean of its assigned data points.
4. **Iterate**: Repeat until centroids stop changing.
- **The Elbow Method**: Plots Inertia (Within-Cluster Sum of Squares, WCSS) against the cluster count $k$, looking for the point of diminishing return:
  $$WCSS = \sum_{j=1}^k \sum_{x_i \in C_j} ||x_i - \mu_j||^2$$

### 5. Hierarchical Clustering
An alternative clustering method that constructs a tree (dendrogram) showing how clusters merge step-by-step.
- **Advantages**: No need to specify $k$ cluster counts upfront; can cut the dendrogram at any threshold height.
- **Drawback**: High computational complexity ($O(n^3)$), making it slow on larger datasets.

### 6. Principal Component Analysis (PCA)
An unsupervised dimensionality reduction technique that projects data onto orthogonal axes of maximum variance:
1. Center the dataset (subtract mean).
2. Calculate the Covariance Matrix $\Sigma$:
   $$\Sigma = \frac{1}{n} X^T X$$
3. Perform Eigendecomposition to retrieve eigenvalues ($\lambda$) and eigenvectors ($v$):
   $$\Sigma v = \lambda v$$
4. Sort eigenvectors by eigenvalues in descending order. The top eigenvectors are the Principal Components representing direction axes of maximum variance.

### 7. Optimization via Gradient Descent
The engine of model optimization. Weights $w$ are updated iteratively in the direction opposite to the loss function gradient:
$$w \leftarrow w - \alpha \nabla J(w)$$
Where:
- $J(w)$ is the objective/loss function.
- $\nabla J(w)$ represents the gradient vector of partial derivatives.
- $\alpha$ represents the learning rate (step size).

### 8. Model Validation (Cross-Validation)
A single train/test split can be biased. We use Cross-Validation to get a generalizable metric:
- **K-Fold**: Splits dataset into $k$ equal segments. Iterates $k$ times, using each segment as test validation once and averaging final scores.
- **Stratified K-Fold**: Preserves the original class distributions across each fold. Critical for imbalanced datasets.
- **Leave-One-Out (LOO)**: Sets $k=n$. Extreme validation where each sample is tested individually. High compute cost.

### 9. Hyperparameter Tuning
- **GridSearchCV**: Exhaustive search checking every possible combination of specified parameters in a grid. Guaranteed to locate global best in search grid, but computationally expensive.
- **RandomizedSearchCV**: Evaluates a random sample of parameter combinations. Executes in a fraction of the time while retrieving comparable optimal values.

---

## Key Things I Want to Remember
- Always fit transformers on training splits only; otherwise, test set information leaks into training.
- PCA is highly sensitive to features with different ranges — always apply standardization (`StandardScaler`) before running PCA.
- Tree-based models are robust against raw feature scales, but distance models (KNN, K-Means) require scaling to prevent large columns from dominating distance calculations.

---

[← Data Science Fundamentals](../01-Data-Science-Fundamentals/) &nbsp;|&nbsp; [Next: Deep Learning →](../03-Deep-Learning/)
