---
title: Verpacken und Bereitstellen von Ressourcen in Desktop-Apps
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ab23b263d572a5573de5fc21f15b56e784a9a94
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
---
# <a name="packaging-and-deploying-resources-in-desktop-apps"></a>Verpacken und Bereitstellen von Ressourcen in Desktop-Apps
Anwendungen sind davon abhängig, dass der .NET Framework-Ressourcen-Manager, der von der Klasse <xref:System.Resources.ResourceManager> dargestellt wird, lokalisierte Ressourcen abruft. Der Ressourcen-Manager geht davon aus, dass ein Speichenarchitektur-Modell (Hub-and-Spoke) verwendet wird, um Ressourcen zu verpacken und bereitzustellen. Der Hub ist die Hauptassembly, die den nicht lokalisierbaren, ausführbaren Code und die Ressourcen für eine einzelne Kultur enthält, die als neutrale oder Standardkultur bezeichnet wird. Die Standardkultur ist die Ausweichkultur der Anwendung. Dabei handelt es sich um die Kultur, deren Ressourcen verwendet werden, wenn keine lokalisierten Ressourcen gefunden werden können. Jede Speiche ist mit einer Satellitenassembly verbunden, die die Ressourcen für eine einzelne Kultur aber keinen Code enthält.  
  
 Dieses Modell hat mehrere Vorzüge:  
  
-   Sie können Ressourcen für neue Kulturen inkrementell hinzufügen, nachdem Sie eine Anwendung bereitgestellt haben. Da die aufeinanderfolgende Entwicklung von kulturspezifischen Ressourcen viel Zeit in Anspruch nehmen kann, können Sie so zunächst Ihre Hauptanwendung veröffentlichen und kulturspezifische Ressourcen zu einem späteren Zeitpunkt nachreichen.  
  
-   Sie können die Satellitenassembly einer Anwendung aktualisieren oder ändern, ohne die Anwendung erneut kompilieren zu müssen.  
  
-   Eine Anwendung muss nur die Satellitenassemblys laden, die die für eine bestimmte Kultur benötigten Ressourcen enthalten. Dadurch kann die Auslastung von Systemressourcen deutlich verringert werden.  
  
 Dennoch hat dieses Modell auch Nachteile:  
  
-   Sie müssen mehrere Ressourcensätze gleichzeitig verwalten.  
  
-   Der anfängliche Kostenaufwand für das Testen einer Anwendung steigt, da Sie mehrere Konfigurationen überprüfen müssen. Beachten Sie, dass es auf lange Sicht einfacher und kostengünstiger wird, eine Kernanwendung mit mehreren Satelliten zu testen, als mehrere internationale Versionen gleichzeitig zu testen und zu verwalten.  
  
## <a name="resource-naming-conventions"></a>Namenskonventionen für Ressourcen  
 Wenn Sie die Ressourcen Ihrer Anwendung verpacken, müssen Sie diese gemäß den Namenskonventionen für Ressourcen benennen, die von der Common Language Runtime (CLR) erwartet werden. Die Runtime identifiziert eine Ressource anhand deren Kulturnamen. Jede Kultur erhält einen eindeutigen Namen, für gewöhnlich eine Kombination aus zwei Kleinbuchstaben, die für eine Kultur und die damit verbundene Sprache steht, und, falls erforderlich, zwei Großbuchstaben, die für eine Subkultur und das damit verbundene Land bzw. die Region stehen. Der Name der Subkultur steht hinter dem Namen der Kultur, getrennt durch einen Bindestrich (-). Dies kann z.B. ja-JP für das in Japan gesprochene Japanisch sein, en-US für das amerikanische Englisch, de-DE für das in Deutschland gesprochene Deutsch oder de-AT für Österreichisch. Eine vollständige Liste der Kulturnamen finden Sie in der [Referenz zur Unterstützung der Landessprache (NLS)](http://go.microsoft.com/fwlink/?LinkId=200048) im Go Global Developer Center.  
  
> [!NOTE]
>  Informationen zum Erstellen von Ressourcendateien finden Sie unter [Erstellen von Ressourcendateien](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) und [Erstellen von Satellitenassemblys](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>Der Ressourcenfallback-Prozess  
 Das Speichenarchitektur-Modell (Hub-and-Spoke) zum Verpacken und Bereitstellen von Ressourcen setzt einen Fallbackprozess ein, um die passenden Ressourcen zu finden. Wenn eine Anwendung eine lokalisierte Ressource anfordert, die nicht verfügbar ist, durchsucht die CLR die Hierarchie von Kulturen nach einer passenden Ausweichressource, die am ehesten der Anfrage der Anwendung des Benutzers entspricht, und löst eine Ausnahme nur dann aus, wenn es keine andere Möglichkeit gibt. Wenn eine passende Ressource auf einer der Ebenen der Hierarchie gefunden wird, verwendet die Runtime diese. Wenn keine Ressource gefunden wird, wird die Suche auf der nächsten Ebene fortgesetzt.  
  
 Um die Suchleistung zu verbessern, wenden Sie das Attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> auf Ihre Hauptassembly an, und übergeben Sie diesem den Namen der neutralen Sprache, die mit Ihrer Hauptassembly funktioniert.  
  
> [!TIP]
>  Möglicherweise können Sie auch den Fallbackprozess von Ressourcen und den Suchprozess der Runtime nach Ressourcenassemblys mit dem Konfigurationselement [\<relativeBindForResources>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) verbessern. Weitere Informationen finden Sie im Abschnitt [Verbessern des Ressourcenfallbackprozesses](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing).  
  
 Der Ressourcenfallbackprozess besteht aus folgenden Schritten:  
  
1.  Zunächst prüft die Runtime den [globalen Assemblycache](../../../docs/framework/app-domains/gac.md) auf eine Assembly, die der angeforderten Kultur für Ihre Anwendung entspricht.  
  
     Der globale Assemblycache kann Ressourcenassemblys speichern, die in vielen Anwendungen eingesetzt werden. So müssen Sie keine bestimmten Ressourcensätze in die Verzeichnisstruktur von jeder Anwendung, die sie erstellen, einbeziehen. Wenn die Runtime einen Verweis auf die Assembly findet, durchsucht sie die Assembly nach der angeforderten Ressource. Wenn sie den Eintrag in der Assembly findet, verwendet sie die angeforderte Ressource. Wenn sie den Eintrag nicht findet, fährt sie mit der Suche fort.  
  
2.  Als Nächstes prüft die Runtime das Verzeichnis der aktuell ausgeführten Assembly auf ein Verzeichnis, das der angeforderten Kultur entspricht. Wenn sie das Verzeichnis findet, durchsucht sie dieses Verzeichnis nach einer gültigen Satellitenassembly für die angeforderte Kultur. Dann durchsucht die Runtime die Satellitenassembly nach der angeforderten Ressource. Wenn sie die Ressource in der Assembly findet, verwendet sie diese. Wenn sie die Ressource nicht findet, fährt sie mit der Suche fort.  
  
3.  Anschließend fragt die Runtime den Windows Installer ab, um zu bestimmten, ob die Satellitenassembly bei Bedarf installiert werden soll. Wenn dies der Fall ist, kümmert sie sich um die Installation, lädt die Assembly und durchsucht diese nach der angeforderten Ressource. Wenn sie die Ressource in der Assembly findet, verwendet sie diese. Wenn sie die Ressource nicht findet, fährt sie mit der Suche fort.  
  
4.  Die Runtime löst das Ereignis <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> aus, um anzugeben, dass die Satellitenassembly nicht gefunden werden kann. Wenn Sie das Ereignis behandeln möchten, kann Ihr Ereignishandler einen Verweis auf die Satellitenassembly zurückgeben, deren Ressourcen bei der Suche verwendet werden. Andernfalls gibt der Ereignishandler `null` zurück und die Suche wird fortgesetzt.  
  
5.  Als Nächstes durchsucht die Runtime erneut den globalen Assemblycache, aber dieses Mal sucht sie nach der übergeordneten Assembly der angeforderten Kultur. Wenn die übergeordnete Assembly im globalen Assemblycache vorhanden ist, durchsucht die Runtime die Assembly nach der angeforderten Ressource.  
  
     Die übergeordnete Kultur ist als zulässige Fallbackkultur definiert. Übergeordnete Elemente könne als Fallback genutzt werden, da da Bereitstellen einer Ressource dem Auslösen einer Ausnahme vorzuziehen ist. Durch diesen Prozess könne Sie auch Ressourcen wiederverwenden. Sie sollten auf der Ebene des übergeordneten Elements nur dann eine bestimmte Ressource verwenden, wenn die untergeordnete Kultur die angeforderte Ressource nicht lokalisieren muss. Wenn Sie z.B. eine Satellitenassembly für en (neutrales Englisch), en-GB (britisches Englisch) und en-US (amerikanisches Englisch) bereitstellen, enthält der en-Satellit das gemeinsame Vokabular, und die Satelliten für en-GB und en-US enthalten nur Überschreibungen für Begriffe, die sich in den beiden Kulturen unterscheiden.  
  
6.  Als Nächstes prüft die Runtime das Verzeichnis der aktuell ausgeführten Assembly auf übergeordnete Verzeichnisse. Wenn ein übergeordnetes Verzeichnis vorhanden ist, durchsucht die Runtime das Verzeichnis nach einer gültigen Satellitenassembly für die übergeordnete Kultur. Wenn sie die Assembly findet, durchsucht die Runtime die Assembly nach der angeforderten Ressource. Wenn sie die Ressource findet, verwendet sie diese. Wenn sie die Ressource nicht findet, fährt sie mit der Suche fort.  
  
7.  Anschließend fragt die Runtime den Windows Installer ab, um zu bestimmten, ob die übergeordnete Satellitenassembly bei Bedarf installiert werden soll. Wenn dies der Fall ist, kümmert sie sich um die Installation, lädt die Assembly und durchsucht diese nach der angeforderten Ressource. Wenn sie die Ressource in der Assembly findet, verwendet sie diese. Wenn sie die Ressource nicht findet, fährt sie mit der Suche fort.  
  
8.  Die Runtime löst das Ereignis <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> aus, um anzugeben, dass die entsprechende Fallbackressource nicht gefunden werden kann. Wenn Sie das Ereignis behandeln möchten, kann Ihr Ereignishandler einen Verweis auf die Satellitenassembly zurückgeben, deren Ressourcen bei der Suche verwendet werden. Andernfalls gibt der Ereignishandler `null` zurück und die Suche wird fortgesetzt.  
  
9. Als Nächstes durchsucht die Runtime die übergeordnete Assembly genauso wie in den drei vorherigen Schritten auf vielen möglichen Ebenen. Jede Kultur hat nur ein übergeordnetes Element, das durch die <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>-Eigenschaft definiert wird. Ein übergeordnetes Element kann jedoch wieder sein eigenes übergeordnetes Element haben. Die Suche nach übergeordneten Kulturen ist beendet, wenn die <xref:System.Globalization.CultureInfo.Parent%2A>-Eigenschaft einer Kultur <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zurückgibt. Beim Ressourcenfallback wird die invariante Kultur nicht als übergeordnete Kultur oder als Kultur angesehen, die Ressourcen haben kann.  
  
10. Wenn die ursprünglich angegebene Kultur und alle übergeordneten Elemente durchsucht wurden, und die Ressource immer noch nicht gefunden werden kann, wir die Ressource für die Standardkultur (Fallback) verwendet. Für gewöhnlich werden die Ressourcen der Standardkultur in die Hauptassembly der Anwendung integriert. Sie könne aber einen Wert von <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> für die <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A>-Eigenschaft des <xref:System.Resources.NeutralResourcesLanguageAttribute>-Attributs angeben, um festzulegen, dass der endgültige Fallbackort für Ressourcen eine Satellitenassembly ist und nicht die Hauptassembly.  
  
    > [!NOTE]
    >  Die Standardressource ist die einzige Ressource, die mit der Hauptassembly kompiliert werden kann. Wenn Sie nicht mit dem <xref:System.Resources.NeutralResourcesLanguageAttribute>-Attribut eine Satellitenassembly angegeben haben, ist sie der endgültige Fallback (letztes übergeordnetes Element). Deshalb wird empfohlen, dass Sie immer ein Standardset an Ressourcen in Ihre Hauptassembly integrieren. So werden Ausnahmen verhindert. Durch das Integrieren einer Standardressourcendatei stellen Sie einen Fallback für alle Ressourcen zur Verfügung und stellen sicher, dass immer mindestens eine Ressource für den Benutzer verfügbar ist, auch wenn diese nicht kulturspezifisch ist.  
  
11. Wenn die Runtime keine Ressource für eine Standard(fallback)kultur findet, wird die Ausnahme <xref:System.Resources.MissingManifestResourceException> oder <xref:System.Resources.MissingSatelliteAssemblyException> ausgelöst, um anzugeben, dass die Ressource nicht gefunden werden konnte.  
  
 Nehmen Sie z.B. an, dass die Anwendung eine lokalisierte Ressource für Spanisch (Mexiko) anfordert (die Kultur es-MX). Zunächst durchsucht die Runtime den globalen Assemblycache nach der Assembly, die es-MX entspricht. Diese kann jedoch nicht gefunden werden. Dann durchsucht die Runtime das Verzeichnis der aktuell ausgeführten Assembly nach dem Verzeichnis es-MX. Da auch dies zu keinem Ergebnis führt, durchsucht die Runtime erneut den globalen Assemblycache nach einer übergeordneten Kultur, die der entsprechenden Fallbackkultur entspricht — in diesem Fall es (Spanisch). Wenn die übergeordnete Assembly nicht gefunden werden kann, durchsucht die Runtime alle potenziellen Ebenen von übergeordneten Assemblys nach der Kultur es-MX, bis sie eine passende Ressource findet. Wenn keine Ressource gefunden werden kann, verwendet die Runtime die Ressource der Standardkultur.  
  
<a name="Optimizing"></a>   
### <a name="optimizing-the-resource-fallback-process"></a>Optimieren des Ressourcen-Fallback-Prozesses  
 Unter folgenden Bedingungen können Sie den Prozess optimieren, mit dem die Runtime nach Ressourcen in den Satellitenassemblys sucht  
  
-   Satellitenassemblys werden am gleichen Ort wie die Codeassembly bereitgestellt. Wenn die Codeassembly im [globalen Assemblycache](../../../docs/framework/app-domains/gac.md) installiert wird, werden gleichzeitig Satellitenassemblys im globalen Assemblycache installiert. Wenn die Codeassembly in einem Verzeichnis installiert wird, werden Satellitenassemblys in kulturspezifischen Ordnern in diesem Verzeichnisses installiert.  
  
-   Satellitenassemblys werden nicht bei Bedarf installiert.  
  
-   Der Anwendungscode behandelt nicht das Ereignis <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
 Sie können die Überprüfung auf Satellitenassemblys durch das Integrieren des Elements [\<relativeBindForResources>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) optimieren, und indem Sie dessen `enabled`-Attribut in der Anwendungskonfigurationsdatei auf `true` festlegen, wie in folgendem Beispiel veranschaulicht.  
  
```xml  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
```  
  
 Die optimierte Überprüfung auf Satellitenassemblys ist ein Opt-In-Feature. Das heißt, dass die Runtime die Schritte aus [Der Ressourcenfallback-Prozess](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) durchführt, es sei denn, das Element [\<relativeBindForResources>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) befindet sich in der Anwendungskonfigurationsdatei, während dessen `enabled`-Attribut auf `true` festgelegt ist. Wenn dies der Fall ist, wird der Suchprozess nach einer Satellitenassembly wie folgt angepasst:  
  
-   Die Runtime verwendet den Speicherort der übergeordneten Codeassembly, um nach der Satellitenassembly zu suchen. Wenn die übergeordnete Assembly im globalen Assemblycache installiert ist, durchsucht die Runtime den Cache, aber nicht das Anwendungsverzeichnis. Wenn die übergeordnete Assembly im Anwendungsverzeichnis installiert ist, durchsucht die Runtime das Anwendungsverzeichnis, aber nicht den globalen Assemblycache.  
  
-   Die Runtime fragt den Windows Installer nicht nach der On-Demand-Installation von Satellitenassemblys.  
  
-   Wenn die Suche nach einer bestimmten Ressourcenassembly fehlschlägt, löst die Runtime nicht das Ereignis <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> aus.  
  
### <a name="ultimate-fallback-to-satellite-assembly"></a>Endgültiger Fallback der Satellitenassembly  
 Sie können optional Ressourcen aus der Hauptassembly entfernen und angeben, dass die Runtime die endgültige Fallbackressource aus einer Satellitenassembly für eine bestimmte Kultur laden soll. Um den Fallbackprozess zu steuern, können Sie den <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType>-Konstruktor verwenden und einen Wert für den Parameter <xref:System.Resources.UltimateResourceFallbackLocation> angeben, der bestimmt, ob der Ressourcen-Manager die Fallbackressource aus der Hauptassembly oder aus einer Satellitenassembly extrahieren soll.  
  
 In folgendem Beispiel wird das Attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> dazu verwendet, die Fallbackressource einer Anwendung in einer Satellitenassembly für Französisch (fr) zu speichern.  Im Beispiel werden zwei textbasierte Ressourcendateien verwendet, die eine einzelne Zeichenfolgenressource mit dem Namen `Greeting` definieren. Die erste Datei, „resources.fr.txt“, enthält eine französische Sprachressource.  
  
```  
Greeting=Bon jour!  
```  
  
 Die zweite Datei, „resources.ru.txt“, enthält eine russische Sprachressource.  
  
```  
Greeting=Добрый день  
```  
  
 Diese beiden Dateien werden zu RESOURCES-Datei kompiliert, indem Sie das [Resource File Generator-Tool („resgen.exe“)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) in der Befehlszeile ausführen.  Der Befehl für die französische Sprachressource lautet:  
  
 **resgen.exe resources.fr.txt**  
  
 Der Befehl für die russische Sprachressource lautet:  
  
 **resgen.exe resources.ru.txt**  
  
 Die RESOURCES-Dateien werden in DLLs (Dynamic Link Libraries) eingebettet, indem Sie den [Assemblylinker („al.exe“)](../../../docs/framework/tools/al-exe-assembly-linker.md) in der Befehlszeile für die französische Sprachressource wie folgt ausführen:  
  
 **al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 und für die russische Sprachressource:  
  
 **al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 Der Quellcode der Anwendung befindet sich in einer Datei mit dem Namen „example1.cs“ oder „example1.vb“. Er beinhaltet das Attribut <xref:System.Resources.NeutralResourcesLanguageAttribute>, um anzugeben, dass sich die Standardanwendungsressource im Unterverzeichnis „fr“ befindet. Er instantiiert den Ressourcen-Manager, ruft den Wert der `Greeting`-Ressource ab und zeigt ihn in der Konsole an.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 Dann können Sie den C#-Quellcode aus der Befehlszeile wie folgt kompilieren:  
  
 **csc Example1.cs**  
  
 Der Befehl für den Visual Basic-Compiler ist sehr ähnlich:  
  
 **vbc Example1.vb**  
  
 Da keine Ressourcen in der Hauptassembly eingebettet sind, müssen Sie nicht mit dem `/resource`-Switch kompilieren.  
  
 Wenn Sie das Beispiel in einem System durchführen, dessen Sprachen nicht Russisch ist, wird die folgende Ausgabe angezeigt:  
  
```  
Bon jour!  
```  
  
## <a name="suggested-packaging-alternative"></a>Empfohlene Verpackalternative  
 Möglicherweise können Sie aus Zeit- oder Kostengründen keinen Satz an Ressourcen für jede Subkultur erstellen, die von Ihrer Anwendung unterstützt wird. Stattdessen können Sie eine einzelne Satellitenassembly für eine übergeordnete Kultur erstellen, die von allen verknüpften Subkulturen verwendet werden kann. Sie können z.B eine einzelne englische Satellitenassembly (en) bereitstellen, die von Benutzern abgerufen wird, die regionsspezifische englische Ressourcen angefordert haben, und eine einzelne deutsche Satellitenassembly (de) für Benutzer, die regionsspezifische deutsche Ressourcen angefordert haben. Für Anforderungen von z.B. Deutsch, wie es in Deutschland (de-DE), in Österreich (de-AT) oder der Schweiz (de-CH) gesprochen wird, wird auf die deutsche Satellitenassembly (de) ausgewichen. Die Standardressourcen sind die endgültigen Fallbacks und sollten deshalb die Ressourcen sein, die von der Mehrheit der Benutzer Ihrer Anwendung angefordert werden. Achten Sie also darauf, welche Ressourcen Sie dafür auswählen. Bei dieser Vorgehensweise werden Ressourcen bereitgestellt, die weniger kulturspezifisch sind, aber die Lokalisierungskosten Ihrer Anwendung deutlich verringern können.  
  
## <a name="see-also"></a>Siehe auch  
 [Ressourcen in Desktop-Apps](../../../docs/framework/resources/index.md)  
 [Globaler Assemblycache](../../../docs/framework/app-domains/gac.md)  
 [Erstellen von Ressourcendateien](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Erstellen von Satellitenassemblys](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
