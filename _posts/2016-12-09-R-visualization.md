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

You will work again with the diamonds dataset. The goal is to create a bar chart that buckets our diamonds based on quality of the cut. Next, for each cut, you want to see how many diamonds there are for each clarity variable.


Calculate the number of diamonds for each cut/clarity combination using the count() function from the dplyr package. Assign the result to diamonds_bucket.
Create a chart of type "bar". The color of the bar depends on the clarity of the diamond. Bucket your diamonds by the cut over the x-axis.



```
# Calculate the numbers of diamonds for each cut<->clarity combination
diamonds_bucket <- diamonds %>% count(cut, clarity)

# Replace ___ with the correct vector
plot_ly(diamonds_bucket, x = ~cut, y = ~n, type = "bar", color = ~clarity) 

```