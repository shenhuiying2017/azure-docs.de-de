---
title: Iteratives Entwickeln und Debuggen in Azure Data Factory | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Data Factory-Pipelines im Azure-Portal iterativ entwickeln und debuggen.
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 05/14/2018
ms.topic: article
ms.service: data-factory
services: data-factory
documentationcenter: ''
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.openlocfilehash: e403afa5c870b2d007a8c5e1d46162cd899ead29
ms.sourcegitcommit: d78bcecd983ca2a7473fff23371c8cfed0d89627
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2018
ms.locfileid: "34164821"
---
# <a name="iterative-development-and-debugging-with-azure-data-factory"></a>Iteratives Entwickeln und Debuggen mit Azure Data Factory

Mithilfe von Azure Data Factory können Sie Data Factory-Pipelines iterativ entwickeln und debuggen.

Das folgende Video enthält eine achtminütige Einführung und Demonstration dieses Features:

> [!VIDEO https://channel9.msdn.com/Shows/Azure-Friday/Iterative-development-and-debugging-with-Azure-Data-Factory/player]

## <a name="iterative-debugging-features"></a>Funktionen für iteratives Debuggen
Mit der Funktion **Debuggen** auf der Pipelinecanvas können Sie Pipelines erstellen und Testläufe ausführen, ohne eine einzige Codezeile schreiben zu müssen.

![Funktion zum Debuggen auf der Pipelinecanvas](media/iterative-development-debugging/iterative-development-image1.png)

Zeigen Sie die Ergebnisse der Testläufe auf der Pipelinecanvas im Fenster **Ausgabe** an.

![Ausgabefenster der Pipelinecanvas](media/iterative-development-debugging/iterative-development-image2.png)

Fügen Sie nach der erfolgreichen Ausführung eines Testlaufs weitere Aktivitäten zur Pipeline hinzu, und setzen Sie das iterative Debuggen fort. Sie können einen aktiven Testlauf auch über **Abbrechen** beenden.

![Abbrechen eines Testlaufs](media/iterative-development-debugging/iterative-development-image3.png)

Beim Ausführen von Testläufen müssen Sie Ihre Änderungen nicht in der Data Factory veröffentlichen, bevor Sie auf **Debuggen** klicken. Dies ist in Szenarien praktisch, bei denen Sie sicherstellen möchten, dass die Änderungen wie erwartet funktionieren, bevor Sie den Data Factory-Workflow aktualisieren.

## <a name="more-info-about-debugging"></a>Weitere Informationen zum Debuggen

1. Die mit der Funktion **Debuggen** initiierten Testläufe sind nicht in der Liste auf der Registerkarte **Überwachen** verfügbar. Es werden nur Testläufe angezeigt, die mithilfe der Trigger **Jetzt auslösen**, **Zeitplan** oder **Rollierendes Fenster** auf der Registerkarte **Überwachen** ausgelöst wurden. Der letzte mit der Funktion **Debuggen** initiierte Testlauf wird im Fenster **Ausgabe** der Pipelinecanvas angezeigt.

2. Durch Auswählen von **Debuggen** wird die Pipeline ausgeführt. Wenn die Pipeline also beispielsweise die copy-Aktivität enthält, werden beim Testlauf Daten aus der Quelle zum Ziel kopiert. Daher wird empfohlen, beim Debuggen Testordner in Ihrer copy-Aktivität und Ihren anderen Aktivitäten zu verwenden. Wechseln Sie nach dem Debuggen der Pipeline zu den Ordnern, die Sie tatsächlich in normalen Vorgängen verwenden möchten.

## <a name="setting-breakpoints-for-debugging"></a>Festlegen von Breakpoints für das Debuggen

Mit Data Factory können Sie das Debuggen auch bis zum Erreichen einer bestimmten Aktivität in der Pipelinecanvas ausführen. Legen Sie einfach einen Breakpoint für die Aktivität fest, bis zu dem der Test ausgeführt werden soll, und klicken Sie auf **Debuggen**. Data Factory stellt sicher, dass die Testläufe nur bis zur Breakpoint-Aktivität auf der Pipelinecanvas ausgeführt werden. Dieses Feature namens *Debug Until* (Debuggen bis) ist nützlich, wenn Sie nicht die gesamte Pipeline, sondern nur eine Teilmenge der Aktivitäten in der Pipeline testen möchten.

![Breakpoints auf der Pipelinecanvas](media/iterative-development-debugging/iterative-development-image4.png)

Um einen Haltepunkt festzulegen, wählen Sie ein Element auf der Pipelinecanvas aus. Eine Option *Debug Until* wird als ein leerer roter Kreis in der oberen rechten Ecke des Elements angezeigt.

![Vor dem Festlegen eines Haltepunkts für das ausgewählte Element](media/iterative-development-debugging/iterative-development-image5.png)

Nachdem Sie die Option *Debug Until* ausgewählt haben, ändert sich der leere Kreis in einen ausgefüllten roten Kreis, um anzugeben, dass der Breakpoint aktiviert ist.

![Nach dem Festlegen eines Haltepunkts für das ausgewählte Element](media/iterative-development-debugging/iterative-development-image6.png)

## <a name="next-steps"></a>Nächste Schritte
[Continuous Integration und Continuous Deployment in Azure Data Factory](continuous-integration-deployment.md)
