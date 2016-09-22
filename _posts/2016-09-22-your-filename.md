---
published: false
layout: post
---
## A New Post

Probability and the Art of Modeling Uncertainty

[MITx+6.008](https://courses.edx.org/courses/course-v1:MITx+6.008.1x+3T2016/courseware/1__Probability_and_Inference/intro_prob/?child=first)


PROBABILITY AND THE ART OF MODELING UNCERTAINTY (COURSE NOTES)

Since probability effectively corresponds to a fraction, it is a value between 0 and 1. Of course, we can have impossible events that have probability 0, or events that deterministically happen and thus have probability 1. Each time we model uncertainty in the world, there will be some underlying experiment (such as flipping a coin in our running example). An event happens with probability q∈[0,1] if in a massive number of repeats of the experiment, the event happens roughly a fraction q of the time; more repeats of the experiment make it so that the fraction gets closer to q.

Some times, an underlying experiment cannot possibly be repeated. Take for instance weather forecasting. Whereas we could actually physically flip a coin many times to repeat the same experiment, we cannot physically repeat a real-life experiment for what different realizations of tomorrow's weather will be. We could wait until tomorrow to see the weather, but then we would need a time machine to go back in time by one day to repeat and see what the weather is like tomorrow (and this assumes that there's some inherent randomness in tomorrow's weather)! In such a case, our only hope is to somehow model or simulate tomorrow's weather given measurements up to present time.

### **A good model**

Different people could model the same real world problem differently! Throughout the course, a recurring challenge in building computer programs that reason probabilistically is figuring out how to model real-world problems. **A good model** — even if not actually accurate in describing, for instance, the science behind weather — enables us to make **good predictions**.

Once a weather forecaster has anchored some **way of modeling or simulating weather**, then if it claims that there's a 30% chance of rain tomorrow, we could **interpret** this as saying that using their way of simulating tomorrow's weather, in roughly 30% of simulated results for tomorrow's weather, there is rain.

A probability is a number that is at least 0 and at most 1.

There is only one way to model tomorrow's weather. False: Different people can model weather differently, leading to different forecasts.

Let's say I have a coin that, when tossed, is heads with probability 0.7. Select all the statements below which are true.

If we flip the coin 10 times, it is possible that none of them are heads. 
As we increase the number of times we flip the coin, the fraction of coin flips that are heads becomes closer to 0.7.

If we flip the coin 10 times, it is indeed possible that none of them are heads. In fact, even if we flip the coin 1,000,000 times, it is still possible that none of them are heads albeit such an outcome is extremely unlikely (by the end of this first section of the course, you'll be able to calculuate just how unlikely). In particular, it does not have to be the case that with 1,000 flips, there will be exactly 700 heads, or that even with 1,000,000 flips, there will be exactly 700,000 heads. However, as we increase the number of flips, the fraction of coin flips that are heads will indeed become closer to 0.7.


**TWO INGREDIENTS TO MODELING UNCERTAINTY (COURSE NOTES)**

When we think of an uncertain world, we will always think of there being some underlying experiment of interest. To model this uncertain world, it suffices to keep track of two things:

The set of all possible outcomes for the experiment: this set is called the **sample space** and is usually denoted by the Greek letter Omega Ω.
(For the fair coin flip, there are exactly two possible outcomes: heads, tails. Thus, _Ω={heads,tails}_.)

**The probability of each outcome**: for each possible outcome, assign a probability that is at least 0 and at most 1.
(For the fair coin flip, P(heads)=12 and P(tails)=12.)

Notation: Throughout this course, for any statement S, “P(S)" denotes the probability of S happening.

In Python:

> model = {'heads': 1/2, 'tails': 1/2}
In particular, we see that we can model uncertainty in code using a Python dictionary. The sample space is precisely the keys in the dictionary:

> sample_space = set(model.keys())
{'tails', 'heads'}
Of course, the dictionary gives us the assignment of probabilities, meaning that for each outcome in the sample space (i.e., for each key in the dictionary), we have an assigned probability:

> model['heads']
0.5
> model['tails']
0.5
A few important remarks:

- The sample space is always specified to be **collectively exhaustive**, meaning that every possible outcome is in it, and **mutually exclusive**, meaning that once the experiment is run (e.g., flipping the fair coin), **exactly** one possible outcome in the sample space happens. It's impossible for multiple outcomes in the sample space to simultaneously happen! It's also impossible for none of the outcomes to happen!

- Probabilities can be thought of as fractions of times outcomes occur; thus, probabilities are nonnegative and at least 0 and at most 1.

- If we add up the probabilities of all the possible outcomes in the sample space, we get 1.
(For the fair coin flip, P(heads)+P(tails)=12+12=1.)

Some intuition for this: Consider the coin flipping experiment. What does the fraction of times heads occur and the fraction of times tails occur add up to? Since these are the only two possible outcomes (and again, recall that these outcomes are exclusive in that they can't simultaneously occur, and exhaustive since they are the only possible outcomes), these two fractions will always sum to 1. For a massive number of repeats of the experiment, these two fractions correspond to P(heads) and P(tails); the fractions sum to 1 and so these probabilities also sum to 1.


Recall that for each key in a Python dictionary, there is an associated value. A Python dictionary stores a valid probability distribution when the values are each at least 0 and at most 1; moreover, when we add up the values for all the keys, the sum is equal to 1.


How a sample space is chosen is not unique. As a more involved example, we could even have a sample space that consists of two fair six-sided dice being thrown, where we basically discard all the information about the second die's outcome to reason about the first die. We could also add junk outcomes that are assigned probability 0. However, in general, it's best to keep the sample space as simple as possible to solve the problem at hand.

Suppose we use the sample space {1,2,3,4,5,6}. Write the Python dictionary that encodes a valid probabilistic model for the fair die roll experiment using this sample space. (Your answer should be the Python dictionary itself, and not the dictionary assigned to a variable, so please do not include, for instance “model =" before specifying your answer. Also please be accurate with your fractions up to 5 decimals.)

Assign each outcome probability 1/6: {1: 1/6, 2: 1/6, 3: 1/6, 4: 1/6, 5: 1/6, 6: 1/6}

### **PROBABILITY SPACES (COURSE NOTES)**

At this point, we've actually already seen the most basic data structure used throughout this course for modeling uncertainty, called a finite probability space (in this course, we'll often also just call this either a probability space or a probability model):

A finite probability space consists of **two ingredients**:

- a sample space Ω consisting of a finite (i.e., not infinite) number of collectively exhaustive and mutually exclusive possible outcomes

- an assignment of probabilities: for each possible outcome ω∈Ω, we assign a probability P(outcome ω) at least 0 and at most 1, where we require that the probabilities across all the possible outcomes in the sample space add up to 1:

∑ω∈ΩP(outcome ω)=1.
 
Notation: As shorthand we occasionally use the tuple “(Ω,P)" to refer to a finite probability space to remind ourselves of the two ingredients needed, sample space Ω and an assignment of probabilities P. As we already saw, in code these two pieces can be represented together in a single Python dictionary. However, when we want to reason about probability spaces in terms of the mathematics, it's helpful to have names for the **two pieces**.

Why finite? Of the **two pieces making up a finite probability space (Ω,P)**, the sample space Ω being finite is a fairly natural constraint, corresponding to how we typically work with Python dictionaries where there is only a **finite number of keys**. As we'll see, finite probability spaces are already extremely useful in practice. Pedagogically, **finite probability spaces** also provide a great intro to probability theory as they already carry a wealth of intuition, much of which carries over to a more complete story of general probability spaces!

### **TABLE REPRESENTATION (COURSE NOTES)**

A probability space is a data structure in that we can always visualize as a table of nonnegative entries that sum to 1. Let's see a concrete example of this, first writing the table out on paper and then coding it up.

Example: Suppose we have a model of tomorrow's weather given as follows: sunny with probability 1/2, rainy with probability 1/6, and snowy with probability 1/3. Here's the probability space, shown as a table:

 	 				Probability
 	sunny			1/2
	Outcome	rainy	1/6
 	snowy			1/3
Note: This a table of 3 nonnegative entries that sum to 1. The rows correspond to the sample space Ω={sunny,rainy,snowy}.

We will often use this table representation of a probability space to tell you how we're modeling uncertainty for a particular problem. It provides the simplest of visualizations of a probability space.

Of course, in Python code, the above probability space is given by:

prob_space = {'sunny': 1/2, 'rainy': 1/6, 'snowy': 1/3}
A different way to code up the same probability space is to separately specify the outcomes (i.e., the sample space) and the probabilities:

outcomes = ['sunny', 'rainy', 'snowy']
probabilities = np.array([1/2, 1/6, 1/3])
The i-th entry of outcomes has probability given by the i-th entry of probabilities. Note that probabilities is a vector of numbers that we represent as a Numpy array. Numpy has various built-in methods that enable us to easily work with vectors (and more generally arrays) of numbers.



### ADDENDUM: MORE ON SAMPLE SPACES

In the video, we saw that a sample space encoding the outcomes of 2 coin flips encodes all the information for 1 coin flip as well. Thus, we could use the same sample space to model a single coin flip. However, if we really only cared about a single coin flip, then a sample space encoding 2 coin flips is richer than we actually need it to be!

When we model some uncertain situation, how we specify a sample space is not unique. We saw an example of this already in an earlier exercise where for rolling a single six-sided die, we can choose to name the outcomes differently, saying for instance "roll 1" instead of "1". We could even add a bunch of extraneous outcomes that all have probability 0. We could add extraneous information that doesn't matter such as "Alice rolls 1", "Bob rolls 1", etc where we enumerate out all the people who could roll the die in which the outcome is a 1. Sure, depending on the problem we are trying to solve, maybe knowing who rolled the die is important, but if we don't care about who rolled the die, then the information isn't helpful but it's still possible to include this information in the sample space.

Generally speaking it's best to choose a sample space that is **as simple as possible for modeling** what we care about solving. For example, if we were rolling a six-sided die, and we actually only care about whether the face shows up at least 4 or not, then it's sufficient to just keep track of two outcomes, "at least 4" and "less than 4".

#### Event

Subset of sample space

### ADDENDUM: CODE FOR DEALING WITH SETS IN PYTHON

In the video, the set operations can actually be implemented in Python as follows:

sample_space = {'HH', 'HT', 'TH', 'TT'}
A = {'HT', 'TT'}
B = {'HH', 'HT', 'TH'}
C = {'HH'}
A_intersect_B = A.intersection(B)  # equivalent to "B.intersection(A)" or "A & B"
A_union_C = A.union(C)  # equivalent to "C.union(A)" and also "A | C"
B_complement = sample_space.difference(B)  # equivalent also to "sample_space - B"

### ADDENDUM: PROBABILITIES WITH EVENTS AND CODE

From the videos, we see that an event is a subset of the sample space Ω. If you remember our table representation for a probability space, then an event could be thought of as a subset of the rows, and the probability of the event is just the sum of the probability values in those rows!

The **probability of an event A⊆Ω** is the sum of the probabilities of the possible outcomes in A:

P(A)≜∑ω∈A P(outcome ω),
 
where “≜" means “defined as".

We can translate the above equation into Python code. In particular, we can compute the probability of an event encoded as a Python set event, where the probability space is encoded as a Python dictionary prob_space:

def prob_of_event(event, prob_space):
    total = 0
    for outcome in event:
        total += prob_space[outcome]
    return total
Here's an example of how to use the above function:

prob_space = {'sunny': 1/2, 'rainy': 1/6, 'snowy': 1/3}
rainy_or_snowy_event = {'rainy', 'snowy'}
print(prob_of_event(rainy_or_snowy_event, prob_space))




In general, suppose that a probability space has m (not infinite) different possible outcomes, i.e., the sample space Ω has size |Ω|=m. How many events are there, in terms of m?

There are 2^m possibilities. To count the number of events, note that to form each event, we go through each of the m possible outcomes and we either include the outcome or not. Thus, the total number of possible events is:

2 (whether we include the first outcome or not) multiplied by
2 (whether we include the second outcome or not) multiplied by 
... 
finally multiplied by 2 (whether we include the m-th outcome or not) 
= 2m.



### A FIRST LOOK AT “RANDOM VARIABLES"

Follow along in an IPython prompt.

We continue with our weather example.

> prob_space = {'sunny': 1/2, 'rainy': 1/6, 'snowy': 1/3}


We can simulate tomorrow's weather using the above model of the world. Let's simulate two different values, one (which we'll call W for "weather") for whether tomorrow will be sunny, rainy, or snowy, and another (which we'll call I for “indicator") that is 1 if it is sunny and 0 otherwise:

> random_outcome = comp_prob_inference.sample_from_finite_probability_space(prob_space)
 W = random_outcome
 if random_outcome == 'sunny':
     I = 1
 else:
     I = 0
     
     
     
Print out the variables W or I to see that they take on specific values. Then re-run the above block of code a few times.

You should see that W and I change and are random (following the probabilities given by the probability space).

This code shows something that's of key importance that we'll see throughout the course. Variables W and I store the values of what are called random variables.




### RANDOM VARIABLES (COURSE NOTES)

To mathematically reason about a random variable, we need to somehow keep track of the full range of possibilities for what the random variable's value could be, and how probable different instantiations of the random variable are. The resulting formalism may at first seem a bit odd but as we progress through the course, it will become more apparent how this formalism helps us study real-world problems and address these problems with powerful solutions.

To build up to the formalism, first note, computationally, what happened in the code in the previous part.

First, there is an underlying **probability space** (Ω,P), where Ω={sunny,rainy,snowy}, and

P(sunny)=1/2,P(rainy)=1/6,P(snowy)=1/3.
A **random outcome** ω∈Ω is **sampled using the probabilities given by the probability space** (Ω,P). This step corresponds to an **underlying experiment happening**.

Two random variables are generated:

W is set to be equal to ω. As an equation:

W(ω)=ωfor ω∈{sunny,rainy,snowy}.
This step perhaps seems entirely unnecessary, as you might wonder “Why not just call the random outcome W instead of ω?" Indeed, this step isn't actually necessary for this particular example, but the formalism for random variables has this step to deal with what happens when we encounter a random variable like I.

I is set to 1 if ω=sunny, and 0 otherwise. As an equation:

I(ω)={1if ω=sunny,0if ω∈{rainy,snowy}.
Importantly, multiple possible outcomes (rainy or snowy) get mapped to the same value 0 that I can take on.

We see that random variable W maps the sample space Ω={sunny,rainy,snowy} to the same set {sunny,rainy,snowy}. Meanwhile, random variable I maps the sample space Ω={sunny,rainy,snowy} to the set {0,1}.

**In general:**

Definition of a **“finite random variable"** (in this course, we will just call this a “random variable"): Given a finite probability space (Ω,P), a finite random variable X is a mapping from the sample space Ω to a set of values X that random variable X can take on. (We will often **call X the “alphabet" of random variable X**.)

For example, random variable W takes on values in the alphabet {sunny,rainy,snowy}, and random variable I takes on values in the alphabet {0,1}.

Quick summary: There's an underlying experiment corresponding to probability space (Ω,P). Once the experiment is run, let ω∈Ω denote the outcome of the experiment. Then the random variable takes on the specific value of X(ω)∈X.

Explanation using a picture: Continuing with the weather example, we can pictorially see what's going on by looking at the probability tables for: the original probability space, the random variable W, and the random variable I:


![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/cdb0d997cac4daf2d612e86780ce72bf/asset-v1:MITx+6.008.1x+3T2016+type@asset+block/images_sec-random-variables-main.png)

These tables make it clear that a “random variable" really is just **reassigning/relabeling what the values are for the possible outcomes in the underlying probability space** (given by the top left table):

- In the top right table, random variable W does not do any sort of relabeling so its probability table looks the same as that of the underlying probability space.

- In the bottom left table, the random variable I**relabels/reassign**s “sunny" to 1, and both “rainy" and “snowy" to 0. Intuitively, since two of the rows now have the same label 0, it makes sense to just combine these two rows, adding their probabilities (16+13=12). This results in the bottom right table.

**Technical note:** Even though the formal definition of a finite random variable doesn't actually make use of the probability assignment P, the probability assignment will become essential as soon as we talk about how probability works with random variables.



### RANDOM VARIABLES NOTATION AND TERMINOLOGY (COURSE NOTES)

In this course, we denote **random variables with capital/uppercase letters, such as X, W, I**, etc. We use the phrases “probability table", “probability mass function" (abbreviated as PMF), and “probability distribution" (often simply called a distribution) to mean the same thing, and in particular we denote the probability table for X to be pX or pX(⋅).

We write pX(x) to denote th**e entry of the probability tabl**e that has label x∈X **where X is the set of values that random variable X takes on**. Note that we use lowercase letters like x to denote variables storing nonrandom values. We can also look up values in a probability table using specific outcomes, e.g., from earlier, we have pW(rainy)=1/6 and pI(1)=1/2.

Note that we use the same notation as in math where a function f might also be written as **f(⋅)** to explicitly indicate that it is the function of one variable. Both f and f(⋅) refer to a function whereas f(x) refers to the value of the function f evaluated at the point x.

As an example of how to use all this notation, recall that a probability table consists of **nonnegative entries that add up to 1**. In fact, each of the entries is at most 1 (otherwise the numbers would add to more than 1). For a random variable X taking on values in X, we can write out these constraints as:

0≤pX(x)≤1for all x∈X,∑x∈XpX(x)=1.
 
Often in the course, if we are making statements about all possible outcomes of X, we will omit writing out the**alphabet X explicitly**. For example, instead of the above, we might write the following equivalent statement:

0≤pX(x)≤1for all x,∑xpX(x)=1.



U and V have the same PMF but they are associated with different probability spaces.


In general, for a real-valued function g (i.e., it maps real numbers to real numbers), is g(f(W)) a random variable?

Yes: g just relabels the outcome labels of the probability table for f(W).


### RELATING TWO RANDOM VARIABLES (COURSE NOTES)

At the most basic level, inference refers to using an observation to reason about some unknown quantity. In this course, the observation and the unknown quantity are represented by random variables. The main modeling question is: **How do these random variables relate**?

Let's build on our earlier weather example, where now another outcome of interest appears, the temperature, which we quantize into to possible values “hot" and “cold". Let's suppose that we have the following probability space:



![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/fc8b9dcd3da199d28417f753515a153a/asset-v1:MITx+6.008.1x+3T2016+type@asset+block/images_sec-joint-rv-prob-space.png)

You can check that the nonnegative entries do add to 1. If we let random variable W be the weather (sunny, rainy, snowy) and random variable T be the temperature (hot, cold), then notice that we could rearrange the table in the following fashion:


![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/84055de694b43918005bc1e7555be4aa/asset-v1:MITx+6.008.1x+3T2016+type@asset+block/images_sec-joint-rv-rearrange-table.png)

When we talk about two separate random variables, we could view them either as a single “super" random variable that happens to consist of a pair of values (the first table; notice the label for each outcome corresponds to a pair of values), or we can view the two separate variables along their own different axes (the second table).

The first table tells us what the underlying probability space is, which includes what the sample space is (just read off the outcome names) and what the probability is for each of the possible outcomes for the underlying experiment at hand.

The second table is called a **joint probability table** pW,T for random variables W and T, and we say that random variables W and T are **jointly distributed** with the above distribution. Since this table is a rearrangement of the earlier table, it also consists of nonnegative entries that add to 1.

The joint probability table gives probabilities in which W and T co-occur with specific values. For example, in the above, the event that “W=sunny" and the event that “T=hot" co-occur with probability 3/10. Notationally, we write

pW,T(sunny,hot)=P(W=sunny,T=hot)=310.
 
**Conceptual note**: Given the joint probability table, we can easily go backwards and write out the first table above, which is the underlying probability space.

**Preview of inference**: Inference is all about answering questions like “if we observe that the weather is rainy, what is the probability that the temperature is cold?" Let's take a look at how one might answer this question.

First, if we observe that it is rainy, then we know that “sunny" and “snowy" didn't happen so those rows aren't relevant anymore. So the **space of possible realizations of the world has shrunk to two options** now: (W=rainy,T=hot) or (W=rainy,T=cold). But what about the probabilities of these two realizations? It's not just 1/30 and 2/15 since these don't sum to 1 — by observing things, **adjustments can be made to the probabilities of different realizations but they should still form a valid probability space.**

Why not just scale both 1/30 and 2/15 by the same constant so that they sum to 1? This can be done by dividing 1/30 and 2/15 by their sum:

hot:130130+215=15,cold:215130+215=45.
 
Now they sum to 1. It turns out that, given that we'ved observed the weather to be rainy, these are the correct probabilities for the two options “hot" and “cold". Let's formalize the steps. We work backwards, first explaining what the the denominator “130+215=16" above comes from.

prob_table = {('sunny', 'hot'): 3/10,
     ('sunny', 'cold'): 1/5,
     ('rainy', 'hot'): 1/30,
     ('rainy', 'cold'): 2/15,
     ('snowy', 'hot'): 0,
     ('snowy', 'cold'): 1/3}


prob_W_T_dict = {}
 for w in {'sunny', 'rainy', 'snowy'}:
     prob_W_T_dict[w] = {}

 prob_W_T_dict['sunny']['hot'] = 3/10
 prob_W_T_dict['sunny']['cold'] = 1/5
 prob_W_T_dict['rainy']['hot'] = 1/30
 prob_W_T_dict['rainy']['cold'] = 2/15
 prob_W_T_dict['snowy']['hot'] = 0
 prob_W_T_dict['snowy']['cold'] = 1/3

 comp_prob_inference.print_joint_prob_table_dict(prob_W_T_dict)
 
 
import numpy as np
 prob_W_T_rows = ['sunny', 'rainy', 'snowy']
 prob_W_T_cols = ['hot', 'cold']
 prob_W_T_array = np.array([[3/10, 1/5], [1/30, 2/15], [0, 1/3]])
 comp_prob_inference.print_joint_prob_table_array(prob_W_T_array, prob_W_T_rows, prob_W_T_cols)
 
 
 
 
prob_W_T_rows = ['sunny', 'rainy', 'snowy']
 prob_W_T_cols = ['hot', 'cold']
 prob_W_T_row_mapping = {label: index for index, label in enumerate(prob_W_T_rows)}
 prob_W_T_col_mapping = {label: index for index, label in enumerate(prob_W_T_cols)}
 prob_W_T_array = np.array([[3/10, 1/5], [1/30, 2/15], [0, 1/3]])
 
 
 Some remarks: The 2D array representation, as we'll see soon, is very easy to work with when it comes to basic operations like summing rows, and retrieving a specific row or column. The main disadvantage of this representation is that you need to store the whole array, and if the alphabet sizes of the random variables are very large, then storing the array will take a lot of space!

The dictionaries within a dictionary representation allows for easily retrieving rows but not columns (try it: write a Python function that picks out a specific row and another function that picks out a specific column; you should see that retrieving a row is easier because it corresponds to looking at the value stored for a single key of the outer dictionary). This also means that summing a column's probabilities is more cumbersome than summing a row's probabilities. However, a huge advantage of this way of representing a joint probability table is that in many problems, we have a massive joint probability table that is mostly filled with 0's. Thus, the 2D array representation would require storing a very, very large table with many 0's, whereas the dictionaries within a dictionary representation is able to only store the nonzero table entries. We'll see more about this issue when we look at robot localization in the second section of the course on inference in graphical models.





### MARGINALIZATION: SUMMARIZING RANDOMNESS (COURSE NOTES)

Given a joint probability table, often we'll want to know what the probability table is for just one of the random variables. We can do this by just summing or “marginalizing" out the other random variables. For example, to get the probability table for random variable W, we do the following:

![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/e53a4844dc2d68449d3fccc92cde813e/asset-v1:MITx+6.008.1x+3T2016+type@asset+block/images_sec-joint-rv-marg-rows.png)


We take the joint probability table (left-hand side) and compute out the row sums (which we've written in the margin).

The right-hand side table is the probability table pW for random variable W; we call this resulting probability distribution the marginal distribution of W (put another way, it is the distribution obtained by marginalizing out the random variables that aren't W).

In terms of notation, the above marginalization procedure whereby we used the joint distribution of W and T to produce the marginal distribution of W is written:

pW(w)=∑t∈TpW,T(w,t),
 
where T is the set of values that random variable T can take on. In fact, throughout this course, we will often omit explicitly writing out the alphabet of values that a random variable takes on, e.g., writing instead

pW(w)=∑tpW,T(w,t).
 
It's clear from context that we're summing over all possible values for t, which is going to be the values that random variable T can possibly take on.

As a specific example,

pW(rainy)=∑tpW,T(rainy,t)=pW,T(rainy,hot)⏟1/30+pW,T(rainy,cold)⏟2/15=16.
 
We could similarly marginalize out random variable W to get the marginal distribution pT for random variable T:

![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/1d0a8c49d5f68c4e702538b4005d6485/asset-v1:MITx+6.008.1x+3T2016+type@asset+block/images_sec-joint-rv-marg-cols.png)

(Note that whether we write a probability table for a single variable horizontally or vertically doesn't actually matter.)

As a formula, we would write:

pT(t)=∑wpW,T(w,t).
 
For example,

pT(hot)=∑wpW,T(w,hot)=pW,T(sunny,hot)⏟3/10+pW,T(rainy,hot)⏟1/30+pW,T(snowy,hot)⏟0=13.
 
In general:

**Marginalization:** Consider two random variables X and Y (that take on values in the sets X and Y respectively) with joint probability table pX,Y. For any x∈X, the marginal probability that X=x is given by

pX(x)=∑y pX,Y (x,y).



For two random variables U and V that take on values in the same alphabet, we say that U and V have the same distribution if pU(a)=pV(a) for all a. 





