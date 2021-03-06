---
title: Gewähren des Zugriffs auf Privileged Identity Management – Azure | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit der Erweiterung Azure Active Directory Privileged Identity Management Rollen zu Benutzern hinzufügen, sodass diese PIM verwalten können.
services: active-directory
documentationcenter: ''
author: curtand
manager: mtillman
editor: ''
ms.service: active-directory
ms.topic: article
ms.workload: identity
ms.component: users-groups-roles
ms.date: 06/06/2017
ms.author: curtand
ms.custom: pim
ms.openlocfilehash: f7e08e35ce4575715a72b0880d038ce0db766b66
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="giving-access-to-manage-azure-ad-privileged-identity-management"></a>Gewähren des Zugriffs zur Verwaltung von Azure AD Privileged Identity Management
Der globale Administrator, der Azure AD Privileged Identity Management (PIM) für eine Organisation aktiviert, erhält automatisch Rollenzuweisungen und Zugriff auf PIM. Andere Benutzer dagegen erhalten nicht standardmäßig Schreibzugriff, auch nicht die weiteren globalen Administratoren. Andere globale Administratoren, Sicherheitsadministratoren und Benutzer mit Leseberechtigung für Sicherheitsfunktionen erhalten schreibgeschützten Zugriff auf Azure AD PIM. Um Zugriff auf PIM zu gewähren, kann der erste Benutzer andere der Rolle **Administrator für privilegierte Rollen** zuweisen. Diese Zuweisung muss innerhalb von PIM erfolgen und kann nicht über PowerShell oder andere Portale geändert werden.

> [!NOTE]
> Für die Verwaltung von Azure AD PIM ist Azure MFA erforderlich. Da Microsoft-Konten nicht für Azure MFA registriert werden können, kann ein Benutzer, der sich mit einem Microsoft-Konto anmeldet, nicht auf Azure AD PIM zugreifen.
> 
> 

Stellen Sie sicher, dass immer mindestens zwei Benutzer mit der Rolle des Administrators für privilegierte Rollen vorhanden sind, falls ein Benutzer gesperrt oder ein Konto gelöscht wird.

## <a name="give-another-user-access-to-manage-pim"></a>Gewähren des Zugriffs für einen anderen Benutzer zur Verwaltung von PIM
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und wählen Sie auf dem Dashboard die App **Azure AD Privileged Identity Management** aus.
2. Wählen Sie **Privilegierte Rollen verwalten** > **Administrator für privilegierte Rollen** > **Hinzufügen** aus.
   
    ![Administrator für privilegierte Rollen hinzufügen – Screenshot][1]
3. Auf dem Blatt „Verwaltete Benutzer hinzufügen“ ist Schritt 1 bereits abgeschlossen. Wählen Sie Schritt 2 **Benutzer auswählen** aus, und suchen Sie nach dem Benutzer, den Sie hinzufügen möchten.
   
    ![Benutzer auswählen – Screenshot][2]
4. Wählen Sie den Benutzer aus den Suchergebnissen aus, und klicken Sie auf **Fertig**.
5. Klicken Sie zum Speichern der Auswahl auf **OK** . Der von Ihnen ausgewählte Benutzer wird in der Liste der Administratoren für privilegierte Rollen angezeigt.
   
   * Wenn Sie einem Benutzer eine neue Rolle zuweisen, wird er automatisch als berechtigt zum Aktivieren der Rolle eingerichtet. Wenn ihm die Rolle permanent zugewiesen werden soll, klicken Sie auf den Benutzer in der Liste. Wählen Sie im Menü mit den Benutzerinformationen **Als permanent festlegen** aus.
6. Senden Sie dem Benutzer einen Link zu [Erste Schritte mit Azure AD Privileged Identity Management](active-directory-privileged-identity-management-getting-started.md).

## <a name="remove-another-users-access-rights-for-managing-pim"></a>Entfernen der Zugriffsrechte eines Benutzers für die Verwaltung von PIM
Bevor Sie einen Benutzer aus der Rolle der Administratoren für privilegierte Rollen entfernen, stellen Sie sicher, dass dieser Rolle danach noch mindestens zwei Benutzer zugewiesen sind.

1. Klicken Sie auf dem PIM-Dashboard auf die Rolle **Administrator für privilegierte Rollen**.  Es wird eine Liste der Benutzer angezeigt, die diese Rolle derzeit innehaben.
2. Klicken Sie auf den Benutzer in der Benutzerliste.
3. Klicken Sie auf **Entfernen**.  Eine Bestätigungsmeldung wird angezeigt.
4. Klicken Sie auf **Ja** , um den Benutzer aus der Rolle zu entfernen.

<!--Every topic should have next steps and links to the next logical set of content to keep the customer engaged-->
## <a name="next-steps"></a>Nächste Schritte
[!INCLUDE [active-directory-privileged-identity-management-toc](../../includes/active-directory-privileged-identity-management-toc.md)]

<!--Image references-->

[1]: ./media/active-directory-privileged-identity-management-how-to-give-access-to-pim/PIM_add_PRA.png
[2]: ./media/active-directory-privileged-identity-management-how-to-give-access-to-pim/PIM_select_users.png
