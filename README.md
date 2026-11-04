# Monterey USB Installer

This workflow runs on a standard GitHub-hosted Intel Mac. It downloads
macOS Monterey 12.7.6 from Apple's software update catalog, verifies the
original InstallAssistant package with macOS PackageKit before unpacking
it, verifies the Apple-signed installer executables, and runs Apple's
`createinstallmedia` against a GUID/HFS+ image.

The original Apple package is catalog product 062-40406, build 21H1320,
with a catalog size of 12409187001 bytes. Package verification covers the
original contents before extraction; this avoids treating the installer's
legacy bundle resource rules as a modern application signature.

The workflow creates a complete USB installer image rather than a
virtual-machine ISO or a network-only recovery image. It does not install
OpenCore or change Mac firmware settings.

The image and verification records expire after one day. The image must
be downloaded and its SHA-256 verified before writing it to a USB device.

The workflow has no schedule, accepts no secrets, and does not read files
from a personal computer. A successful run and downloaded verification
records are required before the resulting image is used.

Using the installer on the target Mac can still require an internet
connection for model-specific firmware and installation information.

References:

- https://support.apple.com/101578
- https://docs.github.com/en/actions/reference/runners/github-hosted-runners
- https://github.com/actions/upload-artifact
