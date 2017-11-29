---
title: IGCHostControl::RequestVirtualMemLimit-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHostControl.RequestVirtualMemLimit
api_location: mscoree.dll
api_type: COM
f1_keywords: RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4892cf5dc3a3663f1bccc95d1975bfe96277faa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="26c42-102">IGCHostControl::RequestVirtualMemLimit-Methode</span><span class="sxs-lookup"><span data-stu-id="26c42-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="26c42-103">Fordert den Host zum Ändern der Grenzen des virtuellen Arbeitsspeichers.</span><span class="sxs-lookup"><span data-stu-id="26c42-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c42-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="26c42-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26c42-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="26c42-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="26c42-106">[in] Die angeforderte Größe des Arbeitsspeichers zugeordnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="26c42-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="26c42-107">[in, out] Ein Zeiger auf die tatsächliche Größe des belegten Arbeitsspeichers.</span><span class="sxs-lookup"><span data-stu-id="26c42-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c42-108">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="26c42-108">Requirements</span></span>  
 <span data-ttu-id="26c42-109">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26c42-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c42-110">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26c42-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26c42-111">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="26c42-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26c42-112">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c42-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c42-113">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="26c42-113">See Also</span></span>  
 [<span data-ttu-id="26c42-114">IGCHostControl-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="26c42-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)