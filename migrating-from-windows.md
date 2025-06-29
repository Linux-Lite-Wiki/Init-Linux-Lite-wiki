## 16. Migrating from Windows

Transitioning from Windows to Linux Lite is a smooth experience, especially for users who value a familiar desktop layout, intuitive settings, and broad application support. This section helps Windows users understand the key differences and similarities between the two operating systems, and introduces suitable Linux Lite alternatives for popular Windows applications.

---

### 16.1 Differences & Similarities

#### File Structure

One of the first noticeable differences between Windows and Linux is the **file system layout**.

| Concept        | Windows                | Linux Lite                                                                    |
| -------------- | ---------------------- | ----------------------------------------------------------------------------- |
| Root Directory | `C:\`                  | `/` (root of the Linux file system)                                           |
| User Files     | `C:\Users\Username`    | `/home/username/`                                                             |
| Program Files  | `C:\Program Files\`    | `/usr/bin/`, `/opt/`, or `/usr/local/`                                        |
| System Files   | `C:\Windows\System32`  | `/etc/`, `/bin/`, `/lib/`                                                     |
| Drive Letters  | `C:\`, `D:\`, `E:\`... | Drives are **mounted** to folders like `/mnt/usb` or `/media/username/device` |

Linux does not use drive letters. Instead, all storage is integrated into a **single hierarchical tree**. External drives appear under `/media` or `/mnt` and are mounted manually or automatically.

#### Control Panel vs Settings Manager

Windows uses the **Control Panel** or **Settings App** to manage system configurations. In Linux Lite, the equivalent is the **Settings Manager**.

| Task                       | Windows                  | Linux Lite Settings Manager                     |
| -------------------------- | ------------------------ | ----------------------------------------------- |
| Display settings           | Display in Control Panel | **Display** module                              |
| Software install/remove    | Programs and Features    | **Lite Software**, **Synaptic**, **Add/Remove** |
| User accounts              | User Accounts            | **User Manager**                                |
| Updates                    | Windows Update           | **Lite Update**, **Synaptic**                   |
| Keyboard, mouse, shortcuts | Devices > Keyboard/Mouse | **Keyboard**, **Mouse and Touchpad**            |
| Sound & audio              | Sound                    | **Audio Mixer**, **PulseAudio Volume Control**  |

Most configuration in Linux Lite can be done graphically, without needing terminal commands.

---

### 16.2 Application Alternatives

Many popular Windows applications have powerful, free, and open-source equivalents on Linux Lite. Below is a comparison of widely used software and their Linux Lite alternatives:

| Windows Application          | Linux Lite Alternative      | Description                                                                          |
| ---------------------------- | --------------------------- | ------------------------------------------------------------------------------------ |
| **Microsoft Office**         | **LibreOffice**             | Full office suite (Word, Excel, PowerPoint alternatives). Supports MS formats.       |
| **Adobe Photoshop**          | **GIMP**                    | Advanced image editor with layers, filters, and plugins.                             |
| **Notepad++**                | **Mousepad**, **Geany**     | Lightweight and advanced text/code editors, respectively. Syntax highlighting, tabs. |
| **WinRAR / 7-Zip**           | **Xarchiver**, **Engrampa** | Archive managers for zip, rar, 7z, tar.gz, and more.                                 |
| **Internet Explorer / Edge** | **Firefox**, **Chromium**   | Secure and modern web browsers.                                                      |
| **Windows Media Player**     | **VLC Media Player**        | Plays all audio/video formats. Customizable and codec-free.                          |
| **Paint**                    | **Pinta**, **KolourPaint**  | Simple drawing programs for quick edits and annotations.                             |
| **Windows Defender**         | **UFW + ClamAV**            | Firewall and antivirus combo. (UFW for firewall, ClamAV for antivirus scanning)      |
| **CMD / PowerShell**         | **Bash Terminal**           | Command-line shell for file management, scripting, and system administration.        |

Most of these alternatives are pre-installed or available via **Lite Software**, **Synaptic Package Manager**, or APT.

To install an app using terminal:

```bash
sudo apt install application-name
```

---
