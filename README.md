# LLM Code releases

This repository contains only GitHub Actions release automation and published installers. Source code remains in the private `opencode-llmcenter` repository.

Create this repository as `opencode-llmcenter-release`, copy this directory's contents to its root, and configure:

- `SOURCE_REPO_TOKEN`: fine-grained token with read access to the private source repository.
- `RELEASE_DISPATCH_TOKEN`: the same token in the private source repository, with Actions write access to this repository.

Publishing a source tag matching `vMAJOR.MINOR.PATCH` dispatches this workflow with the exact source tag. The workflow creates a GitHub Release and uploads installers for macOS, Windows, and Linux. macOS artifacts are signed and notarized when all Apple signing secrets are configured; otherwise they are explicitly built unsigned. Configure Apple and Azure signing before distributing production binaries.
