---
title: WDF 验证
description: 驱动程序验证程序的 WDF 验证
ms.assetid: 9ee72369-878f-4710-a38b-1c93042178bd
keywords:
- 驱动程序验证程序的 WDF 验证
ms.date: 09/14/2018
ms.localizationpriority: medium
ms.openlocfilehash: d3b488b78a019a0d74c30d2e4f311ece9d33fb5b
ms.sourcegitcommit: faff37814159ad224080205ad314cabf412e269f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89384863"
---
# <a name="wdf-verification"></a>WDF 验证

WDF 验证检查内核模式驱动程序是否遵循 [内核模式驱动程序框架 (KMDF) 的要求](../wdf/using-the-framework-to-develop-a-driver.md) 。  

如果未通过此验证检查，将导致 [错误检查0x10D： WDF_VIOLATION](../debugger/bug-check-0x10d---wdf-violation.md)。 


### <a name="activating-this-option"></a>激活此选项：

可以通过使用驱动程序验证器管理器或 Verifier.exe 命令行来为一个或多个驱动程序激活端口/微型端口接口检查。 有关详细信息，请参阅 [选择驱动程序验证程序选项](./selecting-driver-verifier-options.md)。 您必须重新启动计算机以激活或停用端口/微型端口接口检查选项。

* **在命令行中**

    在命令行中，端口微型端口接口检查由 **0x00100000**表示。 例如：
    
    `verifier /flags 0x00100000 /driver MyDriver.sys`

    此功能将在下一次启动后处于活动状态。

* **使用驱动程序验证器管理器**

1. 启动驱动程序验证器管理器。 在命令提示符窗口中键入 Verifier。
2. 选择 "为代码开发人员 (创建自定义设置") ，然后单击 "下一步"。
3. 选择 (检查) 端口微型端口接口检查。
4. 重新启动计算机。