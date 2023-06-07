---
title: Hoe werkt at.js 2.0?
description: at.js 2.0 verbetert Adobe Target-ondersteuning voor toepassingen van één pagina (SPA) en integreert deze met andere Experience Cloud-oplossingen. In deze video en de bijbehorende diagrammen wordt uitgelegd hoe alles samenkomt.
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 7f037665-88a7-469c-8df5-c82cb0f65382
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Begrijpen hoe Adobe Target in.js 2.0 werkt

`at.js` 2.0 verbetert de Adobe Target-ondersteuning voor toepassingen van één pagina (SPA) en integreert deze met andere Experience Cloud-oplossingen. In deze video en de bijbehorende diagrammen wordt uitgelegd hoe alles samenkomt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architectuurdiagrammen

![gedrag at.js 2.0 bij het laden van de pagina](assets/pageload.png)

1. De vraag keert identiteitskaart van Experience Cloud (ECID) terug. Als de gebruiker voor authentiek wordt verklaard, synchroniseert een andere vraag de klantenidentiteitskaart

1. `at.js` bibliotheek wordt synchroon geladen en de hoofdtekst van het document verborgen (`at.js` kan ook asynchroon worden geladen met een optioneel vooraf verborgen fragment dat op de pagina is geïmplementeerd).

1. Het verzoek om het laden van de pagina wordt ingediend met inbegrip van alle gevormde parameters, ECID, SDID en klant ID.

1. Profielscripts worden uitgevoerd en toegevoegd aan de [!UICONTROL Profile Store]. De winkel vraagt een gekwalificeerd publiek aan via [!UICONTROL Audience Library] (bv. publiek dat wordt gedeeld vanuit [!DNL Analytics], Audience Manager, enz.). [!UICONTROL Customer Attributes] worden verzonden naar [!UICONTROL Profile Store] in een batchproces.
1. Gebaseerd op URL, verzoekparameters, en profielgegevens, [!DNL Target] besluit welke Activiteiten en Ervaringen voor de huidige pagina en toekomstige weergaven naar de bezoeker moeten terugkeren

1. Gerichte inhoud die naar pagina wordt teruggestuurd, eventueel inclusief profielwaarden voor extra personalisatie.

   Gerichte inhoud op de huidige pagina wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud.

   Gerichte inhoud voor toekomstige weergaven van een toepassing van één pagina wordt in het cachegeheugen opgeslagen in de browser, zodat deze direct kan worden toegepast zonder een extra serveraanroep wanneer de weergaven worden geactiveerd. (Zie het volgende diagram voor `triggerView()` gedrag).

1. [!DNL Analytics] gegevens die van de pagina naar de [!UICONTROL Data Collection] Servers
1. [!DNL Target] gegevens worden via de SDID gekoppeld aan analysegegevens en worden verwerkt in de [!DNL Analytics] rapporteringsopslag. [!DNL Analytics] gegevens kunnen vervolgens in beide worden weergegeven [!DNL Analytics] en [!DNL Target] via A4T-rapporten.

![at.js 2.0 gedrag wanneer de triggerView() functie wordt gebruikt](assets/triggerview.png)

1. `adobe.target.triggerView()` wordt aangeroepen in de toepassing van één pagina
1. De gerichte inhoud voor de mening wordt gelezen uit het geheime voorgeheugen

1. Gerichte inhoud wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud

1. Aanmelding wordt verzonden naar de [!DNL Target] [!UICONTROL Profile Store] om de bezoeker te tellen in de activiteit en verhogingsmetriek
1. [!DNL Analytics] gegevens worden van de SPA naar de [!UICONTROL Data Collection] Servers

1. [!DNL Target] gegevens worden verzonden door de [!DNL Target] de [!UICONTROL Data Collection] Servers. [!DNL Target] gegevens komen overeen met [!DNL Analytics] gegevens via de SDID en worden verwerkt in de [!DNL Analytics] rapporteringsopslag. [!DNL Analytics] gegevens kunnen vervolgens in beide worden weergegeven [!DNL Analytics] en [!DNL Target] via A4T-rapporten.

## Aanvullende bronnen

* [Implementeer om.js 2.0 in een toepassing van één pagina](implement-atjs-20-in-a-single-page-application.md)
* [Adobe Target-composer voor visuele ervaring gebruiken voor toepassingen van één pagina (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
