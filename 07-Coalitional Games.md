07 - Coalitional Games
================

## 7-1 Coalitional Game Theory

#### Introduction

- Our focus is on what **group of agents**, rather than individual
  agents, can achieve

- Given a set of agents, a coalitional game defines how well each group
  (or *coalition*) of agents can do itself

- We are **not** concerned with:

  - how the agents make individual choices within a coalition;

  - how they coordinate

- …instead, we take the payoffs to a coalition as given

#### Definition

- Transferable utility assumption:

  - payoffs may be redistributed among a coalition’s members

  - satisfied whenever payoffs are dispensed in a universal *currency*

  - each coalition can be assigned a single value as its payoff

Definition (Coalitional game with transferable utility)  
A **coalitional game with transferable utility** is a pair $(N,v)$,
where

- $N$ is a finite set of players, indexed by $i$; and

- $v:2^N \mapsto R$ associates with each coalition $S \subseteq N$ a
  real-valued payoff $v(S)$ that the coalition’s members can distribute
  among themselves. We assume that $v(\not0)=o$

#### Using Coalitional Game Theory

Questions we use coalitional game theory to answer:

1.  **Which coalition** will form?
2.  How should that coalition **divide its payoff** among its members?

The answer to (1) is often “the grand coalition” (all agent in $N$)
though this can depend on having made the right choice about (2)

#### Superadditive games

> [!NOTE]
> Definition (Superadditive game)  
>
> A game $G=(N,u)$ is **superadditive** if for all $S,T \subset N$, if
> $S \cap T = \not0$, then $v(S\cup T) \ge v(S)+v(T)$

- Superadditivity is justified when coalitions can always work without
  interfering with one another

  - the value of two coalitions will be no less than the sum of their
    individual values

  - implies that the grand coalition has the highest payoff

#### Analyzing coalitional games

1.  Which coalition will form?
    1.  we’ll consider cases where the answer is **the grand coalition**
    2.  makes sense for superadditive games
2.  How should the coalition divide its payoff?
    1.  in order to be **fair**
    2.  in order to be **stable**

## 7-2 The Shapley Value

- Lloyd Shapley’s idea: members should receive payments or shares
  proportional to their marginal contributions

- But this is tricky:

  - Suppose $v(N) =1$ but $v(S)=0$ if $N \not= S$

  - Then $v(N \setminus \{i\})=1$ for every $i$: everybody’s marginal
    contribution is 1, everybody is essential to generating any value

  - Cannot pay everyone their marginal Contribution

- We will have to use some weighting system - how should it be designed?

- Shapley’s axioms give us one answer

#### Summetry

- $i$ and $j$ are **interchangeable** relative to $v$ if they always
  contribute the same amount to every coalition of the other agents

  - for all $S$ that contains neither $i$ nor $j$,
    $v(S \cup \{i\}) = v(S \cup \{j\})$

> [!NOTE]
> Axion (Symmetry)  
>
> For any $v$, if $i$ and $j$ are interchangeable then
> $\psi_i (N,v) =\psi_j(N,v)$

- Interchangeable agents should receive the same shares/payments

#### Dummy Players

- $i$ is a **dummy player** if the amount that $i$ contributes to any
  coalition is 0

  - for all $S: v(S \cup \{i\}) = v(S)$

> [!NOTE]
> Axiom (Dummy player)  
>
> For any $v$, if $i$ is a dummy player then $\psi_i(N,v)=0$

- Dummy players should receive nothing

#### Additivity

- If we can separate a game into two parts $v =v_1+v_2$, then we should
  be able to decompose the payments:

> [!NOTE]
> Axiom (Additivity)  
>
> For any two $v_1$ and $v_2$,
> $\psi_i(N,v_1+v_2)=\psi_i(N,v_1)+\psi_i(N,v_2)$ for each $i$, where the
> game $(N,v_1+v_2)$ is defined by $(v_1+v_2)(S)=v_1(S)+v_2(S)$ for every
> coalition $S$

#### Shapley Value

Given a coalitional game $(N,v)$, the **Shapley Value** divide payoffs
among players according to:

$$
\phi_i(N,v)=\frac{1}{N!}\sum_{s \subseteq N \setminus \{i\}} |S|!(|N|-|S|-1)![v(S\cup \{i\})-v(S)]
$$

for each player $i$

> [!NOTE]
> Theorem  
>
> Given a coalitional game $(N,v)$, there is a unique play division
> $x(v)=\phi(N,v)$ that divides the full payoff of the grand coalition and
> that satisfies the Symmetry, Dummy player and Additivity axioms: the
> Shapley Value

#### Understanding the Shapley Value

$$
\phi_i(N,v)=\frac{1}{N!}\sum_{s \subseteq N \setminus \{i\}} |S|!(|N|-|S|-1)![v(S\cup \{i\})-v(S)]
$$

This captures the “marginal contributions” of agent $i$, averaging over
all the different sequences according to which the grand coalition could
be built up

- For any such sequence, look at agent $i$’s marginal contribution when
  added: $[v(S\cup \{i\} - v(S)]$

- Weight this quantity by the $|S|!$ ways the set $S$ could have been
  formed prior $i$’s addition and by the $(|N|-|S|-1)!$ ways the
  remaining players could be added

- Sum over all possible sets $S$ and average by dividing by $|N|!$: the
  number of possible orderings of all the agnets

#### Two Partners Sharing their Profits:

$v(\{1\})=1,v(\{2\})=2, v(\{1,2\})=4$

|     |     |                 |     |
|-----|-----|-----------------|-----|
| 1   | 1,2 | $v(1) =1$       | 1/2 |
| 2   | 1,2 | $v(1,2)-v(2)=2$ | 1/2 |

- $\phi_1 =1.5$

- $\phi_2 = 2.5$

#### Shapley Value

- The Shapley Value allocates the value of a group according to marginal
  contribution calculations

- Captured by some simple axioms and logic

- Other axioms and approaches lead to other allocations of value - for
  example the “Core” up next

## 7-3 The Core

#### Stable payoff division

- The Shapley value defined a **fair way** of dividing the grand
  coalition’s payment among its members

  - However, this analysis ignored questions of stability

- Would the agents be willing to form the **grand coalition** given the
  way it will divide payments, or would some of them prefer to form
  **smaller coalitions**?

  - Unfortunately, sometimes smaller coalitions can be more attractive
    for subsets of the agents, even if they lead to lower value overall

#### Example: Voting Game

Example (Voting Game)  
A parliament is made up of four political parties, $A,B,C$ and $D$,
which have 45,25,15 and 15 representatives, respectively. They are to
vote on whether to pass a \\100 million spending bill and how much of
this amount should be controlled by each of the parties. A majority
vote, that is, a minimum of 51 votes, is required in order to pass any
legislation, and if the bill does not pass then every party gets zero to
spend

- Shapley values: (50,16.67, 16.67,16.67)

- Can a subcoalition gain by defecting? While $A$ can’t obtain more than
  50 on its own, $A$ and $B$ have incentive to defect and divide the
  \\100 million between them (e.g., (75,25))

#### The Core

- Under what payment divisions would the agents **want to form the grand
  coalition**?

- They would want to do so if and only if the payment profile is drawn
  from a set called the **core**

> [!NOTE]
> Definition (Core)  
>
> A payoff vector $x$ is in the **core** of a coalitional game $(N,v)$ iff
>
> $$\forall S \subseteq N, \sum_{i \in S}x_i \ge v(S)$$

- The sum of payoffs to the agents in any subcoalition $S$ is at least
  as much as they could earn on their own

- Analogous to **Nash equilibrium**, except that it allows deviations by
  groups of agents

#### Existence and Uniqueness

1.  Is the core always \_\_\_non empty\_\_? No

- Consider again the voting game

- The set of minimal coalitions that meet the required 51 votes is
  $\{A,B\}, \{A,C\},\{A,D\}$ and $\{B,C,D\}$

- If the sum of the payoffs to parties $B,C$ and $D$ is less than \\ 100
  million, then this set of agents has incentive to deviate

- If $B,C$ and $D$ get the entire payoff of \\100 million, then $A$ will
  receive \\0 and will have incentive to form a coaltion with whichever
  of $B,C$ and $D$ obtained the smallest payoff

- Thus, the core is empty for this game

2.  Is the core always **unique**? No

- Consider changing the example so that an 80% majority is required

- The minimal winning coalitions are now $\{A,B,C\}$ and $\{A,B,D\}$

- Any complete distribution of the \\ 100million among $A$ and $B$ now
  belongs to the core

  - all winning coalitions need the support of these two parties

#### Simple Games

> [!NOTE]
> Definition (Simple game)  
>
> A game $G=(N,v)$ is **simple** if for all
> $S \subset N, v(S) \in \{0,1\}$

> [!NOTE]
> Definition (Veto player)  
>
> A player $i$ is a **veto player** if $v(N \setminus\{i\}) = 0$

> [!NOTE]
> Theorem  
>
> In a simple game the core is empty iff there is no veto player. If there
> are veto players, the core consists of all payoff vectors in which the
> nonveto players get 0

#### Airport Game

Example (Airport game)  
Several nearby cities need airport capacity, with different cities
needing to accommodate aircraft of different sizes. If a new regional
airport is built the cities will have to share its cost, which will
depend on the largest aircraft that they runway can accommodate.
Otherwise each city will have to built its own airport. This situation
can be modeled as a coalitional game $(N,v)$, where $N$ is the set of
cities, and $v(S)$ is the sum of the costs of building runways for each
city in $S$ minus the cost of the largest runway required by any city in
$S$

#### Convex games

> [!NOTE]
> Definition (Convex game)  
>
> A game $G=(N,v)$ is **convex** if for all
> $S,T \subset N, v(S \cup T) \ge v(S)+v(T)-v(S\cap T)$

- Convexity is a stronger condition than superadditivity

- The Airport game is convex

> [!NOTE]
> Theorem  
>
> Every convex game has a nonempty core


> [!NOTE]
> Theorem
>   
> In every convex game, the Shapley value is in the core

## 7-4 Comparing the Core and Shapley value in an Example

#### Compare Core and Shapley Value in an Example

- UN security council: 15 members

- 5 permanent members: China, France, Russia, UK, US

- 10 temporary members

- 5 permanent members can veto resolutions

- UN security council: represent it as a cooperative game

  - China, France, Russia, UK,US are labeled {1,2,3,4,5}

  - $v(S)=1$ if {1,2,3,4,5} $\subset S$ and $\sharp S \ge 8$

  - $v(S)=0$ otherwise

- Let’s start with a three-player game that has a similar structure:

  - 1 permanent member with a veto and 2 temporary members

  - $v(S)=1$ is $1 \in S$ and $\sharp S \ge 2$

  - $v(S)=0$ otherwise

  - Core: $x_1+x_2 \ge 1, x_1+x_3\ge 1, x_1+x_2+x_3=1, x_i \ge0$

    - $x_1 =1$

    - $x_2 =0$

    - $x_3=0$

  - Shapley Value

    - 1’s value: $v(\{1,2,3\})-v(\{2,3\})=1$ weighted by 2/6,
      $v(\{1,2\})-v(\{2\})=1$ weighted by 1/6, $v(\{1,3\})-v(\{3\})=1$
      weighted by 1/6

    - 2’s value: $v(\{1,2\})-v(\{1\})=1$ weighted by 1/6

    - 3’s value: $v(\{1,3\})-v(\{1\})=1$ weighted by 1/6

    - $x_1 = 2/3, x_2=1/6, x_3=1/6$

|     |     |       |     |
|-----|-----|-------|-----|
| 1   | 1,2 | 1,2,3 | 1/6 |
| 1   | 1,3 | 1,2,3 | 1/6 |
| 2   | 1,2 | 1,2,3 | 1/6 |
| 2   | 2,3 | 1,2,3 | 1/6 |
| 3   | 1,3 | 1,2,3 | 1/6 |
| 3   | 2,3 | 1,2,3 | 1/6 |

#### Cooperative Games

- Model complex multilateral bargaining and coalition formation, without
  specifying the particulars of a normal or extensive form

  - Core: Based on coalitional threats - each coalition must get at
    least what it can generate alone

  - Shapley Value: Based on marginal contributions: what does each
    player contribute to each possible coalition

#### Resources

Game Theory: <https://www.coursera.org/learn/game-theory-1>
