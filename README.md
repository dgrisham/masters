# masters

Materials for my Master's thesis work.

## strategy-sim

The Bitswap strategy simulator repository is very related to this work -- see
[here](https://github.com/dgrisham/strategy-sim).

The [strategy analysis Mathematica notbook](./strategy-analysis.nb) sets up the
problem simulated by `strategy-sim` symbolically and finds the solutions
analytically. At the moment, only the linear reciprocation function is supported
in this notebook, as other reciprocation functions (e.g. `Tanh`) make the
problem intractable.

## Bitswap Strategy Implementation in `go-ipfs`

This is in-progress, and can be found
[here](https://github.com/ipfs/go-ipfs/pull/3982).

## Deprecated

An older analysis that uses a now deprecated game-theoretical model of Bitswap
can be found [here](./deprecated/analysis/).
