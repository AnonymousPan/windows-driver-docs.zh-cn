---
title: GUID_NDIS_STATUS_OFFLOAD_HW_CAPABILITIES
description: 本主题描述了 NDIS WMI 接口的 GUID_NDIS_STATUS_OFFLOAD_HW_CAPABILITIES GUID。
ms.assetid: 6f5e11c1-4fa0-4a9b-90f3-85a3cb8b8878
keywords:
- GUID_NDIS_STATUS_OFFLOAD_HW_CAPABILITIES，WDK GUID_NDIS_STATUS_OFFLOAD_HW_CAPABILITIES 网络驱动程序
ms.date: 11/22/2017
ms.localizationpriority: medium
ms.openlocfilehash: 42abf49aa2d3c38270d2cc1aea4af5ce596f3b7d
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89218095"
---
# <a name="guid_ndis_status_offload_hw_capabilities"></a>GUID_NDIS_STATUS_OFFLOAD_HW_CAPABILITIES

GUID_NDIS_STATUS_OFFLOAD_HW_CAPABILITIES 事件 GUID 表示与 NDIS 端口或微型端口适配器关联的硬件的卸载特性发生了变化。 硬件更改通常会反映添加或删除与 MUX 中间驱动程序关联的硬件。 在 NDIS 6.0 和更高版本中支持此 WMI GUID。

MUX 中间驱动程序使用 [NDIS_STATUS_TASK_OFFLOAD_HARDWARE_CAPABILITIES](ndis-status-task-offload-hardware-capabilities.md) 状态指示通知 NDIS 和过量驱动程序已更改任务卸载功能。

当驱动程序指示任务卸载硬件更改时，NDIS 会将状态指示转换为 WMI 客户端的 WMI GUID_NDIS_STATUS_OFFLOAD_HW_CAPABILITIES 事件。

具有 GUID 的 NDIS 提供的数据缓冲区包含后跟[NDIS_OFFLOAD](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload)结构的[NDIS_WMI_EVENT_HEADER](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_wmi_event_header)结构。

有关任务卸载功能的详细信息，请参阅 [NDIS_STATUS_TASK_OFFLOAD_HARDWARE_CAPABILITIES](ndis-status-task-offload-hardware-capabilities.md) 和 [OID_TCP_OFFLOAD_HARDWARE_CAPABILITIES](oid-tcp-offload-hardware-capabilities.md)。