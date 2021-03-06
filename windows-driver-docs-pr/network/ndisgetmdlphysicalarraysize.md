---
title: NdisGetMdlPhysicalArraySize 宏
description: NdisGetMdlPhysicalArraySize 宏检索与 MDL 关联的断开连接的物理内存块的数量。
ms.assetid: 25e3f9a3-3057-4081-af74-427102197906
ms.date: 07/18/2017
keywords:
- NdisGetMdlPhysicalArraySize 从 Windows Vista 开始的宏网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 7abde061cee85358fa9bac71265d1330b95d26c6
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104876"
---
# <a name="ndisgetmdlphysicalarraysize-macro"></a>NdisGetMdlPhysicalArraySize 宏


**NdisGetMdlPhysicalArraySize**宏检索与 MDL 关联的断开连接的物理内存块的数量。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
VOID NdisGetMdlPhysicalArraySize(
    _Mdl,
    _ArraySize
);
```

<a name="parameters"></a>参数
----------

*\_Mdl*   
指向 MDL 的指针。

*\_数组大小*   
指向调用方提供的变量的指针，此宏返回与指定 MDL 关联的断开连接的物理内存块的数量。

<a name="return-value"></a>返回值
------------

无

<a name="remarks"></a>备注
-------

**NdisGetMdlPhysicalArraySize**宏提供[**NdisGetBufferPhysicalArraySize**](/previous-versions/windows/hardware/network/ff552033(v=vs.85))函数的基于 MDL 的版本。

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


[**NdisGetBufferPhysicalArraySize**](/previous-versions/windows/hardware/network/ff552033(v=vs.85))

