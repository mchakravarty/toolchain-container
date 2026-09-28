# Toolchain Container Images for Applicative Code

This repo contains support for building toolchain container images for Applicative Code. The images are based on Ubuntu LTS and support aarch64 only. Image names are prefixed with 'app-tools'. 

We use the macOS [container tool](https://github.com/apple/container), which is a command line utility that facilitates building, managing, and using OCI-compatible Linux containers as lightweight virtual machines on macOS.

## Base image

We build on top of the latest Ubuntu LTS release from Docker Hub, which is the default registry used by `container`. At the moment, this is Ubuntu 26.04.1 LTS (Resolute Raccoon), available from Docker hub with the tag `resolute-20260811.1`.

The base image is being used to build several toolchain images. The resources for each such toolchain image (most notably the `Containerfile`) are in a subdirectory of its own.

## Tools

In each toolchain image, we install at least the following tools:

* the Agda language and proof assistant,
* the Agda standard library,
* the Agda Language Server,
* a distribution of the Haskell GHC compilation system,
* the Cabal build system for Haskell, and
* the Haskell Language Server,
* the Swift toolchain including the SourceKit-LSP server.

Toolchain images vary in which versions of these tools are being installed and what additional libraries and helper tools get installed.

## Configuration

Each toolchain container image includes a file `/.applicative/configuration.json` that specifies the tool configuration for the toolchain set provided by that image.

## License

The code in this repository takes some elements from [docker-haskell](https://github.com/haskell/docker-haskell) (MIT license) and [swift-docker](https://github.com/swiftlang/swift-docker) (Apache-2.0 license with runtime license exception). This repository itself is licensed under the [Apache-2.0 license with runtime license exception](LICENSE.md).

