---
title: 他
description: 他的扩展插件都会显示在指定的处理器，使用的程序计数器符号的中断历史记录。
ms.assetid: 3b91e8aa-5639-4273-9da4-1927d2ae8c62
keywords:
- 中断历史记录
- 他的 Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- ihs
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 127a1465808b6a4add79ad70f3d323547270f393
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63336443"
---
# <a name="ihs"></a>!ihs


**！ 他**扩展插件都会显示在指定的处理器，使用的程序计数器符号的中断历史记录。

```dbgcmd
!ihs Processor 
```

**重要**  此命令已被 Windows 调试器版本 10.0.14257 中不推荐使用和更高版本，并不再可用。

 

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="_______Processor______"></span><span id="_______processor______"></span><span id="_______PROCESSOR______"></span> *Processor*   
指定一个处理器。 如果*处理器*是省略，使用当前的处理器。

### <a name="span-iddllspanspan-iddllspandll"></a><span id="DLL"></span><span id="dll"></span>DLL

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Windows 2000</strong></p></td>
<td align="left"><p>不可用</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Windows XP 及更高版本</strong></p></td>
<td align="left"><p>Kdexts.dll</p></td>
</tr>
</tbody>
</table>

 

此扩展命令仅用于 Itanium 目标计算机。

<a name="remarks"></a>备注
-------

若要显示中断历史记录，而不使用的程序计数器符号，请使用[ **！ ih** ](-ih.md)扩展。 若要启用的中断历史记录，请添加 **/configflag = 32**为启动项选项。

下面是输出的来自此扩展插件示例：

```dbgcmd
kd> !ihs
Total # of interruptions = 2093185
Vector              IIP                   IPSR          ExtraField            IIP Symbol
        VHPT FAULT  e0000000830d3190      1010092a6018  IFA=      6fc00a0200c nt!MiAgeAndEstimateAvailableInWorkingSet+0x70
        VHPT FAULT  e0000000830d33d0      1010092a6018  IFA= 1ffffe00001de2d0 nt!MiAgeAndEstimateAvailableInWorkingSet+0x2b0
        VHPT FAULT  e0000000830d33d0      1010092a6018  IFA= 1ffffe01befff338 nt!MiAgeAndEstimateAvailableInWorkingSet+0x2b0
        VHPT FAULT  e0000000830d3190      1010092a6018  IFA=      6fc00a0200c nt!MiAgeAndEstimateAvailableInWorkingSet+0x70
        VHPT FAULT  e0000000830d33d0      1010092a6018  IFA= 1ffffe00001d9188 nt!MiAgeAndEstimateAvailableInWorkingSet+0x2b0
        VHPT FAULT  e0000000830d3880      1010092a6018  IFA= 1ffffe01befff250 nt!MiAgeAndEstimateAvailableInWorkingSet+0x760
        VHPT FAULT  e0000000830d3fb0      1010092a6018  IFA= e0000165f82dc1c0 nt!MiCheckAndSetSystemTrimCriteria+0x190
        VHPT FAULT  e000000083063390      1010092a6018  IFA= e0000000fffe0018 nt!KeQuerySystemTime+0x30
     THREAD SWITCH  e000000085896040  e00000008588c040  OSP= e0000165f82dbd40 
        VHPT FAULT  e00000008329b130      1210092a6018  IFA= e0000165f7edaf30 nt!IopProcessWorkItem+0x30
 VHPT FAULT  e0000165f7eda640      1210092a6018  IFA= e0000165fff968a9 netbios!RunTimerForLana+0x60
    PROCESS SWITCH  e0000000818bbe10  e000000085896040  OSP= e0000165f8281de0 
        VHPT FAULT  e00000008307cfc0      1010092a2018  IFA= e00000008189fe50 nt!SwapFromIdle+0x1e0
EXTERNAL INTERRUPT  e0000000830623b0      1010092a6018  IVR=               d0 nt!Kil_TopOfIdleLoop
        VHPT FAULT  e00000008314e310      1010092a2018  IFA= e0000165f88203f0 nt!KdReceivePacket+0x10
        VHPT FAULT  e000000083580760      1010092a2018  IFA= e0000000f00ff3fd hal!READ_PORT_UCHAR+0x80
    PROCESS SWITCH  e00000008558c990  e0000000818bbe10  OSP= e00000008189fe20 
        VHPT FAULT  e00000008307cfc0      1010092a2018  IFA= e0000165f02433f0 nt!SwapFromIdle+0x1e0
        VHPT FAULT          77cfbda0      1013082a6018  IFA=         77cfbda0 0x0000000077cfbda0
        VHPT FAULT          77cfbdb0      1213082a6018  IFA=      6fbfee0ff98 0x0000000077cfbdb0
 DATA ACCESS BIT          77b8e150      1213082a6018  IFA=         77c16ab8 0x0000000077b8e150
 VHPT FAULT          77ed5d60      1013082a6018  IFA=      6fbfffa6048 0x0000000077ed5d60
   DATA ACCESS BIT          77ed5d60      1213082a6018  IFA=         77c229c0 0x0000000077ed5d60
 DATA ACCESS BIT          77b8e1b0      1013082a6018  IFA=         77c1c320 0x0000000077b8e1b0
      USER SYSCALL          77cafa40        10082a6018  Num=               42 0x0000000077cafa40
 VHPT FAULT  e00000008344dc20      1010092a6018  IFA= e000010600703784 nt!ExpLookupHandleTableEntry+0x20
...
```

 

 





