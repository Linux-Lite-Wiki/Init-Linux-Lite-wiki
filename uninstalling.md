## Uninstalling Linux Lite
Certainly. Here's the detailed content for:

---

## 18. Uninstalling Linux Lite

There may be situations where you decide to remove Linux Lite from your system—either to revert to Windows, install a different Linux distribution, or reuse the storage. This guide covers both dual-boot reversal and full system wipe methods. Always back up your personal data before proceeding with any removal or partition operation.

---

### 18.1 Dual Boot Reversal

If you installed Linux Lite alongside Windows in a **dual-boot setup**, you'll need to:

1. **Restore the Windows bootloader**, and
2. **Remove the Linux partitions** to reclaim the disk space.

#### Restoring Windows Bootloader

After uninstalling Linux Lite, the GRUB bootloader (used by Linux) will remain, and Windows won’t boot directly. You must restore the **Windows bootloader** using a recovery method.

**Option 1: Using Windows Installation Media**

1. Insert a Windows installation USB/DVD and boot into it.
2. Select your language and region > Click **Next**.
3. Click **Repair your computer**.
4. Go to **Troubleshoot > Advanced options > Command Prompt**.
5. In the terminal, enter the following (based on your Windows version):

##### For Windows 10/11 on UEFI systems:

```cmd
bootrec /fixboot
bcdboot C:\Windows
```

##### For Windows 7/Legacy BIOS:

```cmd
bootrec /fixmbr
bootrec /fixboot
bootrec /rebuildbcd
```

6. Reboot. If successful, Windows should start normally.

If issues persist, tools like **EasyBCD** (on Windows) can also help repair the bootloader.

---

#### Deleting Linux Lite Partitions Safely

After restoring the Windows bootloader:

1. Boot into Windows.

2. Press `Windows + R`, type `diskmgmt.msc`, and press Enter.

3. Identify the Linux partitions. These will not have drive letters and may show as:

   * “Healthy (Primary Partition)” or “Unallocated”
   * Typically formatted as **ext4**, **swap**, or “Unknown”

4. Right-click and choose:

   * **Delete Volume** to remove them.
   * **Extend Volume** on your Windows partition to merge the freed space back.

Alternatively, use a USB tool like **GParted Live** (recommended for more control):

* Download GParted ISO from [https://gparted.org/](https://gparted.org/)
* Create a bootable USB
* Boot into GParted, select your Linux partitions, and delete/resize as needed.

---

### 18.2 Full Wipe and Reinstall

If your goal is to **completely erase Linux Lite** (and everything else) and start fresh with another OS (e.g., Windows or another Linux distro), the process is simple using GParted.

#### Wipe Disk Using GParted

**GParted** is a powerful graphical partition editor available as both a Linux app and a standalone live ISO.

##### Steps:

1. **Create a GParted USB**:

   * Download from [https://gparted.org/download.php](https://gparted.org/download.php)
   * Use tools like **Rufus** (on Windows) or **balenaEtcher** to write the ISO to a USB drive.

2. **Boot into GParted Live**:

   * Choose the default settings when it loads.
   * GParted will show all connected drives and partitions.

3. **Select your drive**:

   * Top-right dropdown: `/dev/sda`, `/dev/nvme0n1`, etc.
   * Carefully choose the correct disk (usually the one with Linux Lite installed).

4. **Delete all partitions**:

   * Right-click on each partition and select **Delete**.
   * Click the **green checkmark** to apply all operations.

5. **Create a new partition table (Optional)**:

   * Device > Create Partition Table
   * Choose **msdos** (for BIOS) or **gpt** (for UEFI)
   * This will completely wipe the disk.

6. **Exit and install new OS**:

   * Insert the new OS installation media (e.g., Windows or another Linux).
   * Proceed with its installation using the now-empty drive.

---

**Warning**: Disk wiping operations are irreversible. Always double-check the drive selection and back up important files before proceeding.

---
