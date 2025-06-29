## 8. Troubleshooting

Despite Linux Lite's emphasis on stability and ease of use, occasional issues may still arise. This section addresses common problems users may face, along with practical solutions to help resolve them quickly.

---

### 8.1 Boot Issues

#### Live USB Not Working

If your system does not boot from the Linux Lite Live USB:

* **Check Boot Order**: Enter BIOS/UEFI and ensure USB is set as the first boot device.
* **UEFI vs Legacy**: Try switching between UEFI and Legacy/CSM boot modes if the USB is not recognized.
* **Recreate USB**: The ISO may have been written incorrectly. Recreate the USB using:

  * **Rufus (Windows)** in “DD” mode
  * **balenaEtcher (cross-platform)**
  * **dd command (Linux)**:

    ```bash
    sudo dd if=linux-lite.iso of=/dev/sdX bs=4M status=progress && sync
    ```
* **Verify ISO Integrity**: Check the SHA256 or MD5 checksum of your ISO file to ensure it is not corrupted.

#### GRUB Issues

If Linux Lite does not appear in the boot menu or fails to load after installation:

* **Missing GRUB Menu**:

  * Hold **Shift** (BIOS) or **Esc** (UEFI) during boot to show GRUB.
* **Repair GRUB**:

  1. Boot into a Live USB session
  2. Mount the root partition:

     ```bash
     sudo mount /dev/sdXY /mnt
     ```
  3. Mount system folders:

     ```bash
     for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
     ```
  4. Chroot and reinstall GRUB:

     ```bash
     sudo chroot /mnt
     grub-install /dev/sdX
     update-grub
     exit
     ```

     Replace `/dev/sdX` with your boot drive.
  5. Reboot.

#### Recovery Mode

If your system does not boot properly, use **Recovery Mode**:

1. Reboot and access the GRUB menu.
2. Select **Advanced options for Linux Lite**.
3. Choose the recovery kernel option.
4. From the recovery menu, you can:

   * Repair broken packages
   * Drop to a root shell
   * Enable networking
   * Check file system
   * Resume normal boot

This mode is especially helpful for resolving issues caused by failed updates or misconfigurations.

---

### 8.2 Display Problems

#### Black Screen After Boot

Common causes include incompatible graphics drivers or misconfigured display settings.

Steps to resolve:

* **Switch to a TTY**:
  Press `Ctrl + Alt + F1` to open a text terminal.
* **Purge NVIDIA driver (if installed)**:

  ```bash
  sudo apt remove --purge nvidia*
  sudo reboot
  ```
* **Reconfigure display manager**:

  ```bash
  sudo dpkg-reconfigure lightdm
  ```

  Select `lightdm` as default display manager and reboot.

If you reach the desktop via TTY, install or revert drivers using the Additional Drivers tool or Lite Software.

#### Screen Tearing (NVIDIA or Intel)

##### NVIDIA:

Enable the **Force Full Composition Pipeline** setting:

1. Open **NVIDIA X Server Settings**
2. Go to **X Server Display Configuration**
3. Enable **Force Full Composition Pipeline**
4. Save to `/etc/X11/xorg.conf`

Ensure that the NVIDIA driver is installed via the Additional Drivers tool.

##### Intel:

Create a configuration file to enable TearFree:

```bash
sudo mkdir -p /etc/X11/xorg.conf.d
sudo nano /etc/X11/xorg.conf.d/20-intel.conf
```

Paste the following:

```bash
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "TearFree" "true"
EndSection
```

Save and reboot.

---

### 8.3 Sound & Network Issues

#### No Sound: PulseAudio Fixes

If sound is not working:

* Open **Menu > Multimedia > PulseAudio Volume Control**

  * Ensure correct output device is selected (e.g., speakers or HDMI).
  * Verify application-specific volume is not muted.
* Restart PulseAudio:

  ```bash
  pulseaudio -k
  pulseaudio --start
  ```

Check ALSA mixer:

```bash
alsamixer
```

* Use arrow keys to unmute (`M`) and raise volume levels.

Reinstall audio components:

```bash
sudo apt install --reinstall alsa-base pulseaudio
sudo reboot
```

#### Wi-Fi Not Detected

If your Wi-Fi card is not working:

* Open **Menu > Settings > Install Drivers** and apply any available proprietary drivers.
* Use `lspci` or `lsusb` to identify your wireless hardware:

  ```bash
  lspci | grep -i network
  lsusb
  ```
* Load the appropriate kernel module:

  ```bash
  sudo modprobe your-driver-name
  ```
* Reboot after installation.

You may also need to enable the interface:

```bash
sudo rfkill unblock all
```

If the issue persists, check `dmesg` or `journalctl -xe` for kernel messages.

---

### 8.4 Common Errors

#### Update Errors

**Fix Broken Packages**:

```bash
sudo apt --fix-broken install
```

**Clear Package Locks**:
If `dpkg` or `apt` is locked:

```bash
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/lib/apt/lists/lock
sudo dpkg --configure -a
```

**Update Failures**:

1. Refresh sources:

   ```bash
   sudo apt update
   ```
2. Try upgrading again:

   ```bash
   sudo apt upgrade
   ```

Check for outdated or conflicting PPAs in `/etc/apt/sources.list.d`.

#### Application Crashes

If an application crashes on launch:

* Try running it from the terminal to view error output.
* Reinstall the application:

  ```bash
  sudo apt remove --purge app-name
  sudo apt install app-name
  ```

If the crash persists:

* Check for missing dependencies:

  ```bash
  ldd /usr/bin/app-name
  ```
* Look for errors in:

  ```bash
  journalctl -p err -b
  ```

You can also check user-specific configuration files in `~/.config/` and reset or rename them to test for corrupted settings.

---
