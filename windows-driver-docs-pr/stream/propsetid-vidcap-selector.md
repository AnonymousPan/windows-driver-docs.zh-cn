---
title: PROPSETID \_ VIDCAP \_ 选择器
description: PROPSETID \_ VIDCAP \_ 选择器
ms.assetid: a7328f22-be49-48ac-b923-15f66dc38ccb
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: cd007d0cadc25b3b1207dcac22fff4ffadf840ff
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89187351"
---
# <a name="propsetid_vidcap_selector"></a>PROPSETID \_ VIDCAP \_ 选择器


## <span id="ddk_propsetid_vidcap_selector_ks"></span><span id="DDK_PROPSETID_VIDCAP_SELECTOR_KS"></span>


PROPSETID \_ VIDCAP \_ 选择器属性集是与 [USB 视频类驱动程序](./usb-video-class-driver.md)一起使用的新集。 此属性集包含实现 **ISelector** 接口所需的属性 (参阅 Microsoft Windows SDK) 中的 DirectShow 文档。

\_Ksmedia 中的 KSPROPERTY VIDCAP \_ 选择*ksmedia.h*器枚举指定此集的属性。

此属性集控制当前提供镜头输入的节点。 对此属性集的支持是可选的，只应由提供这些控件的设备来实现。

USB 视频类驱动程序的客户端可以发出以下筛选器或节点请求：

[**KSPROPERTY \_ 选择器 \_ 源 \_ 节点 \_ ID**](ksproperty-selector-source-node-id.md)

[**KSPROPERTY \_ NUM \_ 源**](ksproperty-num-sources.md)

### <a name="span-iddirectshow_interfacesspanspan-iddirectshow_interfacesspandirectshow-interfaces"></a><span id="directshow_interfaces"></span><span id="DIRECTSHOW_INTERFACES"></span>DirectShow 接口

PROPSETID \_ VIDCAP \_ 选择器属性集中的属性可通过 DirectShow **ISelector** 接口进行访问 (参阅 Microsoft Windows SDK) 中的 DirectShow 文档。

 

