---
title: NDIS 接口信息
description: NDIS 接口信息
ms.assetid: 35187fda-a239-4801-b0be-53fcbee7d24e
keywords:
- 管理信息基本 WDK 网络
- Mib WDK 网络
- NDIS WDK，接口
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: fc2ef6a780972a1dc36d58fb93fa5cc35365a63c
ms.sourcegitcommit: b84d760d4b45795be12e625db1d5a4167dc2c9ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90716702"
---
# <a name="ndis-interface-information"></a>NDIS 接口信息





用于查询 NDIS 管理信息库 (Mib) 的标准化接口，使生成的驱动程序和用户模式应用程序能够更轻松地查询有关网络接口的信息。 MIB 客户端调用 NDIS 提供的函数以从基础 NDIS 接口提供程序请求信息。 这会导致 NDIS 发出 OID 请求来检索信息。 为了向客户端提供信息，NDIS 调用了客户端向 NDIS 注册的回调函数。

有关 NDIS 网络接口服务的详细信息，请参阅 [Ndis 网络接口](/windows-hardware/drivers/ddi/_netvista/)。

NDIS 为管理检测 (WMI) 提供增强的支持。 有关 NDIS 6.0 对 WMI 的支持的详细信息，请参阅 [对 wmi 的 Ndis 支持](ndis-support-for-wmi.md)。

## <a name="related-topics"></a>相关主题


[**NDIS \_ 接口 \_ 信息**](/windows/win32/api/ifdef/ns-ifdef-ndis_interface_information)

 

