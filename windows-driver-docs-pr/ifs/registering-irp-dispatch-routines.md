---
title: 注册 IRP 调度例程
description: 注册 IRP 调度例程
ms.assetid: 096f4bb7-2326-4e6c-b3db-a2d95ca4982b
keywords:
- 正在注册 IRP 调度例程
- 调度例程 WDK 文件系统
- IRP 调度例程 WDK 文件系统，注册
- Irp WDK 文件系统
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 1522ce6c5d8e27ebedac63fb2ee17e30f8c84fc2
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89065926"
---
# <a name="registering-irp-dispatch-routines"></a>注册 IRP 调度例程


## <span id="ddk_registering_irp_dispatch_routines_if"></span><span id="DDK_REGISTERING_IRP_DISPATCH_ROUTINES_IF"></span>


筛选器驱动程序的[**DriverEntry**](/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_initialize)例程的*DriverObject*参数提供一个指针，指向筛选器驱动[**程序的驱动程序对象**](/windows-hardware/drivers/ddi/wdm/ns-wdm-_driver_object)。 若要注册 i/o 请求数据包 (IRP) 调度例程，必须将这些例程的入口点存储到 driver 对象的 **MajorFunction** 成员中。 例如，假设 "MyLegacyFilter" 驱动程序可以设置其调度例程的入口点，如下所示：

```cpp
for (i = 0; i <= IRP_MJ_MAXIMUM_FUNCTION; i++) {
    DriverObject->MajorFunction[i] = MyLegacyFilterDispatch;
}
DriverObject->MajorFunction[IRP_MJ_CREATE] = MyLegacyFilterCreate;
DriverObject->MajorFunction[IRP_MJ_CLOSE] = MyLegacyFilterClose;
DriverObject->MajorFunction[IRP_MJ_FILE_SYSTEM_CONTROL] = MyLegacyFilterFsControl;
```

请注意，上述 **for** 循环为所有 IRP 主要函数代码分配一个默认调度例程。 此分配是一种很好的做法，因为在默认情况下，i/o 管理器将完成任何无法识别的 IRP，并返回 " \_ \_ 设备 \_ 请求无效" 状态 文件系统筛选器驱动程序不应以这种方式拒绝不熟悉的 Irp，因为此类请求通常用于驱动程序堆栈中较低位置的另一个驱动程序。 出于此原因，默认的调度例程通常只将 IRP 传递到下一个较低级别的驱动程序。

 

