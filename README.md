# hyperoptsearchcv

> Wrapper for hyperopt to use it with sklearn pipelines

### Example
[Describe a search space](https://github.com/hyperopt/hyperopt/wiki/FMin#22-a-search-space-example-scikit-learn) just as in original hyperopt 
```python
search_space = {
    'n_estimators': hp.quniform('n_estimators', 25, 1525, 50),
    'min_samples_split': hp.choice('min_samples_split', [2, 5, 20, 50]),
    'min_samples_leaf': hp.choice('min_samples_leaf', [1, 2, 4]),
}
```
Specify types of parameters from search space
* WARNING: hp.quniform always return float type and need to be casted to int if estimator's argument requires it!

```
param_cast = {
    'n_estimators': int,
    'max_depth': int,
    'min_samples_split': None,
    # parameter can be omitted if cast is not required
    # 'min_samples_leaf': None,
}
```
Create HyperoptSearchCV object and fit it
```
rf_hyper = HyperoptSearchCV(estimator=RandomForestClassifier(),
                            search_space=search_space, param_types=param_cast)


rf_hyper.fit(X_train, y_train)
```

### Installing

```
pip install -i https://test.pypi.org/simple/ hyperoptsearchcv
```

