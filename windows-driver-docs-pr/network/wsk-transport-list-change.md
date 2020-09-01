---
title: WSK_TRANSPORT_LIST_CHANGE
description: WSK_TRANSPORT_LIST_CHANGE
ms.assetid: 3b12d692-467c-4d31-bd2a-bb6e34d87fde
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 WSK_TRANSPORT_LIST_CHANGE 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: c25399bfc09649acd0e98fe23b8a6d217816a3c8
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89216072"
---
# <a name="wsk_transport_list_change"></a>WSK \_ 传输 \_ 列表 \_ 更改


WSK 应用程序使用 WSK \_ 传输 \_ 列表 \_ 更改客户端控制操作，以便在可用网络传输列表发生更改时接收通知。

若要在可用网络传输列表发生更改时接收通知，WSK 应用程序需要使用以下参数调用 [**WskControlClient**](/windows-hardware/drivers/ddi/wsk/nc-wsk-pfn_wsk_control_client) 函数。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ControlCode</em></p></td>
<td><p>WSK_TRANSPORT_LIST_CHANGE</p></td>
</tr>
<tr class="even">
<td><p><em>InputSize</em></p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p><em>InputBuffer</em></p></td>
<td><p>Null</p></td>
</tr>
<tr class="even">
<td><p><em>OutputSize</em></p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p><em>OutputBuffer</em></p></td>
<td><p>Null</p></td>
</tr>
<tr class="even">
<td><p><em>OutputSizeReturned</em></p></td>
<td><p>Null</p></td>
</tr>
<tr class="odd">
<td><p><em>Irp</em></p></td>
<td><p>指向 IRP 的指针，该 IRP 由 WSK 子系统排队，直到可用网络传输列表更改。 添加新的网络传输或删除现有网络传输后，WSK 子系统将完成 IRP。</p></td>
</tr>
</tbody>
</table>

此客户端控制操作需要 IRP。

如果 WSK 应用程序调用 [**WskDeregister**](/windows-hardware/drivers/ddi/wsk/nf-wsk-wskderegister) 将其自身从 WSK 子系统分离，则 WSK 子系统将取消任何挂起的 irp。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>版本</p></td>
<td><p>在 Windows Vista 和更高版本的 Windows 操作系统中可用。</p></td>
</tr>
<tr class="even">
<td><p>标头</p></td>
<td>Wsk (包含 Wsk) </td>
</tr>
</tbody>
</table>

 

