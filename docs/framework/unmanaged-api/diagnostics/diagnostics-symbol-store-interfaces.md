---
title: Diagnosesymbolspeicher-Schnittstellen
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50ef54c90609bf8ef1e3a943664daef95f50d926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="5854c-102">Diagnosesymbolspeicher-Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="5854c-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="5854c-103">In diesem Thema wird beschrieben, die nicht verwalteten Schnittstellen, mit die einen Compiler Symbolinformationen für die Verwendung von einem Debugger generieren können.</span><span class="sxs-lookup"><span data-stu-id="5854c-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5854c-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="5854c-104">In This Section</span></span>  
 [<span data-ttu-id="5854c-105">IBindingDisplay-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="5854c-106">Enthält Methoden, die aktuelle Bindungsinformationen über die ausgeführte Anwendung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5854c-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="5854c-107">IDebugAutoAttach-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="5854c-108">Definiert die Schnittstelle an, für eine AutoAttach-Debuggers.</span><span class="sxs-lookup"><span data-stu-id="5854c-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="5854c-109">INotifyConnection2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="5854c-110">Deklariert Methoden zum Registrieren und Aufheben der Registrierung einer Notification Verbindungsquelle.</span><span class="sxs-lookup"><span data-stu-id="5854c-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="5854c-111">INotifySink2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="5854c-112">Deklariert Methoden für die Senke-Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="5854c-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="5854c-113">INotifySource2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="5854c-114">Deklariert eine Methode zum Festlegen der Benachrichtigungsfilter an.</span><span class="sxs-lookup"><span data-stu-id="5854c-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="5854c-115">ISymENCUnmanagedMethod-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="5854c-116">Enthält Informationen für die Funktion bearbeiten und fortfahren.</span><span class="sxs-lookup"><span data-stu-id="5854c-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="5854c-117">ISymUnmanagedAsyncMethod-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="5854c-118">Diese Schnittstelle ist die lesen-Ergänzung zur [ISymUnmanagedAsyncMethodPropertiesWriter-Schnittstelle](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5854c-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="5854c-119">ISymUnmanagedAsyncMethodPropertiesWriter-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="5854c-120">Ermöglicht die Definition der optionalen Async Methodeninformationen pro Methode-Symbol.</span><span class="sxs-lookup"><span data-stu-id="5854c-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="5854c-121">Muss mit einer geöffneten Methode verwenden (d. h. zwischen den Aufrufen der [OpenMethod-Methode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)und die [CloseMethod-Methode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="5854c-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="5854c-122">ISymUnmanagedBinder-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="5854c-123">Stellt einen Symbolbinder für nicht verwalteten Code dar.</span><span class="sxs-lookup"><span data-stu-id="5854c-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="5854c-124">ISymUnmanagedBinder2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="5854c-125">Stellt einen Symbolbinder für nicht verwalteten Code dar und erweitert die `ISymUnmanagedBinder` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5854c-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="5854c-126">ISymUnmanagedBinder3-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="5854c-127">Stellt einen Symbolbinder für nicht verwalteten Code dar und erweitert die `ISymUnmanagedBinder` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5854c-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="5854c-128">ISymUnmanagedConstant-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="5854c-129">Bietet Zugriff auf nicht verwaltete Konstanten.</span><span class="sxs-lookup"><span data-stu-id="5854c-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="5854c-130">ISymUnmanagedDispose-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="5854c-131">Gibt nicht verwaltete Ressourcen frei.</span><span class="sxs-lookup"><span data-stu-id="5854c-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="5854c-132">ISymUnmanagedDocument-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="5854c-133">Stellt ein Dokument dar, auf das von einem Symbolspeicher verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="5854c-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="5854c-134">ISymUnmanagedDocumentWriter-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="5854c-135">Stellt Methoden zum Schreiben in ein Dokument bereit, auf das ein Symbolspeicher verweist.</span><span class="sxs-lookup"><span data-stu-id="5854c-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="5854c-136">ISymUnmanagedENCUpdate-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="5854c-137">Stellt Methoden für die Funktion bearbeiten und fortfahren.</span><span class="sxs-lookup"><span data-stu-id="5854c-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="5854c-138">ISymUnmanagedMethod-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="5854c-139">Stellt eine Methode in den Symbolspeicher dar.</span><span class="sxs-lookup"><span data-stu-id="5854c-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="5854c-140">ISymUnmanagedNamespace-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="5854c-141">Stellt einen Namespace dar.</span><span class="sxs-lookup"><span data-stu-id="5854c-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="5854c-142">ISymUnmanagedReader-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="5854c-143">Stellt einen Symbolreader den Zugriff auf Dokumente, Methoden und Variablen in einem Symbolspeicher dar.</span><span class="sxs-lookup"><span data-stu-id="5854c-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="5854c-144">ISymUnmanagedReader2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="5854c-145">Ruft ein Methodenobjekt des Symbolreaders erhält ein Methodentoken und eine Versionsnummer für bearbeiten und kopieren.</span><span class="sxs-lookup"><span data-stu-id="5854c-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="5854c-146">ISymUnmanagedReaderSymbolSearchInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="5854c-147">Enthält Methoden, die Symbolinformationen für die Suche zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5854c-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="5854c-148">ISymUnmanagedScope-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="5854c-149">Stellt einen lexikalischen Gültigkeitsbereich in einer Methode dar.</span><span class="sxs-lookup"><span data-stu-id="5854c-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="5854c-150">ISymUnmanagedScope2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="5854c-151">Stellt einen lexikalischen Gültigkeitsbereich in einer Methode und erweitert die `ISymUnmanagedScope` -Schnittstelle um Methoden, die Informationen über definierte Konstanten innerhalb des Bereichs zu erhalten...</span><span class="sxs-lookup"><span data-stu-id="5854c-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="5854c-152">ISymUnmanagedSourceServerModule-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="5854c-153">Server-Quelldaten bereitstellt für ein Modul.</span><span class="sxs-lookup"><span data-stu-id="5854c-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="5854c-154">ISymUnmanagedSymbolSearchInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="5854c-155">Enthält Methoden, die Informationen zu den Suchpfad abrufen.</span><span class="sxs-lookup"><span data-stu-id="5854c-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="5854c-156">ISymUnmanagedVariable-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="5854c-157">Stellt eine Variable, z. B. einen Parameter, eine lokale Variable oder ein Feld dar.</span><span class="sxs-lookup"><span data-stu-id="5854c-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="5854c-158">ISymUnmanagedWriter-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="5854c-159">Stellt einen Symbolwriter dar und bietet Methoden zum Definieren von Dokumenten, Sequenzpunkte lexikalischen Gültigkeitsbereiche und Variablen.</span><span class="sxs-lookup"><span data-stu-id="5854c-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="5854c-160">ISymUnmanagedWriter2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="5854c-161">Stellt einen Symbolwriter dar und bietet Methoden zum Definieren von Dokumenten, Sequenzpunkte lexikalischen Gültigkeitsbereiche und Variablen.</span><span class="sxs-lookup"><span data-stu-id="5854c-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="5854c-162">Erweitert die `ISymUnmanagedWriter` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5854c-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="5854c-163">ISymUnmanagedWriter3-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="5854c-164">Stellt einen Symbolwriter dar und bietet Methoden zum Definieren von Dokumenten, Sequenzpunkte lexikalischen Gültigkeitsbereiche und Variablen.</span><span class="sxs-lookup"><span data-stu-id="5854c-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="5854c-165">Erweitert die `ISymUnmanagedWriter` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5854c-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="5854c-166">ISymUnmanagedWriter4-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="5854c-167">ISymUnmanagedWriter4-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5854c-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="5854c-168">ISymUnmanagedWriter5-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5854c-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="5854c-169">ISymUnmanagedWriter5-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5854c-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5854c-170">Verwandte Abschnitte</span><span class="sxs-lookup"><span data-stu-id="5854c-170">Related Sections</span></span>  
 [<span data-ttu-id="5854c-171">Diagnosesymbolspeicher-Enumerationen</span><span class="sxs-lookup"><span data-stu-id="5854c-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="5854c-172">Diagnosesymbolspeicher-Strukturen</span><span class="sxs-lookup"><span data-stu-id="5854c-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="5854c-173">Debuggen</span><span class="sxs-lookup"><span data-stu-id="5854c-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)