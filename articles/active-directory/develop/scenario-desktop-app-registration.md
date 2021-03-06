---
title: Bureau blad-apps registreren die web-Api's aanroepen-micro soft Identity-platform | Azure
description: Meer informatie over het bouwen van een bureau blad-app die web-Api's aanroept (app-registratie)
services: active-directory
author: jmprieur
manager: CelesteDG
ms.service: active-directory
ms.subservice: develop
ms.topic: conceptual
ms.workload: identity
ms.date: 09/09/2019
ms.author: jmprieur
ms.custom: aaddev
ms.openlocfilehash: 787380dbf6f739d4b88f18a836da2146b06024c3
ms.sourcegitcommit: 6109f1d9f0acd8e5d1c1775bc9aa7c61ca076c45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94443140"
---
# <a name="desktop-app-that-calls-web-apis-app-registration"></a>Bureau blad-app voor het aanroepen van web-Api's: app-registratie

In dit artikel worden de app-registratie gegevens voor een bureaublad toepassing besproken.

## <a name="supported-account-types"></a>Ondersteunde accounttypen

De account typen die worden ondersteund in een bureaublad toepassing, zijn afhankelijk van de ervaring die u wilt oplichten. Vanwege deze relatie zijn de ondersteunde account typen afhankelijk van de stromen die u wilt gebruiken.

### <a name="audience-for-interactive-token-acquisition"></a>Doel groep voor het verkrijgen van interactief tokens

Als uw bureaublad toepassing interactieve verificatie gebruikt, kunt u gebruikers van elk [account type](quickstart-register-app.md)aanmelden.

### <a name="audience-for-desktop-app-silent-flows"></a>Doel groep voor desktop-app Silent flows

- Als u geïntegreerde Windows-verificatie of een gebruikers naam en wacht woord wilt gebruiken, moet uw toepassing zich aanmelden bij uw eigen Tenant, bijvoorbeeld als u een LOB-ontwikkelaar (line-of-Business) bent. Of, in Azure Active Directory organisaties, moet uw toepassing gebruikers in uw eigen Tenant aanmelden als deze een ISV-scenario is. Deze verificatie stromen worden niet ondersteund voor persoonlijke micro soft-accounts.
- Als u gebruikers aanmeldt met sociale identiteiten die een Business-to-commerce (B2C)-instantie en-beleid door geven, kunt u alleen de interactieve verificatie en gebruikers naam-wacht woord gebruiken.

## <a name="redirect-uris"></a>Omleidings-Uri's

De omleidings-Uri's voor gebruik in een bureaublad toepassing is afhankelijk van de stroom die u wilt gebruiken.

- Als u interactieve verificatie of de code stroom van het apparaat gebruikt, gebruikt u `https://login.microsoftonline.com/common/oauth2/nativeclient` . Als u deze configuratie wilt behaalt, selecteert u de bijbehorende URL in het gedeelte **verificatie** voor uw toepassing.

  > [!IMPORTANT]
  > Vandaag gebruikt MSAL.NET een andere omleidings-URI standaard in bureaublad toepassingen die worden uitgevoerd op Windows ( `urn:ietf:wg:oauth:2.0:oob` ). In de toekomst wilt u deze standaard instelling wijzigen. u wordt aangeraden om te gebruiken `https://login.microsoftonline.com/common/oauth2/nativeclient` .

- Als u een systeem eigen doel-C of SWIFT-app voor macOS bouwt, moet u de omleidings-URI registreren op basis van de bundel-id van uw toepassing in de volgende indeling: `msauth.<your.app.bundle.id>://auth` . Vervang door `<your.app.bundle.id>` de bundel-id van uw toepassing.
- Als uw app alleen geïntegreerde Windows-verificatie of een gebruikers naam en wacht woord gebruikt, hoeft u geen omleidings-URI voor uw toepassing te registreren. Deze stromen maken een retour afronding naar het micro soft Identity platform v 2.0-eind punt. Uw toepassing wordt niet terugaangeroepen op een specifieke URI.
- Voor het onderscheiden van de [apparaatcode stroom](scenario-desktop-acquire-token.md#device-code-flow), [geïntegreerde Windows-verificatie](scenario-desktop-acquire-token.md#integrated-windows-authentication)en een [gebruikers naam en wacht woord](scenario-desktop-acquire-token.md#username-and-password) van een vertrouwelijke client toepassing met behulp van een client referentie stroom die wordt gebruikt in [daemon-toepassingen](scenario-daemon-overview.md), waarvoor geen omleidings-URI is vereist, moet u deze configureren als een open bare client toepassing. Deze configuratie wordt gerealiseerd:

    1. Selecteer in de [Azure Portal](https://portal.azure.com)uw app in **app-registraties** en selecteer vervolgens **verificatie**.
    1. In **Geavanceerde instellingen**  >  **standaard client type**  >  **behandel toepassing als een open bare client** , selecteert u **Ja**.

        :::image type="content" source="media/scenarios/default-client-type.png" alt-text="Instelling van open bare client inschakelen in het deel venster verificatie in Azure Portal":::

## <a name="api-permissions"></a>API-machtigingen

Bureau blad-Apps bellen Api's voor de aangemelde gebruiker. Ze moeten gedelegeerde machtigingen aanvragen. Ze kunnen geen toepassings machtigingen aanvragen, die alleen worden verwerkt in [daemon-toepassingen](scenario-daemon-overview.md).

## <a name="next-steps"></a>Volgende stappen

Ga naar het volgende artikel in dit scenario, configuratie van de [app-code](scenario-desktop-app-configuration.md).
