---
title: 图像处理筛选器简介
description: 图像处理筛选器简介
ms.assetid: 59fc1bc1-c783-43df-9778-ea4306f6dd50
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: cc57cc4afe844134cdca48b7dabd886efc5486c1
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89189595"
---
# <a name="introduction-to-image-processing-filters"></a>图像处理筛选器简介





图像处理筛选器是一个 WIA 扩展。 图像处理筛选器有两个主要用途：

-   允许从驱动程序分离图像处理代码。 例如，图像处理筛选器可用于修改图像的亮度和对比度，并可用于执行 deskewing 和旋转。 图像处理筛选器位于其自己的 DLL 中，独立于用户模式驱动程序 DLL。 图像处理筛选器从执行筛选的驱动程序接收未筛选的图像处理数据。

-   启用准确的实时预览。 图像处理筛选器可用于 Windows Vista WIA Preview 的新组件 (Microsoft Windows SDK 文档) 提供准确的实时预览。 在这种情况下，"实时" 表示应用程序在更改了几个属性设置（将在本节后面部分中讨论）后无需从扫描程序重新获取映像。 预览是准确的，因为筛选实际上是由供应商组件在实际预览图像上执行的，而不只是完全独立的图像上的随机筛选器。

为了提供准确的预览，筛选器应该至少实现 [**亮度**](./wia-ips-brightness.md) 和 [**对比度**](./wia-ips-contrast.md) 属性。 这就是这样一个向用户提供亮度和对比度控制的通用 UI，可以显示准确的预览。

扫描图像时，始终会执行图像处理筛选器。 因此，应用程序无法在不首先应用图像处理筛选器的情况下从扫描仪获取映像。 应用程序无需知道筛选器。

Microsoft 提供了 WIA 预览组件，用于缓存从扫描仪获取的原始未筛选的预览图像。 使用 "预览" 组件，可以将筛选器多次应用于映像，而无需从扫描程序中重新获取映像。 当应用程序允许用户更改设置（如对比度和亮度）时，WIA 预览组件通常将用于预览图像。 当用户更改设置时，应用程序可以在预览窗格中持续显示生成的图像，而不必重新扫描映像。

图像处理筛选器是一个 WIA 扩展，作为进程内 COM 组件运行。 与分段筛选器不同，应用程序通常不会通过调用 Windows SDK 文档) 中所述的 **IWiaItem2：： path.getextension 对** (来创建图像处理筛选器的实例。 相反，应用程序将创建 WIA 预览组件的实例，然后使用 **IWiaItem2：： path.getextension 对** 方法加载实际图像处理筛选器。 当应用程序调用 IWiaTransfer 时，也会自动调用图像处理筛选器 **：:D o) **。

图像处理筛选器与驱动程序相关联，通常与驱动程序一起分发。 WIA 预览组件在 sti.dll 提供，并随操作系统提供。

下图显示了由 WIA 组件加载到应用程序进程中的图像处理筛选器。 请注意，可能会同时在应用程序的进程中加载图像处理筛选器的多个实例，因此筛选器写入必须对此进行小心。 例如，如果使用全局 (静态) 变量，筛选器编写器必须确保正确同步。

![说明由 wia 组件加载到应用程序进程中的图像处理筛选器的关系图](images/wia-components-app-process.png)

 

