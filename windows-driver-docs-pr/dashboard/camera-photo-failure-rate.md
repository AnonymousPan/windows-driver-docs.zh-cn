---
title: 相机照片捕获失败次数百分比
description: 该度量将来自 7 天滑动窗口的遥测数据聚合为相机设备无法使用照片功能的实例所占的百分比
ms.topic: article
ms.date: 05/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: e5be9197499104417f1170e138f519bba302140c
ms.sourcegitcommit: f63852446e614c985a65f599cdfe788bdb0c6089
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425729"
---
# <a name="percent-of-camera-photo-capture-failures"></a>相机照片捕获失败次数百分比

## <a name="description"></a>说明

若要将相机的预览捕获到内存中，用户可拍摄照片，并将其存储在计算机上。 如果照片处理过程失败，用户将无法捕获所需的图像。

## <a name="measure-attributes"></a>度量属性

|属性|值|
|----|----|
|受众|Standard|
|时间段|7 天滑动窗口|
|度量标准|实例的聚合|
|最小总体数量|10 个实例|
|通过标准|<= 5% 的照片拍摄实例导致故障|
|度量 ID|16998997|

## <a name="calculation"></a>计算

1. 该度量将来自 7 天滑动窗口的遥测数据聚合为相机设备无法使用照片功能的实例所占的百分比  。

     a. 单个设备中可以有多种通过度量进行计数的照片实例

2. 实例类型

   a. 成功的照片事件 = 0% 失败

     i. `MFCaptureEngineOnEvent (MF_CAPTURE_ENGINE_PHOTO_TAKEN)`

     ii. `MFCaptureEngineOnEvent (MF_CAPTURE_ENGINE_PHOTO_SEQUENCE_STARTED)`

    b. 失败的照片事件 = 100% 失败

     i. `MFCaptureEngineOnEvent (MF_CAPTURE_ENGINE_PHOTO_TAKEN) HRESULT !=0`

     ii. `MFCaptureEngineOnEvent (MF_CAPTURE_ENGINE_PHOTO_SEQUENCE_STARTED) HRESULT !=0`

     iii. 超时

### <a name="final-calculation"></a>最终计算

相机照片失败率 = 平均值（所有实例）
