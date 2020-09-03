---
title: NFC 设计指南
description: Windows 公开了使用 NFC 技术（包括以下平台）的一组丰富体验
ms.assetid: 26BFE25A-AC46-4634-8330-990DB447E55A
keywords:
- NFC
- 近场通信
- 近程
- 近场邻近感应
- NFP
ms.date: 04/20/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
author: EliotSeattle
ms.openlocfilehash: 4cba01d979708b19e078f002489670d6c0e533ce
ms.sourcegitcommit: faff37814159ad224080205ad314cabf412e269f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89382553"
---
# <a name="near-field-communications-nfc-design-guide"></a>近场通信 (NFC) 设计指南

Windows 公开了使用 NFC 技术（包括以下平台）的一组丰富体验：

- 邻近感应平台 – 提供了一个平台以便通过 NFC 在设备之间发起内容点对点共享，侧重于 Windows 设备以及其他符合 NFC 标准的移动设备，以及从符合 NFC 论坛规范的标记读取内容/或者向其中写入内容。

- 电子钱包平台 – 提供了安全的存储和交易功能来为设备上付款方案、实体付款以及其他 NFC 交易提供支持。

为了支持 NFC，Microsoft 依赖于 IHV 来提供实现这些主题中定义的设备驱动程序接口 (DDI) 的设备驱动程序。

请使用用户模式驱动程序框架 (UMDF) 2.0 来为 Windows 10 桌面版（家庭版、专业版、企业版和教育版）和 Windows 10 移动版编写 NFC 驱动程序。

## <a name="related-topics"></a>相关主题

[UMDF 入门](../wdf/getting-started-with-umdf-version-2.md)  

[NFC 设备驱动程序接口 (DDI) 参考](/windows-hardware/drivers/ddi/index)