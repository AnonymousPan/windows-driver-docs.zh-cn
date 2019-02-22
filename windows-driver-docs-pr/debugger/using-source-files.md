---
title: 使用源代码文件
description: 使用源代码文件
ms.assetid: c6dfcb37-140f-43d8-aa15-14f0317b5e19
keywords:
- 调试器引擎 API、 源
ms.date: 05/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2b59dcc530b3d4c9708c7539b049b654e2a7aeaf
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56542509"
---
# <a name="using-source-files"></a>使用源代码文件


[调试器引擎](introduction.md#debugger-engine)维护*源路径*，这是目录和包含与最新的目标源代码文件的源服务器的列表。 调试器引擎可以搜索这些目录和源文件的源服务器。 符号文件的帮助下，调试器引擎可匹配目标的内存中的位置与源文件中的行。

有关与调试器配合使用的源文件的概述，请参阅[在源模式中进行调试](debugging-in-source-mode.md)。 源路径的概述，请参阅[源路径](source-path.md)。 使用来自调试器引擎的源服务器的概述，请参阅[使用源服务器](using-a-source-server.md)。

### <a name="span-idsourcepathspanspan-idsourcepathspansource-path"></a><span id="source_path"></span><span id="SOURCE_PATH"></span>源路径

若要添加到源路径的目录或源服务器，请使用方法[ **AppendSourcePath**](https://msdn.microsoft.com/library/windows/hardware/ff538102)。 返回整个源路径[ **GetSourcePath** ](https://msdn.microsoft.com/library/windows/hardware/ff548358) ，可以使用更改[ **SetSourcePath**](https://msdn.microsoft.com/library/windows/hardware/ff556781)。 单个目录或源服务器可以检索从源路径中使用[ **GetSourcePathElement**](https://msdn.microsoft.com/library/windows/hardware/ff548367)。

若要查找源路径的相对路径的源文件，请使用[ **FindSourceFile** ](https://msdn.microsoft.com/library/windows/hardware/ff545423)或者，有关更多高级选项，使用源服务器时，使用[ **FindSourceFileAndToken**](https://msdn.microsoft.com/library/windows/hardware/ff545430). **FindSourceFileAndToken**还可以使用连同[ **GetSourceFileInformation** ](https://msdn.microsoft.com/library/windows/hardware/ff548321)检索到的源服务器上的文件相关的变量。

### <a name="span-idmatchingsourcefilestocodeinmemoryspanspan-idmatchingsourcefilestocodeinmemoryspanmatching-source-files-to-code-in-memory"></a><span id="matching_source_files_to_code_in_memory"></span><span id="MATCHING_SOURCE_FILES_TO_CODE_IN_MEMORY"></span>匹配的源代码文件，以在内存中的代码

调试器引擎提供了三个方法，用于查找分别对应于源文件中的行的内存位置。 若要将源代码的单个行映射到的内存位置，请使用[ **GetOffsetByLine**](https://msdn.microsoft.com/library/windows/hardware/ff548022)。 若要搜索的多个源行或附近的源行的内存位置，请使用[ **GetSourceEntriesByLine**](https://msdn.microsoft.com/library/windows/hardware/ff548305)。 [ **GetSourceFileLineOffsets** ](https://msdn.microsoft.com/library/windows/hardware/ff548339)方法将返回源文件中的每个行的内存位置。

若要执行相反的操作，并找到与目标的内存中的位置相匹配的源文件的行，使用[ **GetLineByOffset**](https://msdn.microsoft.com/library/windows/hardware/ff546995)。

**请注意**  内存位置和源代码文件中的行之间的关系不是一定是一一对应关系。 就可以为源代码，以与多个内存位置相对应的单个行和在单一内存位置，以分别对应于多个行的源代码。

 

 

 




