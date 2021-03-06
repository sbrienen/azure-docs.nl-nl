---
title: Informatie over de factuur voor uw Microsoft-klantovereenkomst
description: Lees hier alles over de factuur voor uw Microsoft-klantovereenkomst in Azure
author: bandersmsft
ms.reviewer: amberb
tags: billing
ms.service: cost-management-billing
ms.subservice: billing
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: banders
ms.openlocfilehash: 766136731cb92b1bd4f0965d4929b1ac5eda14dc
ms.sourcegitcommit: 56cbd6d97cb52e61ceb6d3894abe1977713354d9
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/20/2020
ms.locfileid: "88690490"
---
# <a name="terms-in-your-microsoft-customer-agreement-invoice"></a>Terminologie in uw factuur voor een Microsoft-klantovereenkomst

Dit artikel is van toepassing op een Azure-factureringsaccount voor een Microsoft-klantovereenkomst. [Controleer of u toegang hebt tot een Microsoft-klantovereenkomst](#check-access-to-a-microsoft-customer-agreement).

Uw factuur bevat een overzicht van uw kosten en instructies voor betaling. De factuur kan als PDF worden gedownload uit de [Azure-portal](https://portal.azure.com/) of kan per e-mail worden verzonden. Zie [Uw Microsoft Azure-factuur weergeven en downloaden](download-azure-invoice.md) voor meer informatie.

## <a name="billing-period"></a>Factureringsperiode

U wordt maandelijks gefactureerd. U kunt zien op welke dag van de maand u facturen ontvangt door naar de *factuurdatum* te kijken in de eigenschappen van uw factureringsprofiel in de [Azure-portal](https://portal.azure.com/). Kosten die zijn gemaakt tussen het einde van de factureringsperiode en de factuurdatum worden opgenomen in de factuur van de volgende maand, aangezien deze zich in de volgende factureringsperiode bevinden. De begin-en einddatum van de factureringsperiode voor elke factuur worden vermeld in de PDF-factuur, boven **Factureringsoverzicht**.

## <a name="invoice-terms-and-descriptions"></a>Gebruikte terminologie in facturen

De volgende secties bevatten belangrijke termen die op uw factuur worden gebruikt, inclusief beschrijvingen van elke term.

### <a name="invoice-summary"></a>Factureringsoverzicht

Het **factureringsoverzicht** ziet u bovenaan de eerste pagina en bevat informatie over uw factureringsprofiel en hoe u betaalt.

![Sectie factuuroverzicht](./media/mca-understand-your-invoice/invoicesummary.png)

| Termijn | Beschrijving |
| --- | --- |
| Verkocht aan |Adres van uw juridische entiteit, zoals gevonden in de eigenschappen van het factureringsaccount|
| Factureren aan |Het factuuradres van het factureringsprofiel waarnaar de factuur wordt verzonden, te vinden in de eigenschappen van het factureringsprofiel|
| Factureringsprofiel |De naam van het factureringsprofiel voor de factuur |
| Inkoop- getal |Een optioneel inkoopordernummer dat door u is toegewezen voor traceringsdoeleinden |
| Factuurnummer |Een uniek, door Microsoft gegenereerd factuurnummer dat wordt gebruikt voor traceringsdoeleinden |
| Factuurdatum |Datum waarop de factuur is gegenereerd, meestal vijf tot 12 dagen na het einde van de factureringscyclus. U kunt de factuurdatum controleren in de eigenschappen van het factureringsprofiel.|
| Betalingsvoorwaarden |Hoe u betaalt voor uw Microsoft-factuur. *Netto 30 dagen* betekent dat u betaalt binnen 30 dagen na de factuurdatum. |

### <a name="billing-summary"></a>Factureringsoverzicht

In het **factureringsoverzicht** worden de kosten voor het factureringsprofiel weergegeven sinds de vorige factureringsperiode, eventuele tegoeden die zijn toegepast, belastingen en het totale verschuldigde bedrag.

![Gedeelte Factureringsoverzicht](./media/mca-understand-your-invoice/billingsummary.png)

| Termijn | Beschrijving |
| --- | --- |
| Kosten|Totaalbedrag van de Microsoft-kosten voor dit factureringsprofiel sinds de laatste factureringsperiode |
| Tegoeden |Tegoeden die u hebt ontvangen voor retouren |
| Azure-tegoed toegepast | Azure-tegoeden die elke factureringsperiode automatisch worden verrekend met Azure-kosten |
| Subtotaal |Het verschuldigde bedrag vóór btw |
| Btw |Het type en het bedrag aan belasting dat u betaalt, afhankelijk van het land of de regio van uw factureringsprofiel. Als u geen btw hoeft te betalen, ziet u deze vermelding niet op uw factuur. |
| Geschatte totale besparingen |Het geschatte totaalbedrag dat u hebt bespaard op basis van effectieve kortingen. Als dit van toepassing is, worden de effectieve kortingstarieven vermeld onder de regels met aankoopitems in het gedeelte met gedetailleerde gegevens van de factuur. |

### <a name="invoice-sections"></a>Factuursecties

Voor elke factuursectie onder uw factureringsprofiel ziet u de kosten, het bedrag van de toegepaste Azure-tegoeden, de belasting en het totale verschuldigde bedrag.

`Total = Charges - Azure Credit + Tax`

### <a name="details-by-invoice-section"></a>Gedeelte met factuurdetails

In de details worden de kosten voor elke factuursectie per productorder weergegeven. Binnen elke productorder worden de kosten uitgesplitst op basis van het type service. Dagelijkse kosten voor uw producten en services kunt u vinden in de Azure-portal en het CSV-bestand met gegevens van Azure-gebruik en -kosten. Zie [Inzicht in de kosten op de factuur van uw Microsoft-klantovereenkomst](review-customer-agreement-bill.md) voor meer informatie.

Het totale verschuldigde bedrag voor elke servicegroep wordt berekend door de waarde voor *Azure-tegoed* in mindering te brengen op de waarde voor *Tegoed/kosten* en de waarde voor *Btw-bedrag* erbij op te tellen:


![Gedeelte met factuurdetails](./media/mca-understand-your-invoice/invoicesectiondetails.png)

| Termijn |Beschrijving |
| --- | --- |
| Eenheidsprijs | De werkelijke eenheidsprijs van de service (in de prijsvaluta) die wordt gebruikt om het gebruik te classificeren. Deze prijs is uniek voor een product, servicegroep, meter en aanbieding. |
| Hoeveelheid | Hoeveelheid die is aangeschaft of verbruikt tijdens de factureringsperiode |
| Kosten/tegoeden | Het nettobedrag aan kosten na verrekening van tegoeden/restituties |
| Azure-tegoed | De hoeveelheid Azure-tegoeden die worden toegepast op de kosten/tegoeden|
| Btw-tarief | Een of meer btw-tarieven, afhankelijk van land/regio |
| Btw-bedrag | Bedrag aan btw dat in rekening is gebracht op basis van het geldende btw-tarief |
| Totaal | Het totale verschuldigde bedrag voor de aankoop |

### <a name="how-to-pay"></a>Hoe u kunt betalen

Onderaan de factuur staan instructies voor het betalen van uw factuur. U kunt betalen per cheque, overboeking of online. Als u online betaalt, kunt u een creditcard of Azure-tegoed gebruiken, indien van toepassing.

### <a name="publisher-information"></a>Informatie over uitgever

Als er services van derden op uw factuur worden vermeld, worden de naam en het adres van elke uitgever onderaan uw factuur weer gegeven.

## <a name="check-access-to-a-microsoft-customer-agreement"></a>Toegang tot een Microsoft-klantovereenkomst controleren
[!INCLUDE [billing-check-mca](../../../includes/billing-check-mca.md)]

## <a name="need-help-contact-us"></a>Hulp nodig? Neem contact met ons op.

Als u vragen hebt of hulp nodig hebt, [kunt u een ondersteuningsaanvraag maken](https://go.microsoft.com/fwlink/?linkid=2083458).

## <a name="next-steps"></a>Volgende stappen

- [Inzicht in de kosten op de factuur van uw Microsoft-klantovereenkomst](review-customer-agreement-bill.md)
- [Uw Azure-factuur en de dagelijkse gebruiksgegevens ophalen](../manage/download-azure-invoice-daily-usage-date.md)
- [Azure-prijzen voor uw organisatie bekijken en downloaden](../manage/ea-pricing.md)
- [Belastingdocumenten voor uw Microsoft-klantovereenkomst weergeven](mca-download-tax-document.md)
