# ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh

### [English](README.md) | [中文](README-zh.md)

## Configuration

Motherboard：ASRockz390 phantom gaming-itx/ac

CPU：Intel 9th Gen i9-9900k

Graphics： AMD RX5700 itx 8GB
 
RAM: Team Group 32GBx2 (64GB total)

Wireless network card：BCM943602CS

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about.png)


## Drive situation

* System stability：System has been tested in 11.0 Beta9(20A5384c) with no system crash.

* Graphics：RX5700 driver is normal, boosted with a patch to Radeon Pro W5700X 8 GB for better performance.  

* Sound card：Normal.

* WiFi: Working.

* Bluetooth: Working.

* Handoff: Working.

* Sidecar: Working.

* Sleep &wake：Working.

* Location service：Working.

* nvram：Working.

* USB：No abnormality.

* ThunderBolt 3 ：hot-plug supported, USB function is normal (I do not own a TB3 device to test the speed and functionality, but should be working).

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sidecar.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/thunderbolts.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/usb.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/boot.png)

## BIOS Setting

Advanced \ Chipset Configuration → Vt-d : Disabled

Advanced \ Super IO Configuration → Serial Port: Disabled

Advanced \ USB Configuration → XHCI Hand-off : Enabled

Advanced \ Chipset Configuration → Share Memory : 128MB

Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

## Known Issues
* The enable of the patch change _E2C to XE2C will cause APIC Error while booting Windows with OC
  
  Solution: disable the TB3 Function or boot Windows with BIOS interface.
  
* The current model of "iMac (2019, 5K)" is not support Apple TV + because of the DRM. But Apple Music (tested), Amazon Prime (tested) and Netflix should work by   using Chrome (not working with Safari).
  
  Solution: change the model into iMac Pro, however, you will lose the SideCar function.

## Update Logs

0.6.2: First release


## References
[精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)

[macOS Catalina 10.15安装中常见的问题及解决方法](https://blog.daliansky.net/Common-problems-and-solutions-in-macOS-Catalina-10.15-installation.html)

[使用HIDPI解决睡眠唤醒黑屏、花屏及连接外部显示器的正确姿势](https://blog.daliansky.net/Use-HIDPI-to-solve-sleep-wake-up-black-screen,-Huaping-and-connect-the-external-monitor-the-correct-posture.html)

[OpenCore部件补丁](https://github.com/daliansky/OC-little)


## Special Thanks
**[daliansky](https://github.com/daliansky)（黑果小兵）**

**[RehabMan](https://bitbucket.org/RehabMan/)**

**[ZeRo° Xu](https://github.com/xzhih)(冰水加劲Q)**

**[acidanthera](https://github.com/acidanthera/OpenCorePkg)**

**[fangf2018](https://github.com/fangf2018/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh)**

**[Bat.bat](https://github.com/williambj1)**
