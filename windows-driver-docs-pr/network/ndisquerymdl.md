---
title: NdisQueryMdl 宏
description: NdisQueryMdl 宏从 MDL 检索缓冲区长度，还可以选择基准虚拟地址。
ms.assetid: 0eccd784-c815-4094-87e5-a3e283abed73
ms.date: 07/18/2017
keywords:
- NdisQueryMdl 从 Windows Vista 开始的宏网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 639f68ab80a020c73f28ff51fcbd2d6512526e49
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104872"
---
# <a name="ndisquerymdl-macro"></a>NdisQueryMdl 宏


**NdisQueryMdl**宏从 MDL 检索缓冲区长度，还可以选择基准虚拟地址。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
VOID NdisQueryMdl(
    _Mdl,
    _VirtualAddress,
    _Length,
    _Priority
);
```

<a name="parameters"></a>参数
----------

*\_Mdl*   
指向 MDL 的指针。

*\_VirtualAddress*   
指向调用方提供的变量的指针，此宏返回 MDL 描述的虚拟地址范围的基本虚拟地址。 基本虚拟地址可以为 **NULL** ，原因如下：

-   系统资源不足或已用尽， * \_ Priority*参数设置为**LowPagePriority**或**NormalPagePriority**。

-   系统资源已耗尽， * \_ Priority*参数设置为**HighPagePriority**。

*\_长短*   
指向调用方提供的变量的指针，此宏返回 MDL 所描述的虚拟地址范围的长度（以字节为单位）。

*\_大事*   
页面优先级值。 有关此参数的可能值的列表，请参阅[**MmGetSystemAddressForMdlSafe**](../kernel/mm-bad-pointer.md)宏的*Priority*参数。

<a name="return-value"></a>返回值
------------

无

<a name="remarks"></a>备注
-------

**NdisQueryMdl**宏提供[**NdisQueryBuffer**](/previous-versions/windows/hardware/network/ff554407(v=vs.85))函数的基于 MDL 的版本。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>目标平台</p></td>
<td>桌面型</td>
</tr>
<tr class="even">
<td><p>版本</p></td>
<td><p>在 NDIS 6.0 和更高版本中受支持。</p></td>
</tr>
<tr class="odd">
<td><p>标头</p></td>
<td> (包含 Ndis .h) </td>
</tr>
<tr class="even">
<td><p>IRQL</p></td>
<td><p>&lt;= DISPATCH_LEVEL</p></td>
</tr>
<tr class="odd">
<td><p>DDI 符合性规则</p></td>
<td><a href="/windows-hardware/drivers/devtest/ndis-irql-netbuffer-function" data-raw-source="[&lt;strong&gt;Irql_NetBuffer_Function&lt;/strong&gt;](../devtest/ndis-irql-netbuffer-function.md)"><strong>Irql_NetBuffer_Function</strong></a></td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**MmGetSystemAddressForMdlSafe**](../kernel/mm-bad-pointer.md)

[**NdisQueryBuffer**](/previous-versions/windows/hardware/network/ff554407(v=vs.85))

