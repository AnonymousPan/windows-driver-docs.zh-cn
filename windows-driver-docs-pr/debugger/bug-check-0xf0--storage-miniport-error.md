---
title: Bug 检查 0xF0 STORAGE_MINIPORT_ERROR
description: STORAGE_MINIPORT_ERROR bug 检查的值为0x00000F0。 它表示存储微型端口驱动程序无法完成 SRB 请求。
keywords:
- Bug 检查 0xF0 STORAGE_MINIPORT_ERROR
- STORAGE_MINIPORT_ERROR
ms.date: 01/24/2019
topic_type:
- apiref
api_name:
- STORAGE_MINIPORT_ERROR
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: f60170ee227a41eb818b1555e866f4616dbac681
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89206123"
---
# <a name="bug-check-0xf0-storage_miniport_error"></a>Bug 检查0xF0：存储 \_ 微型端口 \_ 错误

存储 \_ 微型端口 \_ 错误检查的值为0x00000F0。 它表示存储微型端口驱动程序无法完成 SRB 请求。


> [!IMPORTANT]
> 本主题面向程序员。 如果您是在使用计算机时收到蓝屏错误代码的客户，请参阅[蓝屏错误疑难解答](https://www.windows.com/stopcode)。

 

## <a name="storage_miniport_error-parameters"></a>存储 \_ 微型端口 \_ 错误参数

|参数|说明|
|-------- |---------- |
|1| 错误代码。 请参阅下面的值。|
|2| 请参阅下面的值。|
|3| 请参阅下面的值。|
|4| 请参阅下面的值。|

**值**

```text
1: Miniport failed to complete a SRB request even after successful reset operation.
    2 - Driver name unicode string address
    3 - SRB address
    4 - Storport unit device object

2: Miniport failed to complete a SRB request even after successful abort operation for the SRB.
    2 - Driver name unicode string address
    3 - Abort SRB address
    4 - SRB that was being aborted

3: Miniport failed to complete a request within a given timeout.
    2 - Driver name unicode string address
    3 - SRB address
    4 - Timeout of the request

4: Miniport failed to complete a request for a crypto operation. This can occur if it is trying to enable an encryption key on an ICE (Inline Crypto Engine) enabled UFS host. 
    2 - Driver name unicode string address
    3 - The STOR_CRYPTO_OPERATION_TYPE for this failure, typically StorCryptoOperationInsertKey
    4 - Reserved    
```


## <a name="cause"></a>原因
-----

存储微型端口驱动程序中的 bug 保存了 SRB 请求，无法完成。 有关特定类型的故障，请参阅上面列出的错误代码值。


## <a name="resolution"></a>解决方法
-----

[！分析](-analyze.md)调试扩展显示有关 bug 检查的信息，可帮助确定根本原因。 

参数2中返回的驱动程序名称应指向有问题的驱动程序。


## <a name="see-also"></a>另请参阅
----------

[Bug 检查代码参考](bug-check-code-reference2.md)

[Storport 与 Storport 微型端口驱动程序的接口](../storage/storport-s-interface-with-storport-miniport-drivers.md)