---
title: 中间驱动程序绑定操作
description: 中间驱动程序绑定操作
ms.assetid: 129a744c-d4d4-4741-9812-e76087c585fc
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 5bf98110c13cd88742f69b8cd2790e52143721ba
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89215646"
---
# <a name="intermediate-driver-binding-operations"></a>中间驱动程序绑定操作





当微型端口适配器可用时，NDIS 将调用可以绑定到该微型端口适配器的任何中间驱动程序的 [*ProtocolBindAdapterEx*](/windows-hardware/drivers/ddi/ndis/nc-ndis-protocol_bind_adapter_ex) 函数。

中间驱动程序必须提供 [绑定到适配器时](binding-to-an-adapter.md)所记录的协议绑定操作。

绑定时操作包括为绑定分配和初始化适配器特定的上下文区域，初始化任何虚拟微型端口，以及调用 [**NdisOpenAdapterEx**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisopenadapterex) 以绑定到适配器。

中间驱动程序无需为每个绑定分配单独的 [**网络 \_ 缓冲区 \_ 列表**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) 结构池。 \_ \_ 仅当驱动程序设计要求它分配其自己的结构时，才需要中间驱动程序才能分配网络缓冲区列表结构池。 否则，驱动程序可以只传递从其他驱动程序接收的结构。 此类驱动程序应为发送和接收分配不同的池。

有关分配和管理网络数据的要求的信息，请参阅 [中间驱动程序网络数据管理](intermediate-driver-network-data-management.md)。

 

