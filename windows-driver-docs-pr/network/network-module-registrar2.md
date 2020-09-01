---
title: 网络模块注册机构主题
description: 网络模块注册机构主题
ms.assetid: 23c15c42-94aa-410b-8551-fafa8b24ad86
keywords:
- 网络模块注册 WDK
- NMR WDK
- 模块 WDK 网络模块注册器
- 已注册的网络模块 WDK 网络模块注册器
- 软件模块 WDK 网络模块注册器
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: a7634f7172dd4ec750352439069981ca01da1410
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89210655"
---
# <a name="network-module-registrar-topics"></a>网络模块注册机构主题


本部分讨论网络模块注册器，并包括以下主题：

[网络模块注册机构简介](introduction-to-the-network-module-registrar.md)

[网络模块注册机构定义](nmr-definitions.md)

[体系结构概述](architecture-overview.md)

[客户端模块操作](client-module-operations.md)

[提供程序模块操作](provider-module-operations.md)

[编程注意事项](programming-considerations.md)

使用 [**WskRegister**](/windows-hardware/drivers/ddi/wsk/nf-wsk-wskregister) 和 [**WskDeregister**](/windows-hardware/drivers/ddi/wsk/nf-wsk-wskderegister) 函数是注册和注销 WSK 应用程序的首选方法。 网络模块注册机构仍可提供兼容性。 有关详细信息，请参阅 [注册 Winsock 内核应用程序](registering-a-winsock-kernel-application.md)。

 

