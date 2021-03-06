---
title: CoNDIS 客户端注册
description: CoNDIS 客户端注册
ms.assetid: 335dd117-f6c8-4416-8527-ff64c1a5f3ee
keywords:
- 客户端注册 WDK CoNDIS
- 注册入口点
- 入口点 WDK 网络
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 4938719e9b2b43a17abfe5a3363cce76ddfc58d8
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89210789"
---
# <a name="condis-client-registration"></a>CoNDIS 客户端注册





CoNDIS 客户端像其他协议驱动程序一样初始化，还必须注册其他 CoNDIS 入口点。 有关协议驱动程序初始化的一般信息，请参阅 [初始化协议驱动程序](initializing-a-protocol-driver.md)。

若要注册*ProtocolXxx*函数的 CoNDIS 入口点，CoNDIS 客户端从[*ProtocolSetOptions*](/windows-hardware/drivers/ddi/ndis/nc-ndis-set_options)函数调用[**NdisSetOptionalHandlers**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndissetoptionalhandlers)函数。 在*ProtocolSetOptions*中，所有 CoNDIS 协议驱动程序初始化[**NDIS \_ 协议 \_ 共同 \_ 特征**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_protocol_co_characteristics)结构，并将其传递到**NdisSetOptionalHandlers**的*OptionalHandlers*参数。

若要为 CoNDIS 客户端指定入口点，协议驱动程序将初始化[**NDIS \_ 共同 \_ 客户端 \_ 可选 \_ 处理程序**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_co_client_optional_handlers)结构，并将其传递到**NdisSetOptionalHandlers**的*OptionalHandlers*参数。

有关配置可选协议驱动程序服务的详细信息，请参阅 [配置可选的协议驱动程序服务](configuring-optional-protocol-driver-services.md)。

 

