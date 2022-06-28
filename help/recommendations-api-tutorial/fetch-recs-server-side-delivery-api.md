---
title: Recommendations ophalen met de leverings-API
description: In dit gedeelte van de zelfstudie worden ontwikkelaars door de vereiste stappen geleid voor het ophalen van aanbevolen inhoud met de Adobe Target Delivery API.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: 553d1208-647f-479d-acc7-d7760469d642
source-git-commit: 0ecfde208b3e201de135512d5aab70192fc2b826
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Ophalen [!DNL Recommendations] met de leverings-API

Adobe Target en Adobe Target [!DNL Recommendations] API&#39;s kunnen worden gebruikt om reacties op webpagina&#39;s te leveren, maar kunnen ook worden gebruikt in ervaringen die niet op HTML zijn gebaseerd, zoals apps, schermen, consoles, e-mails, kiosken en andere weergaveapparaten. Met andere woorden, wanneer [!DNL Target] bibliotheken en JavaScript kunnen niet worden gebruikt, de **[!DNL Target]Leverings-API** wij hebben nog steeds toegang tot het volledige scala van [!DNL Target] functionaliteit voor persoonlijke ervaringen.

>[!NOTE]
>
> Als u inhoud met feitelijke aanbevelingen (aanbevolen producten of items) aanvraagt, gebruikt u de opdracht [!DNL Target] Leverings-API.

Om aanbevelingen terug te winnen, verzend een vraag van de POST van de Levering API van Adobe Target met de aangewezen contextuele informatie, die een gebruiker - identiteitskaart (voor gebruik met profiel-specifieke aanbevelingen zoals onlangs bekeken punten van de gebruiker), relevante mbox naam, mbox parameters, profielparameters, of andere attributen kan omvatten. De reactie zal geadviseerde entiteit.ids (en kan andere entiteitgegevens omvatten) in formaat JSON of HTML omvatten, die dan in het apparaat kunnen worden getoond.

De [Leverings-API](https://developer.adobe.com/target/implement/delivery-api/){target=_blank} voor Adobe Target toont alle bestaande functies die een standaard [!DNL Target] request biedt.

>[!NOTE]
>De leverings-API:
>* Laat u toe om ervaringen of aanbiedingen voor een plaats en een publiek op een RESTful manier terug te winnen.
>* Geen verificatie vereist.
>* Alleen POST&#39;s.
>* Verwerkt geen cookies of richt geen aanroepen om.
>* Vereist of herkent geen &quot;gebruikersrollen.&quot; Het haalt eenvoudig inhoud of rapporteert gebeurtenissen aan [!DNL Target] Edge-servers.


De API voor levering gebruiken [!DNL Target] ervaringen—inclusief aanbevelingen—volgen de volgende stappen:

1. Een [!DNL Target] activiteit (A/B, XT, AP, of [!DNL Recommendations]) die de op vorm-Gebaseerde Composer (niet de Visuele Composer van de Ervaring) gebruiken.
2. Gebruik de leverings-API om een antwoord te krijgen voor de aanvragen die door de [!DNL Target] activiteit die u zojuist hebt gemaakt.

<!-- Q: Why are BOTH steps necessary for this? If you have a Form-based recommendation defined for an mbox, what's the point/benefit of ALSO having the Delivery API step in to retrieve results? Why can't you just have the Form-based Rec deliver the results in the destination device...?? A: See use case below... it's when you want to "intercept" the pending results in order to do more stuff prior to displaying the results. Things like real-time comparisons to inventory levels. -->

## Een aanbeveling maken met de Form-based Experience Composer

Als u aanbevelingen wilt maken die u met de API voor aflevering kunt gebruiken, gebruikt u de opdracht [Op formulieren gebaseerde composer](https://experienceleague.adobe.com/docs/target/using/experiences/form-experience-composer.html?lang=en).

1. Maak eerst een JSON-ontwerp en sla dit op dat u in uw aanbeveling wilt gebruiken. Voor voorbeeld JSON, plus achtergrondinformatie over hoe de reacties JSON kunnen worden teruggekeerd wanneer het vormen van een op vorm-gebaseerde activiteit, zie de documentatie over [Aanbevelingsontwerpen maken](https://experienceleague.adobe.com/docs/target/using/recommendations/recommendations-design/create-design.html?lang=en). In dit voorbeeld krijgt het ontwerp de naam *Eenvoudige JSON.*

   ![server-side-create-recs-json-design.png](assets/server-side-create-recs-json-design.png)

2. In [!DNL Target], navigeer naar **[!UICONTROL Activities]> [!UICONTROL Create Activity] >[!UICONTROL Recommendations]** selecteert u vervolgens **[!UICONTROL Form]**.

   ![server-side-create-recs.png](assets/server-side-create-recs.png)

3. Selecteer een eigenschap en klik op **[!UICONTROL Next]**.
4. Bepaal de plaats waar u gebruikers de reactie van de aanbeveling wilt ontvangen. In het onderstaande voorbeeld wordt een locatie gebruikt met de naam *api_charter*. Selecteer uw JSON-ontwerp, dat u eerder hebt gemaakt, met de naam *Eenvoudige JSON.*
   ![server-side-create-recs-form.png](assets/server-side-create-recs-form1.png)
5. Sla de aanbeveling op en activeer deze. Het zal resultaten opleveren. [Zodra de resultaten klaar zijn](https://experienceleague.adobe.com/docs/target/using/recommendations/recommendations-activity/previewing-and-launching-your-recommendations-activity.html?lang=en), kunt u de leverings-API gebruiken om deze op te halen.

## De API voor levering gebruiken

De syntaxis voor de [Leverings-API](https://developer.adobe.com/target/implement/delivery-api/#tag/Delivery-API){target=_blank} is:

`POST https://{{CLIENT_CODE}}.tt.omtrdc.net/rest/v1/delivery`

1. Let op: de clientcode is vereist. Ter herinnering: je clientcode kan in Adobe Target worden gevonden door naar **[!UICONTROL Recommendations]>[!UICONTROL Settings]**. Noteer de **[!UICONTROL Client Code]** in de **[!UICONTROL Recommendation API Token]** sectie.
   ![client-code.png](assets/client-code.png)
1. Zodra u uw cliëntcode hebt, construeer uw levering API vraag. Het onderstaande voorbeeld begint met het **[!UICONTROL Web Batched Mboxes Delivery API Call]** in de [Delivery API Postman-collectie](https://developers.adobetarget.com/api/delivery-api/#section/Getting-Started/Postman-Collection), waarbij relevante wijzigingen worden aangebracht. Bijvoorbeeld:
   * de **browser** en **adres** objecten zijn verwijderd uit de **Lichaam**, aangezien deze niet vereist zijn voor gevallen van niet-HTML gebruik
   * *api_charter* wordt vermeld als locatienaam in dit voorbeeld
   * de entiteit.id wordt opgegeven, omdat deze aanbeveling is gebaseerd op Content Gelijksoortigheid, die vereist dat een huidige item-sleutel wordt doorgegeven aan [!DNL Target].
      ![server-side-Delivery-API-call.png](assets/server-side-delivery-api-call2.png)
Herinner me om uw vraagparameters correct te vormen. Zorg er bijvoorbeeld voor dat u 
`{{CLIENT_CODE}}` indien nodig. <!--Q: In the updated call syntax, entity.id is listed as a profileParameter instead of an mboxParameter as in older versions. --> <!--Q: Old image ![server-side-create-recs-post.png](assets/server-side-create-recs-post.png) Old accompanying text: "Note this recommendation is based on Content Similar products based on the entity.id sent via mboxParameters." -->
      ![client-code3](assets/client-code3.png)
1. Verzend de aanvraag. Dit wordt uitgevoerd tegen de *api_charter* -locatie, waarop een actieve aanbeveling wordt uitgevoerd, gedefinieerd met uw JSON-ontwerp dat een lijst met aanbevolen entiteiten uitvoert.
1. Ontvang een reactie op basis van het JSON-ontwerp.
   ![server-side-create-recs-json-response2.png](assets/server-side-create-recs-json-response2.png)
De reactie omvat de sleutel-id en de entiteit-id&#39;s van de aanbevolen entiteiten.

De leverings-API gebruiken met [!DNL Recommendations] op deze manier kunt u aanvullende stappen uitvoeren voordat u aanbevelingen aan de bezoeker weergeeft op het niet-HTML apparaat. U kunt bijvoorbeeld de reactie van de API voor aflevering gebruiken om een extra, realtime zoekopdracht uit te voeren naar de details van de entiteitskenmerken (inventaris, prijs, classificatie, enzovoort) van een ander systeem (zoals een CMS-, PIM- of e-commerce-platform) voordat u de uiteindelijke resultaten weergeeft.

Met behulp van de aanpak die in deze zelfstudie wordt beschreven, kunt u elke toepassing de mogelijkheid bieden om de reactie van [!DNL Target] om persoonlijke aanbevelingen te doen!

## Voorbeeldimplementaties

De volgende bronnen bieden voorbeelden van verschillende implementaties die niet gericht zijn op HTML. Houd er rekening mee dat elke implementatie uniek zal zijn, vanwege het systeem en de apparaten in kwestie.

| Resource | Details |
| --- | --- |
| [Adobe Target Overal - Implementeer server-kant of in de IoT](https://expleague.azureedge.net/labs/L733/index.html) | Adobe Summit 2019 Lab die praktijkervaring biedt voor een React-toepassing die gebruikmaakt van Adobe Target server-side API&#39;s. |
| [Adobe Target in een mobiele toepassing zonder de Adobe-SDK](https://community.tealiumiq.com/t5/Universal-Data-Hub/Adobe-Target-in-a-Mobile-App-Without-the-Adobe-SDK/ta-p/26753) | In deze handleiding ziet u hoe u Adobe Target kunt instellen in uw mobiele app zonder de SDK van de Adobe te installeren. Deze oplossing gebruikt de webweergave van Tealium SDK en de module Externe opdrachten om aanvragen te verzenden en te ontvangen naar de Adobe Visitor API (Experience Cloud) en de Adobe Target API. |
| [Hoe Adobe Target werkt in mobiele apps](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/mobile-how-target-works-mobile-apps.html?lang=en) | Hoe [!DNL Target] werkt met de Mobile SDK |
| [Het vormen van [!DNL Target] uitbreiding in Experience Platform Launch en uitvoering [!DNL Target] API&#39;s](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target) | Stappen voor het configureren van de [!DNL Target] extensie in Experience Platform Launch toevoegen, de extensie [!DNL Target] Extensie naar uw app en implementatie [!DNL Target] API&#39;s om activiteiten aan te vragen, aanbiedingen vooraf in te stellen en de modus voor visuele voorvertoning te activeren. |
| [Adobe Target Node-client](https://www.npmjs.com/package/@adobe/target-nodejs-sdk) | Open-sourced [!DNL Target] Node.js SDK v1.0 |
| [Overzicht van de server](https://experienceleague.adobe.com/docs/target/using/implement-target/server-side/api-and-sdk-overview.html?lang=en) | Informatie over Adobe Target Server Side Delivery-API&#39;s, Server Side Batch Delivery-API&#39;s, Node.js SDK en Adobe Target [!DNL Recommendations] API&#39;s. |
| [Adobe Campaign Content Recommendations in Email](https://medium.com/adobetech/adobe-campaign-content-recommendations-in-email-b51ced771d7f) | Blog waarin wordt beschreven hoe u via Adobe Target en Adobe I/O Runtime in Adobe Campaign aanbevelingen kunt doen voor inhoud. |

## Beheer [!DNL Recommendations] Instellen met API&#39;s

Meestal worden aanbevelingen geconfigureerd in de gebruikersinterface van Adobe Target en vervolgens gebruikt of geopend via de [!DNL Target] API&#39;s om redenen zoals die welke in de bovenstaande secties worden genoemd. Deze UI-API-coördinatie komt veel voor. Soms willen gebruikers echter wel alle handelingen uitvoeren via API&#39;s, zowel de setup als het gebruik van resultaten. Hoewel veel minder vaak, kunnen de gebruikers absoluut vormen, uitvoeren, *en* de resultaten van aanbevelingen volledig te benutten met behulp van de API&#39;s.

We leerden in een [eerdere secties](https://developer.adobe.com/target/before-administer/recs-api/manage-catalog/){target=_blank} hoe u Adobe Target Recommendations-entiteiten beheert en deze op de server levert. Op dezelfde manier staat Adobe I/O u toe om criteria, bevorderingen, inzamelingen, en ontwerpmalplaatjes te beheren zonder het moeten login aan Adobe Target. Een volledige lijst van alle [!DNL Recommendations] Kan API&#39;s vinden [hier](https://developers.adobetarget.com/api/recommendations/), maar hier is een samenvatting ter referentie.

| Resource | Details |
| --- | --- |
| [Verzamelingen](https://developers.adobetarget.com/api/recommendations/#tag/Collections) | Verzamelingen weergeven, maken, ophalen, bewerken en verwijderen. |
| [Criteria](https://developers.adobetarget.com/api/recommendations/#tag/Criteria) | Lijst en krijg criteria. |
| [Ontwerpen](https://developers.adobetarget.com/api/recommendations/#tag/Designs) | Ontwerp weergeven, maken, ophalen, bewerken, verwijderen en valideren. |
| [Entiteiten](https://developers.adobetarget.com/api/recommendations/#tag/Entities) | Entiteiten opslaan, verwijderen en ophalen. |
| [Aanbiedingen](https://developers.adobetarget.com/api/recommendations/#tag/Promotions) | Promoties aanbieden, maken, ophalen, bewerken en verwijderen. |
| [Categoriecriteria](https://developers.adobetarget.com/api/recommendations/#tag/Category-Criteria) | Categoriecriteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Aangepaste criteria](https://developers.adobetarget.com/api/recommendations/#tag/Custom-Criteria) | Aangepaste criteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Objectcriteria](https://developers.adobetarget.com/api/recommendations/#tag/Item-Criteria) | Objectcriteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Criteria voor populariteit](https://developers.adobetarget.com/api/recommendations/#tag/Popularity-Criteria) | Maak een lijst, maak, krijg, bewerk en verwijder populiteitscriteria. |
| [Kenmerkcriteria profiel](https://developers.adobetarget.com/api/recommendations/#tag/Profile-Attribute-Criteria) | Criteria voor profielkenmerken weergeven, maken, ophalen, bewerken en verwijderen. |
| [Recente criteria](https://developers.adobetarget.com/api/recommendations/#tag/Recent-Criteria) | Recente criteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Reekscriteria](https://developers.adobetarget.com/api/recommendations/#tag/Sequence-Criteria) | U kunt volgreekscriteria weergeven, maken, ophalen, bewerken en verwijderen. |

## Referentiedocumentatie

* [Adobe Target Admin API-documentatie](https://developer.adobe.com/target/administer/admin-api/){target=_blank}
* [Adobe Target Delivery-API](https://developer.adobe.com/target/implement/delivery-api/){target=_blank}
* [Integreren [!DNL Recommendations] met e-mail](https://experienceleague.adobe.com/docs/target/using/recommendations/recommendations-faq/integrating-recs-email.html)

## Overzicht en revisie

Gefeliciteerd! Door deze zelfstudie te voltooien hebt u geleerd hoe te:
* [Uw catalogus beheren met de Recommendations API](https://developer.adobe.com/target/before-administer/recs-api/manage-catalog/){target=_blank}
* [Aangepaste criteria beheren met de Recommendations API](https://developer.adobe.com/target/before-administer/recs-api/manage-custom-criteria/){target=_blank}
* [De leverings-API gebruiken met Recommendations](https://developer.adobe.com/target/before-administer/recs-api/fetch-recs-server-side-delivery-api/){target=_blank}
