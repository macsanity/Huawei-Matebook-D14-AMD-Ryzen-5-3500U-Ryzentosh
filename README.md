# **Huawei-Matebook-D14-AMD-Ryzen-5-3500U-Ryzentosh**




# Ryzentosh SUCCESS!**



![gh](https://github.com/macsanity/Huawei-Matebook-D14-AMD-Ryzen-5-3500U-Ryzentosh/assets/116618453/bf918049-fb85-44cd-9f5b-4e7fc86857da)













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
| OPENCORE VERSION   | 1.0.0  |   


## Gathering Files

### ACPI

**In this repository we dump ssdt on our device which maybe doesn't work on your system**

**If you got kernel panic please using [SSDTTime] (https://github.com/corpnewt/SSDTTime) to dump your SSDTs**

1. Start with option `P`. It dumps the current system's DSDT, which will be utilised in order to create these SSDTs and patches.
   - `FixHPET` (Choose option `C` which only patches conflicting IRQs from legacy devices)
   - `USBX` (choose the default option `B` key)
   - `RTCAWAC`
   - `PluginType`  
     **For AMD Laptop**
   - `FakeEC Laptop`
   - `PLNF` (on this file I suggest the PNLF on Chefkiss website, just don't use the one SSDTIME produced.)
   - `XOSI` (Choose default `A` key)
2. Copy all the files that start with SSDT and end in `*.aml` inside of Drive `/EFI/OC/ACPI`
3. Finally, merge `patches_OC.plist` by using the PatchMerge script included with SSDTTime. Run it the same way as SSDTTime

Or you can Follow the guide [AMD HACKINTOSH GUIDE](https://chefkissinc.github.io/guide)



**PlatformInfo**
- Please change the MLB/ROM/Serial Number/UUID by using [GenSMBIOS](https://chefkissinc.github.io/guide)


## **Note**:
macOS Ventura (13.6) runs quite well on my laptop, but due to some [NootedRed](https://github.com/ChefKissInc/NootedRed) known issue but unkown cause, Chromium - based browser causes graphical artefacts and other problems
This is a known issue in [NR](https://github.com/ChefKissInc/NootedRed/issues/158) 
For a workaround on Google Chrome just follow either of these 2 steps

1. Open terminal and paste this: 

> open -a Google\ Chrome --args --disable-gpu

2. Or For the browsers you can disable GPU Rasterisation inside chrome://flags as a workaround or just use Safari instead.


### What is working?
- Full Gpu Acceleration
- WIFI/BT
- iMessage
- Appstore
- Screen Brightness
- Keyboard Light 

### What is not working?
- The built - in ov9734_azurewave_camera is detected but but no show no display on photobooth even on Google Meet, no known fix for this atm.
- FP of course, it will not be fixed!


### Bug(s)
- To make brightness works on my machine I have to boot winddows first then reboot to mac (Which is a known issue [here](https://github.com/ChefKissInc/NootedRed/issues/236) on Raven lineup.
- After laptop go to sleep brightness isn't working 



## PS
- If you're having hard time with your display being too small, just go [here](https://github.com/xzhih/one-key-hidpi/blob/master/README.md) simulate macOS HiDPI on a non-retina display (I'm telling you the display is much readable :) )
- On your AmdTscSync.kext make sure IOCPUNumber to "0" without the " if you're running on Ventura or later
- When Installing make sure to disable your NR kext first, just enable it when your mac boots into your desktop.
- If someone manage to use trackpad without using -vi2c-force-polling help me out.
  
## Credits / Thanks 

- [Apple](https://www.apple.com) for macOS
- [herrnst](https://github.com/herrnst/HuaweiMatebookD14AMD-OpenCore) for the guide making this EFI
- [ChefKissInc](https://github.com/ChefKissInc/NootedRed) for the AMD IGPU support functionality
- [For the RadeonSensor](https://github.com/ChefKissInc/RadeonSensor) (GPU sensors)
- [OpenIntelWireless](https://github.com/OpenIntelWireless) for [AirpotItlwm](https://github.com/OpenIntelWireless/itlwm) and [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
- [For the OpenCore bootloader](https://github.com/acidanthera/OpenCorePkg)
- [chefkissinc for the Installation Guide](https://chefkissinc.github.io/guide)


