---
title: Überwachen der Datenbanknutzung mit Intelligent Insights – Azure SQL-Datenbank | Microsoft-Dokumentation
description: Die in Intelligent Insights von Azure SQL-Datenbank integrierte Logik überwacht kontinuierlich die Datenbanknutzung durch künstliche Intelligenz und ermittelt Störungen, die zu schlechter Leistung führen.
services: sql-database
author: danimir
manager: craigg
ms.reviewer: carlrab
ms.service: sql-database
ms.custom: monitor & tune
ms.topic: article
ms.date: 04/01/2018
ms.author: v-daljep
ms.openlocfilehash: f3ace9d178fdfa90130e4436722e1e36cedc7e50
ms.sourcegitcommit: 3a4ebcb58192f5bf7969482393090cb356294399
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2018
---
# <a name="intelligent-insights"></a>Intelligent Insights

Intelligent Insights von Azure SQL-Datenbank informiert Sie über Ihre Datenbankleistung.

Die in Intelligent Insights integrierte Logik überwacht kontinuierlich die Datenbanknutzung durch künstliche Intelligenz und ermittelt Störungen, die zu mangelhafter Leistung führen. Nach dem Ermitteln wird eine detaillierte Analyse durchgeführt, die ein Diagnoseprotokoll mit einer intelligenten Bewertung des Problems generiert. Die Bewertung besteht aus einer Analyse der Grundursache des Leistungsproblems der Datenbank und nach Möglichkeit Empfehlungen für Leistungsverbesserungen. 

## <a name="what-can-intelligent-insights-do-for-you"></a>Was kann Intelligent Insights für Sie tun?

Bei Intelligent Insights handelt es sich um eine einzigartige Funktion der in Azure integrierten Logik, die folgende Werte bereitstellt:

- Proaktive Überwachung
- Angepasste Einblicke in die Leistung
- Frühe Erkennung von Leistungsminderungen der Datenbank
- Analyse der Grundursache der erkannten Probleme
- Empfehlungen für Leistungsverbesserungen
- Funktion für das horizontale Hochskalieren von einigen Hunderttausend Datenbanken
- Positive Auswirkung auf DevOps-Ressourcen und die Gesamtkosten

## <a name="how-does-intelligent-insights-work"></a>Wie funktioniert Intelligent Insights?

Intelligent Insights analysiert die Leistung von SQL-Datenbank, indem die Datenbankworkload der letzten Stunde mit der Baselineworkload der letzten sieben Tage verglichen wird. Die Datenbankworkload besteht aus den Abfragen, die für die Datenbankleistung am wichtigsten sind, etwa die am meisten wiederholten und die größten Abfragen. Da jede Datenbank durch ihre Struktur, ihre Daten, die Nutzung und die Anwendung eindeutig ist, ist jede generierte Workloadbaseline spezifisch und eindeutig für eine einzelne Instanz. Intelligent Insights überwacht unabhängig von der Workloadbaseline auch die absoluten Betriebsschwellenwerte und erkennt Probleme mit übermäßigen Wartezeiten, kritische Ausnahmen und Probleme mit der Abfrageparametrisierung, die sich auf die Leistung auswirken können.

Nachdem eine beeinträchtigte Leistung aus mehreren erfassten Metriken mithilfe von künstlicher Intelligenz erkannt wird, erfolgt eine Analyse. Ein Diagnoseprotokoll wird erzeugt und ermöglicht einen intelligenten Einblick in die Vorgänge mit Ihrer Datenbank. Durch Intelligent Insights kann das Problem mit der Datenbankleistung vom ersten Auftreten bis hin zu dessen Behebung leicht nachverfolgt werden. Jedes ermittelte Problem wird während seines Lebenszyklus von der ersten Erkennung des Problems und der Überprüfung der Leistungssteigerung bis hin zur Behebung nachverfolgt. Updates werden im Diagnoseprotokoll alle 15 Minuten bereitgestellt. 

![Workflow der Datenbankleistungsanalyse](./media/sql-database-intelligent-insights/intelligent-insights-concept.png)

Die Metriken zum Messen und Erkennen von Leistungsproblemen bei Datenbanken basieren auf der Abfragedauer, Anforderungen mit Zeitüberschreitung, übermäßigen Wartezeiten und fehlerhaften Anforderungen. Weitere Informationen zu Metriken finden Sie im Abschnitt [Erkennungsmetriken](sql-database-intelligent-insights.md#detection-metrics) dieses Dokuments.

Identifizierte Leistungseinbußen von SQL-Datenbank werden im Diagnoseprotokoll mit intelligenten Einträgen aufgezeichnet, die folgende Eigenschaften enthalten:

| Eigenschaft             | Details              |
| :------------------- | ------------------- |
| Datenbankinformationen | Metadaten zu einer Datenbank, für die ein Einblick erkannt wurde, z.B. ein Ressourcen-URI |
| Beobachteter Zeitbereich | Start- und Endzeit für den Zeitraum des erkannten Einblicks |
| Betroffene Metriken | Metriken, die das Generieren eines Einblicks verursachten: <ul><li>Erhöhte Abfragedauer [Sekunden]</li><li>Übermäßige Wartezeiten [Sekunden]</li><li>Zeitüberschreitung bei Anforderungen [Sekunden]</li><li>Fehler bei Anforderungen [Sekunden]</li></ul>|
| Auswirkungswert | Gemessener Wert einer Metrik |
| Betroffene Abfragen und Fehlercodes | Abfragehash oder Fehlercode Diese können für eine einfache Korrelation mit betroffenen Abfragen verwendet werden. Metriken werden bereitgestellt, die aus erhöhten Abfragedauern, Wartezeiten, Zeitüberschreitungen oder Fehlercodes bestehen. |
| Erkennungen | Während eines Ereignisses wurde eine Erkennung auf der Datenbank identifiziert. Es gibt 15 Erkennungsmuster. Nähere Informationen finden Sie unter [Troubleshoot database performance issues with Intelligent Insights (Behandeln von Problemen mit der Leistung mithilfe von Intelligent Insights)](sql-database-intelligent-insights-troubleshoot-performance.md). |
| Analyse der Grundursache | Die Analyse der Grundursache des Problems, die in einem von Menschen lesbaren Format identifiziert wurde. Einige Einblicke enthalten nach Möglichkeit Empfehlungen zur Leistungsverbesserung. |
|||

Im Diagnoseprotokoll aufgezeichnete Leistungsprobleme werden mit einem der drei Statuswerte im Lebenszyklus eines Problems gekennzeichnet: „Aktiv“, „Wird überprüft“, „Abgeschlossen“. Nachdem ein Leistungsproblem erkannt und von der in SQL-Datenbank integrierten Logik als vorhanden angesehen wird, wird das Problem als „Aktiv“ gekennzeichnet. Wenn das Problem als gemindert angesehen wird, wird es überprüft, und der Status des Problems wird in „Wird überprüft“ geändert. Nachdem die in SQL-Datenbank integrierte Logik das Problem als gelöst ansieht, wird der Status des Problems als „Abgeschlossen“ gekennzeichnet.

## <a name="use-intelligent-insights"></a>Verwenden von Intelligent Insights

Intelligent Insights ist ein intelligentes Leistungsdiagnoseprotokoll. Es kann in andere Produkte zur Nutzung sowie in spezielle Anwendungen wie Azure Log Analytics, Azure Event Hubs und Azure Storage oder in Produkte von Drittanbietern integriert werden. 

Intelligent Insights in Verbindung mit Azure Log Analytics wird üblicherweise verwendet, um die Einblicke über einen Webbrowser anzuzeigen und ist vielleicht eine der einfachsten Möglichkeiten, den Einstieg in das Arbeiten mit dem Produkt zu finden. Intelligent Insights zusammen mit Azure Event Hubs wird normalerweise verwendet, um benutzerdefinierte Überwachungs- und Warnungsszenarien zu konfigurieren. Intelligent Insights zusammen mit Azure Storage wird üblicherweise für benutzerdefinierte Anwendungsentwicklung verwendet, so z. B. benutzerdefinierte Berichterstellung oder vielleicht Datenarchivierung und Datenabruf.

Die Integration von Intelligent Insights in andere Produkte, etwa Azure Log Analytics, Azure Event Hubs, Azure Storage oder Produkte von Drittanbietern, zur Nutzung wird vorgenommen, indem zunächst die Intelligent Insights-Protokollierung (SQLInsights-Protokoll) und anschließend die Intelligent Insights-Protokolldaten konfiguriert werden, die an eines dieser Produkte übertragen werden sollen. Weitere Informationen dazu, wie die Intelligent Insights-Protokollierung aktiviert wird und wie Protokolldaten konfiguriert werden, sodass sie an ein nutzendes Produkt übertragen werden, finden Sie unter [Protokollierung von Metriken und Diagnosen für Azure SQL-Datenbank](sql-database-metrics-diag-logging.md). 

Einen praktischen Überblick, wie Intelligent Insights mit Azure Log Analytics und für typische Anwendungsszenarien verwendet wird, finden Sie im eingebetteten Video:


> [!VIDEO https://channel9.msdn.com/Shows/Azure-Friday/Get-Intelligent-Insights-for-Improving-Azure-SQL-Database-Performance/player]
>

Intelligent Insights glänzt bei der Erkennung und Fehlerbehebung von Leistungsproblemen der SQL-Datenbank. Informationen, wie Intelligent Insights verwendet werden kann, um SQL-Datenbankprobleme zu behandeln, finden Sie unter [Behandeln von Problemen mit der Leistung von Azure SQL-Datenbank mithilfe von Intelligent Insights](sql-database-intelligent-insights-troubleshoot-performance.md).

## <a name="set-up-intelligent-insights-with-log-analytics"></a>Einrichten von Intelligent Insights mit Log Analytics 

Log Analytics bietet zusätzlich zu den Diagnoseprotokolldaten von Intelligent Insights Funktionen für die Berichterstellung und für Warnungen.

Um Intelligent Insights mit Log Analytics zu verwenden, konfigurieren Sie Intelligent Insights-Protokolldaten so, dass sie an Log Analytics übertragen werden. Informationen hierzu finden Sie unter [Protokollierung von Metriken und Diagnosen für Azure SQL-Datenbank](sql-database-metrics-diag-logging.md). 

Im Folgenden Beispiel wird ein Intelligent Insights-Bericht in Azure SQL-Analyse dargestellt:

![Intelligent Insights-Bericht](./media/sql-database-intelligent-insights/intelligent-insights-azure-sql-analytics.png)

Nachdem das Diagnoseprotokoll von Intelligent Insights dafür konfiguriert wurde, Daten an SQL-Analyse zu streamen, können Sie [die SQL-Datenbank mithilfe von SQL-Analyse überwachen](../log-analytics/log-analytics-azure-sql.md).

## <a name="set-up-intelligent-insights-with-event-hubs"></a>Einrichten von Intelligent Insights mit Event Hubs

Um Intelligent Insights mit Event Hubs zu verwenden, konfigurieren Sie Intelligent Insights-Protokolldaten so, dass sie an Event Hubs übertragen werden. Informationen hierzu finden Sie unter [Streamen von Azure-Diagnoseprotokollen an einen Event Hubs-Namespace](../monitoring-and-diagnostics/monitoring-stream-diagnostic-logs-to-event-hubs.md).

Informationen zum Verwenden von Event Hubs, um benutzerdefinierte Überwachungen und Warnungen einzurichten, finden Sie unter [Welche Vorgänge können mit Metriken und Diagnoseprotokollen in Event Hubs ausgeführt werden?](sql-database-metrics-diag-logging.md#what-to-do-with-metrics-and-diagnostics-logs-in-event-hubs). 

## <a name="set-up-intelligent-insights-with-storage"></a>Einrichten von Intelligent Insights mit Storage

Um Intelligent Insights mit Storage zu verwenden, konfigurieren Sie Intelligent Insights-Protokolldaten so, dass sie an Storage übertragen werden. Informationen hierzu finden Sie unter [Streamen in den Speicher](sql-database-metrics-diag-logging.md#stream-into-storage).

## <a name="custom-integrations-of-intelligent-insights-log"></a>Benutzerdefinierte Integrationen von Intelligent Insights-Protokollen

Informationen, wie Intelligent Insights mit Tools von Drittanbietern oder zum Entwickeln von benutzerdefinierten Warnungen und Überwachungen verwendet werden kann, finden Sie unter [Verwenden des Intelligent Insights-Diagnoseprotokolls für die Leistung von Azure SQL-Datenbank](sql-database-intelligent-insights-use-diagnostics-log.md).

## <a name="detection-metrics"></a>Erkennungsmetriken

Metriken, die für Erkennungsmodelle verwendet werden, die intelligente Einblicke generieren, basieren auf der Überwachung der:

- Abfragedauer
- Anforderungen mit Zeitüberschreitung
- Übermäßigen Wartezeiten
- Fehlerhaften Anforderungen

Die Abfragedauer und Anforderungen mit Zeitüberschreitung werden als primäre Modelle beim Erkennen von Problemen mit der Workloadleistung der Datenbank verwendet. Sie werden verwendet, da sie direkt die Vorgänge in der Workload messen. Zum Erkennen aller möglichen Fälle von Leistungsminderungen der Workload werden übermäßige Wartezeiten und fehlerhafte Anforderungen als zusätzliche Modelle verwendet, die Probleme mit Auswirkung auf die Leistung der Workload angeben.

Das System berücksichtigt automatisch Änderungen an der Workload und Änderungen an der Anzahl von Abfrageanforderungen, die an die Datenbank gesendet werden, um die normalen und abweichenden Schwellenwerte der Datenbankleistung dynamisch zu bestimmen.

Alle Metriken werden in verschiedenen Beziehungen über ein wissenschaftlich abgeleitetes Datenmodell berücksichtigt, das die erkannten Leistungsprobleme kategorisiert. Über Intelligent Insights bereitgestellte Informationen umfassen:

* Details zum erkannten Leistungsproblem 
* Eine Analyse der Grundursache des erkannten Problems 
* Empfehlungen zu möglichen Verbesserungen der Leistung der überwachten SQL-Datenbank

## <a name="query-duration"></a>Abfragedauer

Das Modell für die Leistungsminderung durch die Abfragedauer analysiert einzelne Abfragen und erkennt erhöhte Kompilier- und Ausführungszeiten für eine Abfrage im Vergleich zur Leistungsbaseline.

Wenn die in SQL-Datenbank integrierte Logik eine beträchtliche Zunahme der Kompilier- oder Ausführungszeit einer Abfrage erkennt, die die Workloadleistung beeinträchtigt, werden diese Abfragen mit Leistungsminderungsproblemen bei der Abfrage gekennzeichnet. 

Das Intelligent Insights-Diagnoseprotokoll gibt den Abfragehash der Abfrage aus, deren Leistung beeinträchtigt ist. Der Abfragehash gibt an, ob die Leistungsminderung auf eine Erhöhung der Kompilierungs- oder der Ausführungsdauer und dadurch eine Erhöhung der Abfragedauer zurückzuführen ist.

## <a name="timeout-requests"></a>Anforderungen mit Zeitüberschreitung

Das Modell für die Leistungsminderung durch Abfragen mit Zeitüberschreitung analysiert einzelne Abfragen und erkennt erhöhte Zeitüberschreitungen auf Ausführungsebene der Abfragen sowie die gesamten Zeitüberschreitungen von Anforderungen auf Datenbankebene im Vergleich zum Zeitraum der Leistungsbaseline.

Bei einigen Abfragen tritt eventuell eine Zeitüberschreitung auf, bevor sie in die Ausführungsphase gelangen. Mithilfe der Mittelwerte der abgebrochenen Worker im Vergleich zu den stattgefundenen Anforderungen misst und analysiert die in SQL-Datenbank integrierte Logik alle Abfragen, die die Datenbank erreicht haben, unabhängig davon, ob sie in die Ausführungsphase gelangt sind. 

Nachdem die Anzahl von Zeitüberschreitungen für ausgeführte Abfragen oder von abgebrochenen Anforderungsworkern den vom System verwalteten Schwellenwert überschreitet, wird ein Diagnoseprotokoll mit intelligenten Einblicken aufgefüllt.

Die generierten Einblicke enthalten die Anzahl der Anforderungen mit Zeitüberschreitungen und die Anzahl der Abfragen mit Zeitüberschreitungen. Es wird eine Angabe bereitgestellt, ob die Leistungsminderung im Zusammenhang mit der vermehrten Zeitüberschreitungen in der Ausführungsphase steht, oder die allgemeine Datenbankebene wird bereitgestellt. Wenn die vermehrten Zeitüberschreitungen als relevant für die Datenbankleistung angesehen werden, werden diese Abfragen mit Leistungsproblemen durch Zeitüberschreitung gekennzeichnet. 

## <a name="excessive-wait-times"></a>Übermäßige Wartezeiten

Das Modell für übermäßige Wartezeiten überwacht einzelne Datenbankabfragen. Es erkennt ungewöhnlich hohe Wartezeiten für Abfragen, die die vom System verwalteten absoluten Schwellenwerte überschritten haben. Die folgenden Metriken für übermäßige Abfragewartezeiten werden mithilfe des neuen SQL Server-Features beobachtet, der Wartestatistiken des Abfragespeichers (sys.query_store_wait_stats):

- Erreichen von Ressourcengrenzwerten
- Erreichen von Ressourcenbegrenzungen von Pools für elastische Datenbanken
- Übermäßige Anzahl von Worker- oder Sitzungsthreads
- Übermäßiges Sperren der Datenbank
- Hohe Arbeitsspeicherauslastung
- Andere Wartestatistiken

Das Erreichen von Ressourcengrenzwerten von Abonnements oder Pools für elastische Datenbanken weist darauf hin, dass die Nutzung der verfügbaren Ressourcen eines Abonnements oder eines Pools für elastische Datenbanken absolute Schwellenwerte überschritten hat. Diese Statistiken zeigen eine Minderung der Workloadleistung an. Eine übermäßige Anzahl von Worker- oder Sitzungsthreads weist darauf hin, dass einige initiierte Workerthreads oder Sitzungen absolute Schwellenwerte überschritten haben. Diese Statistiken zeigen eine Minderung der Workloadleistung an.

Ein übermäßiges Sperren der Datenbank weist darauf hin, dass die Anzahl von Sperren für eine Datenbank absolute Schwellenwerte überschritten hat. Diese Statistik zeigt eine Minderung der Workloadleistung an. Bei einer hohen Arbeitsspeicherauslastung hat die Anzahl der Threads, die eine Speicherzuweisung angefordert haben, einen absoluten Schwellenwert überschritten. Diese Statistik zeigt eine Minderung der Workloadleistung an.

Andere Wartestatistiken geben an, dass verschiedene Metriken, die über die Wartestatistiken des Abfragespeichers gemessen wurden, einen absoluten Schwellenwert überschritten haben. Diese Statistiken zeigen eine Minderung der Workloadleistung an.

Nachdem übermäßige Wartezeiten erkannt wurden, gibt das Diagnoseprotokoll von Intelligent Insights abhängig von den verfügbaren Daten die Hashes von beeinträchtigenden und beeinträchtigten Abfragen aus, deren Leistung gemindert ist, sowie Details zu den Metriken, die die Wartezeiten der Abfragen in der Ausführung verursachen, sowie die gemessenen Wartezeiten.

## <a name="errored-requests"></a>Fehlerhafte Anforderungen

Das Modell für Leistungsminderung durch fehlerhafte Anforderungen überwacht einzelne Abfragen und erkennt eine Erhöhung der Anzahl von Abfragen, bei denen im Vergleich zum Zeitraum der Baseline Fehler aufgetreten sind. Das Modell überwacht auch kritische Ausnahmen, die von der in SQL-Datenbank integrierten Logik verwalteten absoluten Schwellenwerte überschritten haben. Das System berücksichtigt automatisch die Anzahl der Abfrageanforderungen für Workloadänderungen im überwachten Zeitraum, die an die Datenbank und die Konten gesendet wurden.

Wenn die gemessene Erhöhung der Anforderungen mit Fehlern bezogen auf Gesamtzahl der gesendeten Anforderungen als relevant für die Workloadleistung angesehen wird, werden die betroffenen Abfragen mit Problemen mit der Leistungsminderung durch fehlerhafte Anforderungen gekennzeichnet.

Das Intelligent Insights-Protokoll gibt die Anzahl der Anforderungen mit Fehlern zurück. Es gibt an, ob die Leistungsminderung zu einem Anstieg an Anforderungen mit Fehlern oder zum Überschreiten eines überwachten kritischen Schwellenwerts geführt hat, und weist die gemessene Zeit der Leistungsminderung auf. 

Wenn eine der überwachten kritischen Ausnahmen die vom System verwalteten absoluten Schwellenwerte überschreitet, wird ein intelligenter Einblick mit Details zu den kritischen Ausnahmen generiert.

## <a name="next-steps"></a>Nächste Schritte
* Erfahren Sie mehr über das [Behandeln von Problemen mit der Leistung von SQL-Datenbank mithilfe von Intelligent Insights](sql-database-intelligent-insights-troubleshoot-performance.md).
* Erfahren Sie mehr über das Verwenden des [Intelligent Insights-Diagnoseprotokolls für die Leistung von SQL-Datenbank](sql-database-intelligent-insights-use-diagnostics-log.md).
* Erfahren Sie mehr über das [Überwachen von SQL-Datenbank mithilfe von SQL-Analyse](../log-analytics/log-analytics-azure-sql.md).
* Erfahren Sie mehr über das [Erfassen und Nutzen von Protokolldaten aus Ihren Azure-Ressourcen](../monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs.md).


