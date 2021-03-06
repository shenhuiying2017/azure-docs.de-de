---
title: Aufbewahrungsrichtlinien für Azure Active Directory-Berichte | Microsoft Docs
description: Aufbewahrungsrichtlinien für Berichtdaten in Azure Active Directory
services: active-directory
documentationcenter: ''
author: MarkusVi
manager: mtillman
editor: ''
ms.assetid: 183e53b0-0647-42e7-8abe-3e9ff424de12
ms.service: active-directory
ms.devlang: ''
ms.topic: article
ms.tgt_pltfrm: ''
ms.workload: identity
ms.date: 05/10/2018
ms.author: markvi
ms.reviewer: dhanyahk
ms.openlocfilehash: 9101b3877f8a011878baeed0d5c23d29fddaeaad
ms.sourcegitcommit: d28bba5fd49049ec7492e88f2519d7f42184e3a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
ms.locfileid: "34055170"
---
# <a name="azure-active-directory-report-retention-policies"></a>Aufbewahrungsrichtlinien für Azure Active Directory-Berichte


Dieses Thema enthält Antworten auf die am häufigsten gestellten Fragen im Zusammenhang mit der Datenaufbewahrung für die verschiedenen Aktivitätsberichte in Azure Active Directory. 

### <a name="q-how-can-you-get-the-collection-of-activity-data-started"></a>F: Wie wird die Erfassung von Aktivitätsdaten gestartet?

**A:**

| Azure AD-Edition | Start der Erfassung |
| :--              | :--   |
| Azure AD Premium P1 <br /> Azure AD Premium P2 | Bei der Registrierung für ein Abonnement |
| Azure AD Free | Beim ersten Öffnen des Blatts [Azure Active Directory](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) oder bei der ersten Verwendung der [Berichterstellungs-APIs](https://aka.ms/aadreports)  |

---
### <a name="q-when-is-your-activity-data-available-in-the-azure-portal"></a>F: Wann sind die Aktivitätsdaten im Azure-Portal verfügbar?

**A:**

- **Sofort** – Wenn Sie bereits mit Berichten im Azure-Portal gearbeitet haben
- **Innerhalb von 2 Stunden** – Wenn Sie die Berichterstellung im Azure-Portal nicht aktiviert haben

---

### <a name="q-how-can-you-get-the-collection-of-security-signals-started"></a>F: Wie wird die Erfassung von Sicherheitssignalen gestartet?  

**A:** Bei Sicherheitssignalen wird der Erfassungsprozess gestartet, wenn Sie sich für die Verwendung von Identity Protection Center entscheiden. 


---

### <a name="q-for-how-long-is-the-collected-data-stored"></a>F: Wie lange werden die gesammelten Daten gespeichert?

**A:**

**Aktivitätsberichte**    

| Bericht                 | Azure AD Free | Azure AD Premium P1 | Azure AD Premium P2 |
| :--                    | :--           | :--                 | :--                 |
| Verzeichnisprüfbericht        | 7 Tage        | 30 Tage             | 30 Tage             |
| Benutzeranmeldeaktivität       | N/V           | 30 Tage             | 30 Tage             |
| Azure MFA-Nutzung        | 30 Tage       | 30 Tage             | 30 Tage             |

**Sicherheitssignale**

| Bericht         | Azure AD Free | Azure AD Premium P1 | Azure AD Premium P2 |
| :--            | :--           | :--                 | :--                 |
| Gefährdete Benutzer  | 7 Tage        | 30 Tage             | 90 Tage             |
| Riskante Anmeldungen | 7 Tage        | 30 Tage             | 90 Tage             |

---
