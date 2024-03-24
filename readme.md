# Hackintosh-OC-MSI-Granade-H110M-i5-6500-Skylake-HD530

Hackintosh OpenCore configuration

## Support macOS Versions

| Versions              | Support Status | Path                                                                                                         |
|-----------------------|:--------------:|--------------------------------------------------------------------------------------------------------------|
| macOS Monterey (12.x) |       ✅        | [/Monterey](https://github.com/surya432/efi-skylake-hackingtosh/tree/main/SkyLake.Montereyy) |
| macOS Sonoma (14.x)  |       ✅        | [/Ventura](https://github.com/surya432/efi-skylake-hackingtosh/tree/main/SkyLake.Sonoma)   |

Support Status Explanation：
* ✅ Fully supported, including developer versions
* ⚠️ Partially supported, consumer version only
* 🚧 Exploration in progress, not supported

## Computer Hardware

* Motherboard Brand: Micro-Star International
* Motherboard Model: MSI Granade H110M
* Motherboard Chipset: Intel® H110 Chipset

* CPU: Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz
* Graphics Card: Intel HD Graphics 530
* Nvidia/AMD Graphics Card: None
* Audio Card：Realtek ALC882

See detailed configuration at Report.txt(CN)

## BIOS Configuration

If you have the same as my motherboard model and system version, you can refer to the position in the brackets and use the BIOS shell to modify.

### Disabled

* CFG lock (0x11F Set to 0x0)
* VT-d (0x496 Set to 0x0)
* SGX (0x1CA Set to 0x0)
* CSM (0xE17 Set to 0x0)
* RTC Lock (0x5A5 Set to 0x0)

### Enabled

* Above 4G Decoding (0xDEC Set to 0x1)
* Hyper-threading (0xE9 Set to 0x1)
* Execute Disable Bit (0x272 Set to 0x1)
* EHCI Hand-off (0x2 Set to 0x1)

## Attention ⚠️

Please change MLB, SystemSerialNumber, SystemUUID into your own `config.plist`.

```xml
<dict>
    ...
    <key>MLB</key>
    <string>xxxxxxxxxxxxxxx</string>
    ...
    <key>SystemSerialNumber</key>
    <string>xxxxxxxxxxx</string>
    ...
    <key>SystemUUID</key>
    <string>xxxxxxxx-xxxxx-xxxxx-xxxx-xxxxxxxx</string>
</dict>
```

## How to

### Generate your own `CPUFriendDataProvider.kext`

1. Download the **RELEASE** version of `CPUFriend.kext` from [HERE](https://dortania.github.io/builds/?product=CPUFriend&viewall=true).
2. Unzip the archive.
3. Run the shell bellow in `Terminal.app`.

```shell
./ResourceConverter.sh --kext /System/Library/Extensions/IOPlatformPluginFamily.kext/Contents/PlugIns/X86PlatformPlugin.kext/Contents/Resources/Mac-DB15BD556843C820.plist
```

> Note: `Mac-DB15BD556843C820` is your `BID` value in config.plist, Please change it according to SMBIOS


