---
title: 通用 I/O (GPIO) 驱动程序设计指南
description: 此部分介绍如何为常规用途 I/O (GPIO) 控制器设备编写驱动程序。
ms.assetid: D11E72AC-2B0D-4325-8BD0-9AE9B21AFD8D
ms.date: 04/20/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
author: EliotSeattle
ms.openlocfilehash: 313f848dbf429e0c3b117eedf9340436700fc555
ms.sourcegitcommit: 988d100e4d3b218a59fdac034d39a1816d145c85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2020
ms.locfileid: "72824941"
---
# <a name="general-purpose-io-gpio-driver-design-guide"></a>通用 I/O (GPIO) 驱动程序设计指南


此部分介绍如何为常规用途 I/O (GPIO) 控制器设备编写驱动程序。 GPIO 控制器可以配置 GPIO 引脚，使之执行低速数据 I/O 操作、充当设备选择器，以及接收中断请求。 从 Windows 8 开始，GPIO 框架扩展 (GpioClx) 简化了为 GPIO 控制器编写驱动程序的任务。 另外，GpioClx 还提供了统一的 I/O 请求接口，方便外围设备驱动程序与连接到控制器上的 GPIO 引脚的设备通信。

## <a name="in-this-section"></a>本部分内容


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>主题</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-driver-support-overview" data-raw-source="[GPIO Driver Support Overview](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-driver-support-overview)">GPIO 驱动程序支持概述</a></p></td>
<td><p>从 Windows 8 开始，GPIO 框架扩展 (GpioClx) 简化了为 GPIO 控制器设备编写驱动程序的任务。 另外，GpioClx 还为连接到 GPIO 引脚的外围设备提供驱动程序支持。 GpioClx 是系统提供的针对内核模式驱动程序框架 (KMDF) 的扩展，其执行的处理任务对于 GPIO 设备类的成员来说很常见。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpioclx-i-o-and-interrupt-interfaces" data-raw-source="[GpioClx I/O and Interrupt Interfaces](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpioclx-i-o-and-interrupt-interfaces)">GpioClx I/O 和中断接口</a></p></td>
<td><p>通常情况下，GPIO 控制器的客户端是连接到 GPIO 引脚的外围设备的驱动程序。 这些驱动程序使用 GPIO 引脚作为低带宽数据通道、设备选择器输出和中断请求输入。 外围设备驱动程序打开到 GPIO 引脚的逻辑连接，这些引脚已配置为数据输入或输出。 它们使用这些连接将 I/O 请求发送到这些引脚。 另外，外围设备驱动程序可以通过逻辑方式将其中断服务例程连接到已配置为中断请求输入的 GPIO 引脚。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-based-hardware-resources" data-raw-source="[GPIO-Based Hardware Resources](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-based-hardware-resources)">基于 GPIO 的硬件资源</a></p></td>
<td><p>从 Windows 8 开始，受 GPIO 控制器驱动程序控制的常规用途 I/O (GPIO) 引脚可以作为系统管理的硬件资源供其他驱动程序使用。 GPIO I/O 的引脚是已配置为数据输入或数据输出的引脚，可以作为新的 Windows 资源类型（即 <em>GPIO I/O 资源</em>）使用。 另外，GPIO 中断引脚是已配置为中断请求输入的引脚，可以作为普通 Windows 中断资源使用。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-interrupts" data-raw-source="[GPIO Interrupts](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-interrupts)">GPIO 中断</a></p></td>
<td><p>某些常规用途 I/O (GPIO) 控制器设备可以配置其 GPIO 引脚，使之充当中断请求输入。 这些中断请求输入由通过物理方式连接到 GPIO 引脚的外围设备驱动。 这些 GPIO 控制器的驱动程序可以启用、禁用、屏蔽、取消屏蔽以及清除单个 GPIO 引脚上的中断请求。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpioclx-ddi" data-raw-source="[GpioClx DDI](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpioclx-ddi)">GpioClx DDI</a></p></td>
<td><p>常规用途 I/O (GPIO) 控制器驱动程序通过 GpioClx 设备驱动程序接口 (DDI) 与 GPIO 框架扩展 (GpioClx) 通信。 此 DDI 在 Gpioclx.h 头文件中定义，并在<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/index" data-raw-source="[General-Purpose I/O (GPIO) Driver Reference](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)">常规用途 I/O (GPIO) 驱动程序参考</a>中进行了说明。 作为此 DDI 的一部分，GpioClx 实现多个<a href="https://docs.microsoft.com/previous-versions/hh439460(v=vs.85)" data-raw-source="[driver support methods](https://docs.microsoft.com/previous-versions/hh439460(v=vs.85))">驱动程序支持方法</a>，这些方法由 GPIO 控制器驱动程序调用。 此驱动程序实现了一组<a href="https://docs.microsoft.com/previous-versions/hh439464(v=vs.85)" data-raw-source="[event callback functions](https://docs.microsoft.com/previous-versions/hh439464(v=vs.85))">事件回调函数</a>，这些函数由 GpioClx 调用。 GpioClx 使用这些回调来管理已配置为中断输入的 GPIO 引脚提供的中断请求，并将数据传输到已配置为数据输入和输出的 GPIO 引脚，或者从其传输出来。</p></td>
</tr>
</tbody>
</table>

 

 

 




