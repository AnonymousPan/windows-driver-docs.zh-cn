---
title: 从 CoNDIS 驱动程序发送 NET_BUFFER 结构
description: 从 CoNDIS 驱动程序发送 NET_BUFFER 结构
ms.assetid: 63bca3f0-b598-4006-bfd0-6df32ab2cbe7
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f49a58bb9d2e7a8880dbd2a1021e27597076034d
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89212803"
---
# <a name="sending-net_buffer-structures-from-condis-drivers"></a>\_从 CoNDIS 驱动程序发送网络缓冲区结构





下图说明了一个基本的 CoNDIS 发送操作，该操作涉及一个协议驱动程序、NDIS 和一个微型端口驱动程序。

![说明基本 condis 发送操作（涉及协议驱动程序、ndis 和微型端口驱动程序）的示意图](images/netbuffercosend.png)

如上图所示，协议驱动程序调用 [**NdisCoSendNetBufferLists**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscosendnetbufferlists) 函数以将虚拟连接上的 [**网络 \_ 缓冲区 \_ 列表**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) 结构发送 (VC) 。 然后，NDIS 调用微型端口驱动程序的 [**MiniportCoSendNetBufferLists**](/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_send_net_buffer_lists) 函数将网络 \_ 缓冲区 \_ 列表结构转发到基础微型端口驱动程序。

所有 \_ 基于网络缓冲区的发送操作都是异步的。 因此，微型端口驱动程序始终调用 [**NdisMCoSendNetBufferListsComplete**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismcosendnetbufferlistscomplete) 函数，并在发送完数据后提供相应的状态代码。 小型端口驱动程序可以针对每个网络 \_ 缓冲区 \_ 列表结构（独立于其他网络 \_ 缓冲区 \_ 列表结构）完成发送操作。 每次微型小型驱动程序调用**NdisMCoSendNetBufferListsComplete**时，NDIS 都调用协议驱动程序的[**ProtocolCoSendNetBufferListsComplete**](/windows-hardware/drivers/ddi/ndis/nc-ndis-protocol_co_send_net_buffer_lists_complete)函数。

当 NDIS 调用了协议驱动程序的*ProtocolCoSendNetBufferListsComplete*函数时，协议驱动程序可以立即回收[**网络 \_ 缓冲区 \_ 列表**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list)结构和所有关联的结构和数据的所有权。

微型端口驱动程序或 NDIS 可以 \_ \_ 按任意顺序返回网络缓冲区列表结构。 但会保证协议驱动程序不会修改附加到每个网络缓冲区列表结构的 [**网络 \_ 缓冲区**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer) 的列表 \_ \_ 。

协议驱动程序将[**网络 \_ 缓冲区 \_ 列表**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list)结构中的**SourceHandle**成员设置为与**NdisCoSendNetBufferLists**的*NdisVcHandle*参数相同的值。 NDIS 使用 **SourceHandle** 成员将网络 \_ 缓冲区 \_ 列表结构返回到发送网络 \_ 缓冲区列表结构的协议驱动程序 \_ 。

中间驱动程序还将网络缓冲区列表结构中的 **SourceHandle** 成员设置 \_ \_ 为 *NdisVcHandle* 值。 如果中间驱动程序转发发送请求，则驱动程序必须保存过量驱动程序在写入**SourceHandle**成员之前提供的**SourceHandle**值。 当 NDIS \_ \_ 向中间驱动程序返回已转发的网络缓冲区列表结构时，中间驱动程序必须还原它保存的 **SourceHandle** 。

协议驱动程序可以通过使用与无连接驱动程序相同的机制来取消发送请求。 有关取消发送请求的详细信息，请参阅 [取消发送操作](canceling-a-send-operation.md)。

 

