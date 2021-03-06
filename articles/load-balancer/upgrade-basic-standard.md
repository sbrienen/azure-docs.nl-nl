---
title: Voer een upgrade uit van Basic Public naar Standard Public-Azure Load Balancer
description: In dit artikel wordt beschreven hoe u een upgrade uitvoert van de open bare Azure-Load Balancer van de Basic-SKU naar de standaard-SKU
services: load-balancer
author: irenehua
ms.service: load-balancer
ms.topic: how-to
ms.date: 01/23/2020
ms.author: irenehua
ms.openlocfilehash: dd0617536147787f436e5817f3f2367a19ba6aa4
ms.sourcegitcommit: a43a59e44c14d349d597c3d2fd2bc779989c71d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96009276"
---
# <a name="upgrade-azure-public-load-balancer"></a>Open bare Azure-Load Balancer bijwerken
[Azure Standard Load Balancer](load-balancer-overview.md) biedt een uitgebreide set functionaliteit en hoge Beschik baarheid via zone redundantie. Zie [vergelijkings tabel](./skus.md#skus)voor meer informatie over Load Balancer SKU.

Er zijn drie fasen in een upgrade:

1. De configuratie migreren
2. Vm's toevoegen aan back-endservers van Standard Load Balancer

In dit artikel wordt beschreven hoe u de configuratie migreert. Het toevoegen van Vm's aan back-endservers kan variëren, afhankelijk van uw specifieke omgeving. Er zijn echter algemene aanbevelingen [van](#add-vms-to-backend-pools-of-standard-load-balancer)een hoog niveau.

## <a name="upgrade-overview"></a>Overzicht van de upgrade

Er is een Azure PowerShell script beschikbaar dat het volgende doet:

* Hiermee maakt u een standaard SKU-Load Balancer in de resource groep en de locatie die u opgeeft.
* Hiermee worden de configuraties van de basis-SKU Load Balancer naadloos gekopieerd naar de zojuist gemaakte Standard Load Balancer.
* Hiermee maakt u een standaard regel voor uitgaand verkeer waarmee uitgaande verbindingen mogelijk worden gemaakt.

### <a name="caveatslimitations"></a>Caveats\Limitations

* Script ondersteunt alleen Public Load Balancer upgrade. Raadpleeg [Deze pagina](./upgrade-basicinternal-standard.md) voor instructies voor interne basis Load Balancer upgrade.
* Het Standard Load Balancer heeft een nieuw openbaar adres. Het is niet mogelijk om de IP-adressen die zijn gekoppeld aan de bestaande basis Load Balancer naadloos te verplaatsen naar Standard Load Balancer omdat ze verschillende Sku's hebben.
* Als de standaard load balancer in een andere regio wordt gemaakt, kunt u de virtuele machines die in de oude regio bestaan, niet koppelen aan de zojuist gemaakte Standard Load Balancer. Om deze beperking te omzeilen, moet u ervoor zorgen dat u een nieuwe virtuele machine maakt in de nieuwe regio.
* Als uw Load Balancer geen frontend-IP-configuratie of back-end-pool heeft, zult u waarschijnlijk een fout bij het uitvoeren van het script aangaan. Zorg ervoor dat deze niet leeg zijn.

## <a name="download-the-script"></a>Het script downloaden

Down load het migratie script van de  [PowerShell Gallery](https://www.powershellgallery.com/packages/AzurePublicLBUpgrade/2.0).
## <a name="use-the-script"></a>Het script gebruiken

Er zijn twee opties voor u afhankelijk van de instellingen en voor keuren van uw lokale Power shell-omgeving:

* Als u de Azure AZ-modules niet hebt geïnstalleerd of als u niet van mening bent dat u de Azure AZ-modules verwijdert, kunt u het beste de `Install-Script` optie gebruiken om het script uit te voeren.
* Als u de Azure AZ-modules wilt blijven gebruiken, is het verstandig om het script te downloaden en het rechtstreeks uit te voeren.

Als u wilt weten of u de Azure AZ-modules hebt geïnstalleerd, voert u uit `Get-InstalledModule -Name az` . Als er geen geïnstalleerde AZ-modules worden weer geven, kunt u de- `Install-Script` methode gebruiken.

### <a name="install-using-the-install-script-method"></a>Installeren met behulp van de Install-Script methode

Als u deze optie wilt gebruiken, moet u de Azure AZ-modules niet op uw computer installeren. Als ze zijn geïnstalleerd, wordt een fout weer gegeven in de volgende opdracht. U kunt de Azure AZ-modules verwijderen of de andere optie gebruiken om het script hand matig te downloaden en uit te voeren.
  
Voer het script uit met de volgende opdracht:

`Install-Script -Name AzurePublicLBUpgrade`

Met deze opdracht worden ook de vereiste AZ-modules geïnstalleerd.  

### <a name="install-using-the-script-directly"></a>Rechtstreeks installeren met behulp van het script

Als er sommige Azure AZ-modules zijn geïnstalleerd en deze niet kunnen verwijderen (of niet wilt verwijderen), kunt u het script hand matig downloaden met het tabblad **hand matig downloaden** in de koppeling voor het downloaden van het script. Het script wordt gedownload als een onbewerkt nupkg-bestand. Zie [hand matig downloaden van pakketten](/powershell/scripting/gallery/how-to/working-with-packages/manual-download)als u het script wilt installeren vanuit dit nupkg-bestand.

Het script uitvoeren:

1. Gebruiken `Connect-AzAccount` om verbinding te maken met Azure.

1. Gebruiken `Import-Module Az` voor het importeren van de AZ-modules.

1. Controleer de vereiste para meters:

   * **oldRgName: [teken reeks]: vereist** – dit is de resource groep voor de bestaande basis Load Balancer u een upgrade wilt uitvoeren. Als u deze teken reeks waarde wilt vinden, gaat u naar Azure Portal, selecteert u de basis Load Balancer bron en klikt u op het **overzicht** van de Load Balancer. De resource groep bevindt zich op deze pagina.
   * **oldLBName: [teken reeks]: vereist** – dit is de naam van de bestaande Basic-Balancer die u wilt bijwerken. 
   * **newrgName: [teken reeks]: vereist** – dit is de resource groep waarin de Standard Load Balancer worden gemaakt. Dit kan een nieuwe resource groep of een bestaande zijn. Als u een bestaande resource groep kiest, moet u er rekening mee houden dat de naam van de Load Balancer uniek moeten zijn binnen de resource groep. 
   * **newlocation: [string]: vereist** : dit is de locatie waar de Standard Load Balancer wordt gemaakt. Het wordt aanbevolen om dezelfde locatie van de gekozen basis Load Balancer over te nemen naar de Standard Load Balancer voor een betere koppeling met andere bestaande resources.
   * **newLBName: [string]: vereist** : dit is de naam voor de Standard Load Balancer die u wilt maken.
1. Voer het script uit met de juiste para meters. Het kan vijf tot zeven minuten duren voordat de bewerking is voltooid.

    **Voorbeeld**

   ```azurepowershell
   AzurePublicLBUpgrade.ps1 -oldRgName "test_publicUpgrade_rg" -oldLBName "LBForPublic" -newrgName "test_userInput3_rg" -newlocation "centralus" -newLbName "LBForUpgrade"
   ```

### <a name="add-vms-to-backend-pools-of-standard-load-balancer"></a>Vm's toevoegen aan back-endservers van Standard Load Balancer

Controleer eerst of het script een nieuwe standaard open bare Load Balancer heeft gemaakt met de exacte configuratie die is gemigreerd via uw open bare basis Load Balancer. U kunt dit controleren vanuit het Azure Portal.

Zorg ervoor dat u een kleine hoeveelheid verkeer verzendt via de Standard Load Balancer als hand matige test.
  
Hier volgen enkele scenario's voor het toevoegen van Vm's aan back-endservers van de nieuwe open bare standaard-Load Balancer kunnen worden geconfigureerd en onze aanbevelingen voor elk van deze:

* **Het verplaatsen van bestaande vm's van back-endservers van oude basis-open bare Load Balancer naar back-end-Pools van zojuist gemaakte standaard open bare Load Balancer**.
    1. Als u de taken in deze quickstart wilt uitvoeren, moet u zich aanmelden bij de [Azure-portal](https://portal.azure.com).
 
    1. Selecteer **alle resources** in het menu links en selecteer vervolgens de **nieuw gemaakte Standard Load Balancer** in de lijst met resources.
   
    1. Selecteer **Back-endgroepen** in **Instellingen**.
   
    1. Selecteer de back-end-groep die overeenkomt met de back-end-groep van de basis Load Balancer en selecteer de volgende waarde: 
      - **Virtuele machine**: vervolg keuzelijst en selecteer de virtuele machines uit de bijbehorende back-end-groep van de basis Load Balancer.
    1. Selecteer **Opslaan**.
    >[!NOTE]
    >Voor Vm's met open bare Ip's moet u eerst standaard IP-adressen maken waarbij hetzelfde IP-adres niet gegarandeerd is. Koppel Vm's uit Basic Ip's en koppel deze aan de zojuist gemaakte standaard IP-adressen. Daarna kunt u de instructies volgen om Vm's toe te voegen aan de back-end-groep van Standard Load Balancer. 

* **Nieuwe Vm's maken om toe te voegen aan de back-endservers van de zojuist gemaakte standaard open bare Load Balancer**.
    * Meer instructies voor het maken van een VM en het koppelen hiervan aan Standard Load Balancer vindt u [hier](./quickstart-load-balancer-standard-public-portal.md#create-virtual-machines).

### <a name="create-an-outbound-rule-for-outbound-connection"></a>Een uitgaande regel voor de uitgaande verbinding maken

Volg de [instructies](./quickstart-load-balancer-standard-public-powershell.md#create-outbound-rule-configuration) voor het maken van een uitgaande regel, zodat u kunt
* Geef de uitgaande NAT van een geheel nieuwe definitie op.
* Het gedrag van bestaande uitgaande NAT schalen en afstemmen.

## <a name="common-questions"></a>Veelgestelde vragen

### <a name="are-there-any-limitations-with-the-azure-powershell-script-to-migrate-the-configuration-from-v1-to-v2"></a>Zijn er beperkingen met het Azure PowerShell script voor het migreren van de configuratie van v1 naar v2?

Ja. Zie [aanvullende informatie/beperkingen](#caveatslimitations).

### <a name="does-the-azure-powershell-script-also-switch-over-the-traffic-from-my-basic-load-balancer-to-the-newly-created-standard-load-balancer"></a>Schakelt het Azure PowerShell script ook over op het verkeer van mijn basis Load Balancer naar de zojuist gemaakte Standard Load Balancer?

Nee. Met het Azure PowerShell script wordt de configuratie alleen gemigreerd. De werkelijke verkeers migratie is uw verantwoordelijkheid en in uw besturings element.

### <a name="i-ran-into-some-issues-with-using-this-script-how-can-i-get-help"></a>Er zijn problemen opgetreden bij het gebruik van dit script. Hoe kan ik hulp krijgen?
  
U kunt een e-mail verzenden naar slbupgradesupport@microsoft.com , een ondersteunings aanvraag openen met ondersteuning voor Azure of beide.

## <a name="next-steps"></a>Volgende stappen

[Meer informatie over Standard Load Balancer](load-balancer-overview.md)