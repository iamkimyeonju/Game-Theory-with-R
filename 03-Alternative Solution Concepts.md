03 - Alternative Solution Concepts
================
Yeonju Kim
2024-01-19

# 3-1 Beyond the Nash Equilibrium

- **Dominated Strategies**: Should Grace celebrate her 91st birthday by
  jumping out of a plane strapped to a guy?

- **Zero-Sum Game**: Is he really solving for the Nash equilibrium

- **Battle of the Sexes**: either unfairness or miscoordination?

# 3-2 Strictly Dominated Strategies & Iterative Removal

### Rationality

- A basic premise: players maximize their payoffs
- What if all players know this?
- And they know that other players know it?
- And they know that other players know that they know it?
- …

### Strictly Dominated Strategies

- A strictly dominated strategy can never be a best reply

- Let us remove it as it will not be player

- All players know this - so let us iterate…

- Running this process to termination is called the **iterated removal
  of strictly dominated strategies**

- A strategy $a_i \in A_i$ is strictly dominated by $a_i^{'} \in A_i$,
  if

$$
u_i(a_i,a_{-i}) < u_i^{'}(a_i,a_{-i}), \forall a_{-i} \in A_{-i} 
$$

### Iterated Removal of Strictly Dominated Strategies: Example

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & C & R \end{array}
\\
\begin{array}{cccc}
U\\
M \\
D \\
\end{array}
&
\left[
\begin{array}{cccc}
3,0 & 2,1 & 0,0 \\
1,1 & 1,1 & 5,0 \\
0,1 & 4,2 & 0,1 \end{array}
\right]\end{array}
$$

- $R$ is strictly dominated by $C$

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & C  \end{array}
\\
\begin{array}{cccc}
U\\
M \\
D \\
\end{array}
&
\left[
\begin{array}{cccc}
3,0 & 2,1 \\
1,1 & 1,1 \\
0,1 & 4,2 \end{array}
\right]\end{array}
$$

- $M$ is strictly dominated by $U$

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & C  \end{array}
\\
\begin{array}{cccc}
U\\
D \\
\end{array}
&
\left[
\begin{array}{cccc}
3,0 & 2,1 \\
0,1 & 4,2 \end{array}
\right]\end{array}
$$

- $L$ is strictly dominated by $C$

$$
\begin{array}{ccc} &
\begin{array}{ccc} C  \end{array}
\\
\begin{array}{cccc}
U\\
D \\
\end{array}
&
\left[
\begin{array}{cccc}
 2,1 \\
 4,2 \end{array}
\right]\end{array}
$$

- $U$ is strictly dominated by $D$

$$
\begin{array}{ccc} &
\begin{array}{ccc} C  \end{array}
\\
\begin{array}{cccc}
D \\
\end{array}
&
\left[
\begin{array}{cccc}
 4,2 \end{array}
\right]\end{array}
$$ - There is a unique Nash equilibrim of (D,C)

### Iterated Removal of Strictly Dominated Strategies: Another Example

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & C & R \end{array}
\\
\begin{array}{cccc}
U\\
M \\
D \\
\end{array}
&
\left[
\begin{array}{cccc}
3,1 & 0,1 & 0,0 \\
1,1 & 1,1 & 5,0 \\
0,1 & 4,1 & 0,0 \end{array}
\right]\end{array}
$$

- $R$ is dominated by $L$ or $C$

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & C \end{array}
\\
\begin{array}{cccc}
U\\
M \\
D \\
\end{array}
&
\left[
\begin{array}{cccc}
3,1 & 0,1  \\
1,1 & 1,1  \\
0,1 & 4,1  \end{array}
\right]\end{array}
$$

- $M$ is dominated by the mixed strategy that selects $U$ and $D$ with
  equal probability

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & C \end{array}
\\
\begin{array}{cccc}
U\\
D \\
\end{array}
&
\left[
\begin{array}{cccc}
3,1 & 0,1  \\
0,1 & 4,1  \end{array}
\right]\end{array}
$$

- No other strategies are strictly dominated

- What are the Nash Equilibrium?

### Iterated Removal of Strictly Dominated Strategies

- This process preserves Nash **equilibria**
  - It can be used as a **preprocessing step** before computing an
    equilibrium
  - Some games are solvable using this technique - those games are
    **dominance solvable**
- What about the **order of removal** when there are multiple strictly
  dominated strategies?
  - doesn’t matter

### Weak Dominated Strategies

- A strategy $a_i \in A_i$ is **weakly dominated** by $a_i^{'} \in A_i$
  if

$$
u_i(a_i,a_{-i}) \le u_i^{'}(a_i,a_{-i}) \text{ for all } a_{-i} \in A_{-i} 
$$ and $$
u_i(a_i,a_{-i}) < u_i^{'}(a_i,a_{-i}) \text{ for some } a_{-i} \in A_{-i} 
$$

- Can remove them iteratively too, but:

  - They can be best replies
  - Order of removal can matter
  - At least one equilibrium preserved
  - Remember the Keynes Beauty Contest Game? Can you solve it via
    iterative elimination of Weakly Dominated Strategies?

### Summary

- Players maximize their payoffs
- They don’t play *strictly* dominated strategies
- They don’t play *strictly* dominated strategies, given what remains
- Nash equilibria are a subset of what remains
- Do we see such behavior in reality?

# 3-3 Dominated Strategies & Iterative Removal: An Application

### Feeding Behavior among Pigs and Iterative Strict Dominance

- Experiment by B.A Baldwin and G.B Meese (1979) “Social Behavior in
  Pigs Studied by Means of Operant Conditioning” *Animal Behavior*
  Volume 27, pp947-957.
- Two pigs in a cage, one is larger: “dominant”
- need to press a lever to get food to arrive
- food and lever are at opposite sides of cage
- run to press and the other pig gets the food

10 units of food - the typical split:

- if large gets to food first then (1,9) split (1 for small, 9 for
  large)

- if small gets to food first then (4,6) split,

- if gets to food at the same time then (3,7) split

- Pressing the lever costs 2 units of food in energy

$$
\begin{array}{ccc} &
\begin{array}{ccc} Press & Wait  \end{array}
\\
\begin{array}{cccc}
Press\\
Wait \\
\end{array}
&
\left[
\begin{array}{cccc}
1,5 & -1,9 \\
4,4 & 0,0 \end{array}
\right]\end{array}
$$

Note that row player is small pig, and column player is large pig

Let us solve via iterative elimination of strictly dominated strategies:

- For small pig, Press is strictly dominated by Wait
- For large pig, Wait is strictly dominated by Press
- Only left (4,4)

### Pigs Behavior: Frequency of pushing the lever per 15 minutes, after ten tests (learning…) Baldwin and Meese (1979)

$$
\begin{array}{ccc} &
\begin{array}{ccc} Alone & Together  \end{array}
\\
\begin{array}{cccc}
Large\\
Small\\
\end{array}
&
\left[
\begin{array}{cccc}
75 & 105 \\
70 & 5 \end{array}
\right]\end{array}
$$

### Iterative Strict Dominance

- Are pigs rational? Do they know game theory?
- They do seem to be learn and respond to incentives
- Learn not to play a strictly dominated strategy…
- Learn to not to play strictly dominated strategies out of what
  remains…
- Learning, evolution, and survival of the fittest: powerful game theory
  tools

# 3-4 Maxmin Strategies

- Player $i$’s **maxmin strategy** is a strategy that maxmize $i$’s
  worst-case payoff, in the situation where all the other players (whom
  we demote $-i$) happen to play the strategies which cause the greatest
  harm to $i$

- The **maxmin value** (or **safety level**) of the game for player $i$
  is that minimum payoff guaranteed by a maxmin strategy

Definition (Maxmin)  
The **maxmin strategy** for player $i$ is arg
$max_{s_i} min_{s_{-1}}u_i(s_1,s_2)$, and the maxmin value for player
$i$ is $max_{s_i} min_{s_{-1}}u_i(s_1,s_2)$

- Why would $i$ want to play a maxmin strategy?
  - a conervative agent maximizing worst-case payoff
  - a paranoid agent who believes everyone is out to get him

### Minmax Strategies

- Player $i$’s **minmax strategy** against player $-i$ in a 2-player
  game is a strategy that minimize $-i$’s best-case payoff, and the
  **minmax value** for $i$ against $-i$ is payoff

Definition (Minmax, 2-player)  
In a two-player game, the **minmax strategy** for player $i$ against
palyer $-i$ is arg $min_{s_{i}}max_{s_{-i}}u_{-i}(s_i,s_{-i})$, and
player $-i$’s **minmax value** is
$min_{s_{i}}max_{s_{-i}}u_{-i}(s_i,s_{-i})$, and player $-i$

- Why would $i$ want to play a minmax strategy?
  - to punish the other agent as much as possible

### Minmax Theorem

Theorem (von Neumann, 1928)  
In any finite, two-player, zero-sum game, in any Nash equilibrium each
player receives a payoff that is equal to both his maxmin value and his
minmax value.

1.  Each player’s maxmin value is equal to his minmax value. The maxmin
    value for player 1 is called the **value of the game**

2.  For both players, the set of maxmin strategies coincides with the
    set of minmax strategies

3.  Any maxmin strategy profile (or, equivalent, minmax strategy
    profile) is a Nash equilibrium. Furthermore, these are all the Nash
    equilibria. Consequently, all Nash equilibria have the same payoff
    vector (namely. those in which player 1 gets the value of the game)

### Computing Minmax

For 2 player minmax is solvable with LP (Linear Programming)

$$
\text{minimize } U_1^* \\ 
\text{subject to } \sum_{k \in A_2}u_1(a_1^j,a_2^k)s_2^k \le U_1^*  , \forall j \in A_1\\
\sum_{k \in A_2} s_2^k =1 \\
s_2^k \ge 0, \forall k \in A_2
$$

### 2 × 2 Zero-sum Games

- Minmax or maxmin produces the same result as method for finding NE in
  general 2 × 2 games;
- Check against penalty kick game
- Note that the row player is Kicker, and the column player is Goalie

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & R  \end{array}
\\
\begin{array}{cccc}
L\\
R\\
\end{array}
&
\left[
\begin{array}{cccc}
0.6,0.4 & 0.8,0.2 \\
0.9,0.1 & 0.7,0.3 \end{array}
\right]\end{array}
$$

- How does the kicker maximize his minimum?

$$
min_{s_2}[0.6 \cdot s_1(L)s_2(L)+0.8 \cdot s_1(L)s_2(R)+0.9 \cdot s_1(R)s_2(L)+0.7 \cdot s_1(R)s_2(R)] \\
= min_{s_2}[0.6 \cdot s_1(L)(1-s_1(L))+0.8 \cdot s_1(L)s_2(R)+0.9 \cdot (1-s_1(L))s_2(L)+0.7 \cdot (1-s_1(L))(1-s_2(L)) ] \\
= min_{s_2}[(0.2-s_1(L) \cdot 0.4) \cdot s_2(L) + (0.7+s_1(L) \cdot 0.1)] \\
$$ $$
0.2 - s_1(L) \cdot 0.4 = 0 \\
s_1(L) =1/2 , s_1(R)=1/2
$$

$$
\begin{array}{ccc} &
\begin{array}{ccc} L & R  \end{array}
\\
\begin{array}{cccc}
L\\
R\\
\end{array}
&
\left[
\begin{array}{cccc}
0.6,0.4 & 0.8,0.2 \\
0.9,0.1 & 0.7,0.3 \end{array}
\right]\end{array}
$$

- How does the goalie minimize the kicker’s maximum?

$$
min_{s_1}[0.6 \cdot s_1(L)s_2(L)+0.8 \cdot s_1(L)s_2(R)+0.9 \cdot s_1(R)s_2(L)+0.7 \cdot s_1(R)s_2(R)] \\
= min_{s_2}[0.6 \cdot s_1(L)s_2(L)+0.8 \cdot s_1(L)(1-s_2(L))+0.9 \cdot (1-s_1(L))s_2(L)+0.7 \cdot (1-s_1(L))(1-s_2(L)) ] \\
= min_{s_2}[(0.1-s_2(L) \cdot 0.4) \cdot s_1(L) + (0.7+s_2(L) \cdot 0.2)] \\
$$ $$
0.1 - s_2(L) \cdot 0.4 = 0 \\
s_2(L) =1/4 , s_2(R)=3/4
$$

# 3-5 Correlated Equilibrium: Intuition

### Example

- Consider again **Battle of the Sexes**

  - Intuitively, the best outcome seems a 50-50 split between (F,F),
    (B,B)

  - But there’s no way to achieve this, so either someone loses out
    (unfair) or both players often miscoordinate

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

- Another example: **Traffic Game**

$$
\begin{array}{cc} &
\begin{array}{cc} go & wait \end{array}
\\
\begin{array}{cc}
go \\
wait \\
\end{array}
&
\left[
\begin{array}{cc}
-10,-10 & 1,0  \\
0,1 & -1,-1 \end{array}
\right]\end{array}
$$

- What is the natural solution here?

  - A **traffic light**: a fair randomizing device that tells one of the
    agents to go and the other to wait

- Benefits:

  - the negative payoff outcomes are completely avoided
  - fairness is achieved
  - the sum of social welfare can exceed that of any Nash equilibrium

- We could use the same idea to achieve the fair outcome in battle of
  the sexes

- **Correlated Equilibrium** (informal): a randomized assignment of
  (potentially correlated) action recommendations to agents, such that
  nobody want to deviate

### Resources

Game Theory: <https://www.coursera.org/learn/game-theory-1>
