# EV-Charging
![alt text](./images/public-ev-charging-networks-c63e58c0.jpeg "Electric car charging station")

From [Zap-map](https://www.zap-map.com/)

This project was completed as part of the General Assembly immersive data science course.

## Table of Contents
[Background](#Background)  
[Goals of the Project](#Goals-of-the-Project)  
[Data Collection](#Data-Collection)  
[Data Cleaning](#Data-Cleaning)  
[Exploratory Data Analysis](#Exploratory-Data-Analysis) 

## Background
Background
The demand for electric cars has grown exponentially in recent years, with rising environmental pressure, economic incentives and advancements in battery technology driving the transition away from traditional petrol and diesel engines. In January 2023, one out of every five new cars registered in the UK was either a plug-in hybrid vehicle (PHEV) or battery electric vehicle (BEV), representing a significant increase from the previous year. Despite this surge in the number of electric vehicles on the road, there remains a question as to whether the deployment of supporting charging infrastructure is keeping pace with the demand.

The 2021 Competition and Markets Authority (CMA) report highlights the need for charging infrastructure to increase by at least tenfold by 2030. The report also notes the potential risk of "charging deserts" in certain areas across the UK, which makes it evident that the current infrastructure will not be sufficient in the near future. Given this information, it is important to evaluate the effectiveness of the strategy that has been employed until now in deciding the location of charging points. Through this project I aimed to assess the current placement of charging points and determine whether their installation is aligned with areas of high traffic density, where it can be assumed that demand is at its highest.

## Goals of the Project
The hypothesis of this machine learning project is that areas of high traffic flow will correspond with a higher concentration of electric car charging points. In order to test this hypothesis, my project methodology took the following basic outline:
1. Aggregate charging stations in England by location.
2. Determine a metric of traffic flow around each location.
3. Use regression models to determine the coefficients for the traffic variables and assess their significance in predicting the number of charging points per location.

## Data Collection
<img align="right" height="500" src="./images/traffic.png" title="Data collection sites for traffic flow along English motorways">
The data on charging points was sourced from the National Chargepoint Registry (NCR), a government database providing information on publicly accessible charge points within the UK. I then aggregated the data by outcode - the first half of a postal code e.g. ‘NW1’. To determine the factors, other than traffic, that could impact the distribution of charging points, I gathered additional data regarding each outcode. This included data from the Office for National Statistics (ONS), about the local authorities and the rural/urban classification of each area. As the cost of electric vehicles remains high, I was also interested in exploring whether affluence impacted the distribution of charging points. To investigate this, I calculated the average house price per square metre within each outcode using House Price Paid data and Energy Performance of Buildings data.

The crux of the data collection for this project was sourcing the traffic data. Given the talk of "range anxiety" as a major factor preventing people from adopting electric vehicles, I decided to focus on long-range traffic, specifically along motorways. To do this, I web-scraped download links from Highways England, which provided me with over 120,000 CSV files of time-stamped traffic data for various locations along 153 motorways and A-roads in England. I processed this data to determine the average number of cars per minute at over 9000 locations along these roads and used regex to extract the coordinates in longitude and latitude. Finally, using mapbox API, I determined the closest traffic site to each outcode and used the distance and average number of cars to  find a measure of the traffic flow around the outcode. 

## Data Cleaning
Data cleaning included, but was not limited to:

* Removing missing values.
* Standardising the format of variables, e.g. inconsistencies in how the charge point device owner name was written.
* Deriving additional features of interest from the data, which were not originally present in the dataset.
* Performing a sanity check of charge point outcodes against a validated list. Incorrect outcodes were then derived from the longitude and latitude.

## Exploratory Data Analysis
![alt text](./images/charging_plots.png "Charging points in England")
![alt text](./images/charging_dist.png "Distribution of charging points in England")

Initial analysis of the traffic data revealed almost no correlation between the calculated metric of traffic flow and the locations of charging points. This was supported by the findings of the CMA report, which noted the limited number of charging points along motorways relative to demand. Furthermore, the data showed a low proportion of charging points at service stations, which would be the expected location when catering to traffic along major roads.

<p align="center">
  <img src="./images/traffic_relationship.png">
</p>  

Further exploration of other variables through EDA revealed distinct differences between urban and rural areas, as well as between affluent and non-affluent regions. However, the key insight was that the areas with the highest density of charging points corresponded with those governed by councils who received government funding to build EV infrastructure. Although there are multiple factors at play, it appears that public policy has been a key driving force behind the distribution of charging points thus far.

![alt text](./images/rural_urban.png "Distributions of charging points in rural vs urban areas")

<p align="center">
  <img src="./images/london_maps.png">
</p> 





{:style="text-align:center;"}
  ![placeholder](./images/traffic_relationship.png "Relationship between traffic flow and charging points")



![alt text](./images/rural_urban.png "Distributions of charging points in rural vs urban areas")
![alt text](./images/london_maps.png "Charging points in London")




