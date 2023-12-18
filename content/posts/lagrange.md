---
title: "Lagrange Multipliers"
date: 2023-10-02T00:28:30-04:00
draft: false
list: true
summary: "Lagrange multipliers a la Feynman"
color: "#5B9279"
math: true
---

## What are Lagrange Multipliers

I mentioned Lagrange multipliers in my last post, so I thought it would be particularly fitting to give them their own explanation post. So here we go.

In brief. Lagrange multipliers are a way of taking constraints and making them costs, they're traditionally used in constrained optimization problems.

### Imagine

You've just been given $50 to buy lunch for you and your friends. You know what everyone wants, but you only have enough to buy 5 full meals, and there's 7 of you. Your goal is to make sure everyone gets something to eat, and you're all as full as possible.

In this context your goal is what you are optimizing (Pretend for the sake of the argument that you can "measure" how full people are). This could be expressed mathematically. Something like:

$$\sum \text{"Fullness" for each person} $$

Lets say that fullness is represented by the function *f* and each person is $p_{i}$. Then we have:

$$\sum_{i=1}^{7} f(p_i)$$ 

Let's call this summation *F* and say it is a function of the items you get. Cool so you just maximize this sum by choosing a bunch of food items I. Right?

In the unconstrained case yes, you'd take a derivative set it equal to zero and find the inflection point. But in this case there's a problem. The best set of items will probably just be a bunch of meals. That would make everyone as full as possible, *but* it would go over budget.

In this case the budget is our constraint. We can express it mathematically as something like:

$$\sum_{i \in I} cost(i) \leq \$50 $$

In English, the sum of the costs of all the items has to be less that $50. But now we have two equations, and imagine if we had a more complicated constraint or series of constraints. We could end up with quite a few equations.

Lagrange multipliers let us combine these into a single equation. Let's back up a bit. Our goal is to find the set of items $I$ that maximizes group fullness $F$, mathematically something like this:

$$ \underset{I}{\argmax} \quad F(I)$$

Notationally this means the same thing as above, find the argument I that maximizes the function F. 

We can incorporate our constraint by adding it to our argmax function. Effectively, our goal is twofold to maximize fullness *and* to maximize our remaining money. Interestingly enough, this won't change our choice but will enforce the constraint. If we modify our argmax to look like:

$$\underset{I}{\argmax} \quad F(I) + \lambda (50 - C(I))$$

Where C is that summation of costs from before, we implicitly get a solution that prioritises fulfilling our constraint. To solve problems like these we use a similar approach to before. We take the derivative or gradient set it equal to zero and solve from there. The largest distinction is that now, we have an additional $$\lambda$$ term to solve for. But fear not, we also have an additional equation to solve for this additional variable.

The sequence for solving these problems is usually to find this lamba first as a function of your other variables and substitute it in to the previous equations. Rather than writing out examples here I'll direct you to [Wikipedia](https://en.wikipedia.org/wiki/Lagrange_multiplier#Examples) where there are a bunch of good examples with single and multiple constraints.

The sign of $\lambda$ will depend on your constriaint type and if you are maximizing or minimizing. For example if you constraint is $\leq$ and you are maximizing, you want the $\lambda$ to be negative. Imagine what behaviour you want to penalize and what sign would make your optimization worse when that behviour occurs and you should get an idea of the sign you want.

Our example with sets is a little weird as well, typically these operate on functions but pretend that I is an number corresponding to a restaurant special and you get the same idea.

Anyways, that's Lagrange multipliers as I understand them. If you catch a mistake or have a good explanation shoot me an [email](mailto:snibo13@gmail.com) and I'll try to fix it.

Cheers.


