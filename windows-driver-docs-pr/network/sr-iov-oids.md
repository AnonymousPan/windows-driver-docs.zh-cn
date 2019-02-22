---
title: SR-IOV 的 Oid
description: 本部分介绍单根 I/O 虚拟化 (SR-IOV) Oid 和它们的特征。
keywords:
- SR-IOV 的 Oid
- 单根 I/O 虚拟化 Oid
- WDK 的 SR-IOV Oid
- SR-IOV 对象标识符
ms.assetid: E93751BF-17BC-4BE7-89F7-53F6C9941120
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 41c197ce76720fb8e67a24355fd260af47f4585b
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56522953"
---
# <a name="sr-iov-oids"></a>SR-IOV 的 Oid

单根 I/O 虚拟化 (SR-IOV) 对象标识符 (Oid) 适用于微型端口和基础驱动程序支持 SR-IOV 的接口。 在 NDIS 版本 6.30 和更高版本中支持此接口。 

下表定义的 SR-IOV Oid 的特征。 下面的缩写形式用于在表中指定的 Oid 的特征。

- Q  
仅在查询请求中使用 OID。
- S  
仅在设置请求中使用 OID。
- M  
仅在方法请求中使用 OID。 无法对集或查询操作发出这些请求。
- N  
OID 请求直接由 NDIS 而不是由微型端口驱动程序处理。 该驱动程序将不会颁发这些 Oid。
- P  
仅对网络适配器的物理函数 (PF) 的微型端口驱动程序发出 OID 请求。  
PF 驱动程序必须支持这些 Oid。 该驱动程序还必须列出在这些 Oid **SupportedOidList**的成员[NDIS_MINIPORT_ADAPTER_GENERAL_ATTRIBUTES](https://msdn.microsoft.com/library/windows/hardware/ff565923)驱动程序中传递的结构*MiniportAttributes*到调用的参数[NdisMSetMiniportAttributes](https://msdn.microsoft.com/library/windows/hardware/ff563672)。
- V  
仅对网络的虚拟函数 (VFs) 之一的微型端口驱动程序发出 OID 请求。  
VF 驱动程序必须支持这些 Oid。 该驱动程序还必须列出在这些 Oid **SupportedOidList**的成员[NDIS_MINIPORT_ADAPTER_GENERAL_ATTRIBUTES](https://msdn.microsoft.com/library/windows/hardware/ff565923)驱动程序中传递的结构*MiniportAttributes*到调用的参数[NdisMSetMiniportAttributes](https://msdn.microsoft.com/library/windows/hardware/ff563672)。

| 名称                                                                                                 | Q | S | M | N | P | V |
|---                                                                                                   |---|---|---|---|---|---|
| [OID_NIC_SWITCH_ALLOCATE_VF](https://msdn.microsoft.com/library/windows/hardware/hh451814)           |   |   | X |   | X |   | 
| [OID_NIC_SWITCH_CREATE_SWITCH](https://msdn.microsoft.com/library/windows/hardware/hh451815)         |   |   | X |   | X |   | 
| [OID_NIC_SWITCH_CREATE_VPORT](https://msdn.microsoft.com/library/windows/hardware/hh451816)          |   |   | X |   | X |   |
| [OID_NIC_SWITCH_CURRENT_CAPABILITIES](https://msdn.microsoft.com/library/windows/hardware/ff569760)  | X |   |   | X |   |   |  
| [OID_NIC_SWITCH_DELETE_SWITCH](https://msdn.microsoft.com/library/windows/hardware/hh451817)         |   | X |   |   | X |   |  
| [OID_NIC_SWITCH_DELETE_VPORT](https://msdn.microsoft.com/library/windows/hardware/hh451818)          |   | X |   |   | X |   | 
| [OID_NIC_SWITCH_ENUM_SWITCHES](https://msdn.microsoft.com/library/windows/hardware/hh451819)         | X |   |   | X |   |   |   
| [OID_NIC_SWITCH_ENUM_VFS](https://msdn.microsoft.com/library/windows/hardware/hh451820)              | X |   |   | X |   |   |   
| [OID_NIC_SWITCH_ENUM_VPORTS](https://msdn.microsoft.com/library/windows/hardware/hh451821)           | X |   |   | X |   |   |  
| [OID_NIC_SWITCH_FREE_VF](https://msdn.microsoft.com/library/windows/hardware/hh451822)               |   | X |   |   | X |   | 
| [OID_NIC_SWITCH_HARDWARE_CAPABILITIES](https://msdn.microsoft.com/library/windows/hardware/ff569761) | X |   |   | X |   |   |   
| [OID_NIC_SWITCH_PARAMETERS](https://msdn.microsoft.com/library/windows/hardware/hh451823)            |   |   | X |   | X |   | 
| [OID_NIC_SWITCH_VF_PARAMETERS](https://msdn.microsoft.com/library/windows/hardware/hh451824)         |   |   | X |   | X |   | 
| [OID_NIC_SWITCH_VPORT_PARAMETERS](https://msdn.microsoft.com/library/windows/hardware/hh451825)      |   |   | X |   | X |   | 
| [OID_SRIOV_BAR_RESOURCES](https://msdn.microsoft.com/library/windows/hardware/hh451852)              |   | X |   |   | X |   | 
| [OID_SRIOV_CURRENT_CAPABILITIES](https://msdn.microsoft.com/library/windows/hardware/hh451859)       | X |   |   | X |   |   |   
| [OID_SRIOV_HARDWARE_CAPABILITIES](https://msdn.microsoft.com/library/windows/hardware/hh451862)      | X |   |   | X |   |   |   
| [OID_SRIOV_PF_LUID](https://msdn.microsoft.com/library/windows/hardware/hh451864)                    | X |   |   | X |   |   |   
| [OID_SRIOV_PROBED_BARS](https://msdn.microsoft.com/library/windows/hardware/hh451870)                | X |   |   |   | X |   | 
| [OID_SRIOV_READ_VF_CONFIG_BLOCK](https://msdn.microsoft.com/library/windows/hardware/hh451874)       |   |   | X |   | X |   | 
| [OID_SRIOV_READ_VF_CONFIG_SPACE](https://msdn.microsoft.com/library/windows/hardware/hh451879)       |   |   | X |   | X |   | 
| [OID_SRIOV_RESET_VF](https://msdn.microsoft.com/library/windows/hardware/hh451889)                   |   | X |   |   | X |   | 
| [OID_SRIOV_SET_VF_POWER_STATE](https://msdn.microsoft.com/library/windows/hardware/hh451896)         |   | X |   |   | X |   |  
| [OID_SRIOV_VF_INVALIDATE_CONFIG_BLOCK](https://msdn.microsoft.com/library/windows/hardware/hh451903) |   |   | X |   |   | X | 
| [OID_SRIOV_VF_SERIAL_NUMBER](https://msdn.microsoft.com/library/windows/hardware/hh451909)           | X |   |   | X |   |   |   
| [OID_SRIOV_VF_VENDOR_DEVICE_ID](https://msdn.microsoft.com/library/windows/hardware/hh451913)        |   |   | X |   | X |   | 
| [OID_SRIOV_WRITE_VF_CONFIG_BLOCK](https://msdn.microsoft.com/library/windows/hardware/hh451918)      |   | X |   |   | X |   | 
| [OID_SRIOV_WRITE_VF_CONFIG_SPACE](https://msdn.microsoft.com/library/windows/hardware/hh451925)      |   | X |   |   | X |   |

