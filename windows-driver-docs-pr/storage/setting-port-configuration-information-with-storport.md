---
title: 使用 Storport 设置端口配置信息
description: 使用 Storport 设置端口配置信息
ms.assetid: dcc2cb3c-2fe6-4f70-814b-66b59a237dd9
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 715fa20e3399560f23772508233368701f4641cd
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89183835"
---
# <a name="setting-port-configuration-information-with-storport"></a>使用 Storport 设置端口配置信息


## <span id="ddk_setting_port_configuration_information_with_storport_kg"></span><span id="DDK_SETTING_PORT_CONFIGURATION_INFORMATION_WITH_STORPORT_KG"></span>


当 Microsoft Windows PnP 管理器发现由 Storport 管理的适配器时，它会通知 Storport 驱动程序启动它。 接下来，Storport 调用微型端口驱动程序的 [**HwStorFindAdapter**](/windows-hardware/drivers/ddi/storport/nc-storport-hw_find_adapter) 例程，并 [**传入 \_ \_ (Storport) 结构的端口配置信息 **](/previous-versions/windows/hardware/drivers/ff563901(v=vs.85)) 。

由于 Storport 管理的所有适配器都是 PnP 设备，因此 *HwStorFindAdapter* 不会以物理方式搜索适配器。 相反，此微型端口驱动程序例程尝试使用端口配置信息结构中指定的参数初始化适配器 \_ \_ ，并完成端口配置信息的初始化 \_ ，并将 \_ 这些值存储在 \_ 设置 \_ 了 Storport 可能需要的端口配置信息中以初始化设备扩展。

有关详细信息，请参阅 [**端口 \_ 配置 \_ 信息 (SCSI) **](/windows-hardware/drivers/ddi/srb/ns-srb-_port_configuration_information) 和 [**端口 \_ 配置 \_ 信息 (STORPORT) **](/previous-versions/windows/hardware/drivers/ff563901(v=vs.85))。

 

