---
title: rdmsr（读取 MSR）
description: Rdmsr 命令从指定的地址读取 (MSR) 值的模型特定寄存器。
ms.assetid: 693f1be5-f215-4719-ae6f-30e367cefd77
keywords:
- rdmsr (读取 MSR) Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- rdmsr (Read MSR)
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 5130d612f93702490915bd942c3b5f874fee4693
ms.sourcegitcommit: bb3b62a57ba3aea4a0adeefd2d81993367b7b334
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2020
ms.locfileid: "88148405"
---
# <a name="rdmsr-read-msr"></a>rdmsr（读取 MSR）


**Rdmsr**命令从指定的地址读取[ (MSR) 值的模型特定寄存器](other-data-spaces.md)。

```dbgcmd
rdmsr Address 
```

## <a name="span-idddk_cmd_read_msr_dbgspanspan-idddk_cmd_read_msr_dbgspanparameters"></a><span id="ddk_cmd_read_msr_dbg"></span><span id="DDK_CMD_READ_MSR_DBG"></span>参数


<span id="_______Address______"></span><span id="_______address______"></span><span id="_______ADDRESS______"></span>*地址*   
指定 MSR 的地址。

### <a name="span-idenvironmentspanspan-idenvironmentspanspan-idenvironmentspanenvironment"></a><span id="Environment"></span><span id="environment"></span><span id="ENVIRONMENT"></span>环境

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>交货</strong></p></td>
<td align="left"><p>仅限内核模式</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>目标</strong></p></td>
<td align="left"><p>仅限实时调试</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>平台</strong></p></td>
<td align="left"><p>All</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

**Rdmsr**命令可在基于 x86 和基于 x64 的平台上显示 MSR。 MSR 定义是特定于平台的。

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[**wrmsr（写入 MSR）**](wrmsr--write-msr-.md)

 

 






