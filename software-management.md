## 6. Software Management

Linux Lite offers multiple ways to manage software installations and updates, accommodating users of all experience levels. Whether you prefer a graphical interface or the command line, Linux Lite provides reliable tools for discovering, installing, removing, and updating software.

---

### 6.1 Lite Software

**Lite Software** is a custom-built graphical tool provided by Linux Lite to simplify the installation and removal of commonly used applications. It presents users with a curated list of software options, each of which can be installed or removed with a single click.

#### GUI for One-Click Installs

To launch Lite Software:

* Navigate to **Menu > System > Lite Software**
* Enter your password when prompted

The interface includes a categorized list of popular applications, such as:

* Chromium (web browser)
* Skype (communication)
* VLC Media Player
* Dropbox
* GIMP (image editing)
* VirtualBox
* Zoom

Simply check the boxes next to the applications you wish to install or remove, then proceed with the actions.

This tool ensures that required dependencies are installed and avoids conflicts with existing packages, making it ideal for beginners.

#### Adding and Removing Apps

Lite Software not only installs new programs but also allows you to remove selected software from the same interface.

To remove an installed app:

1. Reopen **Lite Software**
2. Select the "Remove Software" section
3. Choose the application you wish to uninstall
4. Click **Next** to confirm and remove the software

The removal process is clean and automatically handles associated packages, unless manually installed dependencies are in use elsewhere.

---

### 6.2 Synaptic Package Manager

**Synaptic Package Manager** is a more advanced graphical interface for package management. It provides full access to all software packages available in the system repositories and offers detailed control over installation, upgrades, and removals.

To launch Synaptic:

* Go to **Menu > System > Synaptic Package Manager**
* Enter your administrative password

#### Package Search & Installation

Steps to install a package:

1. Use the **Search** button to find a package by name or description
2. Right-click the desired package
3. Select **Mark for Installation**
4. Click **Apply** to begin installation

Synaptic will resolve and suggest any required dependencies automatically.

#### Upgrades and Removals

To upgrade installed packages:

1. Click **Reload** to refresh the package list
2. Click **Mark All Upgrades**
3. Click **Apply** to execute

To remove packages:

* Mark the package for removal or complete removal (including configuration files)
* Click **Apply** to confirm

#### Locking Package Versions

If you want to prevent a package from being updated (useful for kernel versions or proprietary drivers), Synaptic allows version locking:

1. Locate the package
2. Right-click and select **Lock Version**
3. Confirm the lock; Synaptic will no longer suggest upgrades for that package

This is particularly useful when a newer version causes instability or conflicts.

---

### 6.3 Terminal-Based Package Management

For users comfortable with the command line, Linux Lite provides full access to Debian’s `apt` (Advanced Package Tool) system for managing software via terminal.

Open a terminal from **Menu > Accessories > Terminal Emulator**.

#### Basic apt Commands

* **Update Package Lists**

  ```bash
  sudo apt update
  ```

* **Upgrade All Installed Packages**

  ```bash
  sudo apt upgrade
  ```

* **Install a Package**

  ```bash
  sudo apt install package-name
  ```

* **Remove a Package**

  ```bash
  sudo apt remove package-name
  ```

* **Remove Completely (with config files)**

  ```bash
  sudo apt purge package-name
  ```

* **Clean Package Cache**

  ```bash
  sudo apt clean
  ```

* **List All Installed Packages**

  ```bash
  dpkg -l
  ```

#### Working with Repositories and PPAs

Linux Lite uses the Ubuntu software repositories by default, and users can extend the available software by adding PPAs (Personal Package Archives).

* **Add a PPA**

  ```bash
  sudo add-apt-repository ppa:user/ppa-name
  sudo apt update
  ```

* **Remove a PPA**

  ```bash
  sudo add-apt-repository --remove ppa:user/ppa-name
  ```

* **Edit Sources Manually**
  The list of enabled repositories is stored in:

  ```
  /etc/apt/sources.list
  ```

  and additional PPA entries are stored under:

  ```
  /etc/apt/sources.list.d/
  ```

Use caution when adding PPAs, as they are third-party sources that may not be verified by the Linux Lite or Ubuntu maintainers.

---
