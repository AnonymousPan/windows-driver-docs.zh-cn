---
title: ReqSendWhileSpinlock 规则（kmdf）
description: ReqSendWhileSpinlock 规则指定在驱动程序持有旋转锁时不发送请求。
ms.assetid: f038f4ca-aa24-4df3-9c31-d8eec928c306
ms.date: 05/21/2018
keywords:
- ReqSendWhileSpinlock 规则（kmdf）
topic_type:
- apiref
api_name:
- ReqSendWhileSpinlock
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: d5c0b4b73da8efc15a53aae7db2004ac39de9b67
ms.sourcegitcommit: 82a9be3b3584f991e5121f8f46a972e04185fa52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85918217"
---
# <a name="reqsendwhilespinlock-rule-kmdf"></a>ReqSendWhileSpinlock 规则（kmdf）


**ReqSendWhileSpinlock**规则指定在驱动程序持有旋转锁时不发送请求。

如果驱动程序在包含旋转锁的情况下发送任何请求，则可能会导致死锁或与接收请求的低级驱动程序发生冲突，前提是该驱动程序还尝试获取锁或访问共享资源。

**驱动程序模型： KMDF**

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
<td align="left"><p>运行<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">静态驱动程序验证程序</a>并指定<strong>ReqSendWhileSpinlock</strong>规则。</p>
使用以下步骤来运行代码分析：
<ol>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code)">准备你的代码（使用角色类型声明）。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier)">运行静态驱动程序验证程序。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results)">查看并分析结果。</a></li>
</ol>
<p>有关详细信息，请参阅<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers)">使用静态驱动程序验证器查找驱动程序中的缺陷</a>。</p></td>
</tr>
</tbody>
</table>

<a name="applies-to"></a>适用于
----------

[**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) 
[**WdfSpinLockAcquire**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff550040(v=vs.85)) 
[**WdfSpinLockRelease**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff550044(v=vs.85)) 
[**KeAcquireSpinLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-keacquirespinlock) 
[**KeReleaseSpinLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-kereleasespinlock)另请参阅
--------

[完成 I/o 请求](https://docs.microsoft.com/windows-hardware/drivers/wdf/completing-i-o-requests) 
[同步取消和完成代码](https://docs.microsoft.com/windows-hardware/drivers/wdf/synchronizing-cancel-and-completion-code)
 

 





