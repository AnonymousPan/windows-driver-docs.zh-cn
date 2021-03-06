---
title: .typeopt（设置类型选项）
description: .Typeopt 命令设置或显示类型选项。
ms.assetid: 17842897-26e3-4b61-aa65-e5cfe8576324
keywords:
- .typeopt （设置类型选项） Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- .typeopt (Set Type Options)
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: cdf33bf31c7e45f0375b467675cc040db9ee910a
ms.sourcegitcommit: 0d684828f1cabcde6c4f87bec7d9451997f2fa8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67302034"
---
# <a name="typeopt-set-type-options"></a>.typeopt（设置类型选项）


**.Typeopt**命令设置或显示类型选项。

```dbgcmd
.typeopt +Flags 
.typeopt -Flags 
.typeopt +FlagName 
.typeopt -FlagName 
.typeopt 
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="______________"></span> **+**    
指定的类型选项将导致*标志*或*FlagName*设置。

<span id="_______-______"></span> **-**    
指定的类型选项将导致*标志*或*FlagName*要清除。

<span id="_______Flags______"></span><span id="_______flags______"></span><span id="_______FLAGS______"></span> *标志*   
指定要更改的类型选项。 *标志*可以是任意以下值 （没有默认值） 的总和：

<span id="0x1"></span><span id="0X1"></span>**0x1**  
显示所有监视窗口和局部变量窗口中的为具有 UNICODE 数据类型中的 16 位无符号的整数值。

<span id="0x2"></span><span id="0X2"></span>**0x2**  
将签名的所有监视窗口和局部变量窗口中的 32 位整数值时显示的默认基数的无符号整数。

<span id="0x4"></span><span id="0X4"></span>**0x4**  
显示为默认基数中的无符号值的有符号整数的所有监视窗口和局部变量窗口中的所有大小。

<span id="0x8"></span><span id="0X8"></span>**0x8**  
使调试器局部变量窗口或监视窗口中按名称引用一个符号，但没有匹配此名称的多个符号时选择的匹配符号宽度的最大大小。 按如下所示定义符号的大小： 如果符号为函数的名称，其大小是在内存中函数的大小。 否则，符号的大小为它所代表的数据类型的大小。

<span id="_______FlagName______"></span><span id="_______flagname______"></span><span id="_______FLAGNAME______"></span> *FlagName*   
指定要更改的类型选项。 *FlagName*可以是以下字符串 （没有默认值） 的任何一个：

<span id="uni"></span><span id="UNI"></span>**uni**  
显示所有监视窗口和局部变量窗口中的为具有 UNICODE 数据类型中的 16 位无符号的整数值。 (这具有相同的效果**0x1**。)

<span id="longst"></span><span id="LONGST"></span>**longst**  
将签名的所有监视窗口和局部变量窗口中的 32 位整数值时显示的默认基数的无符号整数。 (这具有相同的效果**0x2**。)

<span id="radix"></span><span id="RADIX"></span>**radix**  
显示为默认基数中的无符号值的有符号整数的所有监视窗口和局部变量窗口中的所有大小。 (这具有相同的效果**0x4**。)

<span id="size"></span><span id="SIZE"></span>**size**  
使调试器局部变量窗口或监视窗口中按名称引用一个符号，但没有匹配此名称的多个符号时选择的匹配符号宽度的最大大小。 按如下所示定义符号的大小： 如果符号为函数的名称，其大小是在内存中函数的大小。 否则，符号的大小为它所代表的数据类型的大小。 (这具有相同的效果**0x8**。)

### <a name="span-idenvironmentspanspan-idenvironmentspanspan-idenvironmentspanenvironment"></a><span id="Environment"></span><span id="environment"></span><span id="ENVIRONMENT"></span>环境

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>模式</strong></p></td>
<td align="left"><p>用户模式下，内核模式</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>目标</strong></p></td>
<td align="left"><p>实时、 崩溃转储</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>平台</strong></p></td>
<td align="left"><p>全部</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

不带任何参数， **.typeopt**显示当前符号选项。

若要更改默认基数，请使用[ **n (设置数量 Base)** ](n--set-number-base-.md)命令。

 





