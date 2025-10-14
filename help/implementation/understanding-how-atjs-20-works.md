---
title: Hoe werkt at.js 2.0?
description: Leer hoe at.js 2.0 de steun van Adobe Target voor enige paginatoepassingen (SPA) verbetert en met andere oplossingen van Experience Cloud integreert.
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 7f037665-88a7-469c-8df5-c82cb0f65382
source-git-commit: fcd2273ba373dc2b3bc59a77f1925cdb7b2ed3ee
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Begrijp hoe Adobe Target op.js 2.0 werkt

`at.js` 2.0 verbetert de Adobe Target-ondersteuning voor single page applications (SPA) en integreert deze met andere Experience Cloud-oplossingen. In deze video en de bijbehorende diagrammen wordt uitgelegd hoe alles samenkomt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architectuurdiagrammen

![&#x200B; at.js 2.0 gedrag op paginading &#x200B;](assets/pageload.png)

1. De vraag keert Experience Cloud ID (ECID) terug. Als de gebruiker voor authentiek wordt verklaard, synchroniseert een andere vraag de klantenidentiteitskaart

1. `at.js` -bibliotheek wordt synchroon geladen en de hoofdtekst van het document verborgen ( `at.js` kan ook asynchroon worden geladen met een optioneel vooraf verborgen fragment dat op de pagina is geïmplementeerd).

1. Het verzoek om het laden van de pagina wordt ingediend met inbegrip van alle gevormde parameters, ECID, SDID en klant ID.

1. Profielscripts worden uitgevoerd en opgenomen in de [!UICONTROL Profile Store] . De Store vraagt gekwalificeerd publiek aan van [!UICONTROL Audience Library] (bijv. publiek dat vanuit [!DNL Analytics], Audience Manager, enz. wordt gedeeld). [!UICONTROL Customer Attributes] worden in een batchproces verzonden naar [!UICONTROL Profile Store] .
1. Op basis van URL-, verzoek- en profielgegevens bepaalt [!DNL Target] welke Activiteiten en Ervaringen naar de bezoeker worden geretourneerd voor de huidige pagina en toekomstige weergaven

1. Gerichte inhoud die naar pagina wordt teruggestuurd, eventueel inclusief profielwaarden voor extra personalisatie.

   Gerichte inhoud op de huidige pagina wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud.

   Gerichte inhoud voor toekomstige weergaven van een toepassing van één pagina wordt in het cachegeheugen opgeslagen in de browser, zodat deze direct kan worden toegepast zonder een extra serveraanroep wanneer de weergaven worden geactiveerd. (Zie het volgende diagram voor `triggerView()` gedrag).

1. [!DNL Analytics] gegevens die van de pagina naar de [!UICONTROL Data Collection] Servers worden verzonden
1. [!DNL Target] -gegevens worden via de SDID gekoppeld aan analysegegevens en worden verwerkt in de [!DNL Analytics] -rapportageopslag. [!DNL Analytics] -gegevens kunnen vervolgens zowel in [!DNL Analytics] als [!DNL Target] via A4T-rapporten worden weergegeven.

![&#x200B; at.js 2.0 gedrag wanneer de triggerView () functie wordt gebruikt &#x200B;](assets/triggerview.png)

1. `adobe.target.triggerView()` wordt aangeroepen in de toepassing voor één pagina
1. De gerichte inhoud voor de mening wordt gelezen uit het geheime voorgeheugen

1. Gerichte inhoud wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud

1. De meldingsaanvraag wordt naar de [!DNL Target] [!UICONTROL Profile Store] verzonden om de bezoeker te tellen in de activiteiten en metriek voor verhogen
1. [!DNL Analytics] gegevens worden verzonden van het KUUUROORD naar de [!UICONTROL Data Collection] Servers

1. [!DNL Target] -gegevens worden vanuit de [!DNL Target] backend naar de [!UICONTROL Data Collection] -servers verzonden. [!DNL Target] -gegevens komen overeen met [!DNL Analytics] -gegevens via de SDID en worden verwerkt in de [!DNL Analytics] -rapportageopslag. [!DNL Analytics] -gegevens kunnen vervolgens zowel in [!DNL Analytics] als [!DNL Target] via A4T-rapporten worden weergegeven.

## Aanvullende bronnen

* [Implementeer om.js 2.0 in een toepassing van één pagina](implement-atjs-20-in-a-single-page-application.md)
* [Adobe Target-composer voor visuele ervaring gebruiken voor toepassingen van één pagina (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
