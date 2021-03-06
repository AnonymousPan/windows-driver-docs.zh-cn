---
title: 'Irql \_ NetBuffer \_ 函数规则 (ndis) '
description: Irql \_ NetBuffer \_ 函数规则指定 \_ 必须在正确的 Irql 级别调用与网络缓冲区相关的函数。
ms.assetid: e3b43ba1-3b58-4bc8-9d90-7be31c9e0a09
ms.date: 05/21/2018
keywords:
- 'Irql_NetBuffer_Function 规则 (ndis) '
topic_type:
- apiref
api_name:
- Irql_NetBuffer_Function
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 25d8d74446b49360cd81c50f4d369dd035ad8e0d
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104714"
---
# <a name="irql_netbuffer_function-rule-ndis"></a>Irql \_ NetBuffer \_ 函数规则 (ndis) 


Irql \_ NetBuffer \_ 函数规则指定 \_ 必须在正确的 Irql 级别调用与网络缓冲区相关的函数。

此规则验证以下 NDIS 函数：

**NdisAdvanceNetBufferDataStart** 
**disAdvanceNetBufferListDataStart** 
**NdisAllocateCloneNetBufferList** 
**NdisAllocateFragmentNetBufferList** 
**NdisAllocateMdl** 
**NdisAllocateNetBuffer** 
**NdisAllocateNetBufferAndNetBufferList** 
**NdisAllocateNetBufferList** 
**NdisAllocateNetBufferListContext** 
**NdisAllocateNetBufferListPool** 
**NdisAllocateNetBufferMdlAndData** 
**NdisAllocateNetBufferPool** 
**NdisAllocateReassembledNetBufferList** 
**NdisCopyFromNetBufferToNetBuffer** 
**NdisCopyReceiveNetBufferListInfo** 
**NdisCopySendNetBufferListInfo** 
**NdisFreeCloneNetBufferList** 
**NdisFreeFragmentNetBufferList** 
**NdisFreeMdl** 
**NdisFreeNetBuffer** 
**NdisFreeNetBufferList** 
**NdisFreeNetBufferListContext** 
**NdisFreeNetBufferListPool** 
**NdisFreeNetBufferPool** 
**NdisFreeReassembledNetBufferList** 
**NdisGetDataBuffer** 
**NdisGetMdlPhysicalArraySize** 
**NdisGetPoolFromNetBuffer** 
**NdisGetPoolFromNetBufferList** 
**NdisQueryMdl** 
**NdisQueryMdlOffset** 
**NdisQueryNetBufferPhysicalCount** 
**NdisRetreatNetBufferDataStart** 
**NdisRetreatNetBufferListDataStart**

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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>Irql_NetBuffer_Function</strong> 规则。</p>
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

[**NdisAdvanceNetBufferDataStart**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisadvancenetbufferdatastart) 
[**NdisAdvanceNetBufferListDataStart**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisadvancenetbufferlistdatastart) 
[**NdisAllocateCloneNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocateclonenetbufferlist) 
[**NdisAllocateFragmentNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatefragmentnetbufferlist) 
[**NdisAllocateMdl**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatemdl) 
[**NdisAllocateNetBuffer**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbuffer) 
[**NdisAllocateNetBufferAndNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferandnetbufferlist) 
[**NdisAllocateNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlist) 
[**NdisAllocateNetBufferListContext**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistcontext) 
[**NdisAllocateNetBufferListPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistpool) 
[**NdisAllocateNetBufferMdlAndData**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbuffermdlanddata) 
[**NdisAllocateNetBufferPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferpool) 
[**NdisAllocateReassembledNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatereassemblednetbufferlist) 
[**NdisCopyFromNetBufferToNetBuffer**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscopyfromnetbuffertonetbuffer) 
[**NdisCopyReceiveNetBufferListInfo**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscopyreceivenetbufferlistinfo) 
[**NdisCopySendNetBufferListInfo**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscopysendnetbufferlistinfo) 
[**NdisFreeCloneNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreeclonenetbufferlist) 
[**NdisFreeFragmentNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreefragmentnetbufferlist) 
[**NdisFreeMdl**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreemdl) 
[**NdisFreeNetBuffer**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbuffer) 
[**NdisFreeNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlist) 
[**NdisFreeNetBufferListContext**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlistcontext) 
[**NdisFreeNetBufferListPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlistpool) 
[**NdisFreeNetBufferPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferpool) 
[**NdisFreeReassembledNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreereassemblednetbufferlist) 
[**NdisGetDataBuffer**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisgetdatabuffer) 
[**NdisGetMdlPhysicalArraySize**](../network/ndisgetmdlphysicalarraysize.md) 
[**NdisGetPoolFromNetBuffer**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisgetpoolfromnetbuffer) 
[**NdisGetPoolFromNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisgetpoolfromnetbufferlist) 
[**NdisQueryMdl**](../network/ndisquerymdl.md) 
[**NdisQueryMdlOffset**](../network/ndisquerymdloffset.md) 
[**NdisQueryNetBufferPhysicalCount**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisquerynetbufferphysicalcount) 
[**NdisRetreatNetBufferDataStart**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisretreatnetbufferdatastart) 
[**NdisRetreatNetBufferListDataStart**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisretreatnetbufferlistdatastart)