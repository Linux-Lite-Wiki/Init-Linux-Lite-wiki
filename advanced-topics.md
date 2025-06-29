## Advanced Topics
**Section 9: Advanced Topics** of the Linux Lite Wiki:

---

## 9. Advanced Topics

This section introduces more advanced aspects of Linux Lite, enabling users to deepen their understanding of the system and tailor it to their specific needs. Topics include terminal usage, monitoring, service management, and desktop customization.

---

### 9.1 Terminal Guide

#### Shell Basics

Linux Lite uses the Bash shell by default. The shell is a command-line interface that interprets your commands and runs system utilities or scripts.

Basic syntax:

```bash
command [options] [arguments]
```

Examples:

```bash
ls -l /home            # List files with details
cd Documents           # Change to the Documents directory
mkdir new_folder       # Create a new directory
rm file.txt            # Delete a file
```

Keyboard shortcuts:

* `Tab`: Auto-complete file or command names
* `Ctrl + C`: Cancel running command
* `Ctrl + D`: Log out of shell
* `Ctrl + R`: Reverse search command history

#### Common Commands

File and directory management:

```bash
cp file1 file2         # Copy file
mv file1 file2         # Move/rename file
rm file1               # Delete file
touch file1            # Create empty file
nano file1             # Edit file in terminal
```

System and package management:

```bash
sudo apt update              # Update package lists
sudo apt upgrade             # Upgrade installed packages
sudo apt install app-name    # Install a package
sudo apt remove app-name     # Remove a package
```

Navigation:

```bash
pwd                    # Print current directory
ls                     # List files in current directory
cd ..                  # Go up one directory
```

Process and system info:

```bash
ps aux                 # View running processes
kill PID               # Terminate a process
df -h                  # Disk usage
free -h                # RAM usage
```

#### Bash Aliases

Aliases let you define shortcuts for long or repetitive commands.

Create or edit aliases:

```bash
nano ~/.bashrc
```

Add lines like:

```bash
alias update='sudo apt update && sudo apt upgrade'
alias cls='clear'
alias ll='ls -alF'
```

Activate changes:

```bash
source ~/.bashrc
```

Aliases streamline your workflow and reduce the need to type full commands repeatedly.

---

### 9.2 System Logs & Monitoring

#### Log Locations

Linux Lite stores system logs in `/var/log/`.

Important log files:

* `/var/log/syslog`: General system messages
* `/var/log/dmesg`: Kernel ring buffer
* `/var/log/auth.log`: Authentication events
* `/var/log/apt/`: Package manager logs
* `/var/log/Xorg.0.log`: Display server logs

Use `less`, `cat`, or `tail` to read logs:

```bash
sudo less /var/log/syslog
```

#### System Monitor

**Task Manager** in Linux Lite offers a graphical view of running processes and system usage.

To open:

* Go to **Menu > System > Task Manager**

You can:

* Monitor CPU, memory, and disk usage
* Kill unresponsive applications
* View real-time resource load

For a more detailed graphical interface, install **System Monitor** via Lite Software or Synaptic.

#### `top`, `htop`, `journalctl`

**top**:
A built-in terminal tool that shows real-time system resource usage.

```bash
top
```

Press `q` to quit.

**htop**:
A more interactive version of `top` with better visuals. Install it using:

```bash
sudo apt install htop
htop
```

**journalctl**:
Used to query logs from `systemd`.

Examples:

```bash
journalctl             # View all logs
journalctl -b          # Logs from current boot
journalctl -u servicename.service  # Logs for a specific service
journalctl -xe         # View recent critical logs
```

Use arrows or `PgUp/PgDn` to scroll.

---

### 9.3 System Services

#### systemd Basics

Linux Lite uses `systemd` as its init system to manage services during boot and runtime.

Key systemctl commands:

```bash
systemctl status         # Overview of services
systemctl status ssh     # Status of specific service
systemctl start service  # Start a service
systemctl stop service   # Stop a service
systemctl restart service# Restart a service
```

Check all enabled services:

```bash
systemctl list-units --type=service
```

#### Enable/Disable Services

To enable a service at boot:

```bash
sudo systemctl enable service
```

To disable a service from starting at boot:

```bash
sudo systemctl disable service
```

These commands are essential for managing background daemons such as networking, printing, or cron jobs.

#### Boot Optimization

To analyze boot performance:

```bash
systemd-analyze
```

To see which services slow down boot:

```bash
systemd-analyze blame
```

You can disable unused services using `systemctl` to speed up boot time. Exercise caution—disabling essential services can break functionality.

---

### 9.4 Customizing the Desktop

#### XFCE Panel Tweaks

To modify the panel:

* Right-click the panel > **Panel > Panel Preferences**

Customization options:

* Change position (top, bottom, left, right)
* Add/removal of panel items (via “Items” tab)
* Adjust panel opacity and autohide behavior
* Add launchers for favorite apps

You can also create multiple panels if needed.

#### Themes, Icons, Fonts

To change visual style:

* Go to **Menu > Settings > Appearance**

From here, you can:

* Switch between pre-installed themes (light, dark, etc.)
* Select icon sets
* Adjust font types and anti-aliasing

Additional themes and icons can be installed via:

```bash
sudo apt install arc-theme papirus-icon-theme
```

User themes can be placed in `~/.themes/` and icons in `~/.icons/`.

#### Keyboard Shortcuts

Customize keyboard shortcuts from:

* **Menu > Settings > Keyboard > Application Shortcuts**

Add new shortcuts for commands like:

```bash
xfce4-terminal        # Open terminal
xfce4-screenshooter   # Take screenshot
xflock4               # Lock screen
```

You can also bind custom scripts or assign shortcuts to workspace navigation and window control.

---


