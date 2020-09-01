---
title: 重启驱动程序堆栈
description: 重启驱动程序堆栈
ms.assetid: 5c9138f8-4a29-4740-b085-efe24d950fba
keywords:
- 驱动程序堆栈 WDK 网络，重新启动
- 重新启动驱动程序堆栈 WDK 网络
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 1622977937735ce0ca329ae636c10f590348b709
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89215017"
---
# <a name="restarting-a-driver-stack"></a>重启驱动程序堆栈





NDIS 在插入筛选器模块或添加绑定等操作后重新启动驱动程序堆栈。 驱动程序堆栈重启操作按如下方式继续：

1.  NDIS 重启微型端口适配器。

    在 NDIS 调用微型端口驱动程序的 [**MiniportRestart**](/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_restart) 函数后，微型端口适配器将进入重新启动状态。 微型端口驱动程序准备恢复发送和接收操作。 如果准备失败，微型端口适配器将恢复到暂停状态。 当驱动程序准备好继续发送和接收操作后，微型端口适配器将进入 "正在运行" 状态。

2.  NDIS 将重新启动筛选器模块，从驱动程序堆栈的底部开始，到协议驱动程序。

    在 NDIS 调用筛选器驱动程序的 [**FilterRestart**](/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_restart) 函数后，筛选器模块将进入重新启动状态。 筛选器驱动程序准备恢复发送和接收操作。 如果准备失败，则该模块将返回到 "已暂停" 状态。 当驱动程序准备好继续发送和接收操作后，筛选器模块将进入 "正在运行" 状态。

3.  NDIS 将 PnP 重启事件发送到协议驱动程序。

    绑定进入重新启动状态。 协议驱动程序准备恢复发送和接收操作。 如果准备失败，绑定将返回到 "已暂停" 状态。 在协议驱动程序准备好继续发送和接收操作后，绑定将进入 "正在运行" 状态。

 

