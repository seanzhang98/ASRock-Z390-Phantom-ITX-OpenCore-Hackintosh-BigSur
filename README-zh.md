# ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh

### [English Documentation](README.md)

## 硬件配置

主板：ASRock Z390 phantom gaming-itx/ac

CPU：Intel 9th Gen i9-9900k

显卡： AMD RX5700 itx 8GB
 
内存: Team Group 32GBx2 (共64GB)

无线网卡：BCM943602CS

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about.png)


## 驱动情况

* 系统稳定性：在 macOS 11.0 Beta9(20A5384c) 中没有系统崩溃。

* 显卡：RX5700 驱动正常, 使用补丁伪装成 Radeon Pro W5700X 8 GB 以获得更好的性能。  

* 声卡：正常。

* WiFi: 正常。

* 蓝牙: 正常。

* Handoff: 正常。

* 随航: 正常。

* 睡眠和唤醒：正常。

* 定位服务：正常。

* nvram：正常。

* USB：正常。

* 雷劈3 ：支持热插拔, USB 功能正常 (本人没有 TB3 设备无法测试具体速度和功能，理论上应该能正常工作)。
 
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sidecar.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/thunderbolts.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/usb.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/boot.png)

## BIOS 设定

Advanced \ Chipset Configuration → Vt-d : Disabled

Advanced \ Super IO Configuration → Serial Port: Disabled

Advanced \ USB Configuration → XHCI Hand-off : Enabled

Advanced \ Chipset Configuration → Share Memory : 128MB

Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

## 已知问题
* 本人在升级 Beta 10 遇见暂时无法解决的 Bug，暂时退回 B9 等待下一个 Beta 版本。

* 补丁 change _E2C to XE2C 会导致使用 OC 引导 Windows 系统时报 APIC 错误。
  
  解决方案: 禁用该补丁或者用 bios 来引导 Windows。
  
* 引导默认的 "iMac (2019, 5K)" 型号因为 DRM 问题不支持 Apple TV + 播放。 但是 Apple Music (已测试), Amazon Prime (已测试) 和 Netflix 在 Chrome 中可以正常播放 (Safari 不支持播放).
  
  解决方案: 将型号改为 iMac Pro， 但是，随航功能将无法使用。

## 更新日志

0.6.3: 更新 OC 版本

0.6.2: First release


## 参考
[精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)

[macOS Catalina 10.15安装中常见的问题及解决方法](https://blog.daliansky.net/Common-problems-and-solutions-in-macOS-Catalina-10.15-installation.html)

[使用HIDPI解决睡眠唤醒黑屏、花屏及连接外部显示器的正确姿势](https://blog.daliansky.net/Use-HIDPI-to-solve-sleep-wake-up-black-screen,-Huaping-and-connect-the-external-monitor-the-correct-posture.html)

[OpenCore部件补丁](https://github.com/daliansky/OC-little)


## 特别感谢
**[daliansky](https://github.com/daliansky)（黑果小兵）**

**[RehabMan](https://bitbucket.org/RehabMan/)**

**[ZeRo° Xu](https://github.com/xzhih)(冰水加劲Q)**

**[acidanthera](https://github.com/acidanthera/OpenCorePkg)**

**[fangf2018](https://github.com/fangf2018/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh)**

**[Bat.bat](https://github.com/williambj1)**
