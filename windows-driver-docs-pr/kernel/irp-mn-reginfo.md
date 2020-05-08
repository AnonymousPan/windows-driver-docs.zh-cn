---
title: IRP_MN_REGINFO
description: 支持 Microsoft Windows 98 和 Microsoft Windows 2000 上的 WMI 的驱动程序必须处理此 IRP。
ms.date: 08/12/2017
ms.assetid: db93b64b-a2e4-429d-850e-921fb438467c
keywords:
- IRP_MN_REGINFO 内核模式驱动程序体系结构
ms.localizationpriority: medium
ms.openlocfilehash: bf9eff4f32befa3262e7891ef2030fad99de51fb
ms.sourcegitcommit: 7681ac46c42782602bd3449d61f7ed4870ef3ba7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922570"
---
# <a name="irp_mn_reginfo"></a>IRP\_MN\_REGINFO


支持 Microsoft Windows 98 和 Microsoft Windows 2000 上的 WMI 的驱动程序必须处理此 IRP。 （还必须处理[**IRP\_\_MN REGINFO\_EX**](irp-mn-reginfo-ex.md) irp 的驱动程序。）驱动程序可以通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)或处理 IRP 本身来处理 wmi irp，如[处理 WMI 请求](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-wmi-requests)中所述。

<a name="major-code"></a>主要代码
----------

[**IRP\_MJ\_系统\_控件**](irp-mj-system-control.md)

<a name="when-sent"></a>发送时间
---------

在 Windows 98 和 Windows 2000 上，WMI 会发送此 IRP 来在驱动程序调用[**IoWMIRegistrationControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iowmiregistrationcontrol)之后查询或更新驱动程序的注册信息。 在 Windows XP 和更高版本上，WMI 会发送**IRP\_\_MN REGINFO\_EX**请求。

WMI 在系统线程的上下文中以\_IRQL = 被动级别发送此 IRP。

## <a name="input-parameters"></a>输入参数


**Parameters。 ProviderId**指向应响应请求的驱动程序的设备对象。 此指针位于 IRP 中驱动程序的 i/o 堆栈位置。

**数据路径**设置为**WMIREGISTER** ，以查询注册信息或**WMIUPDATE**进行更新。

**Parameters。 BufferSize**指示非分页缓冲区的最大大小 **（以.** 大小必须大于或等于总计（**sizeof**（**WMIREGINFO**） + （*GuidCount* \* **sizeof**（**WMIREGGUID**）），其中*GuidCount*是驱动程序正在注册的数据块和事件块的数目，以及静态实例名称的空间（如果有）。

## <a name="output-parameters"></a>输出参数


如果驱动程序通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)来处理 WMI irp，wmi 会通过调用其[*DpWmiQueryReginfo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nc-wmilib-wmi_query_reginfo_callback)例程获取驱动程序数据块的注册信息。

否则，驱动程序将在[**WMIREGINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmireginfow)结构中填充**参数. Buffer** ，如下所示：

-   将**BufferSize**设置为**WMIREGINFO**结构的大小（以字节为单位）以及关联的注册数据。

-   如果驱动程序代表**另一个驱动**程序处理 WMI 请求，则将**NextWmiRegInfo**设置为以字节为单位的偏移量 **（以字节**为单位）。

-   将**RegistryPath**设置为传递给驱动程序的[**DriverEntry**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_initialize)例程的注册表路径。

-   如果将**数据路径**设置为**WMIREGISTER**，则将**MofResourceName**设置为与此**WMIREGINFO**的开头之间的偏移量，并将其设置为包含其映像文件中驱动程序的 MOF 资源名称的计数 Unicode 字符串。

-   将**GuidCount**设置为要注册或更新的数据块和事件块的数量。

-   为驱动程序公开的每个数据块或事件块写入一个[**WMIREGGUID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmiregguidw)结构数组，在**WMIREGGUID**。

该驱动程序将填充每个**WMIREGGUID**结构，如下所示：

-   将**guid**设置为标识块的 guid。

-   设置**标志**以提供有关块的实例名称和其他特性的信息。 例如，如果使用静态实例名称注册块，驱动程序将使用相应的 WMIREG **Flags** \_标志\_实例\_*XXX*标志设置标志。

如果正在向静态实例名称注册块，则驱动程序：

-   将**InstanceCount**设置为实例数。

-   将以下成员之一设置为块的静态实例名称数据的偏移量（以字节为单位）：
    -   如果驱动程序使用**Flags** WMIREG\_标志\_实例\_列表设置标志，则它会将**InstanceNameList**设置为静态实例名称字符串列表的偏移量。 WMI 通过索引向此列表指定后续请求中的实例。
    -   如果驱动程序使用**Flags** WMIREG\_标志\_实例\_BASENAME 设置标志，则它会将**BaseNameOffset**设置为基名称字符串的偏移量。 WMI 使用此字符串生成块的静态实例名称。
    -   如果驱动程序使用**Flags** WMIREG\_\_标志实例\_PDO 设置标志，则会将**PDO**设置为指向传递给驱动程序的[*AddDevice*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_add_device)例程的 PDO 的指针的偏移量。 WMI 使用 PDO 的设备实例路径为块生成静态实例名称。
-   在**InstanceNameList**、 **BaseName**或**PDO**分别指示的偏移位置写入实例名称字符串、基名称字符串或指向 PDO 的指针。

如果驱动程序代表其他驱动程序（如 miniclass 或微型端口驱动程序）处理 WMI 注册，它将使用其他驱动程序的注册信息填充另一 WMIREGINFO 结构，并将其写入先前结构中的**NextWmiRegInfo** 。

如果位于**参数. buffer**的缓冲区太小，无法接收所有数据，则驱动程序会将所需的大小以字节为单位写入到**参数. buffer** ，并使 IRP 失败并返回状态\_缓冲区\_太\_小。

## <a name="io-status-block"></a>I/o 状态块


如果驱动程序通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)来处理 IRP，WMI 将在 i/o 状态块中设置**irp-&gt;IoStatus**和**irp-&gt;IoStatus。**

否则，驱动程序会将**Irp&gt;-IOSTATUS**设置为状态\_成功，或设置为适当的错误状态，如下所示：

状态\_缓冲区\_太\_小

成功时，驱动程序将**Irp-&gt;IoStatus**设置为写入**缓冲区中的字节数。**

<a name="operation"></a>操作
---------

驱动程序可以通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)或处理 IRP 本身来处理 wmi irp，如[处理 WMI 请求](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-wmi-requests)中所述。

如果驱动程序通过调用[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)来处理 WMI irp，则该例程将调用驱动程序的[*DpWmiQueryReginfo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nc-wmilib-wmi_query_reginfo_callback)例程。

如果驱动程序处理**\_IRP MN\_REGINFO**请求本身，只应在**参数. ProviderId**指向与驱动程序传递到[**IoWMIRegistrationControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iowmiregistrationcontrol)的指针相同的设备对象时才执行此操作。 否则，驱动程序必须将请求转发到下一个较低版本的驱动程序。

在处理请求之前，驱动程序必须检查**数据路径**以确定 WMI 是否正在查询注册信息（**WMIREGISTER**）或请求更新（**WMIUPDATE**）。

当驱动程序调用**IoWMIRegistrationControl**并 WMIREG\_操作\_注册或 WMIREG\_操作\_重新注册后，WMI 将使用 WMIREGISTER 发送此 IRP。 在响应中，驱动程序应使用以下内容在**参数.**

-   [**WMIREGINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmireginfow)结构，指示驱动程序的注册表路径、其 MOF 资源的名称以及要注册的块的数量。

-   要注册的每个块都有一个[**WMIREGGUID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmiregguidw)结构。 如果要向静态实例名称注册块，则驱动程序会在该块的**WMIREGGUID**结构\_中\_设置相应的 WMIREG\_标志实例*XXX*标志。

-   WMI 需要生成静态实例名称的任何字符串。

当驱动程序使用\_WMIREG 操作\_\_更新 guid 调用**IoWmiRegistrationControl**后，WMI 将使用**WMIUPDATE**发送此 IRP。 在响应中，驱动程序**应使用 WMIREGINFO 结构在缓冲区**中填写，如下所示：

-   若要删除块，驱动程序会在\_其\_\_ **WMIREGGUID**结构中设置 WMIREG 标志删除 GUID。

-   若要添加或更新块（例如，要更改其静态实例名称），驱动程序将清除 WMIREG\_标志\_删除\_GUID，并为块提供新的或更新的注册值。

-   若要向静态实例名称注册新的或现有的块，驱动程序将设置\_相应\_的\_WMIREG 标志实例*XXX* ，并提供 WMI 生成静态实例名称所需的任何字符串。

驱动程序可以使用相同的**WMIREGINFO**结构来删除、添加或更新块，因为它最初用于注册其所有块，只更改要更新的块的标志和数据。 如果此类**WMIREGINFO**结构中的**WMIREGGUID**与驱动程序首次注册该块时所传递的**WMIREGGUID**完全匹配，则 WMI 将跳过更新块所涉及的处理过程。

当驱动程序调用[**IOWMIREGISTRATIONCONTROL**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iowmiregistrationcontrol) WMIREG\_ACTION\_取消注册后，wmi 不会发送**\_IRP MN\_REGINFO**请求，因为 wmi 不需要驱动程序提供进一步的信息。 驱动程序通常会注销其块，以响应[**IRP\_MN\_删除\_设备**](irp-mn-remove-device.md)请求。

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


[*DpWmiQueryReginfo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nc-wmilib-wmi_query_reginfo_callback)

[**IoWMIRegistrationControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iowmiregistrationcontrol)

[**WMILIB\_上下文**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/ns-wmilib-_wmilib_context)

[**WMIREGGUID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmiregguidw)

[**WMIREGINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmistr/ns-wmistr-wmireginfow)

[**WmiSystemControl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wmilib/nf-wmilib-wmisystemcontrol)

[**IRP\_MN\_REGINFO\_EX**](irp-mn-reginfo-ex.md)

 

 




