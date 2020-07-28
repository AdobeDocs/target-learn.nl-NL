---
title: Begrijpen hoe Adobe Target in.js 2.0 werkt
seo-title: Begrijpen hoe Adobe Target in.js 2.0 werkt
description: at.js 2.0 verbetert de steun van Adobe Target voor enige paginatoepassingen (SPA) en integreert met andere oplossingen van Experience Cloud. In deze video en de bijbehorende diagrammen wordt uitgelegd hoe alles samenkomt.
audience: developer
difficulty: 3
author: Daniel Wright
doc-type: implement
activity-type: technical-video
translation-type: tm+mt
source-git-commit: 37443ae4c1cdda387c8db0053201d520fa1ec224
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---


# Begrijpen hoe Adobe Target in.js 2.0 werkt

`at.js` 2.0 verbetert Adobe Target steun voor enige paginatoepassingen (SPA) en integreert met andere oplossingen van Experience Cloud. In deze video en de bijbehorende diagrammen wordt uitgelegd hoe alles samenkomt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architectuurdiagrammen

![gedrag at.js 2.0 bij het laden van de pagina](assets/pageload.png)

1. De vraag keert identiteitskaart van Experience Cloud (ECID) terug. Als de gebruiker voor authentiek wordt verklaard, synchroniseert een andere vraag de klantenidentiteitskaart

1. `at.js` De bibliotheek wordt synchroon geladen en de hoofdtekst van het document wordt verborgen (`at.js` kan ook asynchroon worden geladen met een optioneel vooraf verborgen fragment dat op de pagina is geïmplementeerd).

1. Het verzoek om het laden van de pagina wordt ingediend met inbegrip van alle gevormde parameters, ECID, SDID en klant ID.

1. Profielscripts worden uitgevoerd en toegevoegd aan de [!UICONTROL Profile Store]map. De winkel vraagt om gekwalificeerd publiek van het [!UICONTROL Audience Library] (bijvoorbeeld publiek dat wordt gedeeld vanuit [!DNL Analytics], Audience Manager, enz.). [!UICONTROL Customer Attributes] worden verzonden naar [!UICONTROL Profile Store] in een batchproces.
1. Op basis van URL, aanvraagparameters en profielgegevens [!DNL Target] bepaalt u welke Activiteiten en Ervaringen voor de huidige pagina en toekomstige weergaven moeten worden geretourneerd naar de bezoeker

1. Gerichte inhoud die naar pagina wordt teruggestuurd, eventueel inclusief profielwaarden voor extra personalisatie.

   Gerichte inhoud op de huidige pagina wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud.

   Gerichte inhoud voor toekomstige weergaven van een toepassing van één pagina wordt in het cachegeheugen opgeslagen in de browser, zodat deze direct kan worden toegepast zonder een extra serveraanroep wanneer de weergaven worden geactiveerd. (Zie het volgende diagram voor `triggerView()` gedrag).

1. [!DNL Analytics] gegevens die van de pagina naar de [!UICONTROL Data Collection] servers worden verzonden
1. [!DNL Target] gegevens worden via de SDID gekoppeld aan Analytics-gegevens en worden in de [!DNL Analytics] rapportageopslag verwerkt. [!DNL Analytics] gegevens kunnen vervolgens zowel in [!DNL Analytics] als [!DNL Target] via A4T-rapporten worden bekeken.

![at.js 2.0 gedrag wanneer de triggerView() functie wordt gebruikt](assets/triggerview.png)

1. `adobe.target.triggerView()` wordt aangeroepen in de toepassing van één pagina
1. De gerichte inhoud voor de mening wordt gelezen uit het geheime voorgeheugen

1. Gerichte inhoud wordt zo snel mogelijk zichtbaar zonder flikkering van de standaardinhoud

1. Aanvraag voor meldingen wordt naar de [!DNL Target] gebruiker verzonden [!UICONTROL Profile Store] om de bezoeker te tellen in de activiteiten en incrementele cijfers
1. [!DNL Analytics] gegevens worden verzonden van het KUUROORD naar de [!UICONTROL Data Collection] Servers

1. [!DNL Target] gegevens worden van de [!DNL Target] achterkant naar de [!UICONTROL Data Collection] Servers verzonden. [!DNL Target] gegevens worden met behulp van de SDID aan [!DNL Analytics] gegevens aangepast en worden in de [!DNL Analytics] rapportageopslag verwerkt. [!DNL Analytics] gegevens kunnen vervolgens zowel in [!DNL Analytics] als [!DNL Target] via A4T-rapporten worden bekeken.

## Aanvullende bronnen

* [Implementeer om.js 2.0 in een toepassing van één pagina](implement-atjs-20-in-a-single-page-application.md)
* [Adobe Target-composer voor visuele ervaring gebruiken voor toepassingen van één pagina (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
* [Documenten over de werking van Hoe te.js](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/at-js/how-atjs-works.html)