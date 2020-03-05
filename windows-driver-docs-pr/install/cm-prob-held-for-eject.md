---
title: CM_PROB_HELD_FOR_EJECT
description: CM_PROB_HELD_FOR_EJECT
ms.assetid: 8d67ad71-276d-4dea-b3fb-61fedcfba789
keywords:
- CM_PROB_HELD_FOR_EJECT
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: b76724cf14058e890ce97094a5ad460b4d36073a
ms.sourcegitcommit: 6f165a03303b7e4950b37d4b992f0f481b14f3ca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279546"
---
# <a name="code-47---cm_prob_held_for_eject"></a>代码 47-CM_PROB_HELD_FOR_EJECT

此设备管理器错误消息指示设备已准备好进行弹出。

## <a name="error-code"></a>错误代码

47

### <a name="display-message"></a>显示消息

"Windows 无法使用此硬件设备，因为它已为" 安全删除 "做好准备，但尚未从计算机中删除它。 （代码47） "

"若要解决此问题，请将此设备从计算机中拔出，然后再次插上。"

### <a name="recommended-resolution"></a>建议的解决方法

拔出设备并重新插入。 或者，选择 "**重新启动计算机**" 将重新启动计算机并使设备可用。

仅当用户调用热插拔程序来准备要删除的设备时（调用[**CM_Request_Device_Eject**](https://docs.microsoft.com/windows/desktop/api/cfgmgr32/nf-cfgmgr32-cm_request_device_ejectw)）或者如果用户按下物理弹出按钮（它调用[**IoRequestDeviceEject**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iorequestdeviceeject)）时，才会发生此错误。 用户可以准备当前不可删除的设备，例如，光盘在便携式计算机和扩展坞托盘之间补漏白。
