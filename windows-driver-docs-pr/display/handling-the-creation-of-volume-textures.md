---
title: 处理体积纹理的创建
description: 处理体积纹理的创建
ms.assetid: d5f521df-cd52-4c7e-9ad2-5df343c96e8c
keywords:
- 纹理 WDK DirectX 8。0
- DirectX 8.0 发行说明 WDK Windows 2000 显示，音量纹理
- 卷纹理 WDK DirectX 8。0
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0ded6c78ad1932d5c60946f0e4b9bda96ecc80d2
ms.sourcegitcommit: f8619f20a0903dd64f8641a5266ecad6df5f1d57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91423774"
---
# <a name="handling-the-creation-of-volume-textures"></a>处理体积纹理的创建


## <span id="ddk_handling_the_creation_of_volume_textures_gg"></span><span id="DDK_HANDLING_THE_CREATION_OF_VOLUME_TEXTURES_GG"></span>


DirectX 8.0 引入了新的 surface DDSCAPS2 \_ 卷。 此标志在表面的[**DD \_ surface surface \_ **](/windows/win32/api/ddrawint/ns-ddrawint-dd_surface_more)结构的**ddsCapsEx. dwCaps2**字段中设置。 在 [*DdCreateSurface*](/previous-versions/windows/hardware/drivers/ff549263(v=vs.85)) 和 [**D3dCreateSurfaceEx**](/windows/win32/api/ddrawint/nc-ddrawint-pdd_createsurfaceex) 回调中，音量纹理的深度可在图块的 DD 表面的 " **dwCaps4** " 字段中的 "") ** (字段** 中找到 \_ \_ 。 驱动程序应返回 "切片间距" (即，要添加的字节数从卷的一个二维扇区移到表面全局结构的 **dwBlockSizeY** 字段中的下一个卷纹理) 。

 

