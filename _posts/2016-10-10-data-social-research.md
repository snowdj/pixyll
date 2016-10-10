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


## Set theory and Probability

Suppose that X is contained in Y. Which of the following diagrams represents the sample space where X is contained in Y? 



![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/73d8809c4cc7ab59205b3f284cde9cc5/asset-v1:MITx+14.310x+3T2016+type@asset+block/L02_S01_01.JPG)



Diagram D represents the case where X is contained in Y. If X is contained in Y, then that means that all possible outcomes of X also belong within the set of possible outcomes of Y. 


In the diagrams below, which of the following shaded areas shows the union of X and Y?


![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/1c516aed5db91ae8996089778c2cb0a1/asset-v1:MITx+14.310x+3T2016+type@asset+block/L02_S01_02.JPG)

Diagram B shows the **union** of X and Y. In contrast, diagram A shows the **intersection** of A and B.




in set theory, the notation for the **intersection of** A and B, A ∩ B, is **equivalently denoted AB** in probability theory.



**Mutually exclusive** refers to two events that cannot both occur or be true at the same time. for example, the two events “It is Tuesday” or “It is Sunday” are mutually exclusive events.

### Defining Probability


 a **probability** as a collection of numbers P(A) where the following three are true: 
 
 (1) P(A) is greater than or equal to zero for all A in the sample space S. 
 
 (2) The sum of each of the P(A) in the sample space S (equivalent to P(S)) is equal to 1. 
 
 (3) For any sequence of disjoint sets A1, A2, A3, … the probability of the union of these events occurring is equal to the union of the probabilities of the events occurring.




The **probability of P(Ac) (A complemen**t) is equivalent to the probability of all events that are not included in event A. This can be a useful fact to keep in mind for cases where you know the probability of all outcomes not included in A, P(Ac), and can use this information to calculate the probability of A. For example, suppose that you know that the probability of rain on a given day is 0.6 or 60%. You can use this information to calculate the probability that it does not rain as 1-0.6, which is equal to 0.4 or 40%. (In the way this example is set up, P(does rain)=0.6 is the complement and P(does not rain)=0.4 is the event of interest.) 


a **“simple sample space**” is defined as a sample space where each of the possible outcomes are equally likely.

Let’s go through an example of a simple sample space. Suppose that you have two spinners which you can spin to point towards red, orange, yellow, green, or blue with equal probability. If you spin each spinner once, what is the probability that both of the spinners will point to blue? 



![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/ff92ff7df44e1c39cc03e3081c0c9cbb/asset-v1:MITx+14.310x+3T2016+type@asset+block/L02_S03_01.JPG)


The probability that both of spinners points to blue is 1/25. If you spin both spinners, there are 5 x 5 = 25 possible combinations. In only one of these combinations do both spinners turn up as blue, so the probability that both spinners point to blue is 1/25. 


Using the same spinner example as before, what is the probability that at least one of the spinners points to blue?

The probability that both of the spinners points to blue is 1/25. This is an example where each of the pairings of two colors is equally likely. Out of 25 possible outcomes, we only have to count the number of outcomes that involve at least one of the spinners pointing to blue. There are 9 such possible combinations, so we know that the probability that at least one of the spinners points to blue is 9/25



![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/499ab9ffc036f239b0e1f90aed5ab93e/asset-v1:MITx+14.310x+3T2016+type@asset+block/L02_S03_04.JPG)



##### Module 2: Fundamentals of Probability, Random Variables, Distributions, and Joint Distributions > Fundamentals of Probability > Probability: Another Example

A factorial for a number X, represented as X!, is the product of all positive integers less than or equal to X. In other words, take the set all positive integers less than or equal to X and multiply them together. If this concept is new to you or you need a refresher on this notation, we encourage you to learn or refresh on some of these concepts before we get too far along with probability and statistics.



 Under sampling without replacement, each time a certain colored ball is removed from the bag, the probability of drawing any of the remaining colors changes. For example, suppose there is one yellow ball. For the first draw, the probability of randomly selecting the yellow ball is 1/50. Suppose you randomly select a green ball during the first draw. When it comes time for the second draw, there are now 49 differently-colored balls in the bag. So, for the second draw, the probability of randomly selecting the yellow ball is 1/49.




###### Ordered and Unordered Arrangements


 Fundamentals of Probability, Random Variables, Distributions, and Joint Distributions > Fundamentals of Probability > Ordered and Unordered Arrangements
 
 
 
 A permutation refers to an ordered arrangements of objects. For example, the example given in class where the sequence of letters and numbers drawn would make up a complete license plate number is a permutation. One way to think of a permutation is as a list in a particular sequence.



A “permutation” refers to an ordered arrangement of objects. In this case, the ordering of handshakes is irrelevant because a handshake between candidate A and candidate B is the same as a handshake between candidate B and candidate A. So we are only interested in counting the total number of handshakes that occur. We should use a combination rule to count the number of handshakes. Specifically, if there are 9 candidates and pairings of 2 candidates shaking hands, there are 9-choose-2 handshakes total.


In the example discussed in class, there are 40! (40-factorial) possible combinations of office arrangements. For the first faculty member to be assigned an office, there are 40 different possible office assignments. Once the first faculty member has been assigned, one office is filled, and there are 39 possible office assignments remaining, and so on. So, this can be represented as 40! since this case is analogous to sampling without replacement.


Suppose that you and a friend are deciding to watch 2 movies one evening. You have 10 movie options. 3 of these are action movies, and 7 are comedies. You and your friend plan to randomly select two of the movies. How many possible outcomes are there if the order you watch them in does not matter?

There are 45 possible pairings of movies. Using the combination rule discussed in class, we can define the sample space as 10 choose 2. In this example, the number of possible combinations is represented by N!/((N-n)!n!) = 10!/(8!2!) = 45.




There are (7 x 6)/2 = 21 outcomes where you and your friend end up watching 2 comedies.



The proper intuition about independent events is that knowing one
event occurred doesn’t give you any information about
whether the other occurred.

 Two events are said to be independent if the fact that one of the events occurs does not impact the probability that the other will occur.
 
 
 
 
 Which of the following are examples of two events or outcomes that are likely to be independent from each other? (Check all that apply)


a. Two siblings are both taller than average .

b. You roll a “4” twice, when rolling a fair die two times 

c. It rains today, and your classmate brings an umbrella to class.

d. The chance that the morning bus arrives late, and the likelihood that your classmate brings a sandwich for lunch 

EXPLANATION

B and D are both examples of plausibly independent events. If you have a fair 6-sided die, the chance of rolling a 4 is 1/6. Regardless of which number is rolled on the first attempt, the chance of rolling a 4 remains 1/6 for the second roll. The two events in D are completely unrelated, so we would not expect the realization of one to impact the probability that the other occurs. In contrast, A and C represent pairs of events or outcomes that are likely not independent. If we know that one of a pair of siblings is very tall, we might increase our expectation of the probability that the second of a pair of siblings is tall. Similarly, if you know that there is a high likelihood of rain, then you might believe that there is a higher probability that your classmate brought an umbrella to class.
 
 
 
 ##### Probability---conditional probability
Recall that knowing that two events are independent means
that the occurrence (or nonoccurrence) of one event doesn’t
tell you anything about the other.
But what if we have two events where the occurrence of one
event actually tells us something relevant about the
probability of another event? How can we alter the
probability of the second event appropriately?
The probability of A conditional on B, P(A|B), is P(AB)/
P(B), assuming P(B) > 0.
 
 
 Conditional probability refers to the case where knowing the outcome of one event tells you something about the likelihood of a second event. However, if the two events are independent, then knowing that A has occurred does not tell you any new information about the probability that B will occur. In this case, the probability that B occurs conditional on A is equal to the probability that B occurs regardless of the outcome of A.
 
 
 The probability that candidate 3 wins the general election is the probability that candidate 3 wins the republican nomination multiplied by the probability that he or she wins the general election conditional on having won the nomination. This is 0.2 * 0.2 = 0.04 or 4%.
 
 
 
  
 
 To calculate the probability that a Republican candidate will win the general election, we do the following calculation: (0.3 * 0.5) + (0.2 * 0.1) + (0.2 * 0.2) + (0.1 * 0.1) + (0.2 * 0.1) = 0.24 or 24%.

P(R) = P(c1)*P(R|c1) + P(c2)*P(R|c2) + P(c3)*P(R|c3)+ P(c4)*P(R|c4) + P(c5)*P(R|c5)
 
 
We know that the probability of testing positive given that you have the condition is 85% and the probability of testing positive if you do not have the condition is 5%. Furthermore, we know that the probability of having the condition is 1%, so the probability of not having the condition must be 100% - 1% = 99%. Overall, p(t+) = p(t+|c)*p(c) + p(t+|c’)*p(c’) = 0.85 * 0.01 + 0.05 * 0.99 = 0.058, or 5.8%


From above, we know that the probability of testing positive, p(t+), is 5.8% or 0.058. We know the probability of testing positive given that you have the condition, p(t+|c), is 85% or 0.85, and that the probability of having the condition is 1% or 0.01. Using Bayes rule, p(c|t+) = (p(t+|c)*p(c)) / p(t+) = (0.85 * 0.01 ) / 0.058 = 0.1466 = 0.15 or 15%.


Let p(I) denote the probability that you are invited and p(I’) denote the probability that you are not invited. Let p(fs) denote the probability that it is Friday or Saturday and p(fs’) denote the probability that it is not Friday or Saturday. You are given that p(I|fs) = 0.8 and p(I|fs’) = 0.5. You are not given p(fs), but can calculate this as 2/7 = 0.2857 or 29% (two of the possible seven days of the week). Using Bayes rule as before, p(fs|I) = (p(I|fs)*p(fs)) / p(I) = (p(I|fs)*p(fs)) / (p(I|fs)*p(fs) + p(I|fs’)*p(fs’) = (0.8 * 0.2857) / (0.8 * 0.2857 + 0.5 * 0.7143) = 0.39 or 39%.

##### Module 2: Fundamentals of Probability, Random Variables, Distributions, and Joint Distributions > Random Variables, Distributions, and Joint Distributions > Introduction to Random Variables 

A random variable is a real-valued function whose domain is the sample space.


A discrete random variable is a variable that can only take on a finite or countable infinite number of values. Many random variables are integers, but they do not have to be.


The number of books in a box and the number of children in a classroom are classic examples of discrete random variables, because they are integer values. In other words, you can have 1, 2, 3, etc… books in a box but you cannot have 1.12324 books in a box. In principle, the weight of a box of books is not discrete, in that there are infinite possible weights and these are not countable. In contrast, if you have a scale that takes measurements in hundredths of a kilo from 0 to 100, the readings from that scale would be discrete since there are a countable number of possible readings.



A continuous variable refers to a variable that can take on any value within some interval of the real line. The interval can be either bounded (for example, a decimal number from 0 to 25) or unbounded.



















 


















