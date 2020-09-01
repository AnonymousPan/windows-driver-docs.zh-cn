---
title: ProcAmp 控制 DDI
description: ProcAmp 控制 DDI
ms.assetid: 102e21eb-bad4-4ab5-8630-9ac37c33f20a
ms.date: 01/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 31dd406f7f7378df0629f1e935d1ccf42025bf1c
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89066448"
---
# <a name="procamp-control-ddi"></a>ProcAmp 控制 DDI


## <span id="ddk_procamp_control_ddi_gg"></span><span id="DDK_PROCAMP_CONTROL_DDI_GG"></span>


为了使视频混合呈现器 (VMR) 可以访问 ProcAmp 功能，显示驱动程序必须实现 [运动补偿回调函数](/windows-hardware/drivers/ddi/index)。

若要简化驱动程序开发，请使用此部分中的运动补偿代码模板并实现 ProcAmp 控制功能。 函数是取消隔行扫描容器设备或 ProcAmp 控制设备类的成员函数。 有关详细信息，请参阅 [定义隔行扫描容器设备类](./defining-the-deinterlace-container-device-class.md) 和 [定义 ProcAmp Control 设备类](./defining-the-procamp-control-device-class.md)。

 

