---
title: D3DKMT \_ OUTPUTDUPL \_ 元数据结构
description: 了解 D3DKMT \_ OUTPUTDUPL \_ 元数据结构，该结构已保留供系统使用。 请勿在您的驱动程序中使用。
ms.assetid: abf4f00a-05bb-48f6-989e-f1b453fb0708
keywords:
- D3DKMT_OUTPUTDUPL_METADATA 结构显示设备
topic_type:
- apiref
api_name:
- D3DKMT_OUTPUTDUPL_METADATA
api_location:
- D3dkmthk.h
api_type:
- HeaderDef
ms.date: 01/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 3e67a8379c48f6d23708477ce84f54cba36e56b0
ms.sourcegitcommit: fc94eb0d5a41ef81c1b3ab91ad725386db0be0c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2020
ms.locfileid: "91603664"
---
# <a name="d3dkmt_outputdupl_metadata-structure"></a>D3DKMT \_ OUTPUTDUPL \_ 元数据结构


预留给系统使用。 请勿在您的驱动程序中使用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef struct _D3DKMT_OUTPUTDUPL_METADATA {
  D3DKMT_HANDLE                  hAdapter;
  D3DDDI_VIDEO_PRESENT_SOURCE_ID VidPnSourceId;
  D3DKMT_OUTPUTDUPL_METADATATYPE Type;
  UINT                           BufferSizeSupplied;
  PVOID                          pBuffer;
  UINT                           BufferSizeRequired;
} D3DKMT_OUTPUTDUPL_METADATA;
```

<a name="members"></a>成员
-------

**hAdapter**

**VidPnSourceId**

**类型**

**BufferSizeSupplied**

**pBuffer**

**BufferSizeRequired**

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
<td align="left">D3dkmthk (包含 D3dkmthk) </td>
</tr>
</tbody>
</table>

 

 





