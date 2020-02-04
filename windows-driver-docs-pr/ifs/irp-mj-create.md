---
title: IRP_MJ_CREATE
description: IRP\_MJ\_CREATE
ms.assetid: fdcc81f0-e571-4194-88cd-d0956ca1577e
keywords:
- IRP_MJ_CREATE 可安装的文件系统驱动程序
topic_type:
- apiref
api_name:
- IRP_MJ_CREATE
api_type:
- NA
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0b6626a0bc3a480b6bef4cfb98ad0bf4a970d581
ms.sourcegitcommit: c9fc8f401d13ea662709ad1f0cb41c810e7cb4c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977688"
---
# <a name="irp_mj_create"></a>IRP\_MJ\_CREATE


## <a name="when-sent"></a>发送时间


创建新文件或目录时，或在打开现有文件、设备、目录或卷时，i/o 管理器会将 IRP\_MJ 发送\_创建请求。 通常，此 IRP 是代表用户模式应用程序发送的，该应用程序已调用 Microsoft Win32 函数（如[**CreateFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-createfilea) ）或代表已调用[**IoCreateFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iocreatefile)、 [**IoCreateFileSpecifyDeviceObjectHint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefilespecifydeviceobjecthint)、 [**ZwCreateFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntcreatefile)或[**ZwOpenFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntopenfile)的内核模式组件。 如果创建请求成功完成，则应用程序或内核模式组件会接收文件对象的句柄。

## <a name="operation-file-system-drivers"></a>操作：文件系统驱动程序


如果目标设备对象是文件系统的控制设备对象，则在将*irp&gt;IoStatus*和*IRP&gt;IoStatus*设置为合适的值后，文件系统驱动程序的调度例程必须完成 irp 并返回相应的 NTSTATUS 值。

否则，文件系统驱动程序应处理创建请求。

## <a name="operation-file-system-filter-drivers"></a>操作：文件系统筛选器驱动程序


如果目标设备对象是筛选器驱动程序的控制设备对象，则筛选器驱动程序的调度例程必须完成 IRP 并返回相应的 NTSTATUS 值，然后将 IoStatus 设置为相应的值，然后再 *&gt;* 将 Irp *&gt;IoStatus。*

否则，筛选器驱动程序应执行任何所需的处理，并根据筛选器的性质，完成 IRP，或将其向下传递到堆栈上的下一个较低的驱动程序。

通常，筛选器驱动程序不应返回**状态\_等待**，以响应**IRP\_MJ\_CREATE**。 但是，如果较低级别的驱动程序返回**状态\_"挂起**"，则筛选器驱动程序应将此状态值向上传递到驱动程序链。

文件系统筛选器驱动程序编写器应注意到， [**IoCreateStreamFileObject**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-iocreatestreamfileobject)导致[**IRP\_MJ\_清理**](irp-mj-cleanup.md)请求发送到卷的文件系统驱动程序堆栈。 由于文件系统通常会将流文件对象创建为**IRP\_MJ\_create**以外的操作的副作用，因此筛选器驱动程序很难可靠地检测流文件对象创建。 因此，筛选器驱动程序应该接收**IRP\_mj\_清理**和[**irp\_MJ\_关闭**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mj-close)以前不可见的文件对象的请求。 对于[**IoCreateStreamFileObjectLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-iocreatestreamfileobjectlite)，不会发送**IRP\_MJ\_清理**请求。

&gt; \[！注意\] &gt; 当旧筛选器驱动程序在创建后回调中重新发出 create 时，它们必须释放并将与其重新分析点（辅助缓冲区）关联的缓冲区设置为**NULL**。 如果旧筛选器驱动程序未释放此缓冲区并将其设置为**NULL**，则驱动程序将泄漏内存。 微筛选器驱动程序不一定要这样做，因为筛选器管理器会为其执行此操作。

 

## <a name="parameters"></a>参数


文件系统或筛选器驱动程序与给定的 IRP 一起调用[**IoGetCurrentIrpStackLocation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetcurrentirpstacklocation) ，以获取指向其自己的*IrpSp*[**堆栈位置**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_stack_location)的指针，如以下列表所示。 （IRP 显示为*irp*。）驱动程序可以使用 IRP 的下列成员中设置的信息，并使用 IRP 堆栈位置来处理创建请求：

<a href="" id="deviceobject"></a>*DeviceObject*  
指向目标设备对象的指针。

<a href="" id="irp--associatedirp-systembuffer"></a>*Irp-&gt;AssociatedIrp. SystemBuffer*  
如果文件对象表示具有扩展属性的文件，则为指向[**文件\_完整\_EA\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_full_ea_information)结构缓冲区的指针。 否则，此成员设置为**NULL**。

<a href="" id="irp--flags"></a>*Irp-&gt;标志*  
已为此请求设置以下标志：

IRP\_创建\_操作

IRP\_延迟\_IO\_完成

IRP\_同步\_API

<a href="" id="irp--requestormode"></a>*Irp-&gt;irp->requestormode*指示请求操作的进程的执行模式，可以是**KernelMode**或**UserMode**。 请注意，如果设置了 SL\_强制\_访问\_检查标志，则即使*Irp&gt;irp->requestormode*为 KernelMode，也必须执行访问检查。

<a href="" id="irp--iostatus"></a>*Irp-&gt;IoStatus*指向[**IO\_状态的指针\_块**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_status_block)结构，它接收最终完成状态和有关请求的操作的信息。 文件系统将此结构的**信息**成员设置为以下值之一：

已创建文件\_

文件\_\_不\_存在

文件\_存在

文件\_打开

\_覆盖文件

文件\_被取代

<a href="" id="irp--overlay-allocationsize"></a>*Irp-&gt;覆盖 AllocationSize*文件的初始分配大小（以字节为单位）。 如果创建、覆盖或取代了文件，则非零值将不起作用。

<a href="" id="irpsp--fileobject"></a>*IrpSp-&gt;FileObject*一个指针，指向 i/o 管理器创建的文件对象，该对象表示要创建或打开的文件。 当文件系统处理 IRP\_MJ\_创建请求时，它会将此文件对象中的**FsContext**和可能的**FsContext2**字段设置为特定于文件的值。 因此，在文件系统处理创建请求之前，不能将**FsContext**和**FsContext2**字段的值视为有效。 有关详细信息，请参阅[文件流、流上下文和每个流的上下文](https://docs.microsoft.com/windows-hardware/drivers/ifs/file-streams--stream-contexts--and-per-stream-contexts)。

[**FltCancelFileOpen**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcancelfileopen)和[**IOCANCELFILEOPEN**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocancelfileopen)设置\_文件\_在文件对象的 "**标志**" 字段中打开\_取消标记。 如果设置此标志，则表明 IRP\_MJ\_创建请求已取消，并且将对此文件对象发出[**irp\_MJ\_关闭**](irp-mj-close.md)请求。 一旦取消创建请求，就无法重新颁发。

*&gt;IrpSp FileObject*参数包含指向**RelatedFileObject**字段的指针，该字段也是文件\_对象结构。 文件\_对象结构的 " **RelatedFileObject** " 字段用于指示给定文件是相对于已打开的文件对象打开的。 这通常表示相对文件是一个目录，但基于流的文件可能会相对于现有的文件流打开。 文件\_对象结构的**RelatedFileObject**字段仅在处理 IRP\_MJ\_CREATE 期间有效。

<a href="" id="irpsp--flags"></a>*IrpSp-&gt;标志*以下一项或多项操作：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">旗帜</th>
<th align="left">含义</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>SL_CASE_SENSITIVE</p></td>
<td align="left"><p>如果设置了此标志，则文件名比较应区分大小写。</p></td>
</tr>
<tr class="even">
<td align="left"><p>SL_FORCE_ACCESS_CHECK</p></td>
<td align="left"><p>如果设置此标志，则即使<em>IRP&gt;irp->requestormode</em>的值为<strong>KernelMode</strong>，也必须执行访问检查。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>SL_OPEN_PAGING_FILE</p></td>
<td align="left"><p>如果设置了此标志，则该文件为页面文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>SL_OPEN_TARGET_DIRECTORY</p></td>
<td align="left"><p>如果设置此标志，则应打开文件的父目录。</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="irpsp--majorfunction"></a>*IrpSp-&gt;MajorFunction*指定 IRP\_MJ\_CREATE。

<a href="" id="irpsp--parameters-create-ealength"></a>*IrpSp-&gt;参数. EaLength*Irp 的缓冲区大小（以字节为单位） *-&gt;AssociatedIrp. SystemBuffer*。 如果*Irp&gt;AssociatedIrp*的值为**NULL**，则此成员必须为零。

<a href="" id="irpsp--parameters-create-fileattributes"></a>*IrpSp-&gt;参数. FileAttributes*要在创建或打开文件时应用的特性标志的位掩码。 仅当创建、取代或在某些情况下覆盖了文件时，才应用显式指定的属性。 默认情况下，此值为 FILE\_特性\_NORMAL，可以通过任何其他标志或兼容标志的运算组合重写。 此成员对应于[**IoCreateFileSpecifyDeviceObjectHint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefilespecifydeviceobjecthint)的*FileAttributes*参数。

<a href="" id="irpsp--parameters-create-options"></a>*IrpSp-&gt;参数。创建. 选项*标志的位掩码，用于指定创建或打开该文件时要应用的选项，以及在文件已存在时要执行的操作。

此参数的高8位对应于[**IoCreateFileSpecifyDeviceObjectHint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefilespecifydeviceobjecthint)的*处置*参数。

此成员的低24位对应于[**IoCreateFileSpecifyDeviceObjectHint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefilespecifydeviceobjecthint)的*CreateOptions*参数。 执行文件扫描（如防病毒程序）的文件系统筛选器和微筛选器驱动程序应特别注意文件\_完成\_如果\_OPLOCKED 标志。 如果设置了此标志，则筛选器不能阻止或延迟 IRP\_MJ\_创建操作。

如果文件\_完成\_如果在预创建（创建调度）路径中设置\_OPLOCKED 标志，则筛选器不能启动以下任何类型的操作，因为它们可能会导致 oplock 中断：

IRP\_MJ\_清除 IRP\_MJ\_CREATE IRP\_MJ\_FILE\_SYSTEM\_CONTROL IRP\_MJ\_FLUSH\_缓冲 IRP\_mj\_"锁定"\_控件 IRP\_MJ\_读取 IRP\_MJ\_设置\_信息 IRP\_t_23_ OPLOCKED 标志，必须完成 IRP\_MJ\_创建请求，状态\_共享\_冲突。

如果在完成（创建后）路径中设置了\_OPLOCKED 标志，则该文件\_\_完成，筛选器应检查文件系统是否已将*Irp-&gt;IoStatus*状态设置为\_进度状态值\_中断\_的状态。 如果未设置此状态值，筛选器将对该文件启动上述一项操作是安全的。 如果设置此状态值，则 oplock 尚未中断，筛选器不能启动可能导致 oplock 中断的任何操作。 因此，在满足以下条件之一之前，筛选器必须将上述所有操作推迟到该文件中：

-   Oplock 的所有者将发送 FSCTL\_OPLOCK\_BREAK\_确认请求发送到文件系统。
-   除筛选器或微筛选器外的系统组件会向文件系统发送必须等待 oplock 中断完成的 i/o 请求（如 IRP\_MJ\_READ 或 IRP\_MJ\_WRITE）。 筛选器或微筛选器可以为此新操作从其调度（或 preoperation 回调）例程启动上述操作之一，因为调度或 preoperation 回调例程将进入等待状态，直到 oplock 中断完成。

<a href="" id="irpsp--parameters-create-securitycontext--accessstate"></a>*IrpSp-&gt;参数. SecurityContext-&gt;AccessState*指向[**访问\_状态**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_access_state)结构的指针，该结构包含对象的主题上下文、授予访问类型和剩余所需的访问类型。

<a href="" id="irpsp--parameters-create-securitycontext--desiredaccess"></a>*IrpSp-&gt;参数. SecurityContext-&gt;DesiredAccess*访问\_掩码结构，用于指定为文件请求的访问权限。 有关详细信息，请参阅[**IoCreateFileSpecifyDeviceObjectHint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefilespecifydeviceobjecthint)的*DesiredAccess*参数说明。

<a href="" id="irpsp--parameters-create-shareaccess"></a>*IrpSp-&gt;参数. ShareAccess*为文件请求的共享访问权限位掩码。 如果此成员为零，则请求进行独占访问。 有关详细信息，请参阅[**IoCreateFileSpecifyDeviceObjectHint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefilespecifydeviceobjecthint)的*ShareAccess*参数说明。

## <a name="see-also"></a>另请参阅


[**访问\_掩码**](https://docs.microsoft.com/windows-hardware/drivers/kernel/access-mask)

[**访问\_状态**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_access_state)

[**文件\_完整\_EA\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_full_ea_information)

[**FltCancelFileOpen**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcancelfileopen)

[**FltReissueSynchronousIo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltreissuesynchronousio)

[**IO\_堆栈\_位置**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_stack_location)

[**IO\_状态\_块**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_status_block)

[**IoCancelFileOpen**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocancelfileopen)

[**IoCheckEaBufferValidity**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-iocheckeabuffervalidity)

[**IoCreateFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iocreatefile)

[**IoCreateFileSpecifyDeviceObjectHint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefilespecifydeviceobjecthint)

[**IoCreateStreamFileObject**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-iocreatestreamfileobject)

[**IoCreateStreamFileObjectLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-iocreatestreamfileobjectlite)

[**IoGetCurrentIrpStackLocation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetcurrentirpstacklocation)

[**IRP**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_irp)

[**IRP\_MJ\_清除**](irp-mj-cleanup.md)

[**IRP\_MJ\_关闭**](irp-mj-close.md)

[**IRP\_MJ\_创建（WDK 内核引用）** ](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mj-create)

[**ZwCreateFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntcreatefile)

[**ZwOpenFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntopenfile)

 

 






