## 11. Printing & Scanning

Linux Lite includes built-in support for a wide range of printers and scanners. Most devices are detected automatically, and tools like **CUPS**, **system-config-printer**, **Simple Scan**, and **SANE** offer easy setup and configuration for both home and office use.

---

### 11.1 Printer Setup

Linux Lite uses the **CUPS (Common Unix Printing System)** backend for managing printers. The graphical front-end **system-config-printer** provides an intuitive interface to add, remove, and manage print jobs and devices.

#### Using CUPS GUI (system-config-printer)

To configure printers:

1. Open the **Printer Settings** tool via:

   * **Menu > Settings > Printers**
   * Or run in terminal:

     ```bash
     system-config-printer
     ```

2. Click **Add** to begin the printer setup wizard.

3. Linux Lite will scan for:

   * USB printers
   * Network printers (via Bonjour, IPP, or JetDirect)
   * Shared printers via Samba or other protocols

4. Select your printer from the detected list.

5. If your printer model is supported:

   * The driver will be applied automatically.
   * If not, you may need to select a **PPD file** (PostScript Printer Description) or install the manufacturer’s Linux driver.

6. Once installed, print a test page to verify functionality.

You can access and manage all added printers directly from this GUI, including:

* Setting a default printer
* Managing queues
* Pausing/resuming jobs
* Adjusting printer properties

#### Network Printer Setup

For setting up a printer on your network:

1. Ensure your printer is connected to the same network (Wi-Fi or Ethernet).

2. Launch **Printers** and click **Add**.

3. Wait for network printers to appear under:

   * **Network Printer > IPP**
   * **LPD/LPR Host or Printer**
   * **JetDirect**
   * Or **Internet Printing Protocol (https/ipp)**

4. If the printer is not auto-detected:

   * Choose **Enter URI** and provide something like:

     ```
     ipp://192.168.1.100/ipp/print
     ```

     (Replace with your printer’s actual IP address)

5. Complete the setup by selecting the correct model and driver.

Some printers support auto-discovery via **mDNS/Bonjour** (Avahi). Ensure the `avahi-daemon` service is running:

```bash
sudo systemctl enable --now avahi-daemon
```

#### Troubleshooting

* **Printer not detected**:

  * Check USB cable or network connection.
  * Try rebooting printer and system.
  * Run:

    ```bash
    lpinfo -v
    ```

    to list available devices.

* **Driver not found**:

  * Check manufacturer’s website for `.deb` packages or Linux drivers.
  * Install `printer-driver-gutenprint` and `printer-driver-hpijs` for broader compatibility:

    ```bash
    sudo apt install printer-driver-gutenprint printer-driver-hpijs
    ```

* **CUPS Web Interface**:

  * Access advanced settings by visiting:

    ```
    http://localhost:631
    ```
  * From here, you can manage printers, classes, queues, and permissions.

* **Job stuck in queue**:

  * Cancel all jobs:

    ```bash
    cancel -a
    ```
  * Or reset the print service:

    ```bash
    sudo systemctl restart cups
    ```

---

### 11.2 Scanners

Linux Lite supports most scanners out-of-the-box through **SANE (Scanner Access Now Easy)** and provides a graphical front-end with **Simple Scan**.

#### Simple Scan

**Simple Scan** is a lightweight and user-friendly scanner utility.

To install (if not already installed):

```bash
sudo apt install simple-scan
```

To use:

* Go to **Menu > Graphics > Simple Scan**
* The scanner will auto-detect and display in the interface
* Choose **Text** or **Photo** mode
* Click **Scan** to begin scanning

Features include:

* Multi-page PDF support
* Image cropping and rotation
* Save as PDF, JPEG, PNG
* Integration with document editors

Simple Scan supports most flatbed and all-in-one devices without additional configuration.

#### SANE Configuration

**SANE** is the backend that interfaces with scanner hardware. Most USB scanners work without any configuration.

To verify scanner is detected:

```bash
scanimage -L
```

If the scanner is listed, it’s working.

For network scanners:

1. Edit the SANE configuration file:

   ```bash
   sudo nano /etc/sane.d/net.conf
   ```
2. Add your scanner’s IP address (e.g. `192.168.1.120`)
3. Enable the network backend:

   ```bash
   sudo nano /etc/sane.d/dll.conf
   ```

   Uncomment:

   ```
   net
   ```

To test:

```bash
scanimage -L
```

If no scanner is detected:

* Make sure the device is powered on and connected
* Confirm your user is part of the `scanner` group:

  ```bash
  sudo usermod -aG scanner $USER
  ```

Reboot to apply group changes.

For advanced scanning tools, you can also try:

* **XSane** (advanced scanning with more options)
* **gscan2pdf** (scan to searchable PDFs)

---

