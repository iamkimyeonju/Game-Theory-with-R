01 - Introduction and Overview
================

``` r
knitr::opts_chunk$set(echo = TRUE, warning = FALSE, message = FALSE)
library(QGameTheory)
```

    ## Warning: package 'QGameTheory' was built under R version 4.3.2

## 1-1 Game Theory Intro - TCP Backoff

Should you send your packets using correctly-implemented TCP (which has
a “backoff” mechanism) or using a defective implementation (which
doesn’t)?

- This problem is an example of what we call a **two-player game**:

  - both use a correct implementation: both get 1ms delay
  - one correct, one defective: 4ms for correct, 0ms for defective
  - both defective: both get a 3ms delay

- Play this game: in your head; with a friend; on our online system.

- Some questions to discuss after playing:

  - What **action** should a player of the game take?
  - Would all users behave **the same** in this scenario?
  - What global **behavior patterns** should a system designer expect?
  - For what **changes to the numbers** would behavior be the same?
  - What effect would **communication** have?
  - **Repetitions**? (finite? infinite?)
  - Does it matter if I believe that my opponent is **rational**?

## 1-2 Self-Interested Agents and Utility Theory

#### Self-interested agents

- What does it mean to say that an agent is **self-interested**?
  - not that they want to harm others or only care about themselves
  - only that the agent has its own description of states of the world
    that is likes, and acts based on this description
- Each such agent has a **utility function**
  - **quantifies** degree of preference across alternatives
  - explains the impact of **uncertainty**
  - **Decision-theoretic rationality**: act to maximize expected utility

#### Why Utility?

- It might seem obvious that preferences can be described by utility
  function. But:

  - Why is a **single-dimensional** function enough?
  - Why should an agent’s response to uncertainty be captured purely by
    an **expected value**?

- Thus, our claim is substantive.

- There’s a famous theorem [(von Neumann & Morgenstern,
  1994)](https://www.degruyter.com/document/doi/10.1515/9781400829460/html)
  that derives the existence of a utility function from a more basic
  preference ordering and axions on such orderings.

## 1-3 Defining Games

#### Defining Games - Key Ingredients

- **Player**: who are the decision makers?
  - People? Governments? Companies? Somebody employed by a Company?…
- **Action**: what can the players do?
  - Enter a bid in an auction? Decide whether to end a strike? Decide
    when to sell a stock? Decide how to vote?
- **Payoffs**: what motivates players?
  - Do they care about some profits? Do they care about other player?…

#### Defining Games - Two Standard Representations

- **Normal Form** (a.k.a. Matrix Form, Strategic Form) List what payoffs
  gets as a function of their actions
  - It is as if players moved simultaneously
  - But strategies encode many things
- **Extensive Form** Includes timing of moves (later in course)
  - Players move sequentially, represented as a tree
    - Chess: white player moves, then black player can see white’s move
      and react…
  - Keeps track of what each player knows when he or she makes each
    decision
    - Poker: bet sequentially - what can a given player see when they
      bet?

#### Defining Games - The Normal Form

- Finite, *n*-person **normal form** game: [ $N$, $A$, $u$]
  - **Player**: $N = {1,...,n}$ is a finite set of $n$, indexed by $i$
  - **Action set** for player $i$: $A_{i}$
    - $a=(a_{1},...,a_{n}) \in A = A_{i} \times ... \times A_{n}$ is an
      **action profile**
  - **Utility function or Payoff function** for player $i$:
    $u_{i}: A \rightarrow R$
    - $u=(u_{1}, ... ,u_{n})$, is a **profile of utility functions**

#### Normal Form Games - The Stnadard Matrix Representation

- Writing a 2-player game as a **matrix**:
  - “row” player is player 1, “column” player is player 2
  - rows correspond to actions $a_{1} \in A_{1}$, columns correspond to
    actions $a_{2} \in A_{2}$
  - cells listing utility or payoff values for each player the row
    player first, then the column

#### Games in Matrix Form

Here’s the TCP Backoff Game written as a matrix

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} C & D \end{array}
\\
\begin{array}{cc}
C \\
D \\
\end{array}
&
\left[
\begin{array}{cc}
-1,-1 & -4,0  \\
0,-4 & -3,-3 \end{array}
\right]\end{array}
$$

</div>

``` r
player1 <- matrix(c(-1,-4,0,-3), ncol=2, byrow=TRUE)
player2 <- matrix(c(-1,0,-4,-3), ncol=2, byrow=TRUE)
NASH(player1,player2)
```

    ##   V1 V2
    ## 1  2  2

#### A Large Collective Action Game

- **Player**: $N={1,…,10,000,000}$
- **Action set** for player $i$: $A_{i} = {Revolt, Not}$
- **Utility function** for player $i$:
  - $u_{i}(a)=1$ if $\sharp{j:a_{j}=Revolt} >= 2,000,000$
  - $u_{i}(a)=-1$ if $\sharp{j:a_{j}=Revolt} < 2,000,000$ and $a_{i}=Revolt$
  - $u_{i}(a)=0$ if $\sharp{j:a_{j}=Revolt} < 2,000,000$ and $a_{i}=Not$

#### Summary: Defining Games

- For Now: Normal Form (Strategic Form, Matrix Representation…)
  - **Player**: $N$
  - **Action**: $A_{i}$
  - **Payoff**: $u_{i}$
- Later: Extensive Form
  - **Timing**: in what order do things happen?
  - **Information**: what do players know when they act

## 1-4 Examples of Games

#### More General Form

**Prisoner’s dilemma** is any game

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} C & D \end{array}
\\
\begin{array}{cc}
C \\
D \\
\end{array}
&
\left[
\begin{array}{cc}
a,a & b,c  \\
c,d & d,d \end{array}
\right]\end{array}
$$

</div>

with $c\>a\>d\>b$.

#### Games of Pure Competition

Players have **exactly opposed** interests 
- There must be precisely two players (otherwise they can’t have exactly opposed interests)
- For all action profiles \$a A, u\_{1}(a)+u\_{2}(a) =c \$ for some constant $c$ 
- Special case: zero sum + Thus, we only need to store a utility function for one player
-  in a sense, we only have to think about one player’s interests

#### Matching Pennies

One player wants to **match**; the other wants to **mismatch**.

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} Heads & Tails \end{array}
\\
\begin{array}{cc}
Heads \\
Tails \\
\end{array}
&
\left[
\begin{array}{cc}
1,-1 & -1,1  \\
-1,1 & 1,-1 \end{array}
\right]\end{array}
$$

</div>

#### Rock-Paper-Scissors

Generalized matching pennies.

<div class="math">

$$
\begin{array}{ccc} &
\begin{array}{ccc} Rock & Paper & Scissors \end{array}
\\
\begin{array}{ccc}
Rock \\
Paper \\
Scissors
\end{array}
&
\left[
\begin{array}{ccc}
0,0 & -1,1 & 1,-1  \\
1,-1 & 0,0 & -1,1 \\
-1,1 & 1,-1 & 0,0 \end{array}
\right]\end{array}
$$

</div>

… Believe it or not, there’s an annual international competition!

#### Games of Cooperation

Players have **exactly the same** interests
- no conflict: all players want the same things
- $\forall a \in A, \forall i,j, u_{i}(a)=u_{j}(a)$
- we often write such games with a single payoff per cell 
- why are such games “noncooperative”?

#### Coordination Game

Which **side of the road** should you drive on?

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} Left & Right \end{array}
\\
\begin{array}{cc}
Left \\
Right \\
\end{array}
&
\left[
\begin{array}{cc}
1,1 & 0,0  \\
0,0 & 1,1 \end{array}
\right]\end{array}
$$

</div>

#### General Games: Battle of the Sexes

The most interesting games combine elements of cooperation *and*
competition.

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} B & F \end{array}
\\
\begin{array}{cc}
B \\
F \\
\end{array}
&
\left[
\begin{array}{cc}
2,1 & 0,0  \\
0,0 & 1,2 \end{array}
\right]\end{array}
$$

</div>

## 1-5 Nash Equilibrium Intro

#### Keynes’ Beauty Contest Game

- You hold a stock and the price is rising…
- You believe that the price is too high to be justified by the value of
  the company
- You would like to sell it, but would like to wait until the price is
  almost at its peak
- You would like to get out of the market just before other investors do
- How will they act? What should you do in response?

#### Keynes’ Beauty Contest Game: The Stylized Version

- Each player names an integer between 1 and 100
- The player who names the integer closest to two-thirds of the
  *average* integer wins a prize, the other players get nothing
- Ties are broken uniformly at random

## 1-6 Strategic Reasoning

- What will other players do?
- What should I do in response?
- Each player *best responds* to the others: *Nash equilibrium*

#### Solving the Beauty Contest Game

- Suppose a player believes the average play will be $X$ (including his
  or her own integer) +That player’s optimal strategy is to say the
  closest integer to $\frac{2}{3} X$

- $X$ has to be less than 100, so the optimal strategy of any player has
  to be no more than 67

- If $X$ is no more than 67, then the optimal strategy of any player has
  to be no more than $\frac{2}{3} 67$

- If $X$ is no more than $\frac{2}{3} 67$, then the optimal strategy of
  any player has to be no more than $\frac{2}{3}^2 67$

- Iterating, the unique Nash equilibrium of this game is for every
  player to announce 1!

- The result of 2012 GTOC is

  - Mean 34
  - Mode 50
  - Median 33
  - Winner 23

- The result of 2012 Again is

  - Mean 6
  - Mode 1
  - Median 2
  - Winner 4

#### Nash Equilibrium

- A consistent list of actions:

- Each player’s action maximized his or her payoff given the actions of
  the others

- A self-consistent or stable profile

#### Summary Nash Equilibrium

- Each player’s action maximizes his or her payoff given the actions of
  the others

- Nobody has an incentive to *deviate* from their action if an
  equilibrium profile is played

- Someone has an incentive to *deviate* from a profile of actions that
  do *not* form an equilibrium

#### Nash Equilibrium

- Should we expect equilibria to be played?

- Should we expect non-equilibria to be played?

## 1-7 Best Response and Nash Equilibrium

#### Best Response

- If you knew what everyone else was going to do, it would be easy to
  pick your own action
- Let $a_{-1}= [a_{1},...,a_{i-1},a_{i+1},...,a_{n}]$
  - now $a=(a_{-i},a_{i})$

Definition (Best response)  
$$a_{i}^* \in BR(a_{-i}) \text{ iff } \forall a_{i} \in A_{i}, u_{i}(a_{i}^{*},a_{-1})\ge u_{i}(a_{i},a_{-i})$$

#### Nash Equilibrium

- Really, no agent knows what the others will do
- What can we say about which actions will occur?
- Idea: look for **stable** action profiles

Definition (Nash Equilibrium) 
$$a=<a_{1},...,a_{n}> \text{ is a ("pure strategy") Nash equilibrium iff }\forall i, a_{i} \in BR(a_{-1})$$

## 1-8 Nash Equilibrium of Example Games

- Nash equilibrium of **Prisoner’s dilemma** is (D,D)

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} C & D \end{array}
\\
\begin{array}{cc}
C \\
D \\
\end{array}
&
\left[
\begin{array}{cc}
-1,-1 & -4,0  \\
0,-4 & -3,-3 \end{array}
\right]\end{array}
$$

</div>

``` r
player1 <- matrix(c(-1,-4,0,-3), ncol=2, byrow=TRUE)
player2 <- matrix(c(-1,0,-4,-3), ncol=2, byrow=TRUE)
NASH(player1,player2)
```

    ##   V1 V2
    ## 1  2  2

- Nash equilibrium of **Coordination Game** are (Left,Left) and (Right,
  Right)

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} Left & Right \end{array}
\\
\begin{array}{cc}
Left \\
Right \\
\end{array}
&
\left[
\begin{array}{cc}
1,1 & 0,0  \\
0,0 & 1,1 \end{array}
\right]\end{array}
$$

</div>

``` r
player1 <- matrix(c(1,0,0,1), ncol=2, byrow=TRUE)
player2 <- matrix(c(1,0,0,1), ncol=2, byrow=TRUE)
NASH(player1,player2)
```

    ##   V1 V2
    ## 1  1  1
    ## 2  2  2

- Nash equilibrium of **Battle of the Sexes** are (B,B) and (F,F)

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} B & F \end{array}
\\
\begin{array}{cc}
B \\
F \\
\end{array}
&
\left[
\begin{array}{cc}
2,1 & 0,0  \\
0,0 & 1,2 \end{array}
\right]\end{array}
$$

</div>

``` r
player1 <- matrix(c(2,0,0,1), ncol=2, byrow=TRUE)
player2 <- matrix(c(1,0,0,2), ncol=2, byrow=TRUE)
NASH(player1,player2)
```

    ##   V1 V2
    ## 1  1  1
    ## 2  2  2

- There is no Nash equilibrium of **Matching Pennies**

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} Heads & Tails \end{array}
\\
\begin{array}{cc}
Heads \\
Tails \\
\end{array}
&
\left[
\begin{array}{cc}
1,-1 & -1,1  \\
-1,1 & 1,-1 \end{array}
\right]\end{array}
$$

</div>

``` r
player1 <- matrix(c(1,-1,-1,1), ncol=2, byrow=TRUE)
player2 <- matrix(c(-1,1,1,-1), ncol=2, byrow=TRUE)
NASH(player1,player2)
```

    ## [1] V1 V2
    ## <0 rows> (or 0-length row.names)

## 1-9 Dominant Strategies

#### Domination

- Let $s_{i}$ and $s_{i}^{'}$ be two strategies for player $i$, and let
  $S_{-i}$ be the set of all prossible strategy profiles for the other
  players
  - What’s a “strategy”?
  - For now, just choosing an action (“pure strategy”)

Definition  
$$s_{i} \text{ strictly dominates } s_{i}^{'} \text{ if } \forall s_{-i} \in S_{-i}, u_{i}(s_{i},s_{-i})>u_{i}(s_{i}^{'},s_{-i}) $$

Definition  
$$s_{i}  \text{ very weakly dominates } s_{i}^{'} \text{ if } \forall s_{-i} \in S_{-i}, u_{i}(s_{i},s_{-i}) \ge u_{i}(s_{i}^{'},s_{-i}) $$

#### Equilibria and Dominance

- If one strategy dominates all others, we say it is **dominant**
- A strategy profile consisting of dominant strategies for every player
  must be a Nash equilibrium.
  - An equilibrium in strictly dominant strategies must be unique

## 1-10 Pareto Optimality

#### Analyzing Games

- We’ve defined some canonical games, and thought about how to play
  them. Now let’s examine the games from the **outside**
- From the point of view of an outside observer, can some outcomes of a
  game be said to be **better** than others?
  - can’s say one agent’s interests are more important than another’s
  - imagine trying to find the revenue-maximizing outcome when you don’t
    know what currency is used to express each agent’s payoff
- Are there ways to still prefer one outcome to another?

#### Pareto Optimality

- **Idea**: sometimes, one outcome $o$ is at least as good for every
  agent as another outcome $o^{'}$, and there is some agent who strictly
  prefers $o$ to $o^{'}$
  - in this case, it seems reasonable to say that $o$ is better than
    $o^{'}$
  - we say that $o$ **Pareto-dominates** $o^{'}$

Definition (Pareto Optimality)  
An outcome $o^{*}$ is **Pareto-optimal** if there is no other outcome
that Pareto-dominates it.

- Can a game have more than one Pareto-optimal outcome? -\> Yes, for
  example,

$$
\left[ \begin{matrix}
1,1 & 1,1 \\ 
 1,1 & 1,1 
\end{matrix} \right] 
$$

- Does every game have at least one Pareto-optimal outcome? -\> Yes
  - Matching pennies is an example for this

#### Pareto Optimal Outcomes in Exan

- Pareto Optimal Outcomes of **Coordination Game** are (Left,Left) and
  (Right, Right)

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} Left & Right \end{array}
\\
\begin{array}{cc}
Left \\
Right \\
\end{array}
&
\left[
\begin{array}{cc}
1,1 & 0,0  \\
0,0 & 1,1 \end{array}
\right]\end{array}
$$

</div>

- Pareto Optimal Outcomes of **Battle of the Sexes** are (B,B) and (F,F)

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} B & F \end{array}
\\
\begin{array}{cc}
B \\
F \\
\end{array}
&
\left[
\begin{array}{cc}
2,1 & 0,0  \\
0,0 & 1,2 \end{array}
\right]\end{array}
$$

</div>

- Pareto Optimal Outcomes of **Matching Pennies** are every cell

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} Heads & Tails \end{array}
\\
\begin{array}{cc}
Heads \\
Tails \\
\end{array}
&
\left[
\begin{array}{cc}
1,-1 & -1,1  \\
-1,1 & 1,-1 \end{array}
\right]\end{array}
$$

</div>

- Pareto Optimal Outcomes of **Prisoner’s dilemma** are (C,D), (D,C) and
  (C,C)
  - (D,D) is Pareto dominated by (C,C)
  - The paradox of **Prisoner’s dilemma**: the (DS) Nash equilibrium is
    the only non-Pareto-optimal outcome!

<div class="math">

$$
\begin{array}{cc} &
\begin{array}{cc} C & D \end{array}
\\
\begin{array}{cc}
C \\
D \\
\end{array}
&
\left[
\begin{array}{cc}
-1,-1 & -4,0  \\
0,-4 & -3,-3 \end{array}
\right]\end{array}
$$

</div>

## Resources

- Game Theory: <https://www.coursera.org/learn/game-theory-1>
- QGameTheory Package in R: <https://github.com/indrag49/QGameTheory>
