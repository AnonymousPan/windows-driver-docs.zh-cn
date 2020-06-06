---
title: 用户界面插件简介
description: 用户界面插件简介
ms.assetid: 7f01bd14-bcc5-4c26-a9b8-a12aa1ffe242
keywords:
- 用户界面插件 WDK 打印，关于用户界面插件
- UI 插件 WDK 打印，关于用户界面插件
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 9a959ff4ff3164d97a68fd2951954c36f3f5785c
ms.sourcegitcommit: 581fb777a2376854ca12e767d366e2cb79724b73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84461838"
---
# <a name="introduction-to-user-interface-plug-ins"></a>用户界面插件简介

当你向[Microsoft 通用打印机驱动程序](microsoft-universal-printer-driver.md)（Unidrv）或[microsoft PostScript 打印机驱动程序](microsoft-postscript-printer-driver.md)（Pscript）添加对新打印机设备的支持时，你可以通过修改打印机属性表或打印机的文档属性表来自定义驱动程序的用户界面。

可以通过提供用户模式 DLL 完成此自定义。 此 DLL 称为*用户界面插件*或仅限*UI 插件*。

UI 插件可以通过在属性表的 "**设备设置**" 页中添加、删除或替换选项来修改打印机属性表。 它还可以添加新页。 同样，插件可以通过在属性表的**布局**、**纸张/质量**和**高级**页中添加、删除或替换选项来修改文档属性表，也可以添加新页。

如果使用的是 Windows Vista 中的 Unidrv，则可以在插件中实现[**IPrintOemUI2：： HideStandardUI**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemui2-hidestandardui)方法，以隐藏标准驱动程序提供的所有打印机配置属性页。 如果要为打印机提供完全自定义的打印机配置用户界面，则可以使用此方法。

> [!IMPORTANT]
> Windows 帮助（Winhlp32.exe）是一种允许用户查看 .hlp 文件的应用程序。 从 Windows Vista 开始，windows 帮助应用程序不作为 Windows 操作系统的一部分包含在内。 开发依赖于 .hlp 文件的应用程序的软件开发人员应将其文件转换为其他帮助格式，如 .chm、. hxs、.html 或 .xml 文件。 有关详细信息，请参阅 windows 知识库文章中[不再包含 Windows 帮助程序（winhlp32.exe）](https://go.microsoft.com/fwlink/p/?linkid=80917) 。

[打印机接口 DLL](printer-interface-dll.md)使用一组 COM 接口调用 Unidrv 或 PSCRIPT 的 UI 插件。 打印机接口 Dll 是使用 CPSUI 实现的，UI 插件通过驱动程序的打印机接口 DLL 与 CPSUI 间接交互。 因此，在开发 UI 插件之前，应阅读[CPSUI](common-property-sheet-user-interface.md)部分。

除了修改打印机驱动程序的用户界面，UI 插件还可以执行其他操作，如处理某些打印机事件和报告支持的功能。 有关详细信息，请参阅[自定义其他打印机接口操作](customizing-other-printer-interface-operations.md)。
