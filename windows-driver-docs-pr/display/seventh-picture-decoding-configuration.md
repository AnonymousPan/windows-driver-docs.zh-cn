---
title: 第七个图片解码配置
description: 第七个图片解码配置
ms.assetid: eb52cdb4-4009-4860-80ac-5c2172f8a9b3
keywords:
- 压缩的图片解码设置 WDK DirectX VA
- 图片解码设置 WDK DirectX VA
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 641f63be89625c0f60a2cf2614a5998489d4b198
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89067228"
---
# <a name="seventh-picture-decoding-configuration"></a>第七个图片解码配置


## <span id="ddk_seventh_picture_decoding_configuration_gg"></span><span id="DDK_SEVENTH_PICTURE_DECODING_CONFIGURATION_GG"></span>


此集中的第七个配置仅为在[**DXVA \_ ConnectMode**](/windows-hardware/drivers/ddi/dxva/ns-dxva-_dxva_connectmode)结构中指示的[mpeg2 \_ C](mpeg2-c.md)和[mpeg2 \_ D](mpeg2-d.md)限制配置文件定义。 在最小互操作集中，任何其他受限制的配置文件都不包括此配置。

此配置 (这不是首选配置) 的定义方式与 [第一个图片解码配置](first-picture-decoding-configuration.md) 相同，但以下情况例外。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">成员</th>
<th align="left">Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>bConfigResidDiffHost</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bConfigResidDiffAccelerator</strong></p></td>
<td align="left"><p>1</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>bConfig4GroupedCoefs</strong></p></td>
<td align="left"><p>1</p></td>
</tr>
</tbody>
</table>

 

 

