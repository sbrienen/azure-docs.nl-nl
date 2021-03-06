---
title: Gegevens in realtime openbaar door Voer aanvragen | Microsoft Azure kaarten
description: Meer informatie over het aanvragen van real-time gegevens voor openbaar door Voer, zoals aankomsten bij een doorvoer stop. Zie de Azure Maps Mobility-service gebruiken voor dit doel einde.
author: anastasia-ms
ms.author: v-stharr
ms.date: 09/06/2019
ms.topic: how-to
ms.service: azure-maps
services: azure-maps
manager: philmea
ms.custom: mvc
ms.openlocfilehash: e6f6d0738cb1673b752e35761a112f2ca22a409e
ms.sourcegitcommit: 4064234b1b4be79c411ef677569f29ae73e78731
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92895712"
---
# <a name="request-real-time-public-transit-data-using-the-azure-maps-mobility-service"></a>Real-time gegevens van open bare door Voer aanvragen met behulp van de Azure Maps Mobility-service

In dit artikel wordt beschreven hoe u Azure Maps [Mobility-service](/rest/api/maps/mobility) kunt gebruiken om gegevens in realtime open bare door voer te aanvragen.

In dit artikel leert u hoe u de volgende realtime aankomsten kunt aanvragen voor alle regels die bij een bepaalde Stop arriveren

## <a name="prerequisites"></a>Vereisten

U moet eerst een Azure Maps account en een abonnements sleutel hebben om de Azure Maps open bare doorvoer-Api's te kunnen aanroepen. Volg de instructies in [een account maken](quick-demo-map-app.md#create-an-azure-maps-account) om een Azure Maps-account te maken voor meer informatie. Volg de stappen in [primaire sleutel ophalen](quick-demo-map-app.md#get-the-primary-key-for-your-account) om de primaire sleutel voor uw account te verkrijgen. Zie [Verificatie beheren in Azure Maps](./how-to-manage-authentication.md) voor meer informatie over verificatie in Azure Maps.

In dit artikel wordt gebruikgemaakt van de [app postman](https://www.getpostman.com/apps) om rest-aanroepen te bouwen. U kunt elke gewenste API-ontwikkel omgeving gebruiken.

## <a name="request-real-time-arrivals-for-a-stop"></a>Dagelijkse aankomsten aanvragen voor een stop

Als u gegevens in realtime wilt ontvangen van een bepaalde open bare doorvoer stop, moet u een aanvraag indienen bij de API voor de [real-time-ontvangst](/rest/api/maps/mobility/getrealtimearrivalspreview) van de Azure Maps [Mobility-service](/rest/api/maps/mobility). U hebt de **metroID** en **stopID** nodig om de aanvraag te volt ooien. Zie voor meer informatie over het aanvragen van deze para meters onze hand leiding voor het [aanvragen van open bare Transit routes](./how-to-request-transit-data.md).

We gebruiken ' 522 ' als onze metro-ID. Dit is de metro-ID voor het gebied ' Seattle – Tacoma – Bellevue, WA '. Gebruik "522---2060603" als de stop-ID, deze bus stopt op "ne 24 st & 162nd Ave ne, Bellevue WA". Voer de volgende stappen uit om de volgende vijf gegevens over de dagelijkse duur te aanvragen voor alle volgende Live-aankomsten:

1. Open de Postman-app, zodat u een verzameling kunt maken om de aanvragen op te slaan. Selecteer **New** (Nieuw) bovenaan de Postman-app. Selecteer **Collection** (Verzameling) in het venster **Create New** (Nieuwe maken).  Geef de verzameling een naam en selecteer de knop **Create** (Maken).

2. Selecteer nogmaals **New** (Nieuw) om de aanvraag te maken. Selecteer **Request** (Aanvraag) in het venster **Create New** (Nieuwe maken). Voer een **Request name** (Aanvraagnaam) in voor de aanvraag. Selecteer de verzameling die u in de vorige stap hebt gemaakt, als de locatie waar u de aanvraag wilt opslaan. Selecteer vervolgens **Opslaan** .

    ![Een aanvraag maken in postman](./media/how-to-request-transit-data/postman-new.png)

3. Selecteer de methode http **ophalen** op het tabblad opbouw functie en voer de volgende URL in om een GET-aanvraag te maken. Vervang door `{subscription-key}` de primaire sleutel van Azure Maps.

    ```HTTP
    https://atlas.microsoft.com/mobility/realtime/arrivals/json?subscription-key={subscription-key}&api-version=1.0&metroId=522&query=522---2060603&transitType=bus
    ```

4. Na een geslaagde aanvraag ontvangt u het volgende antwoord.  U ziet dat de para meter ' Schedule Type ' definieert of de geschatte aankomst tijd is gebaseerd op realtime of statische gegevens.

    ```JSON
    {
        "results": [
            {
                "arrivalMinutes": 8,
                "scheduleType": "realTime",
                "patternId": "522---4143196",
                "line": {
                    "lineId": "522---3760143",
                    "lineGroupId": "522---666077",
                    "direction": "backward",
                    "agencyId": "522---5872",
                    "agencyName": "Metro Transit",
                    "lineNumber": "249",
                    "lineDestination": "South Bellevue S Kirkland P&R",
                    "transitType": "Bus"
                },
                "stop": {
                    "stopId": "522---2060603",
                    "stopKey": "71300",
                    "stopName": "NE 24th St & 162nd Ave NE",
                    "stopCode": "71300",
                    "position": {
                        "latitude": 47.631504,
                        "longitude": -122.125275
                    },
                    "mainTransitType": "Bus",
                    "mainAgencyId": "522---5872",
                    "mainAgencyName": "Metro Transit"
                }
            },
            {
                "arrivalMinutes": 25,
                "scheduleType": "realTime",
                "patternId": "522---3510227",
                "line": {
                    "lineId": "522---2756599",
                    "lineGroupId": "522---666063",
                    "direction": "forward",
                    "agencyId": "522---5872",
                    "agencyName": "Metro Transit",
                    "lineNumber": "226",
                    "lineDestination": "Bellevue Transit Center Crossroads",
                    "transitType": "Bus"
                },
                "stop": {
                    "stopId": "522---2060603",
                    "stopKey": "71300",
                    "stopName": "NE 24th St & 162nd Ave NE",
                    "stopCode": "71300",
                    "position": {
                        "latitude": 47.631504,
                        "longitude": -122.125275
                    },
                    "mainTransitType": "Bus",
                    "mainAgencyId": "522---5872",
                    "mainAgencyName": "Metro Transit"
                }
            }
        ]
    }
    ```

## <a name="next-steps"></a>Volgende stappen

Meer informatie over het aanvragen van doorvoer gegevens met de Mobility-service:

> [!div class="nextstepaction"]
> [Transit gegevens aanvragen](how-to-request-transit-data.md)

Bekijk de documentatie voor de Azure Maps Mobility Service API:

> [!div class="nextstepaction"]
> [API-documentatie voor Mobility service](/rest/api/maps/mobility)