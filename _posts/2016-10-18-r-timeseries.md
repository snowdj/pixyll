---
published: false
layout: post
---
## R and timeseries

[datacamp](https://campus.datacamp.com/courses/manipulating-time-series-data-in-r-with-xts-zoo/introduction-to-extensible-time-series-using-xts-and-zoo-for-time-series?ex=7). 


Time based indices
100xp
xts objects get their power from the index attribute that holds the time dimension. One major difference between xts and most other time series objects in R is the ability to use any one of various classes that are used to represent time. Whether POSIXct, Date, or some other class, xts will convert this into an internal form to make subsetting as natural to the user as possible.

a <- xts(x = 1:2, as.Date("2012-01-01") + 0:1)
a[index(a)]
We'll get into more detail on subsetting xts objects in a later chapter. For now you can simply use date objects to index appropriate rows from your time series. You can think of this as effectively matching the rownames you see in the object. This works as anticipated for time objects because the rownames are really dates!

For this exercise you'll create two time series using two different time classes. You will then subset each object using the other object's index.
