---
title: IHostSyncManager::CreateRWLockReaderEvent-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockReaderEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a783f4511e27b5d230a90444e5a91b34327543cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="47a48-102">IHostSyncManager::CreateRWLockReaderEvent-Methode</span><span class="sxs-lookup"><span data-stu-id="47a48-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="47a48-103">Erstellt ein Ereignis für manuelles Zurücksetzen-Objekt für die Implementierung der eine Sperre des Lesers.</span><span class="sxs-lookup"><span data-stu-id="47a48-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a48-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="47a48-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47a48-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="47a48-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="47a48-106">[in] `true`, wenn `ppEvent` signalisiert wurde, andernfalls sollte `false`.</span><span class="sxs-lookup"><span data-stu-id="47a48-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="47a48-107">[in] Ein Cookie, die Sperre des Lesers zugeordnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="47a48-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="47a48-108">[out] Ein Zeiger auf die Adresse des ein [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) -Instanz oder null, wenn das Ereignisobjekt nicht erstellt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="47a48-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47a48-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="47a48-109">Return Value</span></span>  
  
|<span data-ttu-id="47a48-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47a48-110">HRESULT</span></span>|<span data-ttu-id="47a48-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="47a48-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47a48-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="47a48-112">S_OK</span></span>|<span data-ttu-id="47a48-113">`CreateRWLockReaderEvent`wurde erfolgreich zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="47a48-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="47a48-114">HOST_E_CLRNOTAVAILABLE ZURÜCK</span><span class="sxs-lookup"><span data-stu-id="47a48-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="47a48-115">Die common Language Runtime (CLR) wurde nicht in einen Prozess geladen, oder die CLR wird in einem Zustand, in dem er nicht verwalteten Code ausführen oder den Aufruf erfolgreich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="47a48-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="47a48-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="47a48-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="47a48-117">Der Aufruf ist ein Timeout aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="47a48-117">The call timed out.</span></span>|  
|<span data-ttu-id="47a48-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="47a48-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="47a48-119">Der Aufrufer ist nicht Besitzer der Sperre.</span><span class="sxs-lookup"><span data-stu-id="47a48-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="47a48-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="47a48-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="47a48-121">Ein Ereignis wurde abgebrochen, während ein blockierten Thread oder eine Fiber darauf gewartet.</span><span class="sxs-lookup"><span data-stu-id="47a48-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="47a48-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47a48-122">E_FAIL</span></span>|<span data-ttu-id="47a48-123">Ein Unbekannter Schwerwiegender Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="47a48-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="47a48-124">Wenn eine Methode E_FAIL zurückgibt, ist die CLR nicht mehr verwendbar innerhalb des Prozesses.</span><span class="sxs-lookup"><span data-stu-id="47a48-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="47a48-125">Nachfolgende Aufrufe zum Hosten der Methoden HOST_E_CLRNOTAVAILABLE zurück.</span><span class="sxs-lookup"><span data-stu-id="47a48-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="47a48-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="47a48-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="47a48-127">Es war nicht genügend Arbeitsspeicher zum Erstellen des angeforderten Ereignisses-Objekts verfügbar.</span><span class="sxs-lookup"><span data-stu-id="47a48-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47a48-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="47a48-128">Remarks</span></span>  
 <span data-ttu-id="47a48-129">Die CLR ruft `CreateRWLockReaderEvent` zum Abrufen eines Verweises auf eine `IHostManualEvent` Instanz, mit der in seiner Implementierung von eine Sperre des Lesers.</span><span class="sxs-lookup"><span data-stu-id="47a48-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="47a48-130">Der Host kann das Cookie verwenden, um zu bestimmen, welche Aufgaben auf die Sperre des Lesers durch Abfragen Warten der [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="47a48-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a48-131">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="47a48-131">Requirements</span></span>  
 <span data-ttu-id="47a48-132">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a48-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a48-133">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47a48-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47a48-134">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="47a48-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47a48-135">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a48-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a48-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="47a48-136">See Also</span></span>  
 [<span data-ttu-id="47a48-137">ICLRSyncManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="47a48-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="47a48-138">IHostAutoEvent-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="47a48-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="47a48-139">IHostManualEvent-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="47a48-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="47a48-140">IHostSyncManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="47a48-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)