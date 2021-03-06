---
title: Wat is Azure Firewall Manager?
description: Meer informatie over Azure Firewall Manager-functies
author: vhorne
ms.service: firewall-manager
services: firewall-manager
ms.topic: overview
ms.date: 09/30/2020
ms.author: victorh
ms.openlocfilehash: 00a84fbf694a58128712abf806ff12df96f0e5e9
ms.sourcegitcommit: eb6bef1274b9e6390c7a77ff69bf6a3b94e827fc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/05/2020
ms.locfileid: "91596690"
---
# <a name="what-is-azure-firewall-manager"></a>Wat is Azure Firewall Manager?

Azure Firewall Manager is een service voor beveiligingsbeheer die centraal beveiligingsbeleid en routebeheer biedt voor op cloud gebaseerde beveiligingsperimeters. 

Firewall Manager biedt beveiligingsbeheer voor twee soorten netwerkarchitectuur:

- **Beveiligde virtuele hub**

   Een [Azure Virtual WAN-hub](../virtual-wan/virtual-wan-about.md#resources) is een door Microsoft beheerde resource waarmee u eenvoudig sterarchitecturen kunt maken. Wanneer aan zo'n hub beveiligings- en routeringsbeleid is gekoppeld, wordt dit een *[beveiligde virtuele hub](secured-virtual-hub.md)* genoemd. 
- **Virtueel hubnetwerk**

   Dit is een standaard virtueel Azure-netwerk dat u zelf maakt en beheert. Wanneer beveiligingsbeleidsregels met een dergelijke hub worden gekoppeld, wordt dit een *virtueel hubnetwerk* genoemd. Op dit ogenblik wordt alleen Azure Firewall-beleid ondersteund. U kunt virtuele spaaknetwerken met uw workloadservers en services via peering verbinden. U kunt ook firewalls beheren in zelfstandige virtuele netwerken die niet aan een spaak zijn gekoppeld.

Zie [Wat zijn de opties voor de Azure Firewall Manager-architectuur?](vhubs-and-vnets.md) voor een gedetailleerde vergelijking van architecturen voor *beveiligde virtuele hubs* en *virtuele hubnetwerken*.

![firewall-manager](media/overview/trusted-security-partners.png)

## <a name="azure-firewall-manager-features"></a>Functies van Azure Firewall Manager

Azure Firewall Manager biedt de volgende functies:

### <a name="central-azure-firewall-deployment-and-configuration"></a>Centrale implementatie en configuratie van Azure Firewall

U kunt meerdere Azure Firewall-instanties die over verschillende Azure-regio's en abonnementen zijn verspreid, centraal implementeren en configureren. 

### <a name="hierarchical-policies-global-and-local"></a>Hiërarchische beleidsregels (globaal en lokaal)

U kunt Azure Firewall Manager gebruiken om Azure Firewall-beleidsregels centraal te beheren via meerdere beveiligde virtuele hubs. Uw centrale IT-teams kunnen globale firewallbeleidsregels opstellen om organisatiebreed firewallbeleid af te dwingen voor alle teams. Met lokaal opgestelde firewallbeleidsregels kan een DevOps-selfservicemodel worden gebruikt voor betere flexibiliteit.

### <a name="integrated-with-third-party-security-as-a-service-for-advanced-security"></a>Geïntegreerd met externe Security as a Service voor geavanceerde beveiliging

Naast Azure Firewall kunt u externe SECaaS-providers (Security as a Service) integreren voor aanvullende netwerkbeveiliging voor uw VNet en vertakte internetverbindingen.

Deze functie is alleen beschikbaar voor implementaties van beveiligde virtuele hubs.

- Verkeer van VNet naar internet (V2I) filteren

   - Filter uitgaand verkeer vanaf het virtuele netwerk met uw favoriete externe beveiligingsprovider.
   - Maak gebruik van geavanceerde op de gebruiker gerichte internetbeveiliging voor uw cloudworkloads die in Azure worden uitgevoerd.

- Verkeer van een vertakking naar internet (B2I) filteren

   Maak gebruik van uw Azure-connectiviteit en globale distributie om eenvoudig externe filters toe te voegen voor scenario's met verkeer van aftakkingen naar internet.

Zie [Wat zijn Azure Firewall Manager-beveiligingspartnerproviders?](trusted-security-partners.md) voor meer informatie over beveiligingspartnerproviders

### <a name="centralized-route-management"></a>Gecentraliseerd routebeheer

Stuur verkeer eenvoudig door naar uw beveiligde hub om te worden gefilterd en in een logboek te worden vastgelegd zonder handmatig UDR's (door de gebruiker gedefinieerde routes) te hoeven instellen in virtuele spaaknetwerken. 

Deze functie is alleen beschikbaar voor implementaties van beveiligde virtuele hubs.

U kunt externe providers gebruiken voor het filteren van het verkeer van vertakkingen naar internet (B2I), tegelijk met Azure Firewall voor verkeer van aftakkingen naar VNet (B2V), verkeer van VNet naar VNet (V2V) en verkeer van VNet naar internet (V2I). U kunt ook externe providers voor het filteren van V2I-verkeer gebruiken, zolang Azure Firewall maar niet is vereist voor B2V of V2V. 

## <a name="region-availability"></a>Beschikbaarheid in regio’s

Azure Firewall-beleidsregels kunnen voor meerdere regio's worden gebruikt. U kunt bijvoorbeeld een beleid maken in US - west en dit vervolgens gebruiken in US - oost. 

## <a name="known-issues"></a>Bekende problemen

Azure Firewall Manager heeft de volgende bekende problemen:

|Probleem  |Beschrijving  |Oplossing  |
|---------|---------|---------|
|Opsplitsen van verkeer|Het opsplitsen van verkeer met Microsoft 365 en Azure Public PaaS wordt momenteel niet ondersteund. Als u een provider van derden voor V2I of B2I selecteert, wordt daardoor ook al het Azure Public PaaS- en Microsoft 365-verkeer via de partnerservice verzonden.|Het opsplitsen van verkeer bij de hub wordt momenteel onderzocht.
|Eén beveiligde virtuele hub per regio|U mag niet meer dan één beveiligde virtuele hub per regio hebben.|Maak meerdere virtuele WAN's in een regio.|
|Basisbeleidsregels moeten zich in dezelfde regio als het lokale beleid bevinden|Maak al uw lokale beleidsregels in dezelfde regio als het basisbeleid. U kunt nog steeds een beleid toepassen dat in een regio is gemaakt op een beveiligde hub vanuit een andere regio.|Wordt onderzocht|
|Verkeer tussen hubs filteren bij implementaties in een beveiligde virtuele hub|Het filteren van communicatie tussen een beveiligde virtuele hub en een andere beveiligde virtuele hub wordt nog niet ondersteund. Hub-naar-hub-communicatie werkt echter nog steeds als filteren van privéverkeer via Azure Firewall niet is ingeschakeld.|Wordt onderzocht|
|Spaken in een andere regio dan de virtuele hub|Spaken in een andere regio dan de virtuele hub worden niet ondersteund.|Wordt onderzocht<br><br>Maak een hub per regio en maak peer-VNets in dezelfde regio als de hub.|
|Verkeer tussen vertakkingen met filteren van privéverkeer ingeschakeld|Verkeer tussen vertakkingen wordt niet ondersteund als het filteren van privéverkeer is ingeschakeld. |Wordt onderzocht.<br><br>Beveilig geen privéverkeer als de connectiviteit tussen vertakkingen essentieel is.|
|Alle beveiligde virtuele hubs die dezelfde virtuele WAN delen, moeten zich in dezelfde resourcegroep bevinden.|Dit gedrag wordt vandaag afgestemd met andere virtuele WAN-hubs.|Maak meerdere virtuele WAN's om ervoor te zorgen dat beveiligde virtuele hubs kunnen worden gemaakt in andere resourcegroepen.|
|Het toevoegen van een bulk-IP-adres mislukt|De firewall van de beveiligde hub krijgt de status Mislukt als u meerdere openbare IP-adressen toevoegt.|Voeg de openbare IP-adressen in kleinere stappen toe. Voeg er bijvoorbeeld tien per keer toe.|
|Toepassingsregels mislukken in een beveiligde hub waarin een aangepast DNS (preview) is geconfigureerd.|Aangepaste DNS (preview-versie) werkt niet in beveiligde hub-implementaties en implementaties van virtuele hubnetwerken waarvoor geforceerde tunneling is ingeschakeld.|Een oplossing wordt onderzocht.|
|DDoS Protection Standard wordt niet ondersteund met beveiligde virtuele hubs|DDoS Protection Standard is niet geïntegreerd met vWAN's.|Wordt onderzocht|
|Activiteitenlogboeken worden niet volledig ondersteund|Het firewallbeleid biedt momenteel geen ondersteuning voor activiteitenlogboeken.|Wordt onderzocht|
|Privé IP-adresbereiken van SNAT configureren|[Instellingen voor privé IP-adresbereiken](../firewall/snat-private-range.md) worden genegeerd als Azure Firewall-beleid is geconfigureerd. Het standaard Azure Firewall-gedrag wordt gebruikt. SNAT-netwerkregels worden toegepast wanneer het doel-IP-adres zich in een privé IP-adresbereik bevindt per [IANA RFC 1918](https://tools.ietf.org/html/rfc1918).|Wordt onderzocht

## <a name="next-steps"></a>Volgende stappen

- [Overzicht van de implementatie van Azure Firewall Manager](deployment-overview.md) controleren
- Meer informatie over [beveiligde virtuele hubs](secured-virtual-hub.md).
