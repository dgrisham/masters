---
title: Game Theoretical Analysis of Resource Allocation in the InterPlanetary File System
author: David Grisham
date: TBD
theme: Amsterdam
...

Background
==========

IPFS (InterPlanetery File System)
---------------------------------

-   P2P hypermedia distribution protocol
-   Content-addressed, versioned filesystem
-   Git repo in a torrent
-   Many use-cases
    -   **Goal:** Replace HTTP, decentralize Internet

IPFS Stack
----------

\graphiccw{img/ipfs_stack.png}{3in}{The IPFS Stack}

Bitswap
-------

-   IPFS's block exchange protocol
-   Inspired by BitTorrent
-   *Given a set of peers who want data, how to allocate resources?*
    -   Reciprocation function

Bitswap
-------

*Given a set of peers who want data, how to allocate resources?*

-   Ever user maintains reputation for each peer
-   Very complex dynamics

Objectives
----------

-   Classify Bitswap strategy functions
    -   Conditions where useful
-   **Analytical work:** Repeated game model
-   **Empirical work:** Simulations

System Model
============

Process
-------

-   Multiple iterations
    -   *Complexity* vs.\ *accuracy*
-   Attempted tools
    -   Evolutionary game theory
    -   Statistical mechanics
    -   **Repeated games**

IPFS Network as Graph
---------------------

-   *Nodes*: Users
-   *Edges*: Peerings; unweighted, undirected

Reputation
----------

-   $b_{ji}^t$: Total bits sent from user $j$ to peer $i$ from round $0$ to
    $t-1$
-   $d_{ji}$: *debt ratio* $j$ to peer $i$

$$
d_{ji}^t = \frac{b_{ji}^{t-1}}{b_{ij}^{t-1}\:+\:1}
$$

Game Formulation
----------------

### Characteristics

-   *Players*: Users/nodes
-   *Infinitely repeated*
    -   Discrete rounds, denoted by $t$
-   *Static*
-   *Incomplete information*

Game Formulation
----------------

### Strategy

-   Reciprocation function
    -   *Input*: peer debt ratio
    -   *Output*: peer weight
    -   $S_j(d_{ji}^t, \mathbf{d}_j^{-i,t}) \in \{0, 1\}$
-   Peers served via weighted round-robin

Preliminary Results
===================

Strategy Simulator
------------------

-   3 node network
-   Parameters
    -   Resource distribution
    -   Initial peer-wise reputations
-   Tests whether given strategy function is NE

Strategy Simulator
------------------

**TODO: figures illustrating full exchange example**

Strategy Simulator
------------------

### Conclusions

-   Homogeneous resource distributions
    -   Any RF (trivially) NE
-   Non-homogeneous resource distributions
    -   NE not yet found

Symbolic Analysis
-----------------

-   Verified results of strategy simulator
-   Mathematica notebook
-   Intractable for nontrivial strategy functions
    -   **Next step:** Alternative functions/representations

Go-IPFS and IPTB
----------------

-   Beta strategy-integration into `go-ipfs`
-   IPTB: IPFS nodes in Docker containers
-   Scripted tests

Plan
====

Analytical Work
---------------

1.  **Repeated game analysis**
    -   Balances model accuracy with complexity
2.  **Evolutionary game theory** (if time allows)
    -   Good model, but high complexity

Simulations
-----------

1.  **Strategy simulator**
    -   Complements repeated game analysis
2.  **Bitswap tests**
    -   Test actual IPFS nodes

Timeline
========

TODO
----

**TODO: need this?**
