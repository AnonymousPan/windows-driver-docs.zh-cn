---
title: 使用 Direct3D 版本 10 句柄
description: 使用 Direct3D 版本 10 句柄
ms.assetid: 98cde374-0267-44bc-b285-acf4a6d17ff4
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 27eed96e950ed91dbe14487659ace627a4a9ca9b
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89067124"
---
# <a name="using-direct3d-version-10-handles"></a>使用 Direct3D 版本 10 句柄


Direct3D 版本10句柄是强类型的，以防止 misusage 并使编译器检测到不匹配的句柄类型。 Direct3D 版本10句柄的生命周期从对 create type 函数的调用开始 (例如， [**CreateGeometryShader**](/windows-hardware/drivers/ddi/d3d10umddi/nc-d3d10umddi-pfnd3d10ddi_creategeometryshader)) ，并通过调用销毁类型 (函数（如 [**DestroyShader**](/windows-hardware/drivers/ddi/d3d10umddi/nc-d3d10umddi-pfnd3d10ddi_destroyshader)) ）结束。 Direct3D 版本10存在三种类型的句柄。 前两种类型的句柄是驱动程序句柄，Direct3D 运行时使用该句柄与驱动程序通信，并使用运行时句柄来与运行时进行通信。 图柄的第三个类别是内核句柄。 以下部分介绍了 Direct3D 版本10的句柄：

[Direct3D 版本 10 运行时和驱动程序句柄](direct3d-version-10-runtime-and-driver-handles.md)

[Direct3D 版本 10 内核句柄](direct3d-version-10-kernel-handles.md)

 

