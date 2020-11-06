
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/intro.png)

<p align="center">
     <a href="https://github.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur/releases">
     <img alt="GitHub release" src="https://img.shields.io/github/v/release/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur?label=EFI%20%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3" />
    </a>
    <a href="https://github.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur/releases">
      <img alt="GitHub Release Date" src="https://img.shields.io/github/release-date/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur" />
      </a>
    <a href="https://github.com/seanzhang98">
      <img alt="メンテナ" src="https://img.shields.io/badge/メンテナ-%40seanzhang98-yellowgreen" />
    </a>
    </br>
    <a href="https://www.apple.com/jp/macos/big-sur-preview/">
      <img alt="Supported OS" src="https://img.shields.io/badge/Supported OS-macOS%20Big%20Sur-blueviolet" />
      <a href="https://developer.apple.com/documentation/macos-release-notes">
      <img alt="OS version" src="https://img.shields.io/badge/Version-11.0.1 Beta (20B5022a)-ff69b4" />
      <a href="https://github.com/williambj1/OpenCore-Factory/releases">
      <img alt="OC Ver" src="https://img.shields.io/badge/OC%20%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3-0.6.4%20(2020--11--04)-191970" />
      </br>
    </p>
<p align="center">
    <a href="README.md"><font size=4><b>简体中文</b></font></a>
    <font size=4><b>·</b></font>
    <a href="README_en.md"><font size=4><b>English</b></font></a>
    <font size=4><b>·</b></font>
    <a href="README_ja.md"><font size=4><b>日本語</b></font></a>
</p>

## 目録 
- <font size=4>[1. 警告](#warm)</font>
- <font size=4>[2. コンポーネントリスト](#config)</font>
- <font size=4>[3. 機能チェックリスト](#driver)</font>
- <font size=4>[4. 準備](#ready)</font>
     - <font size=4>[4.1 Wi-FiとBluetoothモジュールの交換](#wirecard)</font>
     - <font size=4>[4.2. 特別版BIOSを更新する](#tb3)</font>
     - <font size=4>[4.3. BIOS設定](#bios)</font>
     - <font size=4>[4.4. エミュレートNVRAMをクリーンアップ（オプション）](#nvram)</font>
- <font size=4>[5. 既知の問題](#iss)</font>
- <font size=4>[6. 更新ログ](#logs)</font>
- <font size=4>[7. ベンチマーク](#bench)</font>
- <font size=4>[8. 参考文献](#ref)</font>
- <font size=4>[9. 感謝](#thanks)</font>

## <span id="warm">1. 警告</span>
### ⚠️警告１⚠️： このEFIを使用する前に、OpenCoreインストールガイドを読むことを強くお勧めします。このEFIを直接使用しても、構成が同じであっても、システムが正常に起動できるとは限りません。

#### **📖 [OpenCore Install Guide「英語」](https://dortania.github.io/OpenCore-Install-Guide)**

### ⚠️警告２⚠️： このEFIはOpenCoreに基づいています。現在Cloverを使用している場合は、予期しないエラーを回避するために次のドキュメントをお読みください。

#### **📖 [Converting from Clover to OpenCore Guide「英語」](https://github.com/dortania/OpenCore-Install-Guide/tree/master/clover-conversion)**

### ⚠️警告３⚠️：このEFIには、プラットフォーム情報（SN、UUIDなど）は含まれていません。 これらの情報は、OpenCoreConfiguratorを使用して生成できます。
#### **📖 [OpenCore Configurator official site「英語」](https://mackie100projects.altervista.org)**

## <span id="config">2. コンポーネントリスト</span></span></span></span></span>

| 部品 | モデル                                           | 注釈                |
|:------:|:----------------------------------------------:|:-------------------:|
| マザーボード   | ASRock Z390 phantom gaming-itx/ac            |                   |
| CPU  | Intel 9th Gen i9-9900k                           | Set the frequency of all core to 4.5Ghz, full load temperature is around 90 degrees. |
| ワイヤレスネットワークカード |  BCM94360CS2                                            | NGFF to M.2 adapter required |
| クーラー  | Thermalright AXP90                         |  Noctua A9x14 Fan    |
| RAM   | TEAM DDR4 3200Mhz PC4-25600 32GBx2（64GBkit） | Elite Plus Series     |
| ケース  |  Loli 1s mini itx                                    | You can get this case from [ChinaHao.com](https://www.chinahao.com/Product/546595980226/spot_speed__mini-itx_unique_mini_chassis_loli1_chassis_a4_chassis_secondk39_chassis)                  |
| 電源  | Enhance 7660b                                             |    600W 1U Power     |
| GPU   | Powercolor RX5700 8G [AXRX 5700 ITX 8GBD6-2DH]                          | PowerColor Only for Japan market, you can get it from [Amazon.co.jp](https://www.amazon.co.jp/RX5700搭載ショート基板ITXグラフィックボード-AXRX-5700-ITX-8GBD6-2DH/dp/B082W236T1/ref=sr_1_1?__mk_ja_JP=カタカナ&dchild=1&keywords=5700+itx&qid=1604464670&sr=8-1) |
| メインM.2クーラー | Noctua A4x10 Fan x 2 | Required to remove the offical M.2 armor |
<br/>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/about_ja.png)

## <span id="driver">3. 機能チェックリスト</span>

| 機能名        | 作業状況     | 注釈                                                                                                                                                                                                                                    |
|:--------------------:|:-----------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| CPU                  | ☑️                | CPU周波数スケーリングが働いています                                                                                                                                                                                                         |
| GPU                  | ☑️                |                                                                                                                                                                                                                                          |
| サウンドカード           | ☑️                | マザーボードの背面にある緑色のオーディオポートは、「内蔵スピーカー」で、サポートがMacOSの中で機能のショートカットを押すことで音量に調整します                                                                                          |
| LAN ポート             | ☑️                |                                                                                                                                                                                                                                          |
| Wi-Fi                | ☑️                |                                                                                                                                                                                                                                          |
| Bluetooth            | ☑️                |                                                                                                                                                                                                                                          |
| Hand-off             | ☑️                |                                                                                                                                                                                                                                          |
| サイドカー              | ☑️                | このEFI使用してモデル「のiMac 19,1は」サイドカーをサポートしています                                                                                                                                                                                        |
| Sleep and wake       | ☑️                |                                                                                                                                                                                                                                          |
| 位置情報サービス     | ☑️                |                                                                                                                                                                                                                                          |
| NVRAM                | ☑️                |                                                                                                                                                                                                                                          |
| USB                  | ☑️                |                                                                                                                                                                                                                                          |
| Thunderbolt 3        | ☑️                | [Thunderbolt 3](#tb3)                                                                                                                                                                                                                    |
| DRM                  | 部分的に機能している | このEFIは、モデル「iMac 19,1」を使用し、Chromeを使用してAmazonPrimeおよびNetflixでビデオを再生しながらDRMをサポートします。 ただし、Apple TV +はサポートされていません<br/> AppleMuiscを使用して「Music.app」で音楽を再生できます。 <br/> [不完全な解決策](#drm) |
| ハードウェアアクセラレーション | ☑️                | H264とHEVCをサポート                                                                                                                                                                                                                    |

<br/>

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/sidecar_ja.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/thunderbolts_ja.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/usb.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/boot_ja.png)

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/ha_ja.png)

## <span id="ready">4. 準備</span>
### <span id="wirecard">4.1. Wi-FiとBluetoothモジュールの交換
マザーボードにはIntel®Wireless-AC9560モジュールが付属しており、802.11acおよびBluetooth5.0と2x2802.11ac 2.4 / 5GhzWi-Fiをサポートしています。 このモジュールを取り外してBCM94360CS2モジュールと交換する必要があります。BCM94360CS2モジュールにはNGFF-M.2アダプターが必要でした。 以下に示す手順（By icyleaf）：

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/install-boardcom-module-to-motherboard.jpg)

Windows 10では、Wi-FiとBluetoothを使用するために、ドライバーを手動でインストールする必要がある場合があります。


### <span id="tb3">4.2. 特別版BIOSを更新する</span>
 [Z39PGIX4.40C](bios/Z39PGIX4.40C)をダウンロードする, サムドライブに保存し、インスタントフラッシュを実行してBIOSをフラッシュします。
 
BIOSをフラッシュする方法の手順は、のAsrock公式サイトに掲載されています 📖 [ASRock BIOS アップグレードについての説明](https://www.asrock.com/support/BIOSIG.jp.asp?cat=BIOS9).

これは、MacOSでThunderbolt 3を有効にするためのものです。
Thunderbolt 3ポートを使用しない場合は、この手順をスキップできます。 いつでも4.40にフラッシュバックできます。
```diff
- ⚠️警告：BIOSのフラッシュ中にリスクがあります。 
- ⚠️このガイドは、ハードウェアの損傷については責任を負いません。
```
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/bios_eng.BMP)
### <span id="bios">4.3. BIOS設定 (4.40c)</span>

Advanced \ Chipset Configuration → Vt-d : Disabled

Advanced \ Chipset Configuration → Share Memory : 128MB

Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

Advanced \ Super IO Configuration → Serial Port: Disabled

Advanced \ USB Configuration → XHCI Hand-off : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt (TM) Support : Enabled

Advanced \ Intel (R) Thunderbolt → Thunderbolt Usb Support : Enabled

Advanced \ Intel (R) Thunderbolt → GPIO3 Force Pwr : Enabled

![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/tbset_eng.BMP)

### <span id="nvram">4.4. エミュレートNVRAMをクリーンアップ（オプション）<span>
以前にエミュレートされたNVRAMを使用したことがある場合は、エミュレートされたNVRAMをクリーンアップして、ネイティブNVRAMを機能させる必要があります。 エミュレートされたNVRAMを使用したことがない場合、または新規インストールを実行している場合は、この部分をスキップできます。
#### 4.4.1. LogoutHookをクリーンアップします
**ステップ 1：**

ターミナルで実行
```diff
sudo defaults read com.apple.loginwindow LogoutHook
```
出力が
```diff
The domain/default pair of (com.apple.loginwindow, LogoutHook) does not exist
```
LogoutHookが残っていないことを意味します。

**ステップ 2：** 

 ```LogoutHook.command``` ファイルを削除する，ターミナルで実行
```diff
sudo rm -rf $(sudo defaults read com.apple.loginwindow LogoutHook)
```

**ステップ 3：** 

```LogoutHook``` トリガー設定をクリーンアップし、ターミナルで実行します
```diff
sudo defaults delete com.apple.loginwindow LogoutHook
```

#### 4.4.2. ファイルの削除（ある場合）
```nvram.plist``` in ```EFI```  prartition.

```VariableRuntimeDxe.efi``` and ```EmuVariableRuntimeDxe.efi``` in ```/EFI/OC/Drivers```

#### 4.4.3. 検査NVRAM機能
ターミナルで一度に各行を実行し、
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
デバイスを再起動してから、ターミナルで実行します
```diff
vram -p | grep -i myvar
```
 ```myvar test``` がリターンラインに含まれている場合、NVRAMは正しく機能しています。
## <span id="iss">5. 既知の問題</span>

* **パッチ変更_E2CをXE2Cに有効にすると、OCでWindowsを起動しているときにAPICエラーが発生します**
  
  解決策：TB3機能を無効にするか、BIOSインターフェイスを使用してWindowsを起動します。
  
* **<span id="drm">「iMac（2019、5K）」のモデルは、DRMのため、Apple TV +をサポートしていません。 ただし、Apple Music（テスト済み）、Amazon Prime（テスト済み）、NetflixはChromeを使用して動作するはずです（Safariでは動作しません）。</span>**
  
  解決策：モデルをiMac Proに変更します。ただし、サイドカー機能は失われます。
  
  
| システム定義              | iMacPro1,1                                                              | iMac19,1                        |
|:------------------------------:|:-----------------------------------------------------------------------:|:-------------------------------:|
| iGPU（およびQuickSync）           | これらは元々Xeonプロセッサに付属しているため、構成できません | 対応                      |
| サイドカー                        | iGPUなしでは不可能                                               | （ヘッドレス）iGPUと互換性があります |
| SafariでのDRMサポート          | 対応                                                                | 対応なし                              |
| Apple TV/iTunesでのDRMサポート | 対応                                                                | 対応 through WEG                |
| パフォーマンス                    | GPUでより良い                                                         | iGPUでより良い                |
| Vega/Polaris サポート           | 対応、WEGて                                            | 対応                |
| Coffeelakeの電源管理    | 対応、エクステンションて                                                | 対応                        |
| CPU周波数スケーリング          |対応、CPUFriendとiMac19,1て board.plist                         | 対応                        |


## <span id="logs">6. 更新ログ</span>

**0.6.4:** Update OpenCore to 0.6.4

**0.6.3.2:** Re-builded the EFI, removed FakeSMC (tested in 11.0.1 Beta(20B5012d)).

**0.6.3.1:** Fix mirror errors.

**0.6.3:** Update OpenCore to 0.6.3

**0.6.2:** First release

## <span id="bench">7. ベンチマーク</span>
### Geekbench 5 CPU:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_benchmark.png)

### Cinebench R20:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/CPU_cine.png)

### Geekbench 5 GPU OpenCL:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_open.png)

### Geekbench 5 GPU Metal:
![image](https://raw.githubusercontent.com/seanzhang98/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh/main/imgs/gra_metal.png)

## <span id="ref">8. 参考文献</span>
📖 [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)

📖 [精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)

📖 [macOS Catalina 10.15安装中常见的问题及解决方法](https://blog.daliansky.net/Common-problems-and-solutions-in-macOS-Catalina-10.15-installation.html)

📖 [使用HIDPI解决睡眠唤醒黑屏、花屏及连接外部显示器的正确姿势](https://blog.daliansky.net/Use-HIDPI-to-solve-sleep-wake-up-black-screen,-Huaping-and-connect-the-external-monitor-the-correct-posture.html)

📖 [OpenCore部件补丁](https://github.com/daliansky/OC-little)

📖 [华擎ASRock Z390 Phantom Gaming ITX/ac 雷电3 完美驱动 热插拔](http://blog.fangf.cc/2020/05/19/TB3/)

📖 [OpenCore（OC）引导模拟NVRAM](https://imacos.top/2020/04/18/nvram/)

📖 [Sidecar and SMBIOS : iMac19,1 vs. iMacPro1,1](https://www.reddit.com/r/hackintosh/comments/dwbncg/sidecar_and_smbios_imac191_vs_imacpro11/)


## <span id="thanks">9. 感謝</span>
**[daliansky](https://github.com/daliansky)（黑果小兵）**

**[RehabMan](https://bitbucket.org/RehabMan/)**

**[icyleaf](https://icyleaf.com/2019/03/asrock-z390-gaming-itx-install-hackintosh-tutorial/)**

**[ZeRo° Xu](https://github.com/xzhih)（冰水加劲Q）**

**[acidanthera](https://github.com/acidanthera/OpenCorePkg)**

**[fangf2018](https://github.com/fangf2018/ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh)**

**[Bat.bat](https://github.com/williambj1)**

## 10. 読者数
<p align="left">
<a href="http://antzuhl.cn:4000/get/@
ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur.readme_ja">
      <img alt="" src="http://antzuhl.cn:4000/get/@ASRock-Z390-Phantom-ITX-OpenCore-Hackintosh-BigSur.readme_ja" />
</p>