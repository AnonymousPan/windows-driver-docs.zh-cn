---
title: 设备睡眠时将 I/O 请求排队
description: 设备睡眠时将 I/O 请求排队
ms.assetid: 8cc0cea0-e5be-4705-ad4d-13a44d536469
keywords:
- I/o WDK 电源管理
- 排队 i/o 请求
- 睡眠电源管理 WDK 内核
- 睡眠设备 WDK 电源管理
- 队列 Irp
- power Irp WDK 内核，排队 i/o 请求
- 工作状态返回 WDK 电源管理
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: f144ead81de654253c09a998a4933dd89affa7ac
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89183987"
---
# <a name="queuing-io-requests-while-a-device-is-sleeping"></a>设备睡眠时将 I/O 请求排队





设备进入睡眠状态时，其驱动程序应将定向到设备的任何 i/o 请求排队。 [**IoAllocateWorkItem**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioallocateworkitem)、 [**IoQueueWorkItem**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioqueueworkitem)和[**IoFreeWorkItem**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iofreeworkitem)支持例程为延迟处理提供了一种排队 irp 的方式。 有关示例，请参阅在 [设备暂停时保留传入 irp](holding-incoming-irps-when-a-device-is-paused.md)中的 PnP 驱动程序的排队机制。

仅当设备处于工作状态 (D0) 状态时，驱动程序才能访问其设备。 当设备处于睡眠状态时，驱动程序无法触摸任何设备注册;设备必须首先返回到工作状态。

 

