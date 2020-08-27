---
description: 打开资源并检索 IStream 对象
title: 打开资源并检索 IStream 对象
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 20fa28e82a9e4636ca359b4b232aaadc156a292c
ms.sourcegitcommit: 15caaf6d943135efcaf9975927ff3933957acd5d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "88968504"
---
# <a name="opening-a-resource-and-retrieving-an-istream-object"></a>打开资源并检索 IStream 对象


当应用程序必须从设备读取资源数据或将其写入到设备时，将首先调用 **IPortableDeviceResources：： system.resources.resourcemanager.getstream** 方法。 此方法检索一个 **IStream** 接口，应用程序使用该接口进行相应的读取和写入操作。  (，则 WPD API 将返回 **IStream** 接口，而不是驱动程序。 ) 

调用 **IPortableDeviceResources：： system.resources.resourcemanager.getstream** 方法将触发对示例驱动程序中的 **WpdObjectResources：： OnOpenResource** 命令处理程序的调用。 此处理程序创建用于读取操作的驱动程序所使用的资源上下文。 在此特定情况下，资源上下文包括以下项：

-   包含资源的对象的对象标识符
-   资源 PROPERTYKEY
-   用于读取操作 (传输的字节数) 
-   整个资源的大小（以字节为单位）

```ManagedCPlusPlus
HRESULT WpdObjectResources::OnOpenResource(
    IPortableDeviceValues*  pParams,
    IPortableDeviceValues*  pResults)
{
    HRESULT     hr              = S_OK;
    LPWSTR      wszObjectID     = NULL;
    PROPERTYKEY Key             = WPD_PROPERTY_NULL;
    DWORD       dwMode          = STGM_READ;
    CAtlStringW strStrObjectID;
    CAtlStringW strResourceContext;
    ContextMap* pContextMap     = NULL;

    // Get the Object identifier of the object which contains the specified resource
    hr = pParams->GetStringValue(WPD_PROPERTY_OBJECT_RESOURCES_OBJECT_ID, &wszObjectID);
    if (hr != S_OK)
    {
        hr = E_INVALIDARG;
        CHECK_HR(hr, "Missing value for WPD_PROPERTY_OBJECT_RESOURCES_OBJECT_ID");
    }

    // Get the resource key
    if (hr == S_OK)
    {
        hr = pParams->GetKeyValue(WPD_PROPERTY_OBJECT_RESOURCES_RESOURCE_KEYS, &Key);
        CHECK_HR(hr, "Missing value for WPD_PROPERTY_OBJECT_RESOURCES_RESOURCE_KEYS");
    }

    // Get the access mode
    if (hr == S_OK)
    {
        hr = pParams->GetUnsignedIntegerValue(WPD_PROPERTY_OBJECT_RESOURCES_ACCESS_MODE, &dwMode);
        CHECK_HR(hr, "Missing value for WPD_PROPERTY_OBJECT_RESOURCES_ACCESS_MODE");
    }

    // Validate whether the params given to us are correct.  In this case, we need to check that the object
    // supports the resource requested, and can be opened in the requested access mode.
    if (hr == S_OK)
    {
        // In this sample, we only have one object (README_FILE_OBJECT_ID) which supports a
        // resource (WPD_RESOURCE_DEFAULT) for reading only.
        // So if any other Object ID or any other resource is specified, it must be invalid.
        strStrObjectID = wszObjectID;
        if(strStrObjectID.CompareNoCase(README_FILE_OBJECT_ID) != 0)
        {
            hr = E_INVALIDARG;
            CHECK_HR(hr, "Object [%ws] does not support resources", wszObjectID);
        }
        if (hr == S_OK)
        {
            if (!IsEqualPropertyKey(Key, WPD_RESOURCE_DEFAULT))
            {
                hr = E_INVALIDARG;
                CHECK_HR(hr, "Only WPD_RESOURCE_DEFAULT is supported in this sample driver");
            }
        }
        if (hr == S_OK)
        {
            if ((dwMode & STGM_WRITE) != 0)
            {
                hr = E_ACCESSDENIED;
                CHECK_HR(hr, "This resource is not available for write access");
            }
        }
    }

    // Get the context map which the driver stored in pParams for convenience
    if (hr == S_OK)
    {
        hr = pParams->GetIUnknownValue(PRIVATE_SAMPLE_DRIVER_CLIENT_CONTEXT_MAP, (IUnknown**)&pContextMap);
        CHECK_HR(hr, "Failed to get PRIVATE_SAMPLE_DRIVER_CLIENT_CONTEXT_MAP");
    }

    // Create a new resource operation context, initialize it, and add it to the client context map.
    if (hr == S_OK)
    {
        WpdObjectResourceContext* pResourceContext = new WpdObjectResourceContext();
        if (pResourceContext != NULL)
        {
            // Initialize the resource context with ...
            pResourceContext->m_strObjectID      = wszObjectID;
            pResourceContext->m_Resource         = Key;
            pResourceContext->m_BytesTransferred = 0;
            pResourceContext->m_BytesTotal       = GetObjectSize(wszObjectID);

            // Add the resource context to the context map
            pContextMap->Add(pResourceContext, strResourceContext);
        }
        else
        {
            hr = E_OUTOFMEMORY;
            CHECK_HR(hr, "Failed to allocate resource context");
        }
    }

    if (hr == S_OK)
    {
        hr = pResults->SetStringValue(WPD_PROPERTY_OBJECT_RESOURCES_CONTEXT, strResourceContext);
        CHECK_HR(hr, "Failed to set WPD_PROPERTY_OBJECT_RESOURCES_CONTEXT");
    }

    // Set the optimal buffer size
    if (hr == S_OK)
    {
        hr = pResults->SetUnsignedIntegerValue(WPD_PROPERTY_OBJECT_RESOURCES_OPTIMAL_TRANSFER_BUFFER_SIZE, FILE_OPTIMAL_READ_BUFFER_SIZE_VALUE);
        CHECK_HR(hr, "Failed to set WPD_PROPERTY_OBJECT_RESOURCES_OPTIMAL_TRANSFER_BUFFER_SIZE value");
    }

    // Free the memory.  CoTaskMemFree ignores NULLs so no need to check.
    CoTaskMemFree(wszObjectID);

    SAFE_RELEASE(pContextMap);

    return hr;
}
```

 

 




