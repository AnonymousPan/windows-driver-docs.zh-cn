---
title: 调试\_筛选器\_XXX
description: 调试\_筛选器\_XXX
ms.assetid: 1f8f738b-7b2b-419a-949e-b71f937de02d
ms.date: 12/07/2017
keywords:
- DEBUG_FILTER_XXX Windows 调试
topic_type:
- apiref
api_name:
- DEBUG_FILTER_XXX
api_location:
- DbgEng.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.openlocfilehash: 9df8e3b120f5524ee29e376c0a691f5f0e297cfe
ms.sourcegitcommit: a39a3f4c9f26968e00317574c0d8530ee8ab6f8b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894237"
---
# <a name="debugfilterxxx"></a>调试\_筛选器\_XXX


调试\_筛选器\_*XXX*常量来针对三个不同的用途： 指定单个特定的事件筛选器，以指定的中断状态的事件筛选器，并指定的处理状态异常筛选器。

### <a name="span-idspecificeventfilterspanspan-idspecificeventfilterspanspecific-event-filter"></a><span id="specific_event_filter"></span><span id="SPECIFIC_EVENT_FILTER"></span>特定事件筛选器

以下常量用于指定特定的事件筛选器。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">ReplTest1</th>
<th align="left">Event</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_CREATE_THREAD</p></td>
<td align="left"><p>创建线程</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_EXIT_THREAD</p></td>
<td align="left"><p>退出线程</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_CREATE_PROCESS</p></td>
<td align="left"><p>创建进程</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_EXIT_PROCESS</p></td>
<td align="left"><p>退出进程</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_LOAD_MODULE</p></td>
<td align="left"><p>负载模块</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_UNLOAD_MODULE</p></td>
<td align="left"><p>卸载模块</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_SYSTEM_ERROR</p></td>
<td align="left"><p>系统错误</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_INITIAL_BREAKPOINT</p></td>
<td align="left"><p>初始断点</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_INITIAL_MODULE_LOAD</p></td>
<td align="left"><p>初始模块加载</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_DEBUGGEE_OUTPUT</p></td>
<td align="left"><p>目标输出</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idbreakstatusspanspan-idbreakstatusspanbreak-status"></a><span id="break_status"></span><span id="BREAK_STATUS"></span>会中断状态

以下常量用于指定事件筛选器的中断状态。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">值</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_BREAK</p></td>
<td align="left"><p>该事件将进入调试器。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_SECOND_CHANCE_BREAK</p></td>
<td align="left"><p>如果它是第二个机会异常，该事件将进入调试器。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_OUTPUT</p></td>
<td align="left"><p>事件的通知将被打印到调试器控制台。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_IGNORE</p></td>
<td align="left"><p>将忽略该事件。</p></td>
</tr>
</tbody>
</table>

 

此外，对于任意异常筛选器，将中断状态设置为调试\_筛选器\_删除，请移除事件的筛选器。

### <a name="span-idhandlingstatusspanspan-idhandlingstatusspanhandling-status"></a><span id="handling_status"></span><span id="HANDLING_STATUS"></span>处理状态

以下常量用于指定异常筛选器的处理状态。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">ReplTest1</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DEBUG_FILTER_GO_HANDLED</p></td>
<td align="left"><p>已处理了异常。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEBUG_FILTER_GO_NOT_HANDLED</p></td>
<td align="left"><p>未处理异常。</p></td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">DbgEng.h （包括 DbgEng.h）</td>
</tr>
</tbody>
</table>

 

 





