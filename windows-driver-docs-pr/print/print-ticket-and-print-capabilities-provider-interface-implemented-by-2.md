---
title: 打印票证和打印功能提供程序接口
description: 打印机驱动程序实现的打印票证和打印功能提供程序接口
ms.assetid: a14c1173-0419-44c7-bc8f-7197590083b3
keywords:
- 打印机接口 DLL WDK，打印票证支持
- 打印机接口 DLL WDK，打印功能支持
- 打印功能 WDK，打印机接口 DLL
- 打印票证 WDK，打印机接口 DLL
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f2ce3fde22abc5d5aa286edb27b89a931e61e234
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89207113"
---
# <a name="print-ticket-and-print-capabilities-provider-interface-implemented-by-printer-drivers"></a>打印机驱动程序实现的打印票证和打印功能提供程序接口


Windows Vista 操作系统为所有驱动程序提供基本的打印票证支持。 但是，这种支持仅基于通过 Microsoft Win32 应用程序编程接口公开的信息 (Api) 例如 **DeviceCapabilities** 和 **GetDeviceCaps** ，以及 [**DEVMODEW**](/windows/win32/api/wingdi/ns-wingdi-devmodew) 结构的公共部分中的设置。 驱动程序可以通过实现驱动程序打印票证和打印功能提供程序界面来提供更丰富的体验，如以下主题中所述。

打印票证和打印功能提供程序接口的实现必须是多线程安全的，因为对提供程序的调用由应用程序驱动，并且可能会并发进行。

 

