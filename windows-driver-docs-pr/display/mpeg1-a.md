---
title: MPEG1_A
description: MPEG1_A
ms.assetid: 2c4d79b7-3331-49f9-a561-6e5b609543df
keywords:
- MPEG1_A 受限配置文件 WDK DirectX VA
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 064eff868162b011c2a63ea66c0047f81b336212
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89063522"
---
# <a name="mpeg1_a"></a>MPEG1 \_


## <span id="ddk_mpeg1_a_gg"></span><span id="DDK_MPEG1_A_GG"></span>


\_限制配置文件的 MPEG1 包含支持 mpeg-2 视频所需的一组功能。 提供硬件视频加速功能的视频加速器驱动程序需要此配置文件的支持。 这组功能由以下限制集定义：

### <a name="span-idrestrictions_on_dxva_connectmodespanspan-idrestrictions_on_dxva_connectmodespanspan-idrestrictions_on_dxva_connectmodespanrestrictions-on-dxva_connectmode"></a><span id="Restrictions_on_DXVA_ConnectMode"></span><span id="restrictions_on_dxva_connectmode"></span><span id="RESTRICTIONS_ON_DXVA_CONNECTMODE"></span>DXVA ConnectMode 的限制 \_

当[**DXVA \_ ConfigPictureDecode**](/windows-hardware/drivers/ddi/dxva/ns-dxva-_dxva_configpicturedecode)结构的**dwFunction**成员中定义的*bDXVA \_ Func*变量等于1时，适用于[**DXVA \_ ConnectMode**](/windows-hardware/drivers/ddi/dxva/ns-dxva-_dxva_connectmode)结构的以下限制。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">结构成员</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>wRestrictedMode</strong></p></td>
<td align="left"><p>DXVA_RESTRICTED_MODE_MPEG1_A</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idrestrictions_on_dxva_pictureparametersspanspan-idrestrictions_on_dxva_pictureparametersspanspan-idrestrictions_on_dxva_pictureparametersspanrestrictions-on-dxva_pictureparameters"></a><span id="Restrictions_on_DXVA_PictureParameters"></span><span id="restrictions_on_dxva_pictureparameters"></span><span id="RESTRICTIONS_ON_DXVA_PICTUREPARAMETERS"></span>DXVA PictureParameters 的限制 \_

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">结构成员</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><em>BPP</em>变量 (通过将1添加到<strong>bBPPminus1</strong>来定义) </p></td>
<td align="left"><p>等于8</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bSecondField</strong></p></td>
<td align="left"><p>等于零</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>MacroblockWidthMinus1</strong></p></td>
<td align="left"><p>15</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>MacroblockHeightMinus1</strong></p></td>
<td align="left"><p>15</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>bBlockWidthMinus1</strong></p></td>
<td align="left"><p>7</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bBlockHeightMinus1</strong></p></td>
<td align="left"><p>7</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>bChromaFormat</strong> (4:2:0) </p></td>
<td align="left"><p>1</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bPicStructure</strong></p></td>
<td align="left"><p>3 (帧结构) </p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>bRcontrol</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bBidirectionalAveragingMode</strong></p></td>
<td align="left"><p>零 (MPEG-2 双向平均) </p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>bMVprecisionAndChromaRelation</strong></p></td>
<td align="left"><p>零 (MPEG-2 半采样动作) </p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bPicExtrapolation</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>bPicDeblocked</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bPic4MVallowed</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>bPicOBMC</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bMV_RPS</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>SpecificIDCT</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>bPicScanFixed</strong></p></td>
<td align="left"><p>零</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idrestrictions_on_dxva_mbctrl_i_hostresiddiff_1__dxva_mbctrl_i_offhostidct_1__dxva_mbctrl_p_hostresiddiff_1__and_dxva_mbctrl_p_offhostidct_1spanspan-idrestrictions_on_dxva_mbctrl_i_hostresiddiff_1__dxva_mbctrl_i_offhostidct_1__dxva_mbctrl_p_hostresiddiff_1__and_dxva_mbctrl_p_offhostidct_1spanspan-idrestrictions_on_dxva_mbctrl_i_hostresiddiff_1__dxva_mbctrl_i_offhostidct_1__dxva_mbctrl_p_hostresiddiff_1__and_dxva_mbctrl_p_offhostidct_1spanrestrictions-on-dxva_mbctrl_i_hostresiddiff_1-dxva_mbctrl_i_offhostidct_1-dxva_mbctrl_p_hostresiddiff_1-and-dxva_mbctrl_p_offhostidct_1"></a><span id="Restrictions_on_DXVA_MBctrl_I_HostResidDiff_1__DXVA_MBctrl_I_OffHostIDCT_1__DXVA_MBctrl_P_HostResidDiff_1__and_DXVA_MBctrl_P_OffHostIDCT_1"></span><span id="restrictions_on_dxva_mbctrl_i_hostresiddiff_1__dxva_mbctrl_i_offhostidct_1__dxva_mbctrl_p_hostresiddiff_1__and_dxva_mbctrl_p_offhostidct_1"></span><span id="RESTRICTIONS_ON_DXVA_MBCTRL_I_HOSTRESIDDIFF_1__DXVA_MBCTRL_I_OFFHOSTIDCT_1__DXVA_MBCTRL_P_HOSTRESIDDIFF_1__AND_DXVA_MBCTRL_P_OFFHOSTIDCT_1"></span>DXVA \_ MBctrl \_ i \_ HOSTRESIDDIFF \_ 1、DXVA \_ MBCTRL \_ i \_ OffHostIDCT \_ 1、DXVA \_ MBctrl \_ p \_ HostResidDiff \_ 1 和 DXVA \_ MBctrl \_ p \_ OffHostIDCT \_ 1 的限制

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">wMBtype 位</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><em>MotionType</em></p></td>
<td align="left"><p>2 (帧运动) </p></td>
</tr>
<tr class="even">
<td align="left"><p><em>MBscanMethod</em></p></td>
<td align="left"><p>如果 <strong>bConfigHostInverseScan</strong> 等于零，则为零 (之字形) </p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>FieldResidual</em></p></td>
<td align="left"><p>零 (帧残留) </p></td>
</tr>
<tr class="even">
<td align="left"><p><em>H261LoopFilter</em></p></td>
<td align="left"><p>零 (没有261循环筛选器) </p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idrestrictions_on_bitstream_buffersspanspan-idrestrictions_on_bitstream_buffersspanspan-idrestrictions_on_bitstream_buffersspanrestrictions-on-bitstream-buffers"></a><span id="Restrictions_on_Bitstream_Buffers"></span><span id="restrictions_on_bitstream_buffers"></span><span id="RESTRICTIONS_ON_BITSTREAM_BUFFERS"></span>位流缓冲区的限制

任何位流缓冲区的内容必须包含 MPEG-2 主要配置文件视频格式的数据。

 

