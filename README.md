# Dublin Bus- travel between the attractions in the city
![](https://i.imgur.com/rl7NZOs.jpg)

+ This project presents an application that offers the user an easy way to plane his journey through Dublins attractions by selecting his current location and 3 attraction he wants to travel to. 
+ The output is:

   + the necessary lines to get from each location to the other (primary station to first attraction, first attraction to second attraction, and second attraction to third attraction.
   + Some extra information about each attraction (phone number and URL to the attractions website), and a map that shows all the above.
   + prediction of the traveling time between the initial station and the first attraction.
 + As a part of the project we also upload the streaming output to a Data warehouse (we are using Elasticsearch- you can find installation instructions below)

 **<ins>Demonstration of the application</ins>** 

This gif shows what will happen for the following input:

<ins>Initial station:</ins> 14

<ins>First attraction:</ins> Aircoach

<ins>Second attraction:</ins> Merrion Square

<ins>Third attraction:</ins> Blackrock Park

<ins>Input time:</ins> '2017-07-18 12:00:00'

![Alt Text](https://i.imgur.com/HiHYp2f.gif)


The last link will lead to a website with this map:

![](https://i.imgur.com/FbQ93HZ.png)
(to see a gif that shows more details see app_map.gif)


In addition, we use streaming data to predict the time for the first ride (the current location to the first attraction).
- The application is based on wx library- to see the interface run app.py throw a machine with GUI.
- You can see the application output without GUI in main.ipynb.

### pre-requirements
-	Databricks machine with Databricks Runtime Version 6.4 (includes Apache Spark 2.4.5, Scala 2.11)
-	Python 3.7 or higher
-	packages from requirements.txt in this repo

### data.txt
- contains links to the relevant datasets from google drive. the datasets bus_stops and attractions are external datasets that can be found in the references below. the other datasets are the outcome from pre_process.ipynb and are needed for main.ipynb and app.py

### pre_process.ipynb
-	This notebook creates csv files for the application to use.
-	It uses a sample from the static dataset of Dublin and creates the route for each bus-line and finds the stations that are nearby each attraction.
-	In addition, it produces a csv that contains the needed line for each combination of station->attraction. 
-	To run this notebook and reproduce its result, please run the cells in their order (the notebook uses some external dataset that download from google drive- relevant links are in data.txt file). You can find links to those datasets in the references below.

### main.ipynb
-	This notebook presents the application output in the Databricks environment. 
-	It uses the csv that were produce in the pre_process.ipnyb.
-	To run this notebook and reproduce its result, please run the cells in their order.First, select the wanted timestamp in command 1. The notebook presents user interface with 'dbutils.widgets' where you can choose the wanted values as input (run cells 15, then choose the first station, run cell 16 and choose the first attraction and the same for cells 17-18).
-	 You will see the output at the end of the notebook.

### app.py
-	This file contains the user interface code using wx library. Run the file in a machine with GUI and you will see the interface as presented at the beginning of this file.
-	You can update the map presented here by running main.ipnyb with the same inputs. if you won't run it you will get an output that does not use the stream data and therefore does not predict the travel time.

### Elasticsearch + Kibana set up
1. Install docker-compose via: `sudo pip install docker-compose` 
2. Download docker-compose.yml file
3. Within the same directory of the file, execute: `sudo /opt/anaconda3/bin/docker-compose up -d`.
This will build your services using the configurations from docker-compose.yml.
4. After a few moments, you should be able to access your Elasticsearch server on: YOUR_DNS_NAME:9200, and Kibana on: YOUR_DNS_NAME:5601
5. If you want to write to the data warehouse, change the esURL variable in command 27 in main.ipynb to be the private IP of your machine

### References
-	Attractions in Ireland dataset-  [here](https://data.gov.ie/dataset/attractions)
-	Bus_stops in Dublin dataset-  [here](https://hub.arcgis.com/datasets/EsriIreland::dublin-bus-stops)
-	Shapefile for the bus routes (to draw on map)-  [here](https://hub.arcgis.com/datasets/f3cd2313a3e849a798da2dbc68835c77_7?geometry=-6.362%2C53.319%2C-6.145%2C53.355&selectedAttribute=Shape__Length)
-	Traveling time prediction in scheduled transportation with journey segments. Gal et al. (paper that describes the way we predicted the traveling time)-   [here](https://www.sciencedirect.com/science/article/abs/pii/S0306437915002112)

__For more information about the project see slides.html file__

**See you in Dublin!**

[Shoval Zandberg](https://github.com/shoval-z)

[Noa Shmulevich](https://github.com/noashmul)
