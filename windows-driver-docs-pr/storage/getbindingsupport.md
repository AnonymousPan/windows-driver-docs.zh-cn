---
title: GetBindingSupport 函数
description: GetBindingSupport 方法检索当前为指定端口启用的绑定功能。
ms.assetid: 50c90379-613f-42f1-80fe-7bc1b77a53bf
keywords:
- GetBindingSupport 函数存储设备
topic_type:
- apiref
api_name:
- GetBindingSupport
api_location:
- Hbaapi.lib
- Hbaapi.dll
api_type:
- LibDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: b490255c066c63b9c4afa9b4ef570342505f9967
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89185449"
---
# <a name="getbindingsupport-function"></a>GetBindingSupport 函数


**GetBindingSupport**方法检索当前为指定端口启用的绑定功能。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
void GetBindingSupport(
   [in, HBAType("HBA_WWN")] uint8                PortWWN[8],
   [out, HBA_STATUS_QUALIFIERS] HBA_STATUS       HBAStatus,
   [out, HBA_BIND_TYPE_QUALIFIERS] HBA_BIND_TYPE BindType
);
```

<a name="parameters"></a>参数
----------

*PortWWN \[ 8\]*   
一个全球名称，指示要检索其持久性绑定的端口。

*HBAStatus*   
返回时，包含操作的状态。 有关允许值及其说明的列表，请参阅 [HBA \_ 状态](hba-status.md)。 微型端口驱动程序在[**GetBindingSupport \_ OUT**](/windows-hardware/drivers/ddi/hbapiwmi/ns-hbapiwmi-_getbindingsupport_out)结构的**HBAStatus**成员中返回此信息。

*BindType*   
指示 HBA 及其微型端口驱动程序提供与永久性绑定相关的一组特定功能的位图。 有关此参数可以具有的值的列表，请参阅 [HBA \_ 绑定 \_ 类型](hba-bind-type.md) WMI 类限定符的说明。

<a name="return-value"></a>返回值
------------

不适用于 WMI 方法。

<a name="remarks"></a>备注
-------

此 **GetBindingSupport** 方法将返回当前启用的绑定功能，而 [**GetBindingCapability**](getbindingcapability.md) 方法指示该端口的绑定功能，而无需引用是否启用特定的绑定。

此 WMI 方法属于 [MSFC \_ HBAFCPInfo WMI 类](msfc-hbafcpinfo-wmi-class.md)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>目标平台</p></td>
<td align="left">“桌面”</td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left"> (包含 Hbapiwmi、Hbaapi 或 Hbaapi 的 Hbapiwmi) </td>
</tr>
<tr class="odd">
<td align="left"><p>库</p></td>
<td align="left">Hbaapi</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[**GetBindingCapability**](getbindingcapability.md)

[**GetBindingSupport**](getbindingsupport.md)

[**GetBindingSupport \_**](/windows-hardware/drivers/ddi/hbapiwmi/ns-hbapiwmi-_getbindingsupport_in)

[**GetBindingSupport \_**](/windows-hardware/drivers/ddi/hbapiwmi/ns-hbapiwmi-_getbindingsupport_out)

 

