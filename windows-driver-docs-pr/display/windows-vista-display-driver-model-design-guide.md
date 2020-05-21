---
title: Windows 显示驱动程序模型 (WDDM) 设计指南
description: Windows 显示驱动程序模型（WDDM）从 Windows Vista 开始提供，并从 Windows 8 开始是必需的。 本部分讨论 WDDM 驱动程序的要求、规范和行为。
ms.assetid: d9dc0d48-aea4-4614-a23b-e2449800469f
keywords:
- WDDM 设计指南 WDK
- 显示驱动程序模型 WDK Windows Vista
- Windows Vista 显示器驱动程序模型 WDK
- 显示设备 WDK
- 显示驱动程序 WDK，Windows Vista
- 显示驱动程序模型 WDK Windows Vista，关于显示器驱动程序模型
- Windows Vista 显示器驱动程序模型 WDK，关于显示器驱动程序模型
- 微型端口驱动程序 WDK 显示
- 显示微型端口驱动程序 WDK，请参阅微型端口驱动程序 WDK 显示
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 28f2f70abaaed11398fb99aa3f9ff4304da9f9af
ms.sourcegitcommit: d395d4b36f39d3557adda53735a4fdc8745a6408
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83642553"
---
# <a name="windows-display-driver-model-wddm-design-guide"></a>Windows 显示驱动程序模型 (WDDM) 设计指南

Windows 显示驱动程序模型（WDDM）从 Windows Vista 开始提供，并从 Windows 8 开始是必需的。 本部分讨论 WDDM 驱动程序的要求、规范和行为。

## <span id="wddm_id"></span><span id="WDDM_ID"></span>

**注意**  [Windows 2000 显示器驱动程序模型（XDDM）](windows-2000-display-driver-model-design-guide.md)和 VGA 驱动程序将不会在 windows 8 及更高版本上编译。 如果将显示硬件连接到 Windows 8 计算机，而该计算机上没有一个已认证为支持 WDDM 1.2 或更高版本的驱动程序，则系统默认为运行 Microsoft 基本显示驱动程序。

以下部分介绍 Windows 显示驱动程序模型（WDDM）：

[Windows 10 显示器和图形驱动程序的新增功能](what-s-new-for-windows-10-display-and-graphics-drivers.md)

[Windows 8.1 显示驱动程序 (WDDM 1.3) 的新增功能](what-s-new-for-windows-8-1-display-drivers--wddm-1-3-.md)

[Windows 8 显示驱动程序 (WDDM 1.2) 的新增功能](what-s-new-for-windows-8-display-drivers.md)

[Windows 7 显示驱动程序 (WDDM 1.1) 的新增功能](what-s-new-for-windows-7-display-drivers--wddm-1-1-.md)

[WDDM 2.0 和 Windows 10](wddm-2-0-and-windows-10.md)

[WDDM 1.2 和 Windows 8](wddm-in-windows-8.md)

[Windows 显示驱动程序模型 (WDDM) 简介](introduction-to-the-windows-vista-and-later-display-driver-model.md)

[显示微型端口和用户模式显示驱动程序的安装要求](installing-display-miniport-and-user-mode-display-drivers.md)

[针对 Windows 7 和更高版本优化的显示驱动程序的安装要求](installing-display-drivers-optimized-for-windows-7-and-later.md)

[初始化显示微型端口和用户模式显示驱动程序](initializing-display-miniport-and-user-mode-display-drivers.md)

[Windows Vista 显示器驱动程序线程和同步模型](windows-vista-display-driver-threading-and-synchronization-model.md)

[视频内存管理和 GPU 计划](video-memory-management-and-gpu-scheduling.md)

[用户模式显示驱动程序](user-mode-display-drivers.md)

[监视驱动程序](monitor-drivers.md)

[多个监视器和视频呈现网络](multiple-monitors-and-video-present-networks.md)

[Windows 显示驱动程序模型 (WDDM) 中的任务](tasks-in-the-windows-vista-display-driver-model.md)

[Windows 显示驱动程序模型 (WDDM) 的调试提示](debugging-tips-for-the-windows-vista-display-driver-model.md)

[Windows 显示驱动程序模型（WDDM）的实现提示和要求](implementation-tips-and-requirements-for-the-windows-vista-display-dri.md)

[显示示例](display-samples.md)

[容器对非 DX Api 的支持](container-non-dx.md)

**注意**   WDDM 驱动程序不会直接使用 Windows 图形设备接口（GDI）引擎的服务;因此， [GDI](gdi.md)部分与编写 WDDM 驱动程序模型的显示驱动程序并不相关。
