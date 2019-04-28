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

<div class='tableauPlaceholder' id='viz1525635704151' style='position: relative'>
				<noscript><a href='#'><img alt='Dashboard 1 ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;ga&#47;gasoline&#47;Dashboard1&#47;1_rss.png' style='border: none' /></a></noscript>
				<object class='tableauViz'  style='display:none;'>
					<param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> 
					<param name='embed_code_version' value='3' /> 
					<param name='site_root' value='' />
					<param name='name' value='gasoline&#47;Dashboard1' />
					<param name='tabs' value='no' />
					<param name='toolbar' value='yes' />
					<param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;ga&#47;gasoline&#47;Dashboard1&#47;1.png' /> 
					<param name='animate_transition' value='yes' />
					<param name='display_static_image' value='yes' />
					<param name='display_spinner' value='yes' />
					<param name='display_overlay' value='yes' />
					<param name='display_count' value='yes' />
					<param name='filter' value='publish=yes' /></object></div>                
					<script type='text/javascript'>                    var divElement = document.getElementById('viz1525635704151');                    var vizElement = divElement.getElementsByTagName('object')[0];                    vizElement.style.width='100%';vizElement.style.height='827px';                    var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                </script>
			<br>
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
