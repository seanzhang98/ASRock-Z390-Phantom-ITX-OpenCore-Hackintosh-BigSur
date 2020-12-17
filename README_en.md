
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/intro.png)

<p align="center">
     <a href="https://github.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur/releases">
      <img alt="GitHub release" src="https://img.shields.io/github/v/release/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur?label=EFI%20Ver." />
    </a>
    <a href="https://github.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur/releases">
      <img alt="GitHub Release Date" src="https://img.shields.io/github/release-date/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur" />    
      </a>
      <a href="https://github.com/seanzhang98">
      <img alt="Maintainer" src="https://img.shields.io/badge/Maintainer-%40seanzhang98-yellowgreen" />
    </a>
    </br>
    <a href="https://www.apple.com/macos/big-sur-preview/">
      <img alt="Supported OS" src="https://img.shields.io/badge/Supported OS-macOS%20Big%20Sur-blueviolet" />
      <a href="https://developer.apple.com/documentation/macos-release-notes">
      <img alt="OS version" src="https://img.shields.io/badge/Version-11.2 Beta (20D5029f)-ff69b4" />
      <a href="https://github.com/acidanthera/OpenCorePkg/releases/">
      <img alt="OC Ver" src="https://img.shields.io/badge/OpenCore Ver.-0.6.4%20(release)-191970" />
      </br>
    </p>
<p align="center">
    <a href="README.md"><font size=4><b>简体中文</b></font></a>
    <font size=4><b>·</b></font>
    <a href="README_en.md"><font size=4><b>English</b></font></a>
</p>

## Table of contents 
- <font size=4>[1. Warning](#warm)</font>
- <font size=4>[2. Component List](#config)</font>
- <font size=4>[3. Functionalities Checklist](#driver)</font>
- <font size=4>[4. Getting Ready](#ready)</font>
     - <font size=4>[4.1 Wi-Fi & Bluetooth module replacement](#wirecard)</font>
     - <font size=4>[4.2. Flashing Special BIOS to enable TB 3](#tb3)</font>
     - <font size=4>[4.3. BIOS Setting](#bios)</font>
     - <font size=4>[4.4. SMBIOS](#smbios)</font>
     - <font size=4>[4.5. Clean up emulated NVRAM（Optional）](#nvram)</font>
- <font size=4>[5. More](#more)</font>
- <font size=4>[6. Known Issues](#iss)</font>
- <font size=4>[7. Change Logs](#logs)</font>
- <font size=4>[8. Benchmark](#bench)</font>
- <font size=4>[9. References](#ref)</font>
- <font size=4>[10. Special Thanks](#thanks)</font>
</br>

## <span id="warm">1. Warning</span>
### ⚠️Warning A⚠️： Before using the EFI, you should at least understand how do you install macOS and understand the file structure of OpenCore. 
### If you don't, I strongly recommend you to read the OpenCore Install Guide before using this EFI. 
### Directly using this EFI does not mean your system can boot normally, even though the configuration is identical, you would need these knowledge to solve problems in your case. 

#### **📖 [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)**

### ⚠️Warning B⚠️： This EFI is based on OpenCore, if you currently are using Clover, please read following document to avoid unpredictable error.

#### **📖 [Converting from Clover to OpenCore Guide](https://github.com/dortania/OpenCore-Install-Guide/tree/master/clover-conversion)**

### ⚠️Warning C⚠️：This EFI does not contain any platform information (SN, UUID etc.). You can generate these information by using OpenCore Configurator.
#### **📖 [OpenCore Configurator official site](https://mackie100projects.altervista.org)**

### ⚠️Warning D⚠️：This project contains two EFI (iMac19,1 for configuration with iGPU and Mac Pro7,1 for configuration without iGPU) .
</br>

## <span id="config">2. Component List</span></span></span></span></span>

| Parts | Model                                           | Notes                |
|:------:|:----------------------------------------------:|:-------------------:|
| Motherboard   | ASRock Z390 phantom gaming-itx/ac            |                   |
| CPU  | Intel 9th Gen i9-9900k                           | Set the frequency of all core to 4.5Ghz, full load temperature is around 90 degrees. |
| Wireless Network Card |  BCM94360CS2                                            | NGFF to M.2 adapter required |
| Cooler  | Thermalright AXP90                         |  Noctua A9x14 Fan    |
| RAM   | TEAM DDR4 3200Mhz PC4-25600 32GBx2（64GBkit） | Elite Plus Series     |
| Case  |  Loli 1s mini itx                                    | You can get this case from [ChinaHao.com](https://www.chinahao.com/Product/546595980226/spot_speed__mini-itx_unique_mini_chassis_loli1_chassis_a4_chassis_secondk39_chassis)                  |
| Power Source  | Enhance 7660b                                             |    600W 1U Power     |
| GPU   | Powercolor RX5700 8G [AXRX 5700 ITX 8GBD6-2DH]                          | PowerColor Only for Japan market, you can get it from [Amazon.co.jp](https://www.amazon.co.jp/RX5700搭載ショート基板ITXグラフィックボード-AXRX-5700-ITX-8GBD6-2DH/dp/B082W236T1/ref=sr_1_1?__mk_ja_JP=カタカナ&dchild=1&keywords=5700+itx&qid=1604464670&sr=8-1) |
| Main M.2 Cooler | Noctua A4x10 Fan x 2 | Required to remove the offical M.2 armor |
</br>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/neofetch.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about_eng.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about_macpro_en.png)
</br>

## <span id="driver">3. Functionalities Checklist</span>

| Function Name        | Normal or not     | Notes                                                                                                                                                                                                                                    |
|:--------------------:|:-----------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| CPU                  | ⭕️                 | CPU frequency scaling is working                                                                                                                                                                                                         |
| GPU                  | ⭕️                 |                                                                                                                                                                                                                                          |
| Sound card           | ⭕️                 | The green audio port on the rear of motherboard is the “internal speaker”, support adjust in volume by pressing the function shortcuts in MacOS                                                                                          |
| LAN port             | ⭕️                 |                                                                                                                                                                                                                                          |
| Wi-Fi                | ⭕️                 |                                                                                                                                                                                                                                          |
| Bluetooth            | ⭕️                 |                                                                                                                                                                                                                                          |
| Hand-off             | ⭕️                 |                                                                                                                                                                                                                                          |
| Unlock with Apple Watch            | ⭕️                 |                                                                                                                                                                                                                                          |
| Sidecar              | ⭕️｜❌                  | iMac19,1 supports Sidecar,Mac Pro7,1 will not be supported since the REAL Mac have T2 chip（iPad black screen）                                                                                                                                                                                       |
| Sleep and wake       | ⭕️                 |                                                                                                                                                                                                                                          |
| Location Service     | ⭕️                 |                                                                                                                                                                                                                                          |
| NVRAM                | ⭕️                 |                                                                                                                                                                                                                                          |
| USB                  | ⭕️                 |                                                                                                                                                                                                                                          |
| Thunderbolt 3        | ⭕️                 | [Thunderbolt 3](#tb3)                                                                                                                                                                                                                    |
| DRM                  | ⭕️｜❌  | The DRM required by Apple TV + with iMac19,1 under Big Sur is broken for now, Mac Pro7,1 is fully support ALL DRM. [For more info](#drm)|
| Hardware acceleration | ⭕️                 | Support H264 and HEVC                                                                                                                                                                                                                    |
| RAM | ⭕️   |  Mac Pro7,1 without error                                                                                                                                          |
</br>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sidecar_eng.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/boot_eng.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/thunderbolts_eng.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/usb.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/ha_eng.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/ram_en.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/itpg.png)

## <span id="ready">4. Getting Ready</span>
### <span id="wirecard">4.1. Wi-Fi & Bluetooth module replacement
The motherboard comes with Intel® Wireless-AC 9560 module, support 802.11ac and Bluetooth 5.0 with 2x2 802.11ac 2.4/5Ghz Wi-Fi. We need to remove this module and replace it with BCM94360CS2 module,BCM94360CS2 module required an NGFF to M.2 adapter. Steps shown below（By icyleaf）：

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/install-boardcom-module-to-motherboard.png)

In Windows 10 you might need to install drivers manually in order to use Wi-Fi and Bluetooth.
</br>
</br>

### <span id="tb3">4.2. Flashing Special BIOS to enable TB 3</span>
Download [Z39PGIX4.40C](bios/Z39PGIX4.40C), store in a thumb drive and flash the BIOS by executing Instant Flash.
Steps of how to flash BIOS can be found on Asrock Official site 📖[ASRock BIOS Upgrade Instruction](http://www.asrock.com/support/BIOSIG.asp?cat=BIOS9).

This is for enabling Thunderbolt 3 on MacOS.（Do I have to flash this BIOS? I tried and no good with TB 3 while using BIOS 4.40😂.）
If you do not use Thunderbolt 3 port, you can skip this step. You can flash back to 4.40 anytime you want.
```diff
- ⚠️Warning：There are risks while flashing BIOS, 
- ⚠️This instruction dose not responsible for any hardware damage.
```
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/bios_eng.BMP)
</br>
</br>

You also need to check your ```rp21```'s ```reg``` value to choose the proper SSDT file by using IORegistryExplorer.

Download IORegistryExplorer , search for ```rp21``` and check the value under ```reg```.

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/reg.png)

If it includes ```dc```, you don't need to do anything. However if it includes ```d8``` then you need to download the ```SSDT-TbtOnPch_PINI_D8.aml``` file under ```Tools```, then put it under ```OC``` -> ```ACPI``` and remove ```SSDT-TbtOnPch_PINI.aml```. You need to made modification to your config file as well.
</br>
</br>

### <span id="bios">4.3. BIOS Setting (4.40c)</span>

#### - With iGPU
- **Advanced**
    - **Chipset Configuration** 
        - Vt-d → Disable
        - Share Memory → 128MB
        - IGPU Multi-Monitor → Enable

    - **Super IO Configuration** 
        - Serial Port → Disable

    - **USB Configuration** 
        - XHCI Hand-off → Enable

    - **Intel (R) Thunderbolt**
        - Thunderbolt (TM) Support → Enable
        - Thunderbolt Usb Support → Enable
        - GPIO3 Force Pwr → Enable

#### - Without iGPU
- **Advanced**
    - **Chipset Configuration** 
        - Vt-d → Disable
        - IGPU Multi-Monitor → Disable

    - **Super IO Configuration** 
        - Serial Port → Disable

    - **USB Configuration** 
        - XHCI Hand-off → Enable

    - **Intel (R) Thunderbolt**
        - Thunderbolt (TM) Support → Enable
        - Thunderbolt Usb Support → Enable
        - GPIO3 Force Pwr → Enable
</br>
</br>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/tbset_eng.BMP)
</br>
</br>

### <span id="smbios">4.4. SMBIOS <span>

- **Step 1：**
    - Use the latest OpenCore Configuratortor open ```config.plist```.
</br>

- **Step 2：**
    - Choose ```PlatformInfo``` then choose on the top ```DataHub - Generic — PlatfromNVRAM```, click the "up and down arrow" button on the right side on the ```Check Coverage``` button located at the bottom of the interface.

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/occ_smbios.png)
</br>

- **Step 3：**
    - Choose model ```iMac19,1``` if your CPU comes with iGPU, otherwise choose ```Mac Pro7,1```.
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/model.png)

### <span id="nvram">4.5. Clean up emulated NVRAM（Optional）<span>
If you used emulated NVRAM before, you need to clean up the emulated NVRAM to get the native NVRAM works. If you never used emulated NVRAM or you are doing a fresh install, you can skip this part.
#### 4.5.1. Clean up LogoutHook
- **Step 1：**

    Execute in terminal
    ```diff
    sudo defaults read com.apple.loginwindow LogoutHook
    ```
    If the output is
    ```diff
    The domain/default pair of (com.apple.loginwindow, LogoutHook) does     not exist
    ```
    Means no LogoutHook left.
</br>

- **Step 2：** 

    Remove ```LogoutHook.command``` file,execute in terminal
    ```diff
    sudo rm -rf $(sudo defaults read com.apple.loginwindow LogoutHook)
    ```
</br>

- **Step 3：** 

    Clean up ```LogoutHook``` trigger setting, execute in terminal
    ```diff
    sudo defaults delete com.apple.loginwindow LogoutHook
    ```
</br>

#### 4.5.2. Remove Files（If there are any）
- ```nvram.plist``` in ```EFI```  prartition.
- ```VariableRuntimeDxe.efi``` and ```EmuVariableRuntimeDxe.efi``` in ```/EFI/OC/Drivers```
</br>

#### 4.5.3. Examination NVRAM function
- Execute in terminal each line at a time,
    ```diff
    sudo -s
    ```
    ```diff
    sudo nvram -c 
    ```
    ```diff
    sudo nvram myvar=test
    ```
    ```diff
    exit
    ```
</br>

- Reboot your device, then execute in terminal
    ```diff
    vram -p | grep -i myvar
    ```
</br>

- If ```myvar test``` is included in your return line, then the NVRAM is working properly.
</br>
</br>

## <span id="more">5. More</span>
### <span id="nvram">5.1. Big Sur Style Icons<span>

There are many applications are not optimized for Big Sur with the new icon style, we can replace these icons for a unify UI. Image below is how the lunchpad looks like in my case ：

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/lunchpad.png)

You can download these icons form [macosicons](https://macosicons.com). 
I personally also make some of the icons and uploaded them to this website (this is an open-sourced project). If you are capable to make icons for the application you are using, please feel free to make contribution to this project.
</br>
</br>

## <span id="iss">6. Known Issues</span>

* **The enable of the patch change _E2C to XE2C will cause APIC Error while booting Windows with OC**
  
  Solution: disable the TB3 Function or boot Windows with BIOS interface.
</br>
  
* **<span id="drm">My device dose not support Sidecar / Apple TV + ?</span>**
  
  Solution: iMac19,1 can support Sidecar perfectly but Big Sur made some changes, which breaks the DRM required by Apple TV +. Wait for the WEG update to fix this. Mac Pro7,1 can support ALL DRM. However, the real Mac required Apple T2 chip to support Sidecar.
  
  
| System definition              | iMacPro1,1                                                              | iMac19,1                        |
|:------------------------------:|:-----------------------------------------------------------------------:|:-------------------------------:|
| iGPU (and QuickSync)           | Cannot be configured because these originally ship with Xeon processors | Compatible                      |
| Sidecar                        | not possible without iGPU                                               | Compatible with (headless) iGPU |
| DRM support in Safari          | Yes, OOB                                                                | No                              |
| DRM support in Apple TV/iTunes | Yes, OOB                                                                | No for now, Big Sur breaks the DRM support provided by WEG                |
| Performance                    | Better with GPU                                                         | Better with iGPU                |
| Vega/Polaris Support           | Compatible (through WEG)                                                | Compatible (OOB)                |
| Coffeelake Power Management    | Yes, through Extensions                                                 | Yes, OOB                        |
| CPU frequency scaling          | Yes, through CPUFriend and iMac19,1 board.plist                         | Yes, OOB                        |
</br>

* **Time do not sync between Windows 10 and macOS.** 

  - Solution：In Windows 10, run following code in CMD </br>
```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```
</br>

## <span id="logs">7. Change Logs</span>

- <font size=6><b>[Click to View Change Logs](CHANGELOG.md)</b></font>
</br>

## <span id="bench">8. Benchmark</span>
### CPU:

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_benchmark.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_cine.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/r23.png)

### GPU:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_open.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_metal.png)

### Cinebench R15 CPU & GPU
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/GPU_CPU_CINER15.png)

## <span id="ref">9. References</span>
📖 [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)

📖 [精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)

📖 [macOS Catalina 10.15安装中常见的问题及解决方法](https://blog.daliansky.net/Common-problems-and-solutions-in-macOS-Catalina-10.15-installation.html)

📖 [使用HIDPI解决睡眠唤醒黑屏、花屏及连接外部显示器的正确姿势](https://blog.daliansky.net/Use-HIDPI-to-solve-sleep-wake-up-black-screen,-Huaping-and-connect-the-external-monitor-the-correct-posture.html)

📖 [OpenCore部件补丁](https://github.com/daliansky/OC-little)

📖 [华擎ASRock Z390 Phantom Gaming ITX/ac 雷电3 完美驱动 热插拔](http://blog.fangf.cc/2020/05/19/TB3/)

📖 [OpenCore（OC）引导模拟NVRAM](https://imacos.top/2020/04/18/nvram/)

📖 [Sidecar and SMBIOS : iMac19,1 vs. iMacPro1,1](https://www.reddit.com/r/hackintosh/comments/dwbncg/sidecar_and_smbios_imac191_vs_imacpro11/)
</br>
</br>

## <span id="thanks">10. Special Thanks</span>
**[acidanthera](https://github.com/acidanthera/OpenCorePkg)**

**[daliansky](https://github.com/daliansky)（黑果小兵）**

**[RehabMan](https://bitbucket.org/RehabMan/)**

**[icyleaf](https://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)**

**[ZeRo° Xu](https://github.com/xzhih)（冰水加劲Q）**

**[fangf2018](https://github.com/fangf2018/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh)**

**[Bat.bat](https://github.com/williambj1)**

**[lovestfhd](https://github.com/lovestfhd)**
</br>
</br>

## 11. Traffic statistics
<p align="left">
<a href="http://antzuhl.cn:4000/get/@
ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur.readme_en">
      <img alt="" src="http://antzuhl.cn:4000/get/@ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur.readme_en" />
</p>