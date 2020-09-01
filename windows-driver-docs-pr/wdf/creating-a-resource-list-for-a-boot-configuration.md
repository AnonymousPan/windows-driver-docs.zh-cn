---
title: 为启动配置创建资源列表
description: 为启动配置创建资源列表
ms.assetid: 8b78cbac-b547-45a1-a49c-f5543bf5ffed
keywords:
- 硬件资源 WDK KMDF，启动配置资源列表
- 启动配置资源列表 WDK KMDF
- 启动配置资源列表 WDK KMDF，创建
- 资源列表 WDK KMDF
- 资源列表 WDK KMDF，创建
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 02cd24fc646a68a6ce9b45c793f8a1619216e54b
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89187069"
---
# <a name="creating-a-resource-list-for-a-boot-configuration"></a>为启动配置创建资源列表


在总线驱动程序枚举设备后，框架将调用驱动程序的 [*EvtDeviceResourcesQuery*](/windows-hardware/drivers/ddi/wdfpdo/nc-wdfpdo-evt_wdf_device_resources_query) 回调函数。 此回调函数接收资源列表对象的句柄，该对象表示空资源列表。 然后，该驱动程序必须执行以下操作，以便将信息添加到该设备的启动配置所需的每种类型的硬件资源列表中：

1.  填写驱动程序提供的 [**CM \_ 部分 \_ 资源 \_ 描述符**](/windows-hardware/drivers/ddi/wdm/ns-wdm-_cm_partial_resource_descriptor) 结构，此结构指定特定资源的有效值。

2.  调用 [**WdfCmResourceListAppendDescriptor**](/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfcmresourcelistappenddescriptor) 或 [**WdfCmResourceListInsertDescriptor**](/windows-hardware/drivers/ddi/wdfresource/nf-wdfresource-wdfcmresourcelistinsertdescriptor) 将 CM \_ 部分 \_ 资源描述符结构的内容添加 \_ 到资源列表。

驱动程序的 *EvtDeviceResourcesQuery* 回调函数返回后，框架会将资源列表传递到 PnP 管理器。

设备安装程序可以指定其他资源列表。 有关其他资源列表的详细信息，请参阅 [硬件资源](../kernel/hardware-resources.md)。

 

