## 14. Development & Power Tools

Linux Lite is not just for general users—it also provides a capable environment for developers and power users. With support for modern programming languages, source control, advanced text editors, and virtualization platforms, Linux Lite can be used for professional software development, system scripting, and testing virtual machines.

---

### 14.1 IDEs and Editors

#### Geany

**Geany** is a lightweight Integrated Development Environment (IDE) that strikes a balance between speed and functionality. It is especially suitable for users on low-spec systems or those who prefer a traditional interface.

Features:

* Syntax highlighting for dozens of languages
* Code folding and autocompletion
* Terminal emulator plugin
* Lightweight, fast startup
* Built-in compiler/run commands

To install:

```bash
sudo apt install geany
```

Ideal for:

* C, C++, Python, Bash, HTML, PHP, and scripting projects.

#### Visual Studio Code (VS Code)

**VS Code** is a modern and extensible code editor from Microsoft, offering rich support for development workflows via extensions.

Features:

* IntelliSense autocompletion
* Git integration and visual diffing
* Debugging tools
* Extensions for Python, Java, Rust, Docker, and more
* Integrated terminal and task runner

To install:

1. Download the `.deb` package from [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Install using:

   ```bash
   sudo dpkg -i code_*.deb
   sudo apt -f install
   ```

Ideal for:

* Full-stack development, web projects, and DevOps scripting.

#### Vim & Nano

**Nano** is a beginner-friendly terminal text editor with a simple interface.

To open:

```bash
nano filename
```

Key bindings are shown at the bottom (e.g., `^X` to exit).

**Vim** is a modal, powerful editor suitable for advanced users who want full control over their editing workflow.

To open:

```bash
vim filename
```

Basic commands:

* `i`: Insert mode
* `Esc`: Exit to command mode
* `:wq`: Save and exit
* `:q!`: Quit without saving

To install Vim:

```bash
sudo apt install vim
```

---

### 14.2 Programming Setup

Linux Lite supports all major programming languages with minimal configuration. Most tools are available via the APT repository or Snap/Flatpak.

#### Python

Python 3 is pre-installed.

To check:

```bash
python3 --version
```

Install pip and virtual environments:

```bash
sudo apt install python3-pip python3-venv
```

Create a virtual environment:

```bash
python3 -m venv env
source env/bin/activate
```

#### Java

Install OpenJDK:

```bash
sudo apt install openjdk-17-jdk
```

Check version:

```bash
java -version
```

Set environment variables:

```bash
sudo update-alternatives --config java
```

#### Node.js & npm

Install Node.js and npm:

```bash
sudo apt install nodejs npm
```

Check versions:

```bash
node -v
npm -v
```

For newer versions, consider using Node Version Manager (nvm).

#### C/C++

Essential build tools can be installed using:

```bash
sudo apt install build-essential
```

Includes:

* `gcc`, `g++`
* `make`
* `gdb`

Check:

```bash
gcc --version
```

#### Git Setup and Usage

Git is a version control system used to track changes in code and collaborate with others.

Install Git:

```bash
sudo apt install git
```

Initial setup:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Basic commands:

```bash
git init                   # Initialize repo
git clone <url>            # Clone repo
git add .                  # Stage changes
git commit -m "Message"    # Commit changes
git push                   # Push to remote
```

To generate an SSH key:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

---

### 14.3 Virtualization

Linux Lite supports lightweight and full virtualization solutions for testing operating systems, containers, and apps in isolated environments.

#### VirtualBox

VirtualBox is a popular cross-platform virtualization tool.

To install:

```bash
sudo apt install virtualbox
```

Features:

* Supports guest OSes including Windows, Linux, and BSD
* Shared folders, clipboard, and USB passthrough
* Snapshot system for backups and rollbacks

Optional (for full functionality):

```bash
sudo apt install virtualbox-ext-pack
```

To create a new VM:

1. Launch VirtualBox from the menu
2. Click **New**, select OS type and memory
3. Create a virtual hard disk
4. Mount ISO and start the VM

#### QEMU/KVM Setup

**QEMU** with **KVM** provides native-speed virtualization using Linux kernel extensions.

Install required packages:

```bash
sudo apt install qemu-kvm libvirt-daemon-system virt-manager bridge-utils
```

Check if virtualization is supported:

```bash
egrep -c '(vmx|svm)' /proc/cpuinfo
```

Add your user to the libvirt group:

```bash
sudo usermod -aG libvirt $(whoami)
```

Reboot or re-login.

Launch the graphical manager:

```bash
virt-manager
```

Features:

* Create and manage virtual machines with GUI
* Assign CPU cores, RAM, disk
* Advanced networking (bridged, NAT)
* Fast disk I/O using VirtIO

Ideal for:

* Running virtual development servers
* Testing different Linux distributions
* Isolated app testing

---

