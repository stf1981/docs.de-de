---
title: "Sn.exe (Strong Name Tool) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "public keys, signing files"
  - "Strong Name tool"
  - "Sn.exe"
  - "assemblies [.NET Framework], signing"
  - "signing files"
  - "strong-named assemblies, signing files"
  - "key pairs for signing files"
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
caps.latest.revision: 44
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 44
---
# Sn.exe (Strong Name Tool)
Das Strong Name\-Tool \(SN.EXE\) hilft beim Signieren von Assemblys mit [starken Namen](../../../docs/framework/app-domains/strong-named-assemblies.md).  SN.EXE stellt Optionen zum Verwalten von Schlüsseln, Erzeugen und Überprüfen von Signaturen bereit.  
  
 Weitere Informationen zu starken Namen und Assemblys mit starken Namen finden Sie unter [Assemblys mit starkem Namen](../../../docs/framework/app-domains/strong-named-assemblies.md) und [Gewusst wie: Signieren einer Assembly mit einem starken Namen](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Das Strong Name\-Tool wird automatisch mit Visual Studio installiert.  Zum Starten des Tools verwenden Sie die Developer\-Eingabeaufforderung \(oder die Visual Studio\-Eingabeaufforderung in Windows 7\).  Weitere Informationen finden Sie unter [Eingabeaufforderungen](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Auf 64\-Bit\-Computern können die 32\-Bit\-Version von SN.EXE \(über die Eingabeaufforderung von Visual Studio\) und auch die 64\-Bit\-Version \(über die Eingabeaufforderung von Visual Studio x64 Win64\) ausgeführt werden.  
  
 Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
## Syntax  
  
```  
  
sn [-quiet][option [parameter(s)]]  
```  
  
#### Parameter  
  
|Option|Beschreibung|  
|------------|------------------|  
|**\-a** *identityKeyPairFile* *signaturePublicKeyFile*|Generiert <xref:System.Reflection.AssemblySignatureKeyAttribute>\-Daten zum Migrieren des Identitätsschlüssels zum Signaturschlüssel aus einer Datei.|  
|**\-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Generiert <xref:System.Reflection.AssemblySignatureKeyAttribute>\-Daten zum Migrieren des Identitätsschlüssels zum Signaturschlüssel aus einem Schlüsselcontainer.|  
|**\-c** \[*csp*\]|Legt den für das Signieren mit starken Namen zu verwendenden kryptografischen Standarddienstanbieter \(Cryptographic Service Provider, CSP\) fest.  Diese Einstellung gilt für den gesamten Computer.  Wenn Sie keinen CSP\-Namen angeben, löscht SN.EXE die aktuelle Einstellung.|  
|**\-d** *container*|Löscht den angegebenen Schlüsselcontainer aus dem CSP für starke Namen.|  
|**\-D**  *assembly1 assembly2*|Überprüft, ob sich zwei Assemblys nur in der Signatur unterscheiden.  Diese Prüfung wird häufig eingesetzt, nachdem eine Assembly mit einem anderen Schlüsselpaar neu signiert wurde.|  
|**\-e**  *Assembly\-Ausgabedatei*|Extrahiert den öffentlichen Schlüssel aus der *Assembly* und speichert ihn in der *Ausgabedatei*.|  
|**\-h**|Zeigt Befehlssyntax und Optionen für das Tool an.|  
|**\-i** *Eingabedatei Container*|Installiert das Schlüsselpaar aus der *Eingabedatei* in dem angegebenen Schlüsselcontainer.  Der Schlüsselcontainer befindet sich im CSP für starke Namen.|  
|**\-k** \[*Schlüsselgröße*\] *Ausgabedatei*|Generiert einen neuen <xref:System.Security.Cryptography.RSACryptoServiceProvider>\-Schlüssel mit der angegebenen Größe und schreibt ihn in die angegebene Datei.  Sowohl ein öffentlicher als auch ein privater Schlüssel werden in die Datei geschrieben.<br /><br /> Wenn Sie keine Schlüsselgröße angeben, wird standardmäßig ein 1.024\-Bit\-Schlüssel generiert, sofern Microsoft Enhanced Cryptographic Provider installiert ist; andernfalls wird ein 512\-Bit\-Schlüssel generiert.<br /><br /> Wenn der Microsoft Enhanced Cryptographic Provider installiert ist, unterstützt der Parameter *keysize* nur Schlüssellängen von 384 bis 16.384 Bit \(in Schritten von 8 Bit\).  Wenn der Microsoft Base Cryptographic Provider installiert ist, werden Schlüssellängen von 384 bis 512 Bit \(in Schritten von 8 Bit\) unterstützt.|  
|**\-m** \[**y** *&#124;* **n**\]|Gibt an, ob Schlüsselcontainer computerspezifisch oder benutzerspezifisch sind.  Wenn Sie *y* angeben, sind die Schlüsselcontainer computerspezifisch.  Bei Angabe von *n* sind die Schlüsselcontainer benutzerspezifisch.<br /><br /> Wenn weder "y" noch "n" angegeben wird, zeigt diese Option die aktuelle Einstellung an.|  
|**\-o**  *Eingabedatei* \[*Ausgabedatei*\]|Extrahiert den öffentlichen Schlüssel aus der *Eingabedatei* und speichert ihn in einer CSV\-Datei.  Die einzelnen Byte des öffentlichen Schlüssels werden durch Kommas getrennt.  Dieses Format eignet sich zum Hartcodieren von Schlüsselverweisen als initialisierte Arrays im Quellcode.  Wenn Sie keine *Ausgabedatei* angeben, wird die Ausgabe dieser Option in der Zwischenablage gespeichert. **Note:**  Diese Option überprüft nicht, ob die Eingabe nur ein öffentlicher Schlüssel ist.  Wenn `infile` ein Schlüsselpaar mit einem privaten Schlüssel enthält, wird der private Schlüssel auch extrahiert.|  
|**\-p** *Eingabedatei Ausgabedatei* \[*hashalg*\]|Extrahiert den öffentlichen Schlüssel aus dem Schlüsselpaar in der *Eingabedatei* und speichert ihn in der *Ausgabedatei* unter optionaler Verwendung des RSA\-Algorithmus, der von *hashalg* angegeben wird.  Dieser öffentlichen Schlüssel kann zum verzögerten Signieren einer Assembly unter Verwendung der Optionen **\/delaysign\+** und **\/keyfile** des [Assembly Linker\-Tools \(AL.EXE\)](../../../docs/framework/tools/al-exe-assembly-linker.md) verwendet werden.  Beim verzögerten Signieren einer Assembly wird während der Kompilierung nur der öffentliche Schlüssel festgelegt und Speicherplatz in der Datei reserviert, damit die Signatur später hinzugefügt werden kann, wenn der private Schlüssel bekannt ist.|  
|**\-pc**  *Container* *Ausgabedatei* \[*hashalg*\]|Extrahiert den öffentlichen Schlüssel aus dem Schlüsselpaar im *Container* und speichert ihn in der *Ausgabedatei*.  Wenn Sie die Option *hashalg* verwenden, wird der öffentliche Schlüssel mit dem RSA\-Algorithmus extrahiert.|  
|**\-Pb** \[**y** *&#124;* **n**\]|Legt fest, ob die Bypassrichtlinie für starke Namen erzwungen wird.  Wenn Sie *y* angeben, werden starke Namen für voll vertrauenswürdige Assemblys beim Laden in ein voll vertrauenswürdiges <xref:System.AppDomain> nicht geprüft.  Wenn Sie *n* angeben, werden starke Namen auf Korrektheit geprüft, jedoch nicht auf einen bestimmten starken Namen.  <xref:System.Security.Permissions.StrongNameIdentityPermission> hat keine Auswirkung auf voll vertrauenswürdige Assemblys.  Sie müssen eine eigene Überprüfung auf Übereinstimmung bei einem starken Namen durchführen.<br /><br /> Wenn weder `y` noch `n` angegeben ist, zeigt diese Option die aktuelle Einstellung an.  Die Standardeinstellung ist `y`. **Note:**  Auf 64\-Bit\-Computern müssen diese Parameter sowohl in der 32\-Bit\- als auch in der 64\-Bit\-Instanz von SN.EXE festgelegt werden.|  
|**\-q**\[**uiet**\]|Gibt den stillen Modus an, in dem die Anzeige von Erfolgsmeldungen unterdrückt wird.|  
|**\-R**\[**a**\] *Assembly* *Eingabedatei*|Signiert eine bereits signierte oder eine verzögert signierte Assembly mit dem Schlüsselpaar in der *Eingabedatei* neu.<br /><br /> Bei Angabe von **\-Ra** werden Hashes für alle Dateien in der Assembly neu berechnet.|  
|**\-Rc**\[**a**\] *Assembly Container*|Signiert eine bereits signierte oder eine verzögert signierte Assembly mit dem Schlüsselpaar in *Container*.<br /><br /> Bei Angabe von **\-Rca** werden Hashes für alle Dateien in der Assembly neu berechnet.|  
|**\-Rh** *Assembly*|Berechnet Hashes für alle Dateien in der Assembly neu.|  
|**\-t**\[**p**\] *Eingabedatei*|Zeigt das in der *Eingabedatei* gespeicherte Token für den öffentlichen Schlüssel an.  Die *Eingabedatei* muss einen öffentlichen Schlüssel enthalten, der zuvor mittels **\-p** aus einer Schlüsselpaardatei generiert wurde.  Verwenden Sie nicht die Option **\-t\[p\]**, um das Token direkt aus einer Schlüsselpaardatei zu extrahieren.<br /><br /> SN.EXE berechnet das Token mithilfe einer Hashfunktion aus dem öffentlichen Schlüssel.  Um Speicherplatz zu sparen, werden Token für öffentliche Schlüssel von der Common Language Runtime als Teil eines Verweises auf eine weitere Assembly im Manifest gespeichert, wenn eine Abhängigkeit zu einer Assembly mit starkem Namen aufgezeichnet wird.  Bei der Option **\-tp** wird zusätzlich zum Token auch der öffentliche Schlüssel angezeigt.  Wenn das <xref:System.Reflection.AssemblySignatureKeyAttribute>\-Attribut auf die Assembly angewendet wurde, dient das Token für den Identitätsschlüssel, und der Name des Hashalgorithmus und der Identitätsschlüssel werden angezeigt.<br /><br /> Beachten Sie, dass bei Verwendung dieser Option die Assemblysignatur nicht überprüft wird und daher nicht für Entscheidungen über Vertrauensstellungen verwendet werden sollte.  Bei Angabe dieser Option werden nur die unformatierten Tokendaten des öffentlichen Schlüssels angezeigt.|  
|**\-T**\[**p**\] *Assembly*|Zeigt das Token des öffentlichen Schlüssels für die *Assembly an.* Die *Assembly* muss dem Namen einer Datei entsprechen, die ein Assemblymanifest enthält.<br /><br /> SN.EXE berechnet das Token mithilfe einer Hashfunktion aus dem öffentlichen Schlüssel.  Um Speicherplatz zu sparen, werden Token für öffentliche Schlüssel von der Runtime als Teil eines Verweises auf eine weitere Assembly im Manifest gespeichert, wenn eine Abhängigkeit zu einer Assembly mit starkem Namen aufgezeichnet wird.  Bei der Option **\-Tp** wird zusätzlich zum Token auch der öffentliche Schlüssel angezeigt.  Wenn das <xref:System.Reflection.AssemblySignatureKeyAttribute>\-Attribut auf die Assembly angewendet wurde, dient das Token für den Identitätsschlüssel, und der Name des Hashalgorithmus und der Identitätsschlüssel werden angezeigt.<br /><br /> Beachten Sie, dass bei Verwendung dieser Option die Assemblysignatur nicht überprüft wird und daher nicht für Entscheidungen über Vertrauensstellungen verwendet werden sollte.  Bei Angabe dieser Option werden nur die unformatierten Tokendaten des öffentlichen Schlüssels angezeigt.|  
|`-TS`  `assembly` `infile`|Signiert testweise die vollständig oder teilweise signierte `assembly` mit dem Schlüsselpaar aus der `infile`.|  
|\-`TSc` `assembly` `container`|Signiert testweise die vollständig oder teilweise signierte `assembly` mit dem Schlüsselpaar aus dem Schlüsselcontainer `container`.|  
|**\-v** *Assembly*|Überprüft den starken Namen in *Assembly*, wobei *Assembly* der Name einer Datei ist, die ein Assemblymanifest enthält.|  
|**\-vf**  *assembly*|Überprüft den starken Namen in der *Assembly.* Im Unterschied zur Option **\-v** wird bei Angabe von **\-vf** die Überprüfung auch dann erzwungen, wenn diese mit der Option **\-Vr** deaktiviert wurde.|  
|**\-Vk**  *regfile.reg* *Assembly* \[*userlist*\] \[*infile*\]|Erstellt eine Datei für Registrierungseinträge \(.REG\), die Sie verwenden können, um die angegebene Assembly für das Überspringen der Überprüfung zu registrieren.  Für mit der Option **\-Vr** angegebene Assemblys gelten die gleichen Benennungsregeln wie bei der Option **–Vk**.  Weitere Informationen zu den Optionen *userlist* und *infile* finden Sie bei den Erläuterungen zur Option **–Vr**.|  
|**\-Vl**|Listet aktuelle Einstellungen für die Überprüfung starker Namen auf dem Computer auf.|  
|**\-Vr**  *Assembly* \[*userlist*\] \[*infile*\]|Registriert die *Assembly* zum Überspringen bei der Überprüfung.  Optional können Sie eine durch Trennzeichen getrennte Liste von Benutzernamen angeben, bei denen die Überprüfung übersprungen werden soll.  Bei Angabe von *infile* bleibt die Überprüfung aktiviert, bei Überprüfungsvorgängen wird jedoch der öffentliche Schlüssel aus *infile* verwendet.  Sie können *Assembly* in der Form *\*, strongname* angeben, um alle Assemblys mit dem angegebenen starken Namen zu registrieren.  Bei *strongname* geben Sie die Zeichenfolge hexadezimaler Ziffern fest, aus denen der öffentliche Schlüssel in seiner Token\-Form besteht.  Wie Sie den öffentlichen Schlüssel anzeigen, wird bei den Optionen **\-t** und **\-T** erläutert. **Caution:**  Verwenden Sie diese Option nur bei der Entwicklung.  Das Überspringen der Überprüfung einer Assembly kann ein erhebliches Sicherheitsrisiko darstellen.  Wenn die Überprüfung einer Assembly übersprungen wird, besteht die Gefahr, dass deren vollständig angegebener Assemblyname \(Assemblyname, Version, Kultur und öffentliches Schlüsseltoken\) als falsche Identität einer böswilligen Assembly verwendet wird.  Dadurch würde auch die Überprüfung der böswilligen Assembly übersprungen.|  
|||  
|**\-Vu**  *Assembly*|Hebt die Registrierung der *Assembly* für das Überspringen bei der Überprüfung auf.  Bei Assemblynamen gelten für **\-Vu** dieselben Regeln wie für **\-Vr**.|  
|**\-Vx**|Entfernt alle Einträge bezüglich des Überspringens der Überprüfung.|  
|**\-?**|Zeigt Befehlssyntax und Optionen für das Tool an.|  
  
> [!NOTE]
>  Bei allen Optionen für SN.EXE wird zwischen der Groß\- und Kleinschreibung unterschieden. Sie müssen die Optionen daher exakt wie gezeigt angeben, damit sie vom Tool richtig interpretiert werden.  
  
## Hinweise  
 Die Optionen **\-R** und **\-Rc** sind bei Assemblys nützlich, die verzögert signiert wurden.  In diesem Szenario wurde während der Kompilierung nur der öffentliche Schlüssel festgelegt. Die Signierung wird auf einen späteren Zeitpunkt verschoben, wenn der private Schlüssel bekannt ist.  
  
> [!NOTE]
>  Bei Parametern \(wie –**Vr\)**, die Schreibzugriffe auf geschützte Ressourcen \(z. B. die Registrierung\) durchführen, müssen Sie SN.EXE als Administrator ausführen.  
  
## Beispiele  
 Mit dem folgenden Befehl wird ein neues, nach dem Zufallsprinzip erzeugtes Schlüsselpaar erstellt und in `keyPair.snk` gespeichert.  
  
```  
sn -k keyPair.snk  
```  
  
 Mit dem folgenden Befehl wird der Schlüssel aus `keyPair.snk` im CSP für starke Namen im Container `MyContainer` gespeichert.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Der folgende Befehl extrahiert den öffentlichen Schlüssel aus `keyPair.snk` und speichert ihn in `publicKey.snk`.  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Mit dem folgenden Befehl werden der öffentliche Schlüssel und das in `publicKey.snk` gespeicherte Token für den öffentlichen Schlüssel angezeigt.  
  
```  
sn -tp publicKey.snk  
```  
  
 Mit dem folgenden Befehl wird die Assembly `MyAsm.dll` überprüft.  
  
```  
sn -v MyAsm.dll  
```  
  
 Mit dem folgenden Befehl wird `MyContainer` aus dem Standard\-CSP gelöscht.  
  
```  
sn -d MyContainer  
```  
  
## Siehe auch  
 [Tools](../../../docs/framework/tools/index.md)   
 [Al.exe \(Assembly Linker\-Tool\)](../../../docs/framework/tools/al-exe-assembly-linker.md)   
 [Assemblys mit starkem Namen](../../../docs/framework/app-domains/strong-named-assemblies.md)   
 [Eingabeaufforderungen](../../../docs/framework/tools/developer-command-prompt-for-vs.md)