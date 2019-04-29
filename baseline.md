---
layout: page
title: Oracle Data Science Capstone project
subtitle: Electric Vehicle Present Discovery
bigimg: /img/pecanstreet.jpg
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

**Output:**
![log](/img/log.png#log)

### 2. Naive Bayes

- GridSearchCV to find the best_estimator and best_parameter
- Print the classification_report
- Plot confusion_matrix
- Plot roc_auc_score 

**Output:**
![naiv](/img/naiv.png#naiv)





### 3. Test Harness

- Define a Validation Dataset
- Deploy a Method for Model Evaluation  

```
split_point = len(series) - 68
dataset, validation = series[0:split_point], series[split_point:]
print('Dataset %d, Validation %d' % (len(dataset), len(validation))) 
dataset.to_csv('dataset.csv')
validation.to_csv('validation.csv')
```
Dataset 297, Validation 68

