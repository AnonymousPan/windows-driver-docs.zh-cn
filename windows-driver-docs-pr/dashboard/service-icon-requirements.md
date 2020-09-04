---
title: 服务图标要求
description: 服务图标要求
ms.assetid: ce018a26-f5ce-4fbb-8339-b3207ca5ed68
ms.topic: article
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f6803dc5e2f844b60e0005749d590f3e803860b0
ms.sourcegitcommit: 4f08f5686c0bbc27d58930b993cbab1a98e3afb0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "89443927"
---
# <a name="service-icon-requirements"></a>服务图标要求


服务图标用来在 Windows 连接管理器中显示移动网络运营商 (MNO) 或移动虚拟网络运营商 (MVNO) 的徽标。

文件格式必须为 .ICO，且满足以下任一要求：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>256x256:32bit+Alpha（压缩）</p></td>
<td><p>24x24:32bit+Alpha</p></td>
</tr>
<tr class="even">
<td><p>48x48:32bit+Alpha</p></td>
<td><p>24x24:8bit256</p></td>
</tr>
<tr class="odd">
<td><p>48x48:8bit256</p></td>
<td><p>24x24:4bit16</p></td>
</tr>
<tr class="even">
<td><p>48x48:4bit16</p></td>
<td><p>16x16:32bit+Alpha</p></td>
</tr>
<tr class="odd">
<td><p>32x32:32bit+Alpha</p></td>
<td><p>16x16:8bit256</p></td>
</tr>
<tr class="even">
<td><p>32x32:8bit256</p></td>
<td><p>16x16:4bit16</p></td>
</tr>
<tr class="odd">
<td><p>32x32：4 位 16</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

服务图标与服务元数据包的 [ServiceInfo XML](../mobilebroadband/serviceinfo-xml-schema.md) 架构中的 [ServiceIconFile](../mobilebroadband/serviceiconfile.md) 元素相关联。

## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>相关主题

- [创建移动宽带体验](./create-a-mobile-broadband-experience.md)

 

