# **Huawei-Matebook-D14-AMD-Ryzen-5-3500U-Ryzentosh**
OpenCore configuration for Huawei Matebook D14 AMD (2020) -NBLK-WAX9X running macOS 






![Screenshot 2024-05-08 at 21 49 18](https://github.com/macsanity/Huawei-Matebook-D14-AMD-Ryzen-5-3500U-Ryzentosh/assets/116618453/5544305b-d916-4666-b3c6-807e23f54631)





**HARDWARE SPECFIFICATION**
| **Component**  | **Details/Description** | 
| ------------- | ------------- |
| CPU           | AMD Ryzen 5 3500U         |        
| GPU           | AMD Radeon Vega 8 (iGPU)  |        
| RAM           | M471A5244CB0-CRC(DDR4)    |        
| STORAGE       | PC SN730 NVMe SSD         |        
| WIFI/BT CARD  | Intel® Wi-Fi 6 AX200      |        
| AUDIO/MIC     | Realtek ALC256 (AppleALC layout ID 21)  |        
| CAMERA        | ov9734_azurewave_camera  |        
| SMBIOS USED   | MacBookPro16,3  |      
| OPENCORE VERSION   | 0.9.9  |   


## Preparing

### SSDTs

**In this repository we dump ssdt on our device which maybe doesn't work on your system**

**If you got kernel panic please using [SSDTTime] (https://github.com/corpnewt/SSDTTime) to dump your SSDTs**

1. Start with option `P`. It dumps the current system's DSDT, which will be utilised in order to create these SSDTs and patches.
   - `FixHPET` (Choose option `C` which only patches conflicting IRQs from legacy devices)
   - `USBX` (choose the default option `B` key)
   - `RTCAWAC`
   - `PluginType`  
     **For AMD Laptop**
   - `FakeEC Laptop`
   - `PLNF`
   - `XOSI` (Choose default `A` key)
2. Copy all the files that start with SSDT and end in `*.aml` inside of Drive `/EFI/OC/ACPI`
3. Finally, merge `patches_OC.plist` by using the PatchMerge script included with SSDTTime. Run it the same way as SSDTTime

Or you can start the guide [here]([https://nootinc.github.io/guide/gathering-files/acpi](https://chefkissinc.github.io/guide))


**PlatformInfo**
- Please change the MLB/ROM/Serial Number/UUID by using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)


## **Note**:
macOS Ventura (13.6) runs quite well on this machine, but Chromium - based browser causes and apps like Sublime Text cause graphical artefacts and other problems
This is a known issue in [NR](https://github.com/ChefKissInc/NootedRed/issues/158) 
For a workaround just follow either of these 2 steps

1. Open terminal and paste this: 

> open -a Google\ Chrome --args --disable-gpu

2. Or For the browsers you can disable GPU Rasterisation inside chrome://flags as a workaround or just use Safari.


### What is working?
- Full Gpu Acceleration
- WIFI/BT
- iMessage
- Appstore
- Screen Brightness
- Keyboard Light 

### What is not working?
- The built - in ov9734_azurewave_camera is detected but but no show no display on photobooth even on Google Meet
- 


### Bug(s)
- To make brightness works on my machine I have to boot winddows first then reboot to mac
- After laptop go to sleep brightness isn't working 





## Credits / Thanks 

- [Apple](https://www.apple.com) for macOS
- [herrnst](https://github.com/herrnst/HuaweiMatebookD14AMD-OpenCore) For the guide and working EFI.
- [ChefKissInc](https://github.com/ChefKissInc/NootedRed) for the AMD IGPU support functionality
- [RadeonSensor](https://github.com/ChefKissInc/RadeonSensor) (GPU sensors)
- [OpenIntelWireless](https://github.com/OpenIntelWireless) for [AirpotItlwm](https://github.com/OpenIntelWireless/itlwm) and [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
- [OpenCore bootloader](https://github.com/acidanthera/OpenCorePkg)


## What's in the box?

├── EFI
│   ├── BOOT
│   │   └── BOOTx64.efi
│   └── OC
│       ├── ACPI
│       │   ├── SSDT-ALS0.aml
│       │   ├── SSDT-EC-USBX.aml
│       │   ├── SSDT-EC.aml
│       │   ├── SSDT-GPRW.aml
│       │   ├── SSDT-HPET.aml
│       │   └── SSDT-PLUG.aml
│       │   ├── SSDT-PNLF.aml
│       │   ├── SSDT-RMNE.aml
│       │   ├── SSDT-SBUS-MCHC.aml
│       │   ├── SSDT-SLPB.aml
│       │   ├── SSDT-USBX.aml
│       │   └── SSDT-XOSI.aml
│       ├── Bootstrap
│       │   └── Bootstrap.efi
│       ├── config.plist
│       ├── Drivers
│       │   ├── HfsPlus.efi
│       │   ├── OpenCanopy.efi
│       │   └── OpenRuntime.efi
│       ├── Kexts
│       │   ├── AMDRyzenCPUPowerManagement.kext
│       │   ├── AmdTscSync.kext
│       │   ├── AppleALC.kext
│       │   ├── AppleMCEReporterDisabler.kext
│       │   ├── ECEnabler.kext
│       │   ├── itlwm.kext
│       │   ├── Lilu.kext
│       │   ├── NootedRed.kext
│       │   ├── NVMeFix.kext
│       │   ├── RadeonSensor.kext
│       │   ├── SMCAMDProcessor.kext
│       │   ├── SMCBatteryManager.kext
│       │   ├── SMCRadeonGPU.kext
│       │   ├── USBToolBox.kext
│       │   ├── UTBDefault.kext
│       │   ├── VirtualSMC.kext
│       │   ├── VoodooPS2Controller.kext
│       │   └── HeliPort.dmg
│       ├── OpenCore.efi
│       └── Resources
│           ├── Audio
│           ├── Font
│           ├── Image
│           └── Label



