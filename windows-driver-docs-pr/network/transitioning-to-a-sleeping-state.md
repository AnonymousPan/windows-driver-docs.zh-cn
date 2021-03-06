---
title: 转换到睡眠状态
description: 转换到睡眠状态
ms.assetid: cea326dd-7235-41a3-ad37-19549533a8dd
keywords:
- 网络接口卡 WDK 网络，过渡电源状态
- Nic WDK 网络，过渡电源状态
- 睡眠状态 WDK 网络
- 电源管理 WDK NDIS 微型端口，转换电源状态
- 设备电源状态 WDK 网络
- 电源状态 WDK 网络
- 转换电源状态 WDK 网络
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: a6ac4d6e9c4b1daf7ba9c62ffb07572feba092a0
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89215809"
---
# <a name="transitioning-to-a-sleeping-state"></a>转换到睡眠状态





如果微型端口驱动程序支持唤醒事件，NDIS 会向该驱动程序发送 [oid \_ pnp \_ ENABLE \_ 唤醒 \_ ](./oid-pnp-enable-wake-up.md) 请求，然后再发送 [OID \_ pnp \_ 设置 \_ 电源](./oid-pnp-set-power.md) 请求。 有关详细信息，请参阅 [启用唤醒事件](enabling-wake-up-events.md)。 微型端口驱动程序不得使 OID \_ PNP \_ 设置 \_ 电源请求失败。

在返回 NDIS \_ 状态 \_ "成功" 以响应 OID \_ PNP \_ 设置 \_ 电源请求之前，微型端口驱动程序必须：

-   执行准备网络适配器以进入睡眠状态所需的与设备相关的操作。

-   保存任何数据包筛选器、多播地址、当前 MAC 地址、唤醒模式以及网络适配器无法在休眠状态中保留的任何其他硬件上下文。

-   禁用中断和网络适配器的 DMA 引擎。 当总线驱动程序将网络适配器设置为 D3 状态后，微型端口驱动程序无法访问网络适配器硬件。

 

