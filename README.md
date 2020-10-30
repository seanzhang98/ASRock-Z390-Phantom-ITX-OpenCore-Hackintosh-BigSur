# ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh

### [English Documentation](README_en.md)

## 硬件配置

| 部件名称 | 型号                                           | 备注                |
|:------:|:----------------------------------------------:|:-------------------:|
| 主板   | ASRock Z390 phantom gaming-itx/ac            |                   |
| CPU  | Intel 第九代 i9-9900k                           | 设置主频至4.5Ghz，满载温度稳定在90度左右 |
| 无线网卡 |  BCM94360CS                                            | 需要 NGFF M.2 转接卡 |
| 散热器  | 利民 AXP90                         |  猫头鹰 A9x14 风扇    |
| 内存   | TEAM DDR4 3200Mhz PC4-25600 32GBx2枚（64GBkit） | Elite Plus 系列     |
| 机箱   |  Loli 1s mini itx 机箱                                    |                   |
| 电源   | 益恒 7660b                                             |    600W 1U 电源     |
| 显卡   | Powercolor RX5700 8G [AXRX 5700 ITX 8GBD6-2DH]                          | PowerColor 日本市场特供 |
| 主 M.2 散热 | 猫头鹰 A4x10 风扇x2 | 移除原装散热马甲 |


![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/case01.jpeg)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/case02.jpeg)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about.png)

## 性能跑分
### Geekbench 5 CPU:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_benchmark.png)

### Cinebench R20：
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_cine.png)

### Geekbench 5 GPU OpenGL:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_open.png)

### Geekbench 5 GPU Metal:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_metal.png)
## 网卡替换
该主板自带的为 Intel® Wireless-AC 9560 模块，支持无线 802.11ac 方案并提供蓝牙 5.0 和 2x2 802.11ac 2.4/5Ghz Wi-Fi。需要拆下该模块并替换为白果拆机模块BCM94360CS，该模块需要 BCM94360CS2 NGFF M.2 转接卡。操作步骤如图（icyleaf大佬的图）：

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/install-boardcom-module-to-motherboard.jpg)

## 驱动情况

* 系统稳定性：在 macOS 11.0 Beta9(20A5384c) 中没有系统崩溃。

* 显卡：RX5700 驱动正常~~, 使用补丁伪装成 Radeon Pro W5700X 8 GB 以获得更好的性能~~。  

* 声卡：正常。

* WiFi: 正常。

* 蓝牙: 正常。

* Handoff: 正常。

* 随航: 正常。

* 睡眠和唤醒：正常。

* 定位服务：正常。

* nvram：正常。

* USB：正常。

* 雷霹 3 ：支持热插拔, USB 功能正常 (本人没有 TB3 设备无法测试具体速度和功能，理论上应该能正常工作)。

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sidecar.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/thunderbolts.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/usb.png)
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/boot.png)

## 传感器支持
本 EFI 支持在 Big Sur 中显示主板相关传感器, RX5700 的 GPU 核心温度也能正常显示。

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sensors.png)

## 雷霹3驱动
本教程参考了房大叔的教程，刷了华擎的4.40c BIOS。
具体参考：[华擎ASRock Z390 Phantom Gaming ITX/ac 雷电3 完美驱动 热插拔](http://blog.fangf.cc/2020/05/19/TB3/)
## BIOS 设定

Advanced \ Chipset Configuration → Vt-d : Disabled

Advanced \ Super IO Configuration → Serial Port: Disabled

Advanced \ USB Configuration → XHCI Hand-off : Enabled

Advanced \ Chipset Configuration → Share Memory : 128MB

Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt (TM) Support : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt Usb Support : Enabled

Advanced \ Intel (R) Thunderbolt → GPIO3 Force Pwr : Enable

## 已知问题

* 补丁 change _E2C to XE2C 会导致使用 OC 引导 Windows 系统时报 APIC 错误。
  
  解决方案: 禁用该补丁或者用 bios 来引导 Windows。
  
* 引导默认的 "iMac (2019, 5K)" 型号因为 DRM 问题不支持 Apple TV + 播放。 但是 Apple Music (已测试), Amazon Prime (已测试) 和 Netflix 在 Chrome 中可以正常播放 (Safari 不支持播放).
  
  解决方案: 将型号改为 iMac Pro， 但是，随航功能将无法使用。
  
* 部分电脑关机后开机可能会提示 “电脑关机是因为发生了问题”。

  解决方案：清除 CMOS 和 nvram，并运行 "sudo nvram -d aapl,panic-info" 清除kernel panic 文件。

## 更新日志

0.6.3.1: 修复部分问题

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

**[icyleaf](https://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)**

**[ZeRo° Xu](https://github.com/xzhih)(冰水加劲Q)**

**[acidanthera](https://github.com/acidanthera/OpenCorePkg)**

**[fangf2018](https://github.com/fangf2018/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh)**

**[Bat.bat](https://github.com/williambj1)**
