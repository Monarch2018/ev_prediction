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
			    <li class = "selected"><a href="https://monarch2018.github.io/ev_prediction/data/">Data</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/preprocessing/">Preprocessing</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/timeseries/">Time Series</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/baseline/">Baseline</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/prediction/">Prediction</a></li>
			</ul>
		</div>
	
   </div>

### Pecan Street Dataport (pgAdmin 4):

![pgAdmin4](/img/pgAdmin4.png#pgAdmin4)


### Dataport link

[Dataport](https://dataport.cloud/) hosts all the data collected via Pecan Street’s water and electricity research.

### University Access Database 
After sign up an account, I successfully got access to the University Access level database which is available to current faculty, staff, and students at a four-year postsecondary educational institution in the U.S. or equivalent-level institution in other nations. 
![university](/img/university.png#university)

The tables I have used are listed below:

#### Metadata (Features: dataid, city, state, car1) 
![metadata](/img/metadata.png#metadata)

#### Other table (electric_vehicle, electricity_egauge_hours, survey_2017_all_participants, weather) 
![list](/img/list.png#list)


### Insight
#### 1. Geographic dataset
{% include Location.html %}

#### 2. Weather dataset
{% include NOAA.html %}

#### 3. Baseline: traning and testing dataset
Manually splite 43 families as training set, 23 families as testing set.
	```
	train_data=pd.read_csv(os.path.join("/content",'train.csv'), index_col =0)
	test_data=pd.read_csv(os.path.join("/content",'test.csv'), index_col =0)
	print(train_data.info(), test_data.info())
	```
	

