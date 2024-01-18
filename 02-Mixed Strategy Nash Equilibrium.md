02 - Mixed-Strategy Nash Equilibrium
================
Yeonju Kim
2024-01-19

# 2-1 Mixed Strategies and Nash Equilibrium

### Mixed Strategies

- It would be a pretty bad idea to play any deterministic strategy in
  matching pennies
- Idea: confuse the opponent by playing **randomly** \_ Define a
  **strategy** $s_i$ for agent $i$ as any probability distribution over
  the actions $A_i$.
  - **pure strategy**: only one action is played with positive
    probability
  - **mixed strategy**: more than one action is played with positive
    probability
    - these actions are called the **support** of the mixed strategy
- Let the set of **all strategies** for $i$ be $S_i$
- Let the set of **all strategy profiles** be
  $S =S_1 \times ... \times S_n$

### Utility under Mixed Strategies

- What is your **payoff** if all the players follow mixed strategy
  profile $s \in S$? We can’t just read this number from the game matrix
  anymore: we won’t always end up in the same cell

- Instead, use the idea of **expected utility** from decision theory:

$$
u_i(s) = \sum_{a \in A}u_i(a)Pr(a|s) \\
Pr(a|s) = \prod_{j \in N}s_j(a_j)
$$

### Best Response and Nash Equilibrium

- Our definitions of best response and Nash equilibrium generalize from
  actions to strategies

Definition (Best response)  
$$
s_i^* \in BR(s_{-1}) \text{ iff } \forall s_i \in S_i, u_i(s_i^*,s_{-i}) \ge u_i(s_i,s_{-i})
$$

Definition (Nash equilibrium)  
$$
s=<s_1,...,s_n> \text{is a Nash equilibrium iff } \forall i, s_i \in BR(s_{-i})
$$

Theorem (Nash, 1950)  
*Every finite game has a Nash equilibrium*

### Example: Matching Pennies

Even thou there is no pure strategy Nash eqilibrium in matching pennies
game, there is a mixed strategy Nash equilibrium. It is probability of
(0.5,0.5) for Head and Tail

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

### Example: Coordination

Mixed stretegy Nash equilibrium for Coordination game is the probability
of (0.5,0.5) again

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

### Example: Prisoner’s Dilemma

All of the strategies (C,C), (C,D), (D,C), (D,D) are mixed strategy Nash
equilibrium for Prisoner’s Dilemma

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

# 2-2 Computing Mixed Nash Equilibrium

### Battle of the Sexes

- It’s hard in general to compute Nash equilibria, but it’s easy when
  you can guess the **support**

- For Battle of the Sexes, let’s look for an equilibrium where all
  actions are part of the support

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

- Let player 2 play B with p, F with 1-p
- If player 1 best-responds with a mixed strategy, player 2 must make
  him indifferent between F and B

$$
u_1(B) = u_1(F) \\
2p+0(1-p)=0p+1(1-p) \\
p=\frac{1}{3}
$$

- Likewise, player 1 must randomize to make player 2 indifferent

  - Why is player 1 willing to randomize?

- Let player 1 play B with q, F with 1-q $$
  u_2(B) = u_2(F) \\
  q+0(1-q)=0q+2(1-q) \\
  q=\frac{2}{3}
  $$

- Thus the mixed strategies \$(,),(,) \$ are a Nash equilibrium

### Interpreting Mixed Strategy Equilibria

What does it mean to play a mixed strategy? Different interpretations:

- Randomize to **confuse** your opponent

  - consider the matching pennies example

- Randomize when **uncertain** about the other’s action

  - consider battle of the sexes

- Mixed strategies are a concise description of what might happen in
  **repeated play**: count of pure strategies in the limit

- Mixed strategies describe **population dynamics**: 2 agents chosen
  from a population, all having deterministic strategies. Mixed strategy
  gives the probability of getting each Pure Strategy

# 2-3 Hardness Beyond 2x2 Games - Basic

### Algorithms

Two example algorithms for finding NE

- LCP (Linear Complementarity) formulation
  - [Lemke-Howson, 1964](https://www.jstor.org/stable/2946376)
- Support Enumeration Method
  - [Porter et al.,
    2008](https://www.sciencedirect.com/science/article/abs/pii/S0899825606000935)

### From Algorithms to Complexity Analysis

Still, finding even a single NAsh equilibrium seems hard; how do we
capture that?

- Enter PPAD (“Polynomial Parity Arguments on Directed graphs”)
  - [Papadimitriou,
    1994](https://books.google.lt/books/about/Computational_Complexity.html?id=JogZAQAAIAAJ&redir_esc=y)
- At a high level:
  - FNP problems are constructive versions of NP problems (F stands for
    “Functional”)
  - TFNP is a subclass of FNP for problems for which a solution is
    guaranted to exist (T stands for “Total”)
  - PPAD is a subclass of TFNP where the proofs are based on parity
    arguments in directed graphs

### The Complexity of the Nash Equilibrium

**Theorem**  
Computing a Nash equilibrium is PPAD-complete… - for games with $\ge 4$
players; \[Daskalakis, Goldberg, Papadimitriou, 2005\] - for games with
3 players; \[Chen, Deng, 2005\] & \[Daskalakis, Papadimitriou, 2005\] -
for games with 2 players; \[Chen, Deng 2006\]

# 2-4 Hardness Beyond 2x2 Games - Advanced

### Early History

- 1928 von Neumann: existence of Equilibrium in 2-player, zero-sum games
  - proof uses Brouwer’s fixed point theorem;
  - led directly to algorithms:
    - Danzig 1957: equivalent to LP duality
    - Khachiyan 1979: polynomial-time solvable
- 1950 Nash: existence of Equilibrium in multiplayer, general-sum games
  - proof also uses Brouwer’s fixed point theorem;
  - intense effort on equilibrium algorithms:
    - Kuhn 1996, Mangasarian 1964, **Lemke-Howson, 1964**, Rosenmuller
      1971, …
  - …all exponential in the worst case

### The Lemke-Howson Algorithm

- LCP (Linear Complementarity) formulation

$$
\sum_{k \in A_2}u_1(a_1^j,a_2^k)s_2^k + r_1^j = U_1^* , \forall j \in A_1 \\
\sum_{k \in A_1}u_2(a_1^j,a_2^k)s_2^k + r_1^j = U_2^* , \forall j \in A_2 \\
\sum_{k \in A_1}s_1^j=1 \\
\sum_{k \in A_2}s_2^k=1 \\
\\
s_1^j \ge 0,s_2^k \ge 0,\forall j \in A_1, \forall k \in A_2 \\
r_1^j \ge 0,r_2^k \ge 0,\forall j \in A_1, \forall k \in A_2 \\
r_1^j \times s_1^j =0,r_2^j \times s_2^j =0,\forall j \in A_1, \forall k \in A_2 \\
$$

### Support Enumeration Method: Porter et al. 2004

- Step 1: Finding a NE with a specific support

$$p(a\*{-i})u_i(a_i,a\_{-i}) = v_i, i , a_i \_i \\ \\

p(a\*{-i})u_i(a_i,a\_{-i}) v_i, i , a_i \_i \\

p_i(a_i) , i , a_i \_i \\ p_i(a_i) = 0, i , a_i \_i \\

p_i(a\*{i}) = 1, i $$

- Step 2: Smart heuristic search through all sets of support

### From Algorithms to Complexity Analysis

So, is it NP-conplete to find a Nash equilibrium?

- Strictly speaking, no, since a solution is guaranteed to exist…

- However, it is NP-complete to find a “tiny” bit more info than a Nash
  equilibrium; e.g. the following are NP-complete:

  - (**Uniqueness**): Given a game $G$, does there exist a unique
    equilibirum in $G$?
  - (**Pareto optimality**): Given a game $G$, does there exist a
    strictly Pareto efficient equilibrium in $G$?
  - (**Guaranteed payoff**): Given a game $G$ and a value $v$, does
    there exist an equilibrium in which the sum of agents’ utilies is at
    least $k$?
  - (**Action inclusion**): Given a game $G$, and an action
    $a_i \in A_i$ for some player $i \in N$, does there exist an
    equilibrium of $G$ in which player $i$ plays action $a_i$ with
    strictly positive probability?
  - (**Action exclusion**): Given a game $G$ and an action $a_i \in A_i$
    for some player $i \in N$, does there exist an equilibrium of $G$ in
    which player $i$ plays action $a_i$ with zero probability?

# 2-5 Example: Mixed Strategy Nash

### Example - Soccer Penalty Kicks

- Mixed strategies in sports and competitive games
- Be unpredictable
- How do equilibrium strategies adjust to skills?
- Should a kicker who kicks penalty kicks worse to the right than left
  kick more often to the left than right?

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
0,1 & 1,0  \\
1,0 & 0,1 \end{array}
\right]\end{array}
$$

</div>

In this example, equilibrium is (0.5,0.5)

There is an another example

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
0,1 & 1,0  \\
0.75,0.25 & 0,1 \end{array}
\right]\end{array}
$$

- In a mixed equilibrium, the goalie’s strategy must have the kicker
  indifferent

- $p$ probability goalie goes left; Kicker indifferent: $(1-p)1=0,75p$
  or $p=1/1.75=4/7$

- Goalie goes Left more often than Right (4/7 to 3/7), kicker goes Right
  with 4/7

- Goalie’s strategy adjusts, and the kicker actually adjusts to kick
  more to their weak side!

- The Goalie has a slight advantage now, and wins 4/7 of the time

- If the goalie still played equal probability, then the kicker could
  always go left and win 1/2 the time instead of 3/7

- By adjusting the strategy to keep the kicker indifferent, the Goalie
  takes advantage of the kicker’s weak right kick and wins more often!

### Summary

- A players must be indifferent between the actions he or she randomizes
  over

- Interesting comparative statics

- Do players really do this? -\> Next Topic

# 2-6 Data: Professional Sports and Mixed Strategies

- Some counter-intuitive features…
- Do people really play them?

### Professional Soccer - Penalty Kicks

- Ignacio Palacios-Heurta (2003) “Professionals Play Minimax” \_Review
  of Economic Studies”, Volume 70, pp385-415

- 1417 Penalty kicks from FIFA games: Spain, England, Italy…

- Ignacio considers left, cent, or right choices, and considered which
  leg the kicker used; I will keep it down to left and right choices
  (his page 402) ignoring kicker’s leg

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
0.58,0.42 & 0.95,0.05  \\
0.93,0.07 & 0.70,0.30 \end{array}
\right]\end{array}
$$

Note that Row player is **Kicker**, and column player is **Goalie**

- The Goalie’s probability of going Left $p_G$ versus Right $1-p_G$ must
  have kicker indifferent

- $0.58p_G+0.95(1-p_G)=0.93p_G+0.7(1-p_G)$ or $0.25(1-p_G)=0.35p_G$ or
  $p_G=5/12=0.42$

- The Kicker’s probability of going Left $p_K$ versus Right $1-p_K$ must
  have goalie indifferent

- $0.42p_K+0.07(1-p_K)=0.05p_K+0.3(1-p_K)$ or $0.23(1-p_K)=0.37p_K$ or
  $p_K=23/60=0.38$

### Soccer Penalty Kicks - The Data

$$
\begin{array}{cccc} &
\begin{array}{cccc} \text{G Left} & \text{G Right} & \text{K Left} & \text{K Right} \end{array}
\\
\begin{array}{cccc}
\text{Nash Freq.} \\
\text{Actual Freq.} \\
\end{array}
&
\left[
\begin{array}{cccc}
0.42 & 0.58 & 0.38 & 0.62  \\
0.42 & 0.58 & 0.40 & 0.60 \end{array}
\right]\end{array}
$$

### Mixed Strategies

- Do players randomize well over time? Pretty well…

- How about under pressure? Do they become predictable?
  Statisticians/Game Theorists starting to keep them honest…

- Other sports: Tennis players and serves, M. Walker and J.Wooders,
  American Economic Review (2001) “Maximax Play and Wimbeldom” Volume
  91, pp1521-1538

### Summary

- Some games have mixed strategy equilibria
- A players must be indifferent between the actions he or she randomizes
  over
- Interesting comparative statics
- Do see randomization:
  - in (professional) sports
  - in nature: which way a squirrel runs to get out of your way
  - in society and business interactions: audits by tax authorities

### Resources

Game Theory: <https://www.coursera.org/learn/game-theory-1>
