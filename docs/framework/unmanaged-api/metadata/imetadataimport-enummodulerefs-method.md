---
title: IMetaDataImport::EnumModuleRefs-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumModuleRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebba448881b934220f0eb46c392ab0909ae37f68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="a542b-102">IMetaDataImport::EnumModuleRefs-Methode</span><span class="sxs-lookup"><span data-stu-id="a542b-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="a542b-103">Zählt ModuleRef-Token auf, die importierte Module darstellen.</span><span class="sxs-lookup"><span data-stu-id="a542b-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a542b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a542b-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a542b-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="a542b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a542b-106">[in, out] Ein Zeiger auf den Enumerator.</span><span class="sxs-lookup"><span data-stu-id="a542b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a542b-107">Dies muss für den ersten Aufruf dieser Methode NULL sein.</span><span class="sxs-lookup"><span data-stu-id="a542b-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="a542b-108">[out] Das Array zum Speichern der ModuleRef-Token verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a542b-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a542b-109">[in] Die maximale Größe des `rModuleRefs`-Arrays.</span><span class="sxs-lookup"><span data-stu-id="a542b-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="a542b-110">[out] Die Anzahl der zurückgegebenen ModuleRef-Token `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="a542b-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a542b-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="a542b-111">Return Value</span></span>  
  
|<span data-ttu-id="a542b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a542b-112">HRESULT</span></span>|<span data-ttu-id="a542b-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a542b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a542b-114">`EnumModuleRefs`wurde erfolgreich zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a542b-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a542b-115">Es sind keine Token aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="a542b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a542b-116">In diesem Fall `pcModuleRefs` 0 (null).</span><span class="sxs-lookup"><span data-stu-id="a542b-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a542b-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a542b-117">Requirements</span></span>  
 <span data-ttu-id="a542b-118">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a542b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a542b-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a542b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a542b-120">**Bibliothek:** als Ressource in MsCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="a542b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a542b-121">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a542b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a542b-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a542b-122">See Also</span></span>  
 [<span data-ttu-id="a542b-123">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="a542b-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a542b-124">IMetaDataImport2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="a542b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)