---
title: 'Gewusst wie: Erstellen von Windows-Diensten'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 7d93f8543b9e6e370827f5a666315d562e28ee76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-windows-services"></a>Gewusst wie: Erstellen von Windows-Diensten
Wenn Sie einen Dienst erstellen, können Sie Visual Studio-Projektvorlage **Windowsdienst**. Von dieser Vorlage wird ein großer Teil der Arbeit übernommen, indem auf die entsprechenden Klassen und Namespaces verwiesen wird, die Vererbung von den Basisklassen für Dienste eingerichtet wird und eine Reihe von Methoden überschrieben werden, die voraussichtlich überschrieben werden sollen.  
  
> [!WARNING]
>  Die Projektvorlage Windows Service ist nicht in der Express Edition von Visual Studio verfügbar.  
  
 Das Erstellen eines funktionierenden Diensts erfordert mindestens:  
  
-   Legen Sie die <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>-Eigenschaft fest.  
  
-   Das Erstellen der für die Dienstanwendung erforderlichen Installationsprogramme.  
  
-   Durch das Überschreiben der <xref:System.ServiceProcess.ServiceBase.OnStart%2A>-Methode und der <xref:System.ServiceProcess.ServiceBase.OnStop%2A>-Methode und die Eingabe von Code wird das Verhalten des Diensts angepasst.  
  
### <a name="to-create-a-windows-service-application"></a>So erstellen Sie eine Windows-Dienstanwendung  
  
1.  Erstellen einer **Windowsdienst** Projekt.  
  
    > [!NOTE]
    >  Anleitungen zum Schreiben von einem Dienst ohne Verwendung der Vorlage finden Sie unter [wie: Schreiben Sie Dienste programmgesteuert](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  In der **Eigenschaften** legen die <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Eigenschaft für den Dienst.  
  
     ![Legen Sie die ServiceName-Eigenschaft. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  Der Wert der <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>-Eigenschaft muss immer mit dem Namen übereinstimmen, der in den Installationsprogrammklassen aufgezeichnet wurde. Wenn Sie diese Eigenschaft ändern, muss auch die <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>-Eigenschaft der Installationsprogrammklassen aktualisiert werden.  
  
3.  Legen Sie eine oder mehrere der folgenden Eigenschaften fest, um zu bestimmen, wie der Dienst funktionieren soll.  
  
    |Eigenschaft|Einstellung|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|Mit `True` wird angezeigt, dass vom Dienst Anforderungen zum Beenden angenommen werden. Mit `false` wird verhindert, dass der Dienst beendet werden kann.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|Mit `True` wird angegeben, dass der Dienst benachrichtigt werden soll, wenn der ausführende Computer heruntergefahren wird. Dadurch wird ermöglicht, dass die <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>-Prozedur aufgerufen werden kann.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|Mit `True` wird angegeben, dass vom Dienst Anforderungen zum Anhalten und Fortsetzen angenommen werden. Mit `false` wird verhindert, dass der Dienst angehalten oder fortgesetzt werden kann.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`um anzugeben, dass der Dienst Benachrichtigungen zu Änderungen an den Energiezustand des Computers behandeln kann. `false` um zu verhindern, dass den Dienst diese Änderungen informiert wird.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|Mit `True` werden informative Einträge in das Anwendungsereignisprotokoll geschrieben, sobald vom Dienst eine Aktion durchgeführt wird. Mit `false` wird diese Funktion deaktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: Protokoll Informationen zu Diensten](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Hinweis:** standardmäßig <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> festgelegt ist, um `true`.|  
  
    > [!NOTE]
    >  Wenn <xref:System.ServiceProcess.ServiceBase.CanStop%2A> oder <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> festgelegt `false`, die **Dienststeuerungs-Manager** werden die entsprechenden Menüoptionen zum Beenden, Anhalten oder Fortsetzen des Diensts zu deaktivieren.  
  
4.  Greifen Sie auf den Code-Editor zu, und geben Sie die gewünschte Verarbeitung für die <xref:System.ServiceProcess.ServiceBase.OnStart%2A>-Prozedur und die <xref:System.ServiceProcess.ServiceBase.OnStop%2A>-Prozedur ein.  
  
5.  Überschreiben Sie alle anderen Methoden, für die Sie Funktionen definieren möchten.  
  
6.  Fügen Sie die für die Dienstanwendung erforderlichen Installationsprogramme hinzu. Weitere Informationen finden Sie unter [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Erstellen Sie das Projekt, indem Sie auswählen **Projektmappe** aus der **erstellen** Menü.  
  
    > [!NOTE]
    >  Drücken Sie nicht F5, um das Projekt auszuführen. Dienstprojekte können auf diese Weise nicht ausgeführt werden.  
  
8.  Installieren Sie den Dienst. Weitere Informationen finden Sie unter [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in Windows-Dienstanwendungen](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Vorgehensweise: Programmgesteuertes Schreiben von Diensten](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [Vorgehensweise: Hinzufügen von Installern zur Dienstanwendung](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Vorgehensweise: Protokollinformationen über Dienste](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Vorgehensweise: Starten von Diensten](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Vorgehensweise: Angeben des Sicherheitskontexts für Dienste](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [Vorgehensweise: Installieren und Deinstallieren von Diensten](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Exemplarische Vorgehensweise: Erstellen einer Windows-Dienstanwendung im Komponenten-Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
