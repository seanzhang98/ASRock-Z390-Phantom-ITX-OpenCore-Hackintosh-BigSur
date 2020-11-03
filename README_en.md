# ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur

### [中文版文档](README.md)

## Warning A⚠️： I strongly recommend you to read the OpenCore Install Guide before using this EFI, directly using this EFI does not mean your system can boot normally, even though the configuration is identical. 

### **📖 [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)**

## Warning B⚠️： This EFI is based on OpenCore, if you currently are using Clover, please read following document to avoid unpredictable error.

### **📖 [Converting from Clover to OpenCore Guide](https://github.com/dortania/OpenCore-Install-Guide/tree/master/clover-conversion)**

## Warning C⚠️：This EFI does not contain any platform information (SN, UUID etc.). You can generate these information by using OpenCore Configurator.
### **📖 [OpenCore Configurator official site](https://mackie100projects.altervista.org)**

## Configuration

| Parts | Model                                           | Notes                |
|:------:|:----------------------------------------------:|:-------------------:|
| Motherboard   | ASRock Z390 phantom gaming-itx/ac            |                   |
| CPU  | Intel 9th Gen i9-9900k                           | Set the frequency of all core to 4.5Ghz, full load temperature is around 90 degrees. |
| Wireless Network Card |  BCM94360CS2                                            | NGFF to M.2 adapter required |
| Cooler  | Thermalright AXP90                         |  Noctua A9x14 Fan    |
| RAM   | TEAM DDR4 3200Mhz PC4-25600 32GBx2（64GBkit） | Elite Plus Series     |
| Case  |  Loli 1s mini itx                                    |                   |
| Power Source  | Enhance 7660b                                             |    600W 1U Power     |
| GPU   | Powercolor RX5700 8G [AXRX 5700 ITX 8GBD6-2DH]                          | PowerColor Only for Japan market |
| Main M.2 Cooler | Noctua A4x10 Fan x 2 | Required to remove the offical M.2 armor |
<br/>
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about_eng.png)

## Functionalities checklist

| Function Name     | Normal or not | Notes  |
|:--------:|:----:|:---:|
| CPU      | ☑️   | Able to adjust frequency based on different tasks|
| GPU       | ☑️   | |
| Sound card       | ☑️   |The green audio port on the rear of motherboard is the “internal speaker”, support adjust in volume by pressing the function shortcuts in MacOS|
| LAN port     | ☑️   |     |
| Wi-Fi    | ☑️   |     |
| Bluetooth       | ☑️   |     |
| Hand-off       | ☑️   |     |
| SideCar       | ☑️   |This EFI using model  “iMac 19,1” supports SideCar|
| Sleep and wake    | ☑️   |     |
| Location Service     | ☑️   |     |
| NVRAM | ☑️   |     |
| USB      | ☑️   |     |
| Thunderbolt 3     | ☑️   |[Thunderbolt 3](#tb3)|
| DRM      | Partially working   |This EFI using the model “iMac 19,1”, with DRM support while using Chrome to play video on Amazon Prime and Netflix. However, Apple TV + is not supported[*](#drm)<br/>You can play music in “Music.app” with Apple Muisc. |
<br/>
* <font size=4>Above was tested on macOS 11.0.1 Beta 11 (20B5012d) with no crashes.</font>

<br/>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sidecar_eng.png)<br/>
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/thunderbolts_eng.png)<br/>
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/usb.png)<br/>
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/boot_eng.png)


## Benchmark
### Geekbench 5 CPU:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_benchmark.png)

### Cinebench R20:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_cine.png)

### Geekbench 5 GPU OpenGL:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_open.png)

### Geekbench 5 GPU Metal:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_metal.png)

## Wi-Fi & Bluetooth module replacement
The motherboard comes with Intel® Wireless-AC 9560 module, support 802.11ac and Bluetooth 5.0 with 2x2 802.11ac 2.4/5Ghz Wi-Fi. We need to remove this module and replace it with BCM94360CS2 module，BCM94360CS2 module required an NGFF to M.2 adapter. Steps shown below（By icyleaf）：

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/install-boardcom-module-to-motherboard.jpg)

In Windows 10 you might need to install drivers manually in order to use Wi-Fi and Bluetooth.


## <span id="tb3">Thunderbolt 3</span>
This configuration was flashed Asrock special BIOS 4.40c to support TB3 function.
Tutorial By fangf2018 (Chinese Only)：📖 [华擎ASRock Z390 Phantom Gaming ITX/ac 雷电3 完美驱动 热插拔](http://blog.fangf.cc/2020/05/19/TB3/)

## BIOS Setting (4.40c)

Advanced \ Chipset Configuration → Vt-d : Disabled

Advanced \ Chipset Configuration → Share Memory : 128MB

Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

Advanced \ Super IO Configuration → Serial Port: Disabled

Advanced \ USB Configuration → XHCI Hand-off : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt (TM) Support : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt Usb Support : Enabled

Advanced \ Intel (R) Thunderbolt → GPIO3 Force Pwr : Enable

## Known Issues

* **The enable of the patch change _E2C to XE2C will cause APIC Error while booting Windows with OC**
  
  Solution: disable the TB3 Function or boot Windows with BIOS interface.
  
* **<span id="drm">The current model of "iMac (2019, 5K)" is not support Apple TV + because of the DRM. But Apple Music (tested), Amazon Prime (tested) and Netflix should work by   using Chrome (not working with Safari).</span>**
  
  Solution: change the model into iMac Pro, however, you will lose the SideCar function.

## Update Logs

**0.6.3.2:** Re-builded the EFI, removed FakeSMC (tested in 11.0.1 Beta(20B5012d)).

**0.6.3.1:** Fix mirror errors.

**0.6.3:** Update Opencore to 0.6.3

**0.6.2:** First release


## References
📖 [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)

📖 [精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)

📖 [macOS Catalina 10.15安装中常见的问题及解决方法](https://blog.daliansky.net/Common-problems-and-solutions-in-macOS-Catalina-10.15-installation.html)

📖 [使用HIDPI解决睡眠唤醒黑屏、花屏及连接外部显示器的正确姿势](https://blog.daliansky.net/Use-HIDPI-to-solve-sleep-wake-up-black-screen,-Huaping-and-connect-the-external-monitor-the-correct-posture.html)

📖 [OpenCore部件补丁](https://github.com/daliansky/OC-little)

📖 [华擎ASRock Z390 Phantom Gaming ITX/ac 雷电3 完美驱动 热插拔](http://blog.fangf.cc/2020/05/19/TB3/)


## Special Thanks
**[daliansky](https://github.com/daliansky)（黑果小兵）**

**[RehabMan](https://bitbucket.org/RehabMan/)**

**[icyleaf](https://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)**

**[ZeRo° Xu](https://github.com/xzhih)(冰水加劲Q)**

**[acidanthera](https://github.com/acidanthera/OpenCorePkg)**

**[fangf2018](https://github.com/fangf2018/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh)**

**[Bat.bat](https://github.com/williambj1)**
