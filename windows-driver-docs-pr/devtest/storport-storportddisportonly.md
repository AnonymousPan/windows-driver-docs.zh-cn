---
title: 'StorPortDDIsPortOnly 规则 (storport) '
description: 此规则包含 StorPort 仅限 DDIs 的 (的列表，其中包含不应在 StorPort 微型端口中调用的互锁函数) 。
ms.assetid: 55922047-5029-4EB8-B363-61C098339F2E
ms.date: 05/21/2018
keywords:
- 'StorPortDDIsPortOnly 规则 (storport) '
topic_type:
- apiref
api_name:
- StorPortDDIsPortOnly
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 33593ef01a64cebced4d091a43f8acc35d641d48
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104042"
---
# <a name="storportddisportonly-rule-storport"></a>StorPortDDIsPortOnly 规则 (storport) 


此规则包含 StorPort 仅限 DDIs 的 (的列表，其中包含不应在 StorPort 微型端口中调用的互锁函数) 。

**驱动程序模型： Storport**

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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>StorPortDDIsPortOnly</strong> 规则。</p>
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

[**StorPortCompleteRequest**](/windows-hardware/drivers/ddi/storport/nf-storport-storportcompleterequest)
