---
layout: page
title: Oracle Data Science Capstone project
subtitle: Electric Vehicle Present Discovery

---

   <link rel="stylesheet" type="text/css" href="css/main.css" />

   <div id= "main">
		<div id="menubar">
			<ul id="menu">
			    <li><a href="https://monarch2018.github.io/ev_prediction/index.html">Overview</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/data/">Data</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/preprocessing/">Preprocessing</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/timeseries/">Time Series</a></li>
			    <li class = "selected"><a href="https://monarch2018.github.io/ev_prediction/baseline/">Baseline</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/prediction/">Prediction</a></li>
			</ul>
		</div>
	
   </div>

### Main Process (5 models)
1. Logistic Regression 
2. Naive Bayes
3. Suppot Vector Machine
4. Random Forest Classification
4. XGBoost Classification
5. Comparison and Conclusion

```
# Main packages and functions
from sklearn.metrics import mean_squared_error
from statsmodels.tsa.stattools import adfuller
from statsmodels.graphics.tsaplots import plot_acf
from statsmodels.graphics.tsaplots import plot_pacf
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.graphics.gofplots import qqplot
from statsmodels.tsa.arima_model import ARIMAResults
from scipy.stats import boxcox
# Load timeseries dataset
timeseries = importfile(file_id = '1bx2sY8TGrJ7DVRoZ_yjXxp3tQgqn4Zix')
```

### 1. Logistic Regression

- GridSearchCV to find the best_estimator and best_parameter
- Print the classification_report
- Plot confusion_matrix
- Plot roc_auc_score 

```
if __name__ == '__main__':
    train_data=pd.read_csv(os.path.join("/content",'train.csv'), index_col =0)
    test_data=pd.read_csv(os.path.join("/content",'test.csv'), index_col =0)
    X_train, X_test, y_train, y_test = get_data(train_data,test_data)
    # Set the parameters by cross-validation
    tuned_parameters = [{'C': [0.001, 0.01,0.1]}]
    grid = grid_search(tuned_parameters, X_train, y_train)
    best_estimator = grid.best_estimator_
    best_estimator.fit(X_train, y_train)
    y_pred = best_estimator.predict(X_test)
    report(y_test, y_pred)
    plot_confusion_matrix(y_test, y_pred,normalize=False)
    plot_roc_auc(X_test,y_test, y_pred)
```

**Output:**

![log](/img/log.png#log)

### 2. Naive Bayes

- GridSearchCV to find the best_estimator and best_parameter
- Print the classification_report
- Plot confusion_matrix
- Plot roc_auc_score 

```
if __name__ == '__main__':
    train_data=pd.read_csv(os.path.join("/content",'train.csv'), index_col =0)
    test_data=pd.read_csv(os.path.join("/content",'test.csv'), index_col =0)
    X_train, X_test, y_train, y_test = get_data(train_data,test_data)
    # Set the parameters by cross-validation
    tuned_parameters = [{'alpha': [0.01, 0.1, 1]}]
    grid_naiv = grid_search(tuned_parameters, X_train, y_train)
    best_estimator = grid_naiv.best_estimator_
    best_estimator.fit(X_train, y_train)
    y_pred = best_estimator.predict(X_test)
    report(y_test, y_pred)
    plot_confusion_matrix(y_test, y_pred,normalize=False)
    plot_roc_auc(X_test,y_test, y_pred)
```

**Output:**

![naiv](/img/naiv.png#naiv)

### 3. SVM

- GridSearchCV to find the best_estimator and best_parameter
- Print the classification_report
- Plot confusion_matrix
- Plot roc_auc_score 

```
if __name__ == '__main__':
    train_data=pd.read_csv(os.path.join("/content",'train.csv'), index_col =0)
    test_data=pd.read_csv(os.path.join("/content",'test.csv'), index_col =0)
    X_train, X_test, y_train, y_test = get_data(train_data,test_data)
    #Set the parameters by cross-validation
    tuned_parameters = [{'kernel': ['rbf'], 'gamma': [1e-3, 1e-4],'C': [0.1, 1, 10]},
                        {'kernel': ['linear'], 'C': [0.1, 1, 10]}]
    grid_svm = grid_search(tuned_parameters, X_train, y_train)
    best_estimator = grid_svm.best_estimator_
    best_estimator.fit(X_train, y_train)
    y_pred = best_estimator.predict(X_test)
    report(y_test, y_pred)
    plot_confusion_matrix(y_test, y_pred,normalize=False)
    plot_roc_auc(X_test,y_test, y_pred)
```

**Output:**

![svm](/img/svm.png#svm)

### 4. Random Forest Classification

- GridSearchCV to find the best_estimator and best_parameter
- Print the classification_report
- Plot confusion_matrix
- Plot roc_auc_score 

```
if __name__ == '__main__':
    train_data=pd.read_csv(os.path.join("/content",'train.csv'), index_col =0)
    test_data=pd.read_csv(os.path.join("/content",'test.csv'), index_col =0)
    X_train, X_test, y_train, y_test = get_data(train_data,test_data)
    # Set the parameters by cross-validation
    tuned_parameters = [{'n_estimators': [100, 200], 
    			 'max_depth': [10, 50, 100], 
			 'min_samples_split': [2, 4], 
			 'max_features': ['sqrt', 'log2']}]
    grid_rf = grid_search(tuned_parameters, X_train, y_train)
    best_estimator = grid_rf.best_estimator_
    best_estimator.fit(X_train, y_train)
    y_pred = best_estimator.predict(X_test)
    report(y_test, y_pred)
    imp = get_feature_importance(train_data)
    plot_confusion_matrix(y_test, y_pred,normalize=False)
    plot_roc_auc(X_test,y_test, y_pred)
```

**Output:**

![rf1](/img/rf1.png#rf1)
![rf2](/img/rf2.png#rf2)

### 5. XGBoost Classification

- GridSearchCV to find the best_estimator and best_parameter
- Print the classification_report
- Plot confusion_matrix
- Plot roc_auc_score

```
if __name__ == '__main__':
    train_data=pd.read_csv('./train.csv', index_col =0)
    test_data=pd.read_csv('./test.csv', index_col =0)
    X_train, X_test, y_train, y_test = get_data(train_data,test_data)
    #model before grid search
    xgb = model(xgb.XGBClassifier(),X_train, y_train)
    y_pred = xgb.predict(X_test)
    report(y_test, y_pred)
    #grid search
    param = {'n_estimators': [100, 200, 300],
            'max_depth': [3, 4, 5], 
            'min_child_weight': [1, 2, 3],
            'gamma': [0.1, 0.2, 0.3]}
    grid_search(grid_search(param,X_train,y_train))
    #plot
    plot_important_features(xgb)
    plot_confusion_matrix(y_test, y_pred,normalize=False)
    plot_roc_auc(X_test,y_test, y_pred,xgb)
```

**Output:**

![xg1](/img/xg1.png#xg1)
![xg2](/img/xg2.png#xg2)


### 6. Comparison and Conclusion
By looking at the roc_auc_score, it shows that Random Forest and XGBoost classification performs best which are 
