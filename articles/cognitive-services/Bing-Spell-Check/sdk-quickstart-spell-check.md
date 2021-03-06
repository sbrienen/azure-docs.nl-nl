---
title: 'Quickstart: Spellingcontrole met de Bing Spellingcontrole-SDK voor C#'
titleSuffix: Azure Cognitive Services
description: Aan de slag met de Bing Spellingcontrole-REST API om spelling en grammatica te controleren.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: bing-spell-check
ms.topic: quickstart
ms.date: 12/16/2019
ms.author: aahi
ms.custom: devx-track-csharp
ms.openlocfilehash: b2df7bab9bceaefae5793e4802eba6a6aa218e96
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/08/2020
ms.locfileid: "94364799"
---
# <a name="quickstart-check-spelling-with-the-bing-spell-check-sdk-for-c"></a>Quickstart: Spellingcontrole met de Bing Spellingcontrole-SDK voor C#

> [!WARNING]
> Bing Search-API's worden van Cognitive Services naar Bing Search Services verplaatst. Vanaf **30 oktober 2020** moeten nieuwe instanties van Bing Search worden ingericht volgens het proces dat [hier](https://aka.ms/cogsvcs/bingmove) is beschreven.
> Bing Search-API's ingericht met behulp van Cognitive Services, worden voor de komende drie jaar of tot het einde van uw Enterprise Agreement ondersteund, afhankelijk van wat het eerst afloopt.
> Zie [Bing Search Services](https://aka.ms/cogsvcs/bingmigration) voor migratie-instructies.

Gebruik deze quickstart om te beginnen met de Bing Spellingcontrole-SDK voor C#. Hoewel de Bing Spellingcontrole een REST-API heeft die compatibel is met de meeste programmeertalen, biedt de SDK een eenvoudige manier om de service in uw toepassingen te integreren. De broncode voor dit voorbeeld is te vinden op [GitHub](https://github.com/Azure-Samples/cognitive-services-dotnet-sdk-samples/tree/master/samples/SpellCheck).

## <a name="application-dependencies"></a>Afhankelijkheden van de toepassing

* Een versie van [Visual Studio 2017 of hoger](https://visualstudio.microsoft.com/downloads/).
* [NuGet-pakket](https://www.nuget.org/packages/Microsoft.Azure.CognitiveServices.Language.SpellCheck) voor de Bing Spellingcontrole

Als u de Bing Spellingcontrole-SDK wilt toevoegen aan uw project, selecteert u **NuGet-pakketten beheren** vanuit **Solution Explorer** in Visual Studio. Voeg het pakket `Microsoft.Azure.CognitiveServices.Language.SpellCheck` toe. Dit pakket installeert ook de volgende afhankelijkheden:

* Microsoft.Rest.ClientRuntime
* Microsoft.Rest.ClientRuntime.Azure
* Newtonsoft.Json

[!INCLUDE [cognitive-services-bing-spell-check-signup-requirements](../../../includes/cognitive-services-bing-spell-check-signup-requirements.md)]

## <a name="create-and-initialize-the-application"></a>De toepassing maken en initialiseren

1. Maak een nieuwe C#-console-oplossing in Visual Studio. Voeg daarna de volgende `using`-instructie toe.
    
    ```csharp
    using System;
    using System.Linq;
    using System.Threading.Tasks;
    using Microsoft.Azure.CognitiveServices.Language.SpellCheck;
    using Microsoft.Azure.CognitiveServices.Language.SpellCheck.Models;
    ```

2. Maak een nieuwe klasse. Maak vervolgens een asynchrone functie met de naam `SpellCheckCorrection()` die een abonnementssleutel vereist en de aanvraag van de spellingcontrole verstuurt.

3. Maak een instantie van de client door een nieuw `ApiKeyServiceClientCredentials`-object te maken. 

    ```csharp
    public static class SpellCheckSample{
        public static async Task SpellCheckCorrection(string key){
            var client = new SpellCheckClient(new ApiKeyServiceClientCredentials(key));
        }
        //...
    }
    ```

## <a name="send-the-request-and-read-the-response"></a>De aanvraag verzenden en het antwoord lezen

1. Voer in de hierboven gemaakte functie de volgende stappen uit. Verstuur de aanvraag van de spellingcontrole met de client. Voeg de te controleren tekst toe aan de `text`-parameter en stel de modus in op `proof`.  
    
    ```csharp
    var result = await client.SpellCheckerWithHttpMessagesAsync(text: "Bill Gatas", mode: "proof");
    ```

2. Haal het eerste resultaat van de spellingcontrole op, als dat beschikbaar is. Druk het eerste verkeerd gespelde woord (token) af, het type token en het aantal suggesties.

    ```csharp
    var firstspellCheckResult = result.Body.FlaggedTokens.FirstOrDefault();
    
    if (firstspellCheckResult != null)
    {
        Console.WriteLine("SpellCheck Results#{0}", result.Body.FlaggedTokens.Count);
        Console.WriteLine("First SpellCheck Result token: {0} ", firstspellCheckResult.Token);
        Console.WriteLine("First SpellCheck Result Type: {0} ", firstspellCheckResult.Type);
        Console.WriteLine("First SpellCheck Result Suggestion Count: {0} ", firstspellCheckResult.Suggestions.Count);
    }
    ```

3. Neem de eerste voorgestelde correctie, indien er een is. Druk de suggestiescore en het voorgestelde woord af. 

    ```csharp
    var suggestions = firstspellCheckResult.Suggestions;

    if (suggestions?.Count > 0)
    {
        var firstSuggestion = suggestions.FirstOrDefault();
        Console.WriteLine("First SpellCheck Suggestion Score: {0} ", firstSuggestion.Score);
        Console.WriteLine("First SpellCheck Suggestion : {0} ", firstSuggestion.Suggestion);
    }
    ```

## <a name="run-the-application"></a>De toepassing uitvoeren

Bouw uw project en voer het uit. Als u Visual Studio gebruikt, drukt u op **F5** om fouten in het bestand op te sporen.

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Een web-app met één pagina maken](tutorials/spellcheck.md)

- [Wat is de Bing Spellingcontrole-API?](overview.md)
- [Bing Spellingcontrole C# SDK Reference guide](/dotnet/api/overview/azure/cognitiveservices/client/bingspellcheck?view=azure-dotnet)