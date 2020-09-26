---
title: Windows 设备测试框架 (WDTF) 设计指南
description: 使用 Microsoft Windows 设备测试框架 (WDTF)，你可以创建、管理、重用和扩展以设备为中心、基于方案的自动化测试。
ms.assetid: cff552f0-5dde-4fe7-996c-0a496d845edc
ms.date: 04/20/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.openlocfilehash: cc30ce0913bd8f1d7f9fa04950c759e2acacebbb
ms.sourcegitcommit: acef3c512676aad3aed1934cbe3d0f16e6d37619
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2020
ms.locfileid: "91372932"
---
# <a name="windows-device-testing-framework-wdtf-design-guide"></a>Windows 设备测试框架 (WDTF) 设计指南

使用 Microsoft Windows 设备测试框架 (WDTF)，你可以创建、管理、重用和扩展以设备为中心、基于方案的自动化测试。

## <a name="in-this-section"></a>在本节中

|主题|说明|
|----|----|
|[为你的设备编写 WDTF SimpleIO 插件](writing-a-wdtf-simpleio-plug-in-for-your-device.md)|若要充分利用[设备基础测试](/windows-hardware/drivers)，你的设备应当有一个可以对设备执行简单 I/O 操作的简单 I/O 插件。 这可以是 WDTF 附带的默认简单 I/O 插件之一，也可以是你自己编写的插件。 若要了解设备类型是否受支持以及确定是否有特定的测试要求，请参阅[提供的 WDTF 简单 I/O 插件](provided-wdtf-simpleio-plug-ins.md)。|
|[使用 WDTF 编写测试](writing-tests-with-wdtf.md)|无论你是使用 Windows 驱动程序工具包 (WDK) 中提供的模板开始编写驱动程序测试，还是自己创建测试，你都可以借助 Microsoft Windows 设备测试框架 (WDTF) 来创建和扩展以设备为中心、基于方案的自动化测试。|
|[会审基于 WDTF 的测试](triaging-wdtf-based-tests.md)|为了帮助你更好地理解基于 WDTF 的测试中发生的情况，你可以使用内置的 [WDTF 对象日志记录](logging-and-tracing.md)和 [WPP 软件跟踪](../devtest/wpp-software-tracing.md)支持。|
|[WDTF 体系结构和概述](wdtf-overview.md)|使用 Microsoft Windows 设备测试框架 (WDTF)，你可以创建、管理、重用和扩展以设备为中心、基于方案的自动化测试。|