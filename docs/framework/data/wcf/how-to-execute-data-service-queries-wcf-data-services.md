---
title: "Gewusst wie: Ausführen von Datendienstabfragen (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ed40236fd902536a45e821abea768d5117fafde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Gewusst wie: Ausführen von Datendienstabfragen (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ermöglicht es Ihnen, mit den generierten Clientdatendienstklassen einen Datendienst aus einer .NET Framework-basierten Clientanwendung abzufragen. Für die Ausführung der Abfragen stehen folgende Methoden zur Verfügung:  
  
-   Ausführen einer LINQ-Abfrage für die benannte <xref:System.Data.Services.Client.DataServiceQuery%601>-Instanz, die Sie aus dem <xref:System.Data.Services.Client.DataServiceContext>-Objekt abrufen, den das Tool `Add Data Service Reference` generiert.  
  
-   Implizit durch Aufzählen über die benannte <xref:System.Data.Services.Client.DataServiceQuery%601>-Instanz, die Sie aus dem <xref:System.Data.Services.Client.DataServiceContext>-Objekt abrufen, den das Tool `Add Data Service Reference` generiert.  
  
-   Explizit durch Aufrufen der <xref:System.Data.Services.Client.DataServiceContext.Execute%2A>-Methode für die <xref:System.Data.Services.Client.DataServiceQuery%601>-Instanz oder der <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>-Methode für die asynchrone Ausführung.  
  
 Weitere Informationen finden Sie unter [Abfragen des Datendiensts](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Im Beispiel in diesem Thema werden der Northwind-Beispieldatendienst und automatisch generierte Client-Datendienstklassen verwendet. Dieser Dienst und die clientdatenklassen werden erstellt, wenn Sie die [WCF Data Services-Schnellstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie eine LINQ-Abfrage definieren und ausführen, die alle `Customers` für den Northwind-Datendienst zurückgibt.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie den vom Tool `Add Data Service Reference` generierten Kontext verwenden, um eine Abfrage implizit auszuführen, die alle `Customers` für den Northwind-Datendienst zurückgibt. Der URI der angeforderten `Customers`-Entitätenmenge wird automatisch vom Kontext bestimmt. Die Abfrage wird implizit ausgeführt, wenn die Enumeration auftritt.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie den <xref:System.Data.Services.Client.DataServiceContext> verwenden, um eine Abfrage explizit auszuführen, die alle `Customers` für den Northwind-Datendienst zurückgibt.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Hinzufügen von Abfrageoptionen zu einer Datendienstabfrage](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
