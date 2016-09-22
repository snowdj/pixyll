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