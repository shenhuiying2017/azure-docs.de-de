---
title: Bewertungsberechnungen in Azure Migrate | Microsoft-Dokumentation
description: Bietet eine Übersicht über Bewertungsberechnungen im Azure Migrate-Dienst.
author: rayne-wiselman
ms.service: azure-migrate
ms.topic: conceptual
ms.date: 06/02/2017
ms.author: raynew
ms.openlocfilehash: f3ac9c328db1130ea25ac63170ee7de35fb67d16
ms.sourcegitcommit: ca05dd10784c0651da12c4d58fb9ad40fdcd9b10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32779344"
---
# <a name="assessment-calculations"></a>Bewertungsberechnungen

[Azure Migrate](migrate-overview.md) bewertet lokale Workloads für die Migration zu Azure. Dieser Artikel enthält Informationen dazu, wie Bewertungen berechnet werden.


## <a name="overview"></a>Übersicht

Eine Azure Migrate-Bewertung erfolgt in drei Phasen. Die Bewertung beginnt mit einer Eignungsanalyse, gefolgt von einer Größenanpassung und abschließend einer Schätzung der monatlichen Kosten. Ein Computer gelangt nur in die nächste Phase, wenn er die vorherige besteht. Beispiel: Besteht ein Computer die Azure-Eignungsprüfung nicht, wird er als ungeeignet für Azure markiert, und die Größen- und Kostenschätzungen werden nicht durchgeführt.


## <a name="azure-suitability-analysis"></a>Azure-Eignungsanalyse

Nicht alle Computer eignen sich für die Ausführung in der Cloud, da die Cloud eigenen Einschränkungen und Anforderungen unterliegt. Azure Migrate bewertet die Eignung jedes lokalen Computers für die Migration zu Azure und stuft die Computer in eine der folgenden Kategorien ein:
- **Bereit für Azure:** Der Computer kann ohne Änderungen zu Azure migriert werden. Er wird in Azure mit vollständiger Azure-Unterstützung gestartet.
- **Bedingt bereit für Azure:** Der Computer kann in Azure gestartet werden, verfügt jedoch möglicherweise nicht über die vollständige Azure-Unterstützung. Beispielsweise wird ein Computer mit einer älteren Version des Windows Server-Betriebssystems in Azure nicht unterstützt. Gehen Sie bei der Migration dieser Computer zu Azure vorsichtig vor, und befolgen Sie die in der Bewertung empfohlene Korrekturanleitung, um die Bereitschaftsprobleme vor der Migration zu beheben.
- **Nicht bereit für Azure:** Der Computer wird in Azure nicht gestartet. Ein lokaler Computer mit einem angefügten Datenträger mit einer Größe von mehr als 4 TB kann beispielsweise in Azure nicht gehostet werden. Sie müssen die in der Bewertung empfohlene Korrekturanleitung befolgen, um die Bereitschaftsprobleme vor der Migration zu Azure zu beheben. Für Computer, die als nicht bereit für Azure markiert sind, werden keine Größen- und Kostenschätzungen durchgeführt.
- **Bereitschaft unbekannt:** Azure Migrate konnte die Bereitschaft des Computers aufgrund unzureichender Daten in vCenter Server nicht finden.

Azure Migrate überprüft die Computereigenschaften und das Gastbetriebssystem, um die Azure-Bereitschaft des lokalen Computers zu ermitteln.

### <a name="machine-properties"></a>Computereigenschaften
Azure Migrate überprüft die folgenden Eigenschaften des lokalen virtuellen Computers, um zu ermitteln, ob der virtuelle Computer in Azure ausgeführt werden kann.

**Eigenschaft** | **Details** | **Azure-Bereitschaftsstatus**
--- | --- | ---
**Starttyp** | Azure unterstützt virtuelle Computer mit dem Starttyp BIOS, jedoch nicht UEFI. | Bedingt bereit für Azure, wenn der Starttyp UEFI ist.
**Kerne** | Die Anzahl der Kerne in den Computern darf maximal der Anzahl der für einen virtuellen Azure-Computer unterstützten Kerne (32) entsprechen.<br/><br/> Wenn der Leistungsverlauf verfügbar ist, berücksichtigt Azure Migrate die genutzten Kerne beim Vergleich. Wenn in den Bewertungseinstellungen ein Komfortfaktor festgelegt ist, wird die Anzahl der genutzten Kerne mit dem Komfortfaktor multipliziert.<br/><br/> Wenn kein Leistungsverlauf vorhanden ist, verwendet Azure Migrate die zugeordneten Kerne ohne Anwendung des Komfortfaktors. | Nicht bereit, wenn die Anzahl der Kerne größer als 32 ist.
**Memory** | Die Größe des Computerarbeitsspeichers darf maximal dem zulässigen Arbeitsspeicher (448 GB) für einen virtuellen Azure-Computer entsprechen. <br/><br/> Wenn der Leistungsverlauf verfügbar ist, berücksichtigt Azure Migrate den genutzten Arbeitsspeicher beim Vergleich. Wenn ein Komfortfaktor festgelegt ist, wird der genutzte Arbeitsspeicher mit dem Komfortfaktor multipliziert.<br/><br/> Wenn kein Verlauf vorhanden ist, wird der zugeordnete Arbeitsspeicher ohne Anwendung des Komfortfaktors verwendet.<br/><br/> | Nicht bereit, wenn die Speichergröße größer als 448 GB ist.
**Speicherdatenträger** | Die zugeteilte Größe eines Datenträgers darf höchstens 4 TB (4096 GB) betragen.<br/><br/> An den Computer dürfen einschließlich des Betriebssystem-Datenträgers höchstens 65 Datenträger angefügt sein. | Nicht bereit, wenn ein Datenträger eine Größe von über 4 TB aufweist oder mehr als 65 Datenträger an den Computer angefügt sind.
**Netzwerk** | An einen Computer dürfen höchstens 32 NICs angefügt sein. | Nicht bereit, wenn der Computer über mehr als 32 NICs verfügt.

### <a name="guest-operating-system"></a>Gastbetriebssystem
Neben den Eigenschaften des virtuellen Computers überprüft Azure Migrate auch das Gastbetriebssystem des lokalen virtuellen Computers, um zu ermitteln, ob der virtuelle Computer in Azure ausgeführt werden kann.

> [!NOTE]
> Azure Migrate überprüft das in vCenter Server angegebene Betriebssystem für die folgende Analyse. Da die von Azure Migrate durchgeführte Ermittlung anwendungsbasiert ist, kann nicht überprüft werden, ob das auf dem virtuellen Computer ausgeführte Betriebssystem identisch mit dem in vCenter Server angegebenen Betriebssystem ist.

Zur Ermittlung der Azure-Bereitschaft des virtuellen Computers basierend auf dem Betriebssystem wird von Azure Migrate folgende Logik verwendet.

**Betriebssystem** | **Details** | **Azure-Bereitschaftsstatus**
--- | --- | ---
Windows Server 2016 und alle SPs | Azure bietet vollständige Unterstützung. | Bereit für Azure
Windows Server 2012 R2 und alle SPs | Azure bietet vollständige Unterstützung. | Bereit für Azure
Windows Server 2012 und alle SPs | Azure bietet vollständige Unterstützung. | Bereit für Azure
Windows Server 2008 R2 mit allen SPs | Azure bietet vollständige Unterstützung.| Bereit für Azure
Windows Server 2003-2008 R2 | Der Unterstützungszeitraum für diese Betriebssysteme ist abgelaufen. Für die Unterstützung in Azure wird eine benutzerdefinierte Supportvereinbarung ([Custom Support Agreement, CSA](https://aka.ms/WSosstatement)) benötigt. | Bedingt bereit für Azure, erwägen Sie ein Upgrade des Betriebssystems vor der Migration zu Azure.
Windows 2000, 98, 95, NT, 3.1, MS-DOS | Der Unterstützungszeitraum für diese Betriebssysteme ist abgelaufen. Der Computer kann in Azure gestartet werden, es wird jedoch keine Unterstützung des Betriebssystems bereitgestellt. | Bedingt bereit für Azure, es empfiehlt sich ein Upgrade des Betriebssystems vor der Migration zu Azure.
Windows Client 7, 8 und 10 | Azure bietet nur mit Visual Studio-Abonnement Unterstützung. | Bedingt bereit für Azure
Windows Vista, XP Professional | Der Unterstützungszeitraum für diese Betriebssysteme ist abgelaufen. Der Computer kann in Azure gestartet werden, es wird jedoch keine Unterstützung des Betriebssystems bereitgestellt. | Bedingt bereit für Azure, es empfiehlt sich ein Upgrade des Betriebssystems vor der Migration zu Azure.
Linux | Azure empfiehlt diese [Linux-Betriebssysteme](../virtual-machines/linux/endorsed-distros.md). Andere Linux-Betriebssysteme können in Azure gestartet werden. Es empfiehlt sich jedoch ein Upgrade des jeweiligen Betriebssystems auf eine unterstützte Version vor der Migration zu Azure. | Bereit für Azure, wenn die Version unterstützt wird.<br/><br/>Bedingt bereit, wenn die Version nicht unterstützt wird.
Andere Betriebssysteme<br/><br/> z.B. Oracle Solaris, Apple macOS, FreeBSD usw. | Azure unterstützt diese Betriebssysteme nicht. Der Computer kann in Azure gestartet werden, es wird jedoch keine Unterstützung des Betriebssystems bereitgestellt. | Bedingt bereit für Azure, es empfiehlt sich die Installation eines unterstützten Betriebssystems vor der Migration zu Azure.  
In vCenter Server als *Sonstige* angegebenes Betriebssystem | In diesem Fall kann Azure Migrate das Betriebssystem nicht identifizieren. | Bereitschaft unbekannt. Stellen Sie sicher, dass das auf dem virtuellen Computer ausgeführte Betriebssystem in Azure unterstützt wird.
32-Bit-Betriebssysteme | Der Computer kann in Azure gestartet werden, Azure bietet jedoch möglicherweise keine vollständige Unterstützung. | Bedingt bereit für Azure, ziehen Sie vor der Migration zu Azure das Aktualisieren des Computerbetriebssystems von 32 Bit auf 64 Bit in Betracht.

## <a name="sizing"></a>Festlegen der Größe

Nachdem ein Computer als bereit für Azure markiert wurde, bestimmt Azure Migrate die Größe des virtuellen Computers und der zugehörigen Datenträger für Azure. Wenn als Größenkriterium in den Bewertungseigenschaften die leistungsbasierte Größenanpassung angegeben ist, berücksichtigt Azure Migrate den Leistungsverlauf des Computers, um eine VM-Größe in Azure zu ermitteln. Diese Methode ist hilfreich in Szenarien, bei denen Sie die lokalen virtuellen Computer überbelegt haben, die Auslastung jedoch gering ist, und Sie die Größe der virtuellen Computer in Azure optimal anpassen möchten, um Kosten zu sparen.

> [!NOTE]
> Azure Migrate erfasst den Leistungsverlauf von lokalen virtuellen Computern von vCenter Server. Stellen Sie für eine genaue Größenanpassung sicher, dass die Statistikeinstellung in vCenter Server auf Stufe 3 festgelegt ist, und warten Sie mindestens einen Tag, bevor Sie die Ermittlung der lokalen virtuellen Computer starten. Wenn die Statistikeinstellung in vCenter Server auf einen Wert unter 3 festgelegt ist, werden keine Leistungsdaten für Datenträger und Netzwerk erfasst.

Wenn der Leistungsverlauf der VM-Skalierung nicht geprüft werden und der virtuelle Computer unverändert zu Azure migriert werden soll, können Sie das Größenkriterium *Wie lokal* angeben. Azure Migrate legt dann die Größe der virtuellen Computer basierend auf der lokalen Konfiguration ohne Berücksichtigung der Nutzungsdaten fest. Die Datenträgergrößenanpassung basiert in diesem Fall weiterhin auf Leistungsdaten.

### <a name="performance-based-sizing"></a>Leistungsbasierte Größenanpassung

Bei der leistungsbasierten Größenanpassung prüft Azure Migrate zunächst die an den virtuellen Computer angefügten Datenträger und dann die Netzwerkadapter und ordnet anschließend basierend auf den Computeanforderungen des lokalen virtuellen Computers einen virtuellen Azure-Computer zu.

- **Speicher**: Azure Migrate versucht, jeden an den Computer angefügten Datenträger einem Datenträger in Azure zuzuordnen.

    > [!NOTE]
    > Azure Migrate unterstützt bei der Bewertung nur verwaltete Datenträger.

    - Für die effektiven E/A-Vorgänge pro Sekunde (IOPS) der Datenträger und den effektiven Durchsatz (MBit/s) multipliziert Azure Migrate die Datenträger-IOPS und den Durchsatz mit dem Komfortfaktor. Basierend auf den effektiven IOPS- und Durchsatzwerten bestimmt Azure Migrate, ob der Datenträger einem Standard- oder Premium-Datenträger in Azure zugeordnet werden soll.
    - Wenn Azure Migrate keinen Datenträger mit den erforderlichen IOPS- und Durchsatzwerten finden kann, wird der Computer als ungeeignet für Azure gekennzeichnet. [Erfahren Sie mehr](../azure-subscription-service-limits.md#storage-limits) über Azure-Grenzwerte pro Datenträger und virtuellem Computer.
    - Wenn mehrere geeignete Datenträger gefunden werden, wählt Azure Migrate diejenigen aus, die die Speicherredundanzmethode sowie den in den Bewertungseinstellungen festgelegten Speicherort unterstützen.
    - Falls mehrere geeignete Datenträger vorhanden sind, werden die mit den geringsten Kosten ausgewählt.
    - Wenn keine Leistungsdaten für Datenträger verfügbar sind, werden alle Datenträger Standard-Datenträgern in Azure zugeordnet.

- **Netzwerk**: Azure Migrate versucht, einen virtuellen Azure-Computer zu finden, der die Anzahl der an den lokalen Computer angefügten Netzwerkadapter und die für diese Netzwerkadapter erforderliche Leistung unterstützen kann.
    - Um die effektive Netzwerkleistung des lokalen virtuellen Computers zu ermitteln, aggregiert Azure Migrate die vom Computer (Netzwerk ausgehend) pro Sekunde übertragenen Daten (MBit/s) für alle Netzwerkadapter und wendet den Komfortfaktor an. Mithilfe dieser Zahl wird ein virtueller Azure-Computer gesucht, der die erforderliche Netzwerkleistung unterstützen kann.
    - Neben der Netzwerkleistung wird zudem geprüft, ob der virtuelle Azure-Computer die erforderliche Anzahl der Netzwerkadapter unterstützen kann.
    - Wenn keine Netzwerkleistungsdaten verfügbar sind, wird bei der Größenanpassung für virtuelle Computer nur die Anzahl der Netzwerkadapter berücksichtigt.

- **Compute**: Nach der Berechnung der Speicher- und Netzwerkanforderungen prüft Azure Migrate die CPU- und Arbeitsspeicheranforderungen, um eine geeignete VM-Größe in Azure zu suchen.
    - Azure Migrate wendet den Komfortfaktor auf die genutzten Kerne und den Arbeitsspeicher an, um so die effektiven Kerne und den effektiven Arbeitsspeicher zu bestimmen. Auf Grundlage dieser Zahl wird versucht, eine geeignete VM-Größe in Azure zu finden.
    - Wenn keine geeignete Größe gefunden wird, wird der Computer als ungeeignet für Azure gekennzeichnet.
    - Wenn eine geeignete Größe gefunden wird, wendet Azure Migrate die Speicher -und Netzwerkberechnungen an. Für die endgültige VM-Größenempfehlung werden dann noch Speicherort- und Tarifeinstellungen angewendet.
    - Wenn mehrere geeignete Azure-VM-Größen vorhanden sind, wird die mit den geringsten Kosten empfohlen.

### <a name="as-on-premises-sizing"></a>Größenanpassung vom Typ „Wie lokal“
Wenn als Größenanpassungskriterium *Wie lokal* angegeben ist, berücksichtigt Azure Migrate den Leistungsverlauf der virtuellen Computer nicht und ordnet virtuelle Computer basierend auf der lokal zugeordneten Größe zu. Für die Datenträger-Größenanpassung wird der Leistungsverlauf der Datenträger allerdings berücksichtigt, um Standard- oder Premium-Datenträger zu empfehlen.  
- **Speicher**: Azure Migrate ordnet jeden an den Computer angefügten Datenträger einem Datenträger in Azure zu.

    > [!NOTE]
    > Azure Migrate unterstützt bei der Bewertung nur verwaltete Datenträger.

    - Für die effektiven E/A-Vorgänge pro Sekunde (IOPS) der Datenträger und den effektiven Durchsatz (MBit/s) multipliziert Azure Migrate die Datenträger-IOPS und den Durchsatz mit dem Komfortfaktor. Basierend auf den effektiven IOPS- und Durchsatzwerten bestimmt Azure Migrate, ob der Datenträger einem Standard- oder Premium-Datenträger in Azure zugeordnet werden soll.
    - Wenn Azure Migrate keinen Datenträger mit den erforderlichen IOPS- und Durchsatzwerten finden kann, wird der Computer als ungeeignet für Azure gekennzeichnet. [Erfahren Sie mehr](../azure-subscription-service-limits.md#storage-limits) über Azure-Grenzwerte pro Datenträger und virtuellem Computer.
    - Wenn mehrere geeignete Datenträger gefunden werden, wählt Azure Migrate diejenigen aus, die die Speicherredundanzmethode sowie den in den Bewertungseinstellungen festgelegten Speicherort unterstützen.
    - Falls mehrere geeignete Datenträger vorhanden sind, werden die mit den geringsten Kosten ausgewählt.
    - Wenn keine Leistungsdaten für Datenträger verfügbar sind, werden alle Datenträger Standard-Datenträgern in Azure zugeordnet.
- **Netzwerk:** Für jeden Netzwerkadapter wird ein Netzwerkadapter in Azure empfohlen.
- **Compute:** Azure Migrate prüft die Anzahl der Kerne und die Arbeitsspeichergröße des lokalen virtuellen Computers und empfiehlt einen virtuellen Azure-Computer mit der gleichen Konfiguration. Wenn mehrere geeignete Azure-VM-Größen vorhanden sind, wird die mit den geringsten Kosten empfohlen. Nutzungsdaten für CPU- und Arbeitsspeicher werden nicht als lokale Größenanpassung angesehen.

### <a name="confidence-rating"></a>Zuverlässigkeitsstufe

Jeder Bewertung in Azure Migrate wird eine Zuverlässigkeitsstufe zugeordnet. Die Skala reicht von einem Stern (niedrigster Wert) bis zu fünf Sternen (höchster Wert). Die Zuverlässigkeitsstufe wird einer Bewertung auf der Grundlage der Verfügbarkeit von Datenpunkten zugeordnet, die zum Berechnen der Bewertung erforderlich sind. Anhand der Zuverlässigkeitsstufe können Sie die Zuverlässigkeit der von Azure Migrate bereitgestellten Größenempfehlungen besser einschätzen.

Bei Verwendung der leistungsbasierten Größenanpassung des virtuellen Computers benötigt Azure Migrate Nutzungsdaten für CPU und Arbeitsspeicher. Außerdem werden bei der Größenanpassung für jeden an den virtuellen Computer angefügten Datenträger Informationen zu den Lese-/Schreib-IOPS sowie zum Durchsatz benötigt. Analog dazu benötigt Azure Migrate für jeden Netzwerkadapter, der an den virtuellen Computer angefügt ist, Informationen zu ein- und ausgehenden Netzwerkdaten, um die leistungsbasierte Größenanpassung durchführen zu können. Steht eine der oben aufgeführten Nutzungsangaben in vCenter Server nicht zur Verfügung, ist die Größenempfehlung von Azure Migrate unter Umständen nicht zuverlässig. Die Zuverlässigkeitsstufe für die Bewertung ist abhängig davon, wie viele Datenpunkte verfügbar sind (in Prozent), wie es nachfolgend angegeben ist:

   **Verfügbarkeit von Datenpunkten** | **Zuverlässigkeitsstufe**
   --- | ---
   0 % bis 20 % | Ein Stern
   21 % bis 40 % | Zwei Sterne
   41 % bis 60 % | Drei Sterne
   61 % bis 80 % | Vier Sterne
   81 % bis 100 % | Fünf Sterne

Dass für eine Bewertung nicht alle Datenpunkte verfügbar sind, kann folgende Ursachen haben:
- Die Statistikeinstellung in vCenter Server ist nicht auf Stufe 3 festgelegt. Wenn die Statistikeinstellung in vCenter Server auf einen Wert unter 3 festgelegt ist, werden von vCenter Server keine Leistungsdaten für Datenträger und Netzwerk erfasst. In diesem Fall ist die Datenträger- und Netzwerkempfehlung von Azure Migrate nicht nutzungsbasiert. Da ohne Berücksichtigung der IOPS/des Durchsatzes nicht ermittelt werden kann, ob der Datenträger einen Premium-Datenträger in Azure benötigt, empfiehlt Azure Migrate Standarddatenträger für alle Datenträger.
- Die Statistikeinstellung in vCenter Server wurde vor dem Start der Ermittlung kurzzeitig auf Stufe 3 festgelegt. Ein Beispiel: Angenommen, Sie haben die Statistikeinstellung heute auf Stufe 3 festgelegt und starten die Ermittlung morgen (also 24 Stunden später) mithilfe der Collectorappliance. Wenn Sie eine Bewertung für einen einzelnen Tag erstellen, verfügen Sie über alle Datenpunkte, und die Zuverlässigkeitsstufe für die Bewertung beträgt fünf Sterne. Wenn Sie die Leistungsdauer in den Bewertungseigenschaften jedoch auf einen Monat festlegen, führt dies zu einer niedrigeren Zuverlässigkeitsstufe, da für den letzten Monat keine Datenträger- und Netzwerkleistungsdaten vorliegen. Wenn Sie die Leistungsdaten des letzten Monats berücksichtigen möchten, empfiehlt es sich, die Statistikeinstellung in vCenter Server vor Beginn der Ermittlung einen Monat lang auf Stufe 3 festzulegen.
- Einige virtuelle Computer wurden während des Zeitraums, für den die Bewertung berechnet wird, heruntergefahren. Wenn ein virtueller Computer für eine gewisse Zeit heruntergefahren wird, liegen vCenter Server für diesen Zeitraum keine Leistungsdaten vor.
- Einige virtuelle Computer wurden während des Zeitraums, für den die Bewertung berechnet wird, erstellt. Ein Beispiel: Angenommen, Sie erstellen eine Bewertung für den Leistungsverlauf des letzten Monats, und in der Umgebung wurden letzte Woche einige virtuelle Computer erstellt. In solchen Fällen liegt für die neuen virtuellen Computer kein Leistungsverlauf für den gesamten Zeitraum vor.

> [!NOTE]
> Bei einer Zuverlässigkeitsstufe von weniger als vier Sternen empfiehlt es sich, die Statistikeinstellungen in vCenter Server auf Stufe 3 festzulegen und mit der Ermittlung und Bewertung so lange zu warten, bis Daten für den gewünschten Zeitraum (ein Tag/eine Woche/ein Monat) vorliegen. Sollte das nicht möglich sein, ist die leistungsbasierte Größenanpassung möglicherweise nicht zuverlässig, und es empfiehlt sich, in den Bewertungseigenschaften stattdessen die Größenanpassung vom Typ *Wie lokal* festzulegen.

## <a name="monthly-cost-estimation"></a>Schätzung der monatlichen Kosten

Nach Abschluss der Größenempfehlungen berechnet Azure Migrate die Computer- und Speicherkosten nach der Migration.

- **Computekosten**: Azure Migrate berechnet anhand der empfohlenen Azure-VM-Größe mithilfe der Abrechnungs-API die monatlichen Kosten für den virtuellen Computer. Bei der Berechnung werden Betriebssystem-, Software Assurance-, Standort- und Währungseinstellungen berücksichtigt. Die Kosten aller Computer werden zusammengefasst, um die monatlichen Gesamtcomputekosten zu berechnen.
- **Speicherkosten**: Die monatlichen Speicherkosten für einen Computer werden berechnet, indem die monatlichen Kosten aller an den Computer angefügten Datenträger zusammengefasst werden. Azure Migrate berechnet die gesamten monatlichen Speicherkosten durch Aggregieren der Speicherkosten aller Computer. Derzeit werden bei der Berechnung keine Angebote berücksichtigt, die in den Bewertungseinstellungen angegeben sind.

Kosten werden in der Währung angezeigt, die in den Bewertungseinstellungen festgelegt ist.


## <a name="next-steps"></a>Nächste Schritte

[Erstellen einer Bewertung für lokale virtuelle VMware-Computer](tutorial-assessment-vmware.md)
