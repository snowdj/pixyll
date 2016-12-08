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