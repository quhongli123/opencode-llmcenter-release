# LLM Code releases

This repository contains only GitHub Actions release automation and published installers. Source code remains in the private `opencode-llmcenter` repository.

Create this repository as `opencode-llmcenter-release`, copy this directory's contents to its root, and configure:

- `SOURCE_REPO_TOKEN`: fine-grained token with read access to the private source repository.
- `RELEASE_DISPATCH_TOKEN`: the same token in the private source repository, with Actions write access to this repository.

Publishing a source tag matching `vMAJOR.MINOR.PATCH` dispatches this workflow with the exact source tag. The workflow creates a GitHub Release and uploads signed and notarized macOS installers plus Windows and Linux installers.

Configure all of these repository secrets before publishing a release:

- `APPLE_CERTIFICATE`: base64-encoded macOS Developer ID Application `.p12` certificate.
- `APPLE_CERTIFICATE_PASSWORD`: password for the certificate.
- `APPLE_API_KEY_PATH`: contents of the App Store Connect API key `.p8` file.
- `APPLE_API_KEY`: App Store Connect API key ID.
- `APPLE_API_ISSUER`: App Store Connect issuer ID.
- `SOURCE_REPO_TOKEN`: fine-grained token with read access to the private source repository.
- `RELEASE_DISPATCH_TOKEN`: the same token in the private source repository, with Actions write access to this repository.

The macOS build fails before packaging if any Apple signing secret is missing. Unsigned macOS artifacts must not be published because the desktop updater validates the code signature.
