---
published: true
layout: post
---
## R Programming



http://r4ds.had.co.nz/


R有一系列的資料分析pipeline packages 稱作 tidyverse
(dplyr、tidyr、ggplot2、readr、tibble、purrr ...)
Hadley的演講 - "Data Science with R" 解釋了tidy data、Functional programming的理念，以及何以對data analysis有助益：
https://www.youtube.com/watch?v=K-ss_ag2k9E
--
tidyverse
https://blog.rstudio.org/2016/09/15/tidyverse-1-0-0/
--
The tidy tools manifesto
https://mran.microsoft.com/…/tidyv…/vignettes/manifesto.html
--
R, at its heart, is a functional programming (FP) language
http://adv-r.had.co.nz/Functional-programming.html
--
Data Analysis pipeline:
ggplot2, for data visualization.
dplyr, for data manipulation.
tidyr, for data tidying.
readr, for data import.
purrr, for functional programming.
tibble, for tibbles, a modern re-imagining of data frames.
--
hms, for times.
stringr, for strings.
lubridate, for date/times.
forcats, for factors.
--
Data import:
DBI, for databases.
haven, for SPSS, SAS and Stata files.
httr, for web apis.
jsonlite for JSON.
readxl, for .xls and .xlsx files.
rvest, for web scraping.
xml2, for XML.
--
Modelling:
modelr, for simple modelling within a pipeline
broom, for turning models into tidy data

### 
[RProgrammingForResearch](https://geanders.github.io/RProgrammingForResearch/exploring-data-1.html)

### Logical Indexing

v[v>0]

v[confidence >0]

v[v>confidence]

v[v<0] = c(100, 200)  \# recycling

v[v<0] = v[v<0] + c(100, 200)  \# recycling


#### Matrix A


A[]


works for Matlab too.


### Googlevis

[Analyzing World Bank data with WDI, googleVis Motion Charts](https://www.r-bloggers.com/analyzing-world-bank-data-with-wdi-googlevis-motion-charts/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+RBloggers+%28R+bloggers%29)
