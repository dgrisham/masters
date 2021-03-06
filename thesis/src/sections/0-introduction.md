Introduction
============

The Internet is perhaps the largest and most consistent network that has ever
existed. Unfortunately, it predominantly runs on the outdated hypermedia
distribution protocol HTTP. The goal of the InterPlanetary File System (IPFS) is
to upgrade the Internet to a distributed peer-to-peer system, thereby making it
more robust and permanent. This new Internet would be a network of peers, as
opposed to clients and servers, all sharing data between one another. In order
for such a system to thrive, users must be cooperative and willing to share data
with their peers. The goal of this project is to analyze the resource allocation
options of peers interacting in an IPFS network. A combination of analytical and
empirical methods will be used to glean insights into the generally intractable
allocation decisions that users are presented with when participating in an IPFS
network.

IPFS
----

IPFS is a peer-to-peer hypermedia distribution protocol developed by Protocol
Labs. It is a content-addressed, versioned filesystem. While a variety of use
cases exist for such a protocol, the most ambitious goal of the project is to
replace HTTP as the primary file exchange protocol used in the Internet. This
could ultimately result in the decentralization of the Internet.

IPFS synthesizes various technologies developed since the Internet's inception.
These technologies include Git, BitTorrent, distributed hash tables
(e.g. Kademlia), and self-certified filesystems. The IPFS stack is shown in
Figure \ref{img:ipfs-stack}. One way to conceptualize an IPFS network is as a
Git repository shared within a torrent-esque swarm.

\vspace{0.5cm}
\graphicwlc{../figures/ipfs_stack.png}{4in}{img:ipfs-stack}{The IPFS Stack}{{\bf The IPFS Stack}
-- Bitswap is at the exchange layer.}

Bitswap
-------

Bitswap is the block exchange protocol of IPFS. The most direct inspiration of
this submodule is the BitTorrent peer-to-peer file distribution protocol.
Bitswap is the layer of IPFS that incentivizes users to share data. A Bitswap
*reciprocation function* determines which peers to send data to, and in what
relative quantities. The input to the reputation function is a set of metrics
that may be used to weigh peers -- e.g. peer bandwidth, reputation, and/or
location. The output is a set of weights, one for each peer, that assign the
relative resource allocations for the peers. These weights are periodically
recalculated to reflect changes in both the network and peer behavior.

Objectives
----------

**TODO: This section will likely need to be updated/replaced, as it was copied
directly from the proposal. At the very least, I think it might need to be
changed to be past-tense instead of future**

For this project, I will take the initial steps toward understanding the
behavior of users in an IPFS network as predicted by game theoretical models.
This will involve a combination of analytical and empirical analyses, along with
implementation of these ideas in the IPFS software. The analytical work will
focus on repeated games and, potentially, evolutionary games, while the
empirical work will take a simulation-based approach. I intend to use these
methods to classify various Bitswap reciprocation functions and determine useful
allocation behavior under certain conditions.
