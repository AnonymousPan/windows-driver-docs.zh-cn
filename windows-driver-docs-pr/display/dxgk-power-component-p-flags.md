---
title: DXGK \_ 电源 \_ 组件 \_ P \_ 标志结构
description: 了解 DXGK \_ POWER \_ 组件 \_ P \_ FLAGS 结构，它是为系统使用而保留的。 请勿在您的驱动程序中使用。
ms.assetid: 9A3C9821-7E98-4F9E-94EE-AF2C09C2A881
keywords:
- DXGK_POWER_COMPONENT_P_FLAGS 结构显示设备
topic_type:
- apiref
api_name:
- DXGK_POWER_COMPONENT_P_FLAGS
api_location:
- D3dkmddi.h
api_type:
- HeaderDef
ms.date: 01/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: af01b4e272bb912702968998d7551ae0cd19902f
ms.sourcegitcommit: fc94eb0d5a41ef81c1b3ab91ad725386db0be0c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2020
ms.locfileid: "91603582"
---
# <a name="dxgk_power_component_p_flags-structure"></a>DXGK \_ 电源 \_ 组件 \_ P \_ 标志结构


预留给系统使用。 请勿在您的驱动程序中使用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef struct _DXGK_POWER_COMPONENT_P_FLAGS {
  union {
    struct {
      UINT Reserved  :32;
    };
    UINT Value;
  };
} DXGK_POWER_COMPONENT_P_FLAGS;
```

<a name="members"></a>成员
-------

**保护**

**值**

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

 

 





