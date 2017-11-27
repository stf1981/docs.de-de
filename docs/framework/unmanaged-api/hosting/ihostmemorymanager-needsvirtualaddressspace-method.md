---
title: IHostMemoryManager::NeedsVirtualAddressSpace-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.NeedsVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62ceb9e5b4d5843b8e2adad344b3ffb662ab3aff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="9cf3e-102">IHostMemoryManager::NeedsVirtualAddressSpace-Methode</span><span class="sxs-lookup"><span data-stu-id="9cf3e-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="9cf3e-103">Benachrichtigt den Host, dass die common Language Runtime (CLR) versucht, den angegebenen Arbeitsspeicher verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9cf3e-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf3e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9cf3e-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cf3e-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="9cf3e-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="9cf3e-106">[in] Die Startadresse des Arbeitsspeichers.</span><span class="sxs-lookup"><span data-stu-id="9cf3e-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="9cf3e-107">[in] Die Größe in Bytes, des Arbeitsspeichers.</span><span class="sxs-lookup"><span data-stu-id="9cf3e-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cf3e-108">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9cf3e-108">Remarks</span></span>  
 <span data-ttu-id="9cf3e-109">Die `NeedsVirtualAddressSpace` Methode ist eine Rückrufmethode und muss vom Writer der Hostinganwendung implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="9cf3e-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="9cf3e-110">Sie wird von der CLR aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="9cf3e-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="9cf3e-111">Wenn der Host nicht die CLR auf den angegebenen Speicher verwenden möchten, wird möglicherweise ein E_OUTOFMEMORY HRESULT zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="9cf3e-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cf3e-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9cf3e-112">Requirements</span></span>  
 <span data-ttu-id="9cf3e-113">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cf3e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cf3e-114">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9cf3e-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cf3e-115">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="9cf3e-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cf3e-116">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cf3e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf3e-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9cf3e-117">See Also</span></span>  
 [<span data-ttu-id="9cf3e-118">IHostMemoryManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="9cf3e-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)