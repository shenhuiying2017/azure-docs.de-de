---
title: Azure CLI-Beispiele – Azure SignalR-Dienst | Microsoft-Dokumentation
description: Azure CLI-Beispiele – Azure SignalR-Dienst
services: signalr
documentationcenter: signalr
author: wesmc7777
manager: cfowler
editor: ''
tags: azure-service-management
ms.service: signalr
ms.devlang: na
ms.topic: sample
ms.tgt_pltfrm: na
ms.workload: signalr
ms.date: 04/20/2018
ms.author: wesmc
ms.custom: mvc
ms.openlocfilehash: 6e76ee89160c84ff0f1033590d14c288f023f201
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="azure-cli-samples"></a>Azure CLI-Beispiele

Die folgende Tabelle enthält Links zu Bash-Skripts für den Azure SignalR-Dienst, die mithilfe der Azure CLI 2.0 erstellt wurden.

| | |
|-|-|
|**Erstellen**||
| [Erstellen eines neuen SignalR-Diensts und einer neuen Ressourcengruppe](scripts/signalr-cli-create-service.md) | Dieses Skript erstellt eine neue Azure SignalR-Dienstressource in einer neuen Ressourcengruppe mit einem beliebigen Namen.  |
|**Integrieren**||
| [Erstellen eines neuen SignalR-Diensts und einer für die Verwendung von SignalR konfigurierten Web-App](scripts/signalr-cli-create-with-app-service.md) | Dieses Skript erstellt eine neue Azure SignalR-Dienstressource in einer neuen Ressourcengruppe mit einem beliebigen Namen. Es fügt auch eine neue Web-App und einen App Service-Plan hinzu, um eine ASP.NET Core-Web-App zu hosten, die den SignalR-Dienst verwendet. Die Web-App ist mit einer App-Einstellung konfiguriert, um eine Verbindung mit der neuen SignalR-Dienstressource herzustellen. |
| [Erstellen eines neuen SignalR-Diensts und einer für die Verwendung von SignalR und GitHub OAuth konfigurierten Web-App](scripts/signalr-cli-create-with-app-service-github-oauth.md) | Dieses Skript erstellt eine neue Azure SignalR-Dienstressource in einer neuen Ressourcengruppe mit einem beliebigen Namen. Es fügt auch eine neue Azure Web-App und einen Hostingplan hinzu, um eine ASP.NET Core-Web-App zu hosten, die den SignalR-Dienst verwendet. Die Web-App ist mit App-Einstellungen für die Verbindungszeichenfolge für die neue SignalR-Dienstressource sowie mit geheimen Clientschlüsseln konfiguriert, um die [GitHub-Authentifizierung](https://developer.github.com/v3/guides/basics-of-authentication/) zu unterstützen. Dies wird im [Tutorial zur Authentifizierung](signalr-authenticate-oauth.md) veranschaulicht. Die Web-App ist auch für die Verwendung eines lokalen Git-Repositorys als Bereitstellungsquelle konfiguriert. |
| | |
