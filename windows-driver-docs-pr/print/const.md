---
title: Const (TCP/IP)
description: TCP/IP Const 构造定义必须返回的数据类型和值。
ms.assetid: a0ede11d-ada4-4dc4-87a4-68c96635c0fd
keywords:
- Const 构造
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 6b36f92246e2a41abd9767e86849deb7c20b05a3
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90106104"
---
# <a name="const-tcpip"></a>Const (TCP/IP)


TCP/IP Const 构造定义必须返回的数据类型和值。 Const 用于不在值中更改的元素。 Const 构造是在 Tcpbidi 中定义的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribute</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>name</strong></p></td>
<td><p>架构值的名称。</p></td>
</tr>
<tr class="even">
<td><p>type</p></td>
<td><p><strong>值</strong>特性中的数据类型， <a href="/windows-hardware/drivers/ddi/winspool/ne-winspool-bidi_type" data-raw-source="[&lt;strong&gt;BIDI_TYPE&lt;/strong&gt;](/windows-hardware/drivers/ddi/winspool/ne-winspool-bidi_type)"><strong>BIDI_TYPE</strong></a>枚举中的值。</p></td>
</tr>
<tr class="odd">
<td><p><strong>value</strong></p></td>
<td><p>包含常量值的字符串。</p></td>
</tr>
</tbody>
</table>

 

### <a name="code-example"></a>代码示例

下面的代码示例通过将 `Extension` 属性添加到属性 `Printer` ，并将属性添加到属性来扩展双向通信架构 `Version` `Extension` 。 在此示例中， `Extension` 包含一个常 **数值** 项 `Category` 。 此外， `Version` 有两个常 **数值** 项 `Major` 和 `Minor` 。

```cpp
<Property name="Printer">
  <Property name="Extension">
    <Const name="Category" type="BIDI_STRING" value="Extension"/>
    <Property name="Version">
      <Const name="Major" type="BIDI_INT" value="1"/>
      <Const name="Minor" type="BIDI_INT" value="0"/>
    </Property>
  </Property>
</Property>
```

前面的示例将生成以下查询：

```cpp
\Printer.Extension:Category
\Printer.Extension.Version:Major
\Printer.Extension.Version:Minor
```

