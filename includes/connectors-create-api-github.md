---
title: Includedatei
description: Includedatei
services: logic-apps
author: MandiOhlinger
ms.service: logic-apps
ms.topic: include
ms.date: 03/02/2018
ms.author: mandia
ms.custom: include file
ms.openlocfilehash: ec5b3ca9ccd139cbdf17768056eb1d835336e7a7
ms.sourcegitcommit: 0b02e180f02ca3acbfb2f91ca3e36989df0f2d9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
1. Erstellen Sie im [Azure-Portal](https://portal.azure.com) eine leere Logik-App. 

2. Geben Sie im Logik-App-Designer „github“ als Filter ein. 

3. Wählen Sie den zu verwendenden GitHub-Connector und Trigger aus.

   ![GitHub-Connector und Trigger auswählen](./media/connectors-create-api-github/github-connector.png)

   > [!NOTE]
   > Alle Logik-App-Workflows müssen mit einem Trigger gestartet werden. Sie können nur Aktionen auswählen, wenn Ihr Logikworkflow bereits mit einem Trigger beginnt. 

4. Wenn Sie nicht zuvor eine Verbindung erstellt haben, wählen Sie **Anmelden** aus, damit Sie Ihre GitHub-Anmeldeinformationen bei Aufforderung bereitstellen können.  

   ![Anmelden mit Ihren GitHub-Anmeldeinformationen](./media/connectors-create-api-github/github-connector-sign-in-credentials.png)

   Ihre Logik-App verwendet diese Anmeldeinformationen zum Autorisieren des Herstellens einer Verbindung und Zugreifen auf Daten für Ihr GitHub-Konto. 

5. Geben Sie Ihren GitHub-Benutzernamen und das zugehörige Kennwort an, und bestätigen Sie Ihre Autorisierung.

   ![Anmeldeinformationen angeben und Autorisierung bestätigen](./media/connectors-create-api-github/github-connector-authorize.png)   

   Die Verbindung wird jetzt im Azure-Portal erstellt und ist verwendungsbereit.

6. Fahren Sie fort, Ihren Logik-App-Workflow zu definieren.

   ![Fügen Sie Ihrem Logik-App-Workflow weitere Aktionen hinzu](./media/connectors-create-api-github/github-connector-logic-app.png)

