---
title: 从 UI 插件访问驱动程序设置
description: 从 UI 插件访问驱动程序设置
ms.assetid: 898e1cfb-851b-403e-a88b-d38c505c1390
keywords:
- 用户界面插件 WDK 打印，访问驱动程序设置
- UI 插件 WDK 打印，访问驱动程序设置
- 状态信息 WDK 打印插件
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 54a1533eca498863263f7164fc904913e81ceae5
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89216504"
---
# <a name="accessing-driver-settings-from-ui-plug-ins"></a>从 UI 插件访问驱动程序设置





UI 插件可以获取打印机功能和其他内部信息的当前状态。 [**IPrintOemDriverUI：:D rvgetdriversetting**](/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemdriverui-drvgetdriversetting) COM 接口方法是在 Microsoft 的打印机驱动程序的打印机接口 DLL 内实现的，并且可以由 UI 插件调用。

此外，以下方法允许 UI 插件修改驱动程序信息：

[**IPrintOemDriverUI：:D rvupdateuisetting**](/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemdriverui-drvupdateuisetting) 允许 UI 插件在用户修改了驱动程序设置时通知驱动程序。

[**IPrintOemDriverUI：:D rvupgraderegistrysetting**](/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemdriverui-drvupgraderegistrysetting) 允许 UI 插件修改注册表中的设备设置，以便可以更新旧驱动程序版本使用的注册表设置。

 

