---
title: NDIS_STATUS_WWAN_UICC_RESET_INFO
description: NDIS_STATUS_WWAN_UICC_RESET_INFO
ms.assetid: ADA3ADC9-82AD-423A-ABA4-902EAF5F5C74
keywords:
- NDIS_STATUS_WWAN_UICC_RESET_INFO，UICC 重置状态通知，移动宽带 UICC 重置状态通知，MB UICC 重置状态通知
ms.date: 08/18/2017
ms.localizationpriority: medium
ms.openlocfilehash: 4ec741909e4ade2b13b909a72dc331489e1736d3
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89212351"
---
# <a name="ndis_status_wwan_uicc_reset_info"></a>NDIS_STATUS_WWAN_UICC_RESET_INFO

NDIS_STATUS_WWAN_UICC_RESET_INFO 状态通知通过调制解调器微型适配器发送，将当前直通状态的 MB 主机通知给 UICC 智能卡。 此通知是在 folloiwng 两个方案中发送的：

1. [OID_WWAN_UICC_RESET](oid-wwan-uicc-reset.md)查询请求之后。
2. 在 OID_WWAN_UICC_RESET 集请求后完成 UICC reset 后，通知 UICC 卡的传递状态的 MB 主机之后重置。

此通知使用 [NDIS_WWAN_UICC_RESET_INFO](/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_reset_info) 结构。

## <a name="requirements"></a>要求

**版本**： Windows 10，版本 1709 **头**： Ndis。h

## <a name="see-also"></a>另请参阅

[OID_WWAN_UICC_RESET](oid-wwan-uicc-reset.md)

[NDIS_WWAN_UICC_RESET_INFO](/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_reset_info)

[MB 低级别 UICC 访问](mb-low-level-uicc-access.md)