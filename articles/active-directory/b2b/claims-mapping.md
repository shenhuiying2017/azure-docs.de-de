---
title: Zuordnen von Benutzeransprüchen für die B2B-Zusammenarbeit in Azure Active Directory | Microsoft-Dokumentation
description: Passen Sie die Benutzeransprüche an, die im SAML-Token für Azure Active Directory B2B-Benutzer ausgegeben werden.
services: active-directory
ms.service: active-directory
ms.component: B2B
ms.topic: article
ms.date: 04/06/2018
ms.author: twooley
author: twooley
manager: mtillman
ms.reviewer: sasubram
ms.openlocfilehash: f2617fb79fc20fcb385c7e2fc3596245ab18caba
ms.sourcegitcommit: 96089449d17548263691d40e4f1e8f9557561197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="b2b-collaboration-user-claims-mapping-in-azure-active-directory"></a>Zuordnen von Benutzeransprüchen für die B2B-Zusammenarbeit in Azure Active Directory

Azure Active Directory (Azure AD) unterstützt die Anpassung der Ansprüche, die im SAML-Token für B2B-Zusammenarbeitsbenutzer ausgegeben werden. Wenn sich ein Benutzer bei der Anwendung authentifiziert, stellt Azure AD ein SAML-Token für die App aus, das Informationen (so genannte „Ansprüche“) über den Benutzer enthält, die ihn eindeutig identifizieren. Dazu gehören normalerweise der Benutzername, die E-Mail-Adresse, der Vorname und der Nachname des Benutzers.

Sie können die im SAML-Token an die Anwendung übermittelten Ansprüche im [Azure-Portal](https://portal.azure.com) anzeigen oder bearbeiten. Klicken Sie zum Aufrufen der Einstellungen auf **Azure Active Directory** > **Unternehmensanwendungen** > die für einmaliges Anmelden konfigurierte Anwendung > **Einmaliges Anmelden**. Sehen Sie sich die Einstellungen für das SAML-Token im Abschnitt **Benutzerattribute** an.

![SAML-Tokenattribute auf der Benutzeroberfläche](media/claims-mapping/view-claims-in-saml-token.png)

Es gibt zwei Gründe dafür, dass Sie die im SAML-Token ausgegebenen Ansprüche möglicherweise bearbeiten müssen:

1. Die Anwendung wurde erfordert einen anderen Satz an Anspruchs-URIs oder Anspruchswerten.

2. Die Anwendung erfordert, dass es sich beim NameIdentifier-Anspruch nicht um den in Azure AD gespeicherten Benutzerprinzipalnamen (User Principal Name, UPN) handelt.

Informationen zum Hinzufügen und Bearbeiten von Ansprüchen finden Sie unter [Anpassen ausgestellter Ansprüche im SAML-Token für Unternehmensanwendungen in Azure Active Directory](../develop/active-directory-saml-claims-customization.md).

Aus Sicherheitsgründen ist eine mandantenübergreifende Zuordnung von NameID und UPN für Benutzer der B2B-Zusammenarbeit nicht möglich.

## <a name="next-steps"></a>Nächste Schritte

- Informationen zu den Eigenschaften von B2B-Zusammenarbeitsbenutzern finden Sie unter [Eigenschaften eines Azure Active Directory B2B-Zusammenarbeitsbenutzers](user-properties.md).
- Informationen zu Benutzertoken für B2B-Zusammenarbeitsbenutzer finden Sie unter [Informationen zu Benutzertoken für die Azure AD B2B-Zusammenarbeit](user-token.md).

