---
title: 更改适配器上的状态
description: 更改适配器上的状态
ms.assetid: bf503a42-ac32-4d68-9ad9-afec69c5fe2a
keywords:
- 视频适配器状态更改 WDK 视频微型端口
- 状态 WDK 视频微型端口
- 适配器状态 WDK 视频微型端口
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 13ffb56831f8e0b3fd1a36fd1290226c477ccd8d
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89063158"
---
# <a name="changing-state-on-the-adapter"></a>更改适配器上的状态


## <span id="ddk_changing_state_on_the_adapter_gg"></span><span id="DDK_CHANGING_STATE_ON_THE_ADAPTER_GG"></span>


小型端口驱动程序不能永久更改适配器的状态，直到调用其 [*HwVidInitialize*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_initialize) 例程为止。 在 *HwVidInitialize*之前调用的微型端口驱动程序例程（如 [*HwVidFindAdapter*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_find_adapter)）不会不必要地更改任何视频适配器的状态，也不能永久更改任何视频适配器的状态。

当 [*HwVidFindAdapter*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_find_adapter) 运行时，HAL 控制视频适配器，因此它可以在系统启动过程的早期阶段将信息写入屏幕。 如果 *HwVidFindAdapter*尝试识别适配器的状态，则此例程应立即还原原始状态，以便在 *HwVidFindAdapter* 上返回时，HAL 可以继续显示启动消息。

例如， [*HwVidFindAdapter*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_find_adapter) 应延迟将适配器的 DAC 类型确定为 [*HwVidInitialize*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_initialize) 函数，因为进行此确定不会影响是否将加载微型端口驱动程序，而是永久更改适配器的状态。

 

