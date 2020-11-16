# Hackintosh-H370i-Big-Sur-EFI

H370i + i5 8600 + RTX 2070S + OpenCore

Modified from [SuperNG6](https://github.com/SuperNG6)/**[MSI-B360-Catalina-EFI](https://github.com/SuperNG6/MSI-B360-Catalina-EFI)**[(commit 8eea1d7)](https://github.com/SuperNG6/MSI-B360-Catalina-EFI/commit/8eea1d72913fae12a1b656ea2bf869e7fc4bb92f).

## Devices

- Processor: i5 8600

- Motherboard: Asus H370i (version: 2811)

- Graphics:

    Intel UHD Graphics 630 (be used when using MacOS)

    NVIDIA GeForce RTX 2070 SUPER (be disabled)

- Memory: KLEVV 2666 16G * 2

- WLAN: Intel Wireless-AC 9560 160MHz (provided by motherboard)

- Storage: 

    Western Digital SN500 1T * 1 (Only Install Windows)

    Hikvision c2000 1T * 1 (Only Install MacOS)

    Seagate ST4000VX007 * 1

    HGST 725050A7E630 * 1 (In a USB hard drive box)

- Power: Corsair SF600 Platinum

- System: 

    Windows 10 2004

    MacOS Big Sur 20B29

- Monitor: SONGREN 240E (4k60hz/2k144hz, choosing 4k 60hz), HDMI or DP

![](https://cdn.jsdelivr.net/gh/HuaHuaY/Hackintosh-H370i-Big-Sur-EFI/img/0.0.png)

![](https://cdn.jsdelivr.net/gh/HuaHuaY/Hackintosh-H370i-Big-Sur-EFI/img/0.1.png)

![](https://cdn.jsdelivr.net/gh/HuaHuaY/Hackintosh-H370i-Big-Sur-EFI/img/0.2.png)

## Status

### USB

Every port works well but some funtions of are limited.

I make USBPorts.kext to follow 15 USB ports limit.

- 2 x USB 3.1 ports (at back panel, Type-A, support USB 2.0, 3.0 and 3.1)
- 3 x USB 3.0 ports (at back panel, Type-A, only support USB 2.0).
- 1 x USB 3.0 port (at back panel, Type-C SW, only support USB 3.0).
- 2 x  USB 3.0 ports (internal, Type-A, only support one and both support USB 2.0 and 3.0).

### Bluetooth

Work well.

Use [OpenIntelWireless](https://github.com/OpenIntelWireless)/**[IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)**.

![](https://cdn.jsdelivr.net/gh/HuaHuaY/Hackintosh-H370i-Big-Sur-EFI/img/1.png)

### WLAN

Work well.

Use [OpenIntelWireless](https://github.com/OpenIntelWireless)/**[itlwm](https://github.com/OpenIntelWireless/itlwm)**.

![](https://cdn.jsdelivr.net/gh/HuaHuaY/Hackintosh-H370i-Big-Sur-EFI/img/2.png)

### Audio

Work well.

I use some config in `config.plist`:

```
<key>PciRoot(0x0)/Pci(0x1f,0x3)</key>
<dict>
	<key>device-id</key>
	<data>cKEAAA==</data>
	<key>layout-id</key>
	<data>BwAAAA==</data>
</dict>
```

![](https://cdn.jsdelivr.net/gh/HuaHuaY/Hackintosh-H370i-Big-Sur-EFI/img/3.png)

### Sleep

Work well.

### Hardware Decoding

Work well. And I ban the RTX 2070S in the config.plist.

![](https://cdn.jsdelivr.net/gh/HuaHuaY/Hackintosh-H370i-Big-Sur-EFI/img/5.png)

### HDMI and DP

#### When you want to change HDMI or DP config, please see this first.

In the path `Root - DeviceProperties - Add - PciRoot(0x0)/Pci(0x2,0x0)` of `config.plist`, there are two connectors "con0" and "con1", which point to "DP" and "HDMI". 

There are two busid configs, "Framebuffer-con0-busid" and "Framebuffer-con1-busid". In Hackintool, you will see the value of two busid are "5" and "6". However, if you change any of them to "5" or "6", HDMI will be disabled.

#### Test Results

When I only use HDMI or DP, I can use the monitor well. But when coming into the system after Apple progress bar, there is a short black screen when using HDMI.

When I connect HDMI and DP to my monitor at the same time, although most of the people will not do this, some errors happen.

- As we all know, when we turn on the Hackintosh, the Apple progress bar will be divided into two sections to load. And there is a short black screen between the two sections. Whether I choose HDMI or DP in the monitor menu, the Apple icon will be very big in the first section, and there will be black screen in the second section.
- There will take a lot of time to wake from black screen, and it seems to be useful to load faster that unplug the HDMI cable and plug it again.
- After unpluging and plugging HDMI cable, I can find that there are two screen in the system menu. I can switch to HDMI by using the button and menu of my monitor. However, there is just a very small chance of switching successfully. At the most time, I will find I am using DP again by checking the monitor menu.
- When turning down the Hackintosh, the resolution of the background picture may be wrong.

I have another small portable screen which supports TYPE-C one-line communication, or mini HDMI plus another power cord. Because I don't have TYPE-C port which supports video output and I don't have the mini HDMI to HDMI connector, I have to use a mini HDMI to HDMI cable and another power cord. But mini HDMI to HDMI cable I bought both have poor quality and poor contact, I test by using the portable screen almost impossibly. I change the angle of either mini HDMI or HDMI, this screen only lights up once. At the other time, the screen shows "No Signal" and the MacOS shows there is just one monitor.

### Facetime and iMessage

Work badly in my macOS.

I don't have an iphone and I can't use the two functions since I begin to use Hackintosh, and I don't know it caused by my apple account or the config that the two functions are disabled.

