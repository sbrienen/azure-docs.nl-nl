---
title: Tags voor Cognitive Services-containerinstallatiekopie
titleSuffix: Azure Cognitive Services
description: Een uitgebreide lijst met alle afbeeldings Tags voor de cognitieve service container.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.topic: reference
ms.date: 11/17/2020
ms.author: aahi
ms.openlocfilehash: 09a83c28d07540b8ecd813e7ab2f10ceee891d7a
ms.sourcegitcommit: 6a770fc07237f02bea8cc463f3d8cc5c246d7c65
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95792976"
---
# <a name="azure-cognitive-services-container-image-tags-and-release-notes"></a>Azure Cognitive Services container-afbeeldings Tags en opmerkingen bij de release

Azure Cognitive Services biedt veel container installatie kopieën. De container registers en de bijbehorende opslag plaatsen variëren tussen container installatie kopieën. De naam van elke container installatie kopie biedt meerdere labels. Een container afbeeldings code is een mechanisme voor het versie beheer van de container installatie kopie. Dit artikel is bedoeld om te worden gebruikt als een uitgebreide verwijzing voor het weer geven van alle Cognitive Services container installatie kopieën en de beschik bare Tags.

> [!TIP]
> Wanneer u gebruikt [`docker pull`](https://docs.docker.com/engine/reference/commandline/pull/) , moet u zorgvuldig letten op de behuizing van het container register, de opslag plaats, de naam van de container installatie kopie en de bijbehorende tag. Dit zijn **hoofdletter gevoelig**.

## <a name="anomaly-detector"></a>Anomaly Detector

De [afwijkende detector][ad-containers] container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/decision` opslag plaats en heet `anomaly-detector` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/decision/anomaly-detector` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/decision/anomaly-detector/tags/list).

# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.013560003-amd64-preview` |      |

# <a name="previous-versions"></a>[Vorige versies](#tab/previous)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `1.1.012300001-amd64-preview` |       |

---

## <a name="read-ocr-optical-character-recognition"></a>OCR (optische teken herkenning) lezen

De [Computer Vision][cv-containers] OCR-container installatie kopie lezen kan worden gevonden in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services` opslag plaats en heet `read` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/vision/read` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/vision/read/tags/list).

# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

Release opmerkingen voor `3.2-preview.1` :

* Nieuwe container van v 3.2

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `latest`                      |       |
| `3.2-preview.1` |  |

# <a name="previous-versions"></a>[Vorige versies](#tab/previous)

Release opmerkingen voor `v2.0.013250001-amd64-preview` :

* Verminder het geheugen gebruik voor de container.
* Externe cache is vereist voor het instellen van meerdere peulen. Stel bijvoorbeeld redis in voor caching.
* Vast ontbrekend resultaat wanneer de redis-cache is ingesteld en `ResultExpirationPeriod` is ingesteld op 0.
* De limiet voor de grootte van de aanvraag hoofdtekst van 26MB verwijderen. De container kan nu >26MB-bestanden accepteren.
* Tijds tempel en build-versie toevoegen aan console logboek registratie.

Release opmerkingen voor `1.1.013050001-amd64-preview`

* `ReadEngineConfig:ResultExpirationPeriod`De configuratie van de container initialisatie is toegevoegd om op te geven wanneer het systeem de herkennings resultaten moet opschonen. 
    * De instelling is in uren en de standaard waarde is 48 uur.
    * De instelling kan het geheugen gebruik verminderen voor het opslaan van de resultaten, met name als de opslag ruimte in het geheugen wordt gebruikt.
    * Voorbeeld 1. ReadEngineConfig: ResultExpirationPeriod = 1, het systeem verwijdert het herkennings resultaat 1hr na het proces.
    * Als deze configuratie is ingesteld op 0, wordt het herkennings resultaat door het systeem gewist nadat het resultaat is opgehaald.

* Er is een interne server fout 500 opgelost wanneer een ongeldige afbeeldings indeling wordt door gegeven aan het systeem. Er wordt nu een 400-fout geretourneerd:

    ```json
    {
        "error": {
        "code": "InvalidImageSize",
        "message": "Image must be between 1024 and 209715200 bytes."
        }
    }
    ```

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `2.0.013250001-amd64-preview` |       |
| `1.1.013050001-amd64-preview` |       |
| `1.1.011580001-amd64-preview` |       |
| `1.1.009920003-amd64-preview` |       |
| `1.1.009910003-amd64-preview` |       |

---


## <a name="form-recognizer"></a>Form Recognizer

De container installatie kopie voor de [formulier herkenning][fr-containers] vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/custom-form` opslag plaats en heet `labeltool` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/custom-form/labeltool` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/custom-form/labeltool/tags/list).

# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.009301-amd64-preview`    |       |


# <a name="previous-versions"></a>[Vorige versies](#tab/previous)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `1.1.008640001-amd64-preview` |       |
| `1.1.008510001-amd64-preview` |       |

---

## <a name="language-understanding-luis"></a>Language Understanding (LUIS)

De [Luis][lu-containers] -container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/language` opslag plaats en heet `luis` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/language/luis` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/language/luis/tags/list).

# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.012280003-amd64-preview` |       |


# <a name="previous-version"></a>[Vorige versie](#tab/previous)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `1.1.012130003-amd64-preview` |       |

---

## <a name="custom-speech-to-text"></a>Custom Speech-naar-tekst

De [Custom speech-naar-tekst][sp-cstt] container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/speechservices/` opslag plaats en heet `custom-speech-to-text` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/speechservices/custom-speech-to-text` . U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/custom-speech-to-text/tags/list).


# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

Release Opmerking voor `2.7.0-amd64` :

**Functies**
* Interpunctie is standaard ingesteld op ingeschakeld.

Houd er rekening mee dat de grootte van deze container installatie kopie groter is geworden vanwege de opgenomen woordgroepen lijsten.

| Afbeeldings Tags                    | Notities | Samenvatting                                                                  |
|-------------------------------|:------|:------------------------------------------------------------------------|
| `latest`                      |       | `sha256:d1573c2543cb7afedb0122da0995f345767b02f9c5f181950acf1509ca65726` |
| `2.7.0-amd64`                 |       | `sha256:d1573c2543cb7afedb0122da0995f345767b02f9c5f181950acf1509ca65726` |


# <a name="previous-version"></a>[Vorige versie](#tab/previous)
Release Opmerking voor `2.6.0-amd64` :

**Functies**
* Ondersteuning voor phraselist v2 
* Woordgroepen lijsten worden ondersteund in de volgende land instellingen:
    * en-au
    * en-ca
    * en-GB
    * en-in
    * nl-nl
    * zh-cn
* Ondersteuning voor het downloaden van een aangepast basis model. 
    * Gebruiken `BaseModelLocale=<locale>` met de `docker run` opdracht
* Volledig gemigreerd naar .NET 3,1

**Dit**
* Er is een probleem opgelost waarbij de betrouwbaarheids Score altijd 1 is in de Diarization-modus
* Gemigreerd naar de TextAnalytics 3,0-API

Houd er rekening mee dat de grootte van deze container installatie kopie groter is geworden vanwege de opgenomen woordgroepen lijsten.

Release Opmerking voor `2.5.0-amd64` :

**Functies**
* Aangepaste uitspraak op aangepaste modellen ondersteunen
* Azure en Azure Amerikaanse overheids Cloud ondersteunen

**Dit**
* Het uitvoeren als niet-hoofd gebruikers probleem in de Diarization-modus oplossen

| Afbeeldings Tags                    | Notities               |
|-------------------------------|:--------------------|
| `2.6.0-amd64`                 |                     |
| `2.5.0-amd64`                 |   1e GA-versie    |

---

## <a name="custom-text-to-speech"></a>Aangepaste tekst-naar-spraak

De [aangepaste tekst-naar-spraak-][sp-ctts] container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/speechservices/` opslag plaats en heet `custom-text-to-speech` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/speechservices/custom-text-to-speech` . U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/custom-text-to-speech/tags/list).


# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

Release Opmerking voor `1.9.0-amd64` :

Reguliere maandelijkse release

| Afbeeldings Tags                    | Notities | Samenvatting                                                                  |
|-------------------------------|:------|:------------------------------------------------------------------------|
| `latest`                      |       | `sha256:e0397cf12d1367b13dd258f782bb513c93afcd5ee4b897794fe533205336355` |
| `1.9.0-amd64`                 |       | `sha256:e0397cf12d1367b13dd258f782bb513c93afcd5ee4b897794fe533205336355` |


# <a name="previous-version"></a>[Vorige versie](#tab/previous)
Release Opmerking voor `1.8.0-amd64` :

**Functies**
* Volledig gemigreerd naar .NET 3,1

Release Opmerking voor `1.7.0-amd64` :

**Functie**
* Gedeeltelijk gemigreerd naar .NET 3,1

| Afbeeldings Tags                    | Notities               |
|-------------------------------|:--------------------|
| `1.8.0-amd64`                 |                     |
| `1.7.0-amd64`                 |   1e GA-versie    |

---

## <a name="speech-to-text"></a>Spraak naar tekst

De afbeelding voor de [spraak-naar-tekst][sp-stt] container kan worden gevonden in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/speechservices/` opslag plaats en heet `speech-to-text` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/speechservices/speech-to-text` . U kunt een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/speech-to-text/tags/list).

Sinds spraak-naar-tekst v-2.5.0 worden afbeeldingen ondersteund in de regio van de *Amerikaanse overheids-Virginia* . Gebruik het facturerings eindpunt en de API-sleutels van de *Amerikaanse overheid* wanneer u deze regio gebruikt.

# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

Release Opmerking voor `2.7.0-amd64-<locale>` :

**Functies**
* Ondersteuning voor de volgende nieuwe land instellingen:
    * AR-BH, AR-IQ, AR-Jo, AR-lb, AR-om, AR-sy
    * bg-bg
    * el-gr
    * en-HK, en-IE, en-pH, en-SG en en-za
    * es-ar, es-Bo, es-LC, es-co, es-CR, es-Cu, es-do, es-EC, es-gt, es-PA, es-PE, es-PR, Sen-py, es-SV, es-am, es-uy, es-ve
    * et-ee
    * ga-ie
    * hr-hr
    * hu-hu
    * lt-lt
    * lv-lv
    * mt-mt
    * ro-ro
    * sk-sk
    * SL-SL
* Interpunctie is standaard ingeschakeld.

Houd er rekening mee dat de grootte van deze container installatie kopie groter is geworden vanwege de opgenomen woordgroepen lijsten. 

| Afbeeldings Tags                    | Notities                                                                                                |
|-------------------------------|:-----------------------------------------------------------------------------------------------------|
| `latest`                      | Container installatie kopie met de `en-US` land instelling.                                                             |
| `2.7.0-amd64-<locale>`        | Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `2.7.0-amd64-en-us`. |

Voor deze container zijn de volgende land instellingen beschikbaar.

| Land instelling voor v 2.7.0           | Notities                                    | Samenvatting                                                                  |
|-----------------------------|:-----------------------------------------|:------------------------------------------------------------------------|
| `ar-ae`                     | Container installatie kopie met de `ar-AE` land instelling. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-bh`                     | Container installatie kopie met de `ar-BH` land instelling. | `sha256:5a2c140661f50d0c95587121ec1ab8895289f4dda5b3ad14074413e869e6bd4` |
| `ar-eg`                     | Container installatie kopie met de `ar-EG` land instelling. | `sha256:783bb8321fcfb7890b0c99935099f7e84c85a698c2fe0031c661e265358d79c` |
| `ar-iq`                     | Container installatie kopie met de `ar-IQ` land instelling. | `sha256:abd0101f73c1cf71f30da7b11b93d2a7ac8877dbfcfc2d34553d20705aca7a2` |
| `ar-jo`                     | Container installatie kopie met de `ar-JO` land instelling. | `sha256:d4c7fd2a1637e163aa106c23b6a759e8c78366c60ece83b3aabfe93ebabae07` |
| `ar-kw`                     | Container installatie kopie met de `ar-KW` land instelling. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-lb`                     | Container installatie kopie met de `ar-LB` land instelling. | `sha256:20e5c9105e86625c72de54290a6eb07630d35c3760f729c4b855e3661583dfe` |
| `ar-om`                     | Container installatie kopie met de `ar-OM` land instelling. | `sha256:97f1b44f2cbb837a2ef86441a0a52a07f706240edb6ef6618ee4db8cbbe1c19` |
| `ar-qa`                     | Container installatie kopie met de `ar-QA` land instelling. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-sa`                     | Container installatie kopie met de `ar-SA` land instelling. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-sy`                     | Container installatie kopie met de `ar-SY` land instelling. | `sha256:51980a2e2c3dd3548deedcedaf5fc688db602a5eced1a4b7df7d10750393623` |
| `bg-bg`                     | Container installatie kopie met de `bg-BG` land instelling. | `sha256:1c1acf0fbb353ebb04692f37eb4d4cdf0b4e309720dd7e709001dada0d1ea81` |
| `ca-es`                     | Container installatie kopie met de `ca-ES` land instelling. | `sha256:c60baa0007f61c7652b97b49645215de63411125d627c974c09222e316df204` |
| `cs-cz`                     | Container installatie kopie met de `cs-CZ` land instelling. | `sha256:3fa09fc3a6bde6b77df2444aae8fc78b5f25fb9010171d1682db116ea5801f5` |
| `da-dk`                     | Container installatie kopie met de `da-DK` land instelling. | `sha256:4b26dbba50c2771943880b68e0e4ea0713d0e3bb8bad884454849bccc9e94a3` |
| `de-de`                     | Container installatie kopie met de `de-DE` land instelling. | `sha256:5109ed80b1fecf4db0328adcd50528d0aa9e726b5fc84587c40aaea4e91256d` |
| `el-gr`                     | Container installatie kopie met de `el-GR` land instelling. | `sha256:fc8b466c588bf097efac2b79454d5ac0df5c6990398f07ede9be7e1d536e4bd` |
| `en-au`                     | Container installatie kopie met de `en-AU` land instelling. | `sha256:3461892a27fc3eb3f9610b2def00bc15f380c6b9797c90ceca19e6abb55f6a6` |
| `en-ca`                     | Container installatie kopie met de `en-CA` land instelling. | `sha256:a0509be39785f1e869bd96ab10e7c07d3f4e61c9aa17ff5900076e7bd64ba11` |
| `en-gb`                     | Container installatie kopie met de `en-GB` land instelling. | `sha256:1b976fc7ac109e61dcf74af3652c12535e3db92931d2d0bb2ea59bd46f9efed` |
| `en-hk`                     | Container installatie kopie met de `en-HK` land instelling. | `sha256:0b1e1df101f978869c98f6e50632712016b8311fc89b334e7f44e968d64bf2f` |
| `en-ie`                     | Container installatie kopie met de `en-IE` land instelling. | `sha256:c5ba0d3c7219ce39f0b918a51a7cae8a65c277f564279cad920e068725aa39f` |
| `en-in`                     | Container installatie kopie met de `en-IN` land instelling. | `sha256:e907f07be498f024103f6fe6abffa23e242bf3585724741b29a2f3f41d0899c` |
| `en-nz`                     | Container installatie kopie met de `en-NZ` land instelling. | `sha256:66845f6ce20ae71d609867c6eb4772366ce042499e4bcdce4c1b579daf7fad7` |
| `en-ph`                     | Container installatie kopie met de `en-PH` land instelling. | `sha256:e7874653bf66b1a1ab344b3391eb8767be34260b7f11b62fd057cbe17b805b2` |
| `en-sg`                     | Container installatie kopie met de `en-SG` land instelling. | `sha256:827cdb158280e6f4037f4815410c7aa78abf9c6467876c1504aecfef787bdd7` |
| `en-us`                     | Container installatie kopie met de `en-US` land instelling. | `sha256:248d17340055e3e137219ddc234c605e6a53ceead136ea55c9697c352da6a8d` |
| `en-za`                     | Container installatie kopie met de `en-ZA` land instelling. | `sha256:a8abc99f498db7088bb25acec47da81e90b6a5eaa1c6f78e0f9a314d839d0ae` |
| `es-ar`                     | Container installatie kopie met de `es-AR` land instelling. | `sha256:edf78429630851b6eb01f54f8a8a1aeeda9971c6a834403a204662eda22b3b9` |
| `es-bo`                     | Container installatie kopie met de `es-BO` land instelling. | `sha256:5832b44f1da2f6b9a097c99babfbc370d8d0eabe1ff8daabec2c3f482dc9d63` |
| `es-cl`                     | Container installatie kopie met de `es-CL` land instelling. | `sha256:409a712b96235e154472134f96ff9272265f1e5b555e00ad03c2260b0781009` |
| `es-co`                     | Container installatie kopie met de `es-CO` land instelling. | `sha256:99792bc083dc16e0edf15491e6a840d786c9140b747551563a8d98f66f0b415` |
| `es-cr`                     | Container installatie kopie met de `es-CR` land instelling. | `sha256:21fe14a538e5b8b2d288b00b8f5a02d87469e285f32e725155042079f336ac9` |
| `es-cu`                     | Container installatie kopie met de `es-CU` land instelling. | `sha256:05d40eae01cec4c42c4febd379cd61373eb43d0aacfd47b988bb95e6a6ad216` |
| `es-do`                     | Container installatie kopie met de `es-DO` land instelling. | `sha256:73dd0e0d4f39a259563ee7cc18c2e72c9ab20c52905fe343e0413ca7c4b3f0d` |
| `es-ec`                     | Container installatie kopie met de `es-EC` land instelling. | `sha256:c3e69139ef365fe9332b5b68b43458242c7dad9d9f2b557431272306e81cb9e` |
| `es-es`                     | Container installatie kopie met de `es-ES` land instelling. | `sha256:bd83fcfc116ba645a0e12a7a93b6ada74a8f701172f826a91c5f223a1dbaa61` |
| `es-gt`                     | Container installatie kopie met de `es-GT` land instelling. | `sha256:5bb9b18b91b74e123e3720893d88bfcb0a87dac31a1f7171d23c7cb1fa09fee` |
| `es-hn`                     | Container installatie kopie met de `es-HN` land instelling. | `sha256:941d108a4b76eb554e8f13cf5090665a702de3ebf35b75e4350f0916dfccd72` |
| `es-mx`                     | Container installatie kopie met de `es-MX` land instelling. | `sha256:cebea03732781b4425500d162ae6580bbd7ce9b5f4ede988c4570fe311d8567` |
| `es-ni`                     | Container installatie kopie met de `es-NI` land instelling. | `sha256:8ba165f94ad840936ebd0af17a0a63aa08a6292e7ad9029f5b93eef41165eb9` |
| `es-pa`                     | Container installatie kopie met de `es-PA` land instelling. | `sha256:c61b7f1b6801a03c3eab0dd1aede87017a86bc7368ded2f8bad8d9e5f60d0d3` |
| `es-pe`                     | Container installatie kopie met de `es-PE` land instelling. | `sha256:447a3ab3f302aba24d201d9f5b2877ffcd64dfd5e9d6b88d9924847160b2de2` |
| `es-pr`                     | Container installatie kopie met de `es-PR` land instelling. | `sha256:a53b3295c986e91ee8cf93ebe1057b997c76ef7f99913508b859311a194fdd4` |
| `es-py`                     | Container installatie kopie met de `es-PY` land instelling. | `sha256:85b3f75e75e63e29521daf772ee68a59ac2428579512501aa81dc51a2315652` |
| `es-sv`                     | Container installatie kopie met de `es-SV` land instelling. | `sha256:db5ece7ba536e38d5de59cd37807630ab76589dcf1c97e253f98d7f44d9424e` |
| `es-us`                     | Container installatie kopie met de `es-US` land instelling. | `sha256:99f2743725bb71e25543484f49bcfde14584ccbbaaa912678938d69d965075a` |
| `es-uy`                     | Container installatie kopie met de `es-UY` land instelling. | `sha256:a3e11c16a97a1ae76408d812b2fee1e4b3ba07160bbcb62a22814523568ee5d` |
| `es-ve`                     | Container installatie kopie met de `es-VE` land instelling. | `sha256:8cb431aafd84263ead8de946377c1d3f2ddfa7e172b8a4c5aa7ba477c5b41f0` |
| `et-ee`                     | Container installatie kopie met de `et-EE` land instelling. | `sha256:943e7cf894e9d75341a58993104824c1c8cd8da1322cc5a732e9d53882c6523` |
| `fi-fi`                     | Container installatie kopie met de `fi-FI` land instelling. | `sha256:35658e9dce796cb96a1371f250398e86351ea1b5ada080da7ce8471b30c7cae` |
| `fr-ca`                     | Container installatie kopie met de `fr-CA` land instelling. | `sha256:62256cad671e8baa03fdd4c5f4eca7d5c5effedd64cafd9020ba72c9c4210e0` |
| `fr-fr`                     | Container installatie kopie met de `fr-FR` land instelling. | `sha256:b385993232d9daa327d1a7b067268927b17f36eed3e8d423748794544c62746` |
| `ga-ie`                     | Container installatie kopie met de `ga-IE` land instelling. | `sha256:ab9abdb993b0f7487edda8200f1393ac44ba4888c0f444a02afb6c85ca3e393` |
| `gu-in`                     | Container installatie kopie met de `gu-IN` land instelling. | `sha256:328e69488f2948722d7ccc97e266071f61a8c9f65cd671688490955806526de` |
| `hi-in`                     | Container installatie kopie met de `hi-IN` land instelling. | `sha256:b9b0bfec80aa53d06ea2cbd9097f753ec5caaf00ac2f00321ae7ad916fd7fa6` |
| `hr-hr`                     | Container installatie kopie met de `hr-HR` land instelling. | `sha256:ab849cd2eeea682f8958bba8986fe90f0f7bb3b447512a10cf464e8e1ce4ea5` |
| `hu-hu`                     | Container installatie kopie met de `hu-HU` land instelling. | `sha256:30f239b155d91523442cf74a1f2732304fa2b50ae7b786833bb6a020b982621` |
| `it-it`                     | Container installatie kopie met de `it-IT` land instelling. | `sha256:288f95413870eb9d33bf1dabfa6fbd6b55b0faa52e4d5face3171d1dd4ddbdd` |
| `ja-jp`                     | Container installatie kopie met de `ja-JP` land instelling. | `sha256:e3ab37a80c215dec565eca212f57eb81887fc2894452868dff92e3bd42c4bb9` |
| `ko-kr`                     | Container installatie kopie met de `ko-KR` land instelling. | `sha256:c1208b8459333b606af516cd7806e9d4d5e002247bb1225e1f246563b356890` |
| `lt-lt`                     | Container installatie kopie met de `lt-LT` land instelling. | `sha256:8dec331161d3c29fc65ba6651fcc6cfe69fa314519f408b5f9f8eb27da09830` |
| `lv-lv`                     | Container installatie kopie met de `lv-LV` land instelling. | `sha256:7cf31282910b339666bb2b0a555caa7fc6ae414eea4423a41f35c3527f83235` |
| `mr-in`                     | Container installatie kopie met de `mr-IN` land instelling. | `sha256:9cb012bd58ef7723d4905d6fa3c1fde96e33c354b3d96d4e3ff69cf6e1bfe3a` |
| `mt-mt`                     | Container installatie kopie met de `mt-MT` land instelling. | `sha256:a0094c032ea555b168ec5751ab3257337d902d526e9ae335671fb751a352378` |
| `nb-no`                     | Container installatie kopie met de `nb-NO` land instelling. | `sha256:6bbc326e20a6a785b1ca33143b42a060858efb67b863a267d6efb7aebb48f87` |
| `nl-nl`                     | Container installatie kopie met de `nl-NL` land instelling. | `sha256:94b4ddf4cc80fa666e422f8416aea3f98ebe4842dfe9b1f4bfea7c47eb61127` |
| `pl-pl`                     | Container installatie kopie met de `pl-PL` land instelling. | `sha256:58e5f78bf772c3c8cbd5f0c5d6e67f5348e04e3f893d84738a2a3e964bab256` |
| `pt-br`                     | Container installatie kopie met de `pt-BR` land instelling. | `sha256:f500ef956bd28807f40df1f9f0520e437c5084f61a3be6d1379e746887d5b7c` |
| `pt-pt`                     | Container installatie kopie met de `pt-PT` land instelling. | `sha256:c841d2dbe5f40adf6039242c106985febb1a44212feb55d9769fe31134ec116` |
| `ro-ro`                     | Container installatie kopie met de `ro-RO` land instelling. | `sha256:93271c39c0a134e987a069c2a65289acff9869ae0d90fdcb39928c9ef0fd86b` |
| `ru-ru`                     | Container installatie kopie met de `ru-RU` land instelling. | `sha256:8d6b3c600e56cc96813b8c14b7916c5539a20ba561dc1c6d5bbef6285d6eef6` |
| `sk-sk`                     | Container installatie kopie met de `sk-SK` land instelling. | `sha256:6d604092cc6c964663a1c97d91c8f1c8cf4b46d07427d03f7041c0cc55eb521` |
| `sl-si`                     | Container installatie kopie met de `sl-SI` land instelling. | `sha256:f237ed58fedefcc749e74be1258cc70e5a690ee6c5a6b6388bd24075faa61da` |
| `sv-se`                     | Container installatie kopie met de `sv-SE` land instelling. | `sha256:da4233e6658b00eefdadb9d4acd889c6550a5e2a4a7af7a9f915c878abd4c9c` |
| `ta-in`                     | Container installatie kopie met de `ta-IN` land instelling. | `sha256:22b77606d25e9c2f52bf3cad6218782b4719f6a9dcfadc770468d266758a56c` |
| `te-in`                     | Container installatie kopie met de `te-IN` land instelling. | `sha256:7f4d11372862ca1d65fc9b868e2d775701b8e6eabd786c90c4e9ab82ba86e88` |
| `th-th`                     | Container installatie kopie met de `th-TH` land instelling. | `sha256:69033bcd7c0f59d31bafec6c2b7a9ff343928cdd58c16105415c291d555d37b` |
| `tr-tr`                     | Container installatie kopie met de `tr-TR` land instelling. | `sha256:4b7d339846a0d371dfe25aa2e626f131003c01329c9a1da468eb3703ef176ea` |
| `zh-cn`                     | Container installatie kopie met de `zh-CN` land instelling. | `sha256:a428459830fb766083212f71c5638a65ce30d8dd84f6c624ae22768e8a76976` |
| `zh-hk`                     | Container installatie kopie met de `zh-HK` land instelling. | `sha256:7a2903462b67336a6ce4c8e2faac42052f0a4392d1d5eb3839758cc8d0429f1` |
| `zh-tw`                     | Container installatie kopie met de `zh-TW` land instelling. | `sha256:30fd2b3660e047d24a46fbba14ba282f15bc0339ec93f49afd0d02ff4069146` |


# <a name="previous-version"></a>[Vorige versie](#tab/previous)

Release Opmerking voor `2.6.0-amd64-<locale>` :

**Functies**
* Bijgewerkt naar de nieuwste modellen en volledig gemigreerd naar .NET 3,1
* Ondersteuning voor phraselist v2
* Woordgroepen lijsten worden ondersteund in de volgende land instellingen:
    * en-au
    * en-ca
    * en-GB
    * en-in
    * nl-nl
    * zh-cn
* Ondersteuning voor nieuwe land instellingen `cs-CZ` 
    * Hoofdletter gebruik en interpunctie worden momenteel niet ondersteund.

**Dit**
* Hiermee wordt een probleem opgelost waarbij betrouwbaarheids scores altijd 1 zijn in de Diarization-modus
* Gemigreerd gebruik de TextAnalytics 3,0-API

Houd er rekening mee dat de grootte van deze container installatie kopie groter is geworden vanwege de opgenomen woordgroepen lijsten. 

Release Opmerking voor `2.5.0-amd64-<locale>` :

**Functies**
* Ondersteuning voor Azure-Cloud voor de Amerikaanse overheid

**Dit**
* Hiermee wordt een probleem opgelost waarbij een niet-hoofd gebruiker wordt uitgevoerd in de Diarization-modus

| Afbeeldings Tags                  | Notities                                    |
|-----------------------------|:-----------------------------------------|
| `2.6.0-amd64-<locale>`      | Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `2.6.0-amd64-en-us`. |
| `2.5.0-amd64-<locale>`      | Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `2.5.0-amd64-en-us`. |


Voor deze container zijn de volgende land instellingen beschikbaar.

| Land instelling voor v 2.6.0           | Notities                                    |
|-----------------------------|:-----------------------------------------|
| `ar-ae`                     | Container installatie kopie met de `ar-AE` land instelling. |
| `ar-eg`                     | Container installatie kopie met de `ar-EG` land instelling. |
| `ar-kw`                     | Container installatie kopie met de `ar-KW` land instelling. |
| `ar-qa`                     | Container installatie kopie met de `ar-QA` land instelling. |
| `ar-sa`                     | Container installatie kopie met de `ar-SA` land instelling. |
| `ca-es`                     | Container installatie kopie met de `ca-ES` land instelling. |
| `cs-cz`                     | Container installatie kopie met de `cs-CZ` land instelling. |
| `da-dk`                     | Container installatie kopie met de `da-DK` land instelling. |
| `de-de`                     | Container installatie kopie met de `de-DE` land instelling. |
| `en-au`                     | Container installatie kopie met de `en-AU` land instelling. |
| `en-ca`                     | Container installatie kopie met de `en-CA` land instelling. |
| `en-gb`                     | Container installatie kopie met de `en-GB` land instelling. |
| `en-in`                     | Container installatie kopie met de `en-IN` land instelling. |
| `en-nz`                     | Container installatie kopie met de `en-NZ` land instelling. |
| `en-us`                     | Container installatie kopie met de `en-US` land instelling. |
| `es-es`                     | Container installatie kopie met de `es-ES` land instelling. |
| `es-mx`                     | Container installatie kopie met de `es-MX` land instelling. |
| `fi-fi`                     | Container installatie kopie met de `fi-FI` land instelling. |
| `fr-ca`                     | Container installatie kopie met de `fr-CA` land instelling. |
| `fr-fr`                     | Container installatie kopie met de `fr-FR` land instelling. |
| `gu-in`                     | Container installatie kopie met de `gu-IN` land instelling. |
| `hi-in`                     | Container installatie kopie met de `hi-IN` land instelling. |
| `it-it`                     | Container installatie kopie met de `it-IT` land instelling. |
| `ja-jp`                     | Container installatie kopie met de `ja-JP` land instelling. |
| `ko-kr`                     | Container installatie kopie met de `ko-KR` land instelling. |
| `mr-in`                     | Container installatie kopie met de `mr-IN` land instelling. |
| `nb-no`                     | Container installatie kopie met de `nb-NO` land instelling. |
| `nl-nl`                     | Container installatie kopie met de `nl-NL` land instelling. |
| `pl-pl`                     | Container installatie kopie met de `pl-PL` land instelling. |
| `pt-br`                     | Container installatie kopie met de `pt-BR` land instelling. |
| `pt-pt`                     | Container installatie kopie met de `pt-PT` land instelling. |
| `ru-ru`                     | Container installatie kopie met de `ru-RU` land instelling. |
| `sv-se`                     | Container installatie kopie met de `sv-SE` land instelling. |
| `ta-in`                     | Container installatie kopie met de `ta-IN` land instelling. |
| `te-in`                     | Container installatie kopie met de `te-IN` land instelling. |
| `th-th`                     | Container installatie kopie met de `th-TH` land instelling. |
| `tr-tr`                     | Container installatie kopie met de `tr-TR` land instelling. |
| `zh-cn`                     | Container installatie kopie met de `zh-CN` land instelling. |
| `zh-hk`                     | Container installatie kopie met de `zh-HK` land instelling. |
| `zh-tw`                     | Container installatie kopie met de `zh-TW` land instelling. |

| Land instelling voor v 2.5.0           | Notities                                    |
|-----------------------------|:-----------------------------------------|
| `ar-ae`                     | Container installatie kopie met de `ar-AE` land instelling. |
| `ar-eg`                     | Container installatie kopie met de `ar-EG` land instelling. |
| `ar-kw`                     | Container installatie kopie met de `ar-KW` land instelling. |
| `ar-qa`                     | Container installatie kopie met de `ar-QA` land instelling. |
| `ar-sa`                     | Container installatie kopie met de `ar-SA` land instelling. |
| `ca-es`                     | Container installatie kopie met de `ca-ES` land instelling. |
| `da-dk`                     | Container installatie kopie met de `da-DK` land instelling. |
| `de-de`                     | Container installatie kopie met de `de-DE` land instelling. |
| `en-au`                     | Container installatie kopie met de `en-AU` land instelling. |
| `en-ca`                     | Container installatie kopie met de `en-CA` land instelling. |
| `en-gb`                     | Container installatie kopie met de `en-GB` land instelling. |
| `en-in`                     | Container installatie kopie met de `en-IN` land instelling. |
| `en-nz`                     | Container installatie kopie met de `en-NZ` land instelling. |
| `en-us`                     | Container installatie kopie met de `en-US` land instelling. |
| `es-es`                     | Container installatie kopie met de `es-ES` land instelling. |
| `es-mx`                     | Container installatie kopie met de `es-MX` land instelling. |
| `fi-fi`                     | Container installatie kopie met de `fi-FI` land instelling. |
| `fr-ca`                     | Container installatie kopie met de `fr-CA` land instelling. |
| `fr-fr`                     | Container installatie kopie met de `fr-FR` land instelling. |
| `gu-in`                     | Container installatie kopie met de `gu-IN` land instelling. |
| `hi-in`                     | Container installatie kopie met de `hi-IN` land instelling. |
| `it-it`                     | Container installatie kopie met de `it-IT` land instelling. |
| `ja-jp`                     | Container installatie kopie met de `ja-JP` land instelling. |
| `ko-kr`                     | Container installatie kopie met de `ko-KR` land instelling. |
| `mr-in`                     | Container installatie kopie met de `mr-IN` land instelling. |
| `nb-no`                     | Container installatie kopie met de `nb-NO` land instelling. |
| `nl-nl`                     | Container installatie kopie met de `nl-NL` land instelling. |
| `pl-pl`                     | Container installatie kopie met de `pl-PL` land instelling. |
| `pt-br`                     | Container installatie kopie met de `pt-BR` land instelling. |
| `pt-pt`                     | Container installatie kopie met de `pt-PT` land instelling. |
| `ru-ru`                     | Container installatie kopie met de `ru-RU` land instelling. |
| `sv-se`                     | Container installatie kopie met de `sv-SE` land instelling. |
| `ta-in`                     | Container installatie kopie met de `ta-IN` land instelling. |
| `te-in`                     | Container installatie kopie met de `te-IN` land instelling. |
| `th-th`                     | Container installatie kopie met de `th-TH` land instelling. |
| `tr-tr`                     | Container installatie kopie met de `tr-TR` land instelling. |
| `zh-cn`                     | Container installatie kopie met de `zh-CN` land instelling. |
| `zh-hk`                     | Container installatie kopie met de `zh-HK` land instelling. |
| `zh-tw`                     | Container installatie kopie met de `zh-TW` land instelling. |

---

## <a name="text-to-speech"></a>Tekst naar spraak

De [tekst-naar-spraak][sp-tts] container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/speechservices/` opslag plaats en heet `text-to-speech` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/speechservices/text-to-speech` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/text-to-speech/tags/list).


# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

Release Opmerking voor `1.9.0-amd64-<locale-and-voice>` :

* Reguliere maandelijkse release

| Afbeeldings Tags                                  | Notities                                                                                                         |
|---------------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| `latest`                                    | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaRUS` stem.                                            | 
| `1.9.0-amd64-<locale-and-voice>`            | Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `1.9.0-amd64-en-us-ariarus`.  |


| Land instellingen voor v 1.9.0                          | Notities                                                                      | Samenvatting                         |
|---------------------------------------------|:---------------------------------------------------------------------------|:-------------------------------|
| `ar-eg-hoda`                                | Container installatie kopie met de `ar-EG` land instellingen en de `ar-EG-Hoda` stem.            | `sha256:2b19cfd2212d6517b286aa18617d2f9d1dd1520078b559cbbf9240599270d10` | 
| `ar-sa-naayf`                               | Container installatie kopie met de `ar-SA` land instellingen en de `ar-SA-Naayf` stem.           | `sha256:6063aae5fb15c62b234cf945220916516a06ca81354c5311dee02af4d8cb0d3` |
| `bg-bg-ivan`                                | Container installatie kopie met de `bg-BG` land instellingen en de `bg-BG-Ivan` stem.            | `sha256:c6786916464755e64ffa64e69e8f3e7ef16115bac00bb6ea1e45368c42c58d1` |
| `ca-es-herenarus`                           | Container installatie kopie met de `ca-ES` land instellingen en de `ca-ES-HerenaRUS` stem.       | `sha256:2a8a1accbf99e2746c9345b77e2f261e0111227312c402cc2e1cd8760cdc82a` |
| `cs-cz-jakub`                               | Container installatie kopie met de `cs-CZ` land instellingen en de `cs-CZ-Jakub` stem.           | `sha256:3e464356bb08c9c966af2b28a88ccafd591aecd2e37a0fedb356bd443720e8d` |
| `da-dk-hellerus`                            | Container installatie kopie met de `da-DK` land instellingen en de `da-DK-HelleRUS` stem.        | `sha256:b85c43080804103673ff99dddea644a516c4103e8b1f11fa3dd34857492cd40` |
| `de-at-michael`                             | Container installatie kopie met de `de-AT` land instellingen en de `de-AT-Michael` stem.         | `sha256:87b57ee61f964e4d72e75d860c499fa3b3d8dbda6a96c97d696beb20aa8b2a9` |
| `de-ch-karsten`                             | Container installatie kopie met de `de-CH` land instellingen en de `de-CH-Karsten` stem.         | `sha256:ab1385b9746f4f054204302b9d564a433ae03748021b8ed71b4a3a224af1e9b` |
| `de-de-heddarus`                            | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Hedda` stem.           | `sha256:82185a710c87f9dde678d88036867559ab3bf5f08f234d60d1548d3e106db57` |
| `de-de-hedda`                               | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Hedda` stem.           | `sha256:82185a710c87f9dde678d88036867559ab3bf5f08f234d60d1548d3e106db57` |
| `de-de-stefan-apollo`                       | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Stefan-Apollo` stem.   | `sha256:56a1c63e7e6a0f5623ddc1f6a44ac6e51471d073e02e14e8c8b1e577930d816` |
| `el-gr-stefanos`                            | Container installatie kopie met de `el-GR` land instellingen en de `el-GR-Stefanos` stem.        | `sha256:ccbbb09f29ff8f276e246037183c7a3e9a3eb5bf33a942b22205cce3c6857f2` |
| `en-au-catherine`                           | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-Catherine` stem.       | `sha256:0c7374890f963e1ae9507e89dc9965a94723bd57802826c0677cd5262189783` |
| `en-au-hayleyrus`                           | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-HayleyRUS` stem.       | `sha256:7430bf8eace8294ca085f36ea56399261b2b4f69027e86649e8f3868fc3d811` |
| `en-ca-heatherrus`                          | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-HeatherRUS` stem.      | `sha256:0166ce1de3d669ea4ad80738c63369b7032125a54ecabade07241d740a94cfe` |
| `en-ca-linda`                               | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-Linda` stem.           | `sha256:50bed6a7bde9b793d307bcc3ace4c0f28d4a33c7a4dad9b3a394dc39a3e1c28` |
| `en-gb-george-apollo`                       | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-George-Apollo` stem.   | `sha256:50b800c0018a39609ddb1cee1b10062bf38a907644c393d20786db7c3ade748` |
| `en-gb-hazelrus`                            | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-HazelRUS` stem.        | `sha256:2aa79394dfeac8cec0cc1704a5199949cfccf347fe61161d02c7000c4ffcfa6` |
| `en-gb-susan-apollo`                        | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-Susan-Apollo` stem.    | `sha256:7a3174b3aae5f10241e731d392b56f124808cdd506f881ced919ced73d836c0` |
| `en-ie-sean`                                | Container installatie kopie met de `en-IE` land instellingen en de `en-IE-Sean` stem.            | `sha256:2457202fadb2354fc8d3666432096bd87c07760a4e3f4dbcc49853fff658577` |
| `en-in-heera-apollo`                        | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-Heera-Apollo` stem.    | `sha256:e4068cd7ca4272ea94819e2ba8743d2a76c8710b162db5e9ecbde6c92c12877` |
| `en-in-priyarus`                            | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-PriyaRUS` stem.        | `sha256:9d63a0ed53ac06178ab84588551421c0e1d04b8bad3321410ebb99c3ca2a9e8` |
| `en-in-ravi-apollo`                         | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-Ravi-Apollo` stem.     | `sha256:67049c9ce591336655943f5030afcfdaa150a8aace7b372425a69cc33a6b7b9` |
| `en-us-aria24krus`                          | Container installatie kopie met de `en-US` land instellingen en de `en-US-Aria24kRUS` stem.      | `sha256:a95acf6874bf3df7ae8e96be779f80cb5405d21250227b0c4b3ddbcb3014082` |
| `en-us-ariarus`                             | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaRUS` stem.         | `sha256:a95acf6874bf3df7ae8e96be779f80cb5405d21250227b0c4b3ddbcb3014082` |
| `en-us-benjaminrus`                         | Container installatie kopie met de `en-US` land instellingen en de `en-US-BenjaminRUS` stem.     | `sha256:93cd49adaaa2a1bdfb06ab655be164ae66f206cb7c03a2cbd59e5fba70610ab` |
| `en-us-guy24krus`                           | Container installatie kopie met de `en-US` land instellingen en de `en-US-Guy24kRUS` stem.       | `sha256:7b788bfcaae4c63c274ca15924bfd861cfcafd5fec13f685d80babc25b2949d` |
| `en-us-zirarus`                             | Container installatie kopie met de `en-US` land instellingen en de `en-US-ZiraRUS` stem.         | `sha256:bfc87a77df5695ad43481348500fba8f6a7b495708fba200706049469b5ba97` |
| `es-es-helenarus`                           | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-HelenaRUS` stem.       | `sha256:0b6c17aca75efb64aa9bfc0d83303038fe58d4b2fb1fc94c9380a4335b80796` |
| `es-es-laura-apollo`                        | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-Laura-Apollo` stem.    | `sha256:d6fcffc944c37a2dd0de29c39b82f3f8cce3a95ad925d2814ed7538335d5d4f` |
| `es-es-pablo-apollo`                        | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-Pablo-Apollo` stem.    | `sha256:a460bc53d9083d3c3770129995cf96cc1069ae4e8101f1739d304fe210f0af0` |
| `es-mx-hildarus`                            | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-HildaRUS` stem.        | `sha256:5b7578fc5b00158dfa674d95a3f1d57f22eb285e8333b4006d1fe1808bda7ba` |
| `es-mx-raul-apollo`                         | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-Raul-Apollo` stem.     | `sha256:03922fb017783c86d788c72e01c7ede440f8f3c913c86cab19bad4dfc2e4a2b` |
| `fi-fi-heidirus`                            | Container installatie kopie met de `fi-FI` land instellingen en de `fi-FI-HeidiRUS` stem.        | `sha256:146c1f98d6fa061016eba41db6e7b654eef222d37f35406d4b43477bb2ff897` |
| `fr-ca-caroline`                            | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-Caroline` stem.        | `sha256:1ee2e53f12ad1c72665d2aef64e9d4a7f9ea05670cad84dcae5e75409494f32` |
| `fr-ca-harmonierus`                         | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-HarmonieRUS` stem.     | `sha256:a21d25d3ac699af4e9ba9194aadd9b45f35fd9205224f3429a4c7da41fc38fe` |
| `fr-ch-guillaume`                           | Container installatie kopie met de `fr-CH` land instellingen en de `fr-CH-Guillaume` stem.       | `sha256:216125a9bd89a95d3c4dc2d7e031398659427b3aa7d4663d23a65737972e42b` |
| `fr-fr-hortenserus`                         | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-HortenseRUS` stem.     | `sha256:795a698120eecbd80c48e738f73300739c1698ca859130ddb4236317bcdf70f` |
| `fr-fr-julie-apollo`                        | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-Julie-Apollo` stem.    | `sha256:f6eb70d523c435c2e3a713b32a8af4a781df7ec043caad2fc7f458ee341eb2f` |
| `fr-fr-paul-apollo`                         | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-Paul-Apollo` stem.     | `sha256:28864c662a20f459b3051b1da2967a605e06267e6408285f7c2552748cf4eed` |
| `he-il-asaf`                                | Container installatie kopie met de `he-IL` land instellingen en de `he-IL-Asaf` stem.            | `sha256:eaa834bac6b69abef096b36a8baead741db78fe438af3d30f60abde3631d639` |
| `hi-in-hemant`                              | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Hemant` stem.          | `sha256:cfea0fa7cce9cc512f2fbb8b76f1c00fe5c32fad853c90b15934cf4ee6262fa` |
| `hi-in-kalpana-apollo`                      | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Kalpana-Apollo` stem.  | `sha256:afbd6cc0413f3a3c9f6df044b6df6d9dac9e8e888c2cb619fefbdc3e105c644` |
| `hi-in-kalpana`                             | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Kalpana` stem.         | `sha256:afbd6cc0413f3a3c9f6df044b6df6d9dac9e8e888c2cb619fefbdc3e105c644` |
| `hr-hr-matej`                               | Container installatie kopie met de `hr-HR` land instellingen en de `hr-HR-Matej` stem.           | `sha256:86683597c62752b4d769b69e5294979fafd4c277aaef1536e1cb19f9f06c0bf` |
| `hu-hu-szabolcs`                            | Container installatie kopie met de `hu-HU` land instellingen en de `hu-HU-Szabolcs` stem.        | `sha256:aa64eed28ca2ad060e2e02188e0401bf34e4caf7e2182b70a30ce33b3c11c9c` |
| `id-id-andika`                              | Container installatie kopie met de `id-ID` land instellingen en de `id-ID-Andika` stem.          | `sha256:0e1394d231a57a1df8163ccb634dc2ef2f8103b10608a40ab3efc5c0fbe9ded` |
| `it-it-cosimo-apollo`                       | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-Cosimo-Apollo` stem.   | `sha256:eef97f2817fc24405823a5fe4e825244db32279b44c0e6631e8ad9a5c1acf40` |
| `it-it-luciarus`                            | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-LuciaRUS` stem.        | `sha256:ebc331b0685f482d2f55619fa81fd451fd7c8f107f9cd7ad159bc6213ae4e33` |
| `ja-jp-ayumi-apollo`                        | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-Ayumi-Apollo` stem.    | `sha256:e9cb7dfd2eec154c8f3d530c16b66e8558c5955a2edaede69740067f00e43cf` |
| `ja-jp-harukarus`                           | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-HarukaRUS` stem.       | `sha256:93ce2ef6177c0d8ac70b61df8b11fcbcdfd3c0be0cc51cd8644f26679a741c2` |
| `ja-jp-ichiro-apollo`                       | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-Ichiro-Apollo` stem.   | `sha256:6a18bae69ac63b42ba992b8b74d8d31d91ca984d61b5f62f38be988cf38645e` |
| `ko-kr-heamirus`                            | Container installatie kopie met de `ko-KR` land instellingen en de `ko-KR-HeamiRUS` stem.        | `sha256:7a48252d4ada2af43f9266a70113426d330bac192348cbdc929022295a0e727` |
| `ms-my-rizwan`                              | Container installatie kopie met de `ms-MY` land instellingen en de `ms-MY-Rizwan` stem.          | `sha256:90e2ecac14f8e960934fd013d208fc2a0afe1bfff037d5648d422bda8d8a76e` |
| `nb-no-huldarus`                            | Container installatie kopie met de `nb-NO` land instellingen en de `nb-NO-HuldaRUS` stem.        | `sha256:217b61bd6244b5effda8f12a2c563ce1b4572e9c5b8a08df143665f9ff754e4` |
| `nl-nl-hannarus`                            | Container installatie kopie met de `nl-NL` land instellingen en de `nl-NL-HannaRUS` stem.        | `sha256:fbff48dfc9dfadadf377867b28f6e3a3bd605e59da20f77a531efcc7d85d16e` |
| `pl-pl-paulinarus`                          | Container installatie kopie met de `pl-PL` land instellingen en de `pl-PL-PaulinaRUS` stem.      | `sha256:856a033a09925773fa4b4531e199ab7c03c537f366acecbda60f8d21735725e` |
| `pt-br-daniel-apollo`                       | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-Daniel-Apollo` stem.   | `sha256:2d1ec975f1aee56a6fc6039d154fb3f2fbeb4636f7078c5dfe99aeddb6a3634` |
| `pt-br-heloisarus`                          | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-HeloisaRUS` stem.      | `sha256:b7d629f37ab3305274764264dc08fab5236e60ef18d40e987618115db67ce44` |
| `pt-pt-heliarus`                            | Container installatie kopie met de `pt-PT` land instellingen en de `pt-PT-HeliaRUS` stem.        | `sha256:8b380ae7e4aac9d4ada4d15fa9e667387bc9ca038796d9b6999953bfbc97259` |
| `ro-ro-andrei`                              | Container installatie kopie met de `ro-RO` land instellingen en de `ro-RO-Andrei` stem.          | `sha256:b00ca7f1411169a5baf7263a8d7e5eed1a72084d9489eaf458429dfc338564a` |
| `ru-ru-ekaterinarus`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-EkaterinaRUS` stem.    | `sha256:31c588c31e3ac67305af66091e7756dfc4ca454317d0228116ea0b2fedf5d71` |
| `ru-ru-irina-apollo`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-Irina-Apollo` stem.    | `sha256:e76437f8da7c279b38d2643defc997a13b4a364e9a212895cdb33a9a3f6457f` |
| `ru-ru-pavel-apollo`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-Pavel-Apollo` stem.    | `sha256:461c1efa6cce0b10a87f338bc637aca76aef8458061a688870fb3343d682da0` |
| `sk-sk-filip`                               | Container installatie kopie met de `sk-SK` land instellingen en de `sk-SK-Filip` stem.           | `sha256:7fb0cfab4c0fe2913eb20f28a25c6663015d62f82e7e7864d9f7fac2d27697b` |
| `sl-si-lado`                                | Container installatie kopie met de `sl-SI` land instellingen en de `sl-SI-Lado` stem.            | `sha256:5336173d410e10ffeb5dc211a583887e33754319c757914955057d398dfbb0a` |
| `sv-se-hedvigrus`                           | Container installatie kopie met de `sv-SE` land instellingen en de `sv-SE-HedvigRUS` stem.       | `sha256:5dc8cdcc3054386bf69596707d9d261d4db5bfd09f1882ceb4e29238a34b24e` |
| `ta-in-valluvar`                            | Container installatie kopie met de `ta-IN` land instellingen en de `ta-IN-Valluvar` stem.        | `sha256:74ea485f23e4c1fe0029e06894860aa0188c36c0e14ea3584a06d4216ccef56` |
| `te-in-chitra`                              | Container installatie kopie met de `te-IN` land instellingen en de `te-IN-Chitra` stem.          | `sha256:ff2977a98ef691da543db08be9cfe04d7fc3bf8f78b29310c163e47303b2ddd` |
| `th-th-pattara`                             | Container installatie kopie met de `th-TH` land instellingen en de `th-TH-Pattara` stem.         | `sha256:ba7e2c0e5e75d9f2b52aa50c97728616c43e81f48c15e24665e4c2ea5770a8f` |
| `tr-tr-sedarus`                             | Container installatie kopie met de `tr-TR` land instellingen en de `tr-TR-SedaRUS` stem.         | `sha256:375a8ceae89ea1f0dda551feff30ae3679231189b527992edbc49988d042d66` |
| `vi-vn-an`                                  | Container installatie kopie met de `vi-VN` land instellingen en de `vi-VN-An` stem.              | `sha256:b6f82148295b38b4039c45c48695ec50b4e97cd02b18d49c39bf9fca3bec958` |
| `zh-cn-huihuirus`                           | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-HuihuiRUS` stem.       | `sha256:3e773931f3adaac92cba43773a241692a2b471ebe73ec51c475df8ff63b7ee1` |
| `zh-cn-kangkang-apollo`                     | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-Kangkang-Apollo` stem. | `sha256:05fc0d5075a1094caf70d98b4a9469952be52cb6eb4d9f7b9ff4ae961100c7b` |
| `zh-cn-yaoyao-apollo`                       | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-Yaoyao-Apollo` stem.   | `sha256:d7613bcefc48e85b9d6f07c8cd223c16d4958bcf7f24087575250e97c593ac1` |
| `zh-hk-danny-apollo`                        | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-Danny-Apollo` stem.    | `sha256:efe22bc123dac9312dcaeb859a377d81f61fbb25ef46e4678d36ec6bebc5d32` |
| `zh-hk-tracy-apollo`                        | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-Tracy-Apollo` stem.    | `sha256:802c60bc65012c03ffe96268dca79b8c6dcd0c5cc6180ec271c50ef5c9ba132` |
| `zh-hk-tracyrus`                            | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-TracyRUS` stem.        | `sha256:802c60bc65012c03ffe96268dca79b8c6dcd0c5cc6180ec271c50ef5c9ba132` |
| `zh-tw-hanhanrus`                           | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-HanHanRUS` stem.       | `sha256:95d58922463d577d4c4722ab722a5768af35fb62236d47f6709717dea758909` |
| `zh-tw-yating-apollo`                       | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-Yating-Apollo` stem.   | `sha256:33eec6e3aaaedafaf3969746eeaf97a1760e763505decfe2abaa03f5054bfd2` |
| `zh-tw-zhiwei-apollo`                       | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-Zhiwei-Apollo` stem.   | `sha256:456db2898b2e5a9c30b7071ce6ea3f141438cbf1aa4899c7ffccfc2f0dde5bd` |


# <a name="previous-version"></a>[Vorige versie](#tab/previous)

Release Opmerking voor `1.8.0-amd64-<locale-and-voice>` :

**Functie**

* Volledig gemigreerd naar .NET 3,1

Release Opmerking voor `1.7.0-amd64-<locale-and-voice>` :

**Functie**

* Bijgewerkte onderdelen naar .NET 3,1

| Afbeeldings Tags                                  | Notities                                                                                                         |
|---------------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| `1.8.0-amd64-<locale-and-voice>`            | Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `1.8.0-amd64-en-us-ariarus`.  |
| `1.7.0-amd64-<locale-and-voice>`            | 1e GA-versie. Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `1.7.0-amd64-en-us-ariarus`.  |


| Land instellingen voor v 1.8.0                          | Notities                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `ar-eg-hoda`                                | Container installatie kopie met de `ar-EG` land instellingen en de `ar-EG-Hoda` stem.            |
| `ar-sa-naayf`                               | Container installatie kopie met de `ar-SA` land instellingen en de `ar-SA-Naayf` stem.           |
| `bg-bg-ivan`                                | Container installatie kopie met de `bg-BG` land instellingen en de `bg-BG-Ivan` stem.            |
| `ca-es-herenarus`                           | Container installatie kopie met de `ca-ES` land instellingen en de `ca-ES-HerenaRUS` stem.       |
| `cs-cz-jakub`                               | Container installatie kopie met de `cs-CZ` land instellingen en de `cs-CZ-Jakub` stem.           |
| `da-dk-hellerus`                            | Container installatie kopie met de `da-DK` land instellingen en de `da-DK-HelleRUS` stem.        |
| `de-at-michael`                             | Container installatie kopie met de `de-AT` land instellingen en de `de-AT-Michael` stem.         |
| `de-ch-karsten`                             | Container installatie kopie met de `de-CH` land instellingen en de `de-CH-Karsten` stem.         |
| `de-de-hedda`                               | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Hedda` stem.           |
| `de-de-heddarus`                            | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Hedda` stem.           |
| `de-de-stefan-apollo`                       | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Stefan-Apollo` stem.   |
| `el-gr-stefanos`                            | Container installatie kopie met de `el-GR` land instellingen en de `el-GR-Stefanos` stem.        |
| `en-au-catherine`                           | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-Catherine` stem.       |
| `en-au-hayleyrus`                           | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-HayleyRUS` stem.       |
| `en-ca-heatherrus`                          | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-HeatherRUS` stem.      |
| `en-ca-linda`                               | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-Linda` stem.           |
| `en-gb-george-apollo`                       | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-George-Apollo` stem.   |
| `en-gb-hazelrus`                            | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-HazelRUS` stem.        |
| `en-gb-susan-apollo`                        | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-Susan-Apollo` stem.    |
| `en-ie-sean`                                | Container installatie kopie met de `en-IE` land instellingen en de `en-IE-Sean` stem.            |
| `en-in-heera-apollo`                        | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-Heera-Apollo` stem.    |
| `en-in-priyarus`                            | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-PriyaRUS` stem.        |
| `en-in-ravi-apollo`                         | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-Ravi-Apollo` stem.     |
| `en-us-benjaminrus`                         | Container installatie kopie met de `en-US` land instellingen en de `en-US-BenjaminRUS` stem.     |
| `en-us-guy24krus`                           | Container installatie kopie met de `en-US` land instellingen en de `en-US-Guy24kRUS` stem.       |
| `en-us-aria24krus`                          | Container installatie kopie met de `en-US` land instellingen en de `en-US-Aria24kRUS` stem.      |
| `en-us-ariarus`                             | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaRUS` stem.         |
| `en-us-zirarus`                             | Container installatie kopie met de `en-US` land instellingen en de `en-US-ZiraRUS` stem.         |
| `es-es-helenarus`                           | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-HelenaRUS` stem.       |
| `es-es-laura-apollo`                        | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-Laura-Apollo` stem.    |
| `es-es-pablo-apollo`                        | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-Pablo-Apollo` stem.    |
| `es-mx-hildarus`                            | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-HildaRUS` stem.        |
| `es-mx-raul-apollo`                         | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-Raul-Apollo` stem.     |
| `fi-fi-heidirus`                            | Container installatie kopie met de `fi-FI` land instellingen en de `fi-FI-HeidiRUS` stem.        |
| `fr-ca-caroline`                            | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-Caroline` stem.        |
| `fr-ca-harmonierus`                         | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-HarmonieRUS` stem.     |
| `fr-ch-guillaume`                           | Container installatie kopie met de `fr-CH` land instellingen en de `fr-CH-Guillaume` stem.       |
| `fr-fr-hortenserus`                         | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-HortenseRUS` stem.     |
| `fr-fr-julie-apollo`                        | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-Julie-Apollo` stem.    |
| `fr-fr-paul-apollo`                         | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-Paul-Apollo` stem.     |
| `he-il-asaf`                                | Container installatie kopie met de `he-IL` land instellingen en de `he-IL-Asaf` stem.            |
| `hi-in-hemant`                              | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Hemant` stem.          |
| `hi-in-kalpana-apollo`                      | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Kalpana-Apollo` stem.  |
| `hi-in-kalpana`                             | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Kalpana` stem.         |
| `hr-hr-matej`                               | Container installatie kopie met de `hr-HR` land instellingen en de `hr-HR-Matej` stem.           |
| `hu-hu-szabolcs`                            | Container installatie kopie met de `hu-HU` land instellingen en de `hu-HU-Szabolcs` stem.        |
| `id-id-andika`                              | Container installatie kopie met de `id-ID` land instellingen en de `id-ID-Andika` stem.          |
| `it-it-cosimo-apollo`                       | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-Cosimo-Apollo` stem.   |
| `it-it-luciarus`                            | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-LuciaRUS` stem.        |
| `ja-jp-ayumi-apollo`                        | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-Ayumi-Apollo` stem.    |
| `ja-jp-harukarus`                           | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-HarukaRUS` stem.       |
| `ja-jp-ichiro-apollo`                       | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-Ichiro-Apollo` stem.   |
| `ko-kr-heamirus`                            | Container installatie kopie met de `ko-KR` land instellingen en de `ko-KR-HeamiRUS` stem.        |
| `ms-my-rizwan`                              | Container installatie kopie met de `ms-MY` land instellingen en de `ms-MY-Rizwan` stem.          |
| `nb-no-huldarus`                            | Container installatie kopie met de `nb-NO` land instellingen en de `nb-NO-HuldaRUS` stem.        |
| `nl-nl-hannarus`                            | Container installatie kopie met de `nl-NL` land instellingen en de `nl-NL-HannaRUS` stem.        |
| `pl-pl-paulinarus`                          | Container installatie kopie met de `pl-PL` land instellingen en de `pl-PL-PaulinaRUS` stem.      |
| `pt-br-daniel-apollo`                       | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-Daniel-Apollo` stem.   |
| `pt-br-heloisarus`                          | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-HeloisaRUS` stem.      |
| `pt-pt-heliarus`                            | Container installatie kopie met de `pt-PT` land instellingen en de `pt-PT-HeliaRUS` stem.        |
| `ro-ro-andrei`                              | Container installatie kopie met de `ro-RO` land instellingen en de `ro-RO-Andrei` stem.          |
| `ru-ru-ekaterinarus`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-EkaterinaRUS` stem.    |
| `ru-ru-irina-apollo`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-Irina-Apollo` stem.    |
| `ru-ru-pavel-apollo`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-Pavel-Apollo` stem.    |
| `sk-sk-filip`                               | Container installatie kopie met de `sk-SK` land instellingen en de `sk-SK-Filip` stem.           |
| `sl-si-lado`                                | Container installatie kopie met de `sl-SI` land instellingen en de `sl-SI-Lado` stem.            |
| `sv-se-hedvigrus`                           | Container installatie kopie met de `sv-SE` land instellingen en de `sv-SE-HedvigRUS` stem.       |
| `ta-in-valluvar`                            | Container installatie kopie met de `ta-IN` land instellingen en de `ta-IN-Valluvar` stem.        |
| `te-in-chitra`                              | Container installatie kopie met de `te-IN` land instellingen en de `te-IN-Chitra` stem.          |
| `th-th-pattara`                             | Container installatie kopie met de `th-TH` land instellingen en de `th-TH-Pattara` stem.         |
| `tr-tr-sedarus`                             | Container installatie kopie met de `tr-TR` land instellingen en de `tr-TR-SedaRUS` stem.         |
| `vi-vn-an`                                  | Container installatie kopie met de `vi-VN` land instellingen en de `vi-VN-An` stem.              |
| `zh-cn-huihuirus`                           | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-HuihuiRUS` stem.       |
| `zh-cn-kangkang-apollo`                     | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-Kangkang-Apollo` stem. |
| `zh-cn-yaoyao-apollo`                       | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-Yaoyao-Apollo` stem.   |
| `zh-hk-danny-apollo`                        | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-Danny-Apollo` stem.    |
| `zh-hk-tracy-apollo`                        | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-Tracy-Apollo` stem.    |
| `zh-hk-tracyrus`                            | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-TracyRUS` stem.        |
| `zh-tw-hanhanrus`                           | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-HanHanRUS` stem.       |
| `zh-tw-yating-apollo`                       | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-Yating-Apollo` stem.   |
| `zh-tw-zhiwei-apollo`                       | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-Zhiwei-Apollo` stem.   |

| Land instellingen voor v 1.7.0                          | Notities                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `ar-eg-hoda`                                | Container installatie kopie met de `ar-EG` land instellingen en de `ar-EG-Hoda` stem.            |
| `ar-sa-naayf`                               | Container installatie kopie met de `ar-SA` land instellingen en de `ar-SA-Naayf` stem.           |
| `bg-bg-ivan`                                | Container installatie kopie met de `bg-BG` land instellingen en de `bg-BG-Ivan` stem.            |
| `ca-es-herenarus`                           | Container installatie kopie met de `ca-ES` land instellingen en de `ca-ES-HerenaRUS` stem.       |
| `cs-cz-jakub`                               | Container installatie kopie met de `cs-CZ` land instellingen en de `cs-CZ-Jakub` stem.           |
| `da-dk-hellerus`                            | Container installatie kopie met de `da-DK` land instellingen en de `da-DK-HelleRUS` stem.        |
| `de-at-michael`                             | Container installatie kopie met de `de-AT` land instellingen en de `de-AT-Michael` stem.         |
| `de-ch-karsten`                             | Container installatie kopie met de `de-CH` land instellingen en de `de-CH-Karsten` stem.         |
| `de-de-hedda`                               | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Hedda` stem.           |
| `de-de-heddarus`                            | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Hedda` stem.           |
| `de-de-stefan-apollo`                       | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-Stefan-Apollo` stem.   |
| `el-gr-stefanos`                            | Container installatie kopie met de `el-GR` land instellingen en de `el-GR-Stefanos` stem.        |
| `en-au-catherine`                           | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-Catherine` stem.       |
| `en-au-hayleyrus`                           | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-HayleyRUS` stem.       |
| `en-ca-heatherrus`                          | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-HeatherRUS` stem.      |
| `en-ca-linda`                               | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-Linda` stem.           |
| `en-gb-george-apollo`                       | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-George-Apollo` stem.   |
| `en-gb-hazelrus`                            | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-HazelRUS` stem.        |
| `en-gb-susan-apollo`                        | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-Susan-Apollo` stem.    |
| `en-ie-sean`                                | Container installatie kopie met de `en-IE` land instellingen en de `en-IE-Sean` stem.            |
| `en-in-heera-apollo`                        | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-Heera-Apollo` stem.    |
| `en-in-priyarus`                            | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-PriyaRUS` stem.        |
| `en-in-ravi-apollo`                         | Container installatie kopie met de `en-IN` land instellingen en de `en-IN-Ravi-Apollo` stem.     |
| `en-us-benjaminrus`                         | Container installatie kopie met de `en-US` land instellingen en de `en-US-BenjaminRUS` stem.     |
| `en-us-guy24krus`                           | Container installatie kopie met de `en-US` land instellingen en de `en-US-Guy24kRUS` stem.       |
| `en-us-aria24krus`                          | Container installatie kopie met de `en-US` land instellingen en de `en-US-Aria24kRUS` stem.      |
| `en-us-ariarus`                             | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaRUS` stem.         |
| `en-us-zirarus`                             | Container installatie kopie met de `en-US` land instellingen en de `en-US-ZiraRUS` stem.         |
| `es-es-helenarus`                           | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-HelenaRUS` stem.       |
| `es-es-laura-apollo`                        | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-Laura-Apollo` stem.    |
| `es-es-pablo-apollo`                        | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-Pablo-Apollo` stem.    |
| `es-mx-hildarus`                            | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-HildaRUS` stem.        |
| `es-mx-raul-apollo`                         | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-Raul-Apollo` stem.     |
| `fi-fi-heidirus`                            | Container installatie kopie met de `fi-FI` land instellingen en de `fi-FI-HeidiRUS` stem.        |
| `fr-ca-caroline`                            | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-Caroline` stem.        |
| `fr-ca-harmonierus`                         | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-HarmonieRUS` stem.     |
| `fr-ch-guillaume`                           | Container installatie kopie met de `fr-CH` land instellingen en de `fr-CH-Guillaume` stem.       |
| `fr-fr-hortenserus`                         | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-HortenseRUS` stem.     |
| `fr-fr-julie-apollo`                        | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-Julie-Apollo` stem.    |
| `fr-fr-paul-apollo`                         | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-Paul-Apollo` stem.     |
| `he-il-asaf`                                | Container installatie kopie met de `he-IL` land instellingen en de `he-IL-Asaf` stem.            |
| `hi-in-hemant`                              | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Hemant` stem.          |
| `hi-in-kalpana-apollo`                      | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Kalpana-Apollo` stem.  |
| `hi-in-kalpana`                             | Container installatie kopie met de `hi-IN` land instellingen en de `hi-IN-Kalpana` stem.         |
| `hr-hr-matej`                               | Container installatie kopie met de `hr-HR` land instellingen en de `hr-HR-Matej` stem.           |
| `hu-hu-szabolcs`                            | Container installatie kopie met de `hu-HU` land instellingen en de `hu-HU-Szabolcs` stem.        |
| `id-id-andika`                              | Container installatie kopie met de `id-ID` land instellingen en de `id-ID-Andika` stem.          |
| `it-it-cosimo-apollo`                       | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-Cosimo-Apollo` stem.   |
| `it-it-luciarus`                            | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-LuciaRUS` stem.        |
| `ja-jp-ayumi-apollo`                        | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-Ayumi-Apollo` stem.    |
| `ja-jp-harukarus`                           | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-HarukaRUS` stem.       |
| `ja-jp-ichiro-apollo`                       | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-Ichiro-Apollo` stem.   |
| `ko-kr-heamirus`                            | Container installatie kopie met de `ko-KR` land instellingen en de `ko-KR-HeamiRUS` stem.        |
| `ms-my-rizwan`                              | Container installatie kopie met de `ms-MY` land instellingen en de `ms-MY-Rizwan` stem.          |
| `nb-no-huldarus`                            | Container installatie kopie met de `nb-NO` land instellingen en de `nb-NO-HuldaRUS` stem.        |
| `nl-nl-hannarus`                            | Container installatie kopie met de `nl-NL` land instellingen en de `nl-NL-HannaRUS` stem.        |
| `pl-pl-paulinarus`                          | Container installatie kopie met de `pl-PL` land instellingen en de `pl-PL-PaulinaRUS` stem.      |
| `pt-br-daniel-apollo`                       | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-Daniel-Apollo` stem.   |
| `pt-br-heloisarus`                          | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-HeloisaRUS` stem.      |
| `pt-pt-heliarus`                            | Container installatie kopie met de `pt-PT` land instellingen en de `pt-PT-HeliaRUS` stem.        |
| `ro-ro-andrei`                              | Container installatie kopie met de `ro-RO` land instellingen en de `ro-RO-Andrei` stem.          |
| `ru-ru-ekaterinarus`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-EkaterinaRUS` stem.    |
| `ru-ru-irina-apollo`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-Irina-Apollo` stem.    |
| `ru-ru-pavel-apollo`                        | Container installatie kopie met de `ru-RU` land instellingen en de `ru-RU-Pavel-Apollo` stem.    |
| `sk-sk-filip`                               | Container installatie kopie met de `sk-SK` land instellingen en de `sk-SK-Filip` stem.           |
| `sl-si-lado`                                | Container installatie kopie met de `sl-SI` land instellingen en de `sl-SI-Lado` stem.            |
| `sv-se-hedvigrus`                           | Container installatie kopie met de `sv-SE` land instellingen en de `sv-SE-HedvigRUS` stem.       |
| `ta-in-valluvar`                            | Container installatie kopie met de `ta-IN` land instellingen en de `ta-IN-Valluvar` stem.        |
| `te-in-chitra`                              | Container installatie kopie met de `te-IN` land instellingen en de `te-IN-Chitra` stem.          |
| `th-th-pattara`                             | Container installatie kopie met de `th-TH` land instellingen en de `th-TH-Pattara` stem.         |
| `tr-tr-sedarus`                             | Container installatie kopie met de `tr-TR` land instellingen en de `tr-TR-SedaRUS` stem.         |
| `vi-vn-an`                                  | Container installatie kopie met de `vi-VN` land instellingen en de `vi-VN-An` stem.              |
| `zh-cn-huihuirus`                           | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-HuihuiRUS` stem.       |
| `zh-cn-kangkang-apollo`                     | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-Kangkang-Apollo` stem. |
| `zh-cn-yaoyao-apollo`                       | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-Yaoyao-Apollo` stem.   |
| `zh-hk-danny-apollo`                        | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-Danny-Apollo` stem.    |
| `zh-hk-tracy-apollo`                        | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-Tracy-Apollo` stem.    |
| `zh-hk-tracyrus`                            | Container installatie kopie met de `zh-HK` land instellingen en de `zh-HK-TracyRUS` stem.        |
| `zh-tw-hanhanrus`                           | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-HanHanRUS` stem.       |
| `zh-tw-yating-apollo`                       | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-Yating-Apollo` stem.   |
| `zh-tw-zhiwei-apollo`                       | Container installatie kopie met de `zh-TW` land instellingen en de `zh-TW-Zhiwei-Apollo` stem.   |

---

## <a name="neural-text-to-speech"></a>Tekst-naar-spraak Neural

De [Neural tekst naar spraak][sp-ntts] container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/speechservices/` opslag plaats en heet `neural-text-to-speech` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/speechservices/neural-text-to-speech` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/neural-text-to-speech/tags/list).


# <a name="latest-version"></a>[Nieuwste versie](#tab/current)

Release opmerkingen voor `v1.3.0` :
* De Neural tekst-naar-spraak-container is nu algemeen beschikbaar. 

| Afbeeldings Tags                                  | Notities                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `latest`                                    | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaNeural` stem.      |
| `1.3.0-amd64-<locale-and-voice>`    | Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `1.3.0-amd64-en-us-arianeural`. |


| v 1.3.0 land instellingen en stemmen           | Notities                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `de-de-katjaneural`                 | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-KatjaNeural` stem.     |
| `en-au-natashaneural`               | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-NatashaNeural` stem.   |
| `en-ca-claraneural`                 | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-ClaraNeural` stem.     |
| `en-gb-libbyneural`                 | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-LibbyNeural` stem.     |
| `en-gb-mianeural`                   | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-MiaNeural` stem.       |
| `en-us-arianeural`                  | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaNeural` stem.      |
| `en-us-guyneural`                   | Container installatie kopie met de `en-US` land instellingen en de `en-US-GuyNeural` stem.       |
| `es-es-elviraneural`                | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-ElviraNeural` stem.    |
| `es-mx-dalianeural`                 | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-DaliaNeural` stem.     |
| `fr-ca-sylvieneural`                | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-SylvieNeural` stem.    |
| `fr-fr-deniseneural`                | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-DeniseNeural` stem.    |
| `it-it-elsaneural`                  | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-ElsaNeural` stem.      |
| `ja-jp-nanamineural`                | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-NanamiNeural` stem.    |
| `ko-kr-sunhineural`                 | Container installatie kopie met de `ko-KR` land instellingen en de `ko-KR-SunHiNeural` stem.     |
| `pt-br-franciscaneural`             | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-FranciscaNeural` stem. |
| `zh-cn-xiaoxiaoneural`              | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-XiaoxiaoNeural` stem.  |

# <a name="previous-version"></a>[Vorige versie](#tab/previous)

| Afbeeldings Tags                                  | Notities                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `latest`                                    | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaNeural` stem.      |
| `1.2.0-amd64-<locale-and-voice>-preview`    | Vervang door `<locale>` een van de beschik bare land instellingen, zoals hieronder wordt weer gegeven. Bijvoorbeeld `1.2.0-amd64-en-us-arianeural-preview`. |


| v 1.2.0-voor beeld-land instellingen en stemmen           | Notities                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `latest`                                    | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaNeural` stem.      |
| `de-de-katjaneural-preview`                 | Container installatie kopie met de `de-DE` land instellingen en de `de-DE-KatjaNeural` stem.     |
| `en-au-natashaneural-preview`               | Container installatie kopie met de `en-AU` land instellingen en de `en-AU-NatashaNeural` stem.   |
| `en-ca-claraneural-preview`                 | Container installatie kopie met de `en-CA` land instellingen en de `en-CA-ClaraNeural` stem.     |
| `en-gb-libbyneural-preview`                 | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-LibbyNeural` stem.     |
| `en-gb-mianeural-preview`                   | Container installatie kopie met de `en-GB` land instellingen en de `en-GB-MiaNeural` stem.       |
| `en-us-arianeural-preview`                  | Container installatie kopie met de `en-US` land instellingen en de `en-US-AriaNeural` stem.      |
| `en-us-guyneural-preview`                   | Container installatie kopie met de `en-US` land instellingen en de `en-US-GuyNeural` stem.       |
| `es-es-elviraneural-preview`                | Container installatie kopie met de `es-ES` land instellingen en de `es-ES-ElviraNeural` stem.    |
| `es-mx-dalianeural-preview`                 | Container installatie kopie met de `es-MX` land instellingen en de `es-MX-DaliaNeural` stem.     |
| `fr-ca-sylvieneural-preview`                | Container installatie kopie met de `fr-CA` land instellingen en de `fr-CA-SylvieNeural` stem.    |
| `fr-fr-deniseneural-preview`                | Container installatie kopie met de `fr-FR` land instellingen en de `fr-FR-DeniseNeural` stem.    |
| `it-it-elsaneural-preview`                  | Container installatie kopie met de `it-IT` land instellingen en de `it-IT-ElsaNeural` stem.      |
| `ja-jp-nanamineural-preview`                | Container installatie kopie met de `ja-JP` land instellingen en de `ja-JP-NanamiNeural` stem.    |
| `ko-kr-sunhineural-preview`                 | Container installatie kopie met de `ko-KR` land instellingen en de `ko-KR-SunHiNeural` stem.     |
| `pt-br-franciscaneural-preview`             | Container installatie kopie met de `pt-BR` land instellingen en de `pt-BR-FranciscaNeural` stem. |
| `zh-cn-xiaoxiaoneural-preview`              | Container installatie kopie met de `zh-CN` land instellingen en de `zh-CN-XiaoxiaoNeural` stem.  |

---

## <a name="speech-language-detection"></a>Taaldetectie van spraak

De container installatie kopie voor de [spraak taal detectie][sp-lid] kan worden gevonden in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/speechservices/` opslag plaats en heet `language-detection` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/speechservices/language-detection` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/language-detection/tags/list).

| Afbeeldings Tags                                  | Notities                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `latest`                       |      |
| `1.1.0-amd64-preview`                       |      |

## <a name="key-phrase-extraction"></a>Sleuteltermextractie

container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/textanalytics/` opslag plaats en heet `keyphrase` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/textanalytics/keyphrase` .

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/textanalytics/keyphrase/tags/list).

# <a name="latest-version"></a>[Nieuwste versie](#tab/current)


| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.013570001-amd64` |       |

# <a name="previous-versions"></a>[Vorige versies](#tab/previous)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `1.1.012840001-amd64` |       |
| `1.1.012830001-amd64`    |       |

---

## <a name="text-language-detection"></a>Taaldetectie van tekst

De [taaldetectie][ta-la] container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/textanalytics/` opslag plaats en heet `language` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/textanalytics/language`


Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/textanalytics/language/tags/list).

# <a name="latest-versions"></a>[Nieuwste versies](#tab/current)

| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.013570001-amd64` | |
   

# <a name="previous-versions"></a>[Vorige versies](#tab/previous)


| Afbeeldings Tags                    | Notities |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.012840001-amd64` |   |
| `1.1.012830001-amd64` |   |

---

## <a name="sentiment-analysis"></a>Sentimentanalyse

De [sentimentanalyse][ta-se] container installatie kopie vindt u in het `mcr.microsoft.com` container register Syndicate. Deze bevindt zich in de `azure-cognitive-services/textanalytics/` opslag plaats en heet `sentiment` . De volledig gekwalificeerde naam van de container installatie kopie is, `mcr.microsoft.com/azure-cognitive-services/textanalytics/sentiment`

Voor deze container installatie kopie zijn de volgende tags beschikbaar. U kunt ook een volledige lijst met [Tags vinden op het MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/textanalytics/sentiment/tags/list).

| Afbeeldings Tags | Notities                                         |
|------------|:----------------------------------------------|
| `latest`   |                                               |
| `3.0-en`   | Sentimentanalyse v3 (Engels)               |
| `3.0-es`   | Sentimentanalyse v3 (Spaans)               |
| `3.0-fr`   | Sentimentanalyse v3 (Frans)                |
| `3.0-it`   | Sentimentanalyse v3 (Italiaans)               |
| `3.0-de`   | Sentimentanalyse v3 (Duits)                |
| `3.0-zh`   | Sentimentanalyse v3 (Chinees-vereenvoudigd)  |
| `3.0-zht`  | Sentimentanalyse v3 (Chinees-traditioneel) |
| `3.0-ja`   | Sentimentanalyse v3 (Japans)              |
| `3.0-pt`   | Sentimentanalyse v3 (Portugees)            |
| `3.0-nl`   | Sentimentanalyse v3 (Nederlands)                 |
| `2.1`    | Sentimentanalyse v2      |

[ad-containers]: ../anomaly-Detector/anomaly-detector-container-howto.md
[cv-containers]: ../computer-vision/computer-vision-how-to-install-containers.md
[fa-containers]: ../face/face-how-to-install-containers.md
[fr-containers]: ../form-recognizer/form-recognizer-container-howto.md
[lu-containers]: ../luis/luis-container-howto.md
[sp-stt]: ../speech-service/speech-container-howto.md?tabs=stt
[sp-cstt]: ../speech-service/speech-container-howto.md?tabs=cstt
[sp-tts]: ../speech-service/speech-container-howto.md?tabs=tts
[sp-ctts]: ../speech-service/speech-container-howto.md?tabs=ctts
[sp-ntts]: ../speech-service/speech-container-howto.md?tabs=ntts
[sp-lid]: ../speech-service/speech-container-howto.md?tabs=lid
[ta-kp]: ../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=keyphrase
[ta-la]: ../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=language
[ta-se]: ../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=sentiment
