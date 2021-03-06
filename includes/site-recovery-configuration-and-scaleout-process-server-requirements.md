---
title: Includedatei
description: Includedatei
services: site-recovery
author: rayne-wiselman
ms.service: site-recovery
ms.topic: include
ms.date: 05/03/2018
ms.author: raynew
ms.custom: include file
ms.openlocfilehash: 2464fa41deaa1e9c43e5f53e1a900ca11b582040
ms.sourcegitcommit: 870d372785ffa8ca46346f4dfe215f245931dae1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
ms.locfileid: "33901294"
---
**Anforderungen an den Konfigurations-/Prozessserver**

**Komponente** | **Anforderung** 
--- | ---
**HARDWARE** | 
**CPU-Kerne** | 8 
**RAM** | 16 GB
**Anzahl der Datenträger** | 3, einschließlich Betriebssystem-Datenträger, Prozessservercache-Datenträger und Aufbewahrungslaufwerk für Failback 
**Freier Speicherplatz (Prozessservercache)** | 600 GB
**Freier Speicherplatz (Aufbewahrungslaufwerk)** | 600 GB
**SOFTWARE** | 
**Betriebssystem** | Windows Server 2012 R2 <br> Windows Server 2016
**Gebietsschema des Betriebssystems** | Englisch (en-us)
**Windows Server-Rollen** | Aktivieren Sie die folgenden Rollen nicht: <br> - Active Directory Domain Services <br>- Internetinformationsdienste <br> - Hyper-V 
**Gruppenrichtlinien** | Aktivieren Sie die folgenden Gruppenrichtlinien nicht: <br> - Zugriff auf Eingabeaufforderung verhindern <br> - Zugriff auf Programme zum Bearbeiten der Registrierung verhindern <br> - Vertrauenslogik für Dateianlagen <br> - Skriptausführung aktivieren <br> [Weitere Informationen](https://technet.microsoft.com/library/gg176671(v=ws.10).aspx)
**IIS** | - Keine bereits vorhandene Standardwebsite <br> - Keine bereits vorhandene Website/Anwendung sollte an Port 443 lauschen <br>- Die [anonyme Authentifizierung](https://technet.microsoft.com/library/cc731244(v=ws.10).aspx) ist aktiviert. <br> - Aktivieren der Einstellung [FastCGI](https://technet.microsoft.com/library/cc753077(v=ws.10).aspx) 
**NETZWERK** | 
**Art der IP-Adresse** | statischen 
**Zugriff auf das Internet** | Der Server benötigt Zugriff auf diese URLs (direkt oder über einen Proxy) <br> - \*.accesscontrol.windows.net<br> - \*.backup.windowsazure.com <br>- \*.store.core.windows.net<br> - \*.blob.core.windows.net<br> - \*.hypervrecoverymanager.windowsazure.com <br> - https://cdn.mysql.com/archives/mysql-5.5/mysql-5.5.37-win32.msi (beim Einrichten eines Konfigurationsservers) <br> - time.nist.gov <br> - time.windows.com 
**Ports** | 443 (Steuerkanalorchestrierung)<br>9443 (Datentransport) 
**VMWARE (beim Einrichten des Konfigurations-/Prozessservers als VMware-VM)**
**NIC-Typ** | VMXNET3  
**VMware vSphere PowerCLI, ausgeführt auf VM* | [PowerCLI-Version 6.0](https://my.vmware.com/web/vmware/details?productId=491&downloadGroup=PCLI600R1 "PowerCLI 6.0")

**Größenanforderungen an den Konfigurations-/Prozessserver**

**CPU** | **Memory** | **Cachedatenträger** | **Datenänderungsrate** | **Replizierte Computer**
--- | --- | --- | --- | ---
8 vCPUs<br/><br/> 2 Sockets * 4 Kerne mit 2,5 GHz | 16 GB | 300 GB | 500 GB oder weniger | < 100 Computer
12 vCPUs<br/><br/> 2 Sockets * 6 Kerne mit 2,5 GHz | 18 GB | 600 GB | 500 GB bis 1 TB | 100 bis 150 Computer
16 vCPUs<br/><br/> 2 Sockets * 8 Kerne mit 2,5 GHz | 32 GB | 1 TB | 1–2 TB | 150–200 Computer

