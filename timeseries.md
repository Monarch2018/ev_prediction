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
			    <li class = "selected"><a href="https://monarch2018.github.io/ev_prediction/timeseries/">Time Series</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/baseline/">Baseline</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/prediction/">Prediction</a></li>
			</ul>
		</div>
	
   </div>

### Main Process (Deployment)
1. import libraries and methods 
2. import timeseries dataset
3. Family choose
4. Test Harness
4. Persistence
5. Data Anlysis
- Summary Statistics
- Line Plot
- Density Plot
- Box and Whisker Plots
6. ARIMA Models
- Manually Configured ARIMA
- Grid Search ARIMA Hyperparameters
- Review Residence Errors
- Box-Cox Transformed Dataset
7. Model Validation
- Finalize Model
- Make Prediction
- Validate Model

### 1. Import Library and datset
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

### 2. Deploy function which can analyze and predict among 76 families
```
from pandas import read_csv
df = read_csv('timeseries.csv', index_col=2, header = 0, parse_dates=True, squeeze=True)
df.drop(['Unnamed: 0'], axis = 1, inplace = True)

daily_summary = pd.DataFrame()
series = pd.DataFrame()
ids = df.dataid.unique().tolist()

for id in ids:
  daily_summary_id = df[df['dataid'] == id]
  daily_summary['dataid'] = daily_summary_id.dataid.resample('D').max()
  daily_summary['use'] = daily_summary_id.use.resample('D').sum()
  daily_summary['label'] = daily_summary_id.label.resample('D').max()
  series = series.append(daily_summary)
series.dropna(inplace = True)

print('There are totally 76 families, please enter which family you want to predict:')
x = int(input('Enter family number:'))
series = series[series['dataid'] == ids[x-1]]['use']
print("Number %d family's dataid is %d"%(x,ids[x-1]))
```
eg:
![family](/img/family.png#family)

### Dataport link

[Dataport](https://dataport.cloud/) hosts all the data collected via Pecan Street’s water and electricity research.

### University Access Database 
After sign up an account, I successfully got access to the University Access level database which is available to current faculty, staff, and students at a four-year postsecondary educational institution in the U.S. or equivalent-level institution in other nations. 
![university](/img/university.png#university)


### Or some code?

Some code might go here:

```
x <- 5 # Here's some R code
```

What if I just paste the HTML for a plotly plot?

We can do it with a line of markdown that looks like this (without the slashes - I haven't solved that problem just yet...):
```
\{\% include jupyter-basic_bar.html \%\}
```
{% include jupyter-basic_bar.html %}
