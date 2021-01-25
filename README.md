# Dublin Bus- travel between the attractions in the city
![](https://i.imgur.com/rl7NZOs.jpg)

+ This project presents an application that offer the user an easy way to plane his journey through Dublins attractions by selecting his current location, and 3 attraction he wants to travel to. 
+ The output is:

   + the necessary lines to get from each location to the other (primary station to first attraction, first attraction to second attraction and second attraction to third attraction
   + Some extra information about each attraction (phone number and URL to the attractions website), and a map that show all the above
   + prediction the traveling time between the initial station and the first attraction

![Alt Text](https://i.imgur.com/HiHYp2f.gifv)

**photo of the app and a map example**

In addition, we use streaming data to predict the time for the first ride (the current location to the first attraction).
- The application is based on wx library- to see the interface run app.py throw a machine with GUI.
- You can see the application output without GUI in main.ipynb.

### pre-requirements
-	Databricks machine with Databricks Runtime Version 6.4 (includes Apache Spark 2.4.5, Scala 2.11)
-	Python 3.7 or higher
-	packages from requirements.txt in this repo
Dublin Bus- travel between the attractions in the city

### pre_process.ipynb
-	This notebook creates csv files for the application to use.
-	It uses sample from the static dataset of Dublin and creates the route for each bus-line and finds the stations that are nearby each attraction.
-	In addition, it produces a csv that contain the needed line for each combination of station->attraction. 
-	To run this notebook and reproduce its result, please run the cells in their order (the notebook uses some external dataset that can be found in the data folder). You can find links to those datasets in the references below.

### main.ipynb
-	This notebook presents the applications output in the databricks environment. 
-	It uses the csv that were produce in the pre_process.ipnyb.
-	To run this notebook and reproduce its result, please run the cells in their order. The notebook presents users interface with 'dbutils.widgets' where you can choose the wanted values as input (run cells 14, than choose the first station, run cell 15 and choose the first attraction, and the same for cells 16-17).
-	 You will see the output at the end of the notebook.

### app.py
-	This file contains the users interface code using wx library. Run the file in a machine with GUI and you will se the interface as presented in the beginning of this file.
-	You can update the map presented here by running main.ipnyb with the same inputs. 

### Refrences
-	Attractions in Ireland dataset-  [here](https://data.gov.ie/dataset/attractions)
-	Bus_stops in Dublin dataset-  [here](https://hub.arcgis.com/datasets/EsriIreland::dublin-bus-stops)
-	Shapefile for the bus routes (to draw on map)-  [here](https://hub.arcgis.com/datasets/f3cd2313a3e849a798da2dbc68835c77_7?geometry=-6.362%2C53.319%2C-6.145%2C53.355&selectedAttribute=Shape__Length)
-	Traveling time prediction in scheduled transportation with journey segments. Gal et al. (paper that describes the way we predicted the travelling time)-   [here](https://www.sciencedirect.com/science/article/abs/pii/S0306437915002112)

[Shoval Zandberg](https://github.com/shoval-z)

[Noa Shmulevich](https://github.com/noashmul)
