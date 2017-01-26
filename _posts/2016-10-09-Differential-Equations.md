---
published: true
layout: post
---
## Differential Equations

 [Differential Equations](https://classroom.udacity.com/courses/cs222/lessons/48733228/concepts/487091910923).
 
 
 
 
 
 
 
 
 
### Standard linear form

Every first-order linear ODE can be written in standard linear form as follows:

y˙+p(t)y=q(t),
where p(t) and q(t) can be any functions of t.

When the right hand side q(t) is zero, we call the equation homogeneous. An equation that is not homogeneous is inhomogeneous .

 	Homogeneous: y˙+p(t)y	=	0	 
 	Inhomogeneous: y˙+p(t)y	=	q(t)	 
Models that use first order linear ODEs

First-order linear equations are common in modeling. Here are some examples.

Temperature conduction

Concentration diffusion

Radioactive decay

Bank account interest

Simple population growth

In this lecture we will focus in on the first example, and use a model for conduction called Newton Cooling.


#### Example 4.1   My minestrone soup is in an insulating thermos. Model its temperature as a function of time.

Simplifying assumptions:

The insulating ability of the thermos does not change with time.

The rate of cooling depends only on the difference between the soup temperature and the external temperature.

Draw a picture:

![](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/e041e107f3b399b0c8f26a32ff02a74f/asset-v1:MITx+18.031x+1T2017+type@asset+block/images_thermos2.svg)
Identify variables and parameters (with units):

t	time (minutes)
x	external temperature (∘C)
y	soup temperature (∘C)
k	conduction of thermos (to be determined by equation)
Here t is the independent variable, and x and y are functions of t. The conduction k is a parameter of the system determined by the conductivity of the thermos.

Identify input, response, and any initial conditions:

The system is the thermos full of soup.

The input is x, the temperature outside of the thermos.

The response is y, the temperature of the soup inside of the thermos.

We are not given initial conditions in this problem.

Write differential equation:

y˙=k(x−y)
This is Newton's law of cooling : the rate of cooling of an object is proportional to the difference between its temperature and the external temperature. It's very important to get the sign right. When the temperature outside the thermos is smaller than the temperature of the soup, the soup is cooling. We set up the equation this way so that the conductivity constant k is positive.

 	y˙	<	0	 
 	x−y	<	0	 
 	k	>	0	 
The units of k must be minutes−1 for the units of y˙, which is Celsius per minute, to agree with the right hand side, which has units of k times units of Celsius.

Smaller k means better insulation, because smaller k leads to smaller rate of change of temperature. The case k=0 is perfect insulation; the temperature inside the thermos doesn't change at all.

Put into standard linear form: This ODE can be rearranged into standard form:

y˙+ky=kx.
It's a first-order inhomogeneous linear ODE!

Note: Notice that the factor of k is essential in the differential equation for the units to work out. In standard linear form

 	p(t)	=	k	 
 	q(t)	=	kx(t).	 
Note that the right hand side q(t)=kx(t) is not the input. The input signal is x(t). The system response is y(t).


#### 5. Solving homogeneous first-order linear ODEs

Homogeneous first-order linear ODEs can always be solved by separation of variables:

 	y˙+p(t)y	=	0	 
 	dydt+p(t)y	=	0	 
 	dydt	=	−p(t)y	 
 	dyy	=	−p(t)dt	 
Choose any antiderivative P(t) of p(t). Then

 	ln⁡|y|	=	−P(t)+C	 
 	|y|	=	e−P(t)+C	 
 	y	=	±e−P(t)+C	 
 	y	=	ce−P(t),	 
where c is any number (we brought back the solution y=0 corresponding to c=0).

Note: If you choose a different antiderivative, it will have the form P(t)+d for some constant d, and then the new e−P(t) is just a constant e−d times the old one, so the set of all scalar multiples of the function e−P(t) is the same as before.

Conclusion:

General solution to first-order homogeneous linear ODE. Let p(t) be a continuous function on an open interval I. This ensures that p(t) has an antiderivative P(t). The general solution to y˙+p(t)y=0 is

y=ce−P(t),
where c is any real number. The parameter c can be determined from an initial condition.



