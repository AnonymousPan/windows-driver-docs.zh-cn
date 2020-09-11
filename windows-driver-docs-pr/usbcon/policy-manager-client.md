---
description: '客户端驱动程序可参与 USB C # C 连接器的策略决策。'
title: 编写 USB 类型 C 策略管理器客户端驱动程序
ms.date: 10/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 85ee8115a10f72ded6e5ec59f5712605cb8efb6f
ms.sourcegitcommit: 937974aa9bbe0262a7ffe9631593fab48c4e7492
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2020
ms.locfileid: "90010641"
---
# <a name="write-a-usb-type-c-policy-manager-client-driver"></a>编写 USB 类型 C 策略管理器客户端驱动程序

Microsoft 提供的 USB 类型-C 策略管理器监视 USB 类型 C 连接器的活动。 Windows 版本1809引入了一组编程接口，可用于将客户端驱动程序写入到策略管理器中 (名为 _PM 客户端驱动程序_ 的) 。 客户端驱动程序可参与 USB C # C 连接器的策略决策。 使用此设置，可以选择写入内核模式导出驱动程序或用户模式驱动程序。

策略管理器获取并协调 USB 连接器管理器中的信息 (UCM) 、USB 主机控制器和 USB 功能，以及 PM 客户端驱动程序。 需要用户界面通知时，策略管理器会将请求发送到系统 Shell。

![用于 USB 策略管理器的 Architechtural 块关系图](images/pmclient.png)

有关驱动程序的完整视图，请参阅 [体系结构：适用于 Windows 系统的 USB 类型 C 设计](./architecture--usb-type-c-in-a-windows-system.md)。

## <a name="important-apis"></a>重要的 API
PM Api 在 [Usbpmapi](/windows-hardware/drivers/ddi/usbpmapi) 标头中声明。
 
## <a name="1-client-registration"></a>1：客户端注册

1. 客户端驱动程序调用 [**UsbPm_Register**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_register) 来注册驱动程序的回调函数。
2. 客户端驱动程序将等待来自策略管理器的事件。 
    > 成功的 **UsbPm_Register** 调用并不保证客户端驱动程序已请求访问。 当策略管理器准备就绪时，将使用**PolicyManagerArrival**作为事件数据调用驱动程序的[**EVT_USBPM_EVENT_CALLBACK**](/windows-hardware/drivers/ddi/usbpmapi/nc-usbpmapi-evt_usbpm_event_callback) ，以指示实际授予的访问权限。
3. **UsbPm_Register**调用返回注册句柄。
    > 即使**UsbPm_Register**返回，客户端驱动程序也可能会收到**EVT_USBPM_EVENT_CALLBACK** 。

## <a name="2-hub-arrival"></a>2：中心到达

1. UCMCX 设备到达后，会通知策略管理员，并跟踪所有中心句柄，同时跟踪每个中心上所有连接器的属性和状态。
2. 将**HubArrivalRemoval**作为事件数据调用客户端驱动程序的[**EVT_USBPM_EVENT_CALLBACK**](/windows-hardware/drivers/ddi/usbpmapi/nc-usbpmapi-evt_usbpm_event_callback) 。 调用还包含中心句柄。
3. 在 **EVT_USBPM_EVENT_CALLBACK**的客户端驱动程序实现中，驱动程序调用 [**UsbPm_RetrieveHubProperties**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_retrievehubproperties) 以获取集线器上的连接器数量，然后调用 [**UsbPm_RetrieveConnectorProperties**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_retrieveconnectorproperties) 和 [**UsbPm_RetrieveConnectorState**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_retrieveconnectorstate) 以获取有关每个连接器的详细信息。

## <a name="3-connector-state-change"></a>3：连接器状态更改 
1. 由于连接器状态发生更改，例如键入-C 附加/分离、PD 协定协商，策略管理器会更新每个连接器的状态信息。 
2. 将**ConnectorStateChange**作为事件数据调用客户端驱动程序的[**EVT_USBPM_EVENT_CALLBACK**](/windows-hardware/drivers/ddi/usbpmapi/nc-usbpmapi-evt_usbpm_event_callback) 。 调用还包含连接器句柄。
3. 还会调用客户端驱动程序的完成例程，并相应地采取措施。
4. 在 **EVT_USBPM_EVENT_CALLBACK**的客户端驱动程序实现中，驱动程序将调用 [**UsbPm_RetrieveConnectorProperties**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_retrieveconnectorproperties)。 通过使用给定的连接器句柄，driverto 将获取最新的连接器状态，对其进行检查，并可能决定更新其本地副本。  
 
## <a name="4-change-initiated-by-the-client-driver"></a>4：客户端驱动程序启动的更改

1. 若要请求更改客户端驱动程序调用  [**UsbPm_AssignConnectorPowerLevel**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_assignconnectorpowerlevel)。
    > 客户端驱动程序可以在使用**UsbPm_Register**注册的**EVT_USBPM_EVENT_CALLBACK**回调内调用此函数。

2. 策略管理器将请求转发到 USB 连接器管理器 (UCM) 。 UcmCx 的客户端驱动程序采取适当的措施来更改请求的状态。
3. 将**ConnectorStateChange**作为事件数据调用客户端驱动程序的[**EVT_USBPM_EVENT_CALLBACK**](/windows-hardware/drivers/ddi/usbpmapi/nc-usbpmapi-evt_usbpm_event_callback) 。 调用还包含连接器句柄。
4. 还会调用客户端驱动程序的完成例程，并相应地采取措施。
5. 在回调中，客户端驱动程序调用与给定连接器句柄 [**UsbPm_RetrieveConnectorState**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_retrieveconnectorproperties) ，以获取最新的连接器状态，对其进行检查，并可能决定更新其本地副本。

 
## <a name="5-hub-removal"></a>5：集线器删除

1. 当 UcmCx 设备 (不是 UcmCx 设备) 上的单个连接器时，UCM 通知策略管理器。 策略管理器从中心集合中删除中心。
2. 将**HubRemoval**作为事件数据调用客户端驱动程序的[**EVT_USBPM_EVENT_CALLBACK**](/windows-hardware/drivers/ddi/usbpmapi/nc-usbpmapi-evt_usbpm_event_callback)实现。 此调用还包含集线器句柄。
3. 在 **EVT_USBPM_EVENT_CALLBACK**的客户端驱动程序实现中，客户端驱动程序为要删除的集线器和连接器执行清理任务。 驱动程序可以调用 [**UsbPm_RetrieveHubProperties**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_retrievehubproperties) 和 [**UsbPm_RetrieveConnectorProperties**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_retrieveconnectorproperties) 以获取集线器和连接器的属性。
 
## <a name="6-client-deregistration"></a>6：客户端注销 
1. 当驱动程序不再需要任何通知时，客户端驱动程序将调用 [**UsbPm_Deregister**](/windows-hardware/drivers/ddi/usbpmapi/nf-usbpmapi-usbpm_register) 。
2. 策略管理器将客户端句柄注册标记为已取消注册，并且不会调用 **EVT_USBPM_EVENT_CALLBACK** 回调。

## <a name="see-also"></a>另请参阅

[编写 USB 类型 C 连接器驱动程序](./bring-up-a-usb-type-c-connector-on-a-windows-system.md)

[编写 USB 类型 C 端口控制器驱动程序](./write-a-usb-type-c-port-controller-driver.md)

[编写 USB 功能控制器客户端驱动程序](./function-client-driver.md)