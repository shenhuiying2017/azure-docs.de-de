---
title: "Versionshinweise zum Azure SDK für .NET 2.7 und .NET 2.7.1"
description: "Versionshinweise zum Azure SDK für .NET 2.7 und .NET 2.7.1"
services: app-service\web
documentationcenter: .net
author: chrissfanos
editor: 
ms.assetid: 877d070a-9bd5-49b3-8fac-6bb5f65c3554
ms.service: app-service
ms.devlang: multiple
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: integration
ms.date: 02/24/2017
ms.author: juliako
ms.openlocfilehash: 9a69253129cdedc4f5d7e736d5bd8d6a68f95a1e
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2017
---
# <a name="azure-sdk-for-net-27-and-net-271-release-notes"></a>Versionshinweise zum Azure SDK für .NET 2.7 und .NET 2.7.1
## <a name="overview"></a>Übersicht
Dieses Dokument enthält die Versionshinweise für das Azure SDK für .NET 2.7. 

Dieses Dokument enthält auch die Versionshinweise für das Azure SDK für .NET 2.7.1.

Azure SDK 2.7 wird nur in Visual Studio 2015 und Visual Studio 2013 unterstützt. [Azure SDK 2.6](https://azure.microsoft.com/downloads/) ist das letzte unterstützte SDK für Visual Studio 2012.

Ausführliche Informationen zu dieser Version finden Sie im [Ankündigungsbeitrag zu Azure SDK 2.7](https://azure.microsoft.com/blog/2015/07/20/announcing-the-azure-sdk-2-7-for-net/) und im [Ankündigungsbeitrag zu Azure SDK 2.7.1](http://go.microsoft.com/fwlink/?LinkId=623850).

## <a name="azure-sdk-for-net-27"></a>Azure SDK für .NET 2.7
### <a name="sign-in-improvements-for-visual-studio-2015"></a>Verbesserungen bei der Anmeldung für Visual Studio 2015
Azure SDK 2.7 für Visual Studio 2015 unterstützt die neuen Identitätsverwaltungsfunktionen in Visual Studio 2015.  Dies umfasst die Unterstützung für Konten, bei denen der Zugriff auf Azure über die rollenbasierte Access Control, Cloud-Lösungsanbieter und DreamSpark erfolgt, und für andere Konto- und Abonnementtypen.

Diese Verbesserungen bei der Anmeldung im Azure SDK 2.7 sind nur in Visual Studio 2015 verfügbar. Die Unterstützung für Visual Studio 2013 ist im Azure SDK 2.7.1 enthalten.

### <a name="mobile-sdk"></a>Mobile SDK
Aktualisierte **Mobile Apps** -Vorlagen entsprechend dem neuesten [NuGet-Paket](https://www.nuget.org/packages/Microsoft.Azure.Mobile.Server/) und Installationsvorgang.

### <a name="service-bus"></a>Service Bus
Allgemeine Fehlerbehebungen und Verbesserungen. Ausführliche Informationen zu Updates und Funktionen finden Sie in den Versionshinweisen zum neuesten [Service Bus NuGet-Paket](http://www.nuget.org/packages/WindowsAzure.ServiceBus/)(in englischer Sprache).

### <a name="hdinsight-tools"></a>HDInsight-Tools
In dieser Version wurden die folgenden Aktualisierungen vorgenommen. Diese Aktualisierungen befinden sich in der Vorschauphase. Weitere Informationen finden Sie in [diesem Blog](http://go.microsoft.com/fwlink/?LinkId=619108).

* Hive-Diagramme für Hive unter Tez-Aufträge
* Vollständige IntelliSense-Unterstützung für Hive-DML
* Unterstützung von Pig-Vorlagen
* Storm-Vorlagen für Azure-Dienste

#### <a name="breaking-changes"></a>Wichtige Änderungen
* Das alte **Storm** -Projekt muss bei Verwendung dieser Version der Tools aktualisiert werden. Weitere Informationen finden Sie in [diesem Blog](http://go.microsoft.com/fwlink/?LinkId=619108).
* Visual Studio Web Express wird nicht mehr unterstützt. Weitere Informationen finden Sie in [diesem Blog](http://go.microsoft.com/fwlink/?LinkId=619108).

### <a name="azure-app-service-tools"></a>Azure App Service Tools
In dieser Version wurden die folgenden Aktualisierungen an den Erweiterungen für Webtools vorgenommen. Weitere Informationen finden Sie in [diesem](https://azure.microsoft.com/blog/2015/07/20/announcing-the-azure-sdk-2-7-for-net/) Blog. 

* Unterstützung für DreamSpark-Konten
* Vollständige Änderung an Azure Tools zur Unterstützung der neuen Azure Resource Management-APIs
* Unterstützung für Azure App Service in [Cloud Explorer](#cloud_explorer)

#### <a name="known-issues"></a>Bekannte Probleme
Knoten des Web-App-Bereitstellungsslots werden unter dem Knoten "Slots" in Server-Explorer nicht angezeigt, und untergeordnete Knoten des Web-App-Bereitstellungsslots werden unter Cloud Explorer nicht geladen. Dieses Problem wurde behoben und für die nächste SDK-Version vorbereitet. 

### <a name="cloud_explorer"></a>Cloud Explorer für Visual Studio 2015
Azure SDK 2.7 enthält Cloud Explorer für Visual Studio 2015, mit dem Sie Ihre Azure-Ressourcen anzeigen, deren Eigenschaften überprüfen und wichtige Entwickleraktionen in Visual Studio ausführen können. 

In Cloud Explorer wird Folgendes unterstützt:

* Ansichten "Ressourcengruppe" und "Ressourcentyp" von Azure-Ressourcen 
* Suchen nach Ressourcen anhand des Namens (verfügbar in der Ansicht "Ressourcentyp")
* Unterstützung für Abonnements und Ressourcen mit rollenbasierter Access Control (RBAC) 
* Integrierter Bereich "Aktion", in dem entwicklerbezogene spezifische Aktionen für ausgewählte Ressourcen angezeigt werden. Beispiel: Remotedebugger für mit dem Ressourcen-Manager-Stapel erstellte virtuelle Computer anfügen, Diagnosedaten für virtuelle Computer anzeigen usw.
* Integrierter Bereich "Eigenschaften", in dem entwicklerbezogene Eigenschaften angezeigt werden, die häufig beim Entwickeln und Testen benötigt werden. 
* Schnelles Wechseln des Kontos beim Auflisten von Ressourcen (über den Befehl "Einstellungen" in der Symbolleiste) 
* Filtern von Abonnements beim Auflisten von Ressourcen (über den Befehl "Einstellungen" in der Symbolleiste) 
* Deep-Links zum Azure-Portal für die Verwaltung von Ressourcen und Ressourcengruppen 

### <a name="azure-resource-manager-tools"></a>Azure-Ressourcen-Manager-Tools
Die Azure-Ressourcen-Manager-Tools wurden so aktualisiert, dass die rollenbasierte Access Control (RBAC) und neue Abonnementtypen unterstützt werden.  In diesen Änderungen ist neben dem klassischen Speicher auch die Möglichkeit enthalten, mithilfe neuer Speicherkonten bei der Bereitstellung Artefakte zu speichern.  

Wenn Sie ein Azure-Ressourcengruppenprojekt aus einer früheren SDK-Version mit dem SDK 2.7 verwenden, ist bei der Bereitstellung mithilfe eines neuen Speicherkontos anstatt mit einem klassischen Speicher ein neues Bereitstellungsskript erforderlich.  Bevor Änderungen an dem Projekt vorgenommen werden, werden Sie aufgefordert, das neue Skript hinzuzufügen.  Das alte Skript wird umbenannt, und Sie müssen alle Änderungen an dem neuen Skript manuell vornehmen.

### <a name="storage-explorer-tools"></a>Speicher-Explorer-Tools
* Unterstützung für das Anzeigen von Anfügeblobs. Weitere Informationen finden Sie in [diesem Blogbeitrag](http://blogs.msdn.com/b/windowsazurestorage/archive/2015/04/13/introducing-azure-storage-append-blob.aspx)(in englischer Sprache). 
* Unterstützung für das Anzeigen von Storage Premium-Konten über Server-Explorer. In Server-Explorer werden nur Seitenblobs für Storage Premium-Konten angezeigt, da sie als einziger Typ in Storage Premium-Konten unterstützt werden.

### <a name="azure-data-factory-tools-for-visual-studio"></a>Azure Data Factory-Tools für Visual Studio
Einführung von **Azure Data Factory-Tools** für Visual Studio. Es folgt eine Aufstellung der aktivierten Funktionen. Weitere Informationen finden Sie in [diesem Blog](http://go.microsoft.com/fwlink/?LinkId=617530) .

* **Vorlagenbasierte Dokumenterstellung**: Sie können Vorlagen basierend auf Anwendungsfällen, Datenverschiebungsvorlagen oder Datenverarbeitungsvorlagen auswählen, um eine End-to-End-Datenintegrationslösung bereitzustellen, und so schnell Ihre Arbeit mit Daten Factory beginnen. 
* **Integration im Projektmappen-Explorer zum Erstellen und Bereitstellen von Data Factory-Entitäten:** Pipelines und zugehörige Entitäten können als Visual Studio-Projekte erstellt und bereitgestellt werden. 
* **Integration in der Diagrammansicht für visuelle Interaktion während der Erstellung**: Pipelines und DataSets können über die Diagrammansicht visuell erstellt werden. 
* **Integration im Server-Explorer zum Durchsuchen von und Interagieren mit bereits bereitgestellten Entitäten**: Im Server-Explorer können Sie bereits bereitgestellte Data Factorys und zugehörige Entitäten durchsuchen. Sie können eine bereitgestellte Data Factory oder jede gewünschte Entität (Pipeline, verknüpfter Dienst, DataSets) in Ihr Projekt importieren. 
* **JSON-Bearbeitung mit Schemaüberprüfung und IntelliSense**: Mit IntelliSense und der Schemaüberprüfung können Sie JSON-Dokumente von Data Factory-Entitäten effektiv konfigurieren und bearbeiten. 
* **Veröffentlichung in mehreren Umgebungen**: Sie können erstellte Pipelines für die Entwicklungs-, Test- oder Produktionsumgebung veröffentlichen, indem Sie für jede Umgebung gesonderte Konfigurationsdateien erstellen.
* **Unterstützung für die Pig-, Hive- und .Net-basierte Datenverarbeitung**: Pig- und Hive-Skripts werden in Data Factory-Projekten unterstützt. Unterstützung für Verweise auf C#-Projekte zum Verwalten von .Net-Aktivitäten.

## <a name="azure-sdk-for-net-271"></a>Azure SDK für .NET 2.7.1
Der folgende Abschnitt enthält Updates, die mit dem Azure SDK für .NET 2.7.1 eingeführt wurden.

### <a name="hdinsight-tools"></a>HDInsight-Tools
Eine ausführlichere Erläuterung zu den Updates für die HDInsight-Tools finden Sie in [diesem Blog](http://go.microsoft.com/fwlink/?LinkId=623831)(in englischer Sprache).

* Ansicht für Hive-Auftragsoperatoren (neues Feature)
  
    Um Ihnen das Verständnis der Hive-Abfragen zu erleichtern, wurde die Ansicht für Hive-Auftragsoperatoren als neues Feature hinzugefügt. Um alle Operatoren in einen Scheitelpunkt anzuzeigen, doppelklicken Sie auf die Scheitelpunkte des Auftragsdiagramms. Um weitere Details zu einem bestimmten Operator anzuzeigen, zeigen Sie auf diesen Operator.
* Hive-Fehlermarker (neues Feature)
  
    Damit Sie Grammatikfehler sofort anzeigen können, wurde das Hive-Fehlermarker-Feature hinzugefügt. Außerdem wurden die Fehlermeldungen verbessert. Sie können nun sofort ausführliche Grammatikfehler sehen (bis zu dieser Version mussten Sie ein Hive-Skript an den Cluster übermitteln und einige Zeit warten, bis Sie Details zu der Fehlermeldung erhalten haben).  
* Storm-Topologiediagramm (neues Feature)
  
    Visualisierung ist sehr wichtig, um festzustellen, ob die Topologie wie erwartet funktioniert. In dieser Version wurde eine Visualisierung für Storm-Diagramme hinzugefügt. Sie können die wichtigen Metriken für die Topologie visuell darstellen (eine Farbe gibt z. B. an, ob ein bestimmter Bolt "ausgelastet" oder nicht). Sie können auch auf Bolts/Spouts doppelklicken, um weitere Details anzuzeigen.
* Unterstützung für HDInsight-Cluster, die im Azure-Portal erstellt wurden (Programmfehlerbehebung)
  
    Sie können nun Visual Studio zum Anzeigen und Übermitteln von Aufträgen an alle HDInsight-Cluster verwenden, unabhängig davon, wo der Cluster erstellt wurde.
* Mehr IntelliSense-Unterstützung und schnelleres Laden von Hive Metadaten (Verbesserung)
  
    IntelliSense wurde verbessert, indem weitere benutzerfreundliche Vorschläge hinzugefügt wurden. Beispielsweise können in IntelliSense jetzt auch Tabellenaliase vorgeschlagen werden, damit Sie Ihre Abfrage leichter schreiben können. Darüber hinaus haben wir das Laden von Hive-Metadaten verbessert, sodass es nur noch einige Sekunden dauert, bis alle Datenbanken, Tabellen und Spalten des Hive-Metastores aufgelistet werden.

Eine ausführlichere Erläuterung zu den Updates für die HDInsight-Tools finden Sie in [diesem Blog](http://go.microsoft.com/fwlink/?LinkId=623831)(in englischer Sprache).

### <a name="improvements-in-visual-studio-2013"></a>Verbesserungen in Visual Studio 2013
* Das Azure SDK 2.7.1 ermöglicht Visual Studio 2013, über die rollenbasierte Zugriffssteuerung, Cloud-Lösungsanbieter und Dreamspark auf Azure-Konten und -Abonnements zuzugreifen.
* Mit Azure SDK 2.7.1 steht das neue Cloud Explorer-Toolfenster jetzt auch in Visual Studio 2013 zur Verfügung.

### <a name="known-issues"></a>Bekannte Probleme
Bei der Installation des Azure SDK 2.6 oder 2.7.1 für Visual Studio Community 2013 unter einem nichtenglischen Betriebssystem wird eventuell eine Warnung angezeigt, dass die englischen und die nichtenglischen Ressourcen von Visual Studio falsch zugeordnet werden könnten. Diese Warnung kann sicher ignoriert werden. Sie tritt nur auf, wenn der Computer keine vorherige Installation von Visual Studio Community 2013 enthält und das SDK unter einem nichtenglischen Betriebssystem installiert wird. Die Warnung wird angezeigt, nachdem das Sprachpaket die RTM-Ressourcen auf Visual Studio angewendet hat, aber bevor das Update 4 angewendet wird. Wenn Sie die Warnung schließen, kann das Sprachpaket fortgesetzt und das Update 4 des Sprachpakets angewendet werden.

LightSwitch-Projekte sind mit dieser Version nicht kompatibel. Dieses Problem wird in der nächsten SDK-Version behoben.

## <a name="also-see"></a>Siehe auch
[Ankündigungsbeitrag zu Azure SDK 2.7.1 (in englischer Sprache)](http://go.microsoft.com/fwlink/?LinkId=623850)

[Ankündigungsbeitrag zu Azure SDK 2.7 (in englischer Sprache)](https://azure.microsoft.com/blog/2015/07/20/announcing-the-azure-sdk-2-7-for-net/)

[Unterstützungs- und Deaktivierungsinformationen zum Azure SDK für .NET und APIs](https://msdn.microsoft.com/library/azure/dn479282.aspx/)

