---
title: KSPROPERTY \_ E-ac3 \_ 位 \_ 流 \_ 模式
description: KSPROPERTY \_ E-ac3 \_ 位 \_ 流 \_ 模式属性指定位流模式，这是编码为 AC 3 流的音频服务的类型。
ms.assetid: ee3705f5-f16d-4f5e-a551-bea8986d88b6
keywords:
- KSPROPERTY_AC3_BIT_STREAM_MODE 音频设备
topic_type:
- apiref
api_name:
- KSPROPERTY_AC3_BIT_STREAM_MODE
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: d401a2eb9a6a4b0fff1e680cfc4b932b463522ef
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90102350"
---
# <a name="ksproperty_ac3_bit_stream_mode"></a>KSPROPERTY \_ E-ac3 \_ 位 \_ 流 \_ 模式


KSPROPERTY \_ E-ac3 \_ 位 \_ 流 \_ 模式属性指定位流模式，这是编码为 AC 3 流的音频服务的类型。

## <span id="ddk_ksproperty_ac3_bit_stream_mode_ks"></span><span id="DDK_KSPROPERTY_AC3_BIT_STREAM_MODE_KS"></span>


### <a name="span-idusage_summary_tablespanspan-idusage_summary_tablespanspan-idusage_summary_tablespanusage-summary-table"></a><span id="Usage_Summary_Table"></span><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>使用情况摘要表

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
<th align="left">获取</th>
<th align="left">设置</th>
<th align="left">目标</th>
<th align="left">属性描述符类型</th>
<th align="left">属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>Pin</p></td>
<td align="left"><p><a href="/previous-versions/ff564262(v=vs.85)" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](/previous-versions/ff564262(v=vs.85))"><strong>KSPROPERTY</strong></a></p></td>
<td align="left"><p><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksac3_bit_stream_mode" data-raw-source="[&lt;strong&gt;KSAC3_BIT_STREAM_MODE&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksac3_bit_stream_mode)"><strong>KSAC3_BIT_STREAM_MODE</strong></a></p></td>
</tr>
</tbody>
</table>

 

 (操作数据) 的属性值是 \_ \_ \_ 指定位流模式的 KSAC3 位流模式结构。

### <a name="span-idreturn_valuespanspan-idreturn_valuespanspan-idreturn_valuespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值

KSPROPERTY \_ E-ac3 \_ 位 \_ 流 \_ 模式属性请求返回状态 \_ SUCCESS 以指示已成功完成。 否则，请求将返回相应的错误状态代码。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">Ksmedia (包含 Ksmedia) </td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[**KSPROPERTY**](/previous-versions/ff564262(v=vs.85))

[**KSAC3 \_ 位 \_ 流 \_ 模式**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksac3_bit_stream_mode)

