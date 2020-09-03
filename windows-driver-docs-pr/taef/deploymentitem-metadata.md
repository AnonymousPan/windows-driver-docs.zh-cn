---
title: DeploymentItem 元数据
description: DeploymentItem 元数据
ms.assetid: 7F18CD71-F000-4231-9093-82980EB7584D
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 412f6f13dbeeac7771b0d0519d0229879d097478
ms.sourcegitcommit: 7ca2d3e360a4ae1d4d3c3092bd34492a2645ef74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89403470"
---
# <a name="deploymentitem-metadata"></a>DeploymentItem 元数据


**DeploymentItem** 元数据标识测试执行期间测试所使用的文件和文件夹的文件和文件夹依赖项，以便 Taef 可以确定并适当地复制它们 (例如，在 [跨计算机执行方案](cross-machine-execution.md)中，Taef 会将 **DeploymentItem** 属性标识的文件部署到) 指定的测试计算机。

Taef DeploymentItem 实现非常类似于 VSTS 的 [类似功能](/dotnet/api/microsoft.visualstudio.testtools.unittesting.deploymentitemattribute?view=mstest-net-1.2.0)。

DeploymentItem 元数据可以应用于程序集、类或测试级别。 DeploymentItem 元数据指定的项将由与 (程序集、测试类或测试) 安装程序运行的时间通信来部署。 如果 DeploymentItem 元数据指定了依赖项 (例如，文件) 并且目标上已存在该依赖项，则 TAEF 将进行 CRC 比较，并且仅复制该文件（如果该文件已更改）。 如果 DeploymentItem 元数据指定了依赖关系，但找不到依赖项，则会记录错误，该错误将) 测试 (或所有测试类或程序集测试。 对于每个程序集、类或测试，TAEF 将仅部署文件一次，即，如果这些是数据驱动的，则不会在每个程序集、类或测试扩展上进行部署。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


<span id="General_Usage_"></span><span id="general_usage_"></span><span id="GENERAL_USAGE_"></span>常规用法   

<span id="_DeploymentItem__FileOrFolderToDeploy____DestinationFolder___"></span><span id="_deploymentitem__fileorfoldertodeploy____destinationfolder___"></span><span id="_DEPLOYMENTITEM__FILEORFOLDERTODEPLOY____DESTINATIONFOLDER___"></span>\[DeploymentItem ( "FileOrFolderToDeploy"，"DestinationFolder" ) \]  
where

<span id="FileOrFolderToDeploy"></span><span id="fileorfoldertodeploy"></span><span id="FILEORFOLDERTODEPLOY"></span>FileOrFolderToDeploy  
是相对于测试 dll 所在目录的文件或文件夹路径。 如果 **FileOrFolderToDeploy** 是一个文件夹，则会复制其所有内容;但是，不会创建文件夹本身。 如果 **FileOrFolderToDeploy**下有一个文件夹层次结构，则 Taef 将以递归方式复制所有这些目录，并保持其目录层次结构。

<span id="DestinationFolder"></span><span id="destinationfolder"></span><span id="DESTINATIONFOLDER"></span>DestinationFolder  
是相对于测试 dll 所在的目录的文件夹路径，以及要将部署项复制到的位置。 可以使用指定**DestinationFolder**路径。 notation (例如，... \\MyFiles) 。

如果只想部署到测试 dll 所在的文件夹，可以省略 **DestinationFolder** ：

```cpp
[DeploymentItem("FileOrFolderToDeploy")]
```

支持多个属性部分。 例如：

```cpp
[TestClass]
[DeploymentItem("file1.xml")]
[DeploymentItem("file2.xml")]
[DeploymentItem("file3.xml")]
public class UnitTest1
{
    ...
}
```

## <a name="span-idexamplesspanspan-idexamplesspanspan-idexamplesspanexamples"></a><span id="Examples"></span><span id="examples"></span><span id="EXAMPLES"></span>示例


<span id="_deploymentitem__file1.xml___"></span><span id="_DEPLOYMENTITEM__FILE1.XML___"></span>\[DeploymentItem ( "file1.xml" ) \]  
作为依赖项位于测试 dll 旁边 file1.xml 标记。 可以将此元数据解释为系统会将一个名为 file1.xml 的项部署到测试 dll 目录下的测试 dll 旁边的文件夹中。 此配置仅适用于跨计算机方案。

<span id="_deploymentitem__file2.xml____datafiles___"></span><span id="_DEPLOYMENTITEM__FILE2.XML____DATAFILES___"></span>\[DeploymentItem ( "file2.xml"、"数据文件" ) \]  
将名为 file2.xml 的项部署到测试 dll 的 "已创建的数据文件" 子目录下。

<span id="_DeploymentItem__C___MyDataFiles__MyDataFiles2_____"></span><span id="_deploymentitem__c___mydatafiles__mydatafiles2_____"></span><span id="_DEPLOYMENTITEM__C___MYDATAFILES__MYDATAFILES2_____"></span>\[DeploymentItem ( "C： \\ \\ MyDataFiles \\ \\ MyDataFiles2 \\ \\ " ) \]  
部署在 C： \\ \\ MyDataFiles \\ \\ MyDataFiles2 \\ \\ 目录中找到的所有项和目录。 此配置不会在 \\ 部署目录下创建 MyDataFiles MyDataFiles2 目录。 MyDataFiles 中的所有文件和目录都将部署到测试 dll 目录。 若要复制整个 MyDataFiles \\ MyDataFiles2 目录结构，必须将 MyDataFiles \\ MyDataFiles2 指定为输出目录。

<span id="_deploymentitem___mydir__myfile.txt___"></span><span id="_DEPLOYMENTITEM___MYDIR__MYFILE.TXT___"></span>\[DeploymentItem ( "% myDir% \\myFile.txt" ) \]  
如果文件存在于% myDir% 解析到的目录中，则部署该文件 myFile.txt。 如果 TAEF 无法解析环境变量，则会引发错误。

## <a name="span-idmanaged_testsspanspan-idmanaged_testsspanspan-idmanaged_testsspanmanaged-tests"></a><span id="Managed_Tests"></span><span id="managed_tests"></span><span id="MANAGED_TESTS"></span>托管测试


**DeploymentItem** (亦如 DeploymentItemAttribute) 特性可应用于 TestMethod) 特性修饰 (修饰的测试方法 \[ ， (特性) \] \[ \] 或测试程序集进行修饰。 但是，由于 VSTS 不支持程序集级别的此属性，若要在程序集级别上应用此属性，必须将此属性应用于程序集安装 (通过 AssemblyInitialize 属性修饰) ：

```cpp
[AssemblyInitialize]
[DeploymentItem("file1.xml")]
[DeploymentItem("file2.xml")]
[DeploymentItem("file3.xml")]
public  static AssemblySetup(TestContext testContext)
{
    ...
}
```

## <a name="span-idnative_testsspanspan-idnative_testsspanspan-idnative_testsspannative-tests"></a><span id="Native_Tests"></span><span id="native_tests"></span><span id="NATIVE_TESTS"></span>本机测试


对于本机测试，属性格式类似于托管代码格式。 但是，由于本机属性只有单个值，因此在属性值中指定了项路径和可选目标，并使用 **" &gt; "** 字符分隔：

```cpp
BEGIN_TEST_CLASS(TestClassExample)
    TEST_CLASS_PROPERTY(L"DeploymentItem", L"C:\\Dependencies\\>Dependencies")
END_TEST_CLASS()
```

## <a name="span-idscript_testsspanspan-idscript_testsspanspan-idscript_testsspanscript-tests"></a><span id="Script_Tests"></span><span id="script_tests"></span><span id="SCRIPT_TESTS"></span>脚本测试


对于脚本测试，属性格式与本机测试相同：

```cpp
<method name="TestOne">
    <TestMethodProperty name="DeploymentItem" value="C:\\Dependencies\\>Dependencies"/>
</method>
```