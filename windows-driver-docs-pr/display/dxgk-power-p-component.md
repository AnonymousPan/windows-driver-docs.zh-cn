---
title: DXGK \_ POWER \_ P \_ 组件结构
description: 了解 DXGK \_ POWER \_ P \_ 组件结构，它是为系统使用而保留的。 不要在您的驱动程序中使用它。
ms.assetid: 31D76B3B-E939-404B-9EE4-FFCDFCD304C8
keywords:
- DXGK_POWER_P_COMPONENT 结构显示设备
topic_type:
- apiref
api_name:
- DXGK_POWER_P_COMPONENT
api_location:
- D3dkmddi.h
api_type:
- HeaderDef
ms.date: 01/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: ab84a8cda57822026f1338834d80091603506d02
ms.sourcegitcommit: fc94eb0d5a41ef81c1b3ab91ad725386db0be0c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2020
ms.locfileid: "91603579"
---
# <a name="dxgk_power_p_component-structure"></a>DXGK \_ POWER \_ P \_ 组件结构


预留给系统使用。 不要在您的驱动程序中使用它。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef struct _DXGK_POWER_P_COMPONENT {
  ULONG                        StateCount;
  DXGK_POWER_P_STATE           States[DXGK_MAX_P_STATES];
  DXGK_POWER_COMPONENT_P_FLAGS Flags;
} DXGK_POWER_P_COMPONENT;
```

<a name="members"></a>成员
-------

**StateCount**

**状态**

**标记**

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>最低受支持的客户端</p></td>
<td align="left"><p>Windows 8.1</p></td>
</tr>
<tr class="even">
<td align="left"><p>最低受支持的服务器</p></td>
<td align="left"><p>Windows Server 2012 R2</p></td>
</tr>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">D3dkmddi (包含 D3dkmddi) </td>
</tr>
</tbody>
</table>

 

 





