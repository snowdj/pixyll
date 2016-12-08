---
published: false
layout: post
title: Data visualization in R
category: visualization
tags:
  - visualization
  - r
  - plotly
---
## plotly-tutorial-plotly-and-r

[plotly-tutorial-plotly-and-r](https://campus.datacamp.com/courses/plotly-tutorial-plotly-and-r/getting-started-with-plotly?ex=2). 


### scatter

```
library(plotly)
# The diamonds dataset
str(diamonds)

# A firs scatterplot has been made for you
plot_ly(diamonds, x = ~carat, y = ~price)

# Replace ___ with the correct vector
plot_ly(diamonds, x = ~carat, y = ~price, color = ~carat)
        
# Replace ___ with the correct vector
plot_ly(diamonds, x = ~carat, y = ~price, color = ~carat, size = ~carat)
```

### bar

You will work again with the diamonds dataset. The goal is to create a bar chart that buckets our diamonds based on quality of the cut. Next, for each cut, you want to see how many diamonds there are for each clarity variable.




Calculate the number of diamonds for each cut/clarity combination using the count() function from the dplyr package. Assign the result to diamonds_bucket.
Create a chart of type "bar". The color of the bar depends on the clarity of the diamond. Bucket your diamonds by the cut over the x-axis.



```
# Calculate the numbers of diamonds for each cut<->clarity combination
diamonds_bucket <- diamonds %>% count(cut, clarity)

# Replace ___ with the correct vector
plot_ly(diamonds_bucket, x = ~cut, y = ~n, type = "bar", color = ~clarity) 

```


### From the bar to the box: the box plot

In the final exercise of this chapter, you will make an interactive box plot in R.

Using plotly, you can create box plots that are grouped, colored, and that display the underlying data distribution. The code to create a simple box plot using plotly is provided on your right.

Note how you use type= "box" in the function plot_ly() to create a box plot. Make sure to run the code (plotly is already loaded in).

Instructions
Create a second, more fancy, box plot using diamonds. The y-axis should represent the price. The color should depend on the cut.
Create a third box plot where you bucket the diamonds not only by cut but also by clarity. The color should depend on the clarity of the diamond.


```
# The Non Fancy Box Plot
plot_ly(y = ~rnorm(50), type = "box")

# The Fancy Box Plot
plot_ly(diamonds, y = ~price, color = ~cut, type = "box")

# The Super Fancy Box Plot
plot_ly(diamonds, x = ~cut, y = ~price, color = ~clarity, type = "box") %>%
  layout(boxmode = "group")
```
  
  
####  Visualizing volcano data

Mount Eden is a volcano in the Auckland volcanic field. The volcano dataset gives topographic information for Mount Eden on a 10m by 10m grid. Run str(volcano) to examine the dataset.

 

One way to look at the topographic data is via a heatmap. The heatmap's color pattern visualizes how the height of the volcano's surface fluctuates within this 10m by 10m grid.

Alternatively, you could visualize the data by making a 3D surface plot. Namely, plotly visualizations don't actually require a data frame. This makes chart types that accept a z argument especially easy to use if you have a numeric matrix such as our volcano dataset.

Let's try to create that heatmap and 3D surface plot.

Instructions
Create two interactive plots using the volcano dataset:

For one the type of trace is a heatmap.
For the other surface since you also want to see a 3D representation.
  