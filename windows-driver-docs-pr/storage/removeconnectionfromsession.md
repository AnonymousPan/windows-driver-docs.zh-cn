---
title: RemoveConnectionFromSession
description: RemoveConnectionFromSession
ms.assetid: ae23713a-c75d-4669-a643-44e95dbb713c
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: e27d7a77a3bb3850b2a21a19018e0f1c0fead260
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89189233"
---
# <a name="removeconnectionfromsession"></a>RemoveConnectionFromSession


**RemoveConnectionFromSession**方法指示用于管理 iSCSI 发起程序 HBA 的微型端口驱动程序从登录会话中删除连接。

ISCSI 发起程序 (即，虚拟微型端口驱动程序) 不支持具有多个连接的会话。 不要将 **RemoveConnectionFromSession** 与 iSCSI 发起程序一起使用。

**RemoveConnectionFromSession**方法不会从会话中删除最后一个连接。 应使用 [LogoutFromTarget](logoutfromtarget.md) 方法通过单一连接关闭会话。

**RemoveConnectionFromSession** 属于未发布的 [MSiSCSI \_ 操作 WMI 类](msiscsi-operations-wmi-class.md)。 有关 **RemoveConnectionFromSession** 方法的参数的说明，请参阅 [**RemoveConnectionFromSession \_ IN**](/windows-hardware/drivers/ddi/iscsiop/ns-iscsiop-_removeconnectionfromsession_in) 和 [**RemoveConnectionFromSession \_ OUT**](/windows-hardware/drivers/ddi/iscsiop/ns-iscsiop-_removeconnectionfromsession_out) 结构的成员说明。

实现 MSiSCSI 操作 WMI 类的微型端口驱动程序 \_ 必须支持此方法。

 

