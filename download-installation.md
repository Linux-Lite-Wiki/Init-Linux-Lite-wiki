## Download & Installation

Here is the detailed content for **Section 2: Download & Installation** of the Linux Lite Wiki:

---

## 2. Download & Installation

This section covers everything you need to know to download, create installation media, and install Linux Lite on your system.

### 2.1 System Requirements

#### Minimum Specifications

* CPU: 1 GHz processor
* RAM: 768 MB
* Storage: 8 GB of free disk space
* Display: VGA capable of 1024x768 screen resolution

#### Recommended Specifications

* CPU: 1.5 GHz dual-core processor or better
* RAM: 1 GB or more
* Storage: 20 GB of free disk space
* Display: 1366x768 screen resolution or higher

#### 32-bit vs 64-bit Support

As of recent versions, Linux Lite only provides 64-bit ISO images. If you're using an older machine that requires 32-bit support, you will need to use legacy versions of Linux Lite, available through the archive section on the official website. However, it is strongly recommended to use the latest 64-bit version for security, performance, and software compatibility.

---

### 2.2 Download Links

#### Official ISO

The latest Linux Lite ISO can be downloaded directly from the official website:

* [https://www.linuxliteos.com/download.php](https://www.linuxliteos.com/download.php)

Make sure to select the most recent version to benefit from the latest security updates and feature improvements.

#### Torrent and Mirror Options

Linux Lite also offers torrent downloads for faster and more resilient downloading. Torrenting helps reduce bandwidth load on official servers.

Mirror links are available globally to improve download speeds based on your geographic location. These are typically listed on the same download page.

#### Checksums (MD5/SHA256)

To ensure your downloaded ISO file is not corrupted or tampered with, verify its integrity using the provided checksum values:

* MD5: A quick method to verify download integrity
* SHA256: More secure and preferred for validating authenticity

You can check the hash on your system using the following commands:

* On Linux:

  ```bash
  sha256sum linux-lite-x.y.iso
  ```
* On Windows:
  Use tools like HashTab or built-in PowerShell commands.

---

### 2.3 Creating Bootable Media

Once you've downloaded the ISO, you'll need to create a bootable USB drive to install Linux Lite.

#### On Windows

* **Rufus**: A lightweight and reliable utility.

  * Website: [https://rufus.ie](https://rufus.ie)
  * Select the ISO, your USB drive, and click "Start".
* **balenaEtcher**: Cross-platform and beginner-friendly.

  * Website: [https://www.balena.io/etcher/](https://www.balena.io/etcher/)
  * Choose the ISO and your USB drive, then flash.

#### On Linux

* **dd Command** (advanced users):

  ```bash
  sudo dd if=linux-lite-x.y.iso of=/dev/sdX bs=4M status=progress && sync
  ```

  Replace `/dev/sdX` with your actual USB device.
* **UNetbootin**: GUI tool to create bootable USBs.

  * Available via package manager or from [https://unetbootin.github.io](https://unetbootin.github.io)

#### On macOS

* **balenaEtcher** is the simplest method for Mac users and supports writing ISO files to USB with minimal steps.

---

### 2.4 Installation Process

#### BIOS/UEFI Setup

1. Insert the USB stick and reboot your system.
2. Enter BIOS/UEFI settings (usually by pressing `F2`, `F10`, `DEL`, or `ESC` during startup).
3. Set USB as the first boot device.
4. Save and exit.

Linux Lite supports both Legacy BIOS and UEFI boot modes. If your system uses Secure Boot, it is advisable to disable it before installation for best compatibility.

#### Dual-Boot with Windows

Linux Lite supports dual-booting with Windows. During the installation process, you can choose to install alongside Windows, allowing you to select which operating system to use during boot.

Important:

* Backup your important data before modifying partitions.
* Defragment your Windows disk to free up continuous space for Linux Lite.

#### Full Installation Walkthrough

1. Boot into the USB and select “Start Linux Lite”.
2. From the desktop, double-click the “Install Linux Lite” icon.
3. Select your language, location, keyboard layout.
4. Choose installation type:

   * **Install alongside Windows**
   * **Erase disk and install Linux Lite**
   * **Something else** (manual partitioning)
5. Create a user account with a secure password.
6. Wait for the installation to complete (10–20 minutes).
7. Reboot when prompted and remove the USB drive.

#### Partitioning Options

If you choose “Something else”, you can manually create partitions. A typical layout is:

* `/` (root) – 15–20 GB
* `swap` – equal to or less than RAM size
* `/home` – remaining space for user files

Ensure partitions are formatted with ext4, and the correct bootloader location is selected (usually the main drive, like `/dev/sda`).

---


