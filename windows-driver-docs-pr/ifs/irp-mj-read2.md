---
title: 检查 IRP_MJ_READ 操作的 Oplock 状态
description: 检查 IRP_MJ_READ 操作的 Oplock 状态
ms.assetid: 9b4d1ba9-0838-44f1-8328-f60bfb3910ee
ms.date: 11/25/2019
ms.localizationpriority: medium
ms.openlocfilehash: 9c68c370df0ae075d991847d0cdd86dfee5a293f
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89065008"
---
# <a name="checking-the-oplock-state-of-an-irp_mj_read-operation"></a>检查 IRP_MJ_READ 操作的 Oplock 状态

读取*流*时，将应用以下[oplock 中断](./breaking-oplocks.md)条件。 如果 TxF 事务处理读取器执行读取，则不会执行此检查，因为事务读取器会排除编写器 (也就是说，持有 oplock 的编写器不能出现在所有) 上。

### <a name="conditions-for-level-2-filter-read-and-read-handle-request-types"></a>级别2、筛选、读取和读取句柄请求类型的条件

- Oplock 不会中断。

- 不需要确认，操作会立即继续。

### <a name="conditions-for-level-1-batch-read-write-and-read-write-handle-request-types"></a>级别1、批处理、读写和读写句柄请求类型的条件

- 当读取操作发生在带有 oplock 键的 FILE_OBJECT 上时 IRP_MJ_READ 中断，该操作与拥有 oplock 的 FILE_OBJECT 的键不同。 如果 oplock 中断：

  - 级别1和批处理请求中断到级别2。

  - 读写请求中断。

  - 读写-处理请求中断到读取句柄。

- 必须先收到确认，然后才能继续操作。