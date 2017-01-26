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
The units of k must be minutes^−1 for the units of y˙, which is Celsius per minute, to agree with the right hand side, which has units of k times units of Celsius.

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
 	|y|	=	e^−P(t)+C	 
 	y	=	±e^−P(t)+C	 
 	y	=	ce^−P(t),	 
where c is any number (we brought back the solution y=0 corresponding to c=0).

Note: If you choose a different antiderivative, it will have the form P(t)+d for some constant d, and then the new e−P(t) is just a constant e^−d times the old one, so the set of all scalar multiples of the function e^−P(t) is the same as before.

Conclusion:

General solution to first-order homogeneous linear ODE. Let p(t) be a continuous function on an open interval I. This ensures that p(t) has an antiderivative P(t). The general solution to y˙+p(t)y=0 is

y=ce^−P(t),
where c is any real number. The parameter c can be determined from an initial condition.


Suppose that xh is a solution to the differential equation x˙+p(t)x=0 and that xh(a)<0 at some time t=a. What does this tell us about the solution function xh?

The solution has the form xh=ce−P(t) for some constant c and some antiderivative P(t) of p(t). The value of e−P(t) is positive, but xh(a)<0, so c must be negative, and then xh=ce−P(t)<0 for all t.


 that the temperature of the soup is modeled by the equation

y˙+ky=kx.
Here we suppose that x=0, so we are solving the homogeneous equation

y˙+ky=0.
General solution to the homogeneous ODE is

y=ce−kt.
Plugging in the initial condition we find

y=ce−kt ⟹ 100=y(0)=ce0 ⟹ c=100.
Therefore

y=100e−kt.

#### 6. Solving inhomogeneous equations: variation of parameters

Variation of parameters is a method for solving inhomogeneous linear ODEs. Recall a first-order inhomogeneous linear ODE in standard linear form:

y˙+p(t)y=q(t).
Let's see how variation of parameters works in the following example.

##### Example 6.1   Solve ty˙+2y=t5 on the interval (0,∞).

Solution:

Step 1. The associated homogeneous equation is ty˙+2y=0, or equivalently, y˙+2ty=0. Solve by separation of variables:

 	dydt	=	−2ty	 
 	dyy	=	−2tdt	 
 	ln⁡|y|	=	−2ln⁡t+C(since t>0)	 
 	y	=	ce−2ln⁡t	 
 	y	=	ct−2.	 
(Here, we have recovered the y=0 solution by allowing c=0.)
Choose one nonzero solution, say yh=t−2.

Step 2. Substitute y=ut−2 into the inhomogeneous equation: the left side is

 	ty˙+2y	=	t(u˙t−2+u(−2t−3))+2ut−2	 
 	 	=	t−1u˙.	 
Note: Observe the cancellation of two terms after the substitution. If you do not observe such a cancellation, you know you have made an computational error. The reason behind this cancellation will be explained shortly.

Using the result of our substitution, the inhomogeneous equation becomes

 	t−1u˙	=	t5	 
Step 3. Solve for u.

 	u˙	=	t6	 
 	u	=	t77+c.	 
Step 4. The general solution to the inhomogeneous equation is

y=ut−2=(t77+c)t−2=t57+ct−2.
(If you want, check by direct substitution that this really is a solution.)

##### Variation of parameters general procedure

Find a nonzero solution, say yh, of the associated homogeneous ODE

yh˙+p(t)yh=0.
Substitute y=uyh into the inhomogeneous equation,   y˙+p(t)y=q(t) to find an equation for the unknown function u=u(t).

 	ddt(uyh)+puyh	=	q	 
 	⟺u˙yh+uy˙h+puyh	=	q	 
 	⟺u˙yh+u(y˙h+pyh)⏟=0	=	q	 
 	⟺u˙yh	=	q	 
Note that the term in parentheses is zero because yh is a solution to the homogeneous differential equation.

Solve u˙=qyh for u(t) by integration.

Once the general u(t) is found, don't forget to multiply it by the homogeneous solution yh(t) to find y=u(t)yh(t), the general solution to the inhomogeneous equation.

The idea is that the functions of the form cyh are solutions to the homogeneous equation; maybe we can get solutions to the inhomogeneous equation by allowing the parameter c to vary, i.e., if we replace it by a non-constant function u(t).



##### Soup example revisited

Suppose in the minestrone soup example,

y˙+ky=kx
the external temperature is constant T. Solve the initial value problem with y(0)=80.

Let's see how to use variation of parameters here to find a general solution.

Recall that the general homogeneous solution is given by y=ce−kt. Because we only need one, we choose yh=e−kt. We start by substituting u(t)yh=ue−kt into our differential equation:

 	u˙e−kt+u(−ke−kt)+kue−kt	=	kT	 
 	u˙e−kt	=	kT	 
 	∫du	=	∫kTektdt	 
 	u	=	Tekt+C	 
Thus the general solution is y=ue−kt=T+Ce−kt.

Solving the initial value problem we find that y=T+(80−T)e−kt.

Note that:

A particular solution to the inhomogeneous ODE is yp=T. This is the solution in which the soup temperature is already in equilibrium with the exterior temperature.

The general solution to the homogeneous ODE is yh=ce−kt.

The general solution to the inhomogeneous ODE is y=T+ce−kt. As t→∞, the soup temperature approaches T no matter what the initial temperature. This makes sense.
