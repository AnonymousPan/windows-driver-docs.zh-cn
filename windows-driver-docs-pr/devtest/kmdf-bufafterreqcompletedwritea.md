---
title: 'BufAfterReqCompletedWriteA 规则 (kmdf) '
description: BufAfterReqCompletedWriteA 规则指定在 EvtIoWrite 回调函数中，在 i/o 请求完成后，无法访问检索到的 i/o 请求缓冲区。
ms.assetid: 4b7cd08f-8280-4bb6-be00-955ad8d2d015
ms.date: 05/21/2018
keywords:
- 'BufAfterReqCompletedWriteA 规则 (kmdf) '
topic_type:
- apiref
api_name:
- BufAfterReqCompletedWriteA
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 3cfdca43ca859874541b83421bdcb43bd326e8c7
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104718"
---
# <a name="bufafterreqcompletedwritea-rule-kmdf"></a>BufAfterReqCompletedWriteA 规则 (kmdf) 


BufAfterReqCompletedWriteA 规则指定在 [*EvtIoWrite*](/windows-hardware/drivers/ddi/wdfio/nc-wdfio-evt_wdf_io_queue_io_write) 回调函数中，在 i/o 请求完成后，无法访问检索到的 i/o 请求缓冲区。

在驱动程序的 **EvtIoWrite** 回调函数中，通过调用检索到的请求缓冲区

在 i/o 请求上调用[**WdfRequestComplete**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcomplete)、 [**WdfRequestCompleteWithInformation**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithinformation)或[**WdfRequestCompleteWithPriorityBoost**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithpriorityboost)后，无法访问[**WdfRequestRetrieveInputBuffer**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestretrieveinputbuffer)或[**WdfRequestRetrieveUnsafeUserInputBuffer**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestretrieveunsafeuserinputbuffer) 。

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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>BufAfterReqCompletedWriteA</strong> 规则。</p>
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

[**WDF \_内存 \_ 描述符 \_ INIT \_ BUFFER**](/windows-hardware/drivers/ddi/wdfmemory/nf-wdfmemory-wdf_memory_descriptor_init_buffer) 
 [**WdfMemoryAssignBuffer**](/windows-hardware/drivers/ddi/wdfmemory/nf-wdfmemory-wdfmemoryassignbuffer) 
 [**WdfMemoryCopyFromBuffer**](/windows-hardware/drivers/ddi/wdfmemory/nf-wdfmemory-wdfmemorycopyfrombuffer) 
 [**WdfMemoryCopyToBuffer**](/windows-hardware/drivers/ddi/wdfmemory/nf-wdfmemory-wdfmemorycopytobuffer) 
 [**WdfMemoryCreatePreallocated**](/windows-hardware/drivers/ddi/wdfmemory/nf-wdfmemory-wdfmemorycreatepreallocated) 
 [**WdfRequestComplete**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcomplete) 
 [**WdfRequestCompleteWithInformation**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithinformation) 
 [**WdfRequestCompleteWithPriorityBoost**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithpriorityboost) 
 [**WdfRequestRetrieveInputBuffer**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestretrieveinputbuffer) 
 [**WdfRequestRetrieveUnsafeUserInputBuffer**](/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestretrieveunsafeuserinputbuffer) 
 [**RtlCompareMemory**](/windows-hardware/drivers/ddi/wdm/nf-wdm-rtlcomparememory) 
 [**RtlMoveMemory**](/windows-hardware/drivers/ddi/wdm/nf-wdm-rtlmovememory) 
 [**RtlZeroMemory**](/windows-hardware/drivers/ddi/wdm/nf-wdm-rtlzeromemory) 
 [**ZwReadFile**](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntreadfile) ZwReadFile
