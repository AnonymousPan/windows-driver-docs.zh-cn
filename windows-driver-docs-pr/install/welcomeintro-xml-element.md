---
title: welcomeIntro XML 元素
description: welcomeIntro XML 元素
ms.assetid: d0325d14-c31a-453d-b28e-4bdb646d0711
keywords:
- welcomeIntro XML 元素设备和驱动程序安装
topic_type:
- apiref
api_name:
- welcomeIntro XML Element
api_type:
- NA
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 7aa3ef3d3e64ee92e1977410dfa79161668123f9
ms.sourcegitcommit: 4db5f9874907c405c59aaad7bcc28c7ba8280150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2020
ms.locfileid: "89094811"
---
# <a name="welcomeintro-xml-element"></a>welcomeIntro XML 元素


\[DIFx 已弃用，有关详细信息，请参阅 [DIFx 指导原则](./difx-guidelines.md)。\]

**WelcomeIntro** XML 元素自定义 DPInst 欢迎页上的主文本。

### <a name="element-tag"></a>元素标记

```cpp
<welcomeIntro>
```

### <a name="xml-attributes"></a>XML 属性

无

### <a name="element-information"></a>**元素信息**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>父元素</strong></p></td>
<td align="left"><p><a href="language-xml-element.md" data-raw-source="[&lt;strong&gt;language&lt;/strong&gt;](language-xml-element.md)"><strong>语言</strong></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>子元素</strong></p></td>
<td align="left"><p>不允许</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>数据内容</strong></p></td>
<td align="left"><p>自定义欢迎页上的主文本的字符串</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>重复的子元素</strong></p></td>
<td align="left"><p>不允许</p></td>
</tr>
</tbody>
</table>

 

### <a name="remarks"></a><a href="" id="comments"></a>注释

下面的代码示例演示了自定义欢迎页上的主文本的 **welcomeIntro** 元素。 指定自定义欢迎简介的文本以粗体显示。

```cpp
<dpinst>
  ...
  <language code="0x0409">
    . . .
    <welcomeIntro>This wizard will walk you through updating the drivers for your Toaster device.</welcomeIntro>
    ...
  </language>
  ...
</dpinst>
```

如果未指定 **welcomeIntro** 元素，则 DPInst 将显示默认的 "欢迎使用" 页上显示的默认主文本。

## <a name="see-also"></a>另请参阅


[**语言**](language-xml-element.md)

 

