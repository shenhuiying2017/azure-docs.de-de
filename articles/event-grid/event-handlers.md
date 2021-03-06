---
title: Azure Event Grid-Ereignishandler
description: Informationen zu unterstützten Ereignishandlern für Azure Event Grid
services: event-grid
author: tfitzmac
manager: timlt
ms.service: event-grid
ms.topic: conceptual
ms.date: 05/04/2018
ms.author: tomfitz
ms.openlocfilehash: 996bd4b3497861a3bfcbfecebe18a6936f487028
ms.sourcegitcommit: 688a394c4901590bbcf5351f9afdf9e8f0c89505
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/18/2018
ms.locfileid: "34301766"
---
# <a name="event-handlers-in-azure-event-grid"></a>Ereignishandler in Azure Event Grid

Ein Ereignishandler ist der Ort, an den das Ereignis gesendet wird. Der Handler ergreift zur Verarbeitung des Ereignisses weitere Maßnahmen. Mehrere Azure-Dienste werden automatisch für die Behandlung von Ereignissen konfiguriert. Sie können aber auch einen beliebigen Webhook für die Behandlung von Ereignissen verwenden. Der Webhook muss zum Behandeln von Ereignissen nicht in Azure gehostet werden.

Dieser Artikel enthält Links zu Inhalten für die einzelnen Ereignishandler.

## <a name="azure-automation"></a>Azure-Automatisierung

Verwenden Sie Azure Automation für die Verarbeitung von Ereignissen mit automatisierten Runbooks.

|Titel  |BESCHREIBUNG  |
|---------|---------|
|[Integration von Azure Automation mit Event Grid und Microsoft Teams](ensure-tags-exists-on-new-virtual-machines.md) |Erstellen Sie einen virtuellen Computer, der ein Ereignis gesendet. Das Ereignis löst ein Automation-Runbook, das den virtuellen Computer markiert, sowie eine Nachricht aus, die an einen Microsoft Teams-Kanal gesendet wird. |

## <a name="azure-functions"></a>Azure-Funktionen

Verwenden Sie Azure Functions für eine serverlose Reaktion auf Ereignisse.

|Titel  |BESCHREIBUNG  |
|---------|---------|
| [Event Grid-Trigger für Azure Functions](../azure-functions/functions-bindings-event-grid.md) | Übersicht über die Verwendung des Event Grid-Triggers in Functions. |
| [Automatisieren der Größenänderung von hochgeladenen Images per Event Grid](resize-images-on-storage-blob-upload-event.md) | Benutzer laden Bilder über eine Web-App in ein Speicherkonto hoch. Wenn ein Speicherblob erstellt wird, sendet Event Grid ein Ereignis an die Funktions-App, die daraufhin die Größe des hochgeladenen Bilds anpasst. |
| [Streamen von Big Data in ein Data Warehouse](event-grid-event-hubs-integration.md) | Wenn Event Hubs eine Capture-Datei erstellt, sendet Event Grid ein Ereignis an eine Funktions-App. Die App ruft die Capture-Datei ab und migriert Daten zu einem Data Warehouse. |
| [Beispiele für die Integration von Azure Service Bus in Azure Event Grid](../service-bus-messaging/service-bus-to-event-grid-integration-example.md?toc=%2fazure%2fevent-grid%2ftoc.json) | Event Grid sendet Nachrichten von einem Service Bus-Thema an eine Funktions-App und an eine Logik-App. |

## <a name="hybrid-connections"></a>Hybridverbindungen

Verwenden Sie Azure Relay Hybrid Connections zum Senden von Ereignissen an Anwendungen, die sich in einem Unternehmensnetzwerk befinden und nicht über einen öffentlich zugänglichen Endpunkt verfügen.

|Titel  |BESCHREIBUNG  |
|---------|---------|
| [Weiterleiten benutzerdefinierter Ereignisse an Azure Relay Hybrid Connections mit Azure-Befehlszeilenschnittstelle und Event Grid](custom-event-to-hybrid-connection.md) | Sendet ein benutzerdefiniertes Ereignis zur Verarbeitung durch eine Listeneranwendung an eine bestehende Hybridverbindung. |

## <a name="logic-apps"></a>Logic Apps

Verwenden Sie Logic Apps, um Geschäftsprozesse für die Reaktion auf Ereignisse zu automatisieren.

|Titel  |BESCHREIBUNG  |
|---------|---------|
| [Monitor virtual machine changes with Azure Event Grid and Logic Apps](monitor-virtual-machine-changes-event-grid-logic-app.md) (Überwachen von Änderungen an virtuellen Computer mit Azure Event Grid und Logic Apps) | Eine Logik-App überwacht die Änderungen an einem virtuellen Computer und sendet E-Mails zu diesen Änderungen. |
| [Senden von E-Mail-Benachrichtigungen zu Azure IoT Hub-Ereignissen mit Logic Apps](publish-iot-hub-events-to-logic-apps.md) | Eine Logik-App sendet eine E-Mail-Benachrichtigung, wenn Ihrer IoT Hub-Instanz ein Gerät hinzugefügt wird. |
| [Beispiele für die Integration von Azure Service Bus in Azure Event Grid](../service-bus-messaging/service-bus-to-event-grid-integration-example.md?toc=%2fazure%2fevent-grid%2ftoc.json) | Event Grid sendet Nachrichten von einem Service Bus-Thema an eine Funktions-App und an eine Logik-App. |

## <a name="queue-storage"></a>Queue Storage

Verwenden Sie Queue Storage, um Ereignisse zu empfangen, die gepullt werden müssen.

|Titel  |BESCHREIBUNG  |
|---------|---------|
| [Weiterleiten benutzerdefinierter Ereignisse an Azure Queue Storage mit Azure CLI und Event Grid](custom-event-to-queue-storage.md) | Beschreibt das Senden von benutzerdefinierten Ereignisse an eine Queue Storage-Instanz. |

## <a name="webhooks"></a>WebHooks

Verwenden Sie Webhooks für anpassbare Endpunkte, die auf Ereignisse reagieren.

|Titel  |BESCHREIBUNG  |
|---------|---------|
| [Empfangen von Ereignissen an einem HTTP-Endpunkt](receive-events.md) | Beschreibt, wie Sie einen HTTP-Endpunkt überprüfen, um Ereignisse von einem Ereignisabonnement zu empfangen, und Ereignisse empfangen und deserialisieren. |

## <a name="next-steps"></a>Nächste Schritte

* Eine Einführung in Event Grid finden Sie unter [Informationen zu Event Grid](overview.md).
* Um sich schnell mit der Verwendung von Event Grid vertraut zu machen, lesen Sie [Erstellen und Weiterleiten benutzerdefinierter Ereignisse mit Azure Event Grid](custom-event-quickstart.md).
