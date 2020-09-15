---
title: KSPROPERTY \_ VIDEOPROCAMP \_ 伽玛
description: KSPROPERTY \_ VIDEOPROCAMP \_ 伽玛属性控制照相机的 gamma 设置。 此属性是可选的。
ms.assetid: 880f0895-6619-49ac-9753-e44b7eace83d
keywords:
- KSPROPERTY_VIDEOPROCAMP_GAMMA 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_VIDEOPROCAMP_GAMMA
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 178e27c3f1e28e44a3e8aa6dff2e2906c8a4cbde
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104664"
---
# <a name="ksproperty_videoprocamp_gamma"></a>KSPROPERTY \_ VIDEOPROCAMP \_ 伽玛


KSPROPERTY \_ VIDEOPROCAMP \_ 伽玛属性控制照相机的 gamma 设置。 此属性是可选的。

## <span id="ddk_ksproperty_videoprocamp_gamma_ks"></span><span id="DDK_KSPROPERTY_VIDEOPROCAMP_GAMMA_KS"></span>


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
<td><p>是</p></td>
<td><p>筛选器或节点</p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_videoprocamp_s" data-raw-source="[&lt;strong&gt;KSPROPERTY_VIDEOPROCAMP_S&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_videoprocamp_s)"><strong>KSPROPERTY_VIDEOPROCAMP_S</strong></a>或<a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_videoprocamp_node_s" data-raw-source="[&lt;strong&gt;KSPROPERTY_VIDEOPROCAMP_NODE_S&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_videoprocamp_node_s)"> <strong>KSPROPERTY_VIDEOPROCAMP_NODE_S</strong></a></p></td>
<td><p>LONG</p></td>
</tr>
</tbody>
</table>

 

 (操作数据) 的属性值是指定相机伽玛设置的 LONG 值。 伽玛设置的值用伽玛乘以100表示。

<a name="remarks"></a>备注
-------

KSPROPERTY **Value** \_ VIDEOPROCAMP S 结构的 Value 成员 \_ 指定伽玛设置。

每个视频捕获微型驱动程序都必须为此属性定义一个范围和默认值。 所需范围必须为1到500。 默认值通常为 100 (伽玛 = 1) 或 220 (伽玛 = 2.2) ，具体取决于显示介质和视频硬件。

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

[**KSPROPERTY \_ VIDEOPROCAMP \_ S**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_videoprocamp_s)

