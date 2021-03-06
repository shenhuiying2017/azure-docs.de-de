---
title: Erstellen einer Azure IoT Central-Anwendung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie als Administrator eine Azure IoT Central-Anwendung erstellen.
services: iot-central
author: TanmayBhagwat
ms.author: tanmayb
ms.date: 03/20/2018
ms.topic: article
ms.prod: microsoft-iot-central
manager: timlt
ms.openlocfilehash: 83879c6b81985f61b9fcff665e9f764c1346592e
ms.sourcegitcommit: eb75f177fc59d90b1b667afcfe64ac51936e2638
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34200808"
---
# <a name="create-your-azure-iot-central-application"></a>Erstellen Ihrer Azure IoT Central-Anwendung

Erstellen Sie Ihre Microsoft Azure IoT Central-Anwendung über die Seite [Anwendung erstellen](https://apps.microsoftiotcentral.com/create). Um eine Azure IoT Central-Anwendung zu erstellen, müssen Sie alle Felder auf dieser Seite ausfüllen und dann **Erstellen** wählen. Dieser Artikel enthält weitere Informationen zu den einzelnen Feldern.

![Erstellen einer Anwendungsseite](media\howto-create-application\image1.png)

## <a name="payment-plan"></a>Zahlungsplan

Sie können entweder eine kostenlose Testversion oder eine kostenpflichtige Anwendung erstellen. Erfahren Sie auf dieser Seite mehr über eine kostenlose Testversion und kostenpflichtige Anwendungen.

## <a name="application-name"></a>Anwendungsname

Der Name Ihrer Anwendung wird auf der Seite **Anwendungs-Manager** und in jeder Azure IoT Central-Anwendung angezeigt. Für Ihre Azure IoT Central-Anwendung können Sie einen beliebigen Namen wählen. Wählen Sie einen Namen, der für Sie und Ihre Kollegen eindeutig ist.

## <a name="application-url"></a>Anwendungs-URL

Die Anwendungs-URL ist der Link zu Ihrer Anwendung. Sie können ein Lesezeichen in Ihrem Browser speichern oder mit anderen teilen.

Wenn Sie den Namen für Ihre Anwendung eingeben, wird die Anwendungs-URL automatisch generiert. Falls gewünscht, können Sie auch eine andere URL für Ihre Anwendung auswählen. Jede Azure IoT Central-URL muss eindeutig sein. Eine Fehlermeldung wird angezeigt, wenn die von Ihnen gewählte URL bereits vergeben ist.

## <a name="directory"></a>Verzeichnis

Nur in kostenpflichtigen Anwendungen.

Wählen Sie einen Azure Active Directory-Mandanten, um eine Azure IoT Central-Anwendung zu erstellen. Ein Azure Active Directory-Mandant enthält Benutzeridentitäten, Anmeldeinformationen und andere organisatorische Informationen. Mehrere Azure-Abonnements können einem einzelnen Azure Active Directory-Mandanten zugeordnet werden.

Wenn Sie keinen Azure Active Directory-Mandanten haben, wird einer für Sie angelegt, sobald Sie ein Azure-Abonnement erstellen.

Weitere Informationen finden Sie unter [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/).

## <a name="azure-subscription"></a>Azure-Abonnement

Mit einem Azure-Abonnement können Sie Instanzen von Azure-Diensten erstellen. Azure IoT Central findet automatisch alle Azure-Abonnements, auf die Sie Zugriff haben, und zeigt sie auf der Seite **Anwendung erstellen** in einem Dropdownmenü an. Wählen Sie ein Azure-Abonnement, um eine neue Azure IoT Central-Anwendung zu erstellen.

Wenn Sie über kein Azure-Abonnement verfügen, können Sie auf dieser Seite eins erstellen. Nachdem Sie das Azure-Abonnement erstellt haben, navigieren Sie zurück zur Seite **Anwendung erstellen**. Ihr neues Abonnement wird in der Dropdownliste **Azure-Abonnement** angezeigt.

Weitere Informationen finden Sie unter [Azure-Abonnements](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

## <a name="region"></a>Region

Nur in kostenpflichtigen Anwendungen.

Wählen Sie die Region, in der Sie Ihre Azure IoT Central-Anwendung erstellen möchten. Normalerweise sollten Sie die Region wählen, die Ihren Geräten physisch am nächsten liegt, um eine optimale Leistung zu erzielen.

Weitere Informationen finden Sie unter [Azure-Regionen](https://docs.microsoft.com/en-us/azure/guides/developer/azure-developer-guide#azure-regions).

Die Regionen, in denen Azure IoT Central verfügbar ist, finden Sie auf der Seite [Verfügbare Produkte nach Region](https://azure.microsoft.com/regions/services/).

> [!Note]
> Sobald Sie eine Region ausgewählt haben, können Sie Ihre Anwendung später nicht mehr in eine andere Region verschieben.

## <a name="application-template"></a>Anwendungsvorlage

Sie können für Ihre neue Azure IoT Central-Anwendung eine der verfügbaren Anwendungsvorlagen auswählen. Eine Anwendungsvorlage kann vordefinierte Elemente wie Gerätevorlagen und Dashboards enthalten, die Ihnen den Einstieg erleichtern:

| Anwendungsvorlage | Beschreibung |
| -------------------- | ----------- |
| Benutzerdefinierte Anwendung   | Erstellt eine leere Anwendung, die Sie mit Ihren eigenen Gerätevorlagen und Geräten füllen können. |
| Beispiel „Contoso“       | Erstellt eine Anwendung, die eine Gerätevorlage für ein einfach angeschlossenes Gerät enthält. Verwenden Sie diese Vorlage, um mit der Erkundung von Azure IoT Central zu beginnen. |
| Beispiel-Entwickler-Kits       | Erstellt eine Anwendung mit Gerätevorlagen, an die Sie ein MXChip- oder Raspberry Pi-Gerät anschließen können. Verwenden Sie diese Vorlage, wenn Sie ein Geräteentwickler sind, der mit Code auf einem dieser Geräte experimentiert. |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun erfahren haben, wie Sie eine Azure IoT Central-Anwendung erstellen, wird als Nächstes der folgende Schritt empfohlen:

> [!div class="nextstepaction"]
> [Verwalten Ihrer Anwendung](howto-administer.md)