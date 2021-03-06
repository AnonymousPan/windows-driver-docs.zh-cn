---
title: 使用串行框架扩展版本 2 (SerCx2)
description: 您可以编写一起使用版本 2 的串行框架扩展 (SerCx2) 来管理串行控制器的串行控制器驱动程序。
ms.assetid: 192C25B2-936B-40D3-A0EA-5D02A234506E
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: abcb0d14bc56a4e617fb91eab30ce92f0c0d3502
ms.sourcegitcommit: 6a0636c33e28ce2a9a742bae20610f0f3435262c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65836238"
---
# <a name="using-version-2-of-the-serial-framework-extension-sercx2"></a>使用串行框架扩展版本 2 (SerCx2)

您可以编写一起使用版本 2 的串行框架扩展 (SerCx2) 来管理串行控制器的串行控制器驱动程序。 此外可以编写用于连接到由 SerCx2 联合管理的串行控制器上的端口的外围设备的外围设备驱动程序和串行控制器驱动程序。 此外围设备的驱动程序将使用[串行 I/O 请求接口](serial-i-o-request-interface.md)传输设备数据。 扩展基于串行控制器驱动程序处理串行控制器的所有特定于硬件的任务，但使用 SerCx2 来执行许多常见到所有的串行控制器的系统任务。 SerCx2 是从 Windows 8.1 的系统提供的组件。

**请注意**  SerCx2 替换第 1 版 Windows 8 中引入了串行 framework 扩展 (SerCx)。 旨在仅在 Windows 8.1 和更高版本的 Windows 中运行的新串行控制器驱动程序应编写为使用而不是 SerCx DDIs SerCx2 DDIs。 但是，Windows 8.1 和更高版本的 Windows 支持使用 SerCx DDI 的现有串行控制器驱动程序。

串行控制器是 16550 通用异步接收器/转换器 (UART) 或兼容的设备。 有关详细信息，请参阅[串行控制器驱动程序概述](serial-drivers-overview.md)。

## <a name="in-this-section"></a>本节内容

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>主题</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="sercx2-architectural-overview.md" data-raw-source="[SerCx2 Architectural Overview](sercx2-architectural-overview.md)">SerCx2 体系结构概述</a></p></td>
<td><p>SerCx2 一起使用的串行控制器驱动程序，以允许外围设备的驱动程序和串行连接的外围设备之间进行通信。 通常情况下，串行控制器已集成到芯片 (SoC) 芯片上的系统与外部 SoC 芯片但焊接到相同的印刷电路板的外围设备提供低 pin 计数通信。</p></td>
</tr>
<tr class="even">
<td><p><a href="serial-controller-driver-design-for-sercx2.md" data-raw-source="[Serial Controller Driver Design for SerCx2](serial-controller-driver-design-for-sercx2.md)">SerCx2 串行控制器驱动程序设计</a></p></td>
<td><p>若要管理串行控制器，你编写执行特定于硬件的任务，并与 SerCx2 进行通信的串行控制器驱动程序。 从 Windows 8.1 开始，SerCx2 是系统提供的组件，它处理许多通用串行控制器的这些处理任务。</p></td>
</tr>
<tr class="odd">
<td><p><a href="accessing-a-device-on-a-sercx2-managed-serial-port.md" data-raw-source="[Accessing a Device on a SerCx2-Managed Serial Port](accessing-a-device-on-a-sercx2-managed-serial-port.md)">访问 SerCx2 托管串行端口上的设备</a></p></td>
<td><p>SerCx2 和串行控制器驱动程序合作共同管理永久连接到外围设备的串行端口。 若要访问 SerCx2 托管的串行端口上的外围设备，您外围设备的驱动程序打开串行端口的逻辑连接，并获取文件句柄来表示此连接。 然后驱动程序使用此句柄将 I/O 请求发送到端口。</p></td>
</tr>
</tbody>
</table>
