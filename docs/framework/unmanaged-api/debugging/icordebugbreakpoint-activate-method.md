---
title: ICorDebugBreakpoint::Activate-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint.Activate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7112ff7d18d0232da42013dfd533689cb8c5f0ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="103ab-102">ICorDebugBreakpoint::Activate-Methode</span><span class="sxs-lookup"><span data-stu-id="103ab-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="103ab-103">Legt den Zustand "aktiven" dieses `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="103ab-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="103ab-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="103ab-104">Syntax</span></span>  
  
```  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="103ab-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="103ab-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="103ab-106">[in] Legen Sie diesen Wert auf `true` an den Zustand als aktiv ist; andernfalls legen Sie diesen Wert auf `false`.</span><span class="sxs-lookup"><span data-stu-id="103ab-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="103ab-107">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="103ab-107">Requirements</span></span>  
 <span data-ttu-id="103ab-108">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="103ab-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="103ab-109">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="103ab-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="103ab-110">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="103ab-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="103ab-111">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="103ab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>