---
title: 'NoCancelFromEvtSurpriseRemove 规则 (kmdf) '
description: NoCancelFromEvtSurpriseRemove 规则指定 WDF 驱动程序不应取消来自 EvtDeviceSurpriseRemoval 回调函数的请求，而应使用自托管 i/o 回调函数。
ms.assetid: 15C95BD4-6D19-4CCA-9B2E-679B2F3058F1
ms.date: 05/21/2018
keywords:
- 'NoCancelFromEvtSurpriseRemove 规则 (kmdf) '
topic_type:
- apiref
api_name:
- NoCancelFromEvtSurpriseRemove
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: c07da73b97a270128176509109b1ea28d493a715
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90103834"
---
# <a name="nocancelfromevtsurpriseremove-rule-kmdf"></a>NoCancelFromEvtSurpriseRemove 规则 (kmdf) 


**NoCancelFromEvtSurpriseRemove**规则指定 WDF 驱动程序不应取消来自[*EvtDeviceSurpriseRemoval*](/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_surprise_removal)回调函数的请求，而应使用自托管 i/o 回调函数。 *EvtDeviceSurpriseRemoval* 回调函数未与电源线路径同步。

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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>NoCancelFromEvtSurpriseRemove</strong> 规则。</p>
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

[**WdfIoQueueDrain**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuedrain) 
[**WdfIoQueueDrainSynchronously**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuedrainsynchronously) 
[**WdfIoQueuePurge**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuepurge) 
[**WdfIoQueuePurgeSynchronously**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuepurgesynchronously) 
[**WdfIoQueueStop**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuestop) 
[**WdfIoQueueStopAndPurge**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuestopandpurge) 
[**WdfIoQueueStopAndPurgeSynchronously**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuestopandpurgesynchronously) 
[**WdfIoQueueStopSynchronously**](/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuestopsynchronously) 
[**WdfRequestComplete**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcomplete) 
[**WdfRequestCompleteWithInformation**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithinformation) 
[**WdfRequestCompleteWithPriorityBoost**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithpriorityboost)
