---
title: 关于变换器类驱动程序
description: 更换器类驱动程序
ms.assetid: c1c2330c-9cfc-432f-945c-630dc16aa54d
keywords:
- 更换器驱动程序 WDK 存储，类驱动程序
- 存储更换器驱动程序 WDK、类驱动程序
- 类驱动程序 WDK 存储，更换器驱动程序
ms.date: 12/15/2019
ms.localizationpriority: medium
ms.openlocfilehash: 0ab265ab38b8c63d45d511ed6df449050b4735a5
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89186643"
---
# <a name="about-the-changer-class-driver"></a>关于变换器类驱动程序

系统提供的变换器类驱动程序为硬件供应商提供的转换器 miniclass 驱动程序执行特定于设备的操作系统特定的服务。 有关转换器 miniclass 驱动程序的详细信息，请参阅 [转换器 Miniclass 驱动程序](introduction-to-changer-miniclass-drivers.md)。

变换器类驱动程序：

- 提供 miniclass 驱动程序调用的内存分配例程，以分配和释放池内存。

- 提供与操作系统无关的方法，可将同步 SRBs 发送到 Microsoft Windows XP 和更高版本的操作系统中的端口驱动程序 (参阅 [变换器类驱动程序版本中的差异](differences-in-changer-class-driver-versions.md) ，以了解 Windows 2000 和 windows XP) 之间的差异说明。

- 有助于初始化 class/miniclass 驱动程序对。

- 调用 **转换器 * * * Xxx* miniclass driver 例程，以确定为设备特定的信息分配的空间量，并准备转换器以接收其他请求。

- 对 [**IRP_MJ_DEVICE_CONTROL**](../kernel/irp-mj-device-control.md) 请求执行与设备无关的预处理，调用相应的 **转换器 * * ** miniclass 例程，并完成请求。

- 针对错误执行与设备无关的预处理，并调用 miniclass 驱动程序的 [**ChangerError**](/windows-hardware/drivers/ddi/mcd/nf-mcd-changererror) 例程进行特定于设备的处理。

- 调用 **转换器 * * * Xxx* miniclass 驱动程序例程以获取产品数据、更改元素状态或查询查询或卷标记数据。