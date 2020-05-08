---
title: IRP_MN_ENABLE_COLLECTION
description: 注册一个或多个数据块的任何 WMI 驱动程序可能需要花费很长时间或很昂贵的时间来收集此 IRP。
ms.date: 08/12/2017
ms.assetid: dc6c3ceb-a992-4e7b-ab25-d91c00af655a
keywords:
- IRP_MN_ENABLE_COLLECTION 内核模式驱动程序体系结构
ms.localizationpriority: medium
ms.openlocfilehash: 363b4899c818ec6617b51bbca0956f8ad5d147f7
ms.sourcegitcommit: 7681ac46c42782602bd3449d61f7ed4870ef3ba7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922490"
---
# <a name="irp_mn_enable_collection"></a>IRP\_MN\_启用\_收集


注册一个或多个数据块的任何 WMI 驱动程序可能需要花费很长时间或很*昂贵*的时间来收集此 IRP。 驱动程序可以通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)或处理 IRP 本身来处理 wmi irp，如[处理 WMI 请求](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-wmi-requests)中所述。

如果驱动程序调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)来处理**IRP\_MN\_ENABLE\_COLLECTION**请求，则 WMI 反过来会调用该驱动程序的[*DpWmiFunctionControl*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nc-wmilib-wmi_function_control_callback)例程。

<a name="major-code"></a>主要代码
----------

[**IRP\_MJ\_系统\_控件**](irp-mj-system-control.md)

<a name="when-sent"></a>发送时间
---------

WMI 会发送此 IRP，请求驱动程序为已注册的驱动程序（该驱动程序已注册为收集开销）的数据块开始累积数据。

WMI 在任意线程上下文中以 IRQL\_= 被动级别发送此 IRP。

## <a name="input-parameters"></a>输入参数


**Parameters。 ProviderId**指向应响应请求的驱动程序的设备对象。 此指针位于 IRP 中驱动程序的 i/o 堆栈位置。

**数据路径**指向用于标识要为其累积数据的数据块的 GUID。

## <a name="output-parameters"></a>输出参数


无。

## <a name="io-status-block"></a>I/o 状态块


如果驱动程序通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)来处理 IRP，WMI 将在 i/o 状态块中设置**irp-&gt;IoStatus**和**irp-&gt;IoStatus。**

否则，驱动程序会将**Irp&gt;-IOSTATUS**设置为状态\_成功，或设置为适当的错误状态，如下所示：

找\_不\_\_到\_WMI GUID 状态

状态\_无效\_的\_设备请求

成功时，驱动程序将**Irp-&gt;IoStatus**设置为零。

<a name="operation"></a>操作
---------

驱动程序通过在[**WMIREGGUID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmiregguidw)或[**WMIGUIDREGINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/ns-wmilib-_wmiguidreginfo)结构的**Flags**成员中设置\_WMIREG\_标志来注册数据块，从而导致收集成本高昂。 当驱动程序注册或更新数据块时，它会将这些结构传递给 WMI。 驱动程序在接收到开始数据收集的显式请求之前，不需要为此类块累积数据。

驱动程序可以通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)或处理 IRP 本身来处理 wmi irp，如[处理 WMI 请求](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-wmi-requests)中所述。

如果驱动程序通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)来处理 WMI irp，则该例程将调用驱动程序的[*DpWmiFunctionControl*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nc-wmilib-wmi_function_control_callback)例程，\_或在驱动程序未定义例程时返回状态 SUCCESS。

如果驱动程序处理**IRP\_MN\_启用\_集合**请求，则它应仅在**参数. ProviderId**指向与驱动程序传递给[**IoWMIRegistrationControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iowmiregistrationcontrol)的指针相同的设备对象时才执行此操作。 否则，驱动程序必须将请求转发到下一个较低版本的驱动程序。

在处理请求之前，驱动程序应确保**数据路径**指向驱动程序支持的 GUID。 \_如果未\_\_找到，则驱动程序应失败 IRP 并返回状态 WMI GUID\_。 如果数据块有效但未使用 WMIREG\_标志\_进行注册，则驱动程序可能返回状态\_"成功" 并不执行任何其他操作。

如果块有效并且已注册到 WMIREG\_标志\_昂贵，则驱动程序将为该数据块的所有实例启用数据收集。

驱动程序不需要检查是否已为数据块启用了数据收集。 WMI 只发送单个请求，以便在第一个数据使用者启用块后启用数据块。 如果没有干预禁用请求，WMI 将不会发送要启用的另一个请求。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>标头</p></td>
<td>Wdm.h（包括 Wdm.h、Ntddk.h 或 Ntifs.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[*DpWmiFunctionControl*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nc-wmilib-wmi_function_control_callback)

[**IoWMIRegistrationControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iowmiregistrationcontrol)

[**IRP\_MN\_禁用\_收集**](irp-mn-disable-collection.md)

[**WMILIB\_上下文**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/ns-wmilib-_wmilib_context)

[**WMIREGGUID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmiregguidw)

[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)

 

 




