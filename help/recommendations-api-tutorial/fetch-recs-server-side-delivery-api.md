---
title: Recommendations ophalen met de leverings-API
description: In dit gedeelte van de zelfstudie worden ontwikkelaars door de vereiste stappen geleid voor het ophalen van aanbevolen inhoud met de Adobe Target Delivery API.
role: Ontwikkelaar
level: Intermediair
topic: Personalisatie, administratie, integratie, ontwikkeling
feature: API's/SDK's, Recommendations, Beheer en Configuratie
doc-type: tutorial
kt: 3815
thumbnail: null
author: Judy Kim
translation-type: tm+mt
source-git-commit: 2c371ea17ce38928bcf3655a0d604a69e29963a0
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 0%

---


# [!DNL Recommendations] ophalen met de bezorgings-API

De API&#39;s van Adobe Target en Adobe Target [!DNL Recommendations] kunnen worden gebruikt om reacties op webpagina&#39;s te leveren, maar kunnen ook worden gebruikt in niet-HTML-ervaringen, zoals apps, schermen, consoles, e-mails, kiosken en andere weergaveapparaten. Met andere woorden, wanneer [!DNL Target] bibliotheken en JavaScript niet kunnen worden gebruikt, biedt de **[!DNL Target]Delivery API** ons nog steeds toegang tot het volledige bereik van [!DNL Target] functionaliteit om persoonlijke ervaringen te bieden.

>[!NOTE]
>
> Wanneer u inhoud aanvraagt met feitelijke aanbevelingen (aanbevolen producten of items), gebruikt u de API [!DNL Target] Levering.

Om aanbevelingen terug te winnen, verzend een vraag van de POST van de Levering API van Adobe Target met de aangewezen contextuele informatie, die een gebruiker - identiteitskaart (voor gebruik met profiel-specifieke aanbevelingen zoals onlangs bekeken punten van de gebruiker), relevante mbox naam, mbox parameters, profielparameters, of andere attributen kan omvatten. De reactie zal geadviseerde entiteit.ids (en kan andere entiteitgegevens omvatten) in formaat JSON of HTML omvatten, die dan in het apparaat kunnen worden getoond.

De [Delivery API](https://developers.adobetarget.com/api/delivery-api/) voor Adobe Target stelt alle bestaande eigenschappen bloot die een standaard [!DNL Target] verzoek verstrekt.

>[!NOTE]
>De leverings-API:
>* Laat u toe om ervaringen of aanbiedingen voor een plaats en een publiek op een RESTful manier terug te winnen.
>* Geen verificatie vereist.
>* Alleen POST&#39;s.
>* Verwerkt geen cookies of richt geen aanroepen om.
>* Vereist of herkent geen &quot;gebruikersrollen.&quot; Het haalt eenvoudig inhoud op of rapporteert gebeurtenissen aan [!DNL Target] randservers.


Om levering API te gebruiken om [!DNL Target] ervaring-met inbegrip van aanbevelingen-volg deze stappen te leveren:

1. Maak een [!DNL Target]-activiteit (A/B, XT, AP of [!DNL Recommendations]) met behulp van de op formulieren gebaseerde Composer (niet de Visual Experience Composer).
2. Gebruik de leverings-API om een reactie op te halen voor de aanvragen die worden gegenereerd door de activiteit [!DNL Target] die u zojuist hebt gemaakt.

<!-- Q: Why are BOTH steps necessary for this? If you have a Form-based recommendation defined for an mbox, what's the point/benefit of ALSO having the Delivery API step in to retrieve results? Why can't you just have the Form-based Rec deliver the results in the destination device...?? A: See use case below... it's when you want to "intercept" the pending results in order to do more stuff prior to displaying the results. Things like real-time comparisons to inventory levels. -->

## Een aanbeveling maken met de Form-based Experience Composer

Om aanbevelingen tot stand te brengen die met levering API kunnen worden gebruikt, gebruik [Op vorm-gebaseerde Composer](https://docs.adobe.com/content/help/en/target/using/experiences/form-experience-composer.html).

1. Maak eerst een JSON-ontwerp en sla dit op dat u in uw aanbeveling wilt gebruiken. Voor voorbeeld JSON, plus achtergrondinformatie betreffende hoe de reacties JSON kunnen worden teruggekeerd wanneer het vormen van een op vorm-gebaseerde activiteit, zie de documentatie op [het Creëren van de Ontwerpen van de Aanbeveling](https://docs.adobe.com/content/help/en/target/using/recommendations/recommendations-design/create-design.html). In dit voorbeeld krijgt het ontwerp de naam *Eenvoudige JSON.*

   ![server-side-create-recs-json-design.png](assets/server-side-create-recs-json-design.png)

2. Navigeer in [!DNL Target] naar **[!UICONTROL Activities]> [!UICONTROL Create Activity] >[!UICONTROL Recommendations]** en selecteer **[!UICONTROL Form]**.

   ![server-side-create-recs.png](assets/server-side-create-recs.png)

3. Selecteer een eigenschap en klik op **[!UICONTROL Next]**.
4. Bepaal de plaats waar u gebruikers de reactie van de aanbeveling wilt ontvangen. In het onderstaande voorbeeld wordt een locatie met de naam *api_charter* gebruikt. Selecteer uw JSON-ontwerp, dat u eerder hebt gemaakt, met de naam *Simple JSON.*
   ![server-side-create-recs-form.png](assets/server-side-create-recs-form1.png)
5. Sla de aanbeveling op en activeer deze. Het zal resultaten opleveren. [Zodra de resultaten klaar](https://docs.adobe.com/content/help/en/target/using/recommendations/recommendations-activity/previewing-and-launching-your-recommendations-activity.html) zijn, kunt u de levering API gebruiken om hen terug te winnen.

## De API voor levering gebruiken

De syntaxis voor [Delivery API](https://developers.adobetarget.com/api/delivery-api/#tag/Delivery-API) is:

`POST https://{{CLIENT_CODE}}.tt.omtrdc.net/rest/v1/delivery`

1. Let op: de clientcode is vereist. Ter herinnering, uw cliëntcode kan in Adobe Target worden gevonden door aan **[!UICONTROL Recommendations]>[!UICONTROL Settings]** te navigeren. Noteer de waarde **[!UICONTROL Client Code]** in de sectie **[!UICONTROL Recommendation API Token]**.
   ![client-code.png](assets/client-code.png)
1. Zodra u uw cliëntcode hebt, construeer uw levering API vraag. Het onderstaande voorbeeld begint met de **[!UICONTROL Web Batched Mboxes Delivery API Call]** in de [Delivery API Postman collection](https://developers.adobetarget.com/api/delivery-api/#section/Getting-Started/Postman-Collection), waarbij relevante wijzigingen worden aangebracht. Bijvoorbeeld:
   * de **browser** en **address** voorwerpen werden verwijderd uit **Body**, aangezien zij niet voor niet-HTML gebruiksgevallen worden vereist
   * *api_* charteris weergegeven als locatienaam in dit voorbeeld
   * de entiteit.id wordt opgegeven, omdat deze aanbeveling is gebaseerd op Content Gelijksheid, waarvoor een huidige itemsleutel moet worden doorgegeven aan [!DNL Target].
      ![server-zij-levering-API-call.](assets/server-side-delivery-api-call2.png)
pngRemember om uw vraagparameters correct te vormen. Zorg er bijvoorbeeld voor dat u 
`{{CLIENT_CODE}}` indien nodig. <!--Q: In the updated call syntax, entity.id is listed as a profileParameter instead of an mboxParameter as in older versions. --> <!--Q: Old image ![server-side-create-recs-post.png](assets/server-side-create-recs-post.png) Old accompanying text: "Note this recommendation is based on Content Similar products based on the entity.id sent via mboxParameters." -->
      ![client-code3](assets/client-code3.png)
1. Verzend de aanvraag. Dit wordt uitgevoerd tegen de *api_charter* plaats, die een actieve aanbeveling heeft die op het loopt, die met uw ontwerp JSON wordt bepaald die een lijst van geadviseerde entiteiten zal uitvoeren.
1. Ontvang een reactie op basis van het JSON-ontwerp.
   ![server-side-create-recs-json-response2.](assets/server-side-create-recs-json-response2.png)
pngHet antwoord omvat de belangrijkste identiteitskaart, evenals entiteitidentiteitskaart van de geadviseerde entiteiten.

Als u op deze manier de API voor aflevering gebruikt met [!DNL Recommendations], kunt u aanvullende stappen uitvoeren voordat u aanbevelingen aan de bezoeker weergeeft op het niet-HTML-apparaat. U kunt bijvoorbeeld de reactie van de API voor aflevering gebruiken om een extra, realtime zoekopdracht uit te voeren naar de details van de entiteitskenmerken (inventaris, prijs, classificatie, enzovoort) van een ander systeem (zoals een CMS-, PIM- of e-commerce-platform) voordat u de uiteindelijke resultaten weergeeft.

Met behulp van de aanpak die in deze zelfstudie wordt beschreven, kunt u elke toepassing gebruiken om de reactie van [!DNL Target] te benutten en persoonlijke aanbevelingen te doen!

## Voorbeeldimplementaties

De volgende bronnen bieden voorbeelden van verschillende implementaties die niet gericht zijn op HTML. Houd er rekening mee dat elke implementatie uniek zal zijn, vanwege het systeem en de apparaten in kwestie.

| Resource | Details |
| --- | --- |
| [RESTful-API&#39;s gebruiken in AEM](https://helpx.adobe.com/experience-manager/using/restful-services.html) | Hoe te om een bundel van Adobe Experience Manager OSGi tot stand te brengen en op te stellen die gegevens van een derde RESTful Webdienst verbruikt. |
| [Adobe Target Overal - Implementeer server-kant of in de IoT](https://expleague.azureedge.net/labs/L733/index.html) | Adobe Summit 2019 Lab die praktijkervaring biedt voor een React-toepassing die gebruikmaakt van Adobe Target server-side API&#39;s. |
| [Adobe Target in een mobiele toepassing zonder de Adobe-SDK](https://community.tealiumiq.com/t5/Universal-Data-Hub/Adobe-Target-in-a-Mobile-App-Without-the-Adobe-SDK/ta-p/26753) | In deze handleiding ziet u hoe u Adobe Target kunt instellen in uw mobiele app zonder de SDK van de Adobe te installeren. Deze oplossing gebruikt de webweergave van Tealium SDK en de module Externe opdrachten om aanvragen te verzenden en te ontvangen naar de Adobe Visitor API (Experience Cloud) en de Adobe Target API. |
| [Hoe Adobe Target werkt in mobiele apps](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/mobile-how-target-works-mobile-apps.html) | Hoe werkt [!DNL Target] met de mobiele SDK |
| [API&#39; [!DNL Target] extension in Experience Platform Launch and Implementing [!DNL Target] s configureren](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target) | Stappen voor het configureren van de [!DNL Target]-extensie in Experience Platform Launch, het toevoegen van de [!DNL Target]-extensie aan uw app en het implementeren van [!DNL Target]-API&#39;s om activiteiten, prefetch-aanbiedingen en de modus voor visuele voorvertoning te vragen. |
| [Adobe Target Node-client](https://www.npmjs.com/package/@adobe/target-nodejs-sdk) | Open-sourced [!DNL Target] Node.js SDK v1.0 |
| [Overzicht van de server](https://docs.adobe.com/content/help/en/target/using/implement-target/server-side/api-and-sdk-overview.html) | Informatie over Adobe Target Server Side Delivery API&#39;s, Server Side Batch Delivery API&#39;s, Node.js SDK en Adobe Target [!DNL Recommendations] API&#39;s. |
| [Adobe Campaign Content Recommendations in Email](https://medium.com/adobetech/adobe-campaign-content-recommendations-in-email-b51ced771d7f) | Blog waarin wordt beschreven hoe u via Adobe Target en Adobe I/O Runtime in Adobe Campaign aanbevelingen kunt doen voor inhoud. |

## [!DNL Recommendations] Setup met API&#39;s beheren

Meestal worden aanbevelingen geconfigureerd in de gebruikersinterface van Adobe Target, en vervolgens gebruikt of benaderd via de API&#39;s van [!DNL Target], om redenen zoals de in de bovenstaande secties vermelde redenen. Deze UI-API-coördinatie komt veel voor. Soms willen gebruikers echter wel alle handelingen uitvoeren via API&#39;s, zowel de setup als het gebruik van resultaten. Hoewel veel minder vaak, kunnen de gebruikers absoluut vormen, uitvoeren, *en* hefboomwerking de resultaten van aanbevelingen volledig gebruikend APIs.

In een [eerdere sectie](manage-catalog.md) hebben we geleerd hoe we Adobe Target Recommendations-entiteiten kunnen beheren en op de server kunnen leveren. Op dezelfde manier staat Adobe I/O u toe om criteria, bevorderingen, inzamelingen, en ontwerpmalplaatjes te beheren zonder het moeten login aan Adobe Target. Een volledige lijst van alle [!DNL Recommendations] APIs kan [hier ](http://developers.adobetarget.com/api/recommendations/) worden gevonden, maar hier is een samenvatting ter verwijzing.

| Resource | Details |
| --- | --- |
| [Verzamelingen](http://developers.adobetarget.com/api/recommendations/#tag/Collections) | Verzamelingen weergeven, maken, ophalen, bewerken en verwijderen. |
| [Criteria](http://developers.adobetarget.com/api/recommendations/#tag/Criteria) | Lijst en krijg criteria. |
| [Ontwerpen](http://developers.adobetarget.com/api/recommendations/#tag/Designs) | Ontwerp weergeven, maken, ophalen, bewerken, verwijderen en valideren. |
| [Entiteiten](http://developers.adobetarget.com/api/recommendations/#tag/Entities) | Entiteiten opslaan, verwijderen en ophalen. |
| [Aanbiedingen](http://developers.adobetarget.com/api/recommendations/#tag/Promotions) | Promoties aanbieden, maken, ophalen, bewerken en verwijderen. |
| [Categoriecriteria](http://developers.adobetarget.com/api/recommendations/#tag/Category-Criteria) | Categoriecriteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Aangepaste criteria](http://developers.adobetarget.com/api/recommendations/#tag/Custom-Criteria) | Aangepaste criteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Objectcriteria](http://developers.adobetarget.com/api/recommendations/#tag/Item-Criteria) | Objectcriteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Criteria voor populariteit](http://developers.adobetarget.com/api/recommendations/#tag/Popularity-Criteria) | Maak een lijst, maak, krijg, bewerk en verwijder populiteitscriteria. |
| [Kenmerkcriteria profiel](http://developers.adobetarget.com/api/recommendations/#tag/Profile-Attribute-Criteria) | Criteria voor profielkenmerken weergeven, maken, ophalen, bewerken en verwijderen. |
| [Recente criteria](http://developers.adobetarget.com/api/recommendations/#tag/Recent-Criteria) | Recente criteria weergeven, maken, ophalen, bewerken en verwijderen. |
| [Reekscriteria](http://developers.adobetarget.com/api/recommendations/#tag/Sequence-Criteria) | U kunt volgreekscriteria weergeven, maken, ophalen, bewerken en verwijderen. |

## Referentiedocumentatie

* [Adobe Target API-documentatie](https://developers.adobetarget.com/api/#getting-started)
* [Adobe Target Delivery-API](https://developers.adobetarget.com/api/delivery-api/)
* [ [!DNL Recommendations] Integreren met e-mail](https://docs.adobe.com/content/help/en/target/using/recommendations/recommendations-faq/integrating-recs-email.html)

## Overzicht en revisie

Gefeliciteerd! Door deze zelfstudie te voltooien hebt u geleerd hoe te:
* [Uw catalogus beheren met de Recommendations API](manage-catalog.md)
* [Aangepaste criteria beheren met de Recommendations API](manage-custom-criteria.md)
* [De leverings-API gebruiken met Recommendations](fetch-recs-server-side-delivery-api.md)
