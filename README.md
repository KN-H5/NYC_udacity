# Build a ML Pipeline for Short term Rental Prices in NYC
https://github.com/KN-H5/NYC_udacity

## Dependencies
- mlflow


## Installation
```bash
pip install mlflow
```

## Usage

```bash
cd ./NYC_udacity
mlflow run . 
``` 

Run EDA step which will open a jupyter notebook
```bash
cd ./NYC_udacity/componenets/EDA
mlflow run . 
```

Run evaluation step
```bash
mlflow run . -P hydra_options="main.execute_steps=test_model"
```

Run a specific component only
```bash
mlflow run . -P hydra_options="main.execute_steps=train_random_forest"
```

Run a sweep of different hyperparameters to train the model. ```hydra/launcher=joblib``` enables parallel training.
```bash
mlflow run . -P hydra_options="-m hydra/launcher=joblib main.execute_steps=train_random_forest pipeline.model.random_forest.max_features=0.1,0.33,0.5,0.75,1 pipeline.tfidf.max_features=10,15,30"
```
