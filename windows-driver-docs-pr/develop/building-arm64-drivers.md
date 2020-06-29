---
title: 使用 WDK 生成 ARM64 驱动程序
description: 本主题介绍如何使用 Windows 驱动程序工具包 (WDK) 生成 ARM64 驱动程序。
ms.date: 01/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: ac4f277ee1a2d0b9a08c004173f68385b1bacdae
ms.sourcegitcommit: 444e055daa9b28e9fd9dc92dd0a3f1e62e215b31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84666165"
---
# <a name="building-arm64-drivers-with-the-wdk"></a>使用 WDK 生成 ARM64 驱动程序

Windows 10 可以在由 ARM64 处理器提供支持的计算机上运行。  但是，由于基于 ARM 的 Windows 10 不支持模拟 x86 内核模式驱动程序，需要根据以下说明将内核模式驱动程序重新编译为 ARM64。

## <a name="setup"></a>安装

1. 下载 [Visual Studio 2017 或 2019](https://visualstudio.microsoft.com/downloads/)。  所需的最低版本为 15.9。
2. 在 Windows 开始菜单中，键入“Visual Studio 安装程序”。  然后在“工作负载”选项卡上，选择“使用 C++ 的桌面开发”。  
![从工作负载磁贴的 Windows 选项中选择“使用 C++ 的桌面开发”](images/VS-workloads.png)

2. 在“单个组件”选项卡上，选择下列选项：
    *  **适用于 ARM 的 Visual C++ 编译器和库**
    *  **适用于 ARM64 的 Visual C++ 编译器和库**  
![选择要安装的 ARM 特定组件](images/VS-individual-components.png)

3.  安装并重启 Visual Studio。
4.  下载 [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。  确保你有 SDK 版本16299（Windows 10 版本 1709）或更高版本。
5.  下载 [WDK](../download-the-wdk.md)。  确保你有 WDK 版本 16299 或更高版本。

## <a name="building-an-arm64-driver-with-the-wdk"></a>使用 WDK 生成 ARM64 驱动程序

1.  在 Visual Studio 中，打开一个驱动程序解决方案。  你可以使用自己的驱动程序解决方案，也可以使用 [Windows 驱动程序示例](https://github.com/Microsoft/Windows-driver-samples)存储库中的驱动程序解决方案。
2.  单击“解决方案”平台，然后选择“配置管理器”。  
![从顶部工具栏的第二个下拉列表中选择配置管理器](images/VS-config-mgr.png)
  
3.  在“活动解决方案平台”下，选择“新建”。  
![在“活动解决方案平台”下拉列表中，选择“新建”](images/VS-active-solution-platform.png)

4.  从“键入或选择新平台”中选择“ARM64”。  从 **Win32** 复制设置。  单击“确定”和“关闭”。  
![从工具栏级别下拉列表中选择 ARM64 生成目标](images/VS-build-ARM64.png)

5.  选择“ARM64”作为目标平台并重新生成。

## <a name="see-also"></a>另请参阅

* [调试 ARM64](../debugger/debugging-arm64.md)
* [基于 ARM 的 Windows 10](https://docs.microsoft.com/windows/uwp/porting/apps-on-arm)
* [HLK ARM64 入门指南](https://docs.microsoft.com/windows-hardware/test/hlk/getstarted/hlk-arm64-getting-started-guide)
