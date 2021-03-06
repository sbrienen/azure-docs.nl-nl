---
title: Snelstart voor Anomaly Detector-clientbibliotheek voor JavaScript
titleSuffix: Azure Cognitive Services
services: cognitive-services
author: mrbullwinkle
manager: nitinme
ms.service: cognitive-services
ms.topic: include
ms.date: 09/22/2020
ms.author: mbullwin
ms.custom: devx-track-js
ms.openlocfilehash: b970b099d87148d169b2be3b7e72d32c159f5046
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/08/2020
ms.locfileid: "94371654"
---
Aan de slag met de Anomaly Detector-clientbibliotheek voor JavaScript. Voer de volgende stappen uit om het pakket te installeren en de algoritmen te gaan gebruiken die door de service worden geleverd. Met de Anomaly Detector-service kunt u afwijkingen in uw tijdreeksgegevens vinden door automatisch de best passende modellen erop uit te voeren, onafhankelijk van bedrijfstak, scenario of gegevensvolume.

Gebruik de Anomaly Detector-clientbibliotheek voor JavaScript om:

* Anomalieën in uw tijdreeksgegevensset als een batchaanvraag te detecteren
* De anomaliestatus van het laatste gegevenspunt in uw tijdreeks te detecteren
* Trendwijzigingspunten in uw gegevensset te detecteren.

[Referentiedocumentaie voor bibliotheek](https://go.microsoft.com/fwlink/?linkid=2090788) | [Bibliotheekbroncode](https://github.com/Azure/azure-sdk-for-net/tree/master/sdk/cognitiveservices/AnomalyDetector) | [Pakket (npm)](https://www.npmjs.com/package/%40azure/ai-anomaly-detector) | [De code zoeken op GitHub](https://github.com/Azure-Samples/cognitive-services-quickstart-code/tree/master/javascript/AnomalyDetector)

## <a name="prerequisites"></a>Vereisten

* Azure-abonnement: [Krijg een gratis abonnement](https://azure.microsoft.com/free/cognitive-services)
* De huidige versie van [Node.js](https://nodejs.org/)
* Zodra u een Azure-abonnement hebt, <a href="https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesAnomalyDetector"  title="maakt u een Anomaly Detector-resource "  target="_blank">Een Anomaly Detector-resource maken<span class="docon docon-navigate-external x-hidden-focus"></span></a> in de Azure-portal om uw sleutel en eindpunt op te halen. Wacht tot deze is geïmplementeerd en klik op de knop **Naar de resource gaan**.
    * U hebt de sleutel en het eindpunt nodig van de resource die u maakt om de toepassing te verbinden met de Anomaly Detector-API. Later in de quickstart plakt u uw sleutel en eindpunt in de onderstaande code.
    U kunt de gratis prijscategorie (`F0`) gebruiken om de service uit te proberen, en later upgraden naar een betaalde laag voor productie.

## <a name="setting-up"></a>Instellen

[!INCLUDE [anomaly-detector-environment-variables](../environment-variables.md)]

### <a name="create-a-new-nodejs-application"></a>Een nieuwe Node.js-toepassing maken

Maak in een consolevenster (zoals cmd, PowerShell of Bash) een nieuwe map voor de app, en navigeer naar deze map. 

```console
mkdir myapp && cd myapp
```

Voer de opdracht `npm init` uit om een knooppunttoepassing te maken met een `package.json`-bestand. 

```console
npm init
```

Maak een bestand met de naam `index.js` en importeer de volgende bibliotheken:

[!code-javascript[Import statements](~/cognitive-services-quickstart-code/javascript/AnomalyDetector/anomaly_detector_quickstart.js?name=imports)]

Maak variabelen voor het Azure-eindpunt en de Azure-sleutel voor uw resource. Als u de omgevingsvariabele hebt gemaakt nadat u de toepassing hebt gestart, moet u de editor, IDE of shell waarmee deze wordt uitgevoerd, sluiten en opnieuw openen om toegang te krijgen tot de variabele. Maak een andere variabele voor het voorbeeldgegevensbestand dat u in een latere stap gaat downloaden, en maak een lege lijst voor de gegevenspunten. Maak vervolgens een `ApiKeyCredentials`-object om de sleutel in op te slaan.

[!code-javascript[Initial endpoint and key variables](~/cognitive-services-quickstart-code/javascript/AnomalyDetector/anomaly_detector_quickstart.js?name=vars)]

### <a name="install-the-client-library"></a>De clientbibliotheek installeren

Installeer de NPM-pakketten `ms-rest-azure` en `azure-cognitiveservices-anomalydetector`. De CSV-parseerbibliotheek wordt ook gebruikt in deze snelstart:

```console
npm install @azure/ai-anomaly-detector @azure/ms-rest-js csv-parse
```

Het `package.json`-bestand van uw app wordt bijgewerkt met de afhankelijkheden.

## <a name="object-model"></a>Objectmodel

De Anomaly Detector-client is een [AnomalyDetectorClient](/javascript/api/@azure/cognitiveservices-anomalydetector/anomalydetectorclient?view=azure-node-latest)-object dat met behulp van uw sleutel wordt geverifieerd bij Azure. De client kan anomaliedetectie uitvoeren op een hele gegevensset met behulp van [entireDetect()](/javascript/api/@azure/cognitiveservices-anomalydetector/anomalydetectorclient?view=azure-node-latest#entiredetect-request--servicecallback-entiredetectresponse--), of op het laatste gegevenspunt met behulp van [LastDetect()](/javascript/api/@azure/cognitiveservices-anomalydetector/anomalydetectorclient?view=azure-node-latest#lastdetect-request--msrest-requestoptionsbase-). De methode [ChangePointDetectAsync](https://go.microsoft.com/fwlink/?linkid=2090788) detecteert punten die wijzigingen in een trend markeren. 

Tijdreeksgegevens worden verzonden als een reeks [punten](/javascript/api/@azure/cognitiveservices-anomalydetector/point?view=azure-node-latest) in een [aanvraagobject](/javascript/api/@azure/cognitiveservices-anomalydetector/request?view=azure-node-latest). Het `Request`-object bevat eigenschappen die de gegevens (bijvoorbeeld [granulariteit](/javascript/api/@azure/cognitiveservices-anomalydetector/request?view=azure-node-latest#granularity)) en parameters voor de anomaliedetectie beschrijven. 

Het antwoord van Anomaly Detector is een [LastDetectResponse](/javascript/api/@azure/cognitiveservices-anomalydetector/lastdetectresponse?view=azure-node-latest)-, [EntireDetectResponse](/javascript/api/@azure/cognitiveservices-anomalydetector/entiredetectresponse?view=azure-node-latest)- of [ChangePointDetectResponse](https://go.microsoft.com/fwlink/?linkid=2090788)-object afhankelijk van de gebruikte methode. 

## <a name="code-examples"></a>Codevoorbeelden 

Deze codefragmenten laten zien hoe u de volgende taken kunt uitvoeren met de Anomaly Detector-clientbibliotheek voor Node.js:

* [De client verifiëren](#authenticate-the-client)
* [Een tijdreeksgegevensset laden vanuit een bestand](#load-time-series-data-from-a-file)
* [Anomalieën in de volledige gegevensset detecteren](#detect-anomalies-in-the-entire-data-set) 
* [De anomaliestatus van het laatste gegevenspunt detecteren](#detect-the-anomaly-status-of-the-latest-data-point)
* [De wijzigingspunten in de gegevensset detecteren](#detect-change-points-in-the-data-set)

## <a name="authenticate-the-client"></a>De client verifiëren

Instantieer een [AnomalyDetectorClient](/javascript/api/@azure/cognitiveservices-anomalydetector/anomalydetectorclient?view=azure-node-latest)-object met uw eindpunt en referenties.

[!code-javascript[Authentication](~/cognitive-services-quickstart-code/javascript/AnomalyDetector/anomaly_detector_quickstart.js?name=authentication)]

## <a name="load-time-series-data-from-a-file"></a>Tijdreeksgegevens vanuit een bestand laden

Download de voorbeeldgegevens voor deze quickstart van [GitHub](https://github.com/Azure-Samples/cognitive-services-quickstart-code/blob/master/javascript/AnomalyDetector/request-data.csv):
1. Klik in uw browser met de rechtermuisknop op **Onbewerkt**.
2. Klik op **Koppeling opslaan als**.
3. Sla het bestand op in de map van de toepassing als CSV-bestand.

Deze tijdreeksgegevens worden opgemaakt als CSV-bestand en naar de Anomaly Detector-API verzonden.

Lees het gegevensbestand met de `readFileSync()`-methode van de CSV-parseerbibliotheek en parseer het bestand met `parse()`. Voor elke regel pusht u een [puntobject](/javascript/api/@azure/cognitiveservices-anomalydetector/point?view=azure-node-latest) met het tijdstempel en de numerieke waarde.

[!code-javascript[Read the data file](~/cognitive-services-quickstart-code/javascript/AnomalyDetector/anomaly_detector_quickstart.js?name=readFile)]

## <a name="detect-anomalies-in-the-entire-data-set"></a>Anomalieën in de volledige gegevensset detecteren 

Roep de API aan om anomalieën te detecteren in de volledige tijdreeksgegevens met behulp van de [entireDetect()](/javascript/api/@azure/cognitiveservices-anomalydetector/anomalydetectorclient?view=azure-node-latest#entiredetect-request--msrest-requestoptionsbase-)-methode van de client. Sla het geretourneerde [EntireDetectResponse](/javascript/api/@azure/cognitiveservices-anomalydetector/entiredetectresponse?view=azure-node-latest)-object op. Herhaal de `isAnomaly`-lijst van de reactie en druk de index van alle `true`-waarden af. Deze waarden komen overeen met de index van afwijkende gegevenspunten, als die zijn gevonden.

[!code-javascript[Batch detection function](~/cognitive-services-quickstart-code/javascript/AnomalyDetector/anomaly_detector_quickstart.js?name=batchCall)]

## <a name="detect-the-anomaly-status-of-the-latest-data-point"></a>De anomaliestatus van het laatste gegevenspunt detecteren

Roep de Anomaly Detector-API aan om te bepalen of uw laatste gegevenspunt een anomalie is met behulp van de [lastDetect()](/javascript/api/@azure/cognitiveservices-anomalydetector/anomalydetectorclient?view=azure-node-latest#lastdetect-request--msrest-requestoptionsbase-)-methode van de client en sla het geretourneerde [LastDetectResponse](/javascript/api/@azure/cognitiveservices-anomalydetector/lastdetectresponse?view=azure-node-latest)-object op. De `isAnomaly`-waarde van de reactie is een booleaanse waarde die de anomaliestatus van het punt aangeeft.  

[!code-javascript[Last point detection function](~/cognitive-services-quickstart-code/javascript/AnomalyDetector/anomaly_detector_quickstart.js?name=lastDetection)]

## <a name="detect-change-points-in-the-data-set"></a>Wijzigingspunten in de gegevensset detecteren

Roep de API aan om wijzigingspunten in de tijdreeks te detecteren met behulp van de methode [detectChangePoint()](https://go.microsoft.com/fwlink/?linkid=2090788) van de client. Sla het geretourneerde [ChangePointDetectResponse](https://go.microsoft.com/fwlink/?linkid=2090788)-object op. Herhaal de `isChangePoint`-lijst van de reactie en druk de index van alle `true`-waarden af. Deze waarden komen overeen met de indexen van trendwijzigingspunten, als die zijn gevonden.

[!code-javascript[detect change points](~/cognitive-services-quickstart-code/javascript/AnomalyDetector/anomaly_detector_quickstart.js?name=changePointDetection)]

## <a name="run-the-application"></a>De toepassing uitvoeren

Voer de toepassing uit met de opdracht `node` in uw quickstart-bestand.

```console
node index.js
```

[!INCLUDE [anomaly-detector-next-steps](../quickstart-cleanup-next-steps.md)]