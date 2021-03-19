---
title: Hoe werkt at.js 2.0?
description: at.js 2.0 verbetert Adobe Target-ondersteuning voor toepassingen van één pagina (SPA) en integreert deze met andere Experience Cloud-oplossingen. In deze video en de bijbehorende diagrammen wordt uitgelegd hoe alles samenkomt.
role: Ontwikkelaar
level: Intermediair
topic: SPA, architectuur, ontwikkeling
feature: Implementatie
doc-type: technical video
kt: null
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---


# Begrijpen hoe Adobe Target in.js 2.0 werkt

`at.js` 2.0 verbetert de Adobe Target-ondersteuning voor toepassingen van één pagina (SPA) en integreert deze met andere Experience Cloud-oplossingen. In deze video en de bijbehorende diagrammen wordt uitgelegd hoe alles samenkomt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architectuurdiagrammen

![gedrag at.js 2.0 bij het laden van de pagina](assets/pageload.png)

1. De vraag keert identiteitskaart van Experience Cloud (ECID) terug. Als de gebruiker voor authentiek wordt verklaard, synchroniseert een andere vraag de klantenidentiteitskaart

1. `at.js` De bibliotheek wordt synchroon geladen en de hoofdtekst van het document verborgen (`at.js` kan ook asynchroon worden geladen met een optioneel vooraf verborgen fragment dat op de pagina is geïmplementeerd).

1. Het verzoek om het laden van de pagina wordt ingediend met inbegrip van alle gevormde parameters, ECID, SDID en klant ID.

1. De manuscripten van het profiel voeren uit en voeren in [!UICONTROL Profile Store] in. De opslag vraagt gekwalificeerd publiek van [!UICONTROL Audience Library] (b.v. publiek dat van [!DNL Analytics], Audience Manager, enz. wordt gedeeld). [!UICONTROL Customer Attributes] worden verzonden naar  [!UICONTROL Profile Store] in een batchproces.
1. Op basis van URL, aanvraagparameters en profielgegevens bepaalt [!DNL Target] welke Activiteiten en Ervaringen naar de bezoeker moeten worden geretourneerd voor de huidige pagina en toekomstige weergaven

1. Gerichte inhoud die naar pagina wordt teruggestuurd, eventueel inclusief profielwaarden voor extra personalisatie.

   Gerichte inhoud op de huidige pagina wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud.

   Gerichte inhoud voor toekomstige weergaven van een toepassing van één pagina wordt in het cachegeheugen opgeslagen in de browser, zodat deze direct kan worden toegepast zonder een extra serveraanroep wanneer de weergaven worden geactiveerd. (Zie het volgende diagram voor gedrag `triggerView()`).

1. [!DNL Analytics] gegevens die van de pagina naar de  [!UICONTROL Data Collection] servers worden verzonden
1. [!DNL Target] gegevens worden via de SDID gekoppeld aan analysegegevens en worden in de  [!DNL Analytics] rapportageopslag verwerkt. [!DNL Analytics] gegevens kunnen vervolgens zowel in  [!DNL Analytics] als  [!DNL Target] via A4T-rapporten worden weergegeven.

![at.js 2.0 gedrag wanneer de triggerView() functie wordt gebruikt](assets/triggerview.png)

1. `adobe.target.triggerView()` wordt aangeroepen in de toepassing van één pagina
1. De gerichte inhoud voor de mening wordt gelezen uit het geheime voorgeheugen

1. Gerichte inhoud wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud

1. Aanvraag voor meldingen wordt naar [!DNL Target] [!UICONTROL Profile Store] verzonden om de bezoeker te tellen in de activiteit en incrementele metriek
1. [!DNL Analytics] gegevens worden vanuit de SPA naar de  [!UICONTROL Data Collection] servers verzonden

1. [!DNL Target] gegevens worden vanaf de  [!DNL Target] achterkant naar de  [!UICONTROL Data Collection] servers verzonden. [!DNL Target] gegevens worden via de SDID aan  [!DNL Analytics] gegevens aangepast en worden in de  [!DNL Analytics] rapportageopslag verwerkt. [!DNL Analytics] gegevens kunnen vervolgens zowel in  [!DNL Analytics] als  [!DNL Target] via A4T-rapporten worden weergegeven.

## Aanvullende bronnen

* [Implementeer om.js 2.0 in een toepassing van één pagina](implement-atjs-20-in-a-single-page-application.md)
* [Adobe Target-composer voor visuele ervaring gebruiken voor toepassingen van één pagina (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
* [Documenten over de werking van Hoe te.js](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/at-js/how-atjs-works.html)