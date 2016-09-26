---
published: true
layout: post
---
## Optimization


### Stanford CVX
[CVX101 Convex Optimizatio](https://lagunita.stanford.edu/courses/Engineering/CVX101/Winter2014/info/).


### BA

[Optimization Methods for Business Analytics](https://www.edx.org/course/optimization-methods-business-analytics-mitx-15-053x?utm_medium=email&utm_source=sailthru&utm_content=course-announcements-mailing-list&utm_campaign=studentnewsletter-20160830-control&utm_term=Newsletter%20Users%20v2)

[github EDxMIT15053](https://github.com/goedman/EDxMIT15053.jl)

[15-053-optimization-methods-in-management-science](http://ocw.mit.edu/courses/sloan-school-of-management/15-053-optimization-methods-in-management-science-spring-2013/lecture-notes/)
Learn how to use optimization methodologies and modeling approaches to effectively analyze data.


### Open Solver

[opensolver](http://opensolver.org/using-opensolver/)

Can install by the same way we add solver in Excel.

[solverstudio](http://solverstudio.org/download-install/)


The Simplex Method for a maximization problem moves from extreme point to extreme point while increasing the objective value.

The simplex algorithm terminates if this occurs and simplex is guaranteed to terminate at an optimum solution if the problem is feasible.


There are two extreme points: (0, 0) and (0, 1).

There are two extreme rays. The first is the set of points {(λ,0):λ≥0}. The second is the set of points {(λ,1+λ):λ≥0}.


 Because each term of the objective function is guaranteed to be nonnegative, there can be no better solution. Note that (1,2) is not an extreme point of the feasible region. When optimizing a nonlinear function, the optimum is not guaranteed to occur at an extreme point.
 
 A good way to determine which one to store is to solve the problem five additional times. The first problem includes one extra storage unit for chicken. The second problem includes one extra storage unit for beef. And so on. If you do this, you will find that storing 1 extra kg of tofu increases the profit the most. There are other approaches for solving this problem. Next week, we will learn integer programming models. It is possible to write a single model for finding the solution. In the fifth week of this course, you will learn about sensitivity analysis. You can determine the answer from the sensitivity report.
 
 
 The point of Problem 1 is that there are multiple ways of representing integer programs. Some are better in practice because they help the algorithm to find the optimum faster. 
 
 
 
 Select the correct way of modeling this “OR” constraint using linear and integer constraints. 
 
 
 Consider two non-negative integral variables x1 and x2. Suppose that x1≤60 and x2≤50. Model the following constraint using an additional binary variable w:

x1<30 or x2≥20.
 
It is often difficult to work with strict inequalities when modeling MIPs (Mixed Integer/Linear Programs). In this case, x1 is known to be integer valued. We transformed "x1<30" into "x1≤29."

In order to make the constraint x1≤29+M(1−w) redundant when w=0, one needs M to be at least 31. In order to make the constraint x2≥20–Mw be redundant when w=1, we need M to be at least 20.


A basketball coach is trying to come up with a team for the following match. He has a total of 9 players from which he must select 5 . Assume these 5 players will play the whole game. Consider there are three positions players can play: guard, forward, and center. So the team of 5 players will consist of 2 guards, 2 forwards, and 1 center. Players 1,2,3,4,8,9 can play guard, 3,4,5,6,7,8,9 can play forward, and 8,9 can play center.

Consider the decision variables as xi for i∈{1,…,9} so that xi=1 if the coach selects player i , and xi=0 otherwise and examine the IP below. Note that since there is no objective, we state the linear objective as 0.

The IP formulated below requires that we select five players, and that at least two of these five can play guard; at least two can play forward; at least one can play center. If we solve this integer program, and obtain a feasible integer solution, is the solution guaranteed to produce a feasible five person team?






$$\left.\begin{array}{rrcl} \min & 0 \\
                    \text {s.t.:} & & & \\
                    & x_{1} + x_{2} + x_{3} + x_{4}+x_8+x_9 \geq 2 \text{ (2 Guards)}\\
                    & x_{3} + x_{4} + x_{5} + x_{6}+x_{7}+x_{8}+x_9 \ge 2 \text{ (2 Forwards)} \\
                  & x_{8} + x_{9} \ge 1 \text{ (1 Center)} \\
                    & \sum_{i=1}^{9}x_{i} = 5 \text{ (5 players)} \\
                    & x_{i} \in \{0,1\}  \quad \forall i\in\{1,\dots,9\} \text{ (Binary)} \\
                    
                    \end{array}\right\}$$



False

The above IP isn't a correct formulation for our problem. The constraints do ensure that we have 5 players, 2 of which can play guard, 2 forward and 1 center. However, it doesn't guarantee that we can take these five players (from the optimal solution) and assign two of them as forwards, two of them as guards and the remaining player as center.

For instance, consider the solution that picks players 5,6,7,8,9. Players 5, 6 and 7 can only play forward. That means that the two guards and the center must be chosen from the remaining two players, which is impossible.

Historical note: The above false formulation for the basketball problem was (incorrectly) given as the answer by the staff of 15.053 for a quiz in 15.053. If you didn't see why this model was incorrect, you are definitely not alone.


Which of the statements or constraints below is (by itself) equivalent to the statement "If x1=1, then x2=0"?
 
 
 x1 + x2 <=1
 
 
 

