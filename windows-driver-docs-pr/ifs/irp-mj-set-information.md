---
title: IRP_MJ_SET_INFORMATION （IFS）
description: IRP\_MJ\_SET\_INFORMATION
ms.assetid: cc1b539c-8d39-4f4d-93b1-ce9fcdb8c555
keywords:
- IRP_MJ_SET_INFORMATION 可安装的文件系统驱动程序
topic_type:
- apiref
api_name:
- IRP_MJ_SET_INFORMATION
api_type:
- NA
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: b116945fa0ab3b1681179a61d6aa47bc8b6029a2
ms.sourcegitcommit: f788aa204a3923f9023d8690488459a4d9bc2495
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86141233"
---
# <a name="irp_mj_set_information-ifs"></a>IRP \_ MJ \_ 集 \_ 信息（IFS）


## <a name="when-sent"></a>发送时间


IRP \_ MJ \_ 集 \_ 信息请求由 i/o 管理器和其他操作系统组件以及其他内核模式驱动程序发送。 例如，可以在用户模式应用程序调用 Microsoft Win32 函数（如**SetEndOfFile** ）或内核模式组件调用[**ZwSetInformationFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntsetinformationfile)时发送。

## <a name="operation-file-system-drivers"></a>操作：文件系统驱动程序


文件系统驱动程序应提取并解码文件对象，以确定它是表示用户文件还是打开目录。 如果是这样，则文件系统驱动程序应适当处理请求并完成 IRP。

可以在文件和目录上设置以下类型的信息：

FileBasicInformation

FileDispositionInformation

FileLinkInformation （适用于允许在目录层次结构中创建循环的文件系统）

FilePositionInformation

FileRenameInformation

只能对文件设置以下类型的信息：

FileAllocationInformation

FileEndOfFileInformation

FileLinkInformation （对于不允许在目录层次结构中创建循环的文件系统，例如 NTFS）

FileValidDataLengthInformation

## <a name="operation-file-system-filter-drivers"></a>操作：文件系统筛选器驱动程序


筛选器驱动程序必须将此 IRP 传递到堆栈上的下一个较低版本的驱动程序。

## <a name="parameters"></a>参数


文件系统或筛选器驱动程序与给定的 IRP 一起调用[**IoGetCurrentIrpStackLocation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetcurrentirpstacklocation) ，以获取指向其自己的*IrpSp*[**堆栈位置**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_stack_location)的指针，如以下列表所示。 （IRP 显示为*irp*。）驱动程序可以使用 IRP 的下列成员中设置的信息，并使用 IRP 堆栈位置来处理 set file information 请求：

<a href="" id="deviceobject"></a>*DeviceObject*  
指向目标设备对象的指针。

<a href="" id="irp--associatedirp-systembuffer"></a>*Irp- &gt;AssociatedIrp.SystemBuffer*  
指向包含要设置的文件或目录信息的输入缓冲区的指针。 此信息存储在以下结构之一中：

[**文件 \_ 分配 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_allocation_information)

[**文件 \_ 基本 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_basic_information)

[**文件 \_ 处置 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_disposition_information)

[**文件 \_ 末尾 \_ 的 \_ 文件 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_end_of_file_information)

[**文件 \_ 链接 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_link_information)

[**文件 \_ 位置 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_position_information)

[**文件 \_ 重命名 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_rename_information)

[**文件 \_ 有效的 \_ 数据 \_ 长度 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_valid_data_length_information)

<a href="" id="irp--iostatus"></a>*Irp- &gt;IoStatus*指向[**IO \_ 状态 \_ 块**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_status_block)结构的指针，该结构接收最终完成状态和有关请求的操作的信息。 有关详细信息，请参阅[**ZwSetInformationFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntsetinformationfile)的*IoStatusBlock*参数说明。

<a href="" id="irpsp--fileobject"></a>*IrpSp- &gt;* 指向与*DeviceObject*关联的文件对象的 FileObject 指针。

*IrpSp- &gt; FileObject*参数包含指向**RelatedFileObject**字段的指针，该字段也是文件 \_ 对象结构。 文件对象结构的**RelatedFileObject**字段在 \_ 处理 IRP \_ MJ 集信息期间无效 \_ \_ ，不应使用。

<a href="" id="irpsp--majorfunction"></a>*IrpSp- &gt;MajorFunction*指定 IRP \_ MJ \_ 集 \_ 信息。

<a href="" id="irpsp--parameters-setfile-advanceonly"></a>*IrpSp- &gt;SetFile. AdvanceOnly*用于文件结束操作的标志。 这会确定在**FileInformationClass**FileEndOfFileInformation 时，使用**EndOfFile**成员[**文件的 \_ \_ \_ 文件 \_ 结尾**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_end_of_file_information)  ==  **FileEndOfFileInformation**。 如果**为 TRUE**，则仅当文件增加当前有效数据长度时，才从**EndOfFile**设置新的有效数据长度。 如果**为 FALSE**，则从**EndOfFile**设置新的文件大小。

<a href="" id="irpsp--parameters-setfile-clustercount"></a>*IrpSp- &gt;SetFile*保留供系统使用。

<a href="" id="irpsp--parameters-setfile-deletehandle"></a>*IrpSp- &gt;SetFile*保留供系统使用。

<a href="" id="irpsp--parameters-setfile-fileinformationclass"></a>*IrpSp- &gt;SetFile. FileInformationClass*指定要为文件设置的信息类型。 下列情况之一：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">值</th>
<th align="left">含义</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>FileAllocationInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_allocation_information" data-raw-source="[&lt;strong&gt;FILE_ALLOCATION_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_allocation_information)"><strong>FILE_ALLOCATION_INFORMATION</strong></a> 。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>FileBasicInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_basic_information" data-raw-source="[&lt;strong&gt;FILE_BASIC_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_basic_information)"><strong>FILE_BASIC_INFORMATION</strong></a> 。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>FileDispositionInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_disposition_information" data-raw-source="[&lt;strong&gt;FILE_DISPOSITION_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_disposition_information)"><strong>FILE_DISPOSITION_INFORMATION</strong></a> 。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>FileEndOfFileInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_end_of_file_information" data-raw-source="[&lt;strong&gt;FILE_END_OF_FILE_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_end_of_file_information)"><strong>FILE_END_OF_FILE_INFORMATION</strong></a> 。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>FileLinkInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_link_information" data-raw-source="[&lt;strong&gt;FILE_LINK_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_link_information)"><strong>FILE_LINK_INFORMATION</strong></a> 。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>FilePositionInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_position_information" data-raw-source="[&lt;strong&gt;FILE_POSITION_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_position_information)"><strong>FILE_POSITION_INFORMATION</strong></a> 。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>FileRenameInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_rename_information" data-raw-source="[&lt;strong&gt;FILE_RENAME_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_rename_information)"><strong>FILE_RENAME_INFORMATION</strong></a> 。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>FileValidDataLengthInformation</strong></p></td>
<td align="left"><p>为文件设置<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_valid_data_length_information" data-raw-source="[&lt;strong&gt;FILE_VALID_DATA_LENGTH_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_valid_data_length_information)"><strong>FILE_VALID_DATA_LENGTH_INFORMATION</strong></a> 。</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="irpsp--parameters-setfile-fileobject"></a>*IrpSp- &gt;* 用于重命名或链接操作的 SetFile。 如果*irp &gt;AssociatedIrp.SystemBuffer &gt; *包含完全限定的文件名，或者*irp- &gt;AssociatedIrp.SystemBuffer- &gt; RootDirectory*为非**NULL**，则此成员是作为操作目标的文件的父目录的文件对象指针。 否则为**NULL**。

<a href="" id="irpsp--parameters-setfile-length"></a>*IrpSp- &gt;SetFile* * &gt; temBuffer 所AssociatedIrp.Sys*指向的缓冲区的长度（以字节为单位）。

<a href="" id="irpsp--parameters-setfile-replaceifexists"></a>*IrpSp- &gt;SetFile*设置为**TRUE** ，以指定如果已存在具有相同名称的文件，则应将其替换为给定的文件。 如果重命名操作在已存在具有给定名称的文件时失败，则设置为**FALSE** 。

<a name="remarks"></a>备注
-------

缓存管理器将**AdvanceOnly**成员设置为**TRUE** ，以通知文件系统将磁盘上的当前有效数据长度提升到**EndOfFile**中的新有效数据长度。 如果**AdvanceOnly**为**FALSE**，则会设置**EndOfFile**成员中的新文件大小，该大小可大于或小于当前文件大小。

## <a name="see-also"></a>另请参阅


[**文件 \_ 分配 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_allocation_information)

[**文件 \_ 基本 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_basic_information)

[**文件 \_ 处置 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_disposition_information)

[**文件 \_ 末尾 \_ 的 \_ 文件 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_end_of_file_information)

[**文件 \_ 链接 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_link_information)

[**文件 \_ 位置 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_position_information)

[**文件 \_ 重命名 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_rename_information)

[**文件 \_ 有效的 \_ 数据 \_ 长度 \_ 信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_valid_data_length_information)

[**IO \_ 堆栈 \_ 位置**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_stack_location)

[**IO \_ 状态 \_ 块**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_io_status_block)

[**IoGetCurrentIrpStackLocation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetcurrentirpstacklocation)

[**IRP**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_irp)

[**IRP \_ MJ \_ 查询 \_ 信息**](irp-mj-query-information.md)

[**ZwSetInformationFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntsetinformationfile)

 

 






