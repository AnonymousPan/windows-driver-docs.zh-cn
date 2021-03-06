---
title: 'PcRegisterAdapterPower 规则 (音频) '
description: PcRegisterAdapterPower 规则指定 PortCls 微型端口驱动程序不应调用 PcRegisterAdapterPowerManagement 两次，而不会对 PcUnregisterAdapterPowerManagement 调用 PcUnregisterAdapterPowerManagement。
ms.assetid: 8F6E6B1D-F19C-469A-BC5A-061996BEA532
ms.date: 05/21/2018
keywords:
- 'PcRegisterAdapterPower 规则 (音频) '
topic_type:
- apiref
api_name:
- PcRegisterAdapterPower
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 5e200ff31841c75dcca2810b1b7560380aa5f9e3
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90103978"
---
# <a name="pcregisteradapterpower-rule-audio"></a>PcRegisterAdapterPower 规则 (音频) 


PcRegisterAdapterPower 规则指定 PortCls 微型端口驱动程序不应：

-   调用 [**PcRegisterAdapterPowerManagement**](/windows-hardware/drivers/ddi/portcls/nf-portcls-pcregisteradapterpowermanagement) 两次，无需对 [**PcUnregisterAdapterPowerManagement**](/windows-hardware/drivers/ddi/portcls/nf-portcls-pcunregisteradapterpowermanagement)调用干预。
-   请先调用 [**PcUnregisterAdapterPowerManagement**](/windows-hardware/drivers/ddi/portcls/nf-portcls-pcunregisteradapterpowermanagement) ，然后再调用 [**PcRegisterAdapterPowerManagement**](/windows-hardware/drivers/ddi/portcls/nf-portcls-pcregisteradapterpowermanagement) 。

**驱动程序模型：音频**

**Bug 检查 () 发现此规则**： [**bug 检查0XC4：驱动程序 \_ 验证器 \_ 检测到 \_ 违反**](../debugger/bug-check-0xc4--driver-verifier-detected-violation.md) (0x00071006) 


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
<td align="left"><p>若要验证此规则，请打开 "命令提示符" 窗口。 输入 Driver Verifier 命令并指定 <strong>/domain 音频</strong>。</p>
<p>例如：</p>
<p><strong>verifier/domain 音频</strong>[<em>options</em>] <strong>/driver</strong> <em> &lt; yourdriver &gt; </em></p>
<p>有关详细信息，请参阅<a href="/windows-hardware/drivers/devtest/driver-verifier" data-raw-source="[Driver Verifier](./driver-verifier.md)">驱动程序验证程序</a>。</p></td>
</tr>
</tbody>
</table>

 

