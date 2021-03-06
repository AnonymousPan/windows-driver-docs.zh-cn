---
title: 方向传感器数据字段
description: 本主题提供有关特定于方向传感器的数据字段的信息。
ms.assetid: 4B1FA56E-6956-4BC9-B929-3D78EF933057
ms.date: 07/20/2018
ms.localizationpriority: medium
ms.openlocfilehash: 055e8c966220806319909a875382a73e1ff3acce
ms.sourcegitcommit: e6d80e33042e15d7f2b2d9868d25d07b927c86a0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2020
ms.locfileid: "91733137"
---
# <a name="orientation-sensor-data-fields"></a>方向传感器数据字段


本主题提供有关特定于方向传感器的数据字段的信息。

下表显示了数据字段。 有关 "类型" 列中显示的类型的详细信息，请参阅 [PROPVARIANT 结构](/windows/win32/api/propidlbase/ns-propidlbase-propvariant)。

|属性键|类型|必需/可选|说明/注释|
|---|---|---|---|
|PKEY_SensorData_QuaternionW|VT_R4|必须|实系数 (相对于旋转轴矢量) 复数的虚部。|
|PKEY_SensorData_QuaternionX|VT_R4|必须|旋转轴向量的 X 分量。|
|PKEY_SensorData_QuaternionY|VT_R4|必须|旋转轴向量的 Y 分量。|
|PKEY_SensorData_QuaternionZ|VT_R4|必须|旋转轴向量的 Z 分量。|
|PKEY_SensorData_MagnetometerAccuracy|VT_UI4|必须|磁力仪传感器的准确性。 有关有效值的详细信息，请参阅 [MAGNETOMETER_ACCURACY](/windows-hardware/drivers/ddi/sensorsdef/ne-sensorsdef-magnetometer_accuracy)。|
|PKEY_SensorData_DeclinationAngle_Degrees|VT_R4|可选|用于从地球上北部的赤纬中推断出 true 的磁性。 如果不支持，类扩展将计算此值。|
|PKEY_SensorData_LinearAccelerationX_Gs|VT_R4|可选|G 中的 X 轴线性加速度|
|PKEY_SensorData_LinearAccelerationY_Gs|VT_R4|可选|G 中的 Y 轴线性加速度|
|PKEY_SensorData_LinearAccelerationZ_Gs|VT_R4|可选|G 的 Z 轴线性加速度|
|PKEY_SensorData_CorrectedAngularVelocityX_DegreesPerSecond|VT_R4|可选|Gyrometric X 轴速度，以度/秒为单位。|
|PKEY_SensorData_CorrectedAngularVelocityY_DegreesPerSecond|VT_R4|可选|Gyrometric Y 轴速度，以度/秒为单位。|
|PKEY_SensorData_CorrectedAngularVelocityZ_DegreesPerSecond|VT_R4|可选|Gyrometric Z 轴速度，以度/秒为单位。|


## <a name="related-topics"></a>相关主题


[MSDN PROPVARIANT 结构](/windows/win32/api/propidlbase/ns-propidlbase-propvariant)