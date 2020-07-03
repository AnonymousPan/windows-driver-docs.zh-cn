---
title: NDIS_STATUS_WWAN_NITZ_INFO
description: 微型端口驱动程序使用 NDIS_STATUS_WWAN_NITZ_INFO 通知来通知移动宽带（MB）服务完成了上一个 OID_WWAN_NITZ 查询请求。
ms.assetid: 8AC20FB1-FD2E-46B4-97F7-56EC7AA79740
ms.date: 04/11/2019
keywords: -从 Windows Vista 开始 NDIS_STATUS_WWAN_NITZ_INFO 的网络驱动程序
ms.localizationpriority: medium
ms.custom: 19H1
ms.openlocfilehash: 28087695fc38d499c3c68468ba726186baf8fb34
ms.sourcegitcommit: 82a9be3b3584f991e5121f8f46a972e04185fa52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85916645"
---
# <a name="ndis_status_wwan_nitz_info"></a>NDIS_STATUS_WWAN_NITZ_INFO

微型端口驱动程序使用**NDIS_STATUS_WWAN_NITZ_INFO**通知来通知移动宽带（MB）服务完成了上一个[OID_WWAN_NITZ](oid-wwan-nitz.md)查询请求。

微型端口驱动程序以未经请求的事件的形式发送此通知，以提供当前网络时间和时区的 intformation。

此通知使用[**NDIS_WWAN_NITZ_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_nitz_info)结构。

## <a name="requirements"></a>要求

**版本**： Windows 10，版本 1903**头**： Ntddndis （包括 Ndis .h）

## <a name="see-also"></a>另请参阅

[使用 DSS 进行 MB 调制解调器日志记录](mb-modem-logging-with-dss.md)

[OID_WWAN_NITZ](oid-wwan-nitz.md)

[**NDIS_WWAN_NITZ_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_nitz_info) 
