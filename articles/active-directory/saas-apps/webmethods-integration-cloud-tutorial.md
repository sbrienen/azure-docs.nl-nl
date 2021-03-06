---
title: 'Zelfstudie: Azure Active Directory-integratie met webMethods Integration Suite | Microsoft Docs'
description: Ontdek hoe u eenmalige aanmelding configureert tussen Azure Active Directory en webMethods Integration Suite.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: celested
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 02/15/2019
ms.author: jeedes
ms.openlocfilehash: 52ad0d0356f4d309db89db6527d7fd2d7dec253d
ms.sourcegitcommit: fb3c846de147cc2e3515cd8219d8c84790e3a442
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92636813"
---
# <a name="tutorial-azure-active-directory-integration-with-webmethods-integration-suite"></a>Zelfstudie: Azure Active Directory-integratie met webMethods Integration Suite

In deze zelfstudie leert u hoe u webMethods Integration Suite integreert met Azure Active Directory (Azure AD).
De integratie van webMethods Integration Suite met Azure AD biedt de volgende voordelen:

* U kunt in Azure AD beheren wie toegang heeft tot webMethods Integration Suite.
* U kunt inschakelen dat gebruikers automatisch met hun Azure AD-account worden aangemeld bij webMethods Integration Suite (eenmalige aanmelding).
* U kunt uw accounts vanaf één centrale locatie beheren: de Azure-portal.

Zie [What is application access and single sign-on with Azure Active Directory?](../manage-apps/what-is-single-sign-on.md) (Wat houden toegang tot toepassingen en eenmalige aanmelding met Azure Active Directory in?) als u wilt graag meer wilt weten over de integratie van SaaS-apps met Azure AD.
Als u geen abonnement op Azure hebt, maakt u een [gratis account](https://azure.microsoft.com/free/) voordat u begint.

## <a name="prerequisites"></a>Vereisten

Voor het configureren van Azure AD-integratie met webMethods Integration Suite hebt u het volgende nodig:

* Een Azure AD-abonnement Als u geen Azure AD-omgeving hebt, kunt u [hier](https://azure.microsoft.com/pricing/free-trial/) de proefversie van één maand krijgen.
* Een abonnement op webMethods Integration Suite waarvoor eenmalige aanmelding is ingeschakeld

## <a name="scenario-description"></a>Scenariobeschrijving

In deze zelfstudie gaat u in een testomgeving eenmalige aanmelding van Azure AD configureren en testen.

* webMethods Integration Suite ondersteunt door **SP** en **IDP** geïnitieerde eenmalige aanmelding

* webMethods Integration Suite biedt ondersteuning voor **Just-In-Time** -inrichting van gebruikers

## <a name="adding-webmethods-integration-suite-from-the-gallery"></a>webMethods Integration Suite toevoegen vanuit de galerie

Voor het configureren van de integratie van webMethods Integration Suite met Azure AD moet u webMethods Integration Suite uit de galerie toevoegen aan uw lijst met beheerde SaaS-apps.

**Als u webMethods Integration Suite vanuit de galerie wilt toevoegen, moet u de volgende stappen uitvoeren:**

1. Klik in het linkernavigatievenster in de **[Azure-portal](https://portal.azure.com)** op het **Azure Active Directory** -pictogram.

    ![De knop Azure Active Directory](common/select-azuread.png)

2. Navigeer naar **Bedrijfstoepassingen** en selecteer vervolgens de optie **Alle toepassingen** .

    ![De blade Bedrijfstoepassingen](common/enterprise-applications.png)

3. Als u de nieuwe toepassing wilt toevoegen, klikt u op de knop **Nieuwe toepassing** boven aan het dialoogvenster.

    ![De knop Nieuwe toepassing](common/add-new-app.png)

4. Typ **webMethods Integration Suite** in het zoekvak, selecteer **webMethods Integration Suite** in het deelvenster met resultaten en klik vervolgens op **Toevoegen** om de toepassing toe te voegen.

     ![webMethods Integration Suite in de lijst met resultaten](common/search-new-app.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Azure AD-eenmalige aanmelding configureren en testen

In deze sectie configureert en test u eenmalige aanmelding van Azure AD met webMethods Integration Suite op basis van een testgebruiker met de naam **Britta Simon** .
Eenmalige aanmelding werkt alleen als er een koppelingsrelatie tussen een Azure AD-gebruiker en de daaraan gerelateerde gebruiker in webMethods Integration Suite tot stand is gebracht.

Voltooi de volgende stappen om eenmalige aanmelding van Azure AD met webMethods Integration Suite te configureren en te testen:

1. **[Azure AD-eenmalige aanmelding configureren](#configure-azure-ad-single-sign-on)** : als u wilt dat uw gebruikers deze functie kunnen gebruiken.
2. **[Eenmalige aanmelding van webMethods Integration Suite configureren](#configure-webmethods-integration-suite-single-sign-on)** : als u de instellingen voor eenmalige aanmelding aan de toepassingszijde wilt configureren.
3. **[Een Azure AD-testgebruiker maken](#create-an-azure-ad-test-user)** : als u Azure AD-eenmalige aanmelding wil testen met Britta Simon.
4. **[De testgebruiker van Azure AD-toewijzen](#assign-the-azure-ad-test-user)** : als u wilt dat Britta Simon gebruik kan maken van Azure AD-eenmalige aanmelding.
5. **[Een testgebruiker voor webMethods Integration Suite maken](#create-webmethods-integration-suite-test-user)** : als u een tegenhanger van Britta Simon in webMethods Integration Suite wilt hebben die gekoppeld is aan de Azure AD-weergave van de gebruiker.
6. **[Eenmalige aanmelding testen](#test-single-sign-on)** : als u wilt controleren of de configuratie werkt.

### <a name="configure-azure-ad-single-sign-on"></a>Azure AD configureren voor eenmalige aanmelding

In deze sectie gaat u Azure AD-eenmalige aanmelding in de Azure-portal inschakelen.

Voer de volgende stappen uit als u Azure AD-eenmalige aanmelding wilt configureren met webMethods Integration Suite:

1. Ga in [Azure Portal](https://portal.azure.com/) naar de pagina voor integratie van de toepassing **webMethods Integration Suite** en selecteer **Eenmalige aanmelding** .

    ![Koppeling Eenmalige aanmelding configureren](common/select-sso.png)

2. In het dialoogvenster **Een methode voor eenmalige aanmelding selecteren** selecteert u de modus **SAML/WS-Federation** om eenmalige aanmelding in te schakelen.

    ![De modus Eenmalige aanmelding selecteren](common/select-saml-option.png)

3. Op de pagina **Eenmalige aanmelding met SAML instellen** klikt u op het pictogram **Bewerken** om het dialoogvenster **Standaard SAML-configuratie** te openen.

    ![Standaard SAML-configuratie bewerken](common/edit-urls.png)

4. Als u de **webMethods Integration Suite** wilt configureren in de sectie **Standaard SAML-configuratie** , als u de toepassing in de door **IDP** geïnitieerde modus wilt configureren, voert u de volgende stappen uit:

    ![Schermopname die de Standaard SAML-configuratie toont, waar u de id en URL kunt invoeren en vervolgens Opslaan selecteert.](common/idp-intiated.png)

    a. In het tekstvak **Id** typt u een URL met het volgende patroon:

    - `<SUBDOMAIN>.webmethodscloud.com`
    - `<SUBDOMAIN>.webmethodscloud.eu`
    - `<SUBDOMAIN>.webmethodscloud.de`

    b. In het tekstvak **Antwoord-URL** typt u een URL met het volgende patroon:


    - `https://<SUBDOMAIN>.webmethodscloud.com/integration/live/saml/ssoResponse`
    - `https://<SUBDOMAIN>.webmethodscloud.eu/integration/live/saml/ssoResponse`
    - `https://<SUBDOMAIN>.webmethodscloud.de/integration/live/saml/ssoResponse`

    c. Klik op **Extra URL's instellen** en voer de volgende stap uit als u de toepassing in de door **SP** geïnitieerde modus wilt configureren:

    ![Schermopname die Extra URL's instellen toont, waar u een aanmeldings-URL kunt invoeren.](common/metadata-upload-additional-signon.png)

    d. Typ in het tekstvak **Aanmeldings-URL** een URL met het volgende patroon:

    - `https://<SUBDOMAIN>.webmethodscloud.com/integration/live/saml/ssoRequest`
    - `https://<SUBDOMAIN>.webmethodscloud.eu/integration/live/saml/ssoRequest`
    - `https://<SUBDOMAIN>.webmethodscloud.de/integration/live/saml/ssoRequest`

    > [!NOTE]
    > Dit zijn geen echte waarden. Werk deze waarden bij met de werkelijke-id, de antwoord-URL en de aanmeldings-URL. Neem contact op met het [ondersteuningsteam van webMethods Integration Suite](https://empower.softwareag.com/) om deze waarden te verkrijgen. U kunt ook verwijzen naar het patroon dat wordt weergegeven in de sectie **Standaard SAML-configuratie** in de Azure-portal.

5. Als u de **webMethods API Cloud** wilt configureren in de sectie **Standaard SAML-configuratie** , als u de toepassing in de door **IDP** geïnitieerde modus wilt configureren, voert u de volgende stappen uit:

    ![Schermopname die de Standaard SAML-configuratie toont, waar u de id en URL kunt invoeren en vervolgens Opslaan selecteert.](common/idp-intiated.png)

    a. In het tekstvak **Id** typt u een URL met het volgende patroon:

    - `<SUBDOMAIN>.webmethodscloud.com`
    - `<SUBDOMAIN>.webmethodscloud.eu`
    - `<SUBDOMAIN>.webmethodscloud.de`

    b. In het tekstvak **Antwoord-URL** typt u een URL met het volgende patroon:

    - `https://<SUBDOMAIN>.webmethodscloud.com/umc/rest/saml/initsso`
    - `https://<SUBDOMAIN>.webmethodscloud.eu/umc/rest/saml/initsso`
    - `https://<SUBDOMAIN>.webmethodscloud.de/umc/rest/saml/initsso`

    c. Klik op **Extra URL's instellen** en voer de volgende stap uit als u de toepassing in de door **SP** geïnitieerde modus wilt configureren:

    ![Schermopname die Extra URL's instellen toont, waar u een aanmeldings-URL kunt invoeren.](common/metadata-upload-additional-signon.png)

    d. Typ in het tekstvak **Aanmeldings-URL** een URL met het volgende patroon:

    - `https://api.webmethodscloud.com/umc/rest/saml/initsso/?tenant=<TENANTID>`
    - `https://api.webmethodscloud.eu/umc/rest/saml/initsso/?tenant=<TENANTID>`
    - `https://api.webmethodscloud.de/umc/rest/saml/initsso/?tenant=<TENANTID>`

    > [!NOTE]
    > Dit zijn geen echte waarden. Werk deze waarden bij met de werkelijke-id, de antwoord-URL en de aanmeldings-URL. Neem contact op met het [ondersteuningsteam van webMethods Integration Suite](https://empower.softwareag.com/) om deze waarden te verkrijgen. U kunt ook verwijzen naar het patroon dat wordt weergegeven in de sectie **Standaard SAML-configuratie** in de Azure-portal.

6. Op de pagina **Eenmalige aanmelding met SAML instellen** in het gedeelte **SAML-handtekeningcertificaat** klikt u op **Downloaden** om het **XML-bestand met federatieve metagegevens**  te downloaden uit de gegeven opties overeenkomstig met wat u nodig hebt, en slaat u dit op uw computer op.

    ![De link om het certificaat te downloaden](common/metadataxml.png)

7. In de sectie **webMethods Integration Suite instellen** kopieert u de juiste URL('s) op basis van uw behoeften.

    ![Configuratie-URL's kopiëren](common/copy-configuration-urls.png)

    a. Aanmeldings-URL

    b. Azure AD-id

    c. Afmeldings-URL

### <a name="configure-webmethods-integration-suite-single-sign-on"></a>Eenmalige aanmelding van webMethods Integration Suite configureren

Als u eenmalige aanmelding aan de zijde van **webMethods Integration Suite** wilt configureren, moet u het gedownloade **XML-bestand met federatieve metagegevens** en de correcte uit Azure Portal gekopieerde URL's verzenden naar het [ondersteuningsteam van webMethods Integration Suite](https://empower.softwareag.com/). Het team stelt de instellingen zo in dat de verbinding tussen SAML en eenmalige aanmelding aan beide zijden goed is ingesteld.

### <a name="create-an-azure-ad-test-user"></a>Een Azure AD-testgebruiker maken

Het doel van deze sectie is om in de Azure-portal een testgebruiker met de naam Britta Simon te maken.

1. Selecteer in het linkerdeelvenster in de Azure-portal de optie **Azure Active Directory** , selecteer **Gebruikers** en selecteer vervolgens **Alle gebruikers** .

    ![De koppelingen Gebruikers en groepen en Alle gebruikers](common/users.png)

2. Selecteer **Nieuwe gebruiker** boven aan het scherm.

    ![Knop Nieuwe gebruiker](common/new-user.png)

3. In Gebruikerseigenschappen voert u de volgende stappen uit.

    ![Het dialoogvenster Gebruiker](common/user-properties.png)

    a. Voer in het veld **Naam** **Britta Simon** in.
  
    b. In het veld **Gebruikersnaam** typt u **brittasimon\@yourcompanydomain.extension**  
    Bijvoorbeeld: BrittaSimon@contoso.com

    c. Schakel het selectievakje **Wachtwoord weergeven** in en noteer de waarde die wordt weergegeven in het vak Wachtwoord.

    d. Klik op **Create** .

### <a name="assign-the-azure-ad-test-user"></a>De Azure AD-testgebruiker toewijzen

In deze sectie gaat u Britta Simon toestemming geven voor gebruik van eenmalige aanmelding met Azure door haar toegang te geven tot webMethods Integration Suite.

1. Selecteer in Azure Portal achtereenvolgens **Bedrijfstoepassingen** , **Alle toepassingen** en **webMethods Integration Suite** .

    ![De blade Bedrijfstoepassingen](common/enterprise-applications.png)

2. Selecteer **webMethods Integration Cloud** in de lijst met toepassingen.

    ![De webMethods Integration Suite-koppeling in de lijst met toepassingen](common/all-applications.png)

3. Selecteer in het menu aan de linkerkant **Gebruikers en groepen** .

    ![De koppeling Gebruikers en groepen](common/users-groups-blade.png)

4. Klik op de knop **Gebruiker toevoegen** en selecteer vervolgens **Gebruikers en groepen** in het dialoogvenster **Toewijzing toevoegen** .

    ![Het deelvenster Toewijzing toevoegen](common/add-assign-user.png)

5. Selecteer in het dialoogvenster **Gebruikers en groepen** **Britta Simon** in de lijst Gebruikers en klik op de knop **Selecteren** onder aan het scherm.

6. Als u een waarde voor een rol verwacht in de SAML-bewering, moet u in het dialoogvenster **Rol selecteren** de juiste rol voor de gebruiker in de lijst selecteren en vervolgens op de knop **Selecteren** onder aan het scherm klikken.

7. Klik in het dialoogvenster **Toewijzing toevoegen** op de knop **Toewijzen** .

### <a name="create-webmethods-integration-suite-test-user"></a>Een testgebruiker voor webMethods Integration Suite maken

In deze sectie wordt een gebruiker met de naam Britta Simon gemaakt in webMethods Integration Suite. webMethods Integration Suite biedt ondersteuning voor Just-In-Time-inrichting van gebruikers. Deze functie is standaard ingeschakeld. Er is geen actie-item voor u in deze sectie. Als er nog geen gebruiker in webMethods Integration Suite bestaat, wordt er een nieuwe gemaakt na de verificatie.

### <a name="test-single-sign-on"></a>Eenmalige aanmelding testen 

In deze sectie gaat u uw configuratie van Azure AD-eenmalige aanmelding testen via het toegangsvenster.

Wanneer u in het toegangsvenster op de tegel webMethods Integration Suite klikt, wordt u automatisch aangemeld bij het exemplaar van webMethods Integration Suite waarvoor u eenmalige aanmelding hebt ingesteld. Zie [Introduction to the Access Panel](../user-help/my-apps-portal-end-user-access.md) (Inleiding tot het toegangsvenster) voor meer informatie over het toegangsvenster.

## <a name="additional-resources"></a>Aanvullende resources

- [Lijst met zelfstudies over het integreren van SaaS-apps met Azure Active Directory](./tutorial-list.md)

- [What is application access and single sign-on with Azure Active Directory?](../manage-apps/what-is-single-sign-on.md) (Wat houden toegang tot toepassingen en eenmalige aanmelding met Azure Active Directory in?)

- [Wat is voorwaardelijke toegang in Azure Active Directory?](../conditional-access/overview.md)