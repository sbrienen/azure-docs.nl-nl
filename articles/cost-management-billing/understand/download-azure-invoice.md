---
title: Uw Azure-factuur weergeven en downloaden
description: Hierin wordt beschreven hoe u uw Azure-factuur kunt weergeven en downloaden.
keywords: factuur,factuur downloaden,azure-factuur,azure-gebruik
author: bandersmsft
ms.reviewer: amberb
tags: billing
ms.service: cost-management-billing
ms.topic: conceptual
ms.date: 05/28/2020
ms.author: banders
ms.openlocfilehash: 4e77b167f00e2cfa3838439143c6074bd4122976
ms.sourcegitcommit: 1f48ad3c83467a6ffac4e23093ef288fea592eb5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84191235"
---
# <a name="view-and-download-your-microsoft-azure-invoice"></a>Uw Microsoft Azure-factuur weergeven en downloaden

U kunt uw factuur downloaden via de [Azure-portal](https://portal.azure.com/) of naar uw e-mailadres laten verzenden. Als u een Azure-klant bent met een Enterprise Agreement (EA-klant), kunt u de facturen van uw organisatie niet downloaden. Facturen worden verzonden naar degene die is ingesteld voor ontvangst van facturen voor de inschrijving.

## <a name="when-invoices-are-generated"></a>Wanneer facturen worden gegenereerd

Er wordt een factuur gegenereerd op basis van uw type factureringsrekening. Er worden facturen gemaakt voor factureringsrekeningen van Microsoft Online-serviceprogramma (MOSP), Microsoft-klantovereenkomst (MCA) en Microsoft Partner-overeenkomst (MPA). Er worden ook facturen gegenereerd voor factureringsrekeningen van Enterprise Agreement (EA). Facturen voor EA-factureringsrekeningen worden echter niet weergegeven in de Azure-portal.

Zie [Uw factureringsrekeningen weergeven in de Azure-portal](../manage/view-all-accounts.md) voor meer informatie over factureringsrekeningen en het bepalen van uw type factureringsrekening.

## <a name="invoices-for-mosp-billing-accounts"></a>Facturen voor de MOSP-factureringsrekeningen

Een MSOP-factureringsrekening wordt gemaakt wanneer u zich aanmeldt voor Azure via de Azure-website. Bijvoorbeeld als u zich aanmeldt voor een [gratis Azure-account](https://azure.microsoft.com/offers/ms-azr-0044p/), een [account met tarieven op gebruiksbasis](https://azure.microsoft.com/offers/ms-azr-0003p/) of een [Visual Studio-abonnement](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

Klanten in bepaalde regio's, die zich via de Azure-website aanmelden voor een [account met betalen-naar-gebruik-tarieven](https://azure.microsoft.com/offers/ms-azr-0003p/) of een [gratis Azure-account](https://azure.microsoft.com/offers/ms-azr-0044p/), kunnen ook een factureringsrekening voor een MCA hebben.

Zie [Uw type factureringsrekening controleren](../manage/view-all-accounts.md#check-the-type-of-your-account) als u niet zeker weet welk type factureringsrekening u hebt, voordat u de instructies in dit artikel volgt. 

Een MOSP-factureringsrekening kan de volgende facturen hebben:

**Azure-servicekosten**: er wordt een factuur gegenereerd voor elk Azure-abonnement met Azure-resources die worden gebruikt door het abonnement. De factuur bevat kosten voor een factureringsperiode. De factureringsperiode wordt vastgesteld op basis van de dag van de maand waarop het abonnement is gemaakt.

Jeroen maakt bijvoorbeeld *Azure-sub 01* op 5 maart en *Azure-sub 02* op 10 maart. De factuur voor *Azure-sub 01* bevat de kosten vanaf de vijfde dag van de maand tot en met de vierde dag van de volgende maand. De factuur voor *Azure-sub 02* bevat kosten vanaf de tiende dag van de maand tot de negende dag van de volgende maand. De facturen voor alle Azure-abonnementen worden normaal gesproken gegenereerd op de dag van de maand dat het account is gemaakt, maar dat kan ook tot maximaal twee dagen later zijn. Als Jeroen bijvoorbeeld een account heeft gemaakt op 2 februari, worden de facturen voor zowel *Azure-sub 01* als *Azure-sub 02* normaal gesproken gegenereerd op de tweede dag van elke maand, maar dat kan ook tot maximaal twee dagen later zijn.

**Azure Marketplace, reserveringen en spot-VM's**: er wordt een factuur gegenereerd voor reserveringen, Marketplace-producten en spot-VM's die zijn gekocht via een abonnement. De factuur bevat de respectievelijke kosten over de vorige maand. Jeroen heeft bijvoorbeeld een reservering aangeschaft op 1 maart en een andere reservering op 30 maart. Er wordt in april één factuur gegenereerd voor beide reserveringen. De factuur voor Azure Marketplace, reserveringen en spot-VM's wordt altijd gegenereerd rond de negende dag van de maand.

Als u voor Azure betaalt met een creditcard en u de reservering koopt, genereert Azure onmiddellijk een factuur. Als er echter wordt gefactureerd op basis van een factuur, worden er op uw volgende maandelijkse factuur kosten in rekening gebracht voor de reservering.

**Azure-ondersteuningsplan**: er wordt elke maand een factuur gegenereerd voor het abonnement op uw ondersteuningsplan. De eerste factuur wordt gegenereerd op de dag van aankoop of tot maximaal twee dagen later. Volgende facturen voor ondersteuningsplannen worden normaal gesproken gegenereerd op dezelfde dag van de maand dat het account is gemaakt, maar dat kan ook tot twee dagen later zijn.

## <a name="download-your-mosp-azure-subscription-invoice"></a>De factuur voor uw MOSP Azure-abonnement downloaden

Een factuur wordt alleen gegenereerd voor een abonnement dat deel uitmaakt van een factureringsrekening voor een MOSP. [Controleer uw toegang tot een MOSP-rekening](../manage/view-all-accounts.md#check-the-type-of-your-account). 

U moet voor een abonnement de rol van accountbeheerder hebben om de factuur te kunnen downloaden. Gebruikers met de rol van eigenaar, inzender of lezer kunnen de factuur downloaden als de accountbeheerder hen daartoe toestemming heeft gegeven. Zie [Gebruikers toestaan facturen te downloaden](../manage/manage-billing-access.md#opt-in)voor meer informatie.

1. Selecteer uw abonnement op de [pagina Abonnementen](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade) in de Azure-portal.
1. Selecteer **Facturen** in de factureringssectie.  
    ![Schermopname van een gebruiker die de optie Facturen voor een abonnement selecteert](./media/download-azure-invoice/select-subscription-invoice.png)
1. Selecteer **Downloaden** om een PDF-versie van uw factuur te downloaden en selecteer vervolgens **Downloaden** in de factuursectie.  
    ![Schermopname van de factureringsperioden, de downloadoptie en de totale kosten voor elke factureringsperiode](./media/download-azure-invoice/downloadinvoice-subscription.png)
1. U kunt ook een dagelijkse specificatie van de verbruikte hoeveelheden en de kosten downloaden door op **Downloaden** onder de sectie met gebruiksgegevens te klikken. Het kan enkele minuten duren om het CSV-bestand voor te bereiden.  
    ![Schermopname met de pagina voor factuur en gebruik downloaden](./media/download-azure-invoice/usage-and-invoice-subscription.png)

Zie [Meer informatie over uw factuur voor Microsoft Azure](../understand/review-individual-bill.md) voor meer informatie over uw factuur. Zie [Onverwachte kosten voorkomen met Azure-facturering en kostenbeheer](../manage/getting-started.md) voor hulp bij het beheren van uw kosten.

## <a name="download-your-mosp-support-plan-invoice"></a>De factuur voor uw MOSP-ondersteuningsplan downloaden

Een factuur wordt alleen gegenereerd voor een ondersteuningsplanabonnement dat deel uitmaakt van een factureringsrekening voor een MOSP. [Controleer uw toegang tot een MOSP-rekening](../manage/view-all-accounts.md#check-the-type-of-your-account).

U moet voor het ondersteuningsplanabonnement de rol van accountbeheerder hebben om de factuur ervoor te kunnen downloaden.

1. Meld u aan bij de [Azure-portal](https://portal.azure.com).
1. Zoek naar **Kostenbeheer en facturering**.  
    ![Schermopname van de zoekopdracht naar kostenbeheer en facturering in de Azure-portal](./media/download-azure-invoice/search-cmb.png)
1. Selecteer **Facturen** aan de linkerkant.
1. Selecteer uw ondersteuningsplanabonnement en selecteer vervolgens **Downloaden**.  
    [![Schermopname van de lijst met factureringsprofielen](./media/download-azure-invoice/cmb-invoices.png)](./media/download-azure-invoice/cmb-invoices-zoomed-in.png#lightbox)
1. Selecteer **Downloaden** om een PDF-versie van uw factuur te downloaden.  
    ![Schermopname van de factureringsperioden, de downloadoptie en de totale kosten voor elke factureringsperiode](./media/download-azure-invoice/download-invoice-support-plan.png)

## <a name="allow-others-to-download-the-your-subscription-invoice"></a>Anderen toestaan een factuur voor uw abonnement te downloaden

Een factuur downloaden:

1.  Meld u als accountbeheerder voor het abonnement aan bij de [Azure-portal](https://portal.azure.com).

2.  Zoek naar **Kostenbeheer en facturering**.

    ![Schermopname van de zoekopdracht naar kostenbeheer en facturering in de Azure-portal](./media/download-azure-invoice/search-cmb.png)

3.  Selecteer **Facturen** aan de linkerkant.

4.  Selecteer uw Azure-abonnement en klik op **Anderen toestemming geven om factuur te downloaden**.

    [![Schermopname van de selectie van Toegang tot factuur](./media/download-azure-invoice/cmb-select-access-to-invoice.png)](./media/download-azure-invoice/cmb-select-access-to-invoice-zoomed-in.png#lightbox)
1.  Selecteer **Aan** en **Opslaan** boven aan de pagina.  
    ![Schermopname waarop Aan voor Toegang tot factuur wordt geselecteerd](./media/download-azure-invoice/cmb-access-to-invoice.png)

## <a name="get-mosp-subscription-invoice-in-email"></a>Factuur voor MOSP-abonnement via e-mail ontvangen

U moet beschikken over de rol van accountbeheerder voor een abonnement of een ondersteuningsplan om te kunnen aangeven dat u de factuur ervoor per e-mail wilt ontvangen. E-mail facturen zijn alleen beschikbaar voor abonnementen en ondersteuningsplannen, niet voor reserveringen of Azure Marketplace-aankopen. Zodra u zich hebt aangemeld, kunt u extra ontvangers toevoegen die de factuur ook per e-mail ontvangen.

1.  Meld u aan bij de [Azure-portal](https://portal.azure.com).
2.  Zoek naar **Kostenbeheer en facturering**.  
3.  Selecteer **Facturen** aan de linkerkant.
4.  Selecteer uw Azure-abonnement of ondersteuningsplanabonnement en selecteer vervolgens **Factuur ontvangen per e-mail**.  
    [![Schermopname van de lijst met factureringsprofielen](./media/download-azure-invoice/cmb-email-invoice.png)](./media/download-azure-invoice/cmb-email-invoice-zoomed-in.png#lightbox)
5. Klik op **E-mailfactuur** en accepteer de voorwaarden.  
    ![Schermopname met stap 2 van de aanmelding](./media/download-azure-invoice/invoicearticlestep02.png)
6. De factuur wordt verzonden naar het e-mailadres van uw voorkeur. Selecteer **Profiel bijwerken** om het e-mailadres bij te werken.  
    ![Schermopname met stap 3 van de aanmelding](./media/download-azure-invoice/invoicearticlestep03-verifyemail.png)

## <a name="share-subscription-and-support-plan-invoices"></a>Facturen voor abonnementen en ondersteuningsplannen delen

Mogelijk wilt u de facturen voor uw abonnement en ondersteuningsplan elke maand met uw boekhoudteam delen of naar een van uw andere e-mailadressen verzenden.

1. Volg de stappen in [De facturen van uw abonnement en ondersteuningsplan per e-mail ontvangen](#get-mosp-subscription-invoice-in-email) en selecteer **Ontvangers configureren**.  
    ![Schermopname van een gebruiker die Ontvangers configureren selecteert](./media/download-azure-invoice/invoice-article-step03.png)
1. Voer een e-mailadres in en selecteer **Ontvanger toevoegen**. U kunt meerdere e-mailadressen toevoegen.  
    ![Schermopname van een gebruiker die extra ontvangers toevoegt](./media/download-azure-invoice/invoice-article-step04.png)
1. Nadat u alle e-mailadressen hebt toegevoegd, selecteert u **Gereed** onder aan het scherm.

## <a name="invoices-for-mca-and-mpa-billing-accounts"></a>Facturen voor MCA- en MPA-factureringsrekeningen

Er wordt een MCA-factureringsrekening gemaakt wanneer uw organisatie samenwerkt met een medewerker van Microsoft om een MCA te ondertekenen. Sommige klanten in bepaalde regio's, die zich via de Azure-website aanmelden voor een [account met betalen-naar-gebruik-tarieven](https://azure.microsoft.com/offers/ms-azr-0003p/) of een [gratis Azure-account](https://azure.microsoft.com/offers/ms-azr-0044p/), hebben mogelijk ook een factureringsrekening voor een MCA. Zie [Aan de slag met uw MCA-factureringsrekening](../understand/mca-overview.md) voor meer informatie.

Er wordt een MPA-factureringsaccount voor CSP-partners (Cloud Solution Provider) gemaakt zodat zij hun klanten kunnen beheren in de nieuwe Commerce-versie. Partners moeten minstens één klant met een [Azure-abonnement](https://docs.microsoft.com/partner-center/purchase-azure-plan) hebben om hun factureringsaccount te kunnen beheren in de Azure-portal. Zie [Aan de slag met uw MPA-factureringsrekening](../understand/mpa-overview.md) voor meer informatie.

Aan het begin van de maand wordt voor elk factureringsprofiel in uw account een maandelijkse factuur gegenereerd. De factuur bevat de respectievelijke kosten voor alle Azure-abonnementen en andere aankopen van de vorige maand. Jeroen heeft bijvoorbeeld *Azure-sub 01* op 5 maart en *Azure-sub 02* op 10 maart gemaakt. Hij heeft abonnement *Azure support 01* op 28 maart aangeschaft via *Billing profile 01*. Jeroen krijgt aan het begin van april één enkele factuur die de kosten voor zowel Azure-abonnementen als het ondersteuningsplan bevat.

##  <a name="download-an-mca-or-mpa-billing-profile-invoice"></a>Een factuur voor een MCA- of MPA-factureringsprofiel downloaden

U moet de rol van eigenaar, inzender, lezer of factuurbeheerder van een factureringsprofiel hebben om de factuur ervoor te kunnen downloaden in de Azure-portal. Gebruikers met de rol van eigenaar, Inzender of lezer van een factureringsrekening kunnen facturen downloaden voor alle factureringsprofielen in het account.

1.  Meld u aan bij de [Azure-portal](https://portal.azure.com).

2.  Zoek naar **Kostenbeheer en facturering**.

    ![Schermopname van de zoekopdracht naar kostenbeheer en facturering in de Azure-portal](./media/download-azure-invoice/search-cmb.png)

3. Selecteer **Facturen** aan de linkerkant.

    [![Schermopname van de pagina met facturen voor een MCA-factureringsrekening](./media/download-azure-invoice/mca-billingprofile-invoices.png)](./media/download-azure-invoice/mca-billingprofile-invoices-zoomed-in.png#lightbox)

4. Selecteer in de tabel met facturen de factuur die u wilt downloaden.

5. Klik bovenaan de pagina op de knop **PDF met factuur downloaden**.

    [![Schermopname van het downloaden van de PDF met de factuur](./media/download-azure-invoice/mca-billingprofile-download-invoice.png)](./media/download-azure-invoice/mca-billingprofile-download-invoice-zoomed-in.png#lightbox)

6. U kunt ook een dagelijkse uitsplitsing van de verbruikte hoeveelheden en geschatte kosten downloaden door op **Azure-gebruiksgegevens downloaden** te klikken. Het kan enkele minuten duren om het CSV-bestand voor te bereiden.

## <a name="get-your-billing-profiles-invoice-in-email"></a>De factuur voor uw factureringsprofiel via e-mail ontvangen

U moet de rol van eigenaar of Inzender voor het factureringsprofiel of de factureringsrekening hebben om de voorkeur voor het ontvangen van facturen via e-mail bij te werken. Zodra u zich daarvoor hebt aangemeld, ontvangen alle gebruikers met de rol van eigenaar, inzender, lezer of factuurbeheerder in een factureringsprofiel de factuur via e-mail. 

1.  Meld u aan bij de [Azure-portal](https://portal.azure.com).
1.  Zoek naar **Kostenbeheer en facturering**.  
1.  Selecteer **Facturen** aan de linkerkant en selecteer vervolgens **E-mailfactuur** boven aan de pagina.  
    [![Schermopname van de pagina met facturen voor een MCA-factureringsrekening](./media/download-azure-invoice/mca-billing-profile-select-email-invoice.png)](./media/download-azure-invoice/mca-billing-profile-select-email-invoice-zoomed.png#lightbox)
1.  Als u meerdere factureringsprofielen hebt, selecteert u er een en selecteert u vervolgens **Aanmelden**.  
    ![Schermopname van de pagina met facturen voor een MCA-factureringsrekening](./media/download-azure-invoice/mca-billing-profile-email-invoice.png)
1.  Selecteer **Update**.

2.  Zoek naar **Kostenbeheer en facturering**.

    ![Schermopname van de zoekopdracht naar kostenbeheer en facturering in de Azure-portal](./media/download-azure-invoice/search-cmb.png)

3.  Selecteer **Facturen** aan de linkerkant en selecteer vervolgens **E-mailfactuur** boven aan de pagina.

    [![Schermopname van de pagina met facturen voor een MCA-factureringsrekening](./media/download-azure-invoice/mca-billingprofile-select-emailinvoice.png)](./media/download-azure-invoice/mca-billingprofile-select-emailinvoice-zoomed-in.png)

4.  Als u meerdere factureringsprofielen hebt, selecteert u er een en selecteert u vervolgens **Aanmelden**.

U kunt anderen toegang geven om facturen te bekijken, te downloaden en te betalen door hen de rol van factuurbeheerder toe te wijzen voor een MCA- of MPA-factureringsprofiel. Als u ervoor hebt gekozen om facturen via e-mail te ontvangen, krijgen de gebruikers de facturen ook via e-mail.

1. Meld u aan bij de [Azure-portal](https://portal.azure.com).
1. Zoek naar **Kostenbeheer en facturering**.  
1. Selecteer aan de linkerkant de optie **Factureringsprofielen**. Selecteer in de lijst factureringsprofielen een factureringsprofiel waarvoor u de rol van factuurbeheerder wilt toewijzen.  
   ![Schermopname van de lijst met factureringsprofielen](./media/download-azure-invoice/mca-select-profile-zoomed-in.png)
1. Selecteer **Toegangsbeheer (IAM)** aan de linkerkant en selecteer vervolgens **Toevoegen** bovenaan de pagina.  
    ![Schermopname van de pagina Toegangsbeheer](./media/download-azure-invoice/mca-select-access-control-zoomed-in.png)
1. Selecteer **Factuurbeheerder** in de vervolgkeuzelijst Rol. Voer het e-mailadres in van de gebruiker die u toegang wilt verlenen. Selecteer **Opslaan** om de rol toe te wijzen.  
   ![Schermopname van het toevoegen van een gebruiker als een factuurbeheerder](./media/download-azure-invoice/mca-added-invoice-manager.png)

1. Zoek naar **Kostenbeheer en facturering**.

   ![Schermopname van zoekopdracht in portal naar abonnementen](./media/download-azure-invoice/search-cmb.png)

1. Selecteer aan de linkerkant de optie **Factureringsprofielen**. Selecteer in de lijst factureringsprofielen een factureringsprofiel waarvoor u de rol van factuurbeheerder wilt toewijzen.

   ![Schermopname van de lijst met factureringsprofielen](./media/download-azure-invoice/mca-select-profile-zoomed-in.png)

1. Selecteer **Toegangsbeheer (IAM)** aan de linkerkant en selecteer vervolgens **Toevoegen** bovenaan de pagina.

   [![Schermopname van de pagina Toegangsbeheer](./media/download-azure-invoice/mca-select-access-control-zoomed-in.png)

1. Selecteer **Factuurbeheerder** in de vervolgkeuzelijst Rol. Voer het e-mailadres in van de gebruiker die u toegang wilt verlenen. Selecteer **Opslaan** om de rol toe te wijzen.

   [![Schermopname van het toevoegen van een gebruiker als een factuurbeheerder](./media/download-azure-invoice/mca-added-invoice-manager.png)](./media/download-azure-invoice/mca-added-invoice-manager.png#lightbox)
   
   
##  <a name="why-you-might-not-see-an-invoice"></a>Waarom u mogelijk geen factuur ziet

<a name="noinvoice"></a>

Er kunnen verschillende redenen voor zijn dat u geen factuur ziet:

- De factuur is nog niet klaar
    
    - Het is minder dan 30 dagen geleden dat u zich geabonneerd hebt op Azure. 

    - Azure factureert u een paar dagen na het einde van de factureringsperiode. Het is dus mogelijk dat er nog geen factuur is gegenereerd.

- U bent niet gemachtigd om facturen te bekijken. 
    
    - Als u een MCA- of MPA-factureringsrekening hebt, moet u de rol van eigenaar, inzender, lezer of factuurbeheerder voor het factureringsprofiel of de rol van eigenaar, inzender of lezer voor de factureringsrekening hebben om facturen te kunnen bekijken. 
    
    - Voor andere factureringsaccounts ziet u mogelijk geen facturen als u niet de accountbeheerder bent.

- Uw account biedt geen ondersteuning voor facturen.

    - Als u een factureringsaccount voor Microsoft Online Services Program (MOSP) hebt en u zich hebt geregistreerd voor een gratis Azure-account of een abonnement met een maandelijks tegoed, ontvangt u alleen een factuur wanneer u het maandelijkse tegoed overschrijdt.

    - Als u een factureringsaccount voor een Microsoft-klantovereenkomst of Microsoft Partner-overeenkomst hebt, ontvangt u altijd een factuur.

- U hebt toegang tot de factuur via een van uw andere accounts.

    - Dit gebeurt meestal wanneer u op een koppeling in het e-mailbericht klikt, waarin u wordt gevraagd uw factuur weer te geven in de portal. U klikt op de koppeling en ziet een foutbericht: `We can't display your invoices. Please try again`. Controleer of u bent aangemeld met het e-mailadres dat is gemachtigd om de facturen te bekijken.

- U hebt toegang tot de factuur via een andere identiteit. 

    - Sommige klanten hebben twee identiteiten met hetzelfde e-mailadres: een werkaccount en een Microsoft-account. Normaal gesproken heeft slechts een van de identiteiten machtigingen voor het weergeven van facturen. Als de gebruiker zich aanmeldt met de identiteit die niet is gemachtigd, worden de facturen niet weergegeven. Controleer of u de juiste identiteit gebruikt om u aan te melden.

- U bent aangemeld bij de verkeerde Azure Active Directory-tenant (AAD). 

    - Uw factureringsaccount is gekoppeld aan een AAD-tenant. Als u bent aangemeld bij een onjuiste tenant, wordt de factuur voor abonnementen niet weergegeven in op factureringsaccount. Controleer of u bent aangemeld bij de juiste Azure Active Directory-tenant (AAD). Als u niet bent aangemeld bij de juiste tenant, gaar u als volgt te werk om van tenant te wisselen in de Azure-portal:

        1. Selecteer uw e-mailadres rechtsboven op de pagina.

        2. Selecteer **Schakelen tussen directory's**.

           ![Schermopname van het selecteren van Schakelen tussen directory's in de portal](./media/download-azure-invoice/select-switch-directory.png)

        3. Selecteer een directory in de sectie **Alle directory's**.

           ![Schermopname van het selecteren van een directory in de portal](./media/download-azure-invoice/select-directory.png)

## <a name="need-help-contact-us"></a>Hebt u hulp nodig? Neem contact met ons op.

Als u vragen hebt of hulp nodig hebt, [kunt u een ondersteuningsaanvraag maken](https://go.microsoft.com/fwlink/?linkid=2083458).

## <a name="next-steps"></a>Volgende stappen

Zie voor meer informatie over uw factuur en kosten:

- [Uw Microsoft Azure-gebruik en -kosten weergeven en downloaden](download-azure-daily-usage.md)
- [Meer informatie over uw factuur voor Microsoft Azure](review-individual-bill.md)
- [Informatie over begrippen op uw Azure-factuur](understand-invoice.md)

Als u een MCA hebt, zie:

- [Informatie over de kosten op de factuur voor uw factureringsprofiel](review-customer-agreement-bill.md)
- [Informatie over begrippen op de factuur voor uw factureringsprofiel](mca-understand-your-invoice.md)
- [Informatie over het bestand voor Azure-gebruik en -kosten voor uw factureringsprofiel](mca-understand-your-usage.md)