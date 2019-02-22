---
title: gflag
description: Gflag 扩展设置，或显示全局标志。
ms.assetid: b661f775-a313-4a4d-a3db-1e4dacf830de
keywords:
- gflag Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- gflag
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: e741a1e6f14c1b347692c68717f9566cf840868a
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56521624"
---
# <a name="gflag"></a>！ gflag


**！ Gflag**扩展插件设置，或显示全局标志。

```dbgcmd
!gflag [+|-] Value 
!gflag {+|-} Abbreviation 
!gflag -? 
!gflag 
```

## <a name="span-idddkgflagdbgspanspan-idddkgflagdbgspanparameters"></a><span id="ddk__gflag_dbg"></span><span id="DDK__GFLAG_DBG"></span>参数


<span id="_______Value______"></span><span id="_______value______"></span><span id="_______VALUE______"></span> *值*   
指定 32 位十六进制数。 如果不使用加号 (**+**) 或减号 (**-**)，此数目将变为全局标志位域的新值。 如果添加一个加号 (**+**) 之前此编号，数指定一个或多个全局标志位将设置为 1。 如果添加负号 (**-**) 之前此编号，数指定一个或多个全局标志位设置为零。

<span id="_______Abbreviation______"></span><span id="_______abbreviation______"></span><span id="_______ABBREVIATION______"></span> *Abbreviation*   
指定单个全局标志。 *缩写*是一个全局标志，设置为 1 的三个字母缩写 (**+**) 或为零 (**-**)。

<span id="_______-_______"></span> **-?**   
显示此扩展，包括全局标志缩写的列表中的一些帮助文本[调试器命令窗口](debugger-command-window.md)。

### <a name="span-iddllspanspan-iddllspandll"></a><span id="DLL"></span><span id="dll"></span>DLL

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Windows 2000</strong></p></td>
<td align="left"><p></p>
Kdextx86.dll Ntsdexts.dll</td>
</tr>
<tr class="even">
<td align="left"><p><strong>Windows XP 及更高版本</strong></p></td>
<td align="left"><p>Exts.dll</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idadditionalinformationspanspan-idadditionalinformationspanspan-idadditionalinformationspanadditional-information"></a><span id="Additional_Information"></span><span id="additional_information"></span><span id="ADDITIONAL_INFORMATION"></span>其他信息

此外可以通过使用全局标志实用程序 (Gflags.exe) 来设置这些标志。

<a name="remarks"></a>备注
-------

如果未指定任何参数， **！ gflag**扩展将显示当前全局标志设置。

下表包含可用于的缩写*缩写*参数。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">值</th>
<th align="left">名称</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x00000001</p></td>
<td align="left"><p>&quot;soe&quot;</p></td>
<td align="left"><p>停止的异常。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00000002</p></td>
<td align="left"><p>&quot;sls&quot;</p></td>
<td align="left"><p>显示加载程序的快照。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00000004</p></td>
<td align="left"><p>&quot;dic&quot;</p></td>
<td align="left"><p>调试初始命令。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00000008</p></td>
<td align="left"><p>&quot;shg&quot;</p></td>
<td align="left"><p>停止，如果图形用户界面停止响应 （即，挂起）。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00000010</p></td>
<td align="left"><p>&quot;htc&quot;</p></td>
<td align="left"><p>启用堆结尾检查。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00000020</p></td>
<td align="left"><p>&quot;hfc&quot;</p></td>
<td align="left"><p>启用堆免费检查。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00000040</p></td>
<td align="left"><p>&quot;hpc&quot;</p></td>
<td align="left"><p>启用堆参数检查。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00000080</p></td>
<td align="left"><p>&quot;hvc&quot;</p></td>
<td align="left"><p>启用在调用堆验证。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00000100</p></td>
<td align="left"><p>&quot;ptc&quot;</p></td>
<td align="left"><p>启用池结尾检查。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00000200</p></td>
<td align="left"><p>&quot;pfc&quot;</p></td>
<td align="left"><p>启用免费检查池。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00000400</p></td>
<td align="left"><p>&quot;ptg&quot;</p></td>
<td align="left"><p>启用池标记。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00000800</p></td>
<td align="left"><p>&quot;htg&quot;</p></td>
<td align="left"><p>启用堆标记。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00001000</p></td>
<td align="left"><p>&quot;ust&quot;</p></td>
<td align="left"><p>创建用户模式下的堆栈跟踪数据库。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00002000</p></td>
<td align="left"><p>&quot;kst&quot;</p></td>
<td align="left"><p>创建内核模式堆栈跟踪数据库。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00004000</p></td>
<td align="left"><p>&quot;otl&quot;</p></td>
<td align="left"><p>维护的每种类型的对象的列表。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00008000</p></td>
<td align="left"><p>&quot;htd&quot;</p></td>
<td align="left"><p>启用堆标记的 DLL。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00010000</p></td>
<td align="left"><p>&quot;idp&quot;</p></td>
<td align="left"><p>未使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00020000</p></td>
<td align="left"><p>&quot;d32&quot;</p></td>
<td align="left"><p>启用调试的 Microsoft Win32 子系统。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00040000</p></td>
<td align="left"><p>&quot;ksl&quot;</p></td>
<td align="left"><p>启用内核调试程序符号加载。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00080000</p></td>
<td align="left"><p>&quot;dps&quot;</p></td>
<td align="left"><p>禁用分页的内核堆栈。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00100000</p></td>
<td align="left"><p>&quot;scb&quot;</p></td>
<td align="left"><p>启用关键系统分隔线。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00200000</p></td>
<td align="left"><p>&quot;dhc&quot;</p></td>
<td align="left"><p>禁用堆上免费 coalesce。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x00400000</p></td>
<td align="left"><p>&quot;ece&quot;</p></td>
<td align="left"><p>启用关闭异常。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x00800000</p></td>
<td align="left"><p>&quot;eel&quot;</p></td>
<td align="left"><p>启用异常日志记录。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x01000000</p></td>
<td align="left"><p>&quot;eot&quot;</p></td>
<td align="left"><p>启用对象句柄类型标记。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x02000000</p></td>
<td align="left"><p>&quot;hpa&quot;</p></td>
<td align="left"><p>将放在页面末尾的堆分配。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x04000000</p></td>
<td align="left"><p>&quot;dwl&quot;</p></td>
<td align="left"><p>调试 WINLOGON。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x08000000</p></td>
<td align="left"><p>&quot;ddp&quot;</p></td>
<td align="left"><p>禁用内核模式<strong>DbgPrint</strong>并<strong>KdPrint</strong>输出。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x10000000</p></td>
<td align="left"><p>NULL</p></td>
<td align="left"><p>未使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x20000000</p></td>
<td align="left"><p>&quot;sue&quot;</p></td>
<td align="left"><p>停止在未经处理的用户模式异常</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x40000000</p></td>
<td align="left"><p>NULL</p></td>
<td align="left"><p>未使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x80000000</p></td>
<td align="left"><p>&quot;dpd&quot;</p></td>
<td align="left"><p>禁用受保护的 DLL 验证。</p></td>
</tr>
</tbody>
</table>

 

 

 




