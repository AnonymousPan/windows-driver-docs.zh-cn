---
title: OID_WDI_SET_PRIVACY_EXEMPTION_LIST
description: 主机使用 OID_WDI_SET_PRIVACY_EXEMPTION_LIST 来提供数据包说明的免除列表。 适配器将这些例外应用于与为豁免指定的 IEEE EtherType 值匹配的接收的数据包。
ms.assetid: 409ac8c5-0bf7-4ae9-b709-5c2cfa1f8b7f
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 OID_WDI_SET_PRIVACY_EXEMPTION_LIST 网络驱动程序
ms.localizationpriority: medium
ms.custom: 19H1
ms.openlocfilehash: 017304c10dfc6e60f9a8927f1c033f61c21b516e
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89213245"
---
# <a name="oid_wdi_set_privacy_exemption_list"></a>OID \_ WDI \_ SET \_ 隐私 \_ \_ 列表


OID \_ WDI \_ SET \_ 隐私 \_ \_ 列表由主机用于提供数据包说明的免除列表。 适配器将这些例外应用于与为豁免指定的 IEEE EtherType 值匹配的接收的数据包。

| 作用域 | 设置序列化任务 | 正常执行时间 (秒)  |
|-------|--------------------------|---------------------------------|
| 端口  | 是                      | 1                               |

 

## <a name="set-property-parameters"></a>设置属性参数


| TLV                                                                                 | 允许多个 TLV 实例 | 可选 | 说明                        |
|-------------------------------------------------------------------------------------|--------------------------------|----------|------------------------------------|
| [**WDI \_ TLV \_ 隐私 \_ 豁免 \_ 条目**](./wdi-tlv-privacy-exemption-entry.md) | X                              | X        | 隐私例外条目列表。 |

 

## <a name="set-property-results"></a>设置属性结果


无其他数据。 标头中的数据足够了。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低受支持的客户端</p></td>
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>标头</p></td>
<td>Dot11wdi</td>
</tr>
</tbody>
</table>

 

