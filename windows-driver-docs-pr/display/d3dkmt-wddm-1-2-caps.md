---
title: D3DKMT \_ WDDM \_ 1 \_ 2 \_ 大写结构
description: 了解 D3DKMT \_ WDDM \_ 1 \_ 2 \_ cap 结构，该结构保留供系统使用。 请勿在您的驱动程序中使用。
ms.assetid: 0cd26fad-4772-4631-81fc-da2ddb7dc9a1
keywords:
- D3DKMT_WDDM_1_2_CAPS 结构显示设备
topic_type:
- apiref
api_name:
- D3DKMT_WDDM_1_2_CAPS
api_location:
- D3dkmdt.h
api_type:
- HeaderDef
ms.date: 01/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: c9b2951216d73921585b1ee51690d970c6e2275b
ms.sourcegitcommit: fc94eb0d5a41ef81c1b3ab91ad725386db0be0c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2020
ms.locfileid: "91603584"
---
# <a name="d3dkmt_wddm_1_2_caps-structure"></a>D3DKMT \_ WDDM \_ 1 \_ 2 \_ 大写结构


预留给系统使用。 请勿在您的驱动程序中使用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef struct _D3DKMT_WDDM_1_2_CAPS {
  D3DKMDT_PREEMPTION_CAPS PreemptionCaps;
  union {
    struct {
      UINT SupportNonVGA  :1;
      UINT SupportSmoothRotation  :1;
      UINT SupportPerEngineTDR  :1;
      UINT SupportKernelModeCommandBuffer  :1;
      UINT SupportCCD  :1;
      UINT SupportSoftwareDeviceBitmaps  :1;
      UINT SupportGammaRamp  :1;
      UINT SupportHWCursor  :1;
      UINT SupportHWVSync  :1;
      UINT SupportSurpriseRemovalInHibernation  :1;
      UINT Reserved  :22;
    };
    UINT   Value;
  };
} D3DKMT_WDDM_1_2_CAPS;
```

<a name="members"></a>成员
-------

**PreemptionCaps**

**SupportNonVGA**

**SupportSmoothRotation**

**SupportPerEngineTDR**

**SupportKernelModeCommandBuffer**

**SupportCCD**

**SupportSoftwareDeviceBitmaps**

**SupportGammaRamp**

**SupportHWCursor**

**SupportHWVSync**

**SupportSurpriseRemovalInHibernation**

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
<td align="left"><p>Windows 8</p></td>
</tr>
<tr class="even">
<td align="left"><p>最低受支持的服务器</p></td>
<td align="left"><p>Windows Server 2012</p></td>
</tr>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">D3dkmdt (包含 D3dkmdt) </td>
</tr>
</tbody>
</table>

 

 





