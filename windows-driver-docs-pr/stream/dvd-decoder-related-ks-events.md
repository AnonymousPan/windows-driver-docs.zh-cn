---
title: 与 DVD 解码器相关的 KS 事件
description: 与 DVD 解码器相关的 KS 事件
ms.assetid: 19fd2c88-72f4-4742-8c96-74be250dd59d
keywords:
- DVD 解码器微型驱动程序 WDK，KS 事件
- 解码器微型驱动程序 WDK DVD、KS 事件
- KS 事件 WDK DVD 解码器
- 事件 WDK DVD 解码器
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 48b4ba49b095627a0a832b3978f0c8c965179bfb
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90105076"
---
# <a name="dvd-decoder-related-ks-events"></a>与 DVD 解码器相关的 KS 事件





下表描述了内核流式处理事件集及其与 DVD 解码器硬件相关的相应事件：

[KSEVENTSETID \_ VPNotify](./kseventsetid-vpnotify.md)事件集对与调谐器事件相关的所有内核流式处理事件进行分组。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>KSEVENTSETID_VPNotify KS 事件</th>
<th>事件说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="/windows-hardware/drivers/stream/ksevent-vpnotify-formatchange" data-raw-source="[&lt;strong&gt;KSEVENT_VPNOTIFY_FORMATCHANGE&lt;/strong&gt;](./ksevent-vpnotify-formatchange.md)"><strong>KSEVENT_VPNOTIFY_FORMATCHANGE</strong></a></p></td>
<td><p>向 DirectShow 通知视频端口配置更改，如从640x480 到720x480 的分辨率更改。</p></td>
</tr>
</tbody>
</table>

 

