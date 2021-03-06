---
title: Oracle-BFILEs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7e7b7d438abb5a7e14a55f30447d291d3c8ee286
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-bfiles"></a>Oracle-BFILEs
Der .NET Framework-Datenanbieter für Oracle enthält die <xref:System.Data.OracleClient.OracleBFile>-Klasse, die für das Arbeiten mit dem Oracle-<xref:System.Data.OracleClient.OracleType.BFile>-Datentyp verwendet wird.  
  
 Die Oracle **BFILE** -Datentyp ist ein Oracle- **LOB** -Datentyp, der einen Verweis auf Binärdaten mit einer maximalen Größe von 4 Gigabyte enthält. Ein Oracle **BFILE** unterscheidet sich von anderen Oracle- **LOB** -Datentypen darin, dass ihre Daten in einer physischen Datei im Betriebssystem statt auf dem Server gespeichert sind. Beachten Sie, dass die **BFILE** Datentyp bietet schreibgeschützten Zugriff auf Daten.  
  
 Andere Merkmale der eine **BFILE** -Datentyp, der Unterscheidung von einer **LOB** -Datentyp sind:  
  
-   Er enthält unstrukturierte Daten.  
  
-   Er unterstützt das serverseitige Aufteilen in kleine Blöcke.  
  
-   Er verwendet die Semantik zum Kopieren von Verweisen. Angenommen, Sie für einen Kopiervorgang Ausführen eine **BFILE**wird nur der **BFILE** Locator (Dies ist ein Verweis auf die Datei) kopiert wird. Die Daten in der Datei werden nicht kopiert.  
  
 Die **BFILE** -Datentyp sollte zum Verweisen auf LOBs, die groß ist, verwendet werden und daher nicht praktikabel ist, in der Datenbank gespeichert. Client und Server-Kommunikation Aufwands beteiligt ist, bei Verwendung einer **BFILE** Datentyp im Vergleich mit der **LOB** -Datentyp. Es ist jedoch effizienter, den Zugriff auf eine **BFILE** Wenn nur eine kleine Menge Daten abgerufen werden müssen. Es ist effektiver, auf datenbankresidente LOBs zuzugreifen, wenn das ganze Objekt abgerufen werden soll.  
  
 Jeder Wert ungleich NULL **OracleBFile** Objekt bezieht sich auf zwei Entitäten, die den Speicherort der zugrunde liegenden physischen Datei definieren:  
  
1.  Ein Oracle-DIRECTORY-Objekt, das als Datenbank-Alias für ein Verzeichnis im Dateisystem fungiert.  
  
2.  Der Dateiname der zugrunde liegenden physischen Datei, die sich in dem dem DIRECTORY-Objekt zugeordneten Verzeichnis befindet.  
  
## <a name="example"></a>Beispiel  
 Im folgenden C#-Beispiel wird veranschaulicht, wie kann ein **BFILE** in einer Oracle-Tabelle, und klicken Sie dann in Form von Abrufen einer **OracleBFile** Objekt. Im Beispiel veranschaulicht die Verwendung der <xref:System.Data.OracleClient.OracleDataReader> Objekt und die **OracleBFile** **Seek** und **lesen** Methoden. Beachten Sie, dass in diesem Beispiel verwenden möchten, Sie zuerst ein Verzeichnis namens erstellen müssen "" c: "\\\bfiles" und die Datei "MyFile.jpg" auf dem Oracle-Server.  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Oracle und ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET Managed Provider und DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)
