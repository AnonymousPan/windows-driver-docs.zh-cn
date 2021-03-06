---
title: OID_WDI_SET_REMOVE_PM_PROTOCOL_OFFLOAD
description: OID_WDI_SET_REMOVE_PM_PROTOCOL_OFFLOAD 删除协议卸载 ID 指定的协议卸载。
ms.assetid: 47850c43-4d10-48f5-b2e9-1f94f23eabf2
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 OID_WDI_SET_REMOVE_PM_PROTOCOL_OFFLOAD 网络驱动程序
ms.localizationpriority: medium
ms.custom: 19H1
ms.openlocfilehash: d58bad8ff21e67505cb04f5e27c78706f80fbec1
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89212805"
---
# <a name="oid_wdi_set_remove_pm_protocol_offload"></a>OID \_ WDI \_ SET \_ 删除 \_ PM \_ 协议 \_ 卸载


OID \_ WDI \_ 集 \_ 删除 \_ PM \_ 协议 \_ 卸载会删除由协议卸载 ID 指定的协议卸载。

| 作用域 | 设置序列化任务 | 正常执行时间 (秒)  |
|-------|--------------------------|---------------------------------|
| 端口  | 是                      | 1                               |

 

## <a name="set-property-parameters"></a>设置属性参数


| TLV                                                                                        | 允许多个 TLV 实例 | 可选 | 说明          |
|--------------------------------------------------------------------------------------------|--------------------------------|----------|----------------------|
| [**WDI \_ TLV \_ PM \_ 协议 \_ 卸载 \_ 删除**](./wdi-tlv-pm-protocol-offload-remove.md) |                                |          | 协议卸载 ID。 |

 

## <a name="set-property-results"></a>设置属性结果


无其他参数。 标头中的数据足够了。

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

## <a name="see-also"></a>另请参阅


[OID \_ WDI \_ 获取 \_ PM \_ 协议 \_ 卸载](oid-wdi-get-pm-protocol-offload.md)

[OID \_ WDI \_ 设置 \_ 添加 \_ PM \_ 协议 \_ 卸载](oid-wdi-set-add-pm-protocol-offload.md)

 

