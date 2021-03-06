---
title: KSPROPERTY \_ DVDCOPY \_ 区域
description: KSPROPERTY \_ DVDCOPY \_ region 属性根据语言限制指定 DVD 复制保护区域。
ms.assetid: b0ad355b-607f-43c5-9959-a309c6c63259
keywords:
- KSPROPERTY_DVDCOPY_REGION 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_DVDCOPY_REGION
api_location:
- ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: f248bdf33d7d0d46984a99f6fabfe80f40075bd8
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90103122"
---
# <a name="ksproperty_dvdcopy_region"></a>KSPROPERTY \_ DVDCOPY \_ 区域


KSPROPERTY \_ DVDCOPY \_ region 属性根据语言限制指定 DVD 复制保护区域。

## <span id="ddk_ksproperty_dvdcopy_region_ks"></span><span id="DDK_KSPROPERTY_DVDCOPY_REGION_KS"></span>


### <a name="usage-summary-table"></a>使用情况摘要表

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>获取</th>
<th>设置</th>
<th>目标</th>
<th>属性描述符类型</th>
<th>属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>是</p></td>
<td><p>否</p></td>
<td><p>Pin</p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)"><strong>KSPROPERTY</strong></a></p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-_ks_dvdcopy_region" data-raw-source="[&lt;strong&gt;KS_DVDCOPY_REGION&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-_ks_dvdcopy_region)"><strong>KS_DVDCOPY_REGION</strong></a></p></td>
</tr>
</tbody>
</table>

 

 (操作数据) 的属性值是一个 KS \_ DVDCOPY \_ 区域结构，用于描述民族或语言的区域代码。

<a name="remarks"></a>备注
-------

有关语言限制的详细信息，请参阅 [Dvd 实行](./dvd-regionalization.md) 和 [dvd 版权保护](./dvd-copyright-protection.md)。

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
<td>Ksmedia (包含 Ksmedia) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**KS \_ DVDCOPY \_ 区域**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-_ks_dvdcopy_region)

