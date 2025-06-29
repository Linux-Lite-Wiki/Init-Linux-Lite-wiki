## 17. File Management

Linux Lite offers powerful and user-friendly tools for managing files and storage devices. Its default file manager, **Thunar**, is lightweight, fast, and highly customizable—perfect for users who want both simplicity and control. Additionally, Linux Lite ensures seamless access to USB drives, external storage, and NTFS-formatted partitions.

---

### 17.1 Thunar File Manager

**Thunar** is the default file manager in Linux Lite. It is designed to be simple, fast, and efficient, offering advanced features without unnecessary complexity.

#### Custom Actions

Thunar allows users to create **custom actions**—context menu options that run specific commands on selected files or folders. This is useful for tasks like opening a terminal in a folder, converting images, or batch renaming.

To create a custom action:

1. Open Thunar.
2. Go to **Edit > Configure custom actions**.
3. Click **+** to add a new action.
4. Fill in the details:

   * **Name**: Open Terminal Here
   * **Command**: `exo-open --working-directory %f --launch TerminalEmulator`
   * **Icon**: (Optional)
5. Under **Appearance Conditions**, set file types (e.g., “Directories only”) and context menu visibility.
6. Click **OK** to save.

You can now right-click a folder and use the new custom option.

Other common custom actions:

* Open as root: `gksudo thunar %f`
* Compress folder: `file-roller --add %f`

#### Dual-Pane View

Thunar does not have native dual-pane support, but you can mimic it by:

* Opening **two Thunar windows side by side**.
* Using the keyboard shortcut `Ctrl + Shift + N` to launch a new window.
* Navigating independently in each pane for easy drag-and-drop operations between directories.

Alternatively, you can use tools like **Double Commander** if true dual-pane is essential.

To install Double Commander:

```bash
sudo apt install doublecmd-gtk
```

#### Bookmarks

Bookmarks in Thunar allow quick access to frequently used folders.

To add a bookmark:

* Navigate to the folder.
* Click **Bookmarks > Add to Bookmarks**, or
* Drag the folder into the left-hand sidebar.

Bookmarks are saved and persist across sessions. You can also reorder or remove them by right-clicking the bookmark.

To edit bookmarks manually:

```bash
nano ~/.config/gtk-3.0/bookmarks
```

Each line corresponds to a path, e.g.:

```
file:///home/user/Documents
```

---

### 17.2 Mounting Drives

Linux Lite supports a wide range of storage devices and filesystems including FAT32, NTFS, ext4, exFAT, and others. Mounting is generally automatic for USB and external drives.

#### USB & External Drives

When a USB or external hard drive is plugged in:

* Linux Lite will automatically mount the drive under `/media/username/DeviceLabel`
* A desktop icon appears (if enabled)
* You can browse, copy, delete, and manage files using Thunar

To safely remove:

* Right-click the device icon > **Unmount** or **Eject**

If automount fails, you can mount manually:

```bash
sudo mount /dev/sdX1 /mnt
```

(Replace `/dev/sdX1` with the correct device identifier)

To list attached devices:

```bash
lsblk
```

#### NTFS Support

NTFS is fully supported for reading and writing via the `ntfs-3g` driver, which is installed by default in Linux Lite.

To check:

```bash
sudo apt install ntfs-3g
```

Mounting NTFS manually (if needed):

```bash
sudo mount -t ntfs-3g /dev/sdX1 /mnt
```

Thunar provides write access to NTFS partitions automatically once mounted. Useful for accessing files from a dual-boot Windows installation.

#### Auto-Mount Configuration

To automatically mount specific partitions at boot, you'll need to edit the `/etc/fstab` file.

**Caution:** Improper `fstab` configuration can prevent booting.

Steps:

1. Identify the device UUID:

   ```bash
   sudo blkid
   ```

2. Edit the `fstab` file:

   ```bash
   sudo nano /etc/fstab
   ```

3. Add a new line for the partition:

   ```text
   UUID=XXXX-XXXX  /mnt/Data  ntfs-3g  defaults,uid=1000,gid=1000  0  0
   ```

   Replace `UUID`, mount point (`/mnt/Data`), and options as needed.

4. Create the mount point:

   ```bash
   sudo mkdir /mnt/Data
   ```

5. Test the configuration:

   ```bash
   sudo mount -a
   ```

If successful, the partition will be mounted automatically on every boot.

---

