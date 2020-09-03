---
title: MobileBroadbandInfo
description: MobileBroadbandInfo
ms.assetid: 02279e23-becd-49ef-8981-6afb8e5aab91
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0dc46291ca5572d3300887d1b87af8b4914ac1c4
ms.sourcegitcommit: 7ca2d3e360a4ae1d4d3c3092bd34492a2645ef74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89403512"
---
# <a name="mobilebroadbandinfo"></a>MobileBroadbandInfo

[!include[MBAE deprecation warning](../includes/mbae-deprecation-warning.md)]

MobileBroadbandInfo 元素是 [MOBILEBROADBANDINFO XML 架构](mobilebroadbandinfo-xml-schema.md)的父元素。

## <a name="span-idusagespanspan-idusagespanspan-idusagespanusage"></a><span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>使用情况


``` syntax
<MobileBroadbandInfo>
  child elements
</MobileBroadbandInfo>
```

## <a name="span-idattributesspanspan-idattributesspanspan-idattributesspanattributes"></a><span id="Attributes"></span><span id="attributes"></span><span id="ATTRIBUTES"></span>属性


没有特性。

## <a name="span-idchild_elementsspanspan-idchild_elementsspanspan-idchild_elementsspanchild-elements"></a><span id="Child_elements"></span><span id="child_elements"></span><span id="CHILD_ELEMENTS"></span>子元素


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="networkconfiguration.md" data-raw-source="[NetworkConfiguration](networkconfiguration.md)">NetworkConfiguration</a></p></td>
<td><p><a href="networkconfiguration.md" data-raw-source="[NetworkConfiguration](networkconfiguration.md)">NetworkConfiguration</a>元素指定要使用的购买和 Internet 移动宽带配置文件。</p></td>
</tr>
<tr class="even">
<td><p><a href="provisioningengine.md" data-raw-source="[ProvisioningEngine](provisioningengine.md)">ProvisioningEngine</a></p></td>
<td><p><a href="provisioningengine.md" data-raw-source="[ProvisioningEngine](provisioningengine.md)">ProvisioningEngine</a>元素为使用者名称和颁发者名称指定受信任的证书值。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idparent_elementsspanspan-idparent_elementsspanspan-idparent_elementsspanparent-elements"></a><span id="Parent_elements"></span><span id="parent_elements"></span><span id="PARENT_ELEMENTS"></span>父元素


没有父元素。

## <a name="span-idxsdspanspan-idxsdspanxsd"></a><span id="XSD"></span><span id="xsd"></span>XSD.EXE


``` syntax
<xs:element name="MobileBroadbandInfo" type="tns:MobileBroadbandInfoType" />

<xs:complexType name="MobileBroadbandInfoType">
  <xs:sequence>
    <xs:element name="NetworkConfiguration" type="tns:NetworkConfigType" minOccurs="0" />
    <xs:element name="ProvisioningEngine" type="tns:ProvisioningEngineType" minOccurs="0" />
    <xs:any namespace="##other" processContents="lax" minOccurs="0" maxOccurs="unbounded" />
  </xs:sequence>
</xs:complexType>
```

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


MobileBroadbandInfo 元素是必需的。

 

 





