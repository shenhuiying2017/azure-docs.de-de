---
title: Hinzufügen und Entfernen eines VM-Images für Azure Stack | Microsoft-Dokumentation
description: Fügen Sie das benutzerdefinierte Windows- oder Linux-VM-Image Ihrer Organisation hinzu, damit es von Mandanten verwendet werden kann, oder entfernen Sie es.
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
editor: ''
ms.assetid: e5a4236b-1b32-4ee6-9aaa-fcde297a020f
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: PowerShell
ms.topic: get-started-article
ms.date: 05/10/2018
ms.author: mabrigg
ms.reviewer: kivenkat
ms.openlocfilehash: 39708248160b029185b64ed927a453562e1003f2
ms.sourcegitcommit: fc64acba9d9b9784e3662327414e5fe7bd3e972e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2018
---
# <a name="make-a-virtual-machine-image-available-in-azure-stack"></a>Verfügbarmachen eines VM-Images in Azure Stack

*Gilt für: integrierte Azure Stack-Systeme und Azure Stack Development Kit*

In Azure Stack können Sie VM-Images für Ihre Benutzer verfügbar machen. Auf diese Images kann durch Azure Resource Manager-Vorlagen verwiesen werden, sie können aber auch der Azure Marketplace-Benutzeroberfläche als Marketplace-Element hinzugefügt werden. Sie können entweder ein Image vom globalen Azure Marketplace verwenden oder Ihr eigenes benutzerdefiniertes Image hinzufügen. Sie können einen virtuellen Computer über das Portal oder Windows PowerShell hinzufügen.

## <a name="add-a-vm-image-through-the-portal"></a>Hinzufügen eines VM-Images über das Portal

> [!NOTE]
> Mit dieser Methode muss das Marketplace-Element separat erstellt werden.

Auf Images muss über einen Blobspeicher-URI verwiesen werden können. Bereiten Sie ein Image mit Windows- oder Linux-Betriebssystem im VHD-Format (nicht VHDX) vor, und laden Sie es anschließend in ein Speicherkonto in Azure oder Azure Stack hoch. Falls Ihr Image bereits in den Blobspeicher in Azure oder Azure Stack hochgeladen wurde, können Sie Schritt 1 überspringen.

1. [Laden Sie für Resource Manager-Bereitstellungen ein Windows-VM-Image in Azure hoch](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-upload-image/), oder gehen Sie für ein Linux-Image wie unter [Hinzufügen von Linux-Images zu Azure Stack](azure-stack-linux.md) beschrieben vor. Berücksichtigen Sie vor dem Hochladen des Images unbedingt folgende Faktoren:

   - Azure Stack unterstützt das VHD-Format für Datenträger mit fester Größe. Bei diesem Format wird der logische Datenträger in der Datei linear strukturiert, sodass das Datenträger-Offset X beim Blob-Offset X gespeichert wird. Die Eigenschaften der VHD werden in einer kleinen Fußzeile am Ende des Blobs beschrieben. Ob es sich bei Ihrem Datenträger um einen Datenträger mit fester Größe handelt, können Sie mithilfe des PowerShell-Befehls [Get-VHD](https://docs.microsoft.com/powershell/module/hyper-v/get-vhd?view=win10-ps) ermitteln.  

    > [!IMPORTANT]
    >  Azure Stack unterstützt keine dynamischen VHDs. Die Anpassung der Größe eines dynamischen Datenträgers, der an einen virtuellen Computer angefügt ist, führt zu einem Fehler. Löschen Sie in diesem Fall den virtuellen Computer, ohne jedoch seinen Datenträger (ein VHD-Blob in einem Speicherkonto) zu löschen. Konvertieren Sie dann die virtuelle Festplatte von einem dynamischen Datenträger in einen Datenträger mit fester Größe, und erstellen Sie den virtuellen Computer neu.

   * Es ist effizienter, ein Image in den Azure Stack-Blobspeicher als in Azure Blob Storage hochzuladen, da die Übertragung des Images per Push in das Azure Stack-Image-Repository schneller geht.

   * Ersetzen Sie beim Hochladen des [Windows-VM-Images](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-upload-image/) den Schritt **Anmelden bei Azure** durch den Schritt [Konfigurieren der PowerShell-Umgebung des Azure Stack-Betreibers](azure-stack-powershell-configure-admin.md).  

   * Notieren Sie sich den URI des Blobspeichers, in den Sie das Image hochladen. Der Blobspeicher-URI hat folgendes Format: *&lt;Speicherkonto&gt;/&lt;Blobcontainer&gt;/&lt;Ziel-VHD-Name&gt;*.vhd.

   * Damit auf das Blob anonym zugegriffen werden kann, navigieren Sie zum Speicherkonto-Blobcontainer, in den die VM-Image-VHD hochgeladen wurde. Klicken Sie auf **Blob** und anschließend auf **Zugriffsrichtlinie**. Sie können optional auch eine Shared Access Signature für den Container generieren und in den Blob-URI aufnehmen.

   ![Navigieren zu Speicherkontoblobs](./media/azure-stack-add-vm-image/image1.png)

   ![Festlegen des öffentlichen Blobzugriffs](./media/azure-stack-add-vm-image/image2.png)

2. Melden Sie sich bei Azure Stack als Bediener an. Klicken Sie im Menü auf **Weitere Dienste** > **Ressourcenanbieter**. Klicken Sie anschließend auf **Compute** > **VM-Images** > **Hinzufügen**.

3. Geben Sie unter **Add a VM Image** (VM-Image hinzufügen) den Herausgeber, das Angebot, die SKU und die Version des VM-Images ein. Diese Namenssegmente verweisen in Resource Manager-Vorlagen auf das VM-Image. Wählen Sie den korrekten Wert für **osType** aus. Geben Sie unter **OS Disk Blob URI** (Blob-URI des Betriebssystemdatenträgers) den Blob-URI ein, an den das Image hochgeladen wurde. Klicken Sie anschließend auf **Erstellen**, um mit der Erstellung des VM-Images zu beginnen.

   ![Starten der Imageerstellung](./media/azure-stack-add-vm-image/image4.png)

   Nach Erstellung des Images ändert sich der VM-Imagestatus in **Erfolgreich**.

4. Damit über die Benutzeroberfläche leichter auf das VM-Image zugegriffen werden kann, empfiehlt sich die [Erstellung eines Marketplace-Elements](azure-stack-create-and-publish-marketplace-item.md).

## <a name="remove-a-vm-image-through-the-portal"></a>Entfernen eines VM-Images über das Portal

1. Öffnen Sie das Verwaltungsportal unter [https://adminportal.local.azurestack.external](https://adminportal.local.azurestack.external).

2. Wählen Sie **Marketplace-Verwaltung** und dann die VM, die Sie löschen möchten.

3. Klicken Sie auf **Löschen**.

## <a name="add-a-vm-image-to-the-marketplace-by-using-powershell"></a>Hinzufügen eines VM-Images zum Marketplace mit PowerShell

1. [Installieren Sie PowerShell für Azure Stack](azure-stack-powershell-install.md).  

2. Melden Sie sich an Azure Stack als Bediener an. Eine entsprechende Anleitung finden Sie unter [Konfigurieren der PowerShell-Umgebung des Azure Stack-Betreibers](azure-stack-powershell-configure-admin.md).

3. Öffnen Sie PowerShell mit einer Eingabeaufforderung mit erhöhten Rechten, und führen Sie Folgendes aus:

  ````PowerShell  
    Add-AzsPlatformimage -publisher "<publisher>" `
      -offer "<offer>" `
      -sku "<sku>" `
      -version "<#.#.#>” `
      -OSType "<ostype>" `
      -OSUri "<osuri>"
  ````

  Mit dem **Add-AzsPlatformimage**-Cmdlet werden Werte angegeben, die von den Azure Resource Manager-Vorlagen zum Verweisen auf das VM-Image verwendet werden. Hierzu gehören folgende Werte:
  - **publisher**  
    Beispiel: `Canonical`  
    Das von Benutzern bei der Bereitstellung des VM-Images verwendete Segment mit dem Herausgebernamen. Beispiel: **Microsoft**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
  - **offer**  
    Beispiel: `UbuntuServer`  
    Das von Benutzern bei der Bereitstellung des VM-Images verwendete Segment mit dem Angebotsnamen. Beispiel: **WindowsServer**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
  - **sku**  
    Beispiel: `14.04.3-LTS`  
    Das von Benutzern bei der Bereitstellung des VM-Images verwendete Segment mit dem SKU-Namen. Beispiel: **Datacenter2016**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
  - **version**  
    Beispiel: `1.0.0`  
    Die von Benutzern bei der Bereitstellung des VM-Images verwendete Version des VM-Images. Diese Version wird im Format *\#.\#.\#* angegeben. Beispiel: **1.0.0**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
  - **osType**  
    Beispiel: `Linux`  
    Als Betriebssystemtyp des Images muss **Windows** oder **Linux** angegeben werden.  
  - **OSUri**  
    Beispiel: `https://storageaccount.blob.core.windows.net/vhds/Ubuntu1404.vhd`  
    Sie können einen Blobspeicher-URI für ein `osDisk`-Element angeben.  

    Weitere Informationen zum Add-AzsPlatformimage-Cmdlet finden Sie in der [Dokumentation zum Azure Stack-Bedienermodul](https://docs.microsoft.com/powershell/module/) für Microsoft PowerShell.

## <a name="add-a-custom-vm-image-to-the-marketplace-by-using-powershell"></a>Hinzufügen eines benutzerdefinierten VM-Images zum Marketplace mit PowerShell

1. [Installieren Sie PowerShell für Azure Stack](azure-stack-powershell-install.md).

  ```PowerShell  
    # Create the Azure Stack operator's Azure Resource Manager environment by using the following cmdlet:
    Add-AzureRMEnvironment `
      -Name "AzureStackAdmin" `
      -ArmEndpoint $ArmEndpoint

    Set-AzureRmEnvironment `
      -Name "AzureStackAdmin" `
      -GraphAudience $GraphAudience

    $TenantID = Get-AzsDirectoryTenantId `
      -AADTenantName "<myDirectoryTenantName>.onmicrosoft.com" `
      -EnvironmentName AzureStackAdmin

    Add-AzureRmAccount `
      -EnvironmentName "AzureStackAdmin" `
      -TenantId $TenantID
  ```

2. Verwenden Sie bei Nutzung der **Active Directory-Verbunddienste (AD FS)** das folgende Cmdlet:

  ```PowerShell
  # For Azure Stack Development Kit, this value is set to https://adminmanagement.local.azurestack.external. To get this value for Azure Stack integrated systems, contact your service provider.
  $ArmEndpoint = "<Resource Manager endpoint for your environment>"

  # For Azure Stack Development Kit, this value is set to https://graph.local.azurestack.external/. To get this value for Azure Stack integrated systems, contact your service provider.
  $GraphAudience = "<GraphAuidence endpoint for your environment>"

  # Create the Azure Stack operator's Azure Resource Manager environment by using the following cmdlet:
  Add-AzureRMEnvironment `
    -Name "AzureStackAdmin" `
    -ArmEndpoint $ArmEndpoint
    ```

3. Melden Sie sich an Azure Stack als Bediener an. Eine entsprechende Anleitung finden Sie unter [Konfigurieren der PowerShell-Umgebung des Azure Stack-Betreibers](azure-stack-powershell-configure-admin.md).

4. Erstellen Sie ein Speicherkonto in der globalen Azure- oder Azure Stack-Instanz, um Ihr benutzerdefiniertes VM-Image zu speichern. Eine Anleitung finden Sie unter [Schnellstart: Hochladen, Herunterladen und Auflisten von Blobs über das Azure-Portal](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal).

5. Bereiten Sie ein Windows- oder Linux-Betriebssystemimage im VHD-Format (nicht VHDX) vor, laden Sie das Image in Ihr Speicherkonto hoch, und rufen Sie den URI ab, über den das VM-Image per PowerShell abgerufen werden kann.  

  ````PowerShell  
    Add-AzureRmAccount `
      -EnvironmentName "AzureStackAdmin" `
      -TenantId $TenantID
  ````

6. (Optional) Sie können als Teil des VM-Images ein Array mit Datenträgern für Daten hochladen. Erstellen Sie Ihre Datenträger für Daten mit dem New-DataDiskObject-Cmdlet. Öffnen Sie PowerShell über eine Eingabeaufforderung mit erhöhten Rechten, und führen Sie Folgendes aus:

  ````PowerShell  
    New-DataDiskObject -Lun 2 `
    -Uri "https://storageaccount.blob.core.windows.net/vhds/Datadisk.vhd"
  ````

7. Öffnen Sie PowerShell mit einer Eingabeaufforderung mit erhöhten Rechten, und führen Sie Folgendes aus:

  ````PowerShell  
    Add-AzsPlatformimage -publisher "<publisher>" -offer "<offer>" -sku "<sku>" -version "<#.#.#>” -OSType "<ostype>" -OSUri "<osuri>"
  ````

    Weitere Informationen zum Add-AzsPlatformimage- und New-DataDiskObject-Cmdlet finden Sie in der [Dokumentation zum Azure Stack-Bedienermodul](https://docs.microsoft.com/powershell/module/) für Microsoft PowerShell.

## <a name="remove-a-vm-image-by-using-powershell"></a>Entfernen eines VM-Images mithilfe von PowerShell

Wenn Sie das hochgeladene VM-Image nicht mehr benötigen, können Sie es im Marketplace mithilfe des folgenden Cmdlets löschen:

1. [Installieren Sie PowerShell für Azure Stack](azure-stack-powershell-install.md).

2. Melden Sie sich an Azure Stack als Bediener an.

3. Öffnen Sie PowerShell mit einer Eingabeaufforderung mit erhöhten Rechten, und führen Sie Folgendes aus:

  ````PowerShell  
  Remove-AzsPlatformImage `
    -publisher "<publisher>" `
    -offer "<offer>" `
    -sku "<sku>" `
    -version "<version>" `
  ````
  Mit dem **Remove-AzsPlatformImage**-Cmdlet werden Werte angegeben, die von den Azure Resource Manager-Vorlagen zum Verweisen auf das VM-Image verwendet werden. Hierzu gehören folgende Werte:
  - **publisher**  
    Beispiel: `Canonical`  
    Das von Benutzern bei der Bereitstellung des VM-Images verwendete Segment mit dem Herausgebernamen. Beispiel: **Microsoft**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
  - **offer**  
    Beispiel: `UbuntuServer`  
    Das von Benutzern bei der Bereitstellung des VM-Images verwendete Segment mit dem Angebotsnamen. Beispiel: **WindowsServer**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
  - **sku**  
    Beispiel: `14.04.3-LTS`  
    Das von Benutzern bei der Bereitstellung des VM-Images verwendete Segment mit dem SKU-Namen. Beispiel: **Datacenter2016**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
  - **version**  
    Beispiel: `1.0.0`  
    Die von Benutzern bei der Bereitstellung des VM-Images verwendete Version des VM-Images. Diese Version wird im Format *\#.\#.\#* angegeben. Beispiel: **1.0.0**. Dieses Feld darf kein Leerzeichen und kein anderes Sonderzeichen enthalten.  
    
    Weitere Informationen zum Remove-AzsPlatformImage-Cmdlet finden Sie in der [Dokumentation zum Azure Stack-Bedienermodul](https://docs.microsoft.com/powershell/module/) für Microsoft PowerShell.

## <a name="next-steps"></a>Nächste Schritte

[Bereitstellen von virtuellen Computern](azure-stack-provision-vm.md)