# Instructions for creating toolchain container images for Applicative Code using the macOS `container` tool

## Apple container tool

The macOS container tool is a command line utility that facilitates building, managing, and using OCI-compatible Linux containers as lightweight virtual machines on macOS.

The following documentation should be consulted to understand how to use the `container` tool:

* [Tutorial](https://github.com/apple/container/blob/main/docs/tutorials/start-here.md)
* [How-to](https://github.com/apple/container/blob/main/docs/how-to.md)
* [Container CLI Command Reference](https://github.com/apple/container/blob/main/docs/command-reference.md)

## Base image

We build on top of the latest Ubuntu LTS release from Docker Hub, which is the default registry used by `container`. At the moment, this is Ubuntu 26.04.1 LTS (Resolute Raccoon), available from Docker hub with the tag `resolute-20260811.1`.

The base image is being used to build several toolchain images. The resources for each such toolchain image (most notably the `Containerfile`) are in a subdirectory of its own.

## Tools

On each toolchain image, we install at least the following tools:

* the Agda language and proof assistant,
* the Agda standard library,
* the Agda Language Server,
* a distribution of the Hakell GHC compilation system,
* the Cabal build system for Haskell, and
* the Haskell Language Server,
* the Swift toolchain including the SourceKit-LSP server.

Toolchain images vary in which versions of these tools are being installed and what additional libraries and helper tools get installed.

## Rules around Containerfiles

Prefer downloading binaries over building from source for tools installed into container images. Whenever possible source binaries and packages from the release site of the project or organisation maintaining the corresponding tool.

Use SHA hashes to check the integrity of downloaded binaries. Use cryptographic signatures (via GPG) to check the authenticity of downloaded packages and binaries.

Whenever you spot a security risk, inform the user.

