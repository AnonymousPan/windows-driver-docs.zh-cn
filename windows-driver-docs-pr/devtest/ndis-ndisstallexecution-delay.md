---
title: 'NdisStallExecution \_ 延迟规则 (ndis) '
description: NdisStallExecution \_ 延迟规则指定绝不能使用大于50微秒的 MicrosecondsToStall 的值调用 NdisStallExecution。
ms.assetid: 4c9368d0-4da7-4adc-bc63-4f21af90b682
ms.date: 05/21/2018
keywords:
- 'NdisStallExecution_Delay 规则 (ndis) '
topic_type:
- apiref
api_name:
- NdisStallExecution_Delay
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 483c64d0ed6180677ead73daf020ddf7043092ba
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90101588"
---
# <a name="ndisstallexecution_delay-rule-ndis"></a>NdisStallExecution \_ 延迟规则 (ndis) 


NdisStallExecution \_ 延迟规则指定绝不能使用大于50微秒的*MicrosecondsToStall*的值调用**NdisStallExecution** 。

**驱动程序模型： NDIS**

<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在编译时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>NdisStallExecution_Delay</strong> 规则。</p>
使用以下步骤来运行代码分析：
<ol>
<li><a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](./using-static-driver-verifier-to-find-defects-in-drivers.md#preparing-your-source-code)">准备你的代码 (使用) 的角色类型声明。</a></li>
<li><a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](./using-static-driver-verifier-to-find-defects-in-drivers.md#running-static-driver-verifier)">运行静态驱动程序验证程序。</a></li>
<li><a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](./using-static-driver-verifier-to-find-defects-in-drivers.md#viewing-and-analyzing-the-results)">查看并分析结果。</a></li>
</ol>
<p>有关详细信息，请参阅 <a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](./using-static-driver-verifier-to-find-defects-in-drivers.md)">使用静态驱动程序验证器查找驱动程序中的缺陷</a>。</p></td>
</tr>
</tbody>
</table>

<a name="applies-to"></a>适用于
----------

[**NdisStallExecution**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisstallexecution)
