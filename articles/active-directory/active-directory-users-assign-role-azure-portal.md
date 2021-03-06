---
title: Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory | Microsoft-Dokumentation
description: Erläutert, wie in Azure Active Directory Administratorinformationen für Benutzer geändert werden.
services: active-directory
documentationcenter: ''
author: curtand
manager: mtillman
editor: ''
ms.service: active-directory
ms.workload: identity
ms.component: users-groups-roles
ms.topic: article
ms.date: 01/08/2018
ms.author: curtand
ms.reviewer: jeffsta
ms.openlocfilehash: 61662acb10a6f2085d297eae473e1330c619d48d
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="assign-a-user-to-administrator-roles-in-azure-active-directory"></a>Zuweisen eines Benutzers zu Administratorrollen in Azure Active Directory
In diesem Artikel wird erläutert, wie Sie einem Benutzer in Azure Active Directory eine Administratorrolle zuweisen. Informationen dazu, wie Sie neue Benutzer in Ihrer Organisation hinzufügen, finden Sie unter [Hinzufügen neuer Benutzer zu Azure Active Directory](active-directory-users-create-azure-portal.md). Hinzugefügte Benutzer verfügen nicht standardmäßig über Administratorberechtigungen, aber Sie können ihnen jederzeit Rollen zuweisen.

## <a name="assign-a-role-to-a-user"></a>Zuweisen einer Rolle zu einem Benutzer
1. Melden Sie sich beim [Azure AD Admin Center](https://aad.portal.azure.com) mit dem Konto eines globalen Administrators für das Verzeichnis an.
2. Wählen Sie **Benutzer und Gruppen**.

   ![Öffnen der Benutzerverwaltung](./media/active-directory-users-assign-role-azure-portal/create-users-user-management.png)
3. Wählen Sie **Alle Benutzer**.
  
  ![Öffnen der Gruppe „Alle Benutzer“](./media/active-directory-users-assign-role-azure-portal/create-users-open-users-blade.png)
4. Wählen Sie in der Liste einen Benutzer aus.
5. Wählen Sie für den ausgewählten Benutzer die Option **Verzeichnisrolle** aus, und weisen Sie den Benutzer dann über die Liste **Verzeichnisrolle** einer Rolle zu. Weitere Informationen zu Benutzer- und Administratorrollen finden Sie unter [Zuweisen von Administratorrollen in Azure AD](active-directory-assign-admin-roles-azure-portal.md).

      ![Zuweisen einer Rolle zu einem Benutzer](./media/active-directory-users-assign-role-azure-portal/create-users-assign-role.png)
6. Wählen Sie **Speichern**aus.

## <a name="next-steps"></a>Nächste Schritte
* [Schnellstart: Hinzufügen oder Löschen von Benutzern in Azure Active Directory](add-users-azure-active-directory.md)
* [Verwalten von Benutzerprofilen](active-directory-users-profile-azure-portal.md)
* [Hinzufügen von Gastbenutzern aus einem anderen Verzeichnis](active-directory-b2b-what-is-azure-ad-b2b.md) 
* [Zuweisen eines Benutzers zu einer Rolle in Azure AD](active-directory-users-assign-role-azure-portal.md)
* [Wiederherstellen eines gelöschten Benutzers](active-directory-users-restore.md)
