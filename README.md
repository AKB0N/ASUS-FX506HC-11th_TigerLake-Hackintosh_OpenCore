# Hackintosh Guide for **Asus FX506HC**
**This guide it's updated to OpenCore 0.8.8 and NOT YET tested on a friend's laptop on Ventura.**

<!-- START shields -->
<div>
    <!-- downloads --><a href="https://github.com/AKBON/ASUS-FX506HC-11th_TigerLake-Hackintosh_OpenCore/releases">
        <img src="https://img.shields.io/github/downloads/AKBON/ASUS-FX506HC-11th_TigerLake-Hackintosh_OpenCore/total" alt="downloads"/>
    </a>
    <!-- version --><a href="https://github.com/AKBON/ASUS-FX506HC-11th_TigerLake-Hackintosh_OpenCore/releases/latest">
        <img src="https://img.shields.io/github/release/AKBON/ASUS-FX506HC-11th_TigerLake-Hackintosh_OpenCore.svg" alt="latest version"/>
    </a>
     <!-- platform --><a href="https://github.com/AKBON/ASUS-FX506HC-11th_TigerLake-Hackintosh_OpenCore">
        <img src="https://img.shields.io/badge/platform-macOS-lightgrey.svg" alt="platform"/>
    </a>
</div>
</br>
<!-- END shields -->

![Asus FX506HC running macOS Ventura](/Docs/Images/Asus-FX506HC-macOS.png)

# Specifications
Here's the [Amazon Link](https://www.amazon.com/ASUS-TUF-Gaming-F15-i5-11400H/dp/B0CCGDQZ1M) for this exact model.

| Component | Name |
|:--- |:---|
| Motherboard:  | FX506HC **HM470** |
| CPU: | **Intel** i5-11400H |
| RAM: | **Samsung** M471A1G44AB0-CWE 16GB 3200MHz |
| iGPU: | **Intel** Tiger Lake-H GT1 (Mobile) |
| dGPU: | **nVidia** GeForce RTX 3050 Laptop (DISABLED) |
| NVMe: | **SAMSUNG** MZVLQ512HBLU-00B00 |
| WiFi/BT: | **MediaTek** MT7921 (Type CNVi) |
| Audio: | **RealTek** ALC256 |
| Ethernet: | **RealTek** RTL8168 |
| Trackpad: | **ELAN1200** Precision TouchPad (Type HID) |
| Keyboard: | PS/2 Keyboard (ISO Spain)|
><strong>Note:</strong> The WiFi/BT Card needs to be replaced with a **BCM94352Z**  in order to have FULL Native Wirelless Features.

# Working Status
 - ### **Fully Working**
    - Built-In Display
    - Jack 3.5mm, Speakers & Microphone
    - DC-IN & Battery
    - NVMe & HDD
    - Camera
    - Ethernet
    - Keyboard


 - ### **Partially Working**
    - [All USB Ports](/Docs/Images/Guide/Asus-FX506HC-layout.png) (Not mapped correctly YET)

- ### **Not Working**
    - dGPU *(nVidia RTX 3050 Laptop)*
    - WiFi
    - Bluetooth
    - HDMI Port
    - Continuity Features (Apple Ecosystem Fancy Things)
    - Trackpad

---

# GUIDE OF INSTALLATION
<!-- BOOTABLE START -->
<details open>
<summary><h3>Making the Bootable USB</h3></summary>
    <h3>From macOS:</h3>
<p><a href="https://support.apple.com/en-us/HT201372"></a>Link to Apple's Guide</p>

**Download installers:** [Ventura](https://apps.apple.com/us/app/macos-ventura/id1638787999) - [Monterrey](https://apps.apple.com/es/app/macos-monterey/id1576738294) - [Big Sur](https://itunes.apple.com/us/app/macos-big-sur/id1526878132) - [Catalina](https://itunes.apple.com/us/app/macos-catalina/id1466841314) - [Mojave](https://itunes.apple.com/us/app/macos-mojave/id1398502828) - [High Sierra](https://itunes.apple.com/us/app/macos-high-sierra/id1246284741)

[(Alternative Download (Mr. Machintosh Post))](https://mrmacintosh.com/how-to-download-macos-catalina-mojave-or-high-sierra-full-installers/)

1. Connect a >=16 GB pendrive.
2. Open *Disk Utility* and Erase the USB with the name: *MyVolume*.
3. Open *Terminal* and use the proper commands for your macOS installer:
- Ventura: `sudo /Applications/Install\ macOS\ Ventura.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- Monterrey: `sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- Big Sur: `sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- Catalina: `sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- Mojave: `sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- High Sierra: `sudo /Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

![Terminal](/Docs/Images/Guide/BootableUSB.png)

### From Windows:

[**Link to Dortania's Guide**](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/windows-install.html#downloading-macos)

### From Linux:

[**Link to Dortania's Guide**](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/linux-install.html)

 ---
    
</details>
<!-- BOOTABLE END -->
<!-- BIOS START -->
<details open>
<summary><h3>BIOS Settings</h3></summary>
 
- Make Sure you have [Latest BIOS v311]([https://www.asus.com/supportonly/FX504GE/HelpDesk_BIOS/](https://www.asus.com/supportonly/fx506hc/helpdesk_bios/))
- After Updating the BIOS, you just need to **DISABLE** `Secure Boot`, and you are good to go.
---
 
</details>

<!-- BIOS END -->

<!-- POST-INSTALL START-->

<details open>
  <summary><h3>Post Installation</h3></summary>
 
Open Terminal.app and run those commands:
~~~
sudo pmset autopoweroff 0
sudo pmset powernap 0
sudo pmset standby 0
sudo pmset proximitywake 0
sudo pmset tcpkeepalive 0
~~~
>These 5 commands help fixing possible Sleep/Wake Issues
  
~~~
  - sudo rm /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist
  - sudo rm /Library/Preferences/SystemConfiguration/preferences.plist
~~~
>These 2 commands help fixing possible iCloud Ban/iMessages Ban or WiFi/Ethernet Issues (Use only if you want or need)

---

</details>
<!-- POST-INSTALL END -->

If this guide has been useful for you, don't forget to give me a star ⭐️❤️
