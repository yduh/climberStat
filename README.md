# Aaalyze the world's largest rock climbing logbook
This is a fun analysis, which aims to make a discussion about some common questions that almost every climber wants to ask. 

First, we wonder how well we can climb and how long it would probably take. Then, influenced by our different heights, we may have different climbing styles or the ways of movements on a route. We can take a look at our heights and compare them to people in the community. Finally, we will look at some popular climbing places, and hope that will give some ideas about your next climbing trip. :climbing:  

So three questions:
* Q1. How long could it take to climb my first 6a, 7a, or 8+?
* Q2. How is my height compared with other climbers?
* Q3. Where are the popular climbing places?

## Overview of the data
The data can be accessed on "[kaggle 8a.nu Climbing Logbook](https://www.kaggle.com/dcohen21/8anu-climbing-logbook)". It was prepared by collecting the information on [8a.nu](https://www.8a.nu) website by web-scraping. The 8a.nu website has one of the world's largest climbing communities online where climbers can record their climbs and check other's ascents here.

The data is provided in SQLite database, collected on Sep 13, 2017. It includes 4 tabular data with information regarding users, their ascents record, grades, type of climbing, body indexes, personal information, etc.

In the study Q1, the rope climbing curves are composed of 96,115 men and 4726 women. Curves on bouldering come from the climbs of 16,850 men 2402 women.
In Q2, we have 25,593 male climbers and 3964 female climbers who left their heights in the information.
And in Q3, we have 2,875,676 rope climbs log and 1,236,202 boulder climbs records.

## Dependencies/Libraries:
Coding in Python3 in Jupyter Notebook IDE, the following libraries are expected: 
* sqlite3
* Numpy
* pandas
* Matplotlib
* Seaborn
* scipy.stats

## Data analysis
### Q1: How long before I can climb on my first 6a, 7a or 8+?
In the following curves, each square and dots represent the outdoor grade for climbers who have climbed outdoors for a given amount of time. By observing the distance between the neighbors on the x-axis, we can calculate the expected time required to push our grades to the next level.

![progress_rope](plot/progress_rope.png)
![progress_bouldering](plot/progress_bouldering.png)

Insights:
1. Like many skills, it will improve rapidly at first, and then the time required to improve will increase. Or instead, I like to see the level up of each grade as a non-linear growth.
2. The two climbing principles may not be completely equivalent in concept, but their curves are highly similar on a growth trend.
3. As you can imagine, the higher the level, the fewer people can climb, so does the error increases. Similarly, we have a smaller group of female climbers, and it makes the overall female prediction errors larger.
4. The difference on progress rate between men and women may exist or may be negligible, however, given the statistical error it has, it would be hard to say. In fact, it actually shows that the individual differences are greater than the gender differences.

### Q2: How is my height compared with most climbers?
According to the order of height, the accumulated proportion plot is drawn and you can see where you are among the community. Then, I mark some Olympic athletes with very different heights upon the plots. 

![MaleHeightCDF](plot/MaleHeightCDF.png)
![FemaleHeightCDF](plot/FemaleHeightCDF.png)

Insights:
1. Cumulative distribution function (CDF) helps to quickly identify which height range you belong to among climbers, but it is not relevant to which height will be beneficial to climbing. It is more to help distinguishing a style or beta version that might be usful to you from others.
2. The medium height of male climbers is 178 cm and that of female is 165 cm. If the distribution fits in a simple Gaussian, the results are 177.8 ±8.0 cm and 164.8 ±7.9 cm respectively. It is also interesting to compare it with [contemporary national average](https://en.wikipedia.org/wiki/Average_human_height_by_country). For example, the height ratio of male to female is about 1.08 in the climbing community, consistent with many countries.

### Q3: Where are the popular climbing places?
The top 3 countries where the most rope climbing routes had been sent are in Spain (22%), USA (10%), and France (9%). Same ranking for bouldering, are USA (30%), France (11%), and Spain (7%). The numbers only indicate which countries have most climbing logs have been recorded in the data. Some countries may have many crags, so there accumulate many climbs. Or it is just that most climbers in this community come from these countries and they climb nearby. So the crags I list below are the most popular within these countries, while it can not guarantee also be the most popular in the world. Moreover, the exact numbers change time by time when we have more climbs.

Nevertheless, when you happen to be in the US or in the East Europe, consider the following places to go:
* Rope climbing: Rodellar	in Spain, Red River Gorge in the US, Céüse in France, and Kalymnos in Greece.  
* Bouldering: Bishop in the US, Fontainbleau in France, and Albarracín in Spain. 


## Documentation:
The analysis is used to make the plots seen in my Medium Article "[How long could it take to climb my first 8a?](https://kate-d.medium.com/how-long-could-it-take-to-climb-my-first-8a-d841f2573518)".   
The code is put in `ClimbingLogbook_Analyses.ipynb`, or easy reading on nbviewer [here](https://nbviewer.org/github/yduh/climberStat/blob/main/ClimbingLogbook_Analyses.ipynb).

## References:
* How long before you get "Good" as bouldering, [kaggle kernel](https://www.kaggle.com/aarontrefler/how-long-before-you-get-good-at-bouldering), by Aaron Trefler
* Plotting progression times per grade, [kaggle kernel](https://www.kaggle.com/durand1/plotting-progression-times-per-grade), by Durand D'souza
* Climber-characteristic-analysis, [gitHub repo](https://github.com/stevebachmeier/climber-characteristic-analysis), by stevebachmeier
