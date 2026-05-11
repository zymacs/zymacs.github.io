---
title: Installing Arch
thumbnail: 'img/arch_logo.png'
date: 2026-05-09
draft: true
tags:
 - arch
 - linux
categories:
 - installation guides
---

So you want to install Arch? You want to _use Arch btw_? Hehehe. Speaking from experience, you might be doing this some time again in the future so you should probably write one such article yourself.

But that's after we get through the installation.

Let's make some assumptions about you. You are not setting up dual boot. You already
have an Arch installation medium ready to use. You want to install Arch the manual way: no
helper scripts that is. You got stable internet connection. Most preferrably, stable wired connection over wifi. 


Just an extra. The more unlikely a bad event is from happening, the better. Let's bring
likelihood to 0 then. I'd recommend you only have the disk on which you want to install
Arch connected. Its a common mistake selecting the wrong disk during installation. This will
wipe out your data and that without recovery. 


Target Milestone one: Booting into installation medium
- How to get to the bootloader menu
- Choosing UEFI over Grub

Target Milestone two: Getting a network connection
- Using cabled internet
- Using the ip command

Target Milestone three: Ready for arch-chroot
- Switching to a faster reflector
- Installing helper libs
- Partitioning disk
- Necessary mounts
- Swapon

Target Milestone four: Ready to boot up in arch (w/0 installation medium)
- UEFI config
- Grub config
- Locale config
- Creating a normal user



- Setting up a window manager
  - Xorg
  - i3
- Extra software
  - 

the guided script method


Adding Arch to the bootloader menu



To read about
- Creating a bootable drive with dd
  - download
  - verify authenticity with sha1
- Grub, UEFI
- Disk partitioning
  - Avoiding nuking disks
  - GPT vs MBR
- Why visudo, what's wheel
- Locales, Dates and Dhcpd
- Linux directory structure.
- What Arch-chroot does
- Window managers, Compositors and all
  - Xorg and all
- Windowing systems
- Kernel Vs Firmware
- Why mount what is mounted before arch-chroot
- What is swapon
- What is the boot menu
- Configuring wifi with IP (if you cant get your tethering to work)
- Virtual machines (for testing my instructions I need to setup KVM)
- Creating a new user on linux
- Packaging managers
  - Yay
  - Aur
  - Pacman
- Mirror configuration
  - reflector and mirror config file
- OS-prober 