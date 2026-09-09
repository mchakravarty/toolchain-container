# Default Container Image

This container image contains the toolchains used by default by Applicative Code. It's name is 'app-tools-default'.

** The build rules for this image are work in progress **

We are using the following versions:
* Agda: 2.8.0.1
* Agda Standard Library: 2.4
* Agda Language Server: v6
* GHC: 9.14.1
* Cabal: 3.18.1.0
* Haskell Language Server: 2.15.0.0
* Swift toolchain (including SourceKit-LSP): 6.3.3

## Installation details

| Tool | Version | Source | Method | Resource Requirements |
|------|---------|-------|--------|----------------------|
| GHC | 9.14.1 | [downloads.haskell.org/~ghc](https://downloads.haskell.org/~ghc/9.14.1/) | Pre-compiled binary (aarch64-deb12) | N/A |
| Cabal | 3.18.1.0 | [downloads.haskell.org/~cabal](https://downloads.haskell.org/~cabal/cabal-install-3.18.1.0/) | Pre-compiled binary (aarch64-linux-unknown) | N/A |
| Haskell Language Server | 2.15.0.0 | [downloads.haskell.org/~hls](https://downloads.haskell.org/~hls/haskell-language-server-2.15.0.0/) | Pre-compiled binary (aarch64-linux-ubuntu2204) | N/A |
| Agda | 2.8.0.1 | [GitHub Releases](https://github.com/agda/agda/releases/tag/v2.8.0.1) | Compiled from source via Cabal | ~16GB RAM, ~15-20 min, 4 CPUs |
| Agda Standard Library | 2.4 | [GitHub Releases](https://github.com/agda/agda-stdlib/releases/tag/v2.4) | Pre-built library files | N/A |
| Agda Language Server | v6 | [GitHub Releases](https://github.com/agda/agda-language-server/releases/tag/v6) | Compiled from source via Cabal | ~16GB RAM, ~20-30 min, 4 CPUs |
| Swift toolchain (including SourceKit-LSP) | 6.3.3 | [downloads.swift.org](https://download.swift.org/swift-6.3.3-release/) | Pre-compiled binary (aarch64) | N/A |

**Note on Agda**: No official aarch64 Linux binaries are available for Agda 2.8.0.1. The x86-64 Linux binary from GitHub releases cannot be used on aarch64. Therefore, Agda is built from source using the pre-installed GHC and Cabal. The `--constraint="cryptonite -fixed"` flag is used to avoid dependency resolution issues. All intermediate build products and downloaded packages are removed after installation to keep the container image size minimal.

**Note on Agda Standard Library**: The library is installed from the official GitHub release tarball and registered with Agda via the `libraries` and `defaults` configuration files in Agda's application directory (`/root/.config/agda/`).

**Note on Agda Language Server**: Although Agda Language Server v6 was tested with Agda 2.8.0, we build it with Agda 2.8.0.1 (which is compatible with GHC 9.14.1's base-4.22.0.0). Agda 2.8.0 requires base < 4.22, making it incompatible with our GHC version. The difference between Agda 2.8.0 and 2.8.0.1 is minimal and does not affect source code compatibility. All intermediate build products and downloaded packages are removed after installation to keep the container image size minimal.

**Note on Swift**: Swift 6.3.3 is installed from pre-compiled binaries provided by the Swift project. The installation uses the `ubuntu2404-aarch64` platform identifier to download the ARM64 version. The Ubuntu 24.04 binaries are generally compatible with our Ubuntu 26.04 base image. GPG signatures are verified using the Swift 6.x Release Signing Key. The toolchain includes SourceKit-LSP for language server support.

