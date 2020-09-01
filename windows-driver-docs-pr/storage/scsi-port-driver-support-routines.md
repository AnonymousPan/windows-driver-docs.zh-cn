---
title: SCSI 端口驱动程序支持例程
description: 介绍 SCSI 端口驱动程序例程。
ms.assetid: b4bd6afe-77a2-4bd1-a762-5887f77cc737
keywords:
- SCSI 端口驱动程序支持例程
- 存储 WDK
- 存储支持例程
ms.date: 10/08/2019
ms.localizationpriority: medium
ms.openlocfilehash: ede9ab9fbaa308ef00dfd6ab181927ea6491cf18
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89186688"
---
# <a name="scsi-port-driver-support-routines"></a>SCSI 端口驱动程序支持例程

特定于操作系统的 SCSI 端口驱动程序提供 *ScsiPortXxx* 例程，以支持与 Microsoft 提供的、特定于操作系统的 scsi 端口驱动程序关联的独立于操作系统的 scsi 微型端口驱动程序。 SCSI 端口驱动程序是一个内核模式的动态链接库。

可在以下位置找到 *ScsiPortXxx* 例程的列表和引用页：

| 例程 | 标头 |
| ------- | ------- |
| *ScsiPortXxx* | [srb 标头](/windows-hardware/drivers/ddi/srb/) |
| *ScsiPortWmiXxx* | [scsiwmi](/windows-hardware/drivers/ddi/scsiwmi/) |

有关 SCSI 微型端口驱动程序例程的列表，请参阅 [Scsi 微型端口驱动程序例程](scsi-miniport-driver-routines.md)。