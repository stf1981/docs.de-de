---
title: ICorProfilerInfo2::GetClassLayout-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 988e9daf54d9b4edd623e2488b68dff007e4495b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="ca539-102">ICorProfilerInfo2::GetClassLayout-Methode</span><span class="sxs-lookup"><span data-stu-id="ca539-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="ca539-103">Ruft aus dem Arbeitsspeicher Informationen über das Layout der Felder ab, die durch die angegebene Klasse definiert sind .</span><span class="sxs-lookup"><span data-stu-id="ca539-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="ca539-104">Das heißt, diese Methode ruft die Offsets der Felder der Klasse ab.</span><span class="sxs-lookup"><span data-stu-id="ca539-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca539-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca539-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca539-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="ca539-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="ca539-107">[in] Die ID der Klasse, für das Layout abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ca539-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="ca539-108">[in, out] Ein Array von [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) Strukturen, von denen jede die Tokens und Offsets der Klassenfelder enthält.</span><span class="sxs-lookup"><span data-stu-id="ca539-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="ca539-109">[in] Die Größe des `rFieldOffset`-Arrays.</span><span class="sxs-lookup"><span data-stu-id="ca539-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="ca539-110">[out] Ein Zeiger auf die Gesamtzahl der verfügbaren Elemente.</span><span class="sxs-lookup"><span data-stu-id="ca539-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="ca539-111">Wenn `cFieldOffset` gleich 0 ist, gibt dieser Wert gibt die Anzahl von benötigten Elementen an.</span><span class="sxs-lookup"><span data-stu-id="ca539-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="ca539-112">[out] Ein Zeiger auf einen Speicherort, der die Größe der Klasse in Bytes enthält.</span><span class="sxs-lookup"><span data-stu-id="ca539-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca539-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ca539-113">Remarks</span></span>  
 <span data-ttu-id="ca539-114">Die `GetClassLayout`-Methode gibt nur die von der Klasse selbst definierten Felder zurück.</span><span class="sxs-lookup"><span data-stu-id="ca539-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="ca539-115">Wenn die übergeordnete Klasse der Klasse ebenfalls Felder definiert hat, muss der Profiler die `GetClassLayout`-Methode für die übergeordnete Klasse aufrufen, um diese Felder abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ca539-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="ca539-116">Wenn Sie `GetClassLayout` mit Zeichenfolgenklassen verwenden, schlägt die Methode mit dem Fehlercode E_INVALIDARG fehl.</span><span class="sxs-lookup"><span data-stu-id="ca539-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="ca539-117">Verwendung [ICorProfilerInfo2:: GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) beim Abrufen von Informationen über das Layout einer Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="ca539-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="ca539-118">Die `GetClassLayout`-Methode schlägt auch fehl, wenn sie mit einer Arrayklasse aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ca539-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="ca539-119">Nachdem `GetClassLayout` abgeschlossen ist, müssen Sie sicherstellen, dass der `rFieldOffset`-Puffer groß genug war, um alle verfügbaren `COR_FIELD_OFFSET`-Strukturen aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="ca539-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="ca539-120">Vergleichen Sie hierzu den Wert, auf den `pcFieldOffset` verweist, mit der Größe von `rFieldOffset` dividiert durch die Größe einer `COR_FIELD_OFFSET`-Struktur.</span><span class="sxs-lookup"><span data-stu-id="ca539-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="ca539-121">Wenn `rFieldOffset` nicht groß genug ist, weisen Sie einen größeren `rFieldOffset`-Puffer zu, aktualisieren Sie `cFieldOffset` mit der neuen Größe, und rufen Sie `GetClassLayout` erneut auf.</span><span class="sxs-lookup"><span data-stu-id="ca539-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="ca539-122">Alternativ können Sie zuerst `GetClassLayout` mit einem `rFieldOffset`-Puffer der Länge 0 (null) aufrufen, um die richtige Puffergröße zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="ca539-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ca539-123">Sie können die Puffergröße dann auf den Wert festlegen, der von `pcFieldOffset` zurückgegeben wurde, und `GetClassLayout` erneut aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ca539-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca539-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ca539-124">Requirements</span></span>  
 <span data-ttu-id="ca539-125">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca539-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca539-126">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ca539-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca539-127">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca539-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca539-128">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca539-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca539-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ca539-129">See Also</span></span>  
 [<span data-ttu-id="ca539-130">ICorProfilerInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ca539-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ca539-131">ICorProfilerInfo2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ca539-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="ca539-132">Profilerstellungsschnittstellen</span><span class="sxs-lookup"><span data-stu-id="ca539-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ca539-133">Profilerstellung</span><span class="sxs-lookup"><span data-stu-id="ca539-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)