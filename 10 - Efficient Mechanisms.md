10 - Efficient Mechanisms
================

## 10-1 VCG: Definitions

#### The VCG Mechanism

A general way for self-interested agents to choose a social-welfare
maximizing outcome

Works basically everywhere, as long as monetary payments are possible

- Privatization

A government privatizing a public utility like a power plant doesn’t aim
to maximize revenue, but to ensure that the right buyer wins

- Building a Bridge

Businesses on both sides of a river need to decide whether to build a
bridge, and if so how to pay for it

- Scheduling Meetings

Scheduling meetings between people who value times differently and may
not tell the truth

- Buying a Path in a Network

Shipping along privately owned railroads from Hocking Valley Coal Field
to Chicago, 1881

#### A positive result

- Recall that in the quasilinear utility setting, a direct mechanism
  consists of **choice rule** and a **payment rule**

- A **VCG mechanism**:

  - has truth as a dominant strategy (satisfies truthfulness, is
    strategy-proof)

  - makes efficient choices (*not including payments*)

- And, under additional assumptions about the setting, can satisfy:

  - weak budget balance

  - *interim* individual rationality

#### Groves Mechanisms

Definition (Groves mechanism)  
Direct mechanisms, $(\chi, \mathbb{p})$, such that

$$
 \chi(\hat{v}) \in arg \max_x \sum_i \hat{v_i}(x)
\\
\mathbb{p_i} = h_i(\hat{u}_{-i})-\sum_{j \not= i} \hat{v_j}(\chi(\hat{v})
$$

Some people refer these as VCG mechanisms, although that name has more
recently started to be used to refer to a specific mechanism within this
class

#### The Vickrey-Clarke-Groves Mechanism

Definition (A Vickrey-Clarke-Groves (VCG) mechanism, a.k.a. a Pivotal mechanism)  
A **Vickrey-Clarke-Groves mechanism** or a **pivotal mechanism** is a
Groves mechanism $(\chi, \mathbb{p})$, such that

$$
\chi(\hat{v})\in arg \max_x \sum_i\hat{v_i}(x) \\
\mathbb{p_i}(\hat{v})= \max_x \sum_{j \not=i} \hat{v_j}(x) - \sum_{j \not= i} \hat{v_j}(\chi(\hat{v}))
$$

#### VCG discussion

- You get paid everyone’s utility under the allocation that is actually
  chosen
  - except your own, but you get that directly as utility
- Then you get charged everyone’s utility in the world where you don’t
  participate
- Thus you pay your **social cost (** $\mathbb{p_i(\hat{v}})$ is social
  cost for $i$)
- Questions: - who pays 0?
  - agents who don’t affect the outcome - who pays more than 0?
  - (pivotal) agents who make things worse for others by existing - who
    gets paid?
  - (pivotal) agents who make things better for others by existing

#### VCG and Groves Mechanisms: Truthfulness

Theorem  
Truth telling is a dominant strategy under any Groves mechanism
including the pivotal mechanism (a VCG mechanism)

Consider agent $i$’s problem of choosing the best strategy $\hat{v_i}$.
A best strategy for $i$ is solves

$$
\max_{\hat{v_i}}(v_i(\chi(\hat{v})-\mathbb{p}_i(\hat{v_i},\hat{v_{-i}}))
$$

Substituting in the payment function for a Groves mechanism this
becomes:

$$
\max_{\hat{v_i}} \big[ v_i(\chi(\hat{v}))-h_i(\hat{v}_{-i})+\sum_{j \not= i} \hat{v}_j(\chi(\hat{v})) \big]   
$$

Since $h_i(\hat{v}_{-i})$ does not depend on $\hat{v_i}$, it is
sufficient to solve

$$
\max_{\hat{v_i}} \big[ v_i(\chi(\hat{v}))+\sum_{j \not= i}\hat{v_j}(\chi(\hat{v})) \big]
$$

So, $i$ would like to pick a declaration $\hat{v_i}$ that will lead the
mechanism to pick an $x \in X$ which solves

$$
\max_x [v_i(x)+\sum_{j \not= i} \hat{v_j}(x)] \label{eq1}
$$

Under a Groves mechanism,

$$
\chi(\hat{v}) \in arg \max_x [v_i(x)+\sum_{j \not= i} \hat{v_j}(x)]
$$

A Groves mechanism will choose $x$ in a way that solves the maximization
problem in Equation (1) when $\hat{v_i}=v_i$. Thus, truth-telling is a
dominant strategy for agent $i$

#### Groves Uniqueness

Theorem (Green-Laffont)  
Suppose that for all agents any $v_i: X \mapsto \mathbb{R}$ is a
feasible preference. Then an “**efficient**” mechanism
$(\chi,\mathbb{p})$ (such that
$\chi(\hat{v})\in arg \max_x \sum_i \hat{v_i}(x)$ has truthful reporting
as a dominant strategy for all agents and preferences **only if** it is
Groves mechanism:
$\mathbb{p_i}(v)= h(v_{-i})- \sum_{j \not= i} v_j(\chi(v))$

A proof can be found at <https://stanford.edu/~jacksonm/mechtheo.pdf>

#### Summary

- Groves mechanisms, and VCG mechanisms in particular, have nice
  dominant strategy properties

- Agents’ payment include the impact of their announcements on other
  agents

- Internalize the externalities and lead to efficient decisions ($x$’s)

- But may burn payments to do so

## 10-2 VCG: Example

#### Selfish routing example

<img src="images/routing.png" width="325" />

- What outcome will be selected by $\chi$? path $ABEF$

- How much will $AC$ have to pay?

  - The shortest path taking $AC$’s declaration into account has length
    5, and imposes cost -5 on agents other than $AC$. The shortest path
    without $AC$’s declaration also has length 5. Thus,
    $\mathbb{p}_{AC}=(-5)-(-5)=0$

  - This is what we expect, since $AC$ is not pivotal

  - Likewise, $BD,CE,CF$ and $DF$ will all pay zero

- How much will $AB$ pay?

  - The shortest path taking $AB$’s declaration into account has length
    5, and imposes cost 2 on other agents

  - The shortest path without $AB$ is $ACEF$, which has cost 6

  - Thus $\mathbb{p}_{AB}=(-6)-(-2)=-4$

- How much will $BE$ pay? $\mathbb{p}_{BE}=(-6)-(-4)=-2$

- How much will $EF$ pay? $\mathbb{p}_{EF}=(-7)-(-4)=-3$

  - $EF$ and $BE$ have the same costs but are paid differently, Why?

  - $EF$ has more **market power**: for the other agents, the situation
    without $EF$ is worse than the situation without $BE$

## 10-3 VCG: Limitation

#### 1. Privacy

- VCG required agents to fully reveal their private information

- This private information may have value to agents that extends beyond
  the current interaction

  - for example, the agents may know that they will compete with each
    other again in the future

- It is often preferable to elicit only as much information from agents
  as is required to determine the social welfare maximizing choice and
  compete the VCG payments

#### 2. Susceptibility to Collusion

| Agent | $U$ (build road) | $U$ (do not build road) | Payment |
|-------|------------------|-------------------------|---------|
| 1     | **200**          | 0                       | **150** |
| 2     | **100**          | 0                       | **50**  |
| 3     | 0                | 250                     | 0       |

- What happens if agents 1 and 2 both increase their declared valuations
  by \\50

- The choice is unchanged, but both of their payments are reduced

- Thus, while no agent can gain by changing his declaration groups *can*

#### 3. VCG is not Frugal

- VCG can end up paying **arbitrarily more than an agent is willing to
  accept** (or equivalently charging arbitrarily less than an agent is
  willing to pay)

- Consider the effect of $AC$’s cost on the payment to $AB$

  - If the cost of this edge increased to 8, our payment to $AB$ would
    increase to $\mathbb{p}_{AB}=(-12)-(-2)=-10$

  - If the cost were any $x \ge 2$, we would select the path $ABEF$ and
    would have to make a payment to $AB$ of
    $\mathbb{p}_{AB}=(-4-x)-(-2)=-(x+2)$

  - The gap between agents’ true costs and the payments that they could
    receive under VCG is unbounded

Are VCG’s payments at least **close to the cost of the** *second*
**shortest disjoint path**?

<img src="images/notfrugal.png" width="488" />

- The top path has a total cost of $c$

- VCG picks it, pays each of the $k$ agents
  $c(1+\epsilon)-(k-1)\frac{c}{k}$

- Hence VCG’s total payment is $c(1+k\epsilon)$

- For fixed $\epsilon$, VCG’s payment is $\Theta(k)$ times (i.e., only a
  constant away from $k$ times) the cost of the second shortest disjoint
  path

#### 4. Revenue Monotonicity Violated

**Revenue Monotonicity**: revenue **always weakly increases** as agents
are added

| Agent | $U$ (build road) | $U$ (build road) | Payment |
|-------|------------------|------------------|---------|
| 1     | 0                | 90               | 0       |
| 2     | 100              | 0                | 90      |

| Agent | $U$ (build road) | $U$ (do not build road) | Payment |
|-------|------------------|-------------------------|---------|
| 1     | 0                | 90                      | 0       |
| 2     | 100              | 0                       | 0       |
| **3** | 100              | 0                       | 0       |

- Adding agent 3 causes VCG to make the **same choice** but to collect
  **zero revenue**

- Agent 2 could pretend to be two agents and eliminate his payment

#### 5. Cannot Return All Revenue to Agents

- We may want to use VCG to induce agents to report their valuations
  honestly, but may not want to make a profit by collecting money from
  the agents

- Thus, we might want to find some way of **returning the mechanism’s
  profits** back the agents

- However, the possibility of receiving a rebate after the mechanism has
  been run changes the agents’ incentives

- In fact, even if profits are given to a charity that the agents care
  about, or spent in a way that benefits the local economy and hence
  benefits the agents, the VCG mechanism is undermined

- It is possible to return at least some of the revenues to the agents,
  but it must be done very carefully, and in general not all the money
  can be returned

## 10-4 VCG: Individual Rationality and Budget Balance in VCG

Definition (Choice-set monotonicity)  
An environment exhibits **choice-set monotonicity** if
$\forall i , X_{-i} \subseteq X$

- removing any agent weakly decreases - that is, never increases - the
  mechanism’s set of possible choices $X$

Definition (No negative externalities)  
An environment exhibits **no negative externalities** if
$\forall i \forall x \in X_{-i}, v_i(x) \ge 0$

- every agent has zero or positive utility for any choice that can be
  made without his participation

#### Example: road referendum

Consider the problem of holding a referendum to decide whether or not to
build a road

- The set of choices is independent of the number of agents, satisfying
  choice-set monotonicity

- No agent negatively values the project, though some might value the
  situation in which the project is not undertaken more highly than the
  situation is which it is

#### Example: simple exchange

Consider a market setting consisting of agents interested in buying a
single unit of a good such as a share of shock, and another set of
agents interested in selling a single unit of this good. The choices in
this environment are sets of buying-seller pairings (prices are imposed
through the payment function)

- If a new agent is introduced into the market, no previously-existing
  pairings become infeasible, but new ones become possible; thus
  choice-set monotonicity is satisfied

- Because agents have zero utility both for choices that involve trades
  between other agents and no trades at all, there are no negative
  externalities

#### VCG Individual Rationality

Theorem  
The VCG mechanism is *Ex-post* individual rational when the choice set
manotonicity and no negative externalities properties hold

Proof  
All agent truthfully declare their valuations in equilibrium. Then

$$
u_i=v_1(\chi(v)) - (\sum_{j \not = i}v_j(\chi (v_{-i}))\ \sum_{j \not = i} v_j (\chi (v)) \\
= \sum_{i} v_i (\chi (v))-\sum_{j \not = i} v_j (\chi (v_{-1}))
$$

$\chi(v)$ is the outcome that maximizes social welfare, and so the
optimization could have picked $\chi(v_{-i})$ instead (by choice set
monotonicity) Thus,

$$
 \sum_j v_j (\chi(v)) \ge \sum_{j \not = i} v_j(\chi_{-i}) 
$$

furthermore, from no negative externalities

$$
 v_i(\chi(v_{-i})) \ge 0
$$

Therefore

$$
 \sum_j v_i (\chi(v)) \ge \sum_{j } \chi(v_{-i}) 
$$

and thus Equation is non-negative

#### Another property

Definition (No single-agent effect)  
An environment exhibits **no single-agent effect** if
$\forall i,\forall v_{-i}, \forall x \in arg \max_y \sum_y v_j(y)$ there
exists a choice $x'$ that is feasible without $i$ and that has
$\sum_{j \not = i} v_j(x') \ge \sum_{j \not = i}v_j(x)$

Welfare of agents other than $i$ is weakly increased by dropping $i$

Example  
Consider a single-sided auction. Dropping an agent just reduces the
amount of competition, making the other agents better off

#### Good News

Theorem  
The VCG mechanism is weakly budget-balanced when the no single-agent
effect property holds

Proof  
Assume truth-telling in equilibrium. We must show that the sum of
transfers from agents to the center is greater than or equal to zero

$$
\sum_i \mathbb{p_i}(v) = \sum_i (\sum_{j\not=i}v_j(\chi(v_{-1})-\sum_{j \not= i}v_j(\chi(v)))
$$

From the no single-agent effect condition we have that

$$
\forall i \sum_{j \not=i}v_j(\chi(v_{-i})) \ge \sum_{j \not=i}v_j(\chi(v))
$$

Thus the result follows directly

#### More good news

Theorem (Krishra & Perry, 1998)  
In any Bayesian game setting in which VCG is ex post individually
rational, VCG collects at least as much revenue as any other efficient
and ex interim *individually-rational mechanism*

- This is somewhat surprising: does not require dominant strategies, and
  hence compares VCG is as budget balanced as any efficient mechanism
  can be

- A useful corollary: VCG is as budget balanced as any efficient
  mechanism can be

  - it satisfies weak budget balance in every case where any dominant
    strategy, efficient and ex interim IR mechanism is able to

## 10-5 VCG: The Myerson-Satterthwaite Theorem

#### Efficient Trade

- People have private information about the utilities for various
  exchanges of goods at various prices

- Can we design a mechanism that always results in efficient trade?

- Are strikes unavoidable?

#### Simple Exchange Setting

- Exchange of a single unit of an indivisible good

- Seller initially has the item and has a value for it of
  $\theta_S \in [0,1]$

- Buyer has need for the item and has a value for it of
  $\theta_B \in [0,1]$

#### An Example

- The buyer’s value is equally likely to be either 0.1 or 1

- The seller’s value for the good is equally likely to be 0 or 0.9

- Trade should take place for all combinations of values except (0.1,
  0.9)

#### An Example of a Mechanism

- The seller announces a price in\[0,1\]

- The buyer either buys or not at that price

- The seller should say a price of either 0.1 or 1 (presume that buyer
  says yes when indifferent)

- When the seller value is 0:

  - price of .1 lead to sale for sure: expected utility 1

  - price of 1 leads to sale with probability 1/2, expecting utility of
    1/2

  - Better to set the high price

  - *Inefficient trade* (0.1,0) do not trade

- What about other mechanisms?

#### Efficiency, Budget Balance and Individual Rationality

Theorem (Myerson-Satterthwaite)  
There exist distributions on the buyer’s and seller’s valuations such
that; There does not exist any Bayesian incentive - compatible mechanism
is simultaneously efficient, weakly budget balanced and interim
individual rational

#### Proof

- Can get efficient trades for some distributions:

  - Suppose the buyers value is always above $v$ and the sellers value
    is always below $v$

  - Mechanism: always exchange the good, and at the price
    $\mathbb{p}_B (\theta_B) = v = -\mathbb{p}_S (\theta_B)$

  - Satisfies all of the conditions

- Let us show the proof based our example:

  - The buyer’s value is equally likely to be either 0.1 or 1

  - The seller’s value for the good is equally likely to be 0 or 0.9

  - Trade should take place for all combinations of values except (0.1,
    0.9)

- Show the proof for *fully* budget balanced trade that is *ex post*
  individually rational. Extension of the proof is easy

  - Trade should take place for all combinations of values except
    $(\theta_B, \theta_S) = (0.1, 0.9)$

  - Budget balance: we can write payments as a single price
    $\mathbb{p}(\theta_B,\theta_S)$ (payment made by buyer, received by
    the seller)

  - Weak budget balance: you can extend the proof - noting that the
    payment made by the buyer has to be at least that received by the
    seller

1\. $p(1, 0.9) \ge 0.9$ by individual rationality of the seller

2\. $p(0.1, 0) \le 0.1$ by individual rationality of the buyer

3\. $p(0.1, 0.9) = 0$ by individual rationality of both the buyer and
the seller

4\. $p(1,0) =$ ?

- incentive compatibility for seller of type $\theta_S =0$ not wanting
  to pretend to be $\theta_S =0.9$:

  - $\frac{p(1,0)}{2}+\frac{p(0.1,0)}{2} \ge \frac{p(1,0.9)}{2}+\frac{p(0.1,0.9)}{2}$,
    which implies by 1,2,3 that

  - $p(1,0) + 0.1 \ge 0.9 +0$ or $p(1,0) \ge 0.8$

- incentive compatibility for buyer of type $\theta_B =1$ not wanting to
  pretend to be $\theta_B =0.1$:

  - $\frac{1-p(1,0)}{2}+\frac{1-p(0.1,0)}{2} \ge \frac{1-p(1,0.9)}{2}+\frac{p(1-0.1,0.9)}{2}$,
    which implies by 1,2,3 that

  - $1-p(1,0) + 0.1 \ge 0.9 +0$ or $p(1,0) \le 0.2$

- So, $0.2\ge p(1,0)$ and $p(1,0) \ge 0.8$ - impossible

#### Summary

- Private information about values:

  - necessitates some inefficiencies in voluntary trade

  - tension between incentives and efficiency

- Have you ever walked away from bargaining even when you initially
  thought a trade might have been possible?

## Resource

Game Theory II: Advanced Applications
<https://www.coursera.org/learn/game-theory-2>
