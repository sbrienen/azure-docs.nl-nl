---
title: Een Knowledge Base bewerken-QnA Maker
description: Met QnA Maker kunt u de inhoud van uw Knowledge Base beheren door een gebruiks vriendelijke ervaring te bieden.
ms.service: cognitive-services
ms.subservice: qna-maker
ms.topic: conceptual
ms.date: 07/16/2020
ms.openlocfilehash: 3940f060209ea5ba55957a3673020656d45de9e4
ms.sourcegitcommit: a43a59e44c14d349d597c3d2fd2bc779989c71d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96000093"
---
# <a name="edit-qna-pairs-in-your-knowledge-base"></a>QnA-paren in uw Knowledge Base bewerken

Met QnA Maker kunt u de inhoud van uw Knowledge Base beheren door een gebruiks vriendelijke ervaring te bieden.

QnA-paren worden toegevoegd uit een gegevens bron, zoals een bestand of URL, of worden toegevoegd als een redactionele bron. Een redactionele bron geeft aan dat het QnA paar hand matig is toegevoegd in de QnA-Portal. Alle QnA-paren zijn beschikbaar om te bewerken.

<a name="add-an-editorial-qna-set"></a>

## <a name="add-an-editorial-qna-pair"></a>Een redactionel QnA-paar toevoegen

1. Meld u aan bij de [QnA-Portal](https://www.qnamaker.ai/)en selecteer vervolgens de Knowledge Base waaraan u het QnA-paar wilt toevoegen.
1. Selecteer op de pagina **bewerken** van de Knowledge Base **QnA paar toevoegen** om een nieuw QnA-paar toe te voegen.

    > [!div class="mx-imgBorder"]
    > ![QnA paar toevoegen](../media/qnamaker-how-to-edit-kb/add-qnapair.png)

1. Voeg in de rij nieuw QnA paar de vereiste vraag-en antwoord velden toe. De andere velden zijn optioneel. Alle velden kunnen op elk gewenst moment worden gewijzigd.

1. Voeg eventueel **[alternatieve formule ring](../Quickstarts/add-question-metadata-portal.md#add-additional-alternatively-phrased-questions)** toe. Alternatieve formule ring is een vorm van de vraag die significant afwijkt van de oorspronkelijke vraag, maar moet hetzelfde antwoord geven.

    Wanneer uw Knowledge Base is gepubliceerd en u [actief leren](use-active-learning.md) hebt ingeschakeld, QnA maker u alternatieve opties voor formule ring verzamelen die u kunt accepteren. Deze opties worden geselecteerd om de nauw keurigheid van de voor spelling te verg Roten.

1. Voeg eventueel **[meta gegevens](../Quickstarts/add-question-metadata-portal.md#add-metadata-to-filter-the-answers)** toe. Selecteer **weergave opties** in het context menu om meta gegevens weer te geven. Meta gegevens bieden filters voor de antwoorden die de client toepassing, zoals een chat-bot, biedt.

1. U kunt eventueel **[opvolgings aanwijzingen](multiturn-conversation.md)** toevoegen. Bij opvolgings prompts worden extra conversatie paden naar de client toepassing voor de gebruiker weer gegeven.

1. Selecteer **opslaan en trainen** om voor spellingen te zien, met inbegrip van het nieuwe QnA-paar.

## <a name="rich-text-editing-for-answer"></a>RTF bewerken voor antwoord

Met RTF-bewerking van uw antwoord tekst kunt u de opmaak van een eenvoudige werk balk afprijsen.

1. Selecteer het tekst gebied voor een antwoord. de werk balk voor de Rich-tekst editor wordt weer gegeven op de rij QnA paar.

    > [!div class="mx-imgBorder"]
    > ![Scherm opname van de RTF-editor met de vraag en het antwoord van een QnA-paar rij.](../media/qnamaker-how-to-edit-kb/rich-text-control-qna-pair-row.png)

    Alle tekst die al in het antwoord is opgenomen, wordt correct weer gegeven wanneer uw gebruiker deze van een bot ziet.

1. Bewerk de tekst. Selecteer functies opmaken in de werk balk voor het uitvoeren van tekst met opmaak, of gebruik de wissel functie om over te scha kelen naar de afkortings syntaxis.

    > [!div class="mx-imgBorder"]
    > ![Gebruik de RTF-editor om tekst te schrijven en op te maken en op te slaan als korting.](../media/qnamaker-how-to-edit-kb/rich-text-display-image.png)

    |Functies van Rich Text Editor|Sneltoets|
    |--|--|
    |Scha kelen tussen RTF-editor en prijs verlaging. `</>`|CTRL+M|
    |Titel. **B**|AFDELING + LB|
    |Cursief, aangeduid met een cursieve **_I_**|CTRL + I|
    |Ongeordende lijst||
    |Geordende lijst||
    |Alineaopmaakprofiel||
    |Afbeelding: een afbeelding toevoegen die beschikbaar is via een open bare URL.|CTRL + G|
    |Voeg een koppeling toe aan de openbaar beschik bare URL.|CTRL + K|
    |Emoticon: Voeg een selectie van emoticons toe.|CTRL + E|
    |Geavanceerd menu-ongedaan maken|CTRL + Z|
    |Menu Geavanceerd-opnieuw uitvoeren|CTRL + Y|

1. Voeg een afbeelding aan het antwoord toe met behulp van het afbeeldings pictogram op de Rich Text-werk balk. De in-place editor moet de URL voor openbaar toegankelijke afbeelding en de alternatieve tekst voor de afbeelding hebben.


    > [!div class="mx-imgBorder"]
    > ![Scherm afbeelding toont de in-place editor met de URL voor de open bare afbeelding en de alternatieve tekst voor de ingevoerde afbeelding.](../media/qnamaker-how-to-edit-kb/add-image-url-alternate-text.png)

1. Voeg een koppeling naar een URL toe door de tekst in het antwoord te selecteren en vervolgens het koppelings pictogram op de werk balk te selecteren of door het koppelings pictogram in de werk balk te selecteren en vervolgens nieuwe tekst en de URL in te voeren.

    > [!div class="mx-imgBorder"]
    > ![Gebruik de RTF-editor om een openbaar toegankelijke afbeelding en de bijbehorende ALT-tekst toe te voegen.](../media/qnamaker-how-to-edit-kb/add-link-to-answer-rich-text-editor.png)

## <a name="edit-a-qna-pair"></a>Een QnA-paar bewerken

Elk veld in een QnA paar kan worden bewerkt, ongeacht de oorspronkelijke gegevens bron. Sommige velden zijn mogelijk niet zichtbaar vanwege de instellingen voor de huidige **weergave opties** , die u vindt in de context hulpprogramma balk.

## <a name="delete-a-qna-pair"></a>Een QnA-paar verwijderen

Als u een QnA wilt verwijderen, klikt u op het pictogram **verwijderen** helemaal rechts van de rij QnA. Dit is een permanente bewerking. Deze kan niet ongedaan worden gemaakt. U kunt uw KB exporteren vanaf de pagina **publiceren** voordat u paren verwijdert.

![QnA paar verwijderen](../media/qnamaker-how-to-edit-kb/delete-qnapair.png)

## <a name="find-the-qna-pair-id"></a>De QnA-paar-ID zoeken

Als u de QnA-paar-ID moet vinden, kunt u deze op twee plaatsen vinden:

* Beweeg de muis aanwijzer over het pictogram verwijderen op de QnA die u interesseren. De aanwijs tekst bevat de QnA-paar-ID.
* De Knowledge Base exporteren. Elk QnA-paar in de Knowledge Base bevat de QnA-paar ID.

## <a name="add-alternate-questions"></a>Alternatieve vragen toevoegen

Voeg alternatieve vragen toe aan een bestaand QnA-paar om de kans te verg Roten dat er een overeenkomst is met een gebruikers query.

![Alternatieve vragen toevoegen](../media/qnamaker-how-to-edit-kb/add-alternate-question.png)

## <a name="linking-qna-pairs"></a>QnA-paren koppelen

Het koppelen van QnA-paren wordt bij [opvolgings aanwijzingen](multiturn-conversation.md)gegeven. Dit is een logische verbinding tussen QnA-paren die worden beheerd op het niveau van de kennis base. U kunt opvolgings prompts bewerken in de QnA Maker Portal.

U kunt geen QnA-paren koppelen in de meta gegevens van het antwoord.

## <a name="add-metadata"></a>Meta gegevens toevoegen

Voeg eerst de **Opties voor** het toevoegen van meta gegevens toe, en selecteer vervolgens **meta gegevens weer geven**. Hiermee wordt de kolom meta gegevens weer gegeven. Selecteer vervolgens het **+** teken om een meta gegevens paar toe te voegen. Dit paar bestaat uit één sleutel en één waarde.

Meer informatie over meta gegevens vindt u in de QnA Maker portal voor meta gegevens:
* [Creatie: metagegevens toevoegen aan QnA-paar](../quickstarts/add-question-metadata-portal.md#add-metadata-to-filter-the-answers)
* [Queryvoorspelling: antwoorden filteren op metagegevens](../quickstarts/get-answer-from-knowledge-base-using-url-tool.md)

## <a name="save-changes-to-the-qna-pairs"></a>Wijzigingen in de QnA-paren opslaan

Selecteer regel matig **opslaan en trainen** na het maken van bewerkingen om te voor komen dat wijzigingen verloren gaan.

![Meta gegevens toevoegen](../media/qnamaker-how-to-edit-kb/add-metadata.png)

## <a name="when-to-use-rich-text-editing-versus-markdown"></a>Wanneer gebruik ik RTF-bewerking versus korting

Met [RTF-bewerking](#add-an-editorial-qna-set) van antwoorden kunt u, als auteur, een opmaak werkbalk gebruiken om snel tekst te selecteren en op te maken.

De [prijs verlaging](../reference-markdown-format.md) is een beter hulp middel wanneer u inhoud automatisch moet genereren om kennis te maken van de Knowledge bases die als onderdeel van een CI/cd-pijp lijn of voor [batch tests](../Quickstarts/batch-testing.md)moeten worden geïmporteerd.

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Samenwerken aan een knowledge base](./collaborate-knowledge-base.md)

* [Azure-resources beheren die worden gebruikt door QnA Maker](set-up-qnamaker-service-azure.md)
