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

Plot a histogram of the petal lengths of his 50 samples of Iris versicolor using matplotlib/seaborn's default settings. Recall that to specify the default seaborn s


tyle, you can use sns.set(), where sns is the alias that seaborn is imported as.

The subset of the data set containing the Iris versicolor petal lengths in units of centimeters (cm) is stored in the NumPy array versicolor_petal_length. In the video, Justin plotted the histograms by using the Pandas library and indexing the dataframe to extract the desired column. Here, however, you only need to use the provided NumPy array.

As Justin did in the video, be sure to assign your plotting statements (except for plt.show()) to the dummy variable _. This is in line with the Pythonic convention and prevents unnecessary output from being displayed.

Import matplotlib.pyplot and seaborn as their usual aliases (plt and sns).
Use Seaborn to set the plotting defaults.
Plot a histogram of the Iris versicolor petal lengths using plt.hist() and the provided NumPy array versicolor_petal_length.
Show the histogram using plt.show().

```
# Import plotting modules
import matplotlib.pyplot as plt
import seaborn as sns

# Set default Seaborn style
sns.set()

# Plot histogram of versicolor petal lengths
_=plt.hist(versicolor_petal_length)

# Show histogram
plt.show()

```

#### Axis labels!

. Now, add axis labels to the plot using plt.xlabel() and plt.ylabel(). Don't forget to add units and assign both statements to _. The packages matplotlib.pyplot and seaborn are already imported with their standard aliases. This will be the case in what follows, unless specified otherwise.

Instructions
Label the axes. Don't forget that you should always include units in your axis labels. Your yy-axis label is just 'count'. Your xx-axis label is 'petal length (cm)'. The units are essential!
Redraw the plot constructed in the above steps using plt.draw(). Like with plt.show(), you do not need to assign this to _.



```
# Label axes

plt.xlabel('petal length (cm)')
plt.ylabel('count')

# Show histogram
plt.draw()
plt.show()
```


#### Adjusting the number of bins in a histogram

The histogram you just made had ten bins. This is the default of Matplotlib. The "square root rule" is a commonly-used rule of thumb for choosing number of bins: choose the number of bins to be the square root of the number of samples. Plot the histogram of Iris versicolor petal lengths again, this time using the square root rule for the number of bins. You specify the number of bins using the bins keyword argument of plt.hist().

The plotting utilities are already imported and the Seaborn defaults already set. The variable you defined in the last exercise, versicolor_petal_length, is already in your namespace.

Instructions
Import NumPy as np. This gives access to the square root function, np.sqrt().
Determine how many data points you have using len().
Compute the number of bins using the square root rule.
Be sure to convert the number of bins to an integer.
Generate the histogram and make sure to use the bins keyword argument and assign the result to _.
Hit submit to plot the figure and see the fruit of your labors!


