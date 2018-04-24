# masters

Materials for my Master's thesis work.

## strategy-sim

The Bitswap strategy simulator repository is closely related to this work -- see
[here](https://github.com/dgrisham/strategy-sim).

The [strategy analysis Mathematica notebook](./strategy-analysis.nb) sets up the
problem simulated by `strategy-sim` symbolically and finds the solutions
analytically. At the moment, only the linear reciprocation function is supported
in this notebook, as other reciprocation functions (e.g. `Tanh`) make the
problem intractable.

## Bitswap Strategy Implementation in `go-ipfs`

This is in-progress, and can be found
[here](https://github.com/ipfs/go-ipfs/pull/3982).

The [`bitswap-tests` repo](https://github.com/dgrisham/bitswap-tests) uses
[IPTB](https://github.com/ipfs/iptb) to run tests related to Bitswap strategies.
This repo is in its early stages, but currently just wraps IPTB calls in shell
scripts. In particular, we spin up Docker nodes running IPFS instances, connect
the nodes based on some topology, have them exchange data, and measure the
Bitswap state during/after the data exchange.

## Deprecated

An older analysis that uses a now deprecated game-theoretical model of Bitswap
can be found [here](./deprecated/analysis/).
