---
title: KSPROPERTY \_ VPCONFIG \_ SURFACEPARAMS
description: KSPROPERTY \_ VPCONFIG \_ SURFACEPARAMS 属性指定视频端口图面设置。
ms.assetid: cb8ebaea-4667-43c6-964f-89d55d4ff9be
keywords:
- KSPROPERTY_VPCONFIG_SURFACEPARAMS 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_VPCONFIG_SURFACEPARAMS
api_location:
- ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 1b64d2f00a6de6330ea728c301e6d1dc2d0623b0
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89191401"
---
# <a name="ksproperty_vpconfig_surfaceparams"></a>KSPROPERTY \_ VPCONFIG \_ SURFACEPARAMS


KSPROPERTY \_ VPCONFIG \_ SURFACEPARAMS 属性指定视频端口图面设置。

## <span id="ddk_ksproperty_vpconfig_surfaceparams_ks"></span><span id="DDK_KSPROPERTY_VPCONFIG_SURFACEPARAMS_KS"></span>


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
<td><p>否</p></td>
<td><p>是</p></td>
<td><p>Pin</p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)"><strong>KSPROPERTY</strong></a></p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksvpsurfaceparams" data-raw-source="[&lt;strong&gt;KSVPSURFACEPARAMS&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksvpsurfaceparams)"><strong>KSVPSURFACEPARAMS</strong></a></p></td>
</tr>
</tbody>
</table>

 

 (操作数据) 的属性值是描述 surface 螺距和 *x* 和 *y* 原点的 KSVPSURFACEPARAMS 结构。

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


[**KSPROPERTY**](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)

[**KSVPSURFACEPARAMS**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksvpsurfaceparams)

 

