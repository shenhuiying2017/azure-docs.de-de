---
title: Informationen zu Azure IoT SDKs | Microsoft Docs
description: 'Entwicklerhandbuch: Informationen und Links zu verschiedenen Geräte- und Dienst-SDKs für Azure IoT, mit denen Sie Geräte- und Back-End-Apps erstellen können.'
services: iot-hub
documentationcenter: ''
author: dominicbetts
manager: timlt
editor: ''
ms.assetid: c5c9a497-bb03-4301-be2d-00edfb7d308f
ms.service: iot-hub
ms.devlang: multiple
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/12/2018
ms.author: dobett
ms.custom: H1Hack27Feb2017
ms.openlocfilehash: 71d02e3f8bf0757d7ea0622e76b95acda1fefc95
ms.sourcegitcommit: 9cdd83256b82e664bd36991d78f87ea1e56827cd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="understand-and-use-azure-iot-hub-sdks"></a>Verstehen und Verwenden von Azure IoT Hub SDKs

Es gibt zwei Kategorien von Software Development Kits (SDKs) für die Arbeit mit IoT Hub:

* **Geräte-SDKs** ermöglichen das Erstellen von Apps, die auf Ihren IoT-Geräten ausgeführt werden. Mit diesen Apps werden Telemetriedaten an die IoT Hub-Instanz gesendet und optional Nachrichten oder Updates für Aufträge, Methoden oder Gerätezwillingen von der IoT Hub-Instanz empfangen.

* Mit **Dienst-SDKs** können Sie Ihren IoT-Hub verwalten und für Ihre IoT-Geräte optional Nachrichten senden, Aufträge planen, direkte Methoden aufrufen oder gewünschte Eigenschaftsupdates senden.

[Hier][lnk-benefits-blog] erfahren Sie mehr über die Vorteile beim Entwickeln mit Azure IoT SDKs.

[!INCLUDE [iot-hub-basic](../../includes/iot-hub-basic-partial.md)]

## <a name="azure-iot-device-sdks"></a>Azure IoT-Geräte-SDKs

Die Microsoft Azure IoT-Geräte-SDKs enthalten Code, der das Erstellen von Geräten und Anwendungen ermöglicht, die eine Verbindung mit Azure IoT Hub-Diensten herstellen und von ihnen verwaltet werden.

Azure IoT Hub Device SDK für .NET: 
* Installation über [Nuget][lnk-nuget-csharp-device]
* [Quellcode][lnk-dotnet-sdk]
* [API-Referenz][lnk-dotnet-ref]

Azure IoT Hub Device SDK für C wurde in ANSI C (C99) geschrieben und ist auf Portabilität und hohe Plattformkompatibilität ausgelegt.
* Installation über [apt-get, MBED, Arduino-IDE oder Nuget][lnk-c-package]
* [Quellcode][lnk-c-sdk]
* [API-Referenz][lnk-c-ref]

Azure IoT Hub Device SDK für Java: 
* Hinzufügen zum [Maven][lnk-maven-device]-Projekt
* [Quellcode][lnk-java-sdk]
* [API-Referenz][lnk-java-ref]

Azure IoT Hub Device SDK für Node.js: 
* Installation über [npm][lnk-npm-device]
* [Quellcode][lnk-node-sdk]
* [API-Referenz][lnk-node-ref]

Azure IoT Hub Device SDK für Python: 
* Installation über [pip][lnk-pip-device]
* [Quellcode][lnk-python-sdk]

> [!NOTE]
> In den „Readme“-Dateien in den GitHub-Repositorys finden Sie Informationen zum Verwenden sprach- und plattformspezifischer Paket-Manager zum Installieren von Binärdateien und Abhängigkeiten auf Ihrem Entwicklungscomputer.
> 
> 

### <a name="os-platform-and-hardware-compatibility"></a>Betriebssystemplattformen und Hardwarekompatibilität

Weitere Informationen zur Kompatibilität von SDKs mit bestimmten Hardwaregeräten finden Sie im [Azure Certified for IoT-Gerätekatalog][lnk-certified] oder im jeweiligen Repository.

## <a name="azure-iot-service-sdks"></a>Azure IoT-Dienst-SDKs

Die Azure IoT-Dienst-SDKs enthalten Code zum Erstellen von Anwendungen, die direkt mit IoT Hub interagieren, um Geräte und Sicherheit zu verwalten.

Azure IoT Hub Service SDK für .NET:
* Download über [Nuget][lnk-nuget-csharp-service]
* [Quellcode][lnk-dotnet-sdk]
* [API-Referenz][lnk-dotnet-service-ref]

Azure IoT Hub Service SDK für Java: 
* Hinzufügen zum [Maven][lnk-maven-service]-Projekt
* [Quellcode][lnk-java-sdk]
* [API-Referenz][lnk-java-service-ref]

Azure IoT Hub Service SDK für Node.js: 
* Download über [npm][lnk-npm-service]
* [Quellcode][lnk-node-sdk]
* [API-Referenz][lnk-node-service-ref]

Azure IoT Hub Service SDK für Python: 
* Download über [pip][lnk-pip-service]
* [Quellcode][lnk-python-sdk]

Azure IoT Hub Service SDK für C: 
* Download über [apt-get, MBED, Arduino-IDE oder Nuget][lnk-c-package]
* [Quellcode][lnk-c-sdk]

> [!NOTE]
> In den „Readme“-Dateien in den GitHub-Repositorys finden Sie Informationen zum Verwenden sprach- und plattformspezifischer Paket-Manager zum Installieren von Binärdateien und Abhängigkeiten auf Ihrem Entwicklungscomputer.


## <a name="next-steps"></a>Nächste Schritte

Weitere Referenzthemen in diesem IoT Hub-Entwicklungsleitfaden:

* [IoT Hub-Endpunkte][lnk-devguide-endpoints]
* [IoT Hub-Abfragesprache für Gerätezwillinge, Aufträge und Nachrichtenrouting][lnk-devguide-query]
* [Kontingente und Drosselung][lnk-devguide-quotas]
* [IoT Hub-MQTT-Unterstützung][lnk-devguide-mqtt]
* [REST-API-Referenz zu IoT Hub][lnk-rest-ref]

<!-- Links and images -->

[lnk-c-sdk]: https://github.com/Azure/azure-iot-sdk-c
[lnk-dotnet-sdk]: https://github.com/Azure/azure-iot-sdk-csharp
[lnk-java-sdk]: https://github.com/Azure/azure-iot-sdk-java
[lnk-node-sdk]: https://github.com/Azure/azure-iot-sdk-node
[lnk-python-sdk]: https://github.com/Azure/azure-iot-sdk-python
[lnk-certified]: https://catalog.azureiotsuite.com/

[lnk-dotnet-ref]: https://docs.microsoft.com/dotnet/api/microsoft.azure.devices?view=azure-dotnet
[lnk-dotnet-service-ref]: https://docs.microsoft.com/dotnet/api/microsoft.azure.devices
[lnk-c-ref]: https://azure.github.io/azure-iot-sdk-c/index.html
[lnk-java-ref]: https://docs.microsoft.com/java/api/com.microsoft.azure.sdk.iot.device
[lnk-node-ref]: https://docs.microsoft.com/javascript/api/azure-iot-device/?view=azure-iot-typescript-latest
[lnk-rest-ref]: https://docs.microsoft.com/rest/api/iothub/
[lnk-java-service-ref]: https://docs.microsoft.com/java/api/com.microsoft.azure.sdk.iot.service
[lnk-node-service-ref]: https://docs.microsoft.com/javascript/api/azure-iothub/?view=azure-iot-typescript-latest

[lnk-maven-device]: https://github.com/Azure/azure-iot-sdk-java/blob/master/doc/java-devbox-setup.md#for-the-device-sdk
[lnk-maven-service]: https://github.com/Azure/azure-iot-sdk-java/blob/master/doc/java-devbox-setup.md#for-the-service-sdk
[lnk-npm-device]: https://www.npmjs.com/package/azure-iot-device
[lnk-npm-service]: https://www.npmjs.com/package/azure-iothub
[lnk-nuget-csharp-device]: https://www.nuget.org/packages/Microsoft.Azure.Devices.Client/
[lnk-nuget-csharp-service]: https://www.nuget.org/packages/Microsoft.Azure.Devices/
[lnk-c-package]: https://github.com/Azure/azure-iot-sdk-c/blob/master/iothub_client/readme.md
[lnk-pip-device]: https://pypi.python.org/pypi/azure-iothub-device-client/
[lnk-pip-service]: https://pypi.python.org/pypi/azure-iothub-service-client/


[lnk-devguide-endpoints]: iot-hub-devguide-endpoints.md
[lnk-devguide-quotas]: iot-hub-devguide-quotas-throttling.md
[lnk-devguide-query]: iot-hub-devguide-query-language.md
[lnk-devguide-mqtt]: iot-hub-mqtt-support.md
[lnk-benefits-blog]: https://azure.microsoft.com/blog/benefits-of-using-the-azure-iot-sdks-in-your-azure-iot-solution/
