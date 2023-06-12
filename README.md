# SmplML / SimpleML: Simplified Machine Learning for Classification

SmplML is a user-friendly Python library for streamlined machine learning classification. It offers intuitive modules for data preprocessing, model training, and evaluation. Ideal for beginners and experts alike, EasyML simplifies classification tasks, enabling you to gain valuable insights from your data with ease.

## Features

- Data preprocessing: Easily handle encoding categorical variables.
- Model training: Train various classification models with just a few lines of code.
- Model evaluation: Evaluate model performance using common metrics and visualizations.

## Installation

- You can install SmpML using pip:
```shell
pip install SimpleML
```

## Usage

### Classification
```python
import seaborn as sns
import pandas as pd
from smpl_ml.smpl_ml import TrainModel

from sklearn.neighbors import KNeighborsClassifier

# Load the dataset
df = sns.load_dataset('penguins')

# Set the target and features
target = 'species'
features = df.iloc[:, df.columns != target].columns

# Create the classifier trainer
clf_trainer = TrainModel(df.dropna(), target=target, features=features, model=KNeighborsClassifier())

# Fit the model
clf_trainer.fit()

# Evaluate the model
clf_model = clf_trainer.evaluate()
```

`model` when `verbose` is set to `True` will return a DataFrame of classification metrics.


|    | Recall | Specificity | Precision | F1-Score | Accuracy |
|----|--------|-------------|-----------|----------|----------|
| Adelie | 0.91   | 0.70        | 0.67      | 0.77     | 0.76     |
| Chinstrap | 0.38   | 0.92        | 0.62      | 0.47     | 0.76     |
| Gentoo | 0.86   | 1.00        | 1.00      | 0.92     | 0.76     |

### Regression
```python
import seaborn as sns
import pandas as pd
from smpl_ml.smpl_ml import TrainModel

from sklearn.neighbors import KNeighborsRegressor

# Load the dataset
df = sns.load_dataset('iris')

# Set the target and features
target = 'sepal_length'
features = df.columns[1:]

# Create the regressor trainer
reg_trainer = TrainModel(df.dropna(), target=target, features=features, model=KNeighborsRegressor())

# Fit the model
reg_trainer.fit()

# Evaluate the model
reg_model = reg_trainer.evaluate()
```

|   |Metrics|
|---|-------|
|MSE|0.11|
|RMSE|0.34|
|MAE|0.27|
|R-Squared|0.74|