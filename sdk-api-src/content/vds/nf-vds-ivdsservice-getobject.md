---
UID: NF:vds.IVdsService.GetObject
title: IVdsService::GetObject (vds.h)
description: Returns an object pointer for the identified object.
helpviewer_keywords: ["GetObject","GetObject method [VDS]","GetObject method [VDS]","IVdsService interface","IVdsService interface [VDS]","GetObject method","IVdsService.GetObject","IVdsService::GetObject","base.ivdsservice_getobject","vds/IVdsService::GetObject"]
old-location: base\ivdsservice_getobject.htm
tech.root: base
ms.assetid: 622a95a4-0e8c-4f65-a935-61cb48379065
ms.date: 12/05/2018
ms.keywords: GetObject, GetObject method [VDS], GetObject method [VDS],IVdsService interface, IVdsService interface [VDS],GetObject method, IVdsService.GetObject, IVdsService::GetObject, base.ivdsservice_getobject, vds/IVdsService::GetObject
req.header: vds.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows Vista [desktop apps only]
req.target-min-winversvr: Windows Server 2003 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Uuid.lib
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - IVdsService::GetObject
 - vds/IVdsService::GetObject
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - Uuid.lib
 - Uuid.dll
api_name:
 - IVdsService.GetObject
---

# IVdsService::GetObject


## -description

<p class="CCE_Message">[Beginning with Windows 8 and Windows Server 2012, the <a href="/windows/desktop/VDS/virtual-disk-service-portal">Virtual Disk Service</a> COM interface is superseded by the <a href="/previous-versions/windows/desktop/stormgmt/windows-storage-management-api-portal">Windows Storage Management API</a>.]

Returns an object pointer 
   for the identified object.

## -parameters

### -param ObjectId [in]

The GUID of the desired object.

### -param type [in]

A <a href="/windows/desktop/api/vdshwprv/ne-vdshwprv-vds_object_type">VDS_OBJECT_TYPE</a> enumeration value that specifies the object type. 
      <b>VDS_OT_UNKNOWN</b>, <b>VDS_OT_PROVIDER</b>, 
      <b>VDS_OT_ASYNC</b>, <b>VDS_OT_ENUM</b>, and <b>VDS_OT_OPEN_VDISK</b> are not supported.

### -param ppObjectUnk [out]

A pointer to a buffer that receives the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> pointer to the object. When the pointer is no longer needed, the caller should release it by calling the <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-release">IUnknown::Release</a> method.

## -returns

This method can return standard HRESULT values, such as E_INVALIDARG or E_OUTOFMEMORY, and <a href="/windows/desktop/VDS/virtual-disk-service-common-return-codes">VDS-specific return values</a>. It can also return converted <a href="/windows/desktop/Debug/system-error-codes">system error codes</a>  using the <a href="/windows/desktop/api/winerror/nf-winerror-hresult_from_win32">HRESULT_FROM_WIN32</a> macro. Errors can originate from VDS itself or from the underlying <a href="/windows/desktop/VDS/about-vds">VDS provider</a> that is being used. Possible return values include the following.

<table>
<tr>
<th>Return code/value</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>VDS_E_OBJECT_NOT_FOUND</b></dt>
<dt>0x80042405L</dt>
</dl>
</td>
<td width="60%">
An object with the specified identifier and type is not found.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>VDS_E_INITIALIZED_FAILED</b></dt>
<dt>0x80042401L</dt>
</dl>
</td>
<td width="60%">
VDS failed to initialize. If an application calls this method before the service finishes initializing, the 
        method is blocked until the initialization completes. If the initialization fails, this error is returned.

</td>
</tr>
</table>

## -remarks

VDS notifications return an object identifier instead of an object pointer. Callers  use this method to get a 
    pointer to the object referenced in the notification.

## -see-also

<a href="/windows/desktop/api/vds/nn-vds-ivdsservice">IVdsService</a>



<a href="/windows/desktop/api/vdshwprv/ne-vdshwprv-vds_object_type">VDS_OBJECT_TYPE</a>