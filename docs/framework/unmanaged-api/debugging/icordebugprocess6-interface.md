---
title: ICorDebugProcess6-Schnittstelle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9928018b7d4065fbf24b4c39f7ef2d121e66d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6-Schnittstelle
Erweitert logisch die ICorDebugProcess-Schnittstelle zum Aktivieren von Features wie z. B. der Decodierung verwalteter Debug-Ereignisse, die in systemeigenen Ausnahme-Debug-Ereignissen und Teilen virtueller Module codiert sind.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[DecodeEvent-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Decodiert verwaltete Debug-Ereignisse, die in den Nutzdaten der speziell gestalteten systemeigenen Ausnahme-Debug-Ereignissen gekapselt sind.|  
|[EnableVirtualModuleSplitting-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Aktiviert oder deaktiviert die virtuelle Modulteilung.|  
|[GetCode-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Ruft Informationen über den verwalteten Code an einer bestimmten Codeadresse ab.|  
|[GetExportStepInfo-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Enthält Informationen über die exportierten Laufzeitfunktionen, welche dabei helfen, den verwaltetem Code schrittweise durchzugehen.|  
|[MarkDebuggerAttached-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Ändert den internen Status des zu debuggenden Objekts, sodass die <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>-Methode in der .NET Framework-Klassenbibliothek `true` zurückgibt.|  
|[ProcessStateChanged-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Benachrichtigt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , die der Prozess ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
>  Diese Schnittstelle ist nur in Verbindung mit .NET Native verfügbar. Bei dem Versuch, `QueryInterface` aufzurufen, um einen Schnittstellenzeiger abzurufen, wird für ICorDebug-Szenarien außerhalb von .NET Native `E_NOINTERFACE` zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Schnittstellen](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debuggen](../../../../docs/framework/unmanaged-api/debugging/index.md)
