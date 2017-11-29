---
title: CorBindToRuntimeHost-Funktion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeHost
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeHost
helpviewer_keywords: CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eff6fdf0294e3b1cc9830e58bc8103a64102d5b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="3ebaa-102">CorBindToRuntimeHost-Funktion</span><span class="sxs-lookup"><span data-stu-id="3ebaa-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="3ebaa-103">Ermöglicht es Hosts, eine angegebene Version der Common Language Runtime (CLR) in einen Prozess zu laden.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="3ebaa-104">Diese Funktion ist in [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] veraltet.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ebaa-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ebaa-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ebaa-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="3ebaa-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="3ebaa-107">[in] Eine Zeichenfolge, welche die Version der zu ladenden CLR beschreibt.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="3ebaa-108">Eine Versionsnummer in .NET Framework besteht aus vier Teilen, die durch Punkte getrennt: *"Hauptversion.Nebenversion.Build.Revision" vorliegen*.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="3ebaa-109">Die als `pwszVersion` übergebene Zeichenfolge muss mit dem Buchstaben "v" beginnen, auf den die ersten drei Teile der Versionsnummer folgen (z. B. "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="3ebaa-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="3ebaa-110">Einige Versionen der CLR werden mit einer Richtlinienanweisung installiert, welche die Kompatibilität mit früheren Versionen der CLR angibt.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="3ebaa-111">In der Standardeinstellung wertet das Startmodul `pwszVersion` anhand von Richtlinienanweisungen aus und lädt die neueste Version der Common Language Runtime, die mit der angeforderten Version kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="3ebaa-112">Ein Host kann erzwingen, dass das Startmodul die Richtlinienauswertung überspringt und genau die in `pwszVersion` angegebene Version lädt, indem für `startupFlags` der Wert STARTUP_LOADER_SAFEMODE übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="3ebaa-113">Wenn `pwszVersion``null,` ist, wird keine Version der CLR geladen.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="3ebaa-114">Stattdessen wird "CLR_E_SHIM_RUNTIMELOAD" zurückgegeben, womit angegeben wird, dass die Laufzeit nicht geladen werden konnte.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="3ebaa-115">[in] Eine Zeichenfolge, die angibt, ob der Serverbuild oder der Arbeitsstationsbuild der CLR geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="3ebaa-116">Gültige Werte sind `svr` und `wks`.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="3ebaa-117">Der Serverbuild wurde so optimiert, dass mehrere Prozessoren zur Ausführung der Garbage Collection genutzt werden können. Der Arbeitsstationsbuild wurde für die Ausführung von Clientanwendungen auf einem Computer mit einem einzelnen Prozessor optimiert.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="3ebaa-118">Wenn `pwszBuildFlavor` auf festgelegt ist null, wird das Arbeitsstationsbuild geladen.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="3ebaa-119">Bei Ausführung auf einem Computer mit einem Prozessor wird immer das Arbeitsstationsbuild geladen, selbst wenn `pwszBuildFlavor` festgelegt ist, um `svr`.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="3ebaa-120">Jedoch wenn `pwszBuildFlavor` auf festgelegt ist `svr` und gleichzeitige Garbagecollection angegeben wird (finden Sie in der Beschreibung der `startupFlags` Parameter), das Serverbuild geladen wird.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ebaa-121">Die gleichzeitige Garbage Collection wird nicht in Anwendungen unterstützt, die den WOW64 x86-Emulator auf 64-Bit-Systemen mit einer Implementierung der Intel Itanium-Architektur (früher als IA-64 bezeichnet) ausführen.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="3ebaa-122">Weitere Informationen zur Verwendung von WOW64 auf 64-Bit-Windows-Systemen, finden Sie unter [Ausführen von 32-Bit-Anwendungen](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ebaa-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="3ebaa-123">[in] Der Name einer Hostkonfigurationsdatei, welche die zu ladende Version der CLR angibt.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="3ebaa-124">Wenn der Dateiname keinen vollqualifizierten Pfad enthält, wird angenommen, dass sich die Datei in demselben Verzeichnis befindet wie die ausführbare Datei, die den Aufruf ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="3ebaa-125">[in] Für zukünftige Erweiterungen reserviert.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="3ebaa-126">[in] Ein Satz von Flags, welche die gleichzeitige Garbage Collection, domänenneutralen Code und das Verhalten des `pwszVersion`-Parameters steuern.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="3ebaa-127">Wenn kein Flag festgelegt ist, gilt als Standardwert die Einzeldomäne.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="3ebaa-128">Eine Liste der unterstützten Werte finden Sie unter der [STARTUP_FLAGS-Enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="3ebaa-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3ebaa-129">[in] Die `CLSID` der Co-Klasse, die entweder implementiert die [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) oder [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3ebaa-130">Unterstützte Werte sind "CLSID_CorRuntimeHost" oder "CLSID_CLRRuntimeHost".</span><span class="sxs-lookup"><span data-stu-id="3ebaa-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3ebaa-131">[in] Die `IID` der angeforderten Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="3ebaa-132">Unterstützte Werte sind "IID_ICorRuntimeHost" oder "IID_ICLRRuntimeHost".</span><span class="sxs-lookup"><span data-stu-id="3ebaa-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3ebaa-133">[out] Ein Schnittstellenzeiger auf die Version der Common Language Runtime, die geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="3ebaa-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ebaa-134">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="3ebaa-134">Requirements</span></span>  
 <span data-ttu-id="3ebaa-135">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ebaa-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ebaa-136">**Header:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="3ebaa-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="3ebaa-137">**Bibliothek:** "Mscoree.dll"</span><span class="sxs-lookup"><span data-stu-id="3ebaa-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ebaa-138">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ebaa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ebaa-139">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3ebaa-139">See Also</span></span>  
 [<span data-ttu-id="3ebaa-140">CorBindToCurrentRuntime-Funktion</span><span class="sxs-lookup"><span data-stu-id="3ebaa-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="3ebaa-141">CorBindToRuntime-Funktion</span><span class="sxs-lookup"><span data-stu-id="3ebaa-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="3ebaa-142">CorBindToRuntimeByCfg-Funktion</span><span class="sxs-lookup"><span data-stu-id="3ebaa-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="3ebaa-143">CorBindToRuntimeEx-Funktion</span><span class="sxs-lookup"><span data-stu-id="3ebaa-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="3ebaa-144">ICorRuntimeHost-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="3ebaa-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="3ebaa-145">Veraltete CLR-Hostingfunktionen</span><span class="sxs-lookup"><span data-stu-id="3ebaa-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)