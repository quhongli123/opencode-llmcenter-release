# OpenCode llm-center releases

This repository contains only GitHub Actions release automation and published installers. Source code remains in the private `opencode-llmcenter` repository.

Create this repository as `opencode-llmcenter-release`, copy this directory's contents to its root, and configure:

- `SOURCE_REPO_TOKEN`: fine-grained token with read access to the private source repository.
- `RELEASE_DISPATCH_TOKEN`: the same token in the private source repository, with Actions write access to this repository.

Publishing a source tag matching `vMAJOR.MINOR.PATCH` dispatches this workflow with the exact source tag. The workflow creates a GitHub Release and uploads unsigned macOS, Windows, and Linux installers. Configure Apple and Azure signing separately before distributing production binaries.
