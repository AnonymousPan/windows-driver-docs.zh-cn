---
title: KSPROPERTY \_ 连接 \_ STARTAT
description: KSPROPERTY \_ 连接 \_ STARTAT 是一个可选属性，该属性由支持在指定事件发生时启动的筛选器实现。
ms.assetid: fcf76316-4016-4218-8530-5ef79794769a
keywords:
- KSPROPERTY_CONNECTION_STARTAT 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_CONNECTION_STARTAT
api_location:
- ks.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 889338ca11f14215bf6f265fcd115d475d22843d
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90102762"
---
# <a name="ksproperty_connection_startat"></a>KSPROPERTY \_ 连接 \_ STARTAT


KSPROPERTY \_ 连接 \_ STARTAT 是一个可选属性，该属性由支持在指定事件发生时启动的筛选器实现。

## <span id="ddk_ksproperty_connection_startat_ks"></span><span id="DDK_KSPROPERTY_CONNECTION_STARTAT_KS"></span>


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
<td><p>筛选器</p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)"><strong>KSPROPERTY</strong></a></p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ks/ns-ks-ksrelativeevent" data-raw-source="[&lt;strong&gt;KSRELATIVEEVENT&lt;/strong&gt;](/windows-hardware/drivers/ddi/ks/ns-ks-ksrelativeevent)"><strong>KSRELATIVEEVENT</strong></a></p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

仅当 pin 处于暂停状态时，才应请求此属性，以将 pin 转换为运行状态。

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
<td>Ks (包含 Ks .h) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**KSRELATIVEEVENT**](/windows-hardware/drivers/ddi/ks/ns-ks-ksrelativeevent)

[**KSEVENT \_ 项**](/windows-hardware/drivers/ddi/ks/ns-ks-ksevent_item)

