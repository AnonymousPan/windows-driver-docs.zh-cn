---
title: 改进的彩色打印
description: 改进的彩色打印
ms.assetid: b0487ee0-9b4a-4083-9416-ad22b97ed94b
keywords:
- XPSDrv 的打印机驱动程序 WDK、 彩色打印
- 颜色打印 WDK XPSDrv
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: b16cfe7f7e3ca4a0c8902720526800619d8336ea
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63392826"
---
# <a name="improved-color-printing"></a>改进的彩色打印


新的颜色管理功能和 XPS 打印路径在 Windows Vista 工作一起，以提供更丰富、 更可预测的彩色打印。 增强的颜色支持，通过支持打印功能与多个四个颜料高端打印。 （四个以上颜料是与印前应用程序的客户要求的。）新的 XPS 打印体系结构可以应用程序生成扩展的颜色信息传递给范围内所有彩色打印机。 设备驱动程序可以访问和控制打印管道内的颜色信息。

Windows Vista 使得 Windows 颜色系统，它引入了对跨不同的软件应用程序、 图像处理设备、 映像的媒体，查看条件中的可预测性匹配颜色的颜色管理的重要创新，利用可靠，并一致的方式。 XPS 文档是用于将应用程序的颜色信息发送到基于 XPS 文档的设备的通道。 XPS 文档格式采用了此技术，通过对以下的本机支持：

-   较高的精度、 更高版本的动态范围和更大范围的色彩空间。

-   CMYK 和支持 （具有多个四个颜料） n 墨迹系统的使用。

-   支持的已命名的颜色。

通过 XPS 假脱机文件，XPS 打印路径此高级的颜色信息将直接传递到设备驱动程序。 （可选） 的设备驱动程序可以提供下列改进了的颜色处理：

-   自动颜色配置的设备与 XPS 打印路径驱动程序。

-   能够重复使用不同的打印设备的管道中的内容。

-   可以可靠地保持到驱动程序应用程序中的颜色数据，因为可以直接在假脱机文件中嵌入的颜色配置文件和处理指令。

-   改进的颜色功能和设置的通信。 应用程序可以控制处理通过启用或禁用新的打印路径中的系统颜色管理的颜色。 驱动程序可以更完整地表示其设备的颜色功能。

 

 




