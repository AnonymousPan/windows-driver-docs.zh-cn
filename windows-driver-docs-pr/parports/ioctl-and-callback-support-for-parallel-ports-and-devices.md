---
title: 对并行端口和设备的 IOCTL 和回调支持
description: 对并行端口和设备的 IOCTL 和回调支持
ms.assetid: 72a31f50-2f59-4a4d-aac7-571f83a94259
keywords:
- 系统提供的并行驱动程序 WDK，IOCTLs
- IOCTLs WDK 并行驱动程序
- 回调 WDK 并行驱动程序
- 系统提供的并行驱动程序 WDK，回调
- 并行设备 WDK，回调
- 并行设备 WDK，IOCTLs
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e2c94cf76801735de87cdf5b998b0ba29361cbba
ms.sourcegitcommit: faff37814159ad224080205ad314cabf412e269f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89385091"
---
# <a name="ioctl-and-callback-support-for-parallel-ports-and-devices"></a>对并行端口和设备的 IOCTL 和回调支持





本部分提供了一些主题链接，这些主题描述系统提供的并行驱动程序如何支持操作并行端口和连接到并行端口的设备。

附加到并行端口的并行设备的供应商函数驱动程序是可选的。 系统提供的并行驱动程序为直接控制作为原始设备的并行设备以及操作设备的父并行端口提供了广泛的支持。

有关系统提供的函数驱动程序提供的用于操作并行端口的 IOCTLs 和回调的信息，请参阅以下主题：

[获取有关并行端口的信息](obtaining-information-about-a-parallel-port.md)

[同步并行端口的使用](synchronizing-the-use-of-a-parallel-port.md)

[选择和取消选择连接到并行端口的 IEEE 1284 设备](selecting-and-deselecting-an-ieee-1284-device-attached-to-a-parallel-p.md)

[设置和清除并行端口上的通信模式](setting-and-clearing-the-communication-mode-on-a-parallel-port.md)

[连接到 IEEE 1284.3 数据链路设备](connecting-to-an-ieee-1284-3-data-link-device.md)

有关系统提供的总线驱动程序提供的、用于操作连接到并行端口的并行设备的 IOCTLs 和回调的信息，请参阅以下内容：

[打开和使用并行设备](opening-and-using-a-parallel-device.md)

[连接到并行设备](connecting-to-a-parallel-device.md)

[获取有关并行设备的信息](obtaining-information-about-a-parallel-device.md)

[锁定和解锁供并行设备使用的并行端口](locking-and-unlocking-a-parallel-port-for-use-by-a-parallel-device.md)

[设置和清除并行设备的通信模式](setting-and-clearing-a-communication-mode-for-a-parallel-device.md)

[在并行设备上设置属性](setting-attributes-on-a-parallel-device.md)

[向并行设备进行读取和写入](reading-and-writing-a-parallel-device.md)

有关如何操作连接到并行端口的并行端口和设备的详细信息，请参阅：

[打开并行端口](operating-a-parallel-port.md)

[打开连接到并行端口的并行设备](operating-a-parallel-device-attached-to-a-parallel-port.md)

[系统提供的并行驱动程序的客户端接口](/windows-hardware/drivers/ddi/index)

 

