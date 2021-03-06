---
title: Weitere Informationen zu den von Azure AD v2.0 unterstützten Autorisierungsprotokollen | Microsoft-Dokumentation
description: Anleitung für Protokolle, die vom Azure AD v2.0-Endpunkt unterstützt werden.
services: active-directory
documentationcenter: ''
author: CelesteDG
manager: mtillman
editor: ''
ms.assetid: 5fb4fa1b-8fc4-438e-b3b0-258d8c145f22
ms.service: active-directory
ms.component: develop
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 04/22/2018
ms.author: celested
ms.reviewer: hirsin
ms.custom: aaddev
ms.openlocfilehash: 7c6031bb135c48a8d58f61c3c96bf18e817809ba
ms.sourcegitcommit: e14229bb94d61172046335972cfb1a708c8a97a5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2018
ms.locfileid: "34156220"
---
# <a name="v20-protocols---oauth-20--openid-connect"></a>v2.0-Protokolle – OAuth 2.0 und OpenID Connect
Der v2.0-Endpunkt kann Azure AD als Identity-as-a-Service-Lösung mit den Industriestandardprotokollen OpenID Connect und OAuth 2.0 verwenden. Auch wenn der Dienst den Standard entspricht, kann es feine Unterschiede zwischen zwei Implementierungen dieser Protokolle geben. Die hier bereitgestellten Informationen sind hilfreich, wenn Sie Code direkt durch Senden und Verarbeiten von HTTP-Anforderungen schreiben oder eine Open Source-Bibliothek eines Drittanbieters verwenden, anstatt eine unserer [Open-Source-Bibliotheken](active-directory-v2-libraries.md) zu nutzen.

> [!NOTE]
> Nicht alle Szenarien und Funktionen von Azure Active Directory werden vom v2.0-Endpunkt unterstützt. Lesen Sie die Informationen zu den [Einschränkungen des v2.0-Endpunkts](active-directory-v2-limitations.md), um herauszufinden, ob Sie den v2.0-Endpunkt verwenden sollten.
>
>

## <a name="the-basics"></a>Die Grundlagen
In fast allen OAuth- und OpenID Connect-Vorgängen sind vier Beteiligte am Austausch involviert:

![OAuth 2.0-Rollen](../../media/active-directory-v2-flows/protocols_roles.png)

* Der **Autorisierungsserver** ist der v2.0-Endpunkt. Er ist verantwortlich für das Sicherstellen der Identität des Benutzers, das Erteilen und Widerrufen des Zugriffs auf Ressourcen und das Ausstellen von Token. Er ist auch als Identitätsanbieter bekannt und verarbeitet auf sichere Weise alles im Zusammenhang mit den Informationen des Benutzers, dessen Zugriff und den Vertrauensstellungen zwischen den Beteiligten in einem Vorgang.
* Beim **Ressourcenbesitzer** handelt es sich normalerweise um den Endbenutzer. Diese Person besitzt die Daten und hat die Möglichkeit, Dritten den Zugriff auf die Daten oder die Ressource zu gewähren.
* Der **OAuth-Client** ist Ihre App, die durch ihre Anwendungs-ID identifiziert wird. Dies ist normalerweise der Beteiligte, mit dem der Endbenutzer interagiert, und der Token vom Autorisierungsserver anfordert. Der Client muss vom Besitzer der Ressource die Berechtigung zum Zugriff darauf erhalten.
* Der **Ressourcenserver** ist der Ort, an dem die Ressource oder die Daten abgelegt sind. Er vertraut dem Autorisierungsserver, dass der OAuth-Client sicher authentifiziert und autorisiert wird, und verwendet Bearerzugriffstoken, um sicherzustellen, dass der Zugriff auf eine Ressource gewährt werden kann.

## <a name="app-registration"></a>App-Registrierung
Jede App, die den v2.0-Endpunkt nutzt, muss vor der Interaktion mit OAuth oder OpenID Connect unter [apps.dev.microsoft.com](https://apps.dev.microsoft.com/?referrer=https://azure.microsoft.com/documentation/articles&deeplink=/appList) registriert werden. Der Registrierungsprozess für die App sammelt einige Werte und weist ihr einige Werte zu:

* Eine **Anwendungs-ID** , die Ihre Anwendung eindeutig identifiziert.
* Einen **Umleitungs-URI** oder **Paketbezeichner**, der zum Umleiten von Antworten zurück an die App verwendet werden kann
* Einige andere szenariospezifische Werte.

Weitere Informationen finden Sie im Artikel zum [Registrieren von Apps](active-directory-v2-app-registration.md).

## <a name="endpoints"></a>Endpunkte
Nach dem Registrieren kommuniziert eine App mit Azure AD, indem Anforderungen an den v2.0-Endpunkt gesendet werden:

```
https://login.microsoftonline.com/{tenant}/oauth2/v2.0/authorize
https://login.microsoftonline.com/{tenant}/oauth2/v2.0/token
```

Dabei ist für `{tenant}` einer von vier verschiedenen Werten möglich:

| Wert | BESCHREIBUNG |
| --- | --- |
| `common` |Ermöglicht Benutzern mit persönlichen Microsoft-Konten und Geschäfts-, Schul- oder Unikonten aus Azure Active Directory die Anmeldung bei der Anwendung. |
| `organizations` |Ermöglicht nur Benutzern mit Geschäfts-, Schul- oder Unikonten aus Azure Active Directory die Anmeldung bei der Anwendung. |
| `consumers` |Ermöglicht nur Benutzern mit persönlichen Microsoft-Konten (MSA) die Anmeldung bei der Anwendung. |
| `8eaef023-2b34-4da1-9baa-8bc8c9d6a490` oder `contoso.onmicrosoft.com` |Ermöglicht nur Benutzern mit Geschäfts-, Schul- oder Unikonten eines bestimmten Azure Active Directory-Mandanten die Anmeldung bei der Anwendung. Dabei kann entweder der Anzeigename der Domäne des Azure AD-Mandanten oder der GUID-Bezeichner des Mandanten verwendet werden. |

Um weitere Informationen zur Interaktion mit diesen Endpunkten zu erhalten, wählen Sie unten einen bestimmten App-Typ aus.

## <a name="tokens"></a>Token
Die v2.0-Implementierung von OAuth 2.0 und OpenID Connect macht ausgiebig Gebrauch von Bearertoken (auch in Form von JWTs). Ein Trägertoken ist ein einfaches Sicherheitstoken, das dem „Träger“ den Zugriff auf eine geschützte Ressource ermöglicht. In diesem Kontext ist der „Träger“ jede beliebige Partei, die das Token vorweisen kann. Um das Trägertoken zu erhalten, muss sich die Partei zwar zunächst bei Azure AD authentifizieren, falls jedoch keine Maßnahmen ergriffen werden, um das Token bei der Übertragung und Speicherung zu schützen, kann das Token von einer fremden Partei abgefangen und verwendet werden. Einige Sicherheitstoken verfügen über einen integrierten Mechanismus, der eine unbefugte Verwendung durch nicht autorisierte Parteien verhindert. Trägertoken besitzen dagegen keinen solchen Mechanismus und müssen über einen sicheren Kanal wie etwa Transport Layer Security (HTTPS) übertragen werden. Wird ein Trägertoken als Klartext gesendet, kann eine böswillige Partei das Token mithilfe eines Man-in-the-Middle-Angriffs abfangen und damit unautorisiert auf eine geschützte Ressource zugreifen. Die gleichen Sicherheitsprinzipien gelten für die (Zwischen-)Speicherung von Trägertoken zur späteren Verwendung. Stellen Sie daher sicher, dass Ihre App Bearertoken stets auf sichere Weise überträgt und speichert. Weitere Sicherheitsüberlegungen zu Bearertoken finden Sie unter [RFC 6750, Abschnitt 5](http://tools.ietf.org/html/rfc6750).

Weitere Informationen zu verschiedenen Tokentypen, die im v2.0-Endpunkt verwendet werden, finden Sie in der [Tokenreferenz zum v2.0-Endpunkt](active-directory-v2-tokens.md).

## <a name="protocols"></a>Protokolle
Wenn Sie einige Beispielanforderungen sehen möchten, beginnen Sie mit einem der folgenden Lernprogramme. Jedes Lernprogramm entspricht einem bestimmten Szenario. Wenn Sie Hilfe bei der Bestimmung des richtigen Arbeitsablaufs benötigen, informieren Sie sich über die [App-Typen, die mit dem v2.0-Endpunkt erstellt werden können](active-directory-v2-flows.md).

* [Erstellen von mobilen und systemeigenen Anwendungen mit OAuth 2.0](active-directory-v2-protocols-oauth-code.md)
* [Erstellen von Web-Apps mit OpenID Connect](active-directory-v2-protocols-oidc.md)
* [Erstellen von Apps mit einer einzigen Seite mit dem impliziten OAuth 2.0-Fluss](active-directory-v2-protocols-implicit.md)
* [Erstellen von Daemons oder serverseitigen Prozessen mit dem OAuth 2.0-Clientanmeldeinformations-Flow](active-directory-v2-protocols-oauth-client-creds.md)
* [Abrufen von Token in einer Web-API mit dem „Im Namen von“-Fluss von OAuth 2.0](active-directory-v2-protocols-oauth-on-behalf-of.md)
