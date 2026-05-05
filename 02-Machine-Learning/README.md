# 02 — Machine Learning

> My notes from the machine learning sessions of the Pupilica AI Bootcamp.
> Instructor's repo: [turkiyeyapayzekaakademisi/Machine-Learning](https://github.com/turkiyeyapayzekaakademisi/Machine-Learning)

---

## What's in this folder

| File | Description |
|------|-------------|
| `YZA_ML.ipynb` | Instructor's ML notebook — I follow along and add my own comments |
| `musteri_verisi_ml_pratik.csv` | Customer dataset used for preprocessing & model practice |
| `oznitelik_muhendisligi_pratik.csv` | Dataset for feature engineering exercises |

---

## Topics Covered

### Data Preprocessing for ML
Before feeding data into any model, there's a whole pipeline to set up. I worked through each step on the customer dataset:

- **Handling missing values** — dropped rows where there were very few nulls, filled numerical columns with the median, and categorical columns with the mode
- **Label Encoding vs One-Hot Encoding** — label encoding assigns integers to categories (good for tree-based models), one-hot encoding creates binary columns (better for linear models). Getting this wrong can mess up the whole model.
- **Standardization vs Normalization** — `StandardScaler` makes data zero-mean with unit variance; `MinMaxScaler` scales everything to [0, 1]. I use standardization by default unless I know the algorithm expects bounded inputs.
- **Train/test split** — `train_test_split()` with `test_size=0.2`. The important thing I learned: always split *before* fitting any scaler to avoid data leakage.

### Feature Engineering
This was one of my favorite sessions. Instead of just using existing columns, you can *create* new ones that carry more predictive signal:
- Combined columns (e.g. `experience_ratio = experience_years / age`)
- Derived columns (e.g. `estimated_annual_spend`)

Then I used correlation with the target variable to select the most useful features. Features with `|corr| > 0.995` with the target were kept — everything else dropped.

### Decision Trees
My first real classification model. Trained on the Iris dataset (3 flower classes, 4 features). Key things I learned:
- `criterion='gini'` vs `'entropy'` — both work, gini is slightly faster
- `max_depth` controls overfitting — deeper tree = more overfit
- `plot_tree()` lets you actually *see* the decisions the model is making, which is really satisfying
- Feature importance shows which features the tree relied on most — for Iris it was petal length and petal width

### K-Means Clustering
My first unsupervised learning algorithm. Created a synthetic dataset with 4 clusters and trained KMeans on it. The key insight: you need to know (or guess) the number of clusters `k` in advance. The Elbow method helps with that — plot inertia vs k and look for the "elbow."

Visualizing the cluster centroids on the scatter plot really helped me understand what the algorithm is actually doing.

### Hierarchical Clustering
An alternative to K-Means where you don't need to specify k upfront. The dendrogram is a tree diagram that shows how clusters merge step by step — you cut it at a certain height to get your clusters. More intuitive than K-Means but much slower on large datasets.

### PCA — Dimensionality Reduction
Used PCA to reduce the Iris dataset from 4 features down to 2, then plotted it. The 3 classes became clearly separable in 2D even though we dropped 2 dimensions. This showed me that not all dimensions carry equal information.

### Cross-Validation
Splitting data once into train/test is a bit risky — you might get lucky (or unlucky) with that particular split. Cross-validation solves this:
- **K-Fold**: splits data into k folds, trains k times, averages the scores
- **Stratified K-Fold**: same but preserves class proportions in each fold — better for imbalanced datasets
- **Leave-One-Out (LOO)**: extreme version, trains n times. Very accurate but slow.

### Hyperparameter Tuning
Practiced Grid Search and Random Search on KNN, Decision Tree, and Logistic Regression using the breast cancer dataset:
- **GridSearchCV**: tries every combination of parameters — exhaustive but slow
- **RandomizedSearchCV**: samples random combinations — much faster, almost as good

The best practice: use RandomizedSearch for a first pass, then GridSearch to fine-tune around the best region.

---

## Key Things I Want to Remember

- Data leakage is the #1 silent killer — always fit scalers on training data only, never on the full dataset.
- Label encoding creates an *artificial ordering* between categories. If categories have no natural order, use one-hot encoding.
- Decision trees overfit easily. Always tune `max_depth` or use pruning.
- Cross-validation score is more trustworthy than a single train/test split score.
- PCA is useful for visualization and reducing noise, but it makes features less interpretable.

---

[← Data Science Fundamentals](../01-Data-Science-Fundamentals/) &nbsp;|&nbsp; [Next: Deep Learning →](../03-Deep-Learning/)
