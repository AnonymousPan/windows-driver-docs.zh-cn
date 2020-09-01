---
title: 具有离散值的数据范围
description: 具有离散值的数据范围
ms.assetid: 330edd60-0469-4351-bfb1-29b29e133c1a
keywords:
- 数据交集处理程序 WDK 音频，离散值数据范围
- 离散值数据范围 WDK 音频
- 数据范围 WDK 音频，离散值
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 78559ed27b1a1cff7c8d8608fa1479531d0e8e3a
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89208155"
---
# <a name="data-ranges-with-discrete-values"></a>具有离散值的数据范围


## <span id="data_ranges_with_discrete_values"></span><span id="DATA_RANGES_WITH_DISCRETE_VALUES"></span>


例如，如果音频设备支持11、22和 44 kHz 的采样频率，则可以将所有三个频率指定为单个 [**KSDATARANGE \_ 音频**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksdatarange_audio) 结构中的11到 44 kHz 范围。 此方法的优点是非常简单。 一个可能的缺点是，有错误的数据交集处理程序可能会选择无效的参数值 (例如，27 kHz) 在范围内。 在这种情况下，适配器驱动程序没有选项，但若要使 **newstream.ischecked** 调用失败 (例如，请参阅 [**IMiniportWavePci：： newstream.ischecked**](/windows-hardware/drivers/ddi/portcls/nf-portcls-iminiportwavepci-newstream)) 尝试创建格式无效的 pin。

另一种方法是提供数据范围列表，其中每个数据区域指定一个离散值，而不是每个参数的值范围。 例如，对于11、22和 44 kHz，数据范围数组可以包含三个单独的元素，而不是提供单个数据范围以指定从11到 44 kHz 的样本频率范围。 在上述每个元素中，最大和最小采样频率设置为相同的值 (11、22或 44 kHz) 。 此方法的优点是消除了有关支持的准确值的任何多义性。 此外，如果另一个离散值优先于另一值，则包含此值的数据范围可以移动到数组中位于包含其他值的数据范围之前的位置。 离散值的一个小缺点是它们可以增加数据范围数组的大小。

 

