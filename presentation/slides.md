slidenumbers: true
autoscale: true

# Optimal Auction Design

---

## Context

* Mechanism design: seller maximizing profit.
* How? A nash equilibrium among buyers that leads to highest profit for seller.
* This leads to two fundamental results we have covered in class:
  * Revelation Principle
  * Revenue Equivalence Theorum (in a restricted setting)

---

## Setup

Everything is pretty familiar. We start with a distribution over values defined on a finite interval, which are I.I.D:

$$
f_i : [a_1, b_1] \rightarrow \mathbb{R}^+
$$

We call this private signal $$t_i$$ for each player, which gives us a set of all player signals:

$$
T = t_1,...,t_n
$$

---


## Setup

Expected utility of buyer:

$$
U_i(p, x, t_i) = \int_{T_{-i}} (v_i(t)p_i(t) - x_i(t))f_{-i}(t_{-i})dt_{-i}
$$

Conditional expectation of winning:

$$
Q_i(p, t_i) = \int_{T_{-i}} p_i(t)f_{-i}(t_{-i})dt_{-i}
$$

---


## The Revelation Principle

> Given any feasible auction mechanism, there exists an equivalent feasible direct revelation mechanism which gives to the seller and all bidders the same expected utilities as in the given mechanism.

---

### The Revelation Principle

One of the core requirements built into the definition of feasibility is the the __incentive-compatibility__ conditions:

$$
U_i(p,x,t_i) \geq \int_{T_{-i}} (v(t)p_i(t_{-i},s_i) - x_i(t_{-i}, s_i)) f_{-i}(t_{-i}) dt_{-i}
$$

$$
\forall{i} \in N, \ \forall{t_i} \in [a_i, b_i], \ \forall{s_i} \in [a_i, b_i]
$$

If the player can't gain from lying to herself, the auctioneer can implement the function that maps the players signal to strategy, $$ p: T \rightarrow \mathbb{R}^n $$, into the mechanism of the auction itself, as this function is, by definition, shared by all players.

---

## Revenue Equivalence - Introduction

Core assumption on value function:

$$
v_i(t) = t_i + \sum_{j: j \neq i \in N} e_j(t_j)
$$

Note that this is not what we would expect, it's not a convex combination of ours and others' signals.

---


## Revenue Equivalence - Introduction

$$(p,x)$$ is feasible if and only if the following conditions hold:

$$
\text{if } s_i \leq t_i \text{ then  } Q_i(p, s_i) \leq Q_i(p, t_i), \forall{i} \in N, \forall{s_i, t_i} \in [a_i, b_i]
$$

$$
U_i(p, x, t_i) = U_i(p, x, a_i) + \int_{a_i}^{t_i} Q_i(p, s_i)ds_i, \forall{i} \in N, \forall{t_i} \in [a_i, b_i]
$$

$$
U_i(p,x,a_i) \geq 0, \forall{i} \in N
$$

---

## Revenue Equivalence - Dependence on Value Function

This implies the following about the relationship between our conditional-expectation-of-winning function and the expected utility function:

$$
U_i(p, x, t_i) = U_i(p, x, a_i) + \int_{a_i}^{t_i} \frac{\partial}{\partial s_i}U_i(p, x, s_i)ds_i
$$

$$
U_i(p, x, t_i) = U_i(p, x, a_i) + \int_{a_i}^{t_i} Q_i(p, s_i)ds_i
$$

$$
\frac{\partial}{\partial s_i}U_i(p, x, s_i) = Q_i(p, s_i)
$$

---

## Revenue Equivalence - Dependence on Value Function

Using $$f'(x)$$ to denote $$\frac{\partial}{\partial t_i}$$ to ease notation.

$$
\frac{\partial}{\partial t_i} \int_{T_{-i}} (v_i(t)p_i(t) - x_i(t))f_{-i}(t_{-i})dt_{-i} = \int_{T_{-i}} p_i(t)f_{-i}(t_{-i})dt_{-i}
$$

$$
\frac{\partial}{\partial t_i} v_i(t)p_i(t) - x_i(t) = p_i(t)
$$

$$
v_i(t)p'_i(t) - x'_i(t) = p_i(t) - v'_i(t)p_i(t)
$$

---

### Revenue Equivalence - Statement

> The seller's expected utility from a feasible auction mechanism is completely determined by the probability function p and the numbers $$U_i(p, x, a_i)$$ for all i. That is, once we know who gets the object in each possible situation (as specified by p) and how much expected utility each bidder would get if his value estimate were at its lowest possible level $$a_i$$, then the seller's expected utility from the auction does not depend on the payment function x.

---

## Revenue Equivalence - 2nd Lemma

Previous assumptions allow us to write the seller's utility by:

$$
U_o(p,x) = \int_{T} \bigg( \sum_{i \in N} \bigg( t_i - t_0 - e_i(t_i) - \frac{1 - F_i(t_i)}{f_i(t_i)}) p_i(t) \bigg) f(t) dt + \int_{T}v_0(t)f(t)dt - \sum_{i \in N} U_i(p,x,a)
$$

This is maximized with regards to x when:

$$
\sum_{i \in N} U_i(p,x,a) = 0
$$


---

## Revenue Equivalence - 2nd Lemma

Rewriting our previous constraints:

$$
\int_{T_{-i}} \bigg( p_i(t)v_i(t) - \int_{a_i}^{b_i} p_i(t_{-i}, s_i)ds_i - x_i(t) \bigg) f_{-i} dt_{-i} = U_i(p,x,a_i) \geq 0
$$

Choosing x according to:

$$
x_i(t) = p_i(t)v_i(t) - \int_{a_i}^{t_i} p_i(t_{-i}, s_i)ds_i
$$

---

## Revenue Equivalence - 2nd Lemma

Recall the previous result of our feasible auction:

$$
p'_i(t)v_i(t) - x'_i(t) = p_i(t) - p_i(t)v'_i(t)
$$

And recall our choice for $$x_i$$:

$$
x_i(t) = p_i(t)v_i(t) - \int_{a_i}^{t_i} p_i(t_{-i}, s_i)ds_i
$$

$$
x'_i(t) = p'_i(t)v_i(t) + p_i(t)v'_i(t) - p_i(t)
$$
