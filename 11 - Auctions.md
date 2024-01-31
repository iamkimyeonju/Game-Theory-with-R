11 - Auctions
================

## 11-1 Auction: Taxonomy

#### Motivation

- Auctions are any mechanisms for **allocating resources among
  self-interested agents**

- Very widely used

  - government sale of resources

  - privatization

  - stock market

  - request for quote

  - FCC spectrum

  - real estate sales

  - eBay

#### Some Canonical Auctions

- English

- Japanese

- Dutch

- First-Price

- Second-Price

- All-Pay

#### English Auction

- auctioneer starts the bidding at some “reservation price”

- bidders then shout out ascending prices

- once bidders stop shouting, the high bidder gets the good at that
  price

#### Japanese Auction

- Some as an English auction expect that the auctioneer calls out the
  prices

- all bidders start out standing

- when the price reaches a level that a bidder is not willing to pay,
  that bidder sits down

  - once a bidder sits down, they can’t get back up

- the last person standing gets the good

- analytically more tractable than English than because jump bidding
  can’t occur

  - consider the branching factor of the extensive form game

#### Dutch Auction

- the auctioneer starts a clock at some high value; it descends

- at some point, a bidder shouts “mine!” and gets the good at the price
  shown on the clock

#### First-Price Auction

- bidders write down bids on pieces of paper

- auctioneer awards the good to the bidder with the highest bid

- that bidder pays the amount of his bid

#### Second-Price Auction

- bidders write down bids on pieces of paper

- auctioneer awards the good to the bidder with the highest bid

- that bidder pays the amount bid by the second-highest bidder

#### All-Pay Auction

- bidders write down bids on pieces of paper

- auctioneer awards the good to the bidder with the highest bid

- everyone pays the amount of their bid regardless of whether or not
  they win

#### Auctions as Structured Negotiations

Any negotiation mechanism that is:

- **market-based** (determines as exchange in terms of currency)

- **mediated** (auctioneer)

- **well-specified** (follows rules)

Defined by three kinds of rules:

- bidding

  - who can bid, when

  - what is the form of a bid

  - restrictions on offers, as a function of:

    - bidder’s own previous bid

    - auction state (others’ bids)

    - eligibility (e.g., budget constraints)

    - expiration, withdrawal, replacement

- what information is revealed

  - when to real what information to whom

- clearing

  - when to clear

    - at intervals

    - on each bid

    - after a period of inactivity

  - allocation (who gets what)

  - payment (who pays what)

## 11-2 Bidding in Second-Price Auctions

Theorem  
Truth-telling is a dominant strategy in a second-price auction

- Tbh, this is VCG mechnism

Proof  
Assume that the other bidders bid in some arbitrary way. We must show
that $i$’s best response is always to bid truthfully. We’ll break the
proof into two cases:

1.  Bidding honestly, $i$ would win the auction
    - If $i$ bids higher, he will still win and still pay the same
      amount

    - If $i$ bids lower, he will either still win and still pay the same
      amount… or lose and get utility of zero
2.  Bidding honestly, $i$ would lose the auction
    - If $i$ bids lower, he will still lose and still pay nothing

    - If $i$ bids higher, he will either still lose and still pay
      nothing, or win and pay more than his valuation

#### English and Japanese Auctions

- A **much more complicated** strategy space

  - extensive form game

  - bidders are able to condition their bids on information revealed by
    others

  - in the case of English auctions, the ability to place jump bids

- intuitively, though, the revealed information doesn’t make any
  difference in the IPV setting

Theorem  
Under the independent private values model (IPA), it is a **dominant
strategy** for bidders to bid up to (and not beyond) their valuations in
both Japanese and English auctions

## 11-3 Bidding in First-Price Auctions

#### Equivalence of First-Price and Dutch Auctions

Theorem  
First-Price (sealed bid) and Dutch auctions are **strategically
equivalent**

- In both, a bidder must decide on the amount s/he’s willing to pay,
  conditional on it being the highest bid

  - Dutch auctions are extensive-form games, but the only thing a
    winning bidder knows is that all others have not to bid higher

  - Same as a bidder in a first-price auction

- So, why are both auction types used?

  - First-price auctions can be held **asynchronously**

  - Dutch auctions are fast, and require **minimal communication**: only
    one bit needs to be transmitted from the bidders to the auctioneer

#### Discussion

- How should bidders bid in these auctions?

  - Bid **less than valuation**

    - probability of winning

    - amount paid upon winning

  - Bidders don’t have a dominant strategy

#### Analysis

Theorem  
In a first-price auction with two risk-neutral bidders whose valuations
are IID and drawn from $U(0,1), (\frac{1}{2}v_1,\frac{1}{2}v_2)$ is a
Bayes-Nash equilibrium strategy profile

- IID (Independent and identical distributed)

Proof  
Assume that bidder 2 bids $\frac{1}{2}v_2$, and bidder 1 bids $s_1$. 1
wins where $v_2 < 2s_1$, and gains utility $v_1-s_1$, but loses when
$v_2 >2s_1$ and then gets utility 0: (we can ignore the case where the
agents have the same valuation, because this occurs with probability
zero)

$$
E[u_1]= \int_{0}^{2s_1}(v_1-s_1)dv_2+ \int_{2s_1}^{1}(0)dv_2 \\
= (v_1-s_1)v_2|_{0}^{2s_1} \\
= 2v_1s_1 - 2s_1^2
$$

We can find bidder 1’s best response to bidder 2’s strategy by taking
the derivative of (1) and setting it equal to zero

$$
\frac{\partial}{\partial s_1}(2v_1s_1 - 2s_1^2) =0 \\
2v_1 -4s_1 =0 \\
s_1 = \frac{1}{2}v_1
$$

Thus when player 2 is bidding half her valuation, player 1’s best reply
is to bid half his valuation. The calculation of the optimal bid for
player 2 is analogous, given the symmetry of the game

#### More than two bidders

- Narrow result: two bidders, uniform valuations

- Still, first-price auctions are not incentive compatible as direct
  mechanisms

  - Need to solve for equilibrium

Theorem  
In a first-price sealed bid auction with $n$ risk-neutral agents whose
valuations are independently drawn from a uniform distribution on
$[0,1]$ the (unique) symmetric equilibrium is given by the strategy
profile $(\frac{n-1}{n}v_1, ..., \frac{n-1}{n}v_n)$

- proven using similar argument

- A broader problem: the proof only *verified* an equilibrium strategy

  - How do we find the equilibrium?

## 11-4 Revenue Equivalence

#### Revenue Equivalence

- Which auction? To some extent, it doesn’t matter

Theorem (Revenue Equivalence Theorem)  
Assume that each of $n$ risk-neutral agents has an independent private
valuation for a single good at auction, each drawn from cumulative
distribution $F$. Then any two auction mechanisms in which

- in equilibrium, the good is always allocated in the same way; and

- any agent with valuation 0 has an expected utility of 0

both yield the same expected revenue, and both result in any bidder with
valuation $v$ making the same expected payment

In fact, this even holds beyond IPV (independent private value) and
single good

#### First and Second-Price Auctions

- The $k^{th}$ **order statistic** of a distribution: the expected value
  of the $k^{th}$-largest of $n$ draws

- For $n$ IID draws from $[0,v_{max}]$, the $k^{th}$ order statistic
  $\frac{n+1-k}{n+1}v_{max}$

- Thus in a second-price auction, the seller’s expected revenue is
  $\frac{n-1}{n+1}v_{max}$

- First and second-price auctions satisfy the requirements of the
  revenue equivalence theorem

  - every symmetric game has a symmetric equilibrium

  - in a symmetric equilibrium of this auction game, higher bid
    $\Leftrightarrow$ higher valuation

#### Applying Revenue Equivalence

- Thus, a bidder in a FPA must bid his expected payment conditional on
  being the winner of a second-price auction

  - this conditioning will be correct if he does win the FPA; otherwise
    his bid doesn’t matter anyway

  - if $v_i$ is the high value, there are then $n-1$ other values drawn
    from the uniform distribution on $[0,v_i]$

  - thus, the expected value of the second-highest bid is the
    first-order statistic of $n-1$ draws from $[0,v_i]$:

    $$
    \frac{n+1-k}{n+1}v_{max}=\frac{(n-1)+1-(1)}{(n-1)+1}(v_i)=\frac{n-1}{n}v_i
    $$

  - This shows how we derived our earlier claim about $n$-bidder
    first-price auctions

#### Proving Revenue Equivalence

- $\chi_i(v_i|s): i$’s **ex interim allocation probability** given type
  $v_i$, everyone following equilibrium strategy $s$

- $p_i(v_i|s): i$’s **ex interim expected payment**

Theorem (Bayes-Nash Equilibrium Characterization)  
When values are drawn from a continuous joint distribution $F$ and
agents are risk neutral, a strategy profile $s$ is in Bayes-Nash
equilibrium only if for all $i$:

1.  (monotonicity) $\chi_i(v_i|s)$ is monotone non-decreasing, and
2.  (payment identity)
    $p_i(v_i|s) = v_i\chi_i (v_i|s)-\int_0^{v_i}\chi_i(z|s)dz+p_i(0|s)$,
    where often $p_i(0|s)=o$. If $s$ is onto then the converse also
    holds

#### Conclusion

- If two mechanisms have the same allocation rule, they need to have
  (essentially) the same payment rule too

- A key corollary: all efficient auctions yield the same revenue in
  equilibrium

- This applies to some pretty strange auction types: 3rd price, auctions
  in which losers have to pay, etc

- Do note: we need risk neutrality for revenue equivalence

## 11-5 Optimal Auctions

- So far we have considered efficient auctions

- What about maximizing the seller’s revenue?

  - s/he may be willing to risk failing to sell the good

  - s/he may be willing sometimes to sell to a buyer who didn’t make the
    highest bid

#### Optimal auctions in an independent private values setting

- private valuations

- risk-neutral bidders

- each bidder $i$’s valuation independently drawn from a strictly
  increasing cumulative distribution function $F_i(v)$ with a pdf
  $f_i(v)$ that is continuous and bounded below

  - Allow $F_i \not= F_j:$ asymmetric auctions

- the risk neutral seller knows each $F_i$ and has no value for the
  object

The auction that maximizes the seller’s expected revenue subject to (ex
post, interim) individual rationality and Bayesian incentive
compatbility for the buyers is an **optimal auction**

#### Example: An Optimal Reserve Price in a Second Price Auction

- 2 bidders, $v_i$ uniformly distributed on $[0,1]$

- Set reserve price $R$ and then run a second price auction:

  - no sale if both bids below $R$

  - sale at price $R$ if one bid above reserve and other below

  - sale at second highest bid if both bids above reserve

- Which reserve price $R$ maximizes expected revenue?

- still dominant strategy to bid true value, so:

  - no sale if both bids below $R$ - happens with probability \$R^2% and
    revenue = 0

  - sale at price $R$ if one bid above reserve and other below - happens
    with probability $2(1-R)R$ and revenue = 0

  - sale at second highest bid if both bids above reserve - happens with
    probability $(1-R)^2$ and revenue
    $= E[\min v_i|\min v_i \ge R] = \frac{1+2R}{3}$

- Expected revenue $=2(1-R)R^2+(1-R)^2 \frac{1+2R}{3}$

- Expected revenue $=\frac{1+3R^2-4R^3}{3}$

- Maximizing: $0=2R-4R^2$, or $R=\frac{1}{2}$

- Reserve price of 1/2: revenue =5/12, Reserve price of 0: revenue = 1/3

- Tradeoffs:

  - lose sales when both bids were below 1/2 - but low revenue then in
    any case and probability 1/4 of happening

  - increase price when one bidder has low value other high: happens
    with probability 1/2

- Like adding another bidder: increasing competition in the auction

#### Designing Optimal Auctions

Definition (Virtual Valuation)  
Bidder $i$’s **virtual valuation** is
$\psi_i(v_i)=v_i-\frac{1-F_i(v_i)}{f_i(v_i)}$

Let us assume this is increasing in $v_i$ (e.g., for a uniform
distribution it is $2v_i -1$)

Definition (bidder-specific reserve price)  
Bidder $i$’s bidder-specific reserve price $r_i^*$ is the value for
which $\psi_i(r_i^*) =0$

#### Myerson’s Optimal Auctions

Theorem (Myerson, 1981)  
The optimal (single-good) auction in terms of a direct mechanism: The
good is sold to the agent $i=arg \max_i \psi_i(\hat{v_i})$, as long as
$v_i \ge r_i^*$. If the good is sold, the winning agent $i$ is charged
the smallest valuation that he could have declared while still remaining
the winner:

$$
\inf\{ v_i^*: \psi_i(v_i^*) \ge 0 \text{ and } \forall j \not=i, \psi_i(v_i^*)\ge\psi_j(\hat{v_j)}\}
$$

Corollary (Myerson, 1981)  
In a symmetric setting, the optimal (single-good) auction is a second
price auction with a reserve price of $r^*$ that solves
$r^* - \frac{1-F(r^*)}{f(r^*)}=0$

#### Analyzing optimal auctions

Optimal Auction  
- winning agent: $i=\arg\max_i \psi_i(\hat{v_i})$, as long as
  $v_i \ge r_i^*$

- $i$ is charged the smallest valuation that he could have declared
  while still remaining the winner,

  $$
  \inf\{ v_i^*: \psi_i(v_i^*) \ge 0 \text{ and } \forall j \not=i, \psi_i(v_i^*)\ge\psi_j(\hat{v_j)}\}
  $$

- Is this VCG?

  - No, it’s not efficient

- How should bidders bid?

  - it’s a second-price auction with a reserve price, held in virtual
    valuation space

  - neither the reserve prices nor the virtual valuation transformation
    depends on the agent’s declaration

  - thus the proof that a second-price auction is dominant-strategy
    truthful applies here as well

- Why does this work?

  - reserve prices are like compatitors: increase the payments of
    winning bidders

  - the virtual valuations can increase the impact of weak bidders’
    bids, making them more competitive

  - bidders with higher expected valuations bid more aggressively

## Resource

Game Theory II: Advanced Applications
<https://www.coursera.org/learn/game-theory-2>
