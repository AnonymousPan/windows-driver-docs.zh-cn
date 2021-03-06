---
title: 获取其他注册表信息
description: 获取其他注册表信息
ms.assetid: 989acf63-3bb1-4d9a-a7a8-3eea1e2bc68a
keywords:
- 筛选注册表调用 WDK 内核，获取其他信息
- 注册表筛选驱动程序 WDK 内核，要获取的其他信息
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0d96e78326043112e7898d973245850df8d8d9da
ms.sourcegitcommit: 7ca2d3e360a4ae1d4d3c3092bd34492a2645ef74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89403120"
---
# <a name="obtaining-additional-registry-information"></a>获取其他注册表信息


在 Windows Vista 及更高版本的操作系统上运行的注册表筛选驱动程序可以获取以下有关注册表操作的其他信息：

-   对象标识符和名称

    [**CmCallbackGetKeyObjectIDEx**](/windows-hardware/drivers/ddi/wdm/nf-wdm-cmcallbackgetkeyobjectidex)例程检索与指定的注册表项对象相关联的注册表项标识符和对象名。

-   事务对象

    [**CmGetBoundTransaction**](/windows-hardware/drivers/ddi/wdm/nf-wdm-cmgetboundtransaction)例程返回指向 transaction 对象的指针，该对象表示与某个注册表项对象关联的[事务](introduction-to-ktm.md)（如果有）。

-   版本信息

    [**CmGetCallbackVersion**](/windows-hardware/drivers/ddi/wdm/nf-wdm-cmgetcallbackversion)例程检索当前版本的 configuration manager 的注册表回调功能的主要版本号和次版本号。

 

