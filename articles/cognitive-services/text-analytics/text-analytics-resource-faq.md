---
title: Veelgestelde vragen over de Text Analytics-API
titleSuffix: Azure Cognitive Services
description: Hier vindt u antwoorden op veelgestelde vragen over concepten, code en scenario's met betrekking tot de Text Analytics-API voor Azure Cognitive Services.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: text-analytics
ms.topic: conceptual
ms.date: 02/13/2019
ms.author: aahi
ms.openlocfilehash: ffa70afa0edf29181bc622cbef6ff8716134b1f7
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/08/2020
ms.locfileid: "94364935"
---
# <a name="frequently-asked-questions-faq-about-the-text-analytics-cognitive-service"></a>Veelgestelde vragen over de Text Analytics cognitieve service

 Hier vindt u antwoorden op veelgestelde vragen over concepten, code en scenario's met betrekking tot de Text Analytics-API voor Microsoft Cognitive Services op Azure.

## <a name="can-text-analytics-identify-sarcasm"></a>Kan sarcasme Text Analytics identificeren?

Analyse is voor positieve negatieve sentiment in plaats van stemmings detectie.

Er is altijd een zekere mate van onnauwkeurigheid in sentiment-analyse, maar het model is het handigst wanneer er geen verborgen betekenis of subtekst van de inhoud is. Ijzer, sarcasme, humor en soort gelijke inhoud zijn afhankelijk van culturele context en normen voor het overbrengen van de intentie. Dit type inhoud is een van de grootste uitdaging voor het analyseren. Normaal gesp roken is het grootste verschil tussen een gegeven Score die door het analyseprogramma wordt geproduceerd en een subjectieve beoordeling door een mens, voor inhoud met een genuancete betekenis.

## <a name="can-i-add-my-own-training-data-or-models"></a>Kan ik mijn eigen trainings gegevens of modellen toevoegen?

Nee, de modellen zijn voortraind. De enige bewerkingen die beschikbaar zijn voor geüploade gegevens zijn score, extractie van sleutel woorden en taal detectie. We hosten geen aangepaste modellen. Als u aangepaste machine learning modellen wilt maken en hosten, moet u rekening houden [met de machine learning mogelijkheden van Microsoft R server](/r-server/r/concept-what-is-the-microsoftml-package).

## <a name="can-i-request-additional-languages"></a>Kan ik extra talen aanvragen?

Er zijn sentiment-analyse en sleutel woordgroepen extractie beschikbaar voor een [geselecteerd aantal talen](./language-support.md). De verwerking van natuurlijke taal is complex en vereist aanzienlijke tests voordat nieuwe functionaliteit kan worden vrijgegeven. Daarom voor komt u dat er vooraf aangekondigde ondersteuning wordt geboden, zodat niemand meer tijd nodig heeft om te vervallen. 

Stem aan de hand van specifieke talen op de [gebruikers stem](https://cognitive.uservoice.com/forums/555922-text-analytics)om te bepalen welke talen u nu moet gebruiken. 

## <a name="why-does-key-phrase-extraction-return-some-words-but-not-others"></a>Waarom retourneert sleutel woordgroepen extra woorden, maar niet andere?

Met het uitpakken van sleutel woorden worden niet-essentiële woorden en zelfstandige bijvoeglijke code fragmenten geëlimineerd. Combi Naties van zelfstandig naam woorden, zoals ' spectaculaire weer gaven ' of ' Foggy weer ', worden samen geretourneerd.

Normaal gesp roken bestaat de uitvoer uit zelfstandige naam woorden en objecten van de zin. De uitvoer wordt weer gegeven in volg orde van prioriteit, waarbij de eerste zin het belangrijkst is. Het belang wordt gemeten op basis van het aantal keren dat een bepaald concept wordt vermeld, of de relatie van dat element met andere elementen in de tekst.

## <a name="why-does-output-vary-given-identical-inputs"></a>Waarom verschilt de uitvoer, op basis van identieke invoer?

Er worden verbeteringen aangebracht in modellen en algoritmen als de wijziging primair is of als de update stil is geslipstreamt in de-service als het een kleine is. Na verloop van tijd kan het voor komen dat dezelfde tekst invoer resulteert in een andere sentiment-Score of uitvoer van een sleutel woord groep. Dit is een normaal en opzettelijk gevolg van het gebruik van beheerde machine learning-resources in de Cloud.

## <a name="next-steps"></a>Volgende stappen

Is uw vraag over een ontbrekend onderdeel of functionaliteit? Overweeg om IT te vragen of te stemmen op onze [UserVoice-website](https://cognitive.uservoice.com/forums/555922-text-analytics).

## <a name="see-also"></a>Zie ook

 [Stack overflow: Text Analytics-API](https://stackoverflow.com/questions/tagged/text-analytics-api)   
 [Stack overflow: Cognitive Services](https://stackoverflow.com/questions/tagged/microsoft-cognitive)