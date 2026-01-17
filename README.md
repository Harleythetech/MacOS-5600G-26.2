# MacOS-5600G-26.2 (Tahoe)

This build required specific configuration to handle the Ryzen APU and the ALC1200 audio codec. After resolving initial boot issues, it is now stable with full hardware acceleration and functional audio.

---

## Hardware Compatibility Matrix

| Component | Status | Model / Kext Details |
| :--- | :--- | :--- |
| **CPU** | YES | Ryzen 5 5600G |
| **GPU** | YES | AMD Radeon Vega 7 (IGPU) via **NootedRed** |
| **Wi-Fi** | YES | Intel (OEM) via **itwlm Heliport** |
| **Audio** | YES | Realtek ALC1200 via **AppleALC** and **AppleHDA** |
| **Ethernet** | YES | Realtek RTL8111 via **RTL8111** |
| **Bluetooth** | **NO** | Integrated Intel Card |
| **Motherboard** | YES | Asrock B550m Pro4 (Works with Secure Boot) |

---

## Audio Configuration Guide

> ### FAIR WARNING
> **Always perform a full system backup or APFS snapshot before proceeding with audio fixes.** These steps modify system-level kexts and can lead to bootloops. (Note: I personally had to reinstall the OS during testing before achieving success).

To enable audio for the ALC1200 on this version:

1. **KDK Installation:** Download and install [Dortania - KDK 26.2 - 25C56](https://github.com/dortania/KdkSupportPkg/releases/tag/25C56).
2. **Setup Installer:** Download [MyKextInstaller](https://github.com/Mirone/MyKextInstaller).
3. **Download Kext:** Get the specific [AppleHDA](https://github.com/Mirone/MyKextInstaller/releases/download/1.6/AppleHDA.kext.zip) required for this process.
4. **Injection:** Use **MyKextInstaller** to install the `AppleHDA.kext` into your system volume.
5. **Reboot:** Reboot the system. If audio is still missing, verify your layout-id in the OpenCore config.plist.

---

## Known Issues and Fixes

### Firefox Stability
Firefox has a known conflict with this Hackintosh version. To prevent crashes and ensure proper performance, add the following argument to your `boot-args`:

```text
ipc_control_port_options=0
```
#### Discord Graphical Hangs
Discord (and other Electron-based applications) may cause system-wide hangs due to hardware acceleration conflicts. To resolve this, run Discord without GPU acceleration via the Terminal:
```
open -a Discord --args --disable-gpu
```


# Credits
- [Dortania - OpenCore Documentation](https://dortania.github.io/OpenCore-Install-Guide/) 
- [lzhoang2801 - OpenCore Simplify](https://github.com/lzhoang2801/OpCore-Simplify)
- [Mirone - MyKextInstaller](https://github.com/Mirone/MyKextInstaller)
- [trulyspinach - SMCAMDProcessor](https://github.com/trulyspinach/SMCAMDProcessor)
- [ChefKissInc - NootedRed](https://github.com/ChefKissInc/NootedRed)
