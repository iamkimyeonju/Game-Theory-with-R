08 - Social Choice
================

## 8-1 Social Choice

#### Introduction

Our setting now:

- a set of **outcomes** or **alternatives**

- agents have **preferences** over them

- the ‘goal’: a **social choice function**: a mapping from profiles of
  preferences to a particular outcome

  - Which such functions have desirable properties?

#### Preferences

- Given is a finite set of **outcomes** or **alternatives** $O$

- agents have (strict) **preferences**, $\prec$, over the outcomes:
  linear orders (or total orders)

- Linear orders $L$: binary relations $\prec$ that are total and
  transitive

  - total: for every pair of outcomes $a \not= b$ either $a \succ b$ or
    $b \succ a$ (but not both: so it is complete and antisymmetric)

  - transitive: $a \succ b$ and $b \succ c$ implies $a \succ c$

- Non-strict preferences $L_{NS}$: binary relations $\succeq$ that are
  complete and transtive

  - complete: for every $a,b$ either $a \succeq b$ of $b \succeq a$
    (both indicates indifference)

  - transtive: $a \succeq d$ and $b \succeq c$ implies $a \succeq c$

#### Formal model

Given is a set of agent $N=\{1,2,…,n\}$, a finite set of outcomes (or
alternatives, or candidates) $O$, and the linear orders on the outcomes,
$L_{NS}$

Definition (Social choice function)  
A **social choice function** is a function $C:L_{NS}^n \rightarrow Q$

Definition (Social welfare function)  
A **social welfare function** (or social welfare ordering) is a function
$W: L_{NS}^n \rightarrow L_{NS}$

#### Voting Schemes: Scoring Rules

- **Plurality**

  - pick the outcome which is most-preferred by the most people

- **Cumulative voting**

  - distribute e.g., 5 votes each

  - possible to vote for the same outcome multiple times

- **Approval voting**

  - vote for as many outcomes as you “like”

#### Voting Schemes base on Ranking

- **Plurality with elimination** (“instant runoff”, “transferable
  voting”)

  - if some outcome has a majority. it is the winner

  - otherwise, the outcome with the fewest votes is eliminated (may need
    some tie-breaking procedure)

  - repeat until there is a winner

- **Borda Rule, Borda Count**

  - assign each outcome a number

  - the most preferred outcome gets a score of $n-1$, the next most
    preferred gets $n-2$, down to the $n^{th}$ outcomes which gets 0

  - Sum scores for each outcome, and choose one with highest scores

- **Successive elimination**

  - in advance, decide an ordering of alternatives

  - everyone votes for the first or second, and the loser is eliminated

  - then vote for winner vs. third alternative, and lower is eliminated

  - continues until the last alternative is considered

#### Condorcet Consistency

If there is a candidate or outcome that is **preferred to every other
candidate in pairwise majority-rule comparisons**, that candidate should
be chosen

- there is not always a Condorcet winner

- sometimes, there is a cycle where $A$ defeats $B$, $B$ defeats $C$,
  and $C$ defeats $A$, known as a Condorcet Cycle

## 8-2 Paradoxical Outcomes

#### Condorcet example

499 agents: $A \succ B \succ C$

3 agents: $B \succ C \succ A$

498 agents: $C \succ B \succ A$

- What is the Condorcet winner? $B$

- What would win under plurality voting? $A$

- What would win under plurality win elimination? $C$

#### Sensitivity to Losing Candidate

35 agents: $A \succ C \succ B$

33 agents: $B \succ A \succ C$

32 agents: $C \succ B \succ A$

- What candidate wins under plurality voting? $A$

- What candidate wins under Borda voting? $A$

- Now consider dropping $C$. now what happens under both Borda and
  plurality? $B$ wins

#### Sensitivity to Agenda Setter

35 agents: $A \succ C \succ B$

33 agents: $B \succ A \succ C$

32 agents: $C \succ B \succ A$

- Who wins pairwise elimination, with the ordering $A,B,C$? $C$

- Who wins with the ordering $A,C,B$? $B$

- Who wins with the ordering $B,C,A$? $A$

#### Another Pairwise Elimination Problem

1 agents: $B \succ D \succ C \succ A$

1 agents: $A \succ B \succ D \succ C$

1 agents: $C \succ A \succ B \succ D$

- Who wins under pairwise elimination with the ordering $A,B,C,D$? $D$

- What is the problem with this?

  - all of the agents prefer $B$ to $D$ - the selected candidate is
    Pareto-dominated

## 8-3 Impossibility of Non-Paradoxical Social Welfare Functions

#### Pareto Efficiency

Definition (Pareto Efficiency (PE))  
$W$ is **Pareto efficient** if whenever all agents agree on the ordering
of two outcomes, the social welfare function select that ordering

#### Independence of Irrelevant Alternatives

Definition (Independence of Irrelevant Alternatives (IIA))  
$W$ is **independent of irrelevant alternatives** if the selected
ordering between two outcomes depends only on the relative orderings
they are giving by the agents

#### Dictatorship

Definition (Dictatorship)  
$W$ has a **dictator** if there exists a single agent whose preferences
always determine the social ordering

#### Arrow’s Theorem

Theorem (Arrow, 1951)  
Any social welfare function $W$ over three or more outcomes that is
Pareto efficient and independent of irrelevant alternatives is
dictatorial

## 8-4 Arrow’s Theorem

#### Notation

- $N$ is the set of **agents**

- $O$ is a finite set of **outcomes** with $|O| \ge 3$

- $L$ is the set of all possible **strict preference orderings** over
  $O$

  - for ease of exposition we switch to strict orderings

  - we will end up showing that desirable SWFs cannot be found *even if*
    preferences are restricted to strict orderings

- $[\succ]$ is an element of the set $L^n$ (a **preference ordering for
  every agents**; the input to our social welfare function)

- $\succ_W$ is the **preference ordering selected by the social welfare
  function** $W$

  - When the input to $W$ is ambiguous we write it in the subscript;
    thus, the social order selected by $W$ given the input $[\succ']$ is
    denoted as $\succ_{W([\succ'])}$

#### Pareto Efficiency

Definition (Pareto Efficiency (PE))  
$W$ is **Pareto efficiency** if for any
$o_1,o_2 \in O, \forall i \ o_1 \succ_i o_2$ implies that
$o_1 \succ_W o_2$

- When all agents agree on the ordering of two outcomes, the social
  welfare function must select that ordering

#### Independence of Irrelevant Alternatives

Definition (Independence of Irrelevant Alternatives (IIA))  
$W$ is **independent of irrelevant alternatives** if, for any
$o_1,o_2 \in O$ and any two preference profiles
$[\succ'], [\succ''] \in L^n, \forall i \ (o_1 \succ'i o_2$ if and only
if $o_1 \succ''_i o_2$) implies that $(o_1 \succ_{W([\succ'])} o_2$ if
and only if $o_2 \succ_{W([\succ''])} o_2$

- the selected ordering between two outcomes should depend only on the
  relative orderings they are given by the agents

#### Non-dictatorship

Definition (Non-dictatorship)  
$W$ does not have a dictator if
$\neg\exists i \forall o_1,0_2(o_1 \succ_i o_2 \implies o_1 \succ_W o_2)$

- There does not exist a single agent whose preferences always determine
  the social orderings

- We say that $W$ is **dictatorial** if it fails to satisfy this
  property

#### Arrow’s Theorem

Theorem (Arrow, 1951)  
Any social welfare function $W$ that is Pareto efficient and independent
of irrelevant alternatives is dictatorial

We will assume that $W$ is both PE and IIA, and show that $W$ must be
dictatorial. Our assumption that $|O| \ge 3$ is necessary for this
proof. The argument proceeds in four steps

##### Step 1

If every voter puts an outcome $b$ at either the very top or the very
bottom of his preference list, $b$ must be at either the very top or
very bottom of $\succ_W$ as well

Consider an arbitrary preference profile $[\succ]$ in which every voter
ranks some $b \in O$ at either the very bottom or very top, and assume
for contradiction that the above claim in not true. Then there must
exist some pair of distinct outcomes $a,c \in O$ for which $a \succ_W b$
and $b \succ_W c$

Now let’s modify $[\succ]$ so that every voter moves $c$ just above $a$
in his preference ranking, and otherwise leaves the ranking unchanged;
let’s call this new preference profile $[\succ']$. We know from IIA that
for $a \succ_W b$ or $b \succ_W c$ to change, the pairwise relationship
between $a$ and $b$ and/or the pairwise relationship between $b$ and $c$
would have to change. However, since $b$ occupies an extremal position
for all voters, $c$ can be moved above $a$ without changing either of
these pairwise relationships. Thus in profile $[\succ']$ it is also the
case that $a \succ_W c$. However, in $[\succ']$ every voter ranks $s$
above $a$ and so PE requires that $c \succ_W a$. We have a
contradiction.

##### Step 2

There is some voter $n^*$ who is **extremely pivotal** in the sense that
by changing his vote at some profile, he can move a given outcome $b$
from the bottom of the social ranking to the top.

Consider a preference profile $[\succ]$ in which every voter ranks $b$
last, and in which preferences are otherwise arbitrary. By PE, $W$ must
also rank $b$ last. Now let voters from 1 to $n$ successively modify
$[\succ]$ by moving $b$ from the bottom of their rankings to the top,
preserving all other relative rankings. Denote as $n^*$ the first voter
whose change causes the social ranking of $b$ to change. There clearly
must be some such voter: when the voter $n$ moves $b$ to the top of his
ranking, PE will require that $b$ be ranked at the top of the social
ranking.

Denote by $[\succ^1]$ the preference profile just before $n^*$ moves
$b$, and denote by $[\succ^2]$ the preference profile just after $n^*$
has moved $b$ to the top of his ranking. In $[\succ^1]$, $b$ is at the
bottom in $\succ_W$. In $[\succ^2]$. $b$ has changed its position in
$\succ_W$, and every voter ranks $b$ at either the top or the bottom. By
the argument from Step 1, in $[\succ^2]$ $b$ must be ranked at the top
of $\succ_W$.

##### Step 3

$n^*$ (the agent who is extremely pivotal on outcome $b$) is a dictator
over any pair $ac$ not involving $b$.

We begin by choosing one element from the pair $ac$; without loss of
generality, let’s choose $a$. We’ll construct a new preference profile
$[\succ^3]$ from $[\succ^2]$ by making two changes. First, we move $a$
to the top of $n^*$’s preference ordering, leaving it otherwise
unchanged; thus $a \succ_{n^*} b \succ_{n^*}c$. Second, we arbitrarily
rearrange the relative rankings of $a$ and $c$ for all voters other than
$n^*$, while leaving $b$ in its extremal position,

In $[\succ^1]$ we had $a \succ_W b$, as $b$ was at the very bottom of
$\succ_W$. When we compare $[\succ^1]$ to $[\succ^3]$, relative rankings
between $a$ and $b$ are the same for all voters. Thus, by IIA, we must
have $a \succ_W b$ in $[\succ^3]$ as well. In $[\succ^2]$ we had
$b \succ_W c$, as $b$ was at the very top of $\succ_W$. Relative
rankings between $b$ and $c$ are the same in $[\succ^2]$ and
$[\succ^3]$. Thus in $[\succ^3]$, $b \succ_W c$. Using the two above
facts about $[\succ^3]$ and transitivity, we can conclude that
$a \succ_W c$ in $[\succ^2]$.

In $[\succ^3]$ and $[\succ^4]$ all agent have the same relative
preferences between $a$ and $c$; thus, since $a \succ_W c$ in
$[\succ^3]$ and by IIA, $a \succ_W c$ in $[\succ^4]$. Thus we have
determined the social preference between $a$ and $c$ without assuming
anything except that $a \succ_{n^*} c$.

##### Step 4

$n^*$ is a dictator over all pairs $ab$

Consider some third outcome $c$. By the argument in Step 2, there is a
voter $n^{**}$ who is extremely pivotal for $c$. By the argument in Step
3, $n^{**}$ is a dictator over any pair $\alpha \beta$ not involving
$c$. Of course, $ab$ is such a pair $\alpha \beta$. We have already
observed that $n^*$ is able to affect $W$’s $ab$ ranking - for example,
when $n^*$ was able to change $a \succ_W b$ in profile $[\succ^1]$ into
$b \succ_W a$ in profile $[\succ^2]$. Hence, $n^{**}$ and $n^*$ must be
the same agent.

## 8-5 Impossibility of Non-Paradoxical Social Choice Functions

#### Social Choice Functions

- Maybe Arrow’s theorem held because we required a whole preference
  ordering

- Idea: **social choice functions** might be easier to find

- We’ll need to redefine our criteria for the social choice function
  setting; PE and IIA discussed the ordering

#### Weak Pareto Efficiency

Definition (Weak Pareto Efficiency)  
A social choice function $C$ is **weakly Pareto efficient** if it never
selects an outcome $o_2$ when there exists another outcome $o_1$ such
that $\forall i \in N, o_1 \succ_i o_2$

- A dominated outcome can’t be chosen

#### Monotonicity

Definition (Monotonicity)  
$C$ is **monotonic** if, for any $o \in O$ and any preference profile
$[\succ] \in L^n$ with $C([\succ])=o$, then for any other preference
profile $[\succ']$ with the property that
$\forall i \in N, \forall o'\in O, o \succ'_i o'$ if $o \succ_i o'$, it
must be that $C([\succ'])=o$.

- an outcome $o$ must remain the winner whenever the support for it is
  increased in a preference profile under which $o$ was already winning

#### Dictatorship

Definition (Dictatorship)  
$C$ is **dictatorial** if there exists an agent $j$ such that $C$ always
selects the top choice in $j$’s preference ordering

#### The bad news

Theorem (Muller-Satterthwaite, 1977)  
Any social choice function that is weakly Pareto efficient and monotonic
is dictatorial

- Perhaps contrary to intuition, social choice functions are no simpler
  than social welfare functions after all

- The proof repeatedly “probes” a social choice function to determine
  the relative social ordering between given pairs of outcomes

- Because the function must be defined for all inputs, we can use this
  technique to construct a full social welfare ordering

#### But… Isn’t Plurality Monotonic?

Plurality satisfies weak PE and ND, so it must not be monotonic.
Consider the following preferences:

3 agents: $a \succ b \succ c$

2 agents: $b \succ c \succ a$

2 agents: $c \succ b \succ a$

Plurality chooses $a$

Increase support for $a$ by moving $c$ to the bottom:

3 agents: $a \succ b \succ c$

2 agents: $b \succ c \succ a$

2 agents: $b \succ a \succ c$

Now plurality chooses $b$

- So answer is No!

## 8-6 Single-Peaked Preferences

- Sometimes voters’ preferences have nicer properties

- Prominent case: candidates can be ordered from left to right

- Voters: have a most-preferred candidate and then candidates who are
  more extreme are less-preferred

## Resource

Game Theory II: Advanced Applications
<https://www.coursera.org/learn/game-theory-2>
