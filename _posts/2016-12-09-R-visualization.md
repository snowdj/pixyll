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

 ![](http://lh6.ggpht.com/-ONlugp32B3o/VHwNdsi3EcI/AAAAAAAA9dI/b9DWnqncHFA/mount-wellington%25255B5%25255D.jpg?imgmax=800)

One way to look at the topographic data is via a heatmap. The heatmap's color pattern visualizes how the height of the volcano's surface fluctuates within this 10m by 10m grid.

Alternatively, you could visualize the data by making a 3D surface plot. Namely, plotly visualizations don't actually require a data frame. This makes chart types that accept a z argument especially easy to use if you have a numeric matrix such as our volcano dataset.

Let's try to create that heatmap and 3D surface plot.

Instructions
Create two interactive plots using the volcano dataset:

For one the type of trace is a heatmap.
For the other surface since you also want to see a 3D representation.
  
```
# Load the `plotly` library
library(plotly)

# Your volcano data
str(volcano)

# The heatmap
plot_ly(z = ~volcano, type = "heatmap")

# The 3d surface map
plot_ly(z = ~volcano, type = "surface")
```
  
  
#### ggplot2, the interactive dimension

ggplot2 is probably one of the most well known graphing libraries for R. With ggplotly() from plotly, you can now convert your ggplot2 plots into interactive, web-based versions. 

Try it yourself!

Converting a ggplot2 chart to an interactive chart is fairly easy. First you create the ggplot2 graph and next you call ggplotly(). Like this:
```
qplot(carat, price, data = diamonds, 
                   colour = clarity)
ggplotly()
```

Instructions
The mtcars data frame is available in your workspace. Use geom_point() for your plot:

Using ggplot2, map wt onto the x aesthetic, mpg onto the y aesthetic, and cyl onto color.
Use ggplotly() to make your plot interactive.  
```
# Create the ggplot2 graph
ggplot(mtcars, aes(x = wt, y = mpg, col = cyl)) +
  geom_point()

# Make your plot interactive
ggplotly()
```
 
 #### An interactive airport map
 
Ever wonder how some data scientists make these beautiful geographical maps? This exercise shows you how they do it.

A map provides an easy way to visualize how a measurement varies across a geographic area or the level of variability within a region. An example of such a map is provided on the right. Run the first part of the code and you will see a map of the USA showing the most trafficked airports. Hover over each block to see the name of the airport, city, state and number of arrivals.

Let's highlight the most important pieces in the code:

To the lat and lon arguments your provide information regarding the latitude and longitude of the airports locations.
With add_markers() you can add trace(s) to a plotly visualization
In geo you set the reference between the provided geospatial coordinates and a geographic map (e.g. usa)
In layout() you modify the layout of a plotly visualization. For example, with title you tell plotly what title you want to appear above your plot.
Instructions
Based on the code of the "Most trafficked US airports map", create a world map that maps all commercial airports in the world (airports).
For a map of the world, the scope is the world.
Each airport should be represented by a circle and on hover you should see the AirportID, City and Country of that aiport.
The color of the airport circle should depend on the country.


```
# Most Trafficked US Airports
g <- list(
  scope = 'usa',
  showland = TRUE,
  landcolor = toRGB("gray95")
)

plot_geo(airport_traffic, lat = ~lat, lon = ~long) %>%
  add_markers(
    text = ~paste(airport, city, state, paste("Arrivals:", cnt), sep = "<br />"),
    color = ~cnt, symbol = I("square"), size = I(8), hoverinfo = "text"
  ) %>%
  colorbar(title = "Incoming flights<br />February 2011") %>%
  layout(
    title = 'Most trafficked US airports<br />(Hover for airport)', geo = g
  )


# Commercial Airports WorldWide
str(airports)

# Mapping all commercial airports in the world
g <- list(
  scope = 'world',
  showland = TRUE,
  landcolor = toRGB("gray95")
)

plot_geo(airports, lat = ~Latitude, lon = ~Longitude) %>%
  add_markers(
    text = ~paste(AirportID, City, Country, sep = "<br />"),
    color = ~Country, symbol = I("circle"), size = I(3), hoverinfo = "text", colors = "Set1"
  ) %>%
  layout(
    title = 'Commercial Airports Worldwide', geo = g
  )
```

### Sliding into the final exercise

For the final exercise in this course you will implement a range slider to a stock graph.

On the right you see the code for a plotly graph to which a range slider is added using rangeslider(). The plot looks at a time series USAccDeaths that gives the monthly totals of accidental deaths in the USA. Make sure to run the code in your console.

Loaded in, you will find a dataset on Apple's stock price: apple_stock_price. Let's now visualize this stock price over time using an interactive plotly chart. Make sure to add a range slider.

Instructions
Chart Apple's time-series data in R using apple_stock_price. Use the provided sample code.
Make sure to add a range slider

```
# Monthly totals of accidental deaths in the USA
plot_ly(x = time(USAccDeaths), y = USAccDeaths) %>% 
  add_lines() %>%
  rangeslider()

# Apple Stock Price
str(apple_stock_price)


# Apple Stock Price With Rangeslider
plot_ly(apple_stock_price, x = ~Date) %>%
  add_lines(y = ~AAPL.Adjusted, name = "Apple") %>% 
  rangeslider() %>% 
  layout(
    title = "Stock Price Apple",
    xaxis = list(title = "Date"),
    yaxis = list(title = "Price"))
```



## GGplot2


#### 　Adding details to a plot using point shapes, color, and reference lines
　
Adding additional details to your explanatory plots can help emphasize certain aspects of your data. For example, by specifying the pch and col arguments to the plot() function, you can add different point shapes and colors to show how different variables or subsets of your data relate to each other. In addition, you can add a new set of points to your existing scatterplot with the points() function, and add reference lines with the abline() function.

```
# Load the MASS package
library(MASS)

# Plot Max.Price vs. Price as red triangles
plot(Cars93$Price, Cars93$Max.Price, pch = 17, col = 'red')

# Add Min.Price vs. Price as blue circles
points(Cars93$Price, Cars93$Min.Price, col = "blue", pch = 16)

# Add an equality reference line with abline()
abline(a = 0, b = 1, lty = 2)
```
#### Creating multiple plot arrays
 
You can plot multiple graphs on a single pane using the par() function with its mfrow parameter. For example, par(mfrow = c(1, 2)) creates a plot array with 1 row and 2 columns, allowing you to view two graphs side-by-side. This way, you can compare and contrast different datasets or different views of the same dataset. 


 the original representation of the variables that we have in a dataset is not always the best one for visualization or analysis. By representing the original variables in log scale, for example, we can better see and understand the data.
