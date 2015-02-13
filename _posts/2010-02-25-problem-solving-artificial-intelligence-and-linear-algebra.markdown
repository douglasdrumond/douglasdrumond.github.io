---
layout: post
title:  "Problem solving, artificial intelligence and computational linear algebra"
date:   2010-02-25 07:23:28
categories: 
tags: 
---

When students come to computer science, it’s hard to motivate them to learn
fundamental mathematics subjects such as linear algebra and numerical calculus.
In this post I intend to spark this motivation through AI and sketch a method
(and some variations) to solve optimization problems.

It’s hard to define AI. We know what _artificial_ means, but what about
_intelligence_ ? Russel and Norvig [[1]](#russel)<a name="back_russel"></a>
presents us four approaches to AI: systems that think like humans, systems that
think rationally, systems that act like humans and systems that act rationally.
Let’s focus on last one, systems that act rationally.  What that means? It
means a rational agent acts so as to achieve the best outcome, i.e., find the
optimal solution.

One technique to solve this kind of problems is searching. For this to work, we
assume an objective is well known and the agent must satisfy it. For example,
the agent wants to find the shortest path from city A to city B. Or the agent
wants to find a route such that the distance travelled is minimal and passes
for several streets only once per street (travelling salesman problem). Or
choose where to play the next move in a game (for example, chess). Some of
those problems have well known algorithms to solve them leading to the optimal
solution (find the shortest path), some has no known deterministic polynomial
algorithms (the travelling salesman problem). In some games, the search for
best play is possible (tic-tac-toe), in others, this is infeasible (chess and
go, for example). Go, for example, has a decision tree so huge it’s virtually
impossible to apply brute force even for just knowing if some position is good
or bad (imagine find the best one).

When the path to goal doesn’t matter, we can use local search algorithms. For
example, to solve the [8-queens
problem](http://en.wikipedia.org/wiki/Eight_queens_puzzle), it doesn’t
matter how we achieve the solution as long as the solution is really achieved.
One kind of problems that presents this behavior is optimization problems. In
optimization problems, we have an objective function _f_ which we want to
minimize.  Suppose it’s a function \\( f:R^n \rightarrow R \\). We want to find
\\( x \in R^n  \\) such that _f(x)_ is minimum. In first calculus course, when
dealing with functions with domain in R, we repeat to exhaustion: derive and
set it equal to zero. In \\( R^n  \\), this is equivalent to solve the equation
\\( \nabla f = 0  \\).  Unfortunately, it’s much more common a case where this
can’t be solved in closed form. 
So we must appeal to numerical methods. One of
these methods is the hill climbing, where, starting from an initial guess,
\\( x\_{0} \\) ,
we update the state via the formula 
\\( x\_{n+1} = x\_{n} - \delta \nabla f(x\_{n}) \\) . 

Yeah! That’s it!  Hmmm… did you notice the trick? It’s all inside delta.
If it’s too small, the algorithm takes longer to converge. If it’s too big, the
algorithm can overlook the minimum :( Wouldn’t it be great if we can adjust the
delta in each step such a big one is taken when far from solution and small
steps when close? There are a lot of methods out there to solve this
optimization problem.  Basically, they differ from each other in the way they
calculate delta. Here I list some:

### Newton

When we learn Newthon’s method for find roots of an equation, we learn each step is updated through following formula:

\\( x\_{n+1} = x\_n - \frac{f'(x)}{f''(x)}  \\)

A direct translation from this to multivariable is also known as Newthon’s method and takes the form:

\\( x\_{n+1} = x\_n - [Hf(x\_n)]^{-1} \nabla f(x\_n)  \\)

where Hf is the Hessian of f:

\\( Hf = \left( \begin{array}{ccc} \frac{\partial^2 f}{\partial e\_1^2} & \frac{\partial^2 f}{\partial e\_1 e\_2} & \cdots \\ \vdots & \ddots &  \\  &  &  \end{array} \right)  \\)

### Gauss-Newton

Under some conditions Hf can be approximated by \\(\nabla f \nabla^T f \\)

### Levenberg

\\( \delta = [\nabla f \nabla^T f + \lambda I]^{-1} \\), so if lambda is big, it’s easy to invert, but one must adjust lambda when too close to solution.

### Levenber-Marquadt

\\( \delta = [\nabla f \nabla^T f + \lambda diag(\nabla f \nabla^T f)]^{-1} \\) or

\\( \delta = [\nabla f \nabla^T f + \lambda (diag(\nabla f \nabla^T f)+I)]^{-1} \\) so we can garantee there’s no zero.


<a name="russel"></a>[[1]](#back_russel) Russel, S. and Norvig, P., Artificial Intelligence: A Modern Approach, 2n Edition, Pearson Education, 2003
