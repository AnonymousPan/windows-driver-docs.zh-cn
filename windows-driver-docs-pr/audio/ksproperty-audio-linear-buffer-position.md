---
title: KSPROPERTY\_音频\_线性\_缓冲区\_位置
description: KSPROPERTY\_音频\_线性\_缓冲区\_属性请求检索一个数字，表示从音频缓冲区，DMA 具有提取自流开始后的字节数的位置。
ms.assetid: 08CC3164-2B8F-4368-8A34-6F8954992D3A
keywords:
- KSPROPERTY_AUDIO_LINEAR_BUFFER_POSITION 音频设备
topic_type:
- apiref
api_name:
- KSPROPERTY_AUDIO_LINEAR_BUFFER_POSITION
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 964f30dc61310665aee9875ffda0cd4066425477
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63333018"
---
# <a name="kspropertyaudiolinearbufferposition"></a>KSPROPERTY\_音频\_线性\_缓冲区\_位置


KSPROPERTY\_音频\_线性\_缓冲区\_属性请求检索一个数字，表示从音频缓冲区，DMA 具有提取自流开始后的字节数的位置。

### <a name="span-idusagesummarytablespanspan-idusagesummarytablespanspan-idusagesummarytablespanusage-summary-table"></a><span id="Usage_Summary_Table"></span><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>使用率摘要表

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
<th align="left">Get</th>
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
<td align="left"><p>通过 Pin 实例的节点</p></td>
<td align="left"><p>KSP_NODE</p></td>
<td align="left"><p>ULONGULONG</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值

KSPROPERTY\_音频\_线性\_缓冲区\_位置属性请求将返回状态\_成功以指示已成功完成。 否则，请求将返回相应的错误状态代码。

<a name="remarks"></a>备注
-------

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>Windows 8</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">Ksmedia.h</td>
</tr>
</tbody>
</table>

 

 





