---
title: Web 服务扫描仪的示例 INF 文件
description: Web 服务扫描仪的示例 INF 文件
ms.assetid: 1e65739f-9216-4962-9108-60ba291ff052
ms.date: 05/29/2020
ms.localizationpriority: medium
ms.openlocfilehash: 4ca82dc9b5a05d711d63bfbec57c43071921cf63
ms.sourcegitcommit: a16fd2876383265b4ad336dea624e4b13fc13a1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643999"
---
# <a name="sample-inf-file-for-a-web-services-scanner"></a>Web 服务扫描仪的示例 INF 文件

以下 INF 文件 *Sti*演示如何安装 WIA 驱动程序。 突出显示 *WSDScan.sys* 所需的项。

> [!NOTE]
> [ (DOC 下载) ](https://go.microsoft.com/fwlink/p/?linkid=242570)中介绍了在以下 INF 示例中引用的设备硬件 Id 和**PKEY \_ 设备 \_ HardwareIds**属性的要求。

```inf
;
; MyWSScanner.inf - sample installation file that shows how
; to install a WIA driver for a WS scanner by using the inbox
; WSDScan.sys kernel driver
;
[Version]
Signature="$WINDOWS NT$"
Class=Image
ClassGUID={6bdd1fc6-810f-11d0-bec7-08002be2092f}
Provider=%Mfg%
DriverVer=1/17/2006,1.0.0.0 ; replace with the actual driver date
; and version

[SourceDisksFiles.x86]
YourWIADriver.dll=1

[SourceDisksNames.x86]
1=%Location%,,,

[SourceDisksFiles.ia64]
YourWIADriver.dll=1

[SourceDisksNames.ia64]
1=%Location%,,,

[SourceDisksFiles.amd64]
YourWIADriver.dll=1

[SourceDisksNames.amd64]
1=%Location%,,,

[DestinationDirs]
DefaultDestDir = 11

[Manufacturer]
%Mfg%=Models,NTx86,NTamd64,NTia64

;
; Replace UMB\PnPX_YourDevice_HardwareID in the three Models
; sections below to match the actual hardware IDs and compatible
; IDs from the metadata that is supplied by the device, as it
; is described in the PNP-X Implementer's Guide for the
; PKEY_Device_HardwareIds property:
;

[Models.NTx86]
%WSDScanDriver.DeviceDesc% = WSDScanDriver.Device, UMB\PnPX_YourDevice_HardwareID

[Models.NTamd64]
%WSDScanDriver.DeviceDesc% = WSDScanDriver.Device, UMB\PnPX_YourDevice_HardwareID

[Models.NTia64]
%WSDScanDriver.DeviceDesc% = WSDScanDriver.Device, UMB\PnPX_YourDevice_HardwareID

[WSDScanDriver.Device]
Include=sti.inf
Needs=STI.WSDSection
SubClass=StillImage
DeviceType=1            ; scanner device
DeviceSubType=1
Capabilities=0x31       ; STI_GENCAP_NOTIFICATIONS (bit 0) | STI_GENCAP_WIA (bit 4) | bit 5
DeviceData=WSDScanDriver.DeviceData
Events=WSDScanDriver.Events
AddReg=WSDScanDriver.AddReg
CopyFiles=WSDScanDriver.CopyFiles
ICMProfiles="sRGB Color Space Profile.icm"

[WSDScanDriver.CopyFiles]
MyWIADriver.dll

;
; Do not forget to replace 00000000-0000-0000-0000-000000000000
; in the AddReg section below with the actual UUID for your WIA
; minidriver:
;

[WSDScanDriver.AddReg]
HKR,,HardwareConfig,1,1 ; generic WDM device
HKR,,USDClass,,"{00000000-0000-0000-0000-000000000000}"
; the GUID for the WIA mini-driver
HKCR,CLSID\{00000000-0000-0000-0000-000000000000},,,"<Description
of your Web Services scanner WIA device>"
HKCR,CLSID\{00000000-0000-0000-0000-000000000000}\InProcServer32,,,%11%\YourWIADriver.dll
HKCR,CLSID\{00000000-0000-0000-0000-000000000000}\InProcServer32,ThreadingModel,,"Both"

[WSDScanDriver.DeviceData]
Server=local           ; the WIA mini-driver runs on the same
machine as the client application

[WSDScanDriver.Events]
ScanEvent=%ScanEvent.Desc%,{A6C5A715-8C6E-11d2-977A-0000F87A926F},*
ScanToPrintEvent=%ScanToPrintEvent.Desc%,{B441f425-8C6e-11D2-977A-0000F87A926F},*
ScanToFaxEvent=%ScanToFaxEvent.Desc%,{C00EB793-8C6E-11D2-977A-0000F87A926F},*
ScanToOCREvent=%ScanToOCREvent.Desc%,{9D095B89-37D6-4877-AFED-62A297DC6DBE},*
ScanToEmailEvent=%ScanToEmailEvent.Desc%,{C686DCEE-54F2-419E-9A27-2FC7F2E98F9E},*

[WSDScanDriver.Device.HW]
Include=sti.inf
Needs=STI.WSDSection.HW

[WSDScanDriver.Device.Services]
Include=sti.inf
Needs=STI.WSDSection.Services

[Strings]
Mfg="<Your company name here>"
Location="<Your installation source name here>"
WSDScanDriver.DeviceDesc="<Your Web Services WIA device description>"
ScanEvent.Desc="Scan"
ScanToPrintEvent.Desc="Scan To Print"
ScanToFaxEvent.Desc="Scan To Fax"
ScanToOCREvent.Desc="Scan To OCR"
ScanToEmailEvent.Desc="Scan To E-mail"
```
