System Model
============

This section details the model currently used to describe Bitswap in this work.
\cref{network-graph} models the IPFS network as a graph; \cref{reputation}
mathematically describes the peer-wise reputations and user interactions; and
\cref{game-formulation} formulates the problem as a game.

Network Graph
-------------

We model an IPFS swarm as a network \Network of $\abs{\Network}$ users. The
graphical representation consists of

-   *nodes* representing users, and
-   *unweighted, undirected edges*, each of which represents a peering between
    two users.

A user's *neighborhood* is their set of peers, i.e. the set of nodes that the
user is connected to by an edge. User $i$'s neighborhood is denoted by
$\Nbhd{i}$, where $\Nbhd{i} \subseteq \Network$.

Reputation
----------

We break Bitswap interactions into discrete rounds, with a single round denoted
by a nonnegative integer $t$. The following two points describe the way data
distribution takes place in this Bitswap model. Each of these points simplifies
the problem from the real-world scenario.

1.  Each user $j$ distributes exactly $B_j$ bits, where $B_j > 0$, to each of
    their peers in a given round (and has sufficient resources to do so).
2.  All users always have unique data that all of their peers want. So, when a
    user allocates $b$ bits to a particular peer, that user has at least $b$
    bits that the peer wants.

We define $b_{ij}^t$ as the total number of bits sent from user $i$ to peer $j$
from round $0$ to $t-1$. User $i$ maintains a Bitswap *ledger* $l_{ij}^t$, for
each of its peers $j \in \Nbhd{i}$, that stores the amount of data exchanged in
both directions, i.e. $l_{ij}^t = (b_{ij}^t, b_{ji}^t)$.

Now we define the *debt ratio* $d_{ji}$ from user $i$ to peer $j$ as

$$
d_{ji}^t = \frac{b_{ij}^{t-1}}{b_{ji}^{t-1}\:+\:1}
$$

$d_{ji}^t$ can be thought of as peer $i$'s reputation from the perspective of
user $j$. This reputation is then considered by user $j$'s *reputation function*
$S_j(d_{ji}^t, \mathbf{d}_j^{-i,t}) \in \{0, 1\}$, where
$\mathbf{d}_j^{-i,t} = (d_{jk}^t \mid \forall k \in \Nbhd{j}, k \neq i)$ is the
vector of debt ratios for all of user $j$'s peers in round $t$ *excluding* peer
$i$. The reputation function considers the relative reputation of peer $i$ to
the rest of $j$'s peers, and returns a weight for peer $i$. This weight is used
to determine what proportion of $j$'s resources to allocate to peer $i$ in round
$t$. This means that the following must hold:

$$
\sum_{i \in \Nbhd{j}} S_j(d_{ji}^t, \mathbf{d}_j^{-i,t}) = 1
$$

In other words, the sum of the weights that $j$ assigns to its peers must be $1$
(otherwise, $j$ would allocate more than its available bandwidth to its peers).

Given all of this, we can calculate $b_{ji}^{t+1}$ given $b_{ji}^t$, $d_{ji}^t$,
and $\mathbf{d}_j^{-i,t}$:

$$
b_{ji}^{t+1} = b_{ji}^{t} + S_j(d_{ji}^t, \mathbf{d}_j^{-i,t}) \times B_j
$$

Game Formulation
----------------

The game model presented here is the product of multiple iterations that
approached a balance between the accuracy of the model to the problem and model
complexity. Previous modeling approaches included tools from evolutionary game
theory and statistical mechanics on the high complexity end, and repeated games
on the low accuracy end. While the current model uses a repeated game model as
well, the strategy space has been modified to better fit the Bitswap
scenario.[^old-model-link]

[^old-model-link]: A description of the model from the previous iteration can be
found at <https://github.com/dgrisham/masters/tree/master/deprecated/analysis>.

All users in the network participate in the Bitswap game. The players in this
game are the users in the IPFS network, and each player's strategy is the
reciprocation function they choose to assign weights to their peers. The
strategy space, then, is the space containing all pure functions of the form
$S_j(d_{ji}^t, \mathbf{d}_j^{-i,t}) \in \{0, 1\}$. The Bitswap game is an
*infinitely repeated*, *incomplete information* game in which users exchange
data. One game takes place between each pair of peers for each round $t$. The
*players* are the IPFS users in the network \Network. The utility of player $i$
in round $t$ is the sum of all of the data that $i$ is sent by its peers in that
round:

$$
u_i^t = \sum_{j \in \Nbhd{i}} (b_{ji}^t - b_{ji}^{t-1})
$$

The total utility of a peer over the entire repeated game, then, can be
expressed in the following ways:

\begin{align*}
U_i &= \sum_{t=0}^{\infty} u_i^t \\
U_i &= \sum_{j \in \Nbhd{i}} b_{ji}^\infty
\end{align*}

The latter representation can be most directly thought of as the total amount of
data that peer $i$ receives from all of its peers over the entire duration of
the Bitswap game.
