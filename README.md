# Surfs Up and Ice Cream!

A potential investor is interested in my Hawaiian Surf and Ice Cream shop. This person has been burned by weather patterns in the past. They have a weather data they want analyzed for the island we are interested in. This data will be used to present to other investors as well. The final analysis was done on the weather in June and December to determine if this would work as an all year venture or seasonal. 

## Overview of the statistical analysis:

The summary statistics from June and Dec can be seen below:

![image](https://user-images.githubusercontent.com/87042597/139777197-834e7d7c-a127-4c23-acf8-147a52880ccf.png) ![image](https://user-images.githubusercontent.com/87042597/139777231-21a428c6-416b-4ba1-a5d6-c14727ad1df8.png)

The main points of interest were the average, max, and quartile temperatures from the two months.

## Results:

- The mean temperatures of these two months are almost within 1 standard deviation of each other.
- High temperatures will likely drive ice cream sales, and we can see that the June max of 85 is only slightly higher than the Dec max of 83. We can also see that the 50 percentile temps for June and Dec are 75 and 71 respectively. This demonstrates that while slightly cooler, most days in December are above 70 degrees. 
- If the temperatures are too low, it will likely lead to lower ice cream sales along with fewer surfers. We can see that the lower quartile for December shows 69 degrees. 

## Summary:
Overall the temperatures are fairly steady year round and the business model seems viable based on the temperature. Another major factor would be the precipiation in these months. For the temperature analysis, we used the following queries:
```
session.query(Measurement.date, Measurement.tobs).filter(extract('month', Measurement.date)==6).all()
session.query(Measurement.date, Measurement.tobs).filter(extract('month', Measurement.date)==12).all()
```
Where the '12' or '6' in the ```filter(extract('month', Measurement.date)==12).all()``` section correspond to the month value.

To perfrom the same analysis on the precipitaion, we would run the following two queries to extract the data:
```
session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==6).all()
session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==12).all()
```

Then set each to a variable, and find the statistical data via the .describe() method.
