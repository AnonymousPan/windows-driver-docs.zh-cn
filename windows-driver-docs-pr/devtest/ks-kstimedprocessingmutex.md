---
title: 'KsTimedProcessingMutex 规则 ( # A1'
description: KsTimedProcessingMutex 规则指定一个 KS 微型端口驱动程序不应将处理互斥体保留超过100毫秒。
ms.assetid: 18246AAE-6328-4171-973E-4C762CF719AE
ms.date: 05/21/2018
keywords:
- 'KsTimedProcessingMutex 规则 ( # A1'
topic_type:
- apiref
api_name:
- KsTimedProcessingMutex
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 13f7e293f25771f22f5916f11a9c9b53244f9e66
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90103410"
---
# <a name="kstimedprocessingmutex-rule-"></a>KsTimedProcessingMutex 规则 ( # A1


KsTimedProcessingMutex 规则指定一个 KS 微型端口驱动程序不应将处理互斥体保留超过100毫秒。

**驱动程序模型： KS**

**Bug 检查 () 发现此规则**： [**bug 检查0XC4：驱动程序 \_ 验证器 \_ 检测到 \_ 违反**](../debugger/bug-check-0xc4--driver-verifier-detected-violation.md) (0x00082005) 


<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在运行时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>若要验证此规则，请打开 "命令提示符" 窗口。 输入 Driver Verifier 命令并指定 <strong>/domain ks</strong>。</p>
<p>例如：</p>
<p><strong>验证程序/domain ks</strong> [<em>options</em>] <strong>/driver</strong> <em> &lt; &gt; yourdriver</em></p>
<p>有关详细信息，请参阅<a href="/windows-hardware/drivers/devtest/driver-verifier" data-raw-source="[Driver Verifier](./driver-verifier.md)">驱动程序验证程序</a>。</p></td>
</tr>
</tbody>
</table>

 

<a name="see-also"></a>另请参阅
--------

[在 AVStream 中处理互斥](../stream/processing-mutex-in-avstream.md)
