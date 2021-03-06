---
title: 'Irql \_ IrqlSetting \_ 函数规则 (ndis) '
description: Irql \_ IrqlSetting \_ 函数规则指定必须在正确的 Irql 级别调用 NDIS 中断宏。
ms.assetid: 47e62c7c-bd43-4b4a-b7d6-3f64a4b8a6c8
ms.date: 05/21/2018
keywords:
- 'Irql_IrqlSetting_Function 规则 (ndis) '
topic_type:
- apiref
api_name:
- Irql_IrqlSetting_Function
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 9d7e7ad97fae44aa7b99d161ed89ea22d46d7843
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104736"
---
# <a name="irql_irqlsetting_function-rule-ndis"></a>Irql \_ IrqlSetting \_ 函数规则 (ndis) 


Irql \_ IrqlSetting \_ 函数规则指定必须在正确的 Irql 级别调用 NDIS 中断宏。

此规则验证以下 NDIS 宏：

**NDIS \_低 \_ IRQL** 
 **NDIS \_ 引发 \_ IRQL \_ 以 \_ 调度**

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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>Irql_IrqlSetting_Function</strong> 规则。</p>
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

[**NDIS \_低 \_ IRQL**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndis_lower_irql) 
 [**NDIS \_ 引发 \_ IRQL \_ 以 \_ 调度**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndis_raise_irql_to_dispatch)