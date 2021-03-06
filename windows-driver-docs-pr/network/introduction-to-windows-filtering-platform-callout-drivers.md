---
title: Windows 筛选平台标注驱动程序简介
description: Windows 筛选平台标注驱动程序简介
ms.assetid: d075da82-8dbc-41a5-a081-dd0e2b292371
keywords:
- Windows 筛选平台标注驱动程序 WDK，关于标注驱动程序
- 标注驱动程序 WDK Windows 筛选平台，关于标注驱动程序
- 标注 WDK Windows 筛选平台
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 03103a361d7059263119e07e9e406e881e8dd9bd
ms.sourcegitcommit: e6d80e33042e15d7f2b2d9868d25d07b927c86a0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2020
ms.locfileid: "91732817"
---
# <a name="introduction-to-windows-filtering-platform-callout-drivers"></a>Windows 筛选平台标注驱动程序简介


本部分介绍 Windows 筛选平台 [标注驱动程序](callout-driver.md)。 有关 Windows 筛选平台的详细信息，请参阅 Microsoft Windows SDK 中的 [Windows 筛选平台](/windows/win32/fwp/windows-filtering-platform-start-page) 文档。

### <a name="purpose-of-callout-drivers"></a>标注驱动程序的用途

标注驱动程序实现一个或多个 [标注](callout.md)。 标注通过以简单筛选功能范围之外的方式处理基于 TCP/IP 的网络数据，从而扩展了 Windows 筛选平台的功能。 标注通常用于执行以下任务：

<a href="" id="deep-inspection-------"></a>**深度检查**   
对网络数据执行复杂的检查，以确定应阻止哪些数据、应该允许哪些数据以及哪些数据应传递到另一个筛选器。 例如，防病毒产品可能会寻找病毒签名。

<a href="" id="packet-modification-------"></a>**数据包修改**   
对网络数据包标头或数据进行修改和 reinjection，或者同时执行这两项。 例如，网络地址转换 (NAT) 产品可以修改 IPv4 数据包上的标头。

<a href="" id="stream-modification-------"></a>**流修改**   
在流中对网络数据进行修改和 reinjection。 例如，家长控制产品可以在数据流中删除或替换特定的词或短语。

<a href="" id="data-logging-------"></a>**数据日志记录**   
网络流量数据的日志。 例如，网络监视产品可能会计算出于特定原因而丢弃的数据包的数目。

除了处理网络数据外，标注驱动程序还可以执行其他 Windows 筛选平台管理任务，例如将筛选器添加到基本筛选引擎。 有关 callout 驱动程序可以执行的其他任务的详细信息，请参阅 [调用其他 Windows 筛选平台函数](calling-other-windows-filtering-platform-functions.md)。

 

