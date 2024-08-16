---
title: Mastering partition resizing on Linux dual booting Windows
layout: default
tags:
  - Ubuntu
  - Partitioning
  - Dual Boot
  - Windows 11
  - GParted
description: "Learn how to resize partitions on Ubuntu 22.04.4 LTS in a dual-boot setup with Windows 11."
date: 2024-05-14
---

## Introduction

If you're dual-booting Ubuntu 22.04.4 LTS with Windows 11 and need to adjust your partitions, this guide will help you through the process. It involves shrinking the Windows partition to free up space and then resizing the Ubuntu partition to utilize that newly available space.

### Preparing Windows

First, you'll need to create unallocated space on your disk by shrinking the Windows partition:

1. **Boot into Windows** and open the Disk Management tool:
   - Right-click the **Start Menu** and select **Disk Management**.
2. **Shrink the C: Partition**:
   - Right-click on the `C:` partition and choose **Shrink Volume**.
   - Specify the amount of space to shrink and proceed with the operation. This will create unallocated space on your drive.

### Booting into Ubuntu

Next, you need to boot into Ubuntu using a USB drive:

1. **Insert your Ubuntu USB drive** and restart your computer.
2. If you don’t see the option to **Try Ubuntu** in the boot menu:
   - Restart and enter the BIOS/UEFI settings by pressing `F2`, `F12`, `Esc`, or another key specific to your system during startup.
   - Change the boot order to prioritize booting from the USB drive first. Save the changes and exit.

### Adjusting Partitions with GParted

Once you’re in the Ubuntu live session, you’ll use GParted to resize your partitions:

1. **Open GParted**:
   - Open a terminal by pressing `Ctrl + Alt + T` and type `sudo gparted`, then press `Enter`.
2. **Check Unallocated Space**:
   - Locate the unallocated space you created in Windows. Ensure it is adjacent to your Ubuntu root partition (formatted as ext4). If it's not adjacent, you’ll need to move partitions around to make it so.
3. **Resize the Ubuntu Partition**:
   - Right-click on the Ubuntu root partition (ext4) and select **Resize/Move**.
   - Adjust the size to include the unallocated space.
   - Click the **Apply** button (green checkmark) to execute the changes. GParted will process the resizing operation.

### Final Steps

1. **Remove the USB Drive**:
   - Once the resizing is complete, eject the Ubuntu USB drive.
2. **Reboot Your System**:
   - Restart your computer. Ubuntu and Windows should now reflect the new partition sizes.

This process allows you to effectively manage disk space on a dual-boot system with Ubuntu and Windows 11. Always ensure you have backups of important data before making changes to disk partitions.