# Monterey USB Installer

This workflow runs on a standard GitHub-hosted Intel Mac. It downloads
macOS Monterey 12.7.6 with Apple's `softwareupdate`, verifies the installer
signature, and runs Apple's `createinstallmedia` against a GUID/HFS+ image.

The workflow creates a complete USB installer image rather than a
virtual-machine ISO or a network-only recovery image. It does not install
OpenCore or change Mac firmware settings.

The image and verification records expire after one day. The image must
be downloaded and its SHA-256 verified before writing it to a USB device.

The workflow has no schedule, accepts no secrets, and does not read files
from a personal computer. It has not yet been executed.

Using the installer on the target Mac can still require an internet
connection for model-specific firmware and installation information.

References:

- https://support.apple.com/101578
- https://docs.github.com/en/actions/reference/runners/github-hosted-runners
- https://github.com/actions/upload-artifact
