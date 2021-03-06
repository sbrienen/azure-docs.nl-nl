---
title: Fout door taak grootte overschreden
description: Hierin wordt beschreven hoe u fouten oplost wanneer de taak grootte of sjabloon te groot is.
ms.topic: troubleshooting
ms.date: 10/07/2020
ms.openlocfilehash: 638bdef246fc908ab997bfb99e7526febdb3792e
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91822153"
---
# <a name="resolve-errors-for-job-size-exceeded"></a>Fouten oplossen voor de taak grootte is overschreden

In dit artikel wordt beschreven hoe u de **JobSizeExceededException** -en **DeploymentSizeExceededException** -fouten kunt oplossen.

## <a name="symptom"></a>Symptoom

Wanneer u een sjabloon implementeert, wordt er een fout melding weer gegeven dat de implementatie limieten heeft overschreden.

## <a name="cause"></a>Oorzaak

U kunt deze fout ophalen wanneer de grootte van uw sjabloon groter is dan 4 MB. De limiet van 4 MB is van toepassing op de uiteindelijke status van de sjabloon nadat deze is uitgebreid voor resource definities die gebruikmaken van [kopiëren](copy-resources.md) om veel instanties te maken. De uiteindelijke status bevat ook de opgeloste waarden voor variabelen en para meters.

De implementatie taak bevat ook meta gegevens over de aanvraag. Voor grote sjablonen kan de meta gegevens die in combi natie met de sjabloon worden gecombineerd de toegestane grootte voor een taak overschrijden.

Andere limieten voor de sjabloon zijn:

* 256-para meters
* 256 variabelen
* 800 bronnen (met inbegrip van het aantal kopieën)
* 64 uitvoer waarden
* 24.576 tekens in een sjabloon expressie

## <a name="solution-1---simplify-template"></a>Oplossing 1: sjabloon vereenvoudigen

Uw eerste optie is om de sjabloon te vereenvoudigen. Deze optie werkt als uw sjabloon veel verschillende resource typen implementeert. Overweeg om de sjabloon te verdelen in [gekoppelde sjablonen](linked-templates.md). Verdeel uw resource typen in logische groepen en voeg een gekoppelde sjabloon toe voor elke groep. Als u bijvoorbeeld veel netwerk bronnen wilt implementeren, kunt u deze resources naar een gekoppelde sjabloon verplaatsen.

U kunt andere resources instellen als afhankelijk van de gekoppelde sjabloon en [waarden ophalen uit de uitvoer van de gekoppelde sjabloon](linked-templates.md#get-values-from-linked-template).

## <a name="solution-2---reduce-name-size"></a>Oplossing 2: de naam grootte verlagen

Probeer de lengte van de namen die u gebruikt voor [para meters](template-parameters.md), [variabelen](template-variables.md)en [uitvoer](template-outputs.md)in te korten. Wanneer deze waarden worden herhaald via Kopieer lussen, wordt een grote naam meermaals vermenigvuldigd.

## <a name="solution-3---use-serial-copy"></a>Oplossing 3: een seriële kopie gebruiken

De tweede optie is om uw kopie-lus te wijzigen van [parallel naar seriële verwerking](copy-resources.md#serial-or-parallel). Gebruik deze optie alleen als u vermoedt dat de fout afkomstig is van het implementeren van een groot aantal resources via een kopie. Met deze wijziging kan uw implementatie tijd aanzienlijk toenemen omdat de resources niet parallel worden geïmplementeerd.
