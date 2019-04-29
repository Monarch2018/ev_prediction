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
			    <li class = "selected"><a href="https://monarch2018.github.io/ev_prediction/preprocessing/">Preprocessing</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/timeseries/">Time Series</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/baseline/">Baseline</a></li>
			    <li><a href="https://monarch2018.github.io/ev_prediction/prediction/">Prediction</a></li>
			</ul>
		</div>
	
   </div>

### Merge Vehicle and Nonvehicle Dataset (1:1)

```
# Preprocess two raw datasets
novehicle = pd.read_csv(os.path.join("/content","novehicle.csv"), header = 0, keep_default_na = False)
vehicle = pd.read_csv(os.path.join("/content","metadata.csv"), header = 0, keep_default_na = False)
vehicle['label'] = '1'
novehicle['label'] = '0'
vehicle = vehicle.dropna(how = 'any', axis = 0)
novehicle = novehicle.dropna(how = 'any', axis = 0)
...
# Merge two datasets
capstone = vehicle.append(novehicle, ignore_index = True)
# Export new dataset to google drive and name it 'capstone'
from google.colab import drive
drive.mount('drive')
capstone.to_csv('capstone.csv')
!cp capstone.csv drive/My\ Drive/
...
# Check new dataset
Capstone = importfile(file_id = '1-1lVd9sPctCOOrpxJ8vpf7qf6zhU3EhN')
Capstone = pd.read_csv(os.path.join("/content","capstone.csv"), header = 0, keep_default_na = False)
Capstone.groupby('label').size()
```
![merge](/img/merge.png#merge)



### Feature Engineering
1. Check missing values by using missing_map function
```
# see missing values
missing_map = Capstone.replace(['unknown_0','unknown_1'],np.nan)
msno.matrix(missing_map)
```
![missing](/img/missing.png#missing)

2. Format localhour from 'object' to 'datetime' dtype
```
capstone['localhour'] = pd.to_datetime(capstone['localhour'])
capstone.localhour
```

3. Create timeseries dataset
```
timeseries = captone[['dataid', 'localhour', 'car1', 'use', 'label']]
timeseries.head()
```
![timeseries](/img/timeseries.png#timeseries)

4. import weather dataset and create new feature ssd (by temperature, humidity, wind speed)
- import weather dataset
```
weather = importfile(file_id = '1V1qT6o65vB0XsSFs2a3GL1u6QCJTn0R9') 
weather = pd.read_csv(os.path.join("/content","weather.csv"), header = 0, keep_default_na = False)
weather.head()
```
![weather](/img/weather.png#weather)
- using geopandas to create a GeoDataFrame with Coordinate column
```
weather['Coordinates'] = list(zip(weather.longitude, weather.latitude))
weather = weather[weather['Coordinates'] != (-117.15188500000001, 32.778033)]
weather['Coordinates'] = weather['Coordinates'].apply(Point)
gdf = geopandas.GeoDataFrame(weather, geometry='Coordinates')
world = geopandas.read_file(geopandas.datasets.get_path('naturalearth_lowres'))
# We restrict to North America.
ax = world[world.continent == 'North America'].plot(
    color='white', edgecolor='black')
# We can now plot our GeoDataFrame.
gdf.plot(ax=ax, color='red')
plt.show()
```
![geo](/img/geo.png#geo)


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
