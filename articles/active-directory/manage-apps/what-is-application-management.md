---
title: Verwalten von Anwendungen mit Azure Active Directory | Microsoft Docs
description: Dieser Artikel erläutert die Vorteile der Integration von Azure Active Directory in lokale, Cloud- und SaaS-Anwendungen.
services: active-directory
documentationcenter: ''
author: barbkess
manager: mtillman
ms.service: active-directory
ms.component: app-mgmt
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 01/15/2018
ms.author: barbkess
ms.reviewer: asteen
ms.openlocfilehash: 1a8db218309eb48650443f1c9d57fe1ecdf04a6a
ms.sourcegitcommit: d28bba5fd49049ec7492e88f2519d7f42184e3a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058200"
---
# <a name="managing-applications-with-azure-active-directory"></a>Verwalten von Anwendungen mit Azure Active Directory
Abgesehen vom eigentlichen Workflow oder Inhalt gibt es für Unternehmen zwei grundlegende Anforderungen für alle Anwendungen:

1. Für eine gesteigerte Produktivität sollte es einfach sein, Anwendungen zu ermitteln und darauf zuzugreifen.
2. Aus Sicherheits- und Governancegründen muss die Organisation die Kontrolle und den Überblick darüber haben, wer auf die einzelnen Anwendungen zugreifen kann und diese Möglichkeit tatsächlich nutzt.

In Bezug auf Cloudanwendungen gelingt dies am besten über Identitäten, mit denen gesteuert wird, *WER zu WAS berechtigt ist*.

In Computerterminologie:

* Das *Wer* wird als *Identität* bezeichnet: die Verwaltung von Benutzern und Gruppen
* Das *Was* wird *Zugriffsverwaltung* genannt: die Verwaltung des Zugriffs auf geschützte Ressourcen

Beide Komponenten werden zusammen als *Identity and Access Management (IAM)* (Identitäts- und Zugriffsverwaltung) bezeichnet, was durch die [Gartner](http://www.gartner.com/it-glossary/identity-and-access-management-iam)-Gruppe definiert wird als „*die Sicherheitsdisziplin, die den richtigen Personen zur rechten Zeit und aus den richtigen Gründen den Zugriff auf die richtigen Ressourcen ermöglicht*“.

Wo liegt also das Problem? Wenn IAM *nicht zentral mit einer integrierten Lösung verwaltet* wird:

* Identitätsadministratoren müssen die einzelnen Benutzerkonten in allen Anwendungen separat erstellen und aktualisieren – eine redundante und zeitaufwändig Aktivität.
* Benutzer müssen sich für den Zugriff auf die Anwendungen, mit denen sie arbeiten müssen, mehrere Anmeldeinformationen merken. Demzufolge neigen Benutzer dazu, ihre Kennwörter aufzuschreiben oder andere Lösungen zur Kennwortverwaltung zu verwenden. Solche alternativen Vorgehensweisen bergen jedoch zusätzliche Risiken für die Datensicherheit.
* Durch redundante, zeitaufwendige Aktivitäten verringert sich der Zeitraum, in dem Benutzer und Administratoren sich den Geschäftsaktivitäten widmen, die das Geschäftsergebnis Ihres Unternehmens erhöhen.

Was hält Organisationen im Allgemeinen davon ab, integrierte IAM-Lösungen einzuführen?

* Die technischsten Lösungen basieren auf Softwareplattformen, die bereitgestellt und von jeder Organisation für ihre eigenen Anwendungen angepasst werden müssen.
* Cloudanwendungen werden häufig schneller eingeführt als die IT-Organisation vorhandene IAM-Lösungen integrieren kann.
* Tools für Sicherheit und Überwachung erfordern eine zusätzliche Anpassung und Integration, um umfassende E2E-Szenarien zu erzielen.

## <a name="azure-active-directory-integrated-with-applications"></a>Azure Active Directory-Integration in Anwendungen
Azure Active Directory ist die umfassende IDaaS-Lösung (Identity as a Service) von Microsoft, die folgende Vorteile bietet:

* Sie ermöglicht IAM als Clouddienst. 
* Sie stellt eine zentrale Zugriffsverwaltung, einmaliges Anmelden (SSO) und Berichterstellung bereit. 
* Sie unterstützt die integrierte Zugriffsverwaltung für [Tausende von Anwendungen](https://azure.microsoft.com/marketplace/active-directory/) im Anwendungskatalog, einschließlich Salesforce, Google Apps, Box, Concur und viele mehr. 

Mit Azure Active Directory gelten für alle Anwendungen, die Sie für Ihre Partner und Kunden (Geschäftskunden oder Heimanwender) veröffentlichen, dieselben Identitäts- und Zugriffsverwaltungsfunktionen.<br> Dadurch können Sie die Betriebskosten erheblich reduzieren.

Was geschieht, wenn Sie eine Anwendung implementieren müssen, die im Anwendungskatalog noch nicht aufgeführt ist? Auch wenn es etwas zeitaufwändiger ist als das Konfigurieren von SSO für Anwendungen über den Katalog, bietet Azure AD einen Assistenten, der Sie bei der Konfiguration unterstützt.

Der Nutzen von Azure AD geht über Cloudanwendungen hinaus. Sie können es durch die Bereitstellung eines sicheren Remotezugriffs auch mit lokalen Anwendungen verwenden. Mit dem sicheren Remotezugriff sind VPNs oder andere herkömmliche Implementierungen der Remotezugriffsverwaltung nicht länger erforderlich.

Durch die Bereitstellung einer zentralen Zugriffsverwaltung und der einmaligen Anmeldung (SSO) für all Ihre Anwendungen bietet Azure AD die Lösung für die größten Probleme mit der Datensicherheit und Produktivität.

* Benutzer können mit einer einzigen Anmeldung auf mehrere Anwendungen zugreifen und mehr Zeit auf Verdienstmöglichkeiten oder Geschäftsvorgänge verwenden.
* Identitätsadministratoren können den Zugriff auf Anwendungen an zentraler Stelle verwalten.

Der Vorteil für den Benutzer und für Ihr Unternehmen liegt auf der Hand. Werfen wir einen Blick auf die Vorteile für einen Identitätsadministrator und die Organisation.

## <a name="integrated-application-benefits"></a>Vorteile der integrierten Anwendung
Der SSO-Vorgang besteht aus zwei Schritten:

* Authentifizierung: der Prozess zur Überprüfung der Benutzeridentität.
* Autorisierung: die Entscheidung, den Zugriff auf eine Ressource durch eine Zugriffsrichtlinie zu ermöglichen oder zu sperren.

Bei Verwendung von Azure AD zum Verwalten von Anwendungen und zum Aktivieren der einmaligen Anmeldung:

* Die Authentifizierung erfolgt über das lokale (z. B. AD) oder das Azure AD-Konto des Benutzers.
* Die Autorisierung wird anhand der Azure AD-Zuweisungs- und Schutzrichtlinie ausgeführt und gewährleistet eine konsistente Endbenutzeroberfläche. Sie ermöglicht Ihnen das Hinzufügen von Zuweisungs-, Standort- und MFA-Bedingungen für beliebige Anwendungen, unabhängig von deren internen Funktionen.

Es wichtig zu verstehen, dass die Durchsetzung der Autorisierung für die Zielanwendung davon abhängt, wie die Anwendung in Azure AD integriert wurde.

* **Vom Dienstanbieter vorinstallierte Anwendungen** Wie Office 365 und Azure handelt es sich hierbei um Anwendungen, die direkt auf Azure AD aufbauen und es für ihre umfassenden Identitäts- und Zugriffsverwaltungsfunktionen verwenden. Der Zugriff auf diese Anwendungen wird über Verzeichnisinformationen und die Ausstellung von Token aktiviert.
* **Von Microsoft vorinstallierte und benutzerdefinierte Anwendungen** Hierbei handelt es sich um unabhängige Cloudanwendungen, die auf einem internen Anwendungsverzeichnis basieren und unabhängig von Azure AD verwendet werden können. Der Zugriff auf diese Anwendungen wird durch die Ausgabe anwendungsspezifischer Anmeldeinformationen ermöglicht, die einem Anwendungskonto zugeordnet werden. Abhängig von den Anwendungsfunktionen handelt es sich bei den Anmeldeinformationen um ein Verbundtoken oder um einen Benutzernamen und ein Kennwort für ein Konto, das zuvor in der Anwendung bereitgestellt wurde.
* **Lokale Anwendungen** Anwendungen, die über den Azure AD-Anwendungsproxy veröffentlicht werden und damit hauptsächlich den Zugriff auf lokale Anwendungen ermöglichen. Diese Anwendungen basieren auf einem zentralen lokalen Verzeichnis wie Windows Server Active Directory. Der Zugriff auf diese Anwendungen wird durch Auslösen des Proxys ermöglicht, um den Anwendungsinhalt für den Endbenutzer bereitzustellen und dabei die lokale Anmeldungsanforderung zu berücksichtigen.

Wenn ein Benutzer Ihrer Organisation beitritt, müssen Sie z. B. für die primären Anmeldevorgänge ein Konto für den Benutzer in Azure AD erstellen. Wenn dieser Benutzer den Zugriff auf eine verwaltete Anwendung wie Salesforce benötigt, müssen Sie auch ein Konto für diesen Benutzer in Salesforce erstellen und mit dem Azure-Konto verknüpfen, damit SSO funktioniert. Wenn der Benutzer die Organisation verlässt, ist es ratsam, das Azure AD-Konto und alle entsprechenden Konten in den IAM-Speichern der Anwendungen zu löschen, auf die der Benutzer zugreifen konnte.

## <a name="access-detection"></a>Zugriffserkennung
In modernen Unternehmen sind die IT-Abteilungen häufig nicht über alle verwendeten Cloudanwendungen unterrichtet. Mit Cloud App Discovery bietet Azure AD Ihnen auch eine Lösung zum Erkennen dieser Anwendungen.

## <a name="account-management"></a>Kontenverwaltung
Traditionell ist das Verwalten von Konten in den verschiedenen Anwendungen ein manueller Prozess, der vom IT- oder Supportpersonal in der Organisation durchgeführt wird. Azure AD automatisiert die Kontenverwaltung vollständig über alle von Dienstanbietern integrierten Anwendungen und von Microsoft vorab integrierten Anwendungen hinweg, die eine automatische Benutzerbereitstellung oder SAML-Just-In-Time-Bereitstellung unterstützen.

## <a name="automated-user-provisioning"></a>Automatisierte Benutzerbereitstellung
Einige Anwendungen bieten Automatisierungsschnittstellen für die Erstellung und Entfernung (oder Deaktivierung) von Konten. Wenn ein Anbieter eine solche Schnittstelle anbietet, wird sie von Azure AD genutzt. Dadurch werden die Betriebskosten reduziert, da Verwaltungsaufgaben automatisch ausgeführt werden, und die Sicherheit Ihrer Umgebung verbessert sich, da das Risiko eines unbefugten Zugriffs sinkt.

## <a name="access-management"></a>Zugriffsverwaltung
Mit Azure AD können Sie den Zugriff auf Anwendungen mithilfe individueller oder regelgesteuerter Zuweisungen verwalten. Sie können die Zugriffsverwaltung auch an die richtigen Personen in der Organisation delegieren, um eine optimale Aufsicht sicherzustellen und die Belastung des Helpdesks zu reduzieren.

## <a name="on-premises-applications"></a>Lokale Anwendungen
Mit dem integrierten Anwendungsproxy können Sie lokale Anwendungen für Ihre Benutzer veröffentlichen, um sowohl von einer konsistenten Zugriffsoberfläche mit moderner Cloudanwendung als auch von den Vorteilen der Azure AD-Überwachungs-, Berichterstellungs- und Sicherheitsfunktionen zu profitieren.

## <a name="reporting-and-monitoring"></a>Berichterstellung und Überwachung
Azure AD bietet integrierte Berichterstellungs- und Überwachungsfunktionen, mit denen Sie feststellen können, wer auf Anwendungen zugreifen kann und wer sie verwendet hat.

## <a name="related-capabilities"></a>Zugehörige Funktionen
Mit Azure AD können Sie Ihre Anwendungen mit fein abgestimmten Zugriffsrichtlinien und vorinstallierter MFA sichern. Weitere Informationen zu Azure MFA finden Sie unter [Azure MFA](https://azure.microsoft.com/services/multi-factor-authentication/).

## <a name="getting-started"></a>Erste Schritte
Erste Schritte in die Anwendungsintegration in Azure AD finden Sie unter [Erste Schritte zur Integration von Azure Active Directory in Anwendungen](plan-an-application-integration.md).

## <a name="see-also"></a>Weitere Informationen
* [Artikelindex für die Anwendungsverwaltung in Azure Active Directory](../active-directory-apps-index.md)
* [Ausführlicher Bereitstellungsplan für SSO bei einer SaaS-Anwendung](http://aka.ms/ssodeploymentplan)

