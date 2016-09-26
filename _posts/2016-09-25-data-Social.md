---
published: true
layout: post
---
## Data Science for Social research

 [course-v1:MITx+14.310x+3T2016](https://courses.edx.org/courses/course-v1:MITx+14.310x+3T2016/courseware/58cc4fe6fa994e3397a82a9329a7e7ae/5e9578b5bbcb4744975a3d093a407bae/).
 
 The chart does seem to show that use of glyphosate and the number of cases of autism have both increased over time. However, based on this evidence we cannot confidently conclude that increased glyphosate use has caused an increase in autism. There could be many other factors not captured in this chart that have led to the increase in glyphosate use over time and to the increase in cases of autism over time.
 
 
 Professor Duflo presents various examples that demonstrate that caution should be used in collecting, presenting, and interpreting data, since it can sometimes be deceitful. One chart shows some kind of relationship between glyphosate and the number of cases of autism, while another shows some kind of relationship between organic food sales and cases of autism. Professor Duflo makes the point that researchers could focus on or drop certain portions of data in order to show support for whatever explanation or story they have in mind.
 
 
 Better scores and higher income earned are examples of direct effects of education, and hence are not considered to be positive externalities of education. One example of a positive benefit of education would be if parents that were highly educated children make better health and nutrition choices for their children, in turn positively investing in the next generation as a result. Better-educated children that become politicians or businesspeople as adults may create policies or businesses that better help their communities, another potential spillover benefit of education beyond the direct impact on the child’s educational and occupational outcomes themselves.
 
 
 Reverse causality and hidden/omitted variables are discussed in class as reasons that we should use caution before concluding that higher education leads to higher GDP. There could be other third factors that contribute to higher incomes as well as higher education levels which are not included in this simplistic model. There could also be some reverse correlation at play, where it is not necessarily the case that higher education leads to higher income, but rather than higher levels of income lead to higher education levels. In this example of outcomes as complex as national GDP per capita and education levels, there are likely many interrelated factors and interactions at play beyond what is included in this simplistic model.
 
 
 If we are able to control for a wide range relevant variables, this should allow us to better isolate the relationship of interest. However the difficulty is to be sure we have controlled for all the relevant variables.
 
  When running many regressions in a data set, there is the risk of “overfitting”: finding patterns by random chance in a particular data set that would not be found elsewhere because they are not real. We will see later in the course how this can be avoided, with a model (the position traditional econometrics take) or with statistical techniques (the position of Machine Learning)
  
  
  
  In the lecture we discuss the differences between causation and correlation, and the potential risks of confounding the two.
  Ideally to identify the causal effect of the mita, we would compare two equal regions that only differ on the presence of this labor institution. Given the large changes in the altitude across the black boundary, it is likely that other variables that affect development could also change. Therefore, comparing regions within and outside the grey boundary is a better idea since it is expected that they are more similar and that the main differences in long-run development variables are more attributable to the presence of the mita.
  
  
  Since the shaded area inside the boundary is darker, this implies that consumption levels are lower and the stunting rate is higher in the regions with mita presence. From Question 3 we argue that the grey boundary allowed us to identify a causal effect, since the regions across the boundary were very similar in other geographic characteristics. Thus, the maps imply a negative effect of the mita in the long run.
  
  
  ![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/97dbc2fd64d61b4d117f5b117cfd03e3/asset-v1:MITx+14.310x+3T2016+type@asset+block/PSET01_02_2.png)
  
  In the lecture, Professor Duflo presented Michael Greenstone and coauthors’ research, where the relationship between pollution and the distance to the Huai river had two different visualizations: (1) a map similar to the ones in Figure 2, (2) a two-dimensional plane of the data. The latter showed the degree to the north in the x-axis and the level of pollution in the y-axis. Suppose that we were trying to do a similar visualization here. To simplify the plot, we only take the boundary in the south. Assume that the x-axis corresponds to the degree in the north, and that we normalize the boundary to zero. It might be helpful to make some drawings for a better visualization of the plot.
  
  
  
  
  Camacho & Conover (2011) document manipulation of a targeting system for social welfare programs in Colombia. Take a look at the following figure, which shows two histograms: the black arrows present the histogram for a poverty score (lower numbers mean being poorer) that was calculated using the same data the Government collected to target social welfare programs – where only individuals with a poverty score below 48 were eligible to receive most of these programs. The blue bars correspond to the histogram reconstructing this poverty score using other data sources that were not used by the Government for this purpose.
  
  
  ![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/e4675a77bfc8e7141c4eb18ad920ac72/asset-v1:MITx+14.310x+3T2016+type@asset+block/PSET01_03.png)
  
  The first statement is true since the histogram with the black arrows is to the left of the one with the blue bars. In addition, the plot shows bunching exactly in 48 (the social welfare eligibility score used by the government) which is not there looking in the blue histogram. Since the data set that was used by the Government to determine social program eligibility is shown with the black arrows, and this pattern is not found in alternative data sources, this suggests some sort of manipulation of social welfare targeting.
  
  
  Continuing with Colombia, www.laramaciudadana.com is a blog that publishes quantitative information about different topics of national interest. Their objective is to inform public policy debate by collecting data on these controversial topics and displaying it to a general audience. Their most recent project uses satellite photos to map deforestation and evaluate industrial reforestation efforts in the country. 
  
  
  
  The map is presented in Figure : the red dots show the locations where satellites detected deforestation activities, and the yellow dots give an overview of the industrial reforestation efforts made by the Government in recent years. Take a close look at the map.
  
  ![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/496701b130fd46a8dde72d39f650dc27/asset-v1:MITx+14.310x+3T2016+type@asset+block/PSET_01_04.png)
  
  
  
  During the introductory lecture, Professor Duflo discussed that human capital externalities are one potential explanation for the fact that the relationship between schooling and output at the country level is larger than the relationship between an additional year of schooling and income at the individual level. She also argued that some of these externalities could stem from teaching or exchanging ideas within a city. A researcher decides to test this idea formally and she correlates the average schooling level in the city with the individual wage of a sample of individuals. She finds a strong positive correlation! From this statistical evidence, could she conclude that there are human capital externalities?
  
  No, from this evidence the she can’t conclude that. There are multiple arguments for this, as the ones discussed in the lecture. For example, there is a selection problem: individuals that are similar are likely to live in the same city. Thus, individuals will not only be similar in their education levels, but also in other variables that change your income. Thus, the correlation attributed to schooling might come from some of these variables.
  
  In R every time you perform an operation with a missing value, you’ll get as a result a missing value as well.
  
  In order to get the vector without those missing values, we can identify the position in which they are located. We can choose then the ones without those missing values by using the code age[c(1, 2, 3, 4, 6, 7, 8, 9, 10, 12)]. We can try to simplify this, by just telling R to omit those positions where they are located, and this is possible using two different ways: age[-c(5, 11)], and age[c(-5, -11)]. We can even simplify this more, and use the is.na function, asking first where are the missing values and then using the negation symbol !. Then, we can do this by age[!is.na(age)].
