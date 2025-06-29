## 10. Security & Privacy

Security in Linux Lite is grounded in the robust foundations of the Linux kernel and Ubuntu repositories. However, proactive configuration can further enhance protection from intrusions, malware, and misconfigurations. This section provides practical steps for improving system security and maintaining user privacy.

---

### 10.1 Firewalls

Linux Lite includes a user-friendly firewall tool called **GUFW**, a graphical interface for **UFW** (Uncomplicated Firewall). By default, the firewall is disabled but can be easily enabled and configured for everyday use.

#### GUFW Usage

To open GUFW:

* Go to **Menu > Settings > Firewall Configuration**
* Enter your administrator password when prompted

Steps to enable the firewall:

1. Toggle the **Status** switch to "ON"
2. By default, GUFW sets:

   * Incoming connections: Deny
   * Outgoing connections: Allow

These settings block unauthorized incoming connections while allowing all outbound traffic, which is sufficient for most users.

Adding rules:

* Click **Rules > Add**
* Select the **Preconfigured** tab for common applications like SSH, Samba, or HTTP
* Or use **Simple/Advanced** tabs to define ports, protocols, and IP addresses

All changes take effect immediately and persist across reboots.

#### Firewall Profiles

GUFW supports creating different firewall profiles that can be switched based on the network environment.

To create profiles:

1. Click the **Profile** drop-down menu in GUFW
2. Select **New Profile**
3. Name your profile (e.g., Home, Work, Public)
4. Configure specific rules for that environment

This allows you to:

* Block all incoming/outgoing traffic in untrusted networks
* Allow Samba or SSH access in trusted internal networks
* Use custom port rules for specific scenarios

You can manually switch between profiles as needed, depending on where the system is being used.

---

### 10.2 AppArmor

**AppArmor** (Application Armor) is a Mandatory Access Control (MAC) framework that confines programs to a limited set of resources and operations, reducing the impact of potential exploits.

Linux Lite includes AppArmor by default and runs a set of preloaded profiles for core services like `cups`, `dnsmasq`, and `network-manager`.

#### Enable and Configure

To verify AppArmor is active:

```bash
sudo aa-status
```

To manually enable it (if disabled):

```bash
sudo systemctl enable apparmor
sudo systemctl start apparmor
```

Managing AppArmor profiles:

* Profiles are stored in `/etc/apparmor.d/`
* Each file represents a set of rules for a specific application
* You can edit profiles using a text editor:

  ```bash
  sudo nano /etc/apparmor.d/usr.bin.firefox
  ```

After making changes:

```bash
sudo apparmor_parser -r /etc/apparmor.d/your-profile
```

To disable a specific profile:

```bash
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.firefox
```

Use `aa-complain` and `aa-enforce` to switch modes:

```bash
sudo aa-complain /etc/apparmor.d/usr.bin.firefox   # Log-only
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox    # Enforced mode
```

#### Viewing Logs

AppArmor violations and status messages are logged by the system journal.

To view recent logs:

```bash
journalctl -k | grep apparmor
```

Or to monitor in real-time:

```bash
sudo journalctl -f | grep apparmor
```

These logs help identify denied actions and can be used to refine profiles as needed.

---

### 10.3 System Hardening

System hardening refers to steps that reduce attack surfaces and enforce security policies beyond default configurations.

#### Disable Root Login

Linux Lite uses `sudo` for administrative tasks, and root login is disabled by default in the GUI. However, it is important to ensure root access is blocked over the terminal and SSH.

To disable root login via SSH:

1. Edit the SSH config:

   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
2. Find the line:

   ```text
   PermitRootLogin yes
   ```

   and change it to:

   ```text
   PermitRootLogin no
   ```
3. Save and restart SSH:

   ```bash
   sudo systemctl restart ssh
   ```

To disable root password login entirely (if not already disabled):

```bash
sudo passwd -l root
```

This locks the root account, preventing login even if someone knows the password.

#### Enable Automatic Updates

Automatic updates can help ensure timely application of security patches without requiring manual intervention.

Enable unattended upgrades:

```bash
sudo apt install unattended-upgrades
```

To configure:

```bash
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

Review or edit config file:

```bash
sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
```

You can customize:

* Which packages are upgraded
* Email notifications
* Auto-remove behavior

Ensure that periodic updates are scheduled in `/etc/apt/apt.conf.d/10periodic`:

```text
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```

#### Fail2Ban (Basic Setup)

**Fail2Ban** monitors log files for malicious login attempts and blocks IPs that show signs of brute-force attacks.

Install Fail2Ban:

```bash
sudo apt install fail2ban
```

Start and enable the service:

```bash
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

Basic jail configuration is stored in:

```
/etc/fail2ban/jail.conf
```

To customize without affecting defaults, create:

```
/etc/fail2ban/jail.local
```

Example configuration for SSH:

```ini
[sshd]
enabled = true
port    = ssh
logpath = %(sshd_log)s
maxretry = 5
```

Check status:

```bash
sudo fail2ban-client status
sudo fail2ban-client status sshd
```

This provides an effective first layer of defense against automated attacks on SSH and other services.
