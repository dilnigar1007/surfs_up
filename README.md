# Surfs_Up Challenge

## Purpose
W. Avy wanted to open up a ice-cream shop in Oahu, but before starting anything he wanted to do an analysis on weather year round, specifically June and December, so it gives him an idea of how the weather is in summer June and winter December. We filtered our data to June and December conducted two separate analysis. Results showing below. 
![June Temperature](https://github.com/dilnigar1007/surfs_up/blob/main/June%20Temperature.png)
![December Temperature](https://github.com/dilnigar1007/surfs_up/blob/main/December%20Temperature.png)

## Results
There are three key differences between the weather data in June and December: 1) Maximum temperatures are about the same in two months being somewhere between 83 and 85, but minimum temeperature in December is 8 degrees lower than what's in June, 64. This shows that June is slightly warmer than December. 2)The average temperature for the two months are slightly different, in June, we have 75 degrees while we have 71 in December. 3)We have 1,700 temperatures captured for June when 1,517 temperatures captured in December, therefore, it is probably not a good idea to compare two dataset while they have different number of samples. But this gives W. Avy enough data to analyze what to do with the ice-cream shop.

## Summary
We can use the following queries to conduct June and December precipitation data. Based on the summary, we know that average precipitation for June is 0.136 while it's 0.217 for December. Also, max precipitation for December is 6.42 and 4.43 for June. This indicates that June has less rainy weather than December.
```
June_prcp = []
June_prcp = session.query(Measurement.date, Measurement.prcp).\
filter(extract('month', Measurement.date) == 6).all()
June_df = pd.DataFrame(June_prcp, columns=['date', 'June Precipitation'])
June_df.set_index(June_df['date'], inplace=True)
June_df.describe()
```
```
December_prcp = []
December_prcp = session.query(Measurement.date, Measurement.prcp).\
filter(extract('month', Measurement.date) == 12).all()
December_df = pd.DataFrame(December_prcp, columns=['date', 'December Precipitation'])
December_df.set_index(December_df['date'], inplace=True)
December_df.describe()
```
![June Prcp](https://github.com/dilnigar1007/surfs_up/blob/main/June%20Prcp.png)
![December Prcp](https://github.com/dilnigar1007/surfs_up/blob/main/December%20Prcp.png)
