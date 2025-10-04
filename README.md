# SBK
A menu driven sript for enabling Secure Boot on Kali Linux

> [!WARNING]
> I do not take any response on you using this script! This script could be dangerous and break your setup!
> Success depends heavily on how your motherboard's UEFI firmware responds to it.
> This script is not tested widely yet. You were warned!
## ❓ Why?

So I am a beginner (relatively). I've tried many Linux distributions, but Kali is the only one that truly satisfies my needs. The problem is that while other distros either work out-of-the-box or can be relatively easily configured for Secure Boot, I struggled to make it work with Kali.

I need Secure Boot for two main reasons:

1. To maintain a stable dual-boot setup with Windows (for gaming and other applications).

2. For the general security benefits it provides.

I initially tried to configure it using shim-signed but failed repeatedly. After experimenting with other distributions out of frustration, I decided to dive deeper. I began researching how to implement Secure Boot the harder way: by manually enrolling keys directly into the UEFI firmware, etc.

I quickly realized that automating this process with a script while experimenting would save me countless hours of trial and error and could help out someone else. That's why I created SBK.

## ✨ Features
- Create and convert keys (PK, KEK, db) to various formats (.der, .crt, .pem, .key, .esl, .auth)
- Backup and restore original keys, GRUB and kernel
- Enroll the created keys to UEFI, including the original ones
- Support for Dual booting with Windows
- Signing GRUB, DKMS and all kernels
- Automatically sign new installs of GRUB, DKMS and kernels

## Usage:
1. Clone the repo
2. Run `sudo ./sbk`, it will install SBK and it's dependencies
3. Run option 1 and follow the instructions the script shows

The process consists out of two parts:
> Boot with factory default keys
1. Key creation, key extraction and backup --> reboot to UEFI
> Boot in Setup mode (delete all keys and disable key provisioning if present)
2. Signing, enrollment and setup automatic signing --> reboot to UEFI
> Enable Secure Boot
