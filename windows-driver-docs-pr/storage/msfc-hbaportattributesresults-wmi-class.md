---
title: MSFC \_ HBAPORTATTRIBUTESRESULTS WMI 类
description: MSFC \_ HBAPORTATTRIBUTESRESULTS WMI 类
ms.assetid: f268a653-e3ee-47d0-9af8-925dc0545a2b
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 1b41116cf364709d542e1e71a99b41c5261c4118
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89186691"
---
# <a name="msfc_hbaportattributesresults-wmi-class"></a>MSFC \_ HBAPORTATTRIBUTESRESULTS WMI 类


## <span id="ddk_msfc_hbaportattributesresults_wmi_class_kr"></span><span id="DDK_MSFC_HBAPORTATTRIBUTESRESULTS_WMI_CLASS_KR"></span>


WMI 客户端使用 MSFC \_ HBAPORTATTRIBUTESRESULTS WMI 类查询 hba 上端口的属性的 hba 微型端口驱动程序。

MSFC \_ HBAPortAttributesResults 类在 *Hbaapi*中定义如下：

```cpp
class MSFC_HBAPortAttributesResults {
    [HBAType("HBA_WWN"), WmiDataId(1) ] uint8  NodeWWN[8];
    [HBAType("HBA_WWN"), WmiDataId(2) ] uint8  PortWWN[8];
    [ WmiDataId(3) ] uint32 PortFcId;
    [HBAType("HBA_PORTTYPE"), Values{"Unknown", "Other",
      "Not present", "Fabric", "Public Loop",
      "HBA_PORTTYPE_FLPORT", "Fabric Port",
      "Fabric expansion port", "Generic Fabric Port",
      "Private Loop", "Point to Point"} : amended,
      ValueMap{"1", "2", "3", "5", "6", "7", "8", "9",
      "10", "20", "21"},
      WmiDataId(4) ] uint32  PortType;
    [HBAType("HBA_PORTSTATE"), Values{"Unknown", "Operational",
      "User Offline", 
      "Bypassed", "In diagnostics mode", "Link Down", 
      "Port Error", "Loopback"} : amended,
      ValueMap{"1","2","3","4","5","6","7","8"},
      WmiDataId(5) ] uint32  PortState;
    [HBAType("HBA_COS"), WmiDataId(6) ] 
      uint32 PortSupportedClassofService;
   [HBAType("HBA_FC4TYPES"), WmiDataId(7)] 
      uint8 PortSupportedFc4Types[32];
    [HBAType("HBA_FC4TYPES"), WmiDataId(8)]
      uint8 PortActiveFc4Types[32];
    [HBAType("HBA_PORTSPEED"),
      Values{"1 GBit/sec", "2 GBit/sec", "10 GBit/sec", 
      "4 GBit/sec"} : amended,
      ValueMap{"1", "2", "4", "8"},
      WmiDataId(9)] uint32  PortSupportedSpeed;
    [HBAType("HBA_PORTSPEED"),
      Values{"1 GBit/sec", "2 GBit/sec", 
      "10 GBit/sec", "4 GBit/sec"} : amended,
      ValueMap{"1", "2", "4", "8"},
      WmiDataId(10) ] uint32  PortSpeed;
    [WmiDataId(11) ] uint32  PortMaxFrameSize;
    [HBAType("HBA_WWN"), WmiDataId(12) ] uint8  FabricName[8];
    [ WmiDataId(13) ] uint32  NumberofDiscoveredPorts;
};
```

编译此类定义时，将生成以下数据结构：

[**MSFC \_ HBAPortAttributesResults**](/windows-hardware/drivers/ddi/hbapiwmi/ns-hbapiwmi-_msfc_hbaportattributesresults)

没有与此 WMI 类相关联的方法。

 

