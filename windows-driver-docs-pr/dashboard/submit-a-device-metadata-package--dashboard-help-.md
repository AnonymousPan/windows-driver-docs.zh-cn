---
title: 提交设备元数据包（仪表板帮助）
description: 提交设备元数据包（仪表板帮助）
ms.assetid: dcd35784-51c3-410a-8704-94f07fa8959a
ms.topic: article
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: bcbaa91af1ab9fa42ea5adc775ef4dd8876f18a7
ms.sourcegitcommit: 5598b4c767ab56461b976b49fd75e4e5fb6018d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "67364399"
---
# <a name="submit-a-device-metadata-package-dashboard-help"></a>提交设备元数据包（仪表板帮助）


在你已经创建新的设备元数据包或替换现有程序包后，可以提交该程序包以进行验证和后续发布。

## <a name="span-idsubmitting_a_device_metadata_packagespanspan-idsubmitting_a_device_metadata_packagespanspan-idsubmitting_a_device_metadata_packagespansubmitting-a-device-metadata-package"></a><span id="Submitting_a_device_metadata_package"></span><span id="submitting_a_device_metadata_package"></span><span id="SUBMITTING_A_DEVICE_METADATA_PACKAGE"></span>提交设备元数据包


你可以使用相同的方法提交用于预览或发布的包。

**提交设备元数据包**

1.  使用 [SignTool 工具](https://go.microsoft.com/fwlink/p/?LinkId=238330)对元数据包进行签名。

2.  从硬件开发人员中心或 Windows 开发人员中心，使用 Microsoft 帐户登录到“仪表板”  。

3.  在“设备元数据”  下，单击“创建体验”  （如果你希望提交新体验），或单击“管理体验”  （如果你希望修改现有体验）。

4.  浏览并选择你的新体验，然后单击“提交”  。

有关详细信息，请参阅[创建设备元数据体验](https://docs.microsoft.com/windows-hardware/drivers/dashboard/)或[管理设备元数据体验](https://docs.microsoft.com/windows-hardware/drivers/dashboard/)。

在提交过程中，仪表板将验证你的体验中的程序包。

### <a name="span-idpackage_validationspanspan-idpackage_validationspanspan-idpackage_validationspanpackage-validation"></a><span id="Package_validation"></span><span id="package_validation"></span><span id="PACKAGE_VALIDATION"></span>包验证

在验证期间，仪表板将对每个包执行以下操作：

-   确认文件已代码签名。

-   扫描病毒。

-   检查包结构。

-   根据相应的架构验证所有的 .xml 文件。

-   验证所有图标是否均符合指定的 Windows 操作系统。

-   验证 .xml 文件中的所有相关字段是否都指向现有资源。

-   验证需要的所有任务和状态元素是否已包含在 DeviceStage 包中。

-   验证绑定到设备体验的硬件认证提交是否用于正确的设备。

-   将日期值写入包，并确认设备体验。

-   创建并签名每个目录中的 .cat 文件以指明验证。

-   重建包并将其重命名为 GUID。

-   对设备元数据包进行签名。

### <a name="span-idsubmitting_a_service_metadata_packagespanspan-idsubmitting_a_service_metadata_packagespanspan-idsubmitting_a_service_metadata_packagespansubmitting-a-service-metadata-package"></a><span id="Submitting_a_service_metadata_package"></span><span id="submitting_a_service_metadata_package"></span><span id="SUBMITTING_A_SERVICE_METADATA_PACKAGE"></span>提交服务元数据包

有关提交某个移动宽带应用的服务元数据的信息，请参阅[服务元数据包提交](https://docs.microsoft.com/windows-hardware/drivers/mobilebroadband/index)。

## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>相关主题

- [创建设备元数据体验](https://docs.microsoft.com/windows-hardware/drivers/dashboard/)

- [管理设备元数据体验](https://docs.microsoft.com/windows-hardware/drivers/dashboard/)

- [提交批量元数据包](https://docs.microsoft.com/windows-hardware/drivers/dashboard/)

- [提交设备元数据体验时的错误和解决方案](https://docs.microsoft.com/windows-hardware/drivers/dashboard/)

 

 






