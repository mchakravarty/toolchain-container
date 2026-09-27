# Accelerate Container Image

This container image contains the toolchains used by default by Applicative Code together with the [Accelerate](https://www.acceleratehs.org/) library for high-performance array programming in Haskell. It's name is 'app-tools-accelerate'.

We are using the following versions:
* Base package: accelerate 1.4.0.0
* LLVM Native backend: accelerate-llvm-native 1.4.0.0
* containers-accelerate 0.1.0.0
* hashable-accelerate 0.1.0.0
* colour-accelerate 0.4.0.0
* mwc-random-accelerate 0.2.0.0

## Installation details

Important: it is advisable to give `container build` at least 4 CPUs and 16GB of memory.
