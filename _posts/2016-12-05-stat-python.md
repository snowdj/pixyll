---
published: false
layout: post
title: Statistical thinking in Python
category: statistics
tags:
  - python
  - stat
---
## A New Post


[statistical-thinking-in-python](https://campus.datacamp.com/courses/statistical-thinking-in-python-part-1/graphical-exploratory-data-analysis?ex=3)

**Exploratory data analysis** is detective work. 1
There is no excuse for failing to plot and look. 2
The greatest value of a picture is that it forces us to notice what we never expected to see. 3
It is important to understand what you can do before you learn how to measure how well you seem to have done it.


**Advantages of graphical EDA**

It often involves converting tabular data into graphical form. 1
If done well, graphical representations can allow for more rapid interpretation of data. 2

There is no excuse for neglecting to do graphical EDA.

While a good, informative plot can sometimes be the end point of an analysis, it is more like a beginning: it helps guide you in the quantitative statistical analyses that come next.



## Plot sns

a classic data set collected by botanist Edward Anderson and made famous by Ronald Fisher, one of the most prolific statisticians in history. Anderson carefully measured the anatomical properties of samples of three different species of iris, Iris setosa, Iris versicolor, and Iris virginica. The full data set is available as part of scikit-learn. Here, you will work with his measurements of petal length.

Plot a histogram of the petal lengths of his 50 samples of Iris versicolor using matplotlib/seaborn's default settings. Recall that to specify the default seaborn style, you can use sns.set(), where sns is the alias that seaborn is imported as.

The subset of the data set containing the Iris versicolor petal lengths in units of centimeters (cm) is stored in the NumPy array versicolor_petal_length. In the video, Justin plotted the histograms by using the Pandas library and indexing the dataframe to extract the desired column. Here, however, you only need to use the provided NumPy array.

As Justin did in the video, be sure to assign your plotting statements (except for plt.show()) to the dummy variable _. This is in line with the Pythonic convention and prevents unnecessary output from being displayed.

