---
title: "Markup Extensions for XAML Overview | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "markup extensions [XAML Services], custom"
  - "XAML [XAML Services], markup extensions"
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
caps.latest.revision: 14
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 14
---
# Markup Extensions for XAML Overview
Bei Markuperweiterungen handelt es sich um eine XAML\-Technik für das Abrufen eines Werts, der weder ein primitiver noch ein spezifischer XAML\-Typ ist. Für die Attributverwendung verwenden Markuperweiterungen die bekannte Zeichensequenz einer öffnenden geschweiften Klammer `{` für den Anfang des Markuperweiterungsbereichs und eine schließende geschweifte Klammer `}` zum Beenden. Beim Verwenden von .NET Framework\-XAML\-Diensten können Sie einige der vordefinierten XAML\-Sprachmarkuperweiterungen aus der Assembly „System.Xaml“ verwenden. Sie können zudem in „System.Xaml“ definierte Subklassen aus der Klasse <xref:System.Windows.Markup.MarkupExtension> verwenden und Ihre eigenen Markuperweiterungen definieren. Alternativ können Sie durch ein bestimmtes Framework definierte Markuperweiterungen verwenden, wenn Sie dieses Framework bereits referenzieren.  
  
 Wenn auf eine Markuperweiterungsverwendung zugegriffen wird, kann der XAML\-Objekt\-Writer Dienste für eine benutzerdefinierte <xref:System.Windows.Markup.MarkupExtension>\-Klasse über einen Dienstverbindungspunkt in der <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=fullName>\-Überschreibung bereitstellen. Die Dienste können zum Abrufen des Kontexts über die Verwendung, spezifische Funktionalitäten des Objekt\-Writers, den XAML\-Schemakontext usw. verwendet werden.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## XAML\-definierte Markuperweiterungen  
 Zwecks XAML\-Sprachunterstützung werden verschiedene Markuperweiterungen durch die .NET Framework\-XAML\-Dienste implementiert. Diese Markuperweiterungen entsprechen Teilen der Spezifikation von XAML als Sprache. Diese lassen sich für gewöhnlich durch das `x:`\-Präfix in der Syntax bestimmen, wie dies unter der häufigen Verwendung zu sehen ist. Die .NET Framework\-XAML\-Dienstimplementierungen für diese XAML\-Sprachelemente werden alle von der <xref:System.Windows.Markup.MarkupExtension>\-Basisklasse abgeleitet.  
  
> [!NOTE]
>  Das Präfix `x:` wird für die typische XAML\-Namespacezuordnung des XAML\-Sprachnamespace im Stammelement einer XAML\-Produktion verwendet. Beispielsweise initiieren die [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]\-Projekt\- und \-Seitenvorlagen für verschiedene spezifische Frameworks eine XAML\-Datei mithilfe dieser `x:`\-Zuordnung. Sie können ein anderes Präfixtoken in Ihrer XAML\-Namespacezuordnung auswählen. In dieser Dokumentation wird jedoch von der standardmäßigen `x:`\-Zuordnung im Zuge der Ermittlung dieser Entitäten ausgegangen, die im Gegensatz zum standardmäßigen XAML\-Namespace eines bestimmten Frameworks oder anderer willkürlicher CLR\- oder XML\-Namespaces ein definierter Bestandteil des XAML\-Sprachennamespace sind.  
  
### x:Type  
 `x:Type` stellt das <xref:System.Type>\-Objekt für den benannten Typ bereit. Diese Funktionalität wird am häufigsten in Mechanismen mit Verzögerungen verwendet, die einen zugrunde liegenden CLR\-Typ und eine Typenableitung als Gruppierungsmoniker oder Bezeichner verwenden. WPF\-Style und \-Vorlagen und deren Verwendung von `TargetType`\-Eigenschaften sind ein bestimmtes Beispiel. Weitere Informationen finden Sie unter [x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
### x:Static  
 `x:Static` generiert statische Werte aus Werttypecode\-Entitäten, die nicht direkt der Typ des Werts einer Eigenschaft sind, jedoch zu diesem Typ ausgewertet werden können. Dies ist hilfreich für das Angeben von Werten, die bereits als bekannte Konstanten in einer Typendefinition vorhanden sind. Weitere Informationen finden Sie unter [x:Static Markup Extension](../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
### x:Null  
 `x:Null` gibt `null` als einen Wert für ein XAML\-Member an. In Abhängigkeit des Designs von bestimmten Typen oder größerer Frameworkkonzepte ist `null` nicht immer ein Standardwert für eine Eigenschaft oder der implizierte Wert eines leeren Zeichenfolgenattributs. Weitere Informationen finden Sie unter [x:Null Markup Extension](../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
### x:Array  
 `x:Array` unterstützt das Erstellen von allgemeinen Arrays in einer XAML\-Syntax in Fällen, wo die durch Basiselemente und Steuerelementmodelle bereitgestellte Auflistungsunterstützung nicht absichtlich verwendet wird. Weitere Informationen finden Sie unter [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md). Insbesondere in XAML 2009 erfolgt der Zugriff auf Arrays als Sprachprimitive und nicht im Sinne einer Erweiterung. Weitere Informationen finden Sie unter [XAML 2009 Language Features](../../../docs/framework/xaml-services/xaml-2009-language-features.md).  
  
### x:Reference  
 `x:Reference` ist ein Bestandteil von XAML 2009. Hierbei handelt es sich um eine Erweiterung des ursprünglichen \(2006\) Sprachsatzes.`x:Reference` repräsentiert einen Verweis auf ein anderes vorhandenes Objekt in einem Objektdiagramm. Dieses Objekt wird anhand seiner `x:Name` bestimmt. Weitere Informationen finden Sie unter [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md).  
  
### Andere x:\-Konstrukte  
 Es sind weitere `x:`\-Konstrukte für die Unterstützung von XAML\-Sprachfeatures vorhanden. Diese sind jedoch nicht als Markuperweiterungen implementiert. Weitere Informationen finden Sie unter [XAML Namespace \(x:\) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## Die MarkupExtension\-Basisklasse  
 Zum Definieren einer benutzerdefinierten Markuperweiterung, die mit standardmäßigen Implementierungen von XAML\-Readern und XAML\-Writern in „System.Xaml“ interagieren kann, müssen Sie eine Klasse aus der abstrakten Klasse <xref:System.Windows.Markup.MarkupExtension> ableiten. Diese Klasse verfügt über eine zu überschreibende Methode, nämlich <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Sie müssen möglicherweise zudem zusätzliche Konstruktoren definieren, um Argumente für die Markuperweiterungsverwendung und für den Abgleich von festlegbaren Eigenschaften zu unterstützen.  
  
 Durch <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> verfügt eine benutzerdefinierte Markuperweiterung über Zugriff auf einen Dienstkontext, der der Umgebung meldet, wo die Markuperweiterung tatsächlich durch einen XAML\-Prozessor aufgerufen wird. Im Ladepfad ist dies für gewöhnlich ein <xref:System.Xaml.XamlObjectWriter>. Im Speicherpfad ist dies für gewöhnlich ein <xref:System.Xaml.XamlXmlWriter>. Jeder Bericht der Dienstkontext als eine interne XAML\-Dienstanbieter\-Kontextklasse, die ein Dienstanbietermuster implementiert. Weitere Informationen über die verfügbaren Dienste und was sie darstellen finden Sie unter [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Ihre Markuperweiterungsklasse muss eine öffentliche Zugriffsebene verwenden. XAML\-Prozessoren müssen immer in der Lage sein, die Unterstützungsklasse der Markuperweiterung zu instanziieren, um die zugehörigen Dienste zu verwenden.  
  
<a name="naming_the_support_type"></a>   
## Definieren des Unterstützungstyps für eine benutzerdefinierte Markuperweiterung  
 Beim Verwenden von .NET Framework\-XAML\-Diensten oder auf .NET Framework\-XAML\-Diensten aufbauenden Frameworks haben Sie zwei Optionen hinsichtlich der Benennung des Markup\-Erweiterungsunterstützungstyps. Der Typname ist relevant für die Art und Weise des Zugriffsversuchs und Aufrufs von XAML\-Objekt\-Writern auf einen Markup\-Erweiterungsunterstützungstyp, wenn sie eine Markuperweiterungsverwendung in XAML feststellen. Verwenden Sie eine der folgenden Strategien für die Benennung:  
  
-   Der Typname muss genau mit dem Namen des XAML\-Markupverwendungstokens übereinstimmen. Benennen Sie beispielsweise für die Unterstützung einer `{Collate ...}`\-Erweiterungsverwendung den Unterstützungstyp `Collate`.  
  
-   Benennen Sie den Typnamen, sodass er das  Verwendungszeichenfolgentoken plus das Suffix `Extension` lautet. Benennen Sie beispielsweise für die Unterstützung einer `{Collate ...}`\-Erweiterungsverwendung den Unterstützungstyp `CollateExtension`.  
  
 Entsprechend der Suchreihenfolge wird zunächst nach dem Klassennamen mit dem Suffix `Extension` und dann nach dem Klassennamen ohne dem Suffix `Extension` gesucht.  
  
 Aus Sicht der Markupverwendung ist das Einschließen des Suffixes `Extension` als Bestandteil der Verwendung gültig. Dies verhält sich jedoch so, als wäre `Extension` ein wirklicher Bestandteil des Klassennamens. So könnten XAML\-Objekt\-Writer eine Markuperweiterungs\-Unterstützungsklasse für diese Verwendung nicht erfolgreich auflösen, wenn die Unterstützungsklasse nicht über das Suffix `Extension` verfügen würde.  
  
### Der Standardkonstruktor  
 Sie sollten für alle Markup\-Erweiterungsunterstützungstypen einen öffentlichen Standardkonstruktor verfügbar machen. Ein Standardkonstruktor ist erforderlich, wenn ein XAML\-Objekt\-Writer die Markuperweiterung über eine Objektelementverwendung instanziiert. Das Unterstützen der Objektelementverwendung ist eine angemessene Erwartung für eine Markuperweiterung, insbesondere für die Serialisierung. Sie können jedoch eine Markuperweiterung ohne einen öffentlichen Konstruktor implementieren, wenn Sie nur die Attributverwendungen der Markuperweiterung unterstützen möchten.  
  
 Wenn Ihre Markuperweiterungsverwendung über keine Argument verfügt, ist der Standardkonstruktor erforderlich, um die Verwendung zu unterstützen.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## Konstruktormuster und Positionsargumente für eine benutzerdefinierte Markuperweiterung  
 Für eine Markuperweiterung mit vorgesehener Argumentverwendung müssen die öffentlichen Konstruktoren den Modi der vorgesehenen Verwendung entsprechen. Wen für Ihre Markuperweiterung ein Positionsargument als eine gültige Verwendung erforderlich ist, sollten Sie demnach einen öffentlichen Konstruktor mit einem Eingabeparameter unterstützen, der das Positionsargument akzeptiert.  
  
 Angenommen, die `Collate`\-Markuperweiterung soll nur einen Modus unterstützen, in dem ein Positionsargument vorhanden ist, der den zugehörigen Modus darstellt, und zwar als eine `CollationMode`\-Enumerationskonstante angegeben. In diesem Fall sollte ein Konstruktor mit der folgenden Form vorliegen:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Auf einer grundlegenden Ebene handelt es sich bei den an eine Markuperweiterung weitergegebenen Argumenten um eine Zeichenfolge, da sie von den Attributwerten des Markups weitergeleitet werden. Sie können alle Ihre Argumente in Zeichenfolgen umwandeln und mit Eingaben auf dieser Ebene arbeiten. Sie haben jedoch Zugriff auf bestimmte Verarbeitungen, die auftreten, bevor die Markuperweiterungsargumente an die Unterstützungsklassen weitergegeben werden.  
  
 Die Verarbeitung erfolgt konzeptionell, als ob die Markuperweiterung ein zu erstellendes Objekt wäre, anschließend werden die zugehörigen Memberwerte festgelegt. Jede festzulegende angegebene Eigenschaft wird in ähnlicher Weise ausgewertet, wie ein angegebenes Member in einem erstellten Objekt festgelegt werden kann, wenn XAML analysiert wird. Es gibt zwei wichtige Unterschiede:  
  
-   Ein Markup\-Erweiterungsunterstützungstyp benötigt, wie bereits erwähnt, keinen Standardkonstruktor, um in XAML instanziiert zu werden. Seine Objektkonstruktion wird verzögert, bis seine möglichen Argumente in der Textsyntax als Positions\- oder Namensargumente in Token übersetzt und ausgewertet werden und der entsprechende Konstruktor zu diesem Zeitpunkt aufgerufen wird.  
  
-   Markuperweiterungsverwendungen können verschachtelt werden. Die innerste Markuperweiterung wird zuerst ausgewertet. Daher können Sie eine solche Verwendung annehmen und einen der Konstruktionsparameter als einen Typ deklarieren, für den ein zu generierender Wertkonverter \(beispielsweise eine Markuperweiterung\) erforderlich ist.  
  
 Der Einsatz dieser Verarbeitung wurde im vorherigen Beispiel gezeigt. Der XAML\-Objekt\-Writer für .NET Framework\-XAML\-Dienste verarbeitet Namen für Aufzählungskonstanten in Aufzählungswerte auf einer systemeigenen Ebene.  
  
 Die Verarbeitung einer Textsyntax eines Markup\-Erweiterungspositionsparameters kann auch auf einem Typkonverter beruhen, der mit dem Typ verknüpft ist, der sich im Konstruktionsargument befindet.  
  
 Die Argumente werden als Positionsargumente bezeichnet, da die Reihenfolge, in welcher die Token in der Verwendung ermittelt werden, der Positionsreihenfolge des Konstruktorparameters entspricht, zu dem sie zugewiesen werden. Ziehen Sie beispielsweise die folgende Konstruktorsignatur in Betracht:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Ein XAML\-Prozessor erwartet zwei Positionsargumente für diese Markuperweiterung. Bei Vorhandensein eines Verwendungs\-`{Collate AlphaUp,{x:Reference circularFile}}` wird das `AlphaUp`\-Token an den ersten Parameter gesendet und als eine als Konstante bezeichnete `CollationMode`\-Enumeration ausgewertet. Das Ergebnis der inneren `x:Reference` wird an den zweiten Parameter gesendet und wird als ein Objekt ausgewertet.  
  
 In der XAML dient das Komma für angegebene Regeln für die Markuperweiterungssyntax und \-verarbeitung als Trennzeichen zwischen Argumenten, und zwar unabhängig davon, ob es sich um Positions\- oder Namensargumente handelt.  
  
### Doppelte Stelligkeit von positionellen Argumenten  
 Wenn ein XAML\-Objekt\-Writer eine Markuperweiterungsverwendung mit Positionsargumenten ermittelt und mehrere Konstruktorargumente vorliegen, die die Anzahl der Argumente \(eine doppelte Stelligkeit\) verwenden, handelt es sich nicht zwangsläufig um einen Fehler. Das Verhalten ist von der anpassbaren XAML\-Schemakontexteinstellung <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> abhängig. Wenn <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>`true` ist, sollte ein XAML\-Objekt\-Writer keine Ausnahme auslösen, wenn es sich nur um eine doppelte Stelligkeit handelt. Das Verhalten über diesen Punkt hinaus ist nicht streng definiert. Im grundlegenden Entwurfsansatz wird davon ausgegangen, dass der Schemakontext für die bestimmten Parameter verfügbaren Typinformationen aufweist und explizite Umwandlungen versuchen kann, die die doppelten Kandidaten abgleichen, um zu sehen, bei welcher Signatur es sich um die beste Übereinstimmung handelt. Eine Ausnahme wird möglicherweise weiterhin ausgelöst, wenn keine der Signaturen die Tests besteht, die durch diesen bestimmten Schemakontext veranlasst werden, der auf einem XAML\-Objekt\-Writer ausgeführt wird.  
  
 Standardmäßig ist <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>`false` im CLR\-basierten <xref:System.Xaml.XamlSchemaContext> für .NET Framework\-XAML\-Dienste.  Daher löst der standardmäßige <xref:System.Xaml.XamlObjectWriter> Ausnahmen aus, wenn er eine Markuperweiterungsverwendung erkennt, bei der eine doppelte Stelligkeit in den Konstruktoren des Unterstützungstyps vorliegt.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## Benannte Argumente für eine benutzerdefinierte Markuperweiterung  
 Gemäß XAML spezifizierte Markuperweiterungen können zudem ein Formular für benannte Argumente für die Verwendung verwenden. Auf der ersten Ebene der Tokenisierung wird die Textsyntax in Argumente unterteilt. Das Vorhandensein eines Gleichheitszeichens \(\=\) in einem Argument bestimmt ein Argument als ein benanntes Argument. Ein derartiges Argument wird ebenfalls in ein Name\/Wert\-Paar in Token übersetzt. In diesem Fall wird eine öffentlich festlegbare Eigenschaft des Unterstützungstyps der Markuperweiterung benannt. Wenn Sie die benannte Argumentverwendung unterstützen möchten, sollten Sie diese öffentlich festlegbaren Eigenschaften bereitstellen. Bei den Eigenschaften kann es sich um geerbte Eigenschaften handeln, solange sie öffentlich bleiben.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## Zugriff auf den Dienstanbieterkontext über eine Markuperweiterungsimplementierung  
 Die verfügbaren Dienste sind für jeden Wertkonverter gleich. Der Unterschied besteht darin, wie jeder Wertkonverter den Dienstkontext empfängt. Der Zugriff auf Dienste und die verfügbaren Dienste wird im Thema [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md) beschrieben.  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## Eigenschaftselementverwendung einer Markuperweiterung  
 Die Szenarien für die Markuperweiterungsverwendungen werden oftmals um die Verwendung der Markuperweiterung in der Attributverwendung herum entworfen. Es ist jedoch auch potenziell möglich, die dahinterliegende Klasse zur Unterstützung von Eigenschaftselementen zu definieren.  
  
 Definieren Sie zum Unterstützen der Eigenschaftselementverwendung Ihrer Markuperweiterung einen öffentlichen Standardkonstruktor. Hierbei sollte es sich um einen Instanzkonstruktor und nicht um einen statischen Konstruktor handeln. Dies ist erforderlich, da ein XAML\-Prozessor in der Regel den Standardkonstruktor für jedes Objektelement aufrufen muss, dass es über das Markup verarbeitet, und dies umfasst Markuperweiterungsklassen als Objektelemente. Für erweiterte Szenarien können Sie nicht standardmäßige Konstruktionspfade für Klassen definieren. \(Weitere Informationen finden Sie unter [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md).\) Sie sollten diese Muster jedoch nicht für Markuperweiterungszwecke verwenden, da dadurch die Ermittlung des Verwendungsmusters viel komplizierter wird, und zwar sowohl für Designer als auch für die Benutzer des unformatierten Markups.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## Attributierung für eine benutzerdefinierte Markuperweiterung  
 Zum Unterstützen von Entwurfsumgebungen und bestimmten XAML\-Objekt\-Writer\-Szenarien sollten Sie einen Markup\-Erweiterungsunterstützungstyp mit verschiedenen CLR\-Attributen mit Attributen versehen. Diese Attribute melden die vorgesehene Markuperweiterungsverwendung.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> meldet die <xref:System.Type>\-Informationen für den Objekttyp, den <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> zurückgibt. Anhand seiner reinen Signatur gibt <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A><xref:System.Object> zurück. Verschiedene Verbraucher benötigen möglicherweise genauere Rückgabetypinformationen.  Dies umfasst Folgendes:  
  
-   Designer und IDEs, die möglicherweise in der Lage sind, eine typenkompatible Unterstützung für Markuperweiterungsverwendungen bereitzustellen.  
  
-   Erweiterte Implementierungen von `SetMarkupExtension`\-Handlern in Zielklassen, die sich auf die Berücksichtigung verlassen, um anstelle der Verzweigung auf spezifischen bekannten <xref:System.Windows.Markup.MarkupExtension>\-Implementierungen nach Name den Rückgabetyp einer Markuperweiterung zu bestimmen  
  
<a name="serialization_of_markup_extension_usages"></a>   
## Serialisierung von Markuperweiterungsverwendungen  
 Wenn ein XAML\-Objekt\-Writer eine Markuperweiterungsverwendung verarbeitet und <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> aufruft, verbleibt der Kontext dafür, der zuvor eine Markuperweiterungsverwendung war, im XAML\-Knotenstream, aber nicht im Objektdiagramm. Im Objektdiagramm wird nur der Wert beibehalten. Wenn andere Designszenarien oder andere Gründe für das Beibehalten der ursprünglichen Markuperweiterungsverwendung in die serialisierte Ausgabe vorliegen, müssen Sie Ihre eigene Infrastruktur für das Nachverfolgen der Markuperweiterungsverwendungen aus dem Ladepfad\-XAML\-Knotenstream entwerfen. Sie können ein Verhalten implementieren, um die Elemente des Knotenstreams aus dem Ladepfad erneut zu erstellen und sie für XAML\-Writer für die Serialisierung im Speicherpfad wiedergeben, wobei der Wert an der entsprechenden Stelle des Knotenstreams ersetzt wird.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## Markuperweiterungen im XAML\-Knotenstream  
 Beim Verwenden eines XAML\-Knotenstreams im Ladepfad wird eine Markuperweiterungsverwendung im Knotenstream als ein Objekt angezeigt.  
  
 Wenn die Markuperweiterungsverwendung Positionsargumente verwendet, wird sie als ein Startobjekt mit einem Initialisierungswert repräsentiert. Als grobe Textdarstellung ähnelt der Knotenstream Folgendem:  
  
 `StartObject` \(<xref:System.Xaml.XamlType> ist der Definitionstyp der Markuperweiterung und nicht dessen Rückgabetyp\)  
  
 `StartMember` \(der Name von <xref:System.Xaml.XamlMember> lautet `_InitializationText`\)  
  
 `Value` \(Wert entspricht den Positionsargumenten als eine Zeichenfolge, einschließlich der Trennzeichen\)  
  
 `EndMember`  
  
 `EndObject`  
  
 Eine Markuperweiterungsverwendung mit benannten Argumenten wird als ein Objekt mit Membern der entsprechenden Namen repräsentiert, wobei jedes mit Textzeichenfolgenwerten festgelegt ist.  
  
 Tatsächlich ist für das Aufrufen der `ProvideValue`\-Implementierung einer Markuperweiterung der XAML\-Schemakontext erforderlich, da dafür die Typenzuordnung und das Erstellen einer Markup\-Erweiterungsunterstützungs\-Typinstanz erforderlich sind. Daher werden Markuperweiterungsverwendungen auf diese Weise in standardmäßigen .NET Framework\-XAML\-Dienstknotenstreams beibehalten. Der Reader\-Teil eines Ladepfads verfügt oftmals nicht über den nötigen XAML\-Schemakontext.  
  
 Wenn Sie einen XAML\-Knotenstream auf einem Speicherpfad verwenden, steht für gewöhnlich nichts in einer Objektdiagrammdarstellung zur Verfügung, was Sie darüber informieren könnte, dass das zu serialisierende Objekt ursprünglich durch eine Markuperweiterungsverwendung und ein `ProvideValue`\-Ergebnis bereitgestellt wurde. Szenarien, die Markuperweiterungsverwendungen für 1 beibehalten und gleichzeitig andere Änderungen im Objektdiagramm erfassen müssen, müssen ihre eigenen Techniken für das Beibehalten der Informationen einer Markuperweiterungsverwendung aus der ursprünglichen XAML\-Eingabe entwickeln. Beispielsweise müssen Sie zum Wiederherstellen der Markuperweiterungsverwendungen mit dem Knotenstream auf dem Speicherpfad arbeiten, um Markuperweiterungsverwendungen wiederherzustellen, oder einen Zusammenführungstyp zwischen der ursprünglichen  XAML und der Roundtrip\-XAML ausführen. Einige XAML\-Implementierungsframeworks wie WPF verwenden Zwischentypen \(Ausdrücke\), um das Darstellen von Fällen zu unterstützen, in denen Markuperweiterungsverwendungen die Werte bereitstellen.  
  
## Siehe auch  
 <xref:System.Windows.Markup.MarkupExtension>   
 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)   
 [Markuperweiterungen und WPF\-XAML](../../../ocs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)