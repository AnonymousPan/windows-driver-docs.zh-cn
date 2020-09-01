---
title: KS 方法
description: KS 方法
ms.assetid: 1d7bd6f4-0aaf-4d77-8132-f551fd2ecbd2
keywords:
- 内核流 WDK，方法
- KS WDK，方法
- 方法 WDK 内核流式处理
- 方法设置 WDK 内核流式处理
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: b431ea48f5fa08e513580a539687136298e58c65
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89188181"
---
# <a name="ks-methods"></a>KS 方法





方法集是内核流式处理客户端可以对 KS 对象调用的一组相关的操作。 例如，分配器对象可能会提供一个方法集，其中包含分配和释放内存的方法。

微型驱动程序为其支持的每个方法集提供 [**KSMETHOD \_ 集**](/windows-hardware/drivers/ddi/ks/ns-ks-ksmethod_set) 结构。 反过来，KSMETHOD \_ 集结构包含描述单个方法的 [**KSMETHOD \_ 项**](/windows-hardware/drivers/ddi/ks/ns-ks-ksmethod_item) 结构的数组。 微型驱动程序提供指向驱动程序提供的 [*KStrMethodHandler*](/windows-hardware/drivers/ddi/ks/nc-ks-pfnkshandler) 和 [*KStrSupportHandler*](/previous-versions/ff567206(v=vs.85)) 处理例程的指针，该指针位于 SupportHandler 项结构的 **MethodHandler** 和 **KSMETHOD** 成员中 \_ 。

客户端通过调用[**KsSynchronousDeviceControl**](/windows-hardware/drivers/ddi/ksproxy/nf-ksproxy-kssynchronousdevicecontrol)或异步请求来发出同步方法请求，方法是调用 Microsoft Windows SDK 文档) with [**IOCTL \_ KS \_ 方法**](/windows-hardware/drivers/ddi/ks/ni-ks-ioctl_ks_method)中所述的**DeviceIoControl** (。

驱动程序通过在上述调用的*InBuffer*参数中提供[**KSMETHOD**](/previous-versions/ff563398(v=vs.85))结构来请求特定方法。

AVStream 筛选器和 pin 通过在[**KSFILTER \_ 描述符**](/windows-hardware/drivers/ddi/ks/ns-ks-_ksfilter_descriptor)结构或[**KSPIN \_ 描述符 \_ EX**](/windows-hardware/drivers/ddi/ks/ns-ks-_kspin_descriptor_ex)结构的**AutomationTable**成员中提供[**KSAUTOMATION \_ 表**](/windows-hardware/drivers/ddi/ks/ns-ks-ksautomation_table_)结构来说明它们支持的方法。 有关详细信息，请参阅 [定义自动化表](defining-automation-tables.md)。

 

