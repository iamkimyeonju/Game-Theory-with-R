09 - Mechanism Design
================

## 9-1 Mechanism Design: Implementation

#### Bayesian Game Setting

- Extend the social choice setting to a new setting there agents can’t
  be relied upon to disclose their preferences honestly.

- Start with a set of agents in a Bayesian game setting (but no actions)

> [!NOTE]
> Definition (Bayesian game setting)  
>
> A **Bayesian game setting** is a tuple $(N,O,\Theta,p,u)$, where
>
> - $N$ is a finite set of agents
>
> - $O$ is a set of outcomes
>
> - $\Theta = \Theta_1 \times \cdots \times \Theta_n$ is a set of possible
>  joint type vectors
>
> - $p$ is a (common prior) probability distribution on $\Theta$
>
> - $u=(u_1, …, u_n)$, where $u_i: O \times \Theta \mapsto \mathbb{R}$ is
>  the utility function for each player $i$

#### Mechanism Design

> [!NOTE]
> Definition (Mechanism)  
>
> A **mechanism** (for a Bayesian game setting $(N,O,\Theta,p,u))$ is a
> pair $(A,M)$, where
>
> - $A=A_1 \times \cdots \times A_n$, where $A_i$ is the set of actions
>  available to agent $i \in N$
>
> - $M: A \mapsto \prod(O)$ maps each action profile to a distribution
>  over outcomes
>
> - Thus, the designer gets to specify
>
>  - the action sets for the agents
>
>  - the mapping to outcomes, over which agents have utility
>
>  - **can’t** change outcomes; agents’ preferences or type spaces

#### What we’re up to

- The problem is to pick a mechanism that will **cause rational agents
  to behave in a desired way**

  - each agent holds private information, in the Bayesian game sense

- Various **equivalent** ways of looking at this setting

  - perform an optimization problem, given that the values of (some of)
    the inputs are unknown

  - choose the Bayesian game out of a set of possible Bayesian games
    that maximizes some performance measure

  - design a game that *implements* a particular social choice function
    in equilibrium, given that the designer no longer knows agents’
    preferences and the agents might lie

#### Implementation in Dominant Strategies

Definition (Implementation in dominant strategies)  
Given a Bayesian game setting $(N,O,\Theta,p,u)$, a mechanism $(A,M)$ is
an **implementation in dominant strategies** of a social choice function
$C$ (over $N$ and $O$) if for any vector of utility function $u$, the
game has an equilibrium in dominant strategies and in any such
equilibrium $a^*$ we have $M(a^*)=C(u)$

#### Implementation in Bayes-Nash equilibrium

Definition (Bayes-Nash implementation)  
Given a Bayesian game setting $(N,O,\Theta,p,u)$, a mechanism $(A,m)$ is
an **implementation in Bayes-Nash equilibrium** of a social choice
function $C$ (over $N$ and $O$) if there exists a Bayes-Nash equilibrium
of the game of incomplete information $(N,A,\Theta,p,u)$ such that for
every $\theta \in \Theta$ and every action profile $a \in A$ that can
arise given type profile $\theta$ in this equilibrium, we have that
$M(a)=C(u(\cdot,\theta))$

- Bayes-Nash Equilibrium **Problems**:

  - there could be more than one equilibrium

    - which one should I expect agents to play?

  - agents could mis-coordinate and play none of the equilibria

  - asymmetric equilibria are implausible

- Refinements:

  - Symmetric Bayes-Nash implementation

  - *Ex-post* implementation

We can require that **the desired outcome arises**

- in the only equilibrium

- in every equilibrium

- in at least one equilibrium

Forms of implementation:

- **Direct Implementation**: agents each simultaneously send a single
  message to the center

- **Indirect Implementation**: agents send a sequence of messages;
  information may be (partially) revealed about the messages that were
  sent previously

## 9-2 Mechanism Design: Example

#### Bayesian Game Setting: Voting Examples

- $N=\{1,2,...,n\}$ is a committee of voters;

- $O=\{a,b,c\}$, the outcomes, are candidates who could be elected

#### Types and Utility functions

- This example has ‘private values’: the agent’s own type $\theta_i$
  fully captures the preferences of the agent:

  - $\tilde{\theta_i}$ has utility 3 for $a$, 2 for $b$, and 1 for $c$

  - $u_i(o,\tilde{\theta_i})$ depends only on $\theta_i$

  - $u(a,\tilde{\theta_i})=3, u(b,\tilde{\theta_i})=2$, and
    $u(c,\tilde{\theta_i})=1$

- $\Theta_i$ is the same for all $i$ and is
  $\{\tilde{\theta_i}, \hat{\theta_i}, \bar{\theta_i}\}$ where:

  - $\tilde{\theta_i}$ has utility 3 for $a$, 2 for $b$, and 1 for $c$

  - $\hat{\theta_i}$ has utility 3 for $b$, 2 for $a$, and 1 for $c$

  - $\bar{\theta_i}$ has utility 3 for $c$, 2 for $a$, and 1 for $b$

#### Probabilities

- Types are independent across agents:

  - $p=0.49$ of $\tilde{\theta_i}$

  - $p=0.49$ of $\hat{\theta_i}$

  - $p=0.02$ of $\bar{\theta_i}$

#### A Plurality Voting Mechanism

- $A=A_1 \times \cdots \times A_n$, where $A_i =\{a,b,c\}$

- $M: A \mapsto \prod(O)$:

  - picks the candidate named by the most agents (e.g., $M(b,b,c)=b$

  - if there is a tie, then picks among those getting most votes
    uniformly at random $(M(a,b,c)$ picks each candidate with
    probability 1/3)

#### No Dominant Strategies

- Suppose that $n$ is odd and at least 5, and consider type
  $\bar{\theta_i}$ who has utility 3 for $c$, 2 for $a$, and 1 for $b$:

  - If half of the other players vote for $a$ and half for $b$, then
    best off voting for $a$

  - If half of the other players vote for $c$ and half for $a$, then
    best off voting for $c$

- Optimal action depends on what think others will do

- (What if $n=3$?)

#### Many Bayes-Nash equilibria

- Suppose that $n$ is odd and at least 5:

  - All vote for candidate $b$ is an equilibrium,

  - All votes for candidate $b$ is an equilibrium, (not sensible?)

  - A ‘two candidate’ equilibrium (see ‘Duverger’s Law’):

    - $\tilde{\theta_i}$ votes $a$

    - $\hat{\theta_i}$ votes $b$

    - $\bar{\theta_i}$ (utility 3 for $c$, 2 for $a$, and 1 for $b$)
      votes for $a$

#### One Possible ‘Direct Mechanism’ for Plurality Rule

- Voter status type in
  $\{\tilde{\theta_i}, \hat{\theta_i}, \bar{\theta_i}\}$

- Mechanism translates type announcement into vote for favorite
  candidate:

  - saying $\tilde{\theta_i}$ is as if voting for $a$

  - saying $\hat{\theta_i}$ is as if voting for $b$

  - saying $\bar{\theta_i}$ is as if voting for $c$

#### Manipulation of that ‘Direct Mechanism’ for Plurality Rule

- If others are truthful, then type $\bar{\theta_i}$ would prefer to
  vote for $a$, so lies to $\tilde{\theta_i}$

- Look at other direct mechanisms next..

## 9-3 Revelation Principle

![](assets/images/revelation%201.png)

- It turns out that any social choice function that can be implemented
  by any mechanism can be implemented by a **truthful, direct**
  mechanism

- Consider an arbitrary, non-truthful mechanism

  - may be indirect

- Recall that a mechanism defines a game, and consider an equilibrium
  $s=(s_1,…,s_n)$

![](assets/images/revelation%202.png)

- We can construct a new **direct** mechanism, as shown above

- This mechanism is truthful by exactly the same argument that $a$ was
  an equilibrium in the original mechanism

- **The agents don’t have to lie, because the mechanism already lies for
  them**

#### Discussion of the Revelation Principle

- The set of equilibria in **not always the same** in the original
  mechanism and revelation mechanism

  - of course, we’ve shown that the revelation mechanism does have the
    original equilibrium of interest

  - however, in the case of indirect, mechanisms, even if the indirect
    mechanism had a unique equilibrium, the revelation mechanism can
    also have new, bad equilibria

- So what is the revelation principle **good for**?

  - recognition that truthfulness is not a restrictive assumption

  - recognition that indirect mechanisms can’t do (inherently) better
    than direct mechanisms

  - for analysis purposes, we can consider only truthful mechanisms, and
    be assured that such a mechanism exists

## 9-4 Revelation Principle: Example

#### Recall Plurality Example

- $N=\{1,2,…,n\}$ is a committee of voters;

- $O=\{a,b,s\}$, candidates who could be elected;

- $\Theta_i$ is the same for all $i$ and is
  $\{\tilde{\theta_i}, \hat{\theta_i}, \bar{\theta_i}\}$ where:

  - $(p=0.49)$ of $\tilde{\theta_i}$ has utility 3 for $a$, 2 for $b$,
    and 1 for $c$

  - $(p=0.49)$ of $\hat{\theta_i}$ has utility 3 for $b$, 2 for $a$, and
    1 for $c$

  - $(p=0.02)$ of $\bar{\theta_i}$ has utility 3 for $c$, 2 for $a$, and
    1 for $b$

#### Many Bayes-Nash equilibria

- Suppose that $n$ is odd and at least 5:

  - All vote for candidate $b$ is an equilibrium,

  - All vote for candidate $b$ is an equilibrium, (not sensible?)

  - A ‘two candidate’ equilibrium (see ‘Duverger’s Law’):

    - $\tilde{\theta_i}$ votes $a$

    - $\hat{\theta_i}$ votes $b$

    - $\bar{\theta_i}$ (utility 3 for $c$, 2 for $a$, and 1 for $b$)
      votes for $a$

#### ‘Direct Mechanism’ for Plurality Rule Equilibrium where all vote for $a$

- Voter states type in
  $\{\tilde{\theta_i}, \hat{\theta_i}, \bar{\theta_i}\}$

- Mechanism translates every type of announcement into vote $a$:

  - saying $\tilde{\theta_i}$ is as if voting for $a$

  - saying $\hat{\theta_i}$ is as if voting for $a$

  - saying $\bar{\theta_i}$ is as if voting for $a$

  - outcome is $a$

#### ‘Direct Mechanism’ for Plurality Rule Equilibrium vote for $a$ or $b$

- Voter states type in
  $\{\tilde{\theta_i}, \hat{\theta_i}, \bar{\theta_i}\}$

- Mechanism translates every type announcement into vote $a$:

  - saying $\tilde{\theta_i}$ is as if voting for $a$

  - saying $\hat{\theta_i}$ is as if voting for $b$

  - saying $\bar{\theta_i}$ is as if voting for $a$

  - outcome is $a$

## 9-5 Impossibility of General Dominant-Strategy Implementation

#### Dominant Strategies and Mechanisms: Let us apply the revelation principle

Consider a society $N, O$ and any mechanism $A, M$ for which every agent
has a dominant strategy for each preference. There exists a social
choice function $C$ (a ‘direct mechanism’) for which truthful
announcement of preferences is a dominant strategy

So, if we are considering implementation in dominant strategies, is is
enough to look only at social choice functions for which truth is a
dominant strategy: the set of *non-manipulable* or *strategy-proof*
social choice functions

#### Impossibility Result

> [!NOTE]
> Theorem (Gibbard-Satterthwaite)  
>
> Consider a social choice function $C: L^n \mapsto O$. suppose that
>
> 1.  There are at least three outcomes so that $|O| \ge 3$ and
> 2.  $C$ is onto; that is, for every $o \in O$ there is a preference
>    profile $[\succ]\in L^n$ such that $C([\succ])=o$
>
> Truthful reporting of preferences is a dominant strategy for each agent
> $i$ and each preference $\succ_i \in L$ if and only if $C$ is
> dictatorial: there exists $i$ for whom $C([\succ]) = argmax_O \succ_i$
> for all $[\succ] \in L^n$
>
> So any non-dictatorial social choice functions on a full domain of
> preferences and with at least three alternatives will be manipulable by
> some agents for some preference profiles

#### What does this mean?

- Having dominant strategies for all agents and possible preferences is
  infeasible unless we have a dictatorial social choice function

- However, in practice we can **circumvent the Gibbard-Satterthwaite
  theorem** in various ways:

  - use a weaker form of implementation:

    - the result only holds for dominant strategy implementation, not
      e.g., Bayes-Nash implementation

  - relax the assumption that agents are allowed to have arbitrary
    preferences and look at more structured settings

#### Setting with Strategy-Proof Social Choice Functions:

- Single-Peaked domains:

  - median voting

  - or take the max of peaks, or the min of peaks

- Trade:

  - Have a private value for buying (or selling) an indivisible good

  - A price is fixed in advance

  - declare whether willing to buy (sell) at that price

## 9-6 Transferable Utility

> [!NOTE]
> Definition (Quasilinear preferences with transferable utility)  
>
> Agents have **quasilinear preferences with transferable utility** in an
> $n$-player Bayesian game when the set of outcomes is
>
> $$O=X\times\mathbb{R^n}$$
>
> for a set $X$, if the utility of an agent $i$ given joint type $\theta$
> can be written
>
> $$u_i(o,\theta)=u_i(x,\theta)-p_i$$
>
> where $o=(x,p)$ is an element of $O$, and
> $u_i: X \times \Theta \mapsto \mathbb{R}$

#### Transferable utility mechanisms

- When outcomes consist of basic outcomes and some transfers or
  payments: $u_i(o,\theta)=u_i(x,\theta)-p_i$

- We can split the mechanism into a **choice rule** and a **payment
  rule** (or transfer rule):

  - $x \in X$ is a “nonmonetary” outcome

  - $p_i \in \mathbb{R}$ is a “monetary” payment (possibly negative)
    that agent $i$ makes to the mechanism

- Implications:

  - $u_i(x,\theta)$ is not influenced by the amount of money/wealth an
    agent has

  - agents don’t care how much others are made to pay (though they can
    care about how the choice affects others)

#### Direct Mechanisms in a Quailinear Setting

> [!NOTE]
> Definition (Direct mechanism)  
>
> A **direct mechanism** (in a quasilinear setting
> $(N,O = X \times \mathbb{R^n},\Theta,p,u)$ ) is a pair
> $(\chi,\mathbb{p})$ specifying a basic outcome $\chi(\theta)$ and a
> profile of payments or transfers
> $\mathbb{p}(\theta)=(\mathbb{p_1}(\theta),…,\mathbb{p_n}(\theta))$

#### Private Values (Conditional Utility Independence)

- Preferences have private values, or satisfy conditional utility
  independence, if each agent $i$’s utility function can be written as
  $u_i(o,\theta_i)$

  - it does not depend on the other agents’ types

- An agent’s type becomes their **valuation function**: $i$’s value for
  choice $x \in X$ is $v_i(x)=u_i(x,\theta_i)$

  - the maximum amount $i$ would be willing to pay to get $x$

- Alternative definition of a **direct mechanism**:

  - ask agents $i$ to declare valuation functions
    $v_i: X \rightarrow \mathbb{R}$

  - standard notation: $\hat{v_i}$ is the valuation function that agent
    $i$ declares

## 9-7 Transferable Utility Example

#### Building a Public Project/Making a Joint Investment

- $N=\{1,…,n\}$ a set of citizens, $n$ is odd

- $O=\{0,1\}:$ 0=do nothing, 1= undertake the project

#### Types:

- $\theta_i$ is now a (private value) valuation function

- utilities for outcomes 0,1: $v_i(0), v_i(1)$

  - e.g., $v_i(0)=0$ and $v_i(1)=4$

  - represent that as $v_i=(0,4)$

  - another possible $v_i=(0,-2)$

#### An Example of a transferable utility mechanism

- People announce either $\hat{v_i}=(0,4)$ or $\hat{v_i}=(0,-2)$

- If majority of people announce $\hat{v_i}=(0,4)$, then:

  - $x=1$ (undertake project)

  - $p_i =0$ for all $i$

- If majority of people announce $\hat{v_i}=(0,-2)$, then:

  - $x=0$ (don’t do the project)

  - $p_i =0$ for all $i$

- Truth is an equilibrium, but sometimes gets negative utility and choice
  does not maximize total utility

#### Another Example of a transferable utility mechanism

- People announce either $\hat{v_i}=(0,4)$ or $\hat{v_i}=(0,-2)$

- If $m>n/3$ announce $\hat{v_i}=(0,4)$, then:

  - $x=1$ (undertake project)

  - $p_i=(\frac{n-m}{m})2$ if $\hat{v_i}=(0,4)$, and $p_i=-2$ if
    $\hat{v_i}=(0,-2)$

- Otherwise

  - $x=0$ (don’t do the project)

  - $p_i=0$ for all $i$

- Choice maximizes total (announced utilities), don’t get a negative
  utility, but

- Truth may no longer be an equilibrium (large $n$: if everyone else is
  honest, might want to lie when (0,4) and say (0,-2))

## 9-8 Mechanism Design as an Optimization Problem

#### Mechanism Design as an Optimization Problem

- We can understand mechanism design as the problem of finding the best
  possible mechanism, given constraints about how it operates

- We’ll now consider some typical choices for

  - these constraints

  - this notion of “best”

#### Truthfulness

> [!NOTE]
> Definition (Truthfulness)  
>
> A transferable utility mechanism is **truthful** if it is direct and
> $\forall i \forall v_i$, agent $i$’s equilibrium strategy is to adopt
> the strategy $\hat{v_i}=v_i$

#### Efficiency

> [!NOTE]
> Definition (Efficiency)  
>
> A transferable utility mechanism is **strictly Pareto efficient**, or
> just **efficient**, if in equilibrium it selects a choice $x$ such that
>
> $$\forall v \forall x', \sum_{i}v_i(x) \ge \sum_{i}v_i(x')$$

- An efficient mechanism selects the choice that maximizes the sum of
  agents’ utilities, disregarding monetary payments

- How is this related to the standard game-theoretic definition of
  Pareto efficiency?

  - if we include the mechanism as an agent, all Pareto-efficient
    outcomes involve the same choice (and different payments)

  - any outcome involving another choice is Pareto-dominated: some
    agents could pay others such that all would prefer the swap

- Called **economic efficiency** to distinguish from others (e.g.,
  computational) notions

- Also called **social-welfare maximization**

- Note: defined in terms of true (not declared) valuations

#### Budget Balance


> [!NOTE]
> Definition (Budget balance)  
> A transferrable utility mechanism is **budget balanced** when
>
> $$\forall v, \sum_{i}\mathbb{p_i}(s(v))=0,$$
> where $s$ is the equilibrium strategy profile

- regardless of the agents’ types, the mechanism collects and disburses
  the same amount of money from and to the agents

- relaxed version: **weak budget balance**:

$$
\forall v, \sum_i\mathbb{p_i}(s(v))\ge0
$$

- the mechanism never takes a loss, but it may make a profit

- Budget balance can be required to hold *ex ante*:

$$
\mathbb{E_v} \sum_i \mathbb{p_i}(s(v))=0
$$

- the mechanism must break even only on expectation

#### Individual-Rationality

> [!NOTE]
> Definition (Ex interim individual rationality)  
>
> A mechanism is **ex interim individual rational** when
> $\forall i \forall v_i, \mathbb{E_{v_{-i}|v_i}}v_i(\chi(s_i(v_i), s_{-i}(v_{-1})))-\mathbb{p_i}(s_i(v_i), s_{-i}(v_{-i}))\ge 0$
> where $s$ is the equilibrium strategy profile

- no agent loses by participating in the mechanism

- ex *interim* because it holds for every possible valuation for agent
  $i$, but averages over the possible valuations of the other agents


> [!NOTE]
> Definition (Ex post individual rationality)  
>
> A mechanism is **ex post individual rational**
> when$\forall i \forall v, v_i(\chi(s(v)))-\mathbb{p_i}(s(v)))\ge 0$
> where $s$ is the equilibrium strategy profile

#### Tractability

> [!NOTE]
> Definition (Tractability)  
>
> A mechanism is **tractable** when $\forall \hat{v}, \chi(\hat{v})$ and
> $\mathbb{p}(\hat{v})$ can be computed in polynomial time

- The mechanism is (guaranteed to be) computationally feasible

#### Revenue Maximization

We can also add an objective function to our mechanism. One example:
revenue maximization

> [!NOTE]
> Definition (Revenue maximization)  
>
> A mechanism is **Revenue maximizing** when, among the set of functions
> $\chi$ and $\mathbb{p}$ that satisfy the other constraints, the
> mechanism selects the $\chi$ and $\mathbb{p}$ that maximize
> $\mathbb{E_\theta}\sum_i p_i(s(\theta))$, where $s(\theta)$ denotes the
> agents’ equilibrium strategy profile

- The mechanism designer can choose among mechanisms that satisfy the
  desired constraints by adding an objective function such as revenue
  maximization

#### Revenue Minimization

- The mechanism may not be intended to make money

- Budget balance may be impossible to satisfy

- Set weak budget balance as a constraint and add the following
  objective

> [!NOTE]
> Definition (Revenue maximization)  
>
> A mechanism is **Revenue minimizing** when, among the set of functions
> $\chi$ and $\mathbb{p}$ that satisfy the other constraints, the
> mechanism selects the $\chi$ and $\mathbb{p}$ that minimize
> $max_v\sum_i p_i(s(\theta))$, where $s(\theta)$ denotes the agents’
> equilibrium strategy profile

- Note: this considers the **worst case** over valuations; we could
  consider the average case instead

#### Fairness

- Fairness is hard to define. What is fairer:

  - charging all agents \\100 and making a choice they all hate equally?

  - charging all agents \\0 and making a choice that some hate and some
    like?

- **Maxmin fairness**: make the least-happy agent the happiest

> [!NOTE]
> Definition (Maxmin fairness)  
>
> A transferrable utility mechanism is **maxmin fair** when, among the set
> of functions $\chi$ and $\mathbb{p}$ that satisfy the other constraints,
> the mechanism selects the $\chi$ and $\mathbb{p}$ that maximize
>
> $$\mathbb{E_v}\big[ \min_{i \in N} v_i (\chi(s(v)))-\mathbb{p_i}(s(v))  \big]$$
>
> where $s(v)$ denotes the agents’ equilibrium strategy profile

#### Price of Anarchy Minimization

- When efficiency is impossible, we can try to get close

- Minimize the **worst-case ratio** between optimal social welfare and
  the social welfare achieved by the given mechanism

> [!NOTE]
> Definition (Price-of-anarchy minimization)  
>
> A transferrable utility mechanism **minimizes the price of anarchy**
> when, among the set of functions $\chi$ and $\mathbb{p}$ that satisfy
> the other constraints, the mechanism selects the $\chi$ and $\mathbb{p}$
> that minimize
>
> $$\max_{v \in V}\frac{\max_{x \in X} \sum_{i \in N} v_i(x)}{\sum_{i \in N}v_i(\chi(s(v)))}$$
>
> where $s(v)$ denotes the agents’ equilibrium strategy profile in the
> *worst* equilibrium of the mechanism-i.e., the equilibrium in which
> $\sum_{i \in N} v_i(\chi(s(v)))$ is the smallest

## Resource

Game Theory II: Advanced Applications
<https://www.coursera.org/learn/game-theory-2>
