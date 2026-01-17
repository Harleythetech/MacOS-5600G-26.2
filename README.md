# MacOS-5600G-26.2
Took me a while to get this working properly but now it works with proper audio!


| Parts | Works | - |
|---|---|---|
| CPU | YES | Ryzen 5 5600G |
| GPU | YES (via NootedRed) | AMD Radeon Vega 7 (IGPU)|
| Wi-Fi | YES (via itwlm Heliport) | Intel (forgot the model) |
| Audio | YES (via AppleALC, AppleHDA) | Realtek ALC1200|
| Ethernet | YES (via RTL8111) | Realtek RTL8111 |
| Bluetooth | NO | Same intel card |
| USB | YES (2.0, 3.1, Type C) | - |

# To Get Audio Working:
### FAIR WARNING: Make sure to do a backup / snapshot of your system before proceeding to fixing the audio as this may cause bootloops and other shit that you'd hate. (Trust me, I had to reinstall tahoe before i managed to make it work)

Download [Dortania - KDK 26.2 - 25C56](https://github.com/dortania/KdkSupportPkg/releases/tag/25C56) and install it, after that download [MyKextInstaller](https://github.com/Mirone/MyKextInstaller) and make sure to AGAIN do a backup / snapshot of your build before proceeding.

Once you have [MyKextInstaller](https://github.com/Mirone/MyKextInstaller) up and running, download [AppleHDA](https://github.com/Mirone/MyKextInstaller/releases/download/1.6/AppleHDA.kext.zip) from the same source or just by pressing the link. Once done, Proceed in installing the AppleHDA.kext using MykextInstaller.

It should prompt you to rebooot the system, reboot it and the audio should now work. (if not you fucked something in the config)

# Any issues that requires fixing:
- Firefox on 26.2 has a known issue on hackintosh to prevent it from running properly, To fix this add the following args to your boot arg (this is already added in my bootarg, but incase you are making one on your own then do add this)
```
ipc_control_port_options=0
```
- Discord on 26.2 has some graphical issues that causes a system wide hang, (probably an electron issue) to fix this just run discord without gpu acceleration using termnial or automate it
```
open -a Discord --args --disable-gpu
```


# Credits
- [Dortania](https://dortania.github.io/OpenCore-Install-Guide/)
- [lzhoang2801 - OpenCore Simplify](https://github.com/lzhoang2801/OpCore-Simplify)
- [Mirone - MyKextInstaller](https://github.com/Mirone/MyKextInstaller)
- [trulyspinach - SMCAMDProcessor](https://github.com/trulyspinach/SMCAMDProcessor)
- [ChefKissInc - NootedRed](https://github.com/ChefKissInc/NootedRed)
