---
title: DIF_REGISTER_COINSTALLERS
description: DIF_REGISTER_COINSTALLERS
ms.assetid: 9b75470b-9f65-47ec-b738-9664f3e766d1
keywords:
- DIF_REGISTER_COINSTALLERS 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DIF_REGISTER_COINSTALLERS
api_location:
- Setupapi.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: b4d4c7b2078fc349a9846f51b935da0f48591b39
ms.sourcegitcommit: b84d760d4b45795be12e625db1d5a4167dc2c9ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90716204"
---
# <a name="dif_register_coinstallers"></a>DIF_REGISTER_COINSTALLERS


DIF_REGISTER_COINSTALLERS 请求允许安装程序参与设备共同安装程序的注册。

### <a name="when-sent"></a>发送时间

完成设备安装。

### <a name="who-handles"></a>谁处理

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>类共同安装程序</p></td>
<td align="left"><p>可以处理</p></td>
</tr>
<tr class="even">
<td align="left"><p>设备共同安装程序</p></td>
<td align="left"><p>不处理</p></td>
</tr>
<tr class="odd">
<td align="left"><p>类安装程序</p></td>
<td align="left"><p>可以处理</p></td>
</tr>
</tbody>
</table>

 

### <a name="installer-input"></a>安装程序输入

<a href="" id="deviceinfoset"></a>*DeviceInfoSet*  
向 [设备信息集](./device-information-sets.md) 提供一个句柄，其中包含要为其注册共同安装程序的设备。

<a href="" id="deviceinfodata"></a>*DeviceInfoData*  
提供一个指向 [**SP_DEVINFO_DATA**](/windows/win32/api/setupapi/ns-setupapi-sp_devinfo_data) 结构的指针，该结构在设备信息集中标识设备。

<a href="" id="device-installation-parameters-"></a>设备安装参数   
与*DeviceInfoData*关联的设备安装参数 ([**SP_DEVINSTALL_PARAMS**](/windows/win32/api/setupapi/ns-setupapi-sp_devinstall_params_a)) 。

<a href="" id="class-installation-parameters"></a>类安装参数  
无

### <a name="installer-output"></a>安装程序输出

<a href="" id="none"></a>无  

### <a name="installer-return-value"></a>安装程序返回值

共同安装程序可以返回 NO_ERROR、ERROR_DI_POSTPROCESSING_REQUIRED 或 Win32 错误代码。

如果类安装程序成功处理此请求，并且 [**SetupDiCallClassInstaller**](/windows/win32/api/setupapi/nf-setupapi-setupdicallclassinstaller) 随后应调用默认处理程序，则类安装程序将返回 ERROR_DI_DO_DEFAULT。

如果类安装程序成功处理此请求（包括直接调用默认处理程序），则类安装程序应返回 NO_ERROR 并且 **SetupDiCallClassInstaller** 将不会再次调用默认处理程序。

**注意**   类安装程序可以直接调用默认处理程序，但类安装程序永远不会尝试取代默认处理程序的操作。

 

有关调用默认处理程序的详细信息，请参阅 [调用默认的 DIF 代码处理程序](./calling-the-default-dif-code-handlers.md)。

如果类安装程序遇到错误，则安装程序应返回相应的 Win32 错误代码，并且 **SetupDiCallClassInstaller** 将不会随后调用默认处理程序。

### <a name="default-dif-code-handler"></a>默认的 DIF 代码处理程序

[**SetupDiRegisterCoDeviceInstallers**](/windows/win32/api/setupapi/nf-setupapi-setupdiregistercodeviceinstallers)

### <a name="installer-operation"></a>安装程序操作

为了响应 DIF_REGISTER_COINSTALLERS 请求，安装程序可能会修改设备的共同安装程序列表。 例如，安装程序可能以编程方式注册或删除基于设备分析的设备特定设备的共同安装程序。

除非设置了 DI_NOFILECOPY 标志，否则处理此 DIF 请求的安装程序应复制共同安装程序 () 所需的文件。

如果 DI_NOFILECOPY 标志清晰但设置了 DI_NOVCP 标志，则安装程序必须将任何文件操作排队到提供的文件队列中，但不得提交队列。

如果安装程序返回 Win32 错误代码，则 Windows 将停止安装。

有关 DIF 代码的详细信息，请参阅 [处理 Dif 代码](./handling-dif-codes.md)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>在 Microsoft Windows 2000 和更高版本的 Windows 中受支持。</p></td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left">Setupapi.log (包含 Setupapi.log) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**SetupDiRegisterCoDeviceInstallers**](/windows/win32/api/setupapi/nf-setupapi-setupdiregistercodeviceinstallers)

[**SP_DEVINFO_DATA**](/windows/win32/api/setupapi/ns-setupapi-sp_devinfo_data)

[**SP_DEVINSTALL_PARAMS**](/windows/win32/api/setupapi/ns-setupapi-sp_devinstall_params_a)

 

