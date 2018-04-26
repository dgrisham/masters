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
    -   Strategy function

Objectives
----------

-   Classify Bitswap strategy functions
    -   Conditions where useful
-   **Analytical work:** Repeated game model
-   **Empirical work:** Simulations

Plan
====

Analytical Work
---------------

1.  **Repeated game analysis**
    -   Balance model accuracy with complexity
2.  **Evolutionary game theory** (if time allows)
    -   Good model, but high complexity

Simulations
-----------

1.  **Strategy simulator**
    -   Complements repeated game analysis
2.  **Bitswap tests**
    -   Test actual IPFS nodes

Progress and Preliminary Results
================================

Strategy Simulator
------------------

-   3 node network
-   Parameters
    -   Resource distribution
    -   Initial peer-wise reputations
-   Tests whether given strategy function gives NE

**TODO: full exchange example?**

Repeated Game Analysis
----------------------

-   Verified results of strategy simulator
-   Mathematica notebook
-   Intractable for nontrivial strategy functions
    -   **Next step:** Alternative functions/representations

Go-IPFS and IPTB
----------------

-   Beta strategy-integration into `go-ipfs`
-   IPTB: IPFS nodes in Docker containers
-   Scripted tests

Timeline
========


