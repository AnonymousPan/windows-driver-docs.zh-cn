---
title: WDI NDIS 空闲检测
description: 此下图显示了简单的状态关系图的 NDIS 空闲检测，使用到 USB 选择性挂起的驱动器。
ms.assetid: A2E5D433-7825-434E-811F-B24A26913BEC
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: ce606ba5ca558dfdf7e9e82c161752b9c1eb7cc1
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385374"
---
# <a name="wdi-ndis-idle-detection"></a>WDI NDIS 空闲检测


此下图显示了简单的状态关系图的 NDIS 空闲检测，使用到 USB 选择性挂起的驱动器。

![wdi ndis 空闲检测 usb 选择性挂起](images/wdi-idle-detection-selective-suspend.png)

如果 WDI 设备/驱动程序支持 USB 选择性挂起，NDIS 检测到其空闲状态，以将设备发送到低功耗状态 (D2)。

 

 





