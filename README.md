# ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur

### [Switch to English Version](README_en.md)

## 目录
- <font size=4>[注意事项](#warm)</font>
- <font size=4>[硬件配置](#config)</font>
- <font size=4>[驱动情况](#driver)</font>
- <font size=4>[网卡替换](#wirecard)</font>
- <font size=4>[雷霹 3 驱动](#tb3)</font>
- <font size=4>[BIOS 设定](#bios)</font>
- <font size=4>[已知问题](#iss)</font>
- <font size=4>[更新日志](#logs)</font>
- <font size=4>[性能跑分](#bench)</font>
- <font size=4>[参考](#ref)</font>
- <font size=4>[特别感谢](#thanks)</font>

## <span id="warm">注意事项</span>
## 注意一⚠️：建议在使用本 EFI 之前完整阅读 OC 官方配置指南，使用本 EFI 并不意味着你的系统也能正常启动，即使配置完全相同。 

### **📖 [OpenCore 官方指南（英文版）](https://dortania.github.io/OpenCore-Install-Guide)**

### **📖 [OpenCore 配置项非官方中文翻译](https://oc.skk.moe)**

## 注意二⚠️：本配置是 OpenCore 引导，如果你现在正在使用 Clover 引导，请参考以下文档以免出现错误。

### **📖 [Clover 转 OpenCore 指南（英文版）](https://github.com/dortania/OpenCore-Install-Guide/tree/master/clover-conversion)**

## 注意三⚠️：请生成你自己的三码，本 EFI 不包含任何三码信息。你可以用使用 OpenCore Configurator 来生成相关数据。

### **📖 [OpenCore Configurator 官网（英文版）](https://mackie100projects.altervista.org)**

## <span id="config">硬件配置</span>

| 部件名称 | 型号                                           | 备注                |
|:------:|:----------------------------------------------:|:-------------------:|
| 主板   | ASRock Z390 phantom gaming-itx/ac            |                   |
| CPU  | Intel 第九代 i9-9900k                           | 设置主频至4.5Ghz，满载温度稳定在90度左右 |
| 无线网卡 |  BCM94360CS2                                            | 需要 NGFF M.2 转接卡 |
| 散热器  | 利民 AXP90                         |  猫头鹰 A9x14 风扇    |
| 内存   | TEAM DDR4 3200Mhz PC4-25600 32GBx2枚（64GBkit） | Elite Plus 系列     |
| 机箱   |  Loli 1s mini itx 机箱                                    |                   |
| 电源   | 益恒 7660b                                             |    600W 1U 电源     |
| 显卡   | Powercolor RX5700 8G [AXRX 5700 ITX 8GBD6-2DH]                          | PowerColor 日本市场特供 |
| 主 M.2 散热 | 猫头鹰 A4x10 风扇x2 | 移除原装散热马甲 |
<br/>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about.png)

## <span id="driver">驱动情况</span>

| 功能名称     | 是否正常 | 备注  |
|:--------:|:----:|:---:|
| CPU      | ☑️   | 支持变频|
| 显卡       | ☑️   |能够正确识别并且性能正常|
| 声卡       | ☑️   |主板绿色接口为 “内置扬声器” ，支持原生功能键调节音量|
| 有线网卡     | ☑️   |     |
| Wi-Fi    | ☑️   |     |
| 蓝牙       | ☑️   |     |
| 接力       | ☑️   |     |
| 随航       | ☑️   |本 EFI 默认机型 “iMac 19,1” 支持随航|
| 睡眠与唤醒    | ☑️   |     |
| 定位服务     | ☑️   |     |
| 原生 NVRAM | ☑️   |     |
| USB      | ☑️   |     |
| 雷霹 3     | ☑️   |[雷霹 3 驱动教程](#tb3)|
| DRM      | 部分正常   |本 EFI 默认机型 “iMac 19,1” 只支持 Chrome 中 Amazon Prime 和 Netflix 的 DRM，Apple TV + 无法正常播放[*](#drm)<br/>“音乐.app”中，Apple Muisc 可以正常播放音乐|
<br/>
* <font size=4>以上内容在 macOS 11.0.1 Beta 11 (20B5012d) 中测试没有系统崩溃。</font>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sidecar.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/thunderbolts.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/usb.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/boot.png)


## <span id="wirecard">网卡替换</span>
该主板自带的为 Intel® Wireless-AC 9560 模块，支持无线 802.11ac 方案并提供蓝牙 5.0 和 2x2 802.11ac 2.4/5Ghz Wi-Fi。需要拆下该模块并替换为白果拆机模块BCM94360CS2，该模块需要 BCM94360CS2 NGFF M.2 转接卡。操作步骤如图（icyleaf大佬的图）：

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/install-boardcom-module-to-motherboard.jpg)

Windows 下可能需要手动安装驱动才能使用 Wi-Fi 和 蓝牙功能。

## <span id="tb3">雷霹 3 驱动</span>
本教程参考了房大叔的教程，刷了华擎的4.40c BIOS。
具体参考：[华擎ASRock Z390 Phantom Gaming ITX/ac 雷电3 完美驱动 热插拔](http://blog.fangf.cc/2020/05/19/TB3/)

## <span id="bios">BIOS 设定 (4.40c)<span>

Advanced \ Chipset Configuration → Vt-d : Disabled

Advanced \ Chipset Configuration → Share Memory : 128MB

Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

Advanced \ Super IO Configuration → Serial Port: Disabled

Advanced \ USB Configuration → XHCI Hand-off : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt (TM) Support : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt Usb Support : Enabled

Advanced \ Intel (R) Thunderbolt → GPIO3 Force Pwr : Enable

## <span id="iss">已知问题<span>

* **补丁 change _E2C to XE2C 会导致使用 OC 引导 Windows 系统时报 APIC 错误。**
  
  解决方案: 禁用该补丁或者用 bios 来引导 Windows。
  
* <span id="drm">**引导默认的 "iMac (2019, 5K)" 型号因为 DRM 问题不支持 Apple TV + 播放。 但是 Apple Music (已测试), Amazon Prime (已测试) 和 Netflix 在 Chrome 中可以正常播放 (Safari 不支持播放).**</span>
  
  解决方案: 将型号改为 iMac Pro， 但是，随航功能将无法使用。
  
* **部分电脑关机后开机可能会提示 “电脑关机是因为发生了问题”。**

  解决方案： 清除 CMOS 和 nvram，并运行 "sudo nvram -d aapl,panic-info" 清除kernel panic 文件。

## <span id="logs">更新日志</span>

**0.6.3.2:** 重构 EFI，移除 FakeSMC。（已在 11.0.1 Beta版(20B5012d) 测试）

**0.6.3.1:** 修复部分问题

**0.6.3:** 更新 OC 版本

**0.6.2:** First release

## <span id="bench">性能跑分</span>
### Geekbench 5 CPU:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_benchmark.png)

### Cinebench R20：
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_cine.png)

### Geekbench 5 GPU OpenGL:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_open.png)

### Geekbench 5 GPU Metal:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_metal.png)




## <span id="ref">参考</span>
📖 [OpenCore 官方指南](https://dortania.github.io/OpenCore-Install-Guide)

📖 [精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)

📖 [macOS Catalina 10.15安装中常见的问题及解决方法](https://blog.daliansky.net/Common-problems-and-solutions-in-macOS-Catalina-10.15-installation.html)

📖 [使用HIDPI解决睡眠唤醒黑屏、花屏及连接外部显示器的正确姿势](https://blog.daliansky.net/Use-HIDPI-to-solve-sleep-wake-up-black-screen,-Huaping-and-connect-the-external-monitor-the-correct-posture.html)

📖 [OpenCore部件补丁](https://github.com/daliansky/OC-little)

📖 [华擎ASRock Z390 Phantom Gaming ITX/ac 雷电3 完美驱动 热插拔](http://blog.fangf.cc/2020/05/19/TB3/)



## <span id="thanks">特别感谢</span>
**[daliansky](https://github.com/daliansky)（黑果小兵）**

**[RehabMan](https://bitbucket.org/RehabMan/)**

**[icyleaf](https://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)**

**[ZeRo° Xu](https://github.com/xzhih)（冰水加劲Q）**

**[acidanthera](https://github.com/acidanthera/OpenCorePkg)**

**[fangf2018](https://github.com/fangf2018/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh)**

**[Bat.bat](https://github.com/williambj1)**
