---
title: 驱动程序初始化方法
ms.assetid: CA8F6308-501D-47BC-902E-3259949A1D57
description: 传感器驱动程序支持的方法来初始化设备。
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: b54568165741c8157a72718623187dac7c0dc83e
ms.sourcegitcommit: ec7bebe3f94536455e62b372c2a28fe69d1717f7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2020
ms.locfileid: "93349707"
---
# <a name="driver-initialization-methods"></a>驱动程序初始化方法

传感器驱动程序必须支持客户端和设备初始化。 伪代码使用以下方法演示这一点：

- DriverClientInitialize ( # A1
- DeviceSensorInitialize ( # A1

## <a name="client-initialization"></a>客户端初始化

客户端初始化方法具有以下形式。

```cpp
DriverClientInitialize(sensorID)
{
    // the following properties can be set from the API
    CRI = defaultCRI
    CS[] = defaultCS[]
    LDA = default[LDA]

    // the following properties cannot be set from the API
    // the driver provides defaults for these properties
    // the defaults can be overridden by the device
    sensorCategory = defaultSensorCategory
    sensorType = defaultSensorType
    minCRI = defaultMinCRI
    persistentUniqueID = defaultPersistentUniqueID
    sensorManufacturer = defaultSensorManufacturer
    sensorModel = defaultSensorModel
    serialNumber = defaultSerialNumber
    friendlyName = defaultFriendlyName
    sensorDescription = defaultDescription
    connectionType = defaultConnectionType

    // the following values are internal to the driver
    clientCount = 0
    subscriberCount = 0

    flagCRI = false
    flagCS = false
    flagLDA = false

    deviceState = deviceStateDisconnected
}
```

## <a name="related-topics"></a>相关主题

[Windows 中的传感器和位置平台简介](./index.md)

[传感器驱动程序逻辑](./driver-logic--pseudo-code-.md)