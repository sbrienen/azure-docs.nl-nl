---
title: Azure Communication Services - Voorbeeld van webaanroeping
titleSuffix: An Azure Communication Services sample
description: Meer informatie over het voorbeeld van webaanroeping voor Communication Services
author: chriswhilar
manager: mariusu-msft
services: azure-communication-services
ms.author: mariusu
ms.date: 10/15/2020
ms.topic: overview
ms.service: azure-communication-services
ms.openlocfilehash: 8faa6533ba4dc7fad61c045278c5504c5f78d900
ms.sourcegitcommit: 230d5656b525a2c6a6717525b68a10135c568d67
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94888960"
---
# <a name="get-started-with-the-web-calling-sample"></a>Aan de slag met het voorbeeld van aanroeping

[!INCLUDE [Public Preview Notice](../includes/public-preview-include.md)]

> [!IMPORTANT]
> [Dit voorbeeld is beschikbaar op GitHub.](https://github.com/Azure-Samples/communication-services-web-calling-tutorial/).

Het **voorbeeld van webaanroeping** laat zien hoe de clientbibliotheek van Communication Services kan worden gebruikt voor het bouwen van een gesprekservaring met JavaScript.

In deze quickstart over hero-voorbeelden komt u te weten hoe het voorbeeld werkt voordat u het op uw lokale computer gaat uitvoeren. Vervolgens gaat u het voorbeeld in Azure implementeren met behulp van uw eigen Azure Communication Services-resources.

## <a name="overview"></a>Overzicht

Het voorbeeld van webaanroeping is een webtoepassing die als stapsgewijze instructie dient voor de verschillende mogelijkheden van de Communication Services-clientbibliotheek voor webaanroeping. 

Dit voorbeeld is gebouwd voor ontwikkelaars en maakt het eenvoudig om aan de slag te gaan met Communication Services. De gebruikersinterface is onderverdeeld in meerdere secties, elk met de knop 'Code weergeven' waarmee u rechtstreeks vanuit uw browser codes kunt kopiëren naar uw eigen Communication Services-toepassing.

Wanneer de [voorbeeld van webaanroep](https://github.com/Azure-Samples/communication-services-web-calling-tutorial) op uw computer wordt uitgevoerd, ziet u de volgende landingspagina:

:::image type="content" source="./media/web-calling-tutorial-page-1.png" alt-text="Zelfstudie voor webaanroeping 1" lightbox="./media/web-calling-tutorial-page-1.png":::

:::image type="content" source="./media/web-calling-tutorial-page-2.png" alt-text="Zelfstudie voor webaanroeping 2" lightbox="./media/web-calling-tutorial-page-2.png":::


## <a name="user-provisioning-and-sdk-initialization"></a>Gebruikersinrichting en SDK-initialisatie 

Als u de demo wilt gaan gebruiken, voert u de verbindingsreeks van uw [Communication Services-resource](../quickstarts/create-communication-resource.md) in `config.json`. Dit wordt gebruikt om een [token voor gebruikerstoegang in te richten](../concepts/authentication.md) zodat de aanroepende SDK kan worden geïnitialiseerd.

Geef uw eigen persoonlijke id op bij het invoeren van de gebruikers-id. Als hier niets wordt geboden, wordt er een willekeurige gebruikers-id gegenereerd. 

Klik op ‘Gebruiker inrichten en SDK initialiseren’ om uw SDK te initialiseren met behulp van een token dat is ingericht door de service voor het inrichten van de back-end-token. Deze back-end-service is te vinden in `/project/webpack.config.js`.

Klik op de knop ‘Code weergeven’ om de voorbeeldcode te bekijken die u kunt gebruiken in uw eigen oplossing.

Nadat de SDK is geïnitialiseerd, ziet u het volgende:

:::image type="content" source="./media/user-provisioning.png" alt-text="Inrichten van gebruikers" lightbox="./media/user-provisioning.png":::

U bent nu klaar om te beginnen met het plaatsen van oproepen met uw Communication Services-resource!

## <a name="placing-and-receiving-calls"></a>Oproepen plaatsen en ontvangen

De weboproep-SDK van Communication Services maakt de volgende oproepen **1:1**, **1: N** en **groep**.

Voor 1:1 of 1: N uitgaande oproepen kunt u meerdere gebruikersidentiteiten voor Communication Services opgeven om aan te roepen met door komma's gescheiden waarden. U kunt ook traditionele (PSTN) telefoonnummers opgeven om aan te roepen met door komma's gescheiden waarden. 

Wanneer u PSTN-telefoonnummers belt, geeft u uw alternatieve beller-ID op. Klik op de knop ‘Oproep doen’ om een uitgaande oproep te plaatsen:

:::image type="content" source="./media/place-a-call.png" alt-text="Een oproep doen" lightbox="./media/place-a-call.png":::

Als u deel wilt nemen aan een groepsgesprek, voert u de GUID in die de oproep identificeert en klikt u op de knop ‘Deelnemen aan groep’:

:::image type="content" source="./media/join-a-group-call.png" alt-text="Deelnemen aan een groepsgesprek" lightbox="./media/join-a-group-call.png":::

Klik op de knop ‘Code weergeven’ om de voorbeeldcode voor het plaatsen van oproepen te bekijken, oproepen te ontvangen en groepsgesprekken samen te voegen.

Een actiefgesprek ziet er als volgt uit:

:::image type="content" source="./media/group-call.png" alt-text="Groepsgesprek" lightbox="./media/group-call.png":::

Dit voorbeeld bevat ook codefragmenten voor de volgende mogelijkheden:

  - Klik op het pictogram video om uw videocamera in- of uit te schakelen
  - Klikken op het pictogram microfoon om uw microfoon in- of uit te schakelen
  - Klik op het pictogram afspelen om de oproep in de wacht te zetten/te beantwoorden
  - Klik op het pictogram scherm om uw scherm te starten/stoppen
  - Klik op het pictogram persoon om een deelnemer aan het gesprek toe te voegen
  - Klik op ‘Deelnemer verwijderen’ in de deelnemerslijst om een specifieke deelnemer uit het gesprek te verwijderen


## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"] 
>[Het voorbeeld downloaden uit GitHub](https://github.com/Azure-Samples/communication-services-web-calling-tutorial/)

Raadpleeg voor meer informatie de volgende artikelen:

- Vertrouwd raken met [het gebruik van de clientbibliotheek voor aanroepen](../quickstarts/voice-video-calling/calling-client-samples.md)
- Meer informatie over [de werking van aanroepen](../concepts/voice-video-calling/about-call-types.md)
- Controleer de [API-referentiedocumenten](/javascript/api/azure-communication-services/@azure/communication-calling/?view=azure-communication-services-js)

## <a name="additional-reading"></a>Meer artikelen

- [Azure Communication GitHub](https://github.com/Azure/communication): u vindt meer voorbeelden en informatie op de officiële GitHub-pagina
- [Redux](https://redux.js.org/): statusbeheer op de client
- [FluentUI](https://aka.ms/fluent-ui): door Microsoft ondersteunde bibliotheek voor de gebruikersinterface
- [React](https://reactjs.org/): bibliotheek voor het ontwikkelen van gebruikersinterfaces
- [ASP.NET Core](/aspnet/core/introduction-to-aspnet-core?preserve-view=true&view=aspnetcore-3.1): een framework voor het bouwen van webtoepassingen