---
title: Alias server namen Azure Analysis Services | Microsoft Docs
description: Meer informatie over het maken van aliassen voor Azure Analysis Services server naam. Gebruikers kunnen vervolgens verbinding maken met uw server met een kortere alias naam in plaats van de server naam.
author: minewiskan
ms.service: azure-analysis-services
ms.topic: conceptual
ms.date: 06/16/2020
ms.author: owend
ms.reviewer: minewiskan
ms.openlocfilehash: 753ac449418b78fe02640f1b70b94b5b3d7f2be5
ms.sourcegitcommit: 2c586a0fbec6968205f3dc2af20e89e01f1b74b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "92019032"
---
# <a name="alias-server-names"></a>Alias server namen

Met behulp van een server naam alias kunnen gebruikers verbinding maken met uw Azure Analysis Services server met een kortere *alias* in plaats van de server naam. Wanneer u verbinding maakt vanuit een client toepassing, wordt de alias opgegeven als een eind punt met de **link://** -protocol indeling. Het eind punt retourneert vervolgens de naam van de echte server om verbinding te kunnen maken.

Alias server namen zijn geschikt voor:

- Modellen migreren tussen servers zonder dat dit van invloed is op gebruikers. 
- Beschrijvende server namen zijn eenvoudiger voor gebruikers te onthouden. 
- Stuur gebruikers naar verschillende servers op verschillende tijdstippen van de dag. 
- Gebruikers in verschillende regio's direct naar instanties die geografisch dichter zijn, zoals bij het gebruik van Azure Traffic Manager. 

Elk HTTPS-eind punt dat een geldige Azure Analysis Services server naam retourneert, kan als alias fungeren. Het eind punt moet HTTPS ondersteunen via poort 443 en de poort mag niet worden opgegeven in de URI.

![Alias met koppelings indeling](media/analysis-services-alias/aas-alias-browser.png)

Wanneer u verbinding maakt vanaf een client, wordt de naam van de alias server ingevoerd met de **link://** -protocol indeling. Bijvoorbeeld in Power BI Desktop:

![Power BI Desktop verbinding](media/analysis-services-alias/aas-alias-connect-pbid.png)

## <a name="create-an-alias"></a>Een alias maken

Als u een alias eindpunt wilt maken, kunt u elke methode gebruiken die een geldige Azure Analysis Services server naam retourneert. Bijvoorbeeld een verwijzing naar een bestand in Azure Blob Storage met de echte naam van de server of het maken en publiceren van een ASP.NET Web Forms-toepassing.

In dit voor beeld wordt een ASP.NET Web Forms-toepassing gemaakt in Visual Studio. De pagina verwijzing en het gebruikers besturings element worden verwijderd van de pagina default. aspx. De inhoud van default. aspx is gewoon de volgende pagina-instructie:

```
<%@ Page Title="Home Page" Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="FriendlyRedirect._Default" %>
```

De Page_Load gebeurtenis in Default.aspx.cs gebruikt de methode Response. write () om de naam van de Azure Analysis Services-server te retour neren.

```
protected void Page_Load(object sender, EventArgs e)
{
    this.Response.Write("asazure://<region>.asazure.windows.net/<servername>");
}
```

## <a name="see-also"></a>Zie ook

[Client bibliotheken](/analysis-services/client-libraries?view=azure-analysis-services-current)   
[Verbinding maken vanuit Power BI Desktop](analysis-services-connect-pbi.md)