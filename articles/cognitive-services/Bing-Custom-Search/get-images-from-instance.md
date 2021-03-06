---
title: Afbeeldingen ophalen uit uw aangepaste weer gave-Bing Aangepaste zoekopdrachten
titleSuffix: Azure Cognitive Services
description: Overzicht op hoog niveau over het gebruik van Bing Aangepaste zoekopdrachten om installatie kopieën op te halen uit uw aangepaste weer gave van het web.
services: cognitive-services
author: swhite-msft
manager: nitinme
ms.service: cognitive-services
ms.subservice: bing-custom-search
ms.topic: conceptual
ms.date: 09/10/2018
ms.author: scottwhi
ms.openlocfilehash: c29e83f7851bc9be1688f3828373942c0e31f4ef
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/08/2020
ms.locfileid: "94367462"
---
# <a name="get-images-from-your-custom-view"></a>Afbeeldingen ophalen uit uw aangepaste weer gave

> [!WARNING]
> Bing Zoeken-API's van Cognitive Services naar Bing Search-Services verplaatsen. Vanaf **30 oktober 2020** moeten nieuwe exemplaren van Bing Search worden ingericht volgens het proces dat [hier](https://aka.ms/cogsvcs/bingmove)wordt beschreven.
> Bing Zoeken-API's ingericht met Cognitive Services wordt voor de komende drie jaar of tot het einde van uw Enterprise Agreement ondersteund, afhankelijk van wat het eerst gebeurt.
> Zie [Bing Search Services](https://aka.ms/cogsvcs/bingmigration)voor migratie-instructies.

Met Bing aangepaste afbeeldingen zoeken kunt u uw aangepaste zoek ervaring verrijken met afbeeldingen. Bij aangepast zoeken, kunt u (net als bij webresultaten) zoeken naar afbeeldingen in de lijst websites van uw exemplaar. U kunt de installatie kopieën ophalen met behulp van de zoek-API voor de aangepaste installatie kopieën van Bing of via de gehoste UI-functie. Het gebruik van de gehoste UI-functie is eenvoudig te gebruiken en wordt aanbevolen om uw zoek opdracht in een korte volg orde uit te voeren.  Zie [uw gehoste UI-ervaring configureren](hosted-ui.md)voor meer informatie over het configureren van uw gehoste gebruikers interface voor het toevoegen van installatie kopieën.

Als u meer controle wilt over het weer geven van de zoek resultaten, kunt u de zoek-API van Bing aangepaste installatie kopieën gebruiken. Omdat het aanroepen van de API lijkt op het aanroepen van de Bing Afbeeldingen zoeken-API, wordt met de kassa [Bing Image Search](../Bing-Image-Search/overview.md) voor beelden van het aanroepen van de API. Maar voordat u dit doet, moet u vertrouwd raken met de naslag informatie voor het [zoeken naar aangepaste afbeeldingen](/rest/api/cognitiveservices-bingsearch/bing-custom-images-api-v7-reference) in de API. De belangrijkste verschillen zijn de ondersteunde query parameters (u moet de query parameter customConfig toevoegen) en het eind punt waarnaar u aanvragen verzendt.

<!--
## Next steps

[Call your custom view](search-your-custom-view.md)
-->