## 5. System Configuration

Linux Lite provides a comprehensive range of tools for configuring system settings, hardware, and network options. Designed with usability in mind, these tools are accessible through the **Settings Manager** and other dedicated utilities that offer a straightforward experience for users at all levels.

---

### 5.1 Settings Manager

The **Settings Manager** in Linux Lite (based on the XFCE environment) serves as the central location for adjusting most system preferences. It offers categorized access to various configuration options.

#### Appearance

The **Appearance** module allows users to change the visual style of the desktop, including themes, icons, fonts, and mouse cursors.

Key features:

* Switch between light and dark themes
* Customize window borders and controls
* Adjust font rendering for better readability

#### Display

The **Display** module is used to configure monitor settings.

Features include:

* Screen resolution and refresh rate selection
* Multiple monitor support (extend or mirror displays)
* Rotation and scaling options
* Set primary display in multi-monitor setups

Settings are stored persistently and applied at each boot.

#### Power Manager

The **Power Manager** controls power-saving features and behavior, especially useful for laptops.

Configuration options include:

* Screen blanking and automatic locking
* Suspend and hibernate settings
* Actions on power button, lid close, and inactivity
* Battery status and notifications

Users can extend battery life and reduce power usage through these options.

#### Mouse & Touchpad

This module provides settings for pointer behavior and input devices.

Mouse settings:

* Sensitivity, acceleration, and button layout (left/right-handed)

Touchpad settings (if supported):

* Enable tap-to-click
* Two-finger scrolling
* Palm detection and disable-while-typing options

#### Keyboard Shortcuts

Keyboard shortcuts can significantly improve productivity. The **Keyboard Settings** module includes a tab for custom shortcut configuration.

Common actions configurable through shortcuts:

* Launch terminal or file manager
* Switch workspaces
* Adjust volume or brightness
* Lock screen or take screenshots

Users can assign, remove, or modify shortcuts to match their workflow preferences.

---

### 5.2 Drivers & Hardware

Linux Lite simplifies the management of hardware and proprietary drivers by including a built-in graphical utility and compatibility tools.

#### Additional Drivers Tool

Linux Lite provides access to Ubuntu’s **Additional Drivers** utility, which detects hardware that can use third-party or proprietary drivers.

Use this tool to:

* Install NVIDIA or AMD graphics drivers
* Enable support for Broadcom or Realtek Wi-Fi chips
* Activate multimedia codecs (if not already installed)

Steps:

1. Go to **Menu > Settings > Install Drivers**
2. Wait for the system to scan your hardware
3. Select and apply the recommended drivers
4. Reboot the system if required

#### Printer Setup (with CUPS GUI)

Linux Lite uses **CUPS (Common Unix Printing System)** for printer management.

Steps to set up a printer:

1. Open **Menu > Settings > Printers**
2. Click **Add** to begin the printer detection process
3. Select your printer from the list (USB or network)
4. Follow prompts to install drivers or select a model
5. Set the printer as default and print a test page

CUPS also offers a web-based interface available at `http://localhost:631` for advanced management, though most users will find the GUI sufficient.

#### Scanner Support

Linux Lite supports most modern scanners using **XSane** or **Simple Scan**, which can be installed via Lite Software or Synaptic.

Steps:

1. Connect the scanner via USB
2. Launch **Simple Scan** from the menu
3. Perform a test scan and adjust resolution or color options as needed

Many multifunction printers with scanning capabilities are automatically detected and supported via SANE backends.

---

### 5.3 Network Configuration

Linux Lite includes both graphical tools and terminal-based methods for managing network connections and settings.

#### Ethernet & Wi-Fi Setup

The **Network Manager** handles all basic network configurations.

Features:

* Automatically connects to available Ethernet or Wi-Fi
* Save and prioritize wireless networks
* Manage proxy settings and static IPs

To access:

* Use the **Network icon** in the system tray
* Or go to **Menu > Settings > Network Connections**

Users can create, modify, or delete network profiles for both wired and wireless interfaces.

#### Firewall (GUFW)

Linux Lite includes **GUFW**, a graphical front-end for the Uncomplicated Firewall (UFW).

To enable and configure:

1. Open **Menu > Settings > Firewall Configuration**
2. Enable the firewall with a single switch
3. Add or remove rules for specific ports or applications
4. Set up default policies (allow/deny incoming/outgoing)

This provides an essential layer of security, especially on public or shared networks.

#### VPN Setup

Linux Lite supports VPN connections through the **Network Manager**.

Supported types:

* PPTP, L2TP, and OpenVPN (via plugins)
* Import `.ovpn` configuration files

Steps:

1. Install relevant plugins using Synaptic or terminal
2. Go to **Network Connections > Add**
3. Select VPN and fill in the required details
4. Save and connect from the network icon in the panel

Advanced users can also use tools like `openvpn` or `wireguard` via terminal for scripting and custom setups.

#### Network Sharing (Samba)

Linux Lite uses **Samba** to facilitate file and printer sharing between Linux and Windows systems.

To install and configure:

1. Install Samba via Synaptic or terminal:

   ```bash
   sudo apt install samba
   ```
2. Use **Thunar file manager** to right-click a folder and select **Properties > Share**
3. Enable sharing and set permissions
4. Restart Samba service:

   ```bash
   sudo systemctl restart smbd
   ```

Windows systems on the same network will now be able to access shared folders via the `\\hostname` or `\\IP-address`.

---
