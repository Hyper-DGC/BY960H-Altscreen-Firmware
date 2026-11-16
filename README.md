# MHI2Q Wireless CarPlay Adapter (BY960H) Firmware Mod

Custom firmware modification for the **BY960H Wireless CarPlay Adapter**, enabling advanced instrument cluster integration, including Alt Screen, Route Guidance Integration (RGI), and Telephone settings on compatible MHI2Q infotainment systems.

**Tested and confirmed working** with the [kamgurgul/mib2q-carplay](https://github.com/kamgurgul/mib2q-carplay) repository.

**Adapter:** [BY960H Wireless CarPlay Adapter](https://www.amazon.ca/dp/B0H7BQK56W)

---

## ⚠️ Important Compatibility Warning

> [!CAUTION]
> **This modification is ONLY compatible with the BY960H adapter.**
>
> Installing this firmware on a different dongle model or hardware revision may permanently brick the device.
>
> Designed specifically for vehicles equipped with **MHI2Q** infotainment systems running the compatible cluster navigation modification.

---

## ✨ Features & Status

| Feature | Status | Notes |
|---|:---:|---|
| Wireless CarPlay | ✅ Working | Standard dongle functionality |
| Alt Screen / CarPlay Map in Cluster | ✅ Working | Displays correctly on supported clusters |
| Route Guidance Arrows (RGI) | ✅ Working | Turn-by-turn directions displayed on the instrument cluster |
| Telephone Settings | ✅ Working | Call status and menus functional |
| Track Cover Art | ❌ Not Working | Currently unsupported by the dongle's video/data stream |

---

## 📥 Installation

### Requirements

- Compatible BY960H wireless CarPlay adapter.
- Repository files downloaded or cloned onto your computer.
- Mac or Windows laptop.
- Laptop connected to the Wi-Fi network broadcast by the CarPlay adapter.

> [!IMPORTANT]
> Your laptop must be connected to the dongle's Wi-Fi network throughout the installation process.

### 🍎 macOS Installation (Tested)

The following installation procedure has been tested and confirmed working.

**1. Connect to the adapter**

- Power on the BY960H adapter.
- Connect your Mac to the Wi-Fi network broadcast by the adapter.

**2. Open Terminal in the repository folder**

- Open Finder and navigate to the folder containing the repository files.
- Right-click inside the folder.
- Select **New Terminal at Folder**.
- Alternatively, open Terminal manually and navigate to the repository directory using `cd`.

**3. Run the installation script**

From inside the repository folder, execute:

```bash
DEV=192.168.18.9 ./install.sh
```

The `DEV` variable specifies the IP address of the CarPlay adapter. The default address used here is `192.168.18.9`.

**4. Remove factory hook restrictions**

After the installation script finishes, execute:

```bash
curl -s -G --data-urlencode 'cmd=rm -f /etc/hook/native111.off /mnt/UDISK/hook/native111.off /mnt/UDISK/hook/bridge.off' http://192.168.18.9/cgi-bin/shell.cgi
```

This removes the factory `.off` hook flags that would otherwise interfere with alternative screen and cluster integration functionality.

**5. Power-cycle the adapter**

Once both commands have completed:

1. Unplug the CarPlay adapter.
2. Wait a few seconds.
3. Plug the adapter back in.
4. Reconnect to CarPlay.

**6. Verify installation**

Confirm the following:

- The CarPlay map appears on the instrument cluster.
- Start navigating to a destination.
- Confirm that the native turn-by-turn navigation arrow appears on the instrument cluster.

If both are working, installation is complete.

---

### 🪟 Windows Installation (Untested)

> [!WARNING]
> Windows installation has not been tested or confirmed. The following procedure is expected to work but may require adjustments.

The installation process should be similar to macOS, using Windows Terminal with a Bash-compatible environment such as Git Bash or WSL.

**1. Connect to the adapter**

- Power on the BY960H adapter.
- Connect your Windows laptop to the adapter's Wi-Fi network.

**2. Open Terminal in the repository folder**

- Open the repository folder in File Explorer.
- Right-click inside the folder.
- Select **Open in Terminal**.
- Ensure you are using a Bash-compatible environment.

**3. Run the installation script**

```bash
DEV=192.168.18.9 ./install.sh
```

**4. Remove factory hook restrictions**

After the installation script finishes, execute:

```bash
curl -s -G --data-urlencode 'cmd=rm -f /etc/hook/native111.off /mnt/UDISK/hook/native111.off /mnt/UDISK/hook/bridge.off' http://192.168.18.9/cgi-bin/shell.cgi
```

This removes the factory `.off` hook flags that would otherwise interfere with alternative screen and cluster integration functionality.

**5. Power-cycle the adapter**

- Unplug the adapter.
- Wait a few seconds.
- Plug it back in.
- Reconnect CarPlay.

**6. Verify installation**

Confirm that the CarPlay map appears on the instrument cluster and that native navigation arrows appear when navigating.

---

## 🔄 Uninstallation / Restore

To remove the modification, follow the same general procedure as installation.

1. Connect your laptop to the CarPlay adapter's Wi-Fi network.
2. Open Terminal in the repository folder.
3. Run the following command:

```bash
DEV=192.168.18.9 ./install.sh remove
```

The `remove` argument instructs the installation script to execute its removal procedure instead of installing the modification.

4. Once the script finishes, unplug the adapter.
5. Wait a few seconds and plug it back in.

---

## 📝 Additional Notes

- The default adapter IP address used in these instructions is `192.168.18.9`.
- If the adapter uses a different IP address, replace `192.168.18.9` in the commands with its current IP address.
- Always execute the installation and removal commands from the repository folder containing `install.sh`.
- Do not disconnect the adapter while the installation script is running.
- A power cycle is required after installation for the changes to take effect.

---

## ✅ Tested Configuration

| Component | Version / Model |
|---|---|
| Wireless CarPlay Adapter | BY960H |
| Infotainment System | MHI2Q |
| Compatible Software | [kamgurgul/mib2q-carplay](https://github.com/kamgurgul/mib2q-carplay) |
| macOS Installation | Tested and confirmed working |
| Windows Installation | Untested |

---

**Disclaimer:** This modification is provided as-is. Proceed at your own risk. Always verify your hardware compatibility before attempting installation.
