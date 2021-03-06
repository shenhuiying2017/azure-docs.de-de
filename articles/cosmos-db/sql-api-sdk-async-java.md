---
title: 'Azure Cosmos DB: SQL Async Java-API, SDK und Ressourcen | Microsoft-Dokumentation'
description: Wichtige Informationen zur SQL Async Java-API und zum SDK, einschließlich Veröffentlichungsterminen, Deaktivierungsterminen und Änderungen an den einzelnen Versionen des Azure Cosmos DB SQL Async Java SDK.
services: cosmos-db
documentationcenter: java
author: SnehaGunda
manager: kfile
ms.assetid: a452ffa2-c15d-4b0a-a8c1-ec9b750ce52b
ms.service: cosmos-db
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: java
ms.topic: article
ms.date: 05/18/2018
ms.author: sngun
ms.openlocfilehash: 9dae401bc007b78d8ee3c6993735650e3b26b9d1
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2018
ms.locfileid: "34359525"
---
# <a name="azure-cosmos-db-async-java-sdk-for-sql-api-release-notes-and-resources"></a>Azure Cosmos DB Async Java SDK für SQL-API: Versionshinweise und Ressourcen
> [!div class="op_single_selector"]
> * [.NET](sql-api-sdk-dotnet.md)
> * [.NET-Änderungsfeed](sql-api-sdk-dotnet-changefeed.md)
> * [.NET Core](sql-api-sdk-dotnet-core.md)
> * [Node.js](sql-api-sdk-node.md)
> * [Async Java](sql-api-sdk-async-java.md)
> * [Java](sql-api-sdk-java.md)
> * [Python](sql-api-sdk-python.md)
> * [REST](https://docs.microsoft.com/rest/api/cosmos-db/)
> * [REST-Ressourcenanbieter](https://docs.microsoft.com/rest/api/cosmos-db-resource-provider/)
> * [SQL](https://msdn.microsoft.com/library/azure/dn782250.aspx)
> * [BulkExecutor: .NET](sql-api-sdk-bulk-executor-dot-net.md)
> * [BulkExecutor: Java](sql-api-sdk-bulk-executor-java.md)

Das Async Java SDK für die SQL-API unterscheidet sich vom Java SDK für die SQL-API dahingehend, dass es asynchrone Vorgänge mit Unterstützung der [Netty-Bibliothek](http://netty.io/) bereitstellt. Das bereits vorhandene [Java SDK für die SQL-API](sql-api-sdk-java.md) unterstützt asynchrone Vorgänge nicht. 

<table>

<tr><td>**SDK-Download**</td><td>[Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-cosmosdb)</td></tr>

<tr><td>**API-Dokumentation**</td><td>[Java-API-Referenzdokumentation](https://azure.github.io/azure-cosmosdb-java/)</td></tr>

<tr><td>**Am SDK mitwirken**</td><td>[GitHub](https://github.com/Azure/azure-cosmosdb-java)</td></tr>

<tr><td>**Erste Schritte**</td><td>[Erste Schritte mit dem Async Java SDK](https://github.com/Azure-Samples/azure-cosmos-db-sql-api-async-java-getting-started)</td></tr>

<tr><td>**Codebeispiel**</td><td>[Github](https://github.com/Azure/azure-cosmosdb-java#usage-code-sample)</td></tr>

<tr><td>**Leistungstipps**</td><td>[Github-Infodatei](https://github.com/Azure/azure-cosmosdb-java#guide-for-prod)</td></tr>

<tr><td>**Unterstützte Mindestlaufzeit**</td><td>[JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)</td></tr>
</table></br>

## <a name="release-notes"></a>Versionshinweise

### <a name="a-name102102"></a><a name="1.0.2"/>1.0.2
* Unterstützung für die Richtlinie des eindeutigen Index wurde hinzugefügt.
* Unterstützung für die Begrenzung der Antwort bezüglich der Größe von Fortsetzungstoken in Feedoptionen wurde hinzugefügt.
* Unterstützung für die Partitionsaufteilung in partitionsübergreifenden Abfragen wurde hinzugefügt.
* Fehler in der JSON-Zeitstempelserialisierung wurde behoben ([github #32](https://github.com/Azure/azure-cosmosdb-java/issues/32)).
* Fehler in der JSON-Enumerationsserialisierung wurde behoben.
* Fehler bei der Verwaltung von Dokumenten mit einer Größe von 2 MB wurde behoben ([github #33](https://github.com/Azure/azure-cosmosdb-java/issues/33)).
* Abhängigkeit von com.fasterxml.jackson.core:jackson-databind wurde auf 2.9.5 aufgrund eines Fehlers aktualisiert ([jackson-databind: github #1599](https://github.com/FasterXML/jackson-databind/issues/1599)).
* Abhängigkeit von rxjava-extras wurde auf 0.8.0.17 aufgrund eines Fehlers aktualisiert ([rxjava-extras: github #30](https://github.com/davidmoten/rxjava-extras/issues/30)).
* Die Metadatenbeschreibung in der Pom-Datei wurde aktualisiert, damit sie mit dem Rest der Dokumentation übereinstimmt.
* Syntaxverbesserung ([github #41](https://github.com/Azure/azure-cosmosdb-java/issues/41)), ([github 40 #](https://github.com/Azure/azure-cosmosdb-java/issues/40))

### <a name="a-name101101"></a><a name="1.0.1"/>1.0.1
* Rückstauunterstützung in Abfrage hinzugefügt
* Unterstützung für die ID des Partitionsschlüsselbereichs in der Abfrage hinzugefügt
* Korrektur, um größeres Fortsetzungstoken im Anforderungsheader zu ermöglichen (Fehlerbehebung: GitHub Nr. 24).
* Netty-Abhängigkeit aktualisiert auf 4.1.22. Sicherstellung, dass JVM nach Abschluss des Hauptthreads herunterfährt.
* Korrektur, um beim Lesen der Masterressourcen die Übergabe des Sitzungstokens zu verhindern
* Weitere Beispiele hinzugefügt
* Weitere Benchmarktestszenarien hinzugefügt
* Java-Headerdateien zur ordnungsgemäßen Erstellung von Java-Dokumenten korrigiert

### <a name="a-name100100"></a><a name="1.0.0"/>1.0.0
* Allgemein verfügbares SDK mit End-to-End-Unterstützung für nicht blockierende EA-Vorgänge mit der [Netty-Bibliothek](http://netty.io/) im Gatewaymodus 

## <a name="release-and-retirement-dates"></a>Veröffentlichungs- und Deaktivierungstermine
Wenn Microsoft ein SDK deaktiviert, werden Sie mindestens **12 Monate** vorher benachrichtigt, um einen reibungslosen Übergang zu einer neueren/unterstützten Version zu gewährleisten.

Neue Features, Funktionen und Optimierungen werden nur zum aktuellen SDK hinzugefügt. Daher wird empfohlen, stets so früh wie möglich ein Upgrade auf die aktuelle SDK-Version auszuführen.

Anforderungen an Cosmos DB mithilfe eines deaktivierten SDK werden vom Dienst abgelehnt.

<br/>

| Version | Herausgabedatum | Deaktivierungstermine |
| --- | --- | --- |
| [1.0.2](#1.0.2) |18. Mai 2018|--- |
| [1.0.1](#1.0.1) |20. April 2018|--- |
| [1.0.0](#1.0.0) |27. Februar 2018|--- |

## <a name="faq"></a>Häufig gestellte Fragen
[!INCLUDE [cosmos-db-sdk-faq](../../includes/cosmos-db-sdk-faq.md)]

## <a name="see-also"></a>Weitere Informationen
Weitere Informationen zu Cosmos DB finden Sie auf der Seite zum Dienst [Microsoft Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/).

