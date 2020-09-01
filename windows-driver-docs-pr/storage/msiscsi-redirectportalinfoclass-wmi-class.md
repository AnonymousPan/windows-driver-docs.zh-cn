---
title: MSiSCSI \_ REDIRECTPORTALINFOCLASS WMI 类
description: MSiSCSI \_ REDIRECTPORTALINFOCLASS WMI 类
ms.assetid: 38f510ed-1f31-4b3c-84c6-515f5d42a1f8
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 779f7a638f55fa9862e5a672d78aa9082ca567d5
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89185421"
---
# <a name="msiscsi_redirectportalinfoclass-wmi-class"></a>MSiSCSI \_ REDIRECTPORTALINFOCLASS WMI 类


MSiSCSI \_ REDIRECTPORTALINFOCLASS WMI 类包含适配器 ID 的会话集合。 此外，它还包含每个会话的门户重定向信息。 此类在*管理 mof*中定义为：

```cpp
class MSiSCSI_RedirectPortalInfoClass
{
    [read,key] String InstanceName;

    [read] boolean Active;

    [read,
     WmiDataId(1),
     DisplayName("Adapter Id") : amended,
     DisplayInHex,
     description("Id that is globally unique for all instances of iSCSI initiators.") : amended,
     WmiVersion(1)
    ]
    uint64 UniqueAdapterId;

    [read,
     WmiDataId(2),
     DisplayName("Number of session on the adapter : Number of elements in RedirectSessionInfo array") : amended,
     Description("Number of elements in RedirectSessionInfo array") : amended,
     WmiVersion(1)
    ] uint32 SessionCount;

    [read,
     WmiDataId(3),
     DisplayName("List Of ISCSI_RedirectSessionInfo ") : amended,
     Description("Variable length array of ISCSI_RedirectSessionInfo. SessionCount specifies the number of elements in the array. NOTE: this is a variable length array.") : amended,
     WmiSizeIs("SessionCount"),
     WmiVersion(1)
    ] ISCSI_RedirectSessionInfo RedirectSessionList[];
};
```

当 WMI 工具套件编译上述类定义时，它会生成 [**MSiSCSI \_ RedirectPortalInfoClass**](/windows-hardware/drivers/ddi/iscsimgt/ns-iscsimgt-_msiscsi_redirectportalinfoclass) 数据结构。

 

