---
title: WDI_TLV_SSID
description: WDI_TLV_SSID 是包含 SSID TLV。
ms.assetid: 31391E25-B507-4652-9D70-9DA0D6245CA8
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 WDI_TLV_SSID 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 12ea12a875c7ffa359dd0da4a21ea88128caad89
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63330427"
---
# <a name="wditlvssid"></a>WDI\_TLV\_SSID


WDI\_TLV\_SSID 是包含 SSID TLV。

## <a name="tlv-type"></a>TLV 类型


0x3B

## <a name="length"></a>长度


UINT8 元素的数组大小 （以字节为单位）。 允许数组长度为 0。

## <a name="values"></a>值


| 在任务栏的搜索框中键入      | 描述                                        |
|-----------|----------------------------------------------------|
| UINT8\[\] | 指定 SSID UINT8 元素的数组。 |

 

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低受支持的客户端</p></td>
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wditypes.hpp</td>
</tr>
</tbody>
</table>

 

 




