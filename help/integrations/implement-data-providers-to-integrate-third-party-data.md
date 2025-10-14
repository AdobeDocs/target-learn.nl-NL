---
title: Hoe te om de Leveranciers van Gegevens uit te voeren om Gegevens van de derde te integreren
description: Deze zelfstudie bevat implementatiedetails en voorbeelden van hoe u de functie Adobe Target-gegevensleveranciers kunt gebruiken om gegevens van externe gegevensleveranciers op te halen en door te geven in de aanvraag Doel.
role: Developer
level: Experienced
topic: Personalization, Integrations
feature: Implementation, Integrations, APIs/SDKs
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: fcf6d1a8-e2a7-41ce-9c1c-02985b7afb5a
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Implementeren [!UICONTROL Data Providers] om gegevens van derden te integreren in Adobe Target

Implementatiedetails en voorbeelden van hoe u de Adobe Target-functie [!UICONTROL Data Providers] kunt gebruiken om gegevens van externe gegevensproviders op te halen en door te geven in de aanvraag Doel.

>[!NOTE]
>
>[!UICONTROL Data Providers] vereist `at.js` 1.3 of hoger

## Implementeer de basiscomponenten van gegevensleveranciers

>[!VIDEO](https://video.tv.adobe.com/v/22348/?quality=12)

Een kort overzicht van de basiscomponenten van een `dataProvider` en hoe u de code in de juiste volgorde kunt krijgen.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[&#x200B; https://target.enablementadobe.com/data-providers/simple.html](https://target.enablementadobe.com/data-providers/simple.html)

## Integreren met een externe API

>[!VIDEO](https://video.tv.adobe.com/v/22345/)

Een realistischer voorbeeld, die een weer API integreren.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[&#x200B; https://target.enablementadobe.com/data-providers/3rdparty.html](https://target.enablementadobe.com/data-providers/3rdparty.html)

## Integreren met meerdere providers

>[!VIDEO](https://video.tv.adobe.com/v/22346/)

Hoe te om gegevens van veelvoudige leveranciers in uw globale [!DNL Target] verzoek op te nemen.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[&#x200B; https://target.enablementadobe.com/data-providers/combined.html](https://target.enablementadobe.com/data-providers/combined.html)

## Effect paginabelasting minimaliseren

>[!VIDEO](https://video.tv.adobe.com/v/22347/)

Minimaliseer de invloed op de laadtijd van de pagina door gegevens in een voorwerp van de zittingsopslag op te slaan. U kunt de waarden ook doorgeven als profielparameters met behulp van het voorvoegsel `profile.` en ze gewoon doorgeven in het eerste [!DNL Target] -verzoek van de sessie. U kunt echter alleen vijftig profielparameters doorgeven per aanvraag.

Een werkend voorbeeld met de code die in de video wordt gebruikt kan hier worden gevonden: [&#x200B; https://target.enablementadobe.com/data-providers/reducedCalls.html &#x200B;](https://target.enablementadobe.com/data-providers/reducedCalls.html)

## Ondersteunende materialen

* [&#x200B; Leveranciers van Gegevens van het Gebruik met Adobe Target &#x200B;](use-data-providers-to-integrate-third-party-data.md)
