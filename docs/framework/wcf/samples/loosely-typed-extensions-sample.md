---
title: Beispiel zu lose typisierten Erweiterungen
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8861138f7763f413f06983bbfba5f6e0ec3c8b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="loosely-typed-extensions-sample"></a>Beispiel zu lose typisierten Erweiterungen
Das Syndication-Objektmodell bietet umfangreiche Unterstützung zum Arbeiten mit Erweiterungsdaten – Informationen, die in der XML-Darstellung eines Syndication-Feeds vorhanden, jedoch nicht explizit durch Klassen wie <xref:System.ServiceModel.Syndication.SyndicationFeed> und <xref:System.ServiceModel.Syndication.SyndicationItem> verfügbar gemacht werden. Dieses Beispiel veranschaulicht die grundlegenden Techniken zum Arbeiten mit Erweiterungsdaten.  
  
 Für das Beispiel wird die <xref:System.ServiceModel.Syndication.SyndicationFeed>-Klasse verwendet. Die in diesem Beispiel gezeigten Muster können jedoch mit allen Syndication-Klassen verwendet werden, die Erweiterungsdaten unterstützen:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Beispiel-XML  
 Zu Referenzzwecken wird in diesem Beispiel das folgende XML-Dokument verwendet.  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 Dieses Dokument enthält die folgenden einzelnen Erweiterungsdaten:  
  
-   Das `myAttribute`-Attribut des `<feed>`-Elements.  
  
-   `<simpleString>`-Element.  
  
-   `<DataContractExtension>`-Element.  
  
-   `<XmlSerializerExtension>`-Element.  
  
-   `<xElementExtension>`-Element.  
  
## <a name="writing-extension-data"></a>Schreiben von Erweiterungsdaten  
 Attributerweiterungen werden erstellt, indem man der <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>-Auflistung Einträge hinzufügt, wie im folgenden Beispielcode gezeigt.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Elementerweiterungen werden erstellt, indem man der <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>-Auflistung Einträge hinzufügt. Diese Erweiterungen können einfache Werte (wie Zeichenfolgen), XML-Serialisierungen von .NET Framework-Objekten oder manuell codierte XML-Knoten sein.  
  
 Im folgenden Beispielcode wird ein Erweiterungselement namens `simpleString` erstellt.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Der XML-Namespace für dieses Element ist der leere Namespace ("") und sein Wert ist ein Textknoten mit der Zeichenfolge "hello, World!".  
  
 Eine Möglichkeit zum Erstellen komplexer Elementerweiterungen, die aus vielen verschachtelten Elementen bestehen, wäre die Verwendung der .NET Framework-APIs zur Serialisierung (sowohl <xref:System.Runtime.Serialization.DataContractSerializer> als auch <xref:System.Xml.Serialization.XmlSerializer> werden unterstützt), wie in den folgenden Beispielen dargestellt.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 In diesem Beispiel sind `DataContractExtension` und `XmlSerializerExtension` benutzerdefinierte, zur Verwendung mit einem Serialisierer geschriebene Typen.  
  
 Elementerweiterungen können auch mithilfe der <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>-Klasse aus einer <xref:System.Xml.XmlReader>-Instanz erstellt werden. Dies erlaubt eine einfache Integration in APIs für die Verarbeitung von XML (wie <xref:System.Xml.Linq.XElement>), wie im folgenden Beispielcode gezeigt.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Lesen von Erweiterungsdaten  
 Die Werte für Attributerweiterungen können erhalten werden, indem das Attribut in der <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>-Auflistung anhand seines <xref:System.Xml.XmlQualifiedName> nachgeschlagen wird, wie im folgenden Beispielcode gezeigt.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Der Zugriff auf Elementerweiterungen erfolgt mit der `ReadElementExtensions<T>`-Methode.  
  
```  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 Es ist auch möglich, einen `XmlReader` bei einzelnen Elementerweiterungen mithilfe der <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>-Methode abzurufen.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>So können Sie das Beispiel einrichten, erstellen und ausführen  
  
1.  Stellen Sie sicher, dass Sie ausgeführt haben die [Setupprozedur für die Windows Communication Foundation-Beispiele zum einmaligen](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Um die C#- oder Visual Basic .NET-Edition der Projektmappe zu erstellen, befolgen Sie die unter [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)aufgeführten Anweisungen.  
  
3.  Um das Beispiel in einer einzelnen oder computerübergreifenden Konfiguration ausführen möchten, folgen Sie den Anweisungen [Ausführen der Windows Communication Foundation-Beispiele](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Siehe auch  
 [Stark typisierte Erweiterungen](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [WCF Syndication](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
