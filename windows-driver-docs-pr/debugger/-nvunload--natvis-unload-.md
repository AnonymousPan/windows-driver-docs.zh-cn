---
title: .nvload（NatVis 卸载）
description: Nvunload 命令从调试器环境中卸载 NatVis 文件。
ms.assetid: E63BE2B5-291B-4F78-98FF-C1D7663A184E
keywords:
- nvunload (NatVis 卸载) Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- .nvunload (NatVis Unload)
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: bca9a103b183db5ba914c3d9fdae412c388baec4
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89211251"
---
# <a name="nvunload-natvis-unload"></a>.nvload（NatVis 卸载）

Nvunload 命令从调试器环境中卸载 NatVis 文件。

```dbgcmd
.nvunload FileName|ModuleName  
```

*FileName |ModuleName*

指定要卸载的 NatVis 文件名或模块名称。

**FileName**是要卸载的 natvis 文件的显式名称。 可以使用完全限定的路径。

**ModuleName**是正在调试的目标进程中的模块的名称。 嵌入到符号文件中的所有 NatVis 文件 (PDB) 命名的模块名称。

## <a name="environment"></a>环境

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>交货</strong></p></td>
<td align="left"><p>用户模式，内核模式</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>目标</strong></p></td>
<td align="left"><p>实时，故障转储</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>平台</strong></p></td>
<td align="left"><p>全部</p></td>
</tr>
</tbody>
</table>

## <a name="additional-information"></a>其他信息

有关详细信息，请参阅 [创建本机对象的自定义视图](/visualstudio/debugger/create-custom-views-of-native-objects?view=vs-2015)。

## <a name="see-also"></a>另请参阅

[**dx (显示 NatVis 表达式) **](dx--display-visualizer-variables-.md)