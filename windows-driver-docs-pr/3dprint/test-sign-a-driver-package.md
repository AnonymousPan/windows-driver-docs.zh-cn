---
title: 对驱动程序包进行测试签名
description: 本部分介绍如何对驱动程序包进行测试签名。
ms.assetid: 3BC92099-A464-4C62-9EB7-DD6AA0D1FB03
ms.date: 05/15/2018
ms.localizationpriority: medium
ms.openlocfilehash: a0463933af63ae282e38d6923ce3c476aa18f4de
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89184903"
---
# <a name="test-sign-a-driver-package"></a>对驱动程序包进行测试签名


本部分介绍如何对驱动程序包进行测试签名。

## <a name="test-sign-a-driver-package"></a>对驱动程序包进行测试签名


使用以下步骤对驱动程序包进行测试，使用测试证书对驱动程序包进行签名：

1.  创建新的证书文件：

    ```console
    makecert -r -pe -ss TestCertStoreName -n "CN=WSD FabrikamV4 Driver Testing Cert" CertFileName.cer -sv CertFile.pvk
    ```

    系统将提示你输入密码。

2.  使用 pvk 文件创建 pfx 文件：

    ```console
    pvk2pfx.exe /pvk CertFile.pvk /spc CertFileName.cer /pfx CertPfx.pfx
    ```

    系统将提示你输入密码。

3.  将证书添加到要安装驱动程序的计算机上的根和 trustedpublisher 证书存储。

    这使得驱动程序能够在即插即用安装期间传递签名验证。 如果没有此步骤，驱动程序将不会通过此检查，并将无法自动安装打印机。

    ```console
    CertMgr /add CertFileName.cer /s /r localMachine root
    CertMgr /add CertFileName.cer /s /r localMachine trustedpublisher
    ```

4.  用在步骤2中创建的 pfx 文件来签署 "FabrikamPrintDriverV4 Package"。 其他项目不需要是驱动程序签名的，因为此步骤将创建包。

有关详细信息，请参阅 [如何对驱动程序包进行测试签名](../install/how-to-test-sign-a-driver-package.md)。