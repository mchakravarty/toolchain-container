# Instructions for creating toolchain container images for Applicative Code using the macOS `container` tool

Read the `README.md` in this directory and, before working in one of the subdirectories (for specific container images), also consult the `README.md` in that directory.

## Apple container tool

Use the following documentation for detail on how to use the `container` tool:

* [Tutorial](https://github.com/apple/container/blob/main/docs/tutorials/start-here.md)
* [How-to](https://github.com/apple/container/blob/main/docs/how-to.md)
* [Container CLI Command Reference](https://github.com/apple/container/blob/main/docs/command-reference.md)

## Rules around Containerfiles

Prefer downloading binaries over building from source for tools installed into container images. Whenever possible source binaries and packages from the release site of the project or organisation maintaining the corresponding tool.

Use SHA hashes to check the integrity of downloaded binaries. Use cryptographic signatures (via GPG) to check the authenticity of downloaded packages and binaries.

Whenever you spot a security risk, inform the user.

Before working on a `Containerfile` in one of the subdirectories, read that subdirectories `README.md` for guidance on the specifics of that build.

## General behaviour

Before embarking on significant changes or tests (especially if they involve running or building containers), present a plan of what you want to do to the user. Refine the plan with the user and only execute it after confirmation from the user.

During testing and experimenting, minimise the number of container builds as they can take a long time. Try to ammortise by reusing containers and working incrementally (instead of starting from scratch each time).

