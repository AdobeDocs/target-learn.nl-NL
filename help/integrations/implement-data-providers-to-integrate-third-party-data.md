---
title: Hoe te om de Leveranciers van Gegevens uit te voeren om Gegevens van de derde te integreren
description: Deze zelfstudie bevat implementatiedetails en voorbeelden van hoe u de functie Adobe Target-gegevensleveranciers kunt gebruiken om gegevens van externe gegevensleveranciers op te halen en door te geven in de aanvraag Doel.
role: Ontwikkelaar
level: Ervaren
topic: Personalisatie, integratie
feature: Implementatie, integratie, API's/SDK's
doc-type: technical video
kt: null
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# [!UICONTROL Data Providers] implementeren om gegevens van derden te integreren in Adobe Target

Implementatiedetails en voorbeelden van hoe u de Adobe Target-functie [!UICONTROL Data Providers] kunt gebruiken om gegevens van externe gegevensproviders op te halen en door te geven in de aanvraag Doel.

>[!NOTE]
>
>[!UICONTROL Data Providers] vereist  `at.js` 1.3 of hoger

## Implementeer de basiscomponenten van gegevensleveranciers

>[!VIDEO](https://video.tv.adobe.com/v/22348/?quality=12)

Een kort overzicht van de basiscomponenten van een `dataProvider` en hoe te om uw code in de juiste orde te krijgen.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[https://target.enablementadobe.com/data-providers/simple.html](https://target.enablementadobe.com/data-providers/simple.html)

## Integreren met een externe API

>[!VIDEO](https://video.tv.adobe.com/v/22345/)

Een realistischer voorbeeld, die een weer API integreren.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[https://target.enablementadobe.com/data-providers/3rdparty.html](https://target.enablementadobe.com/data-providers/3rdparty.html)

## Integreren met meerdere providers

>[!VIDEO](https://video.tv.adobe.com/v/22346/)

Hoe te om gegevens van veelvoudige leveranciers in uw globale [!DNL Target] verzoek op te nemen.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[https://target.enablementadobe.com/data-providers/combined.html](https://target.enablementadobe.com/data-providers/combined.html)

## Effect paginabelasting minimaliseren

>[!VIDEO](https://video.tv.adobe.com/v/22347/)

Minimaliseer de invloed op de laadtijd van de pagina door gegevens in een voorwerp van de zittingsopslag op te slaan. U kunt de waarden ook doorgeven als profielparameters met behulp van het voorvoegsel `profile.` en ze gewoon doorgeven in het eerste [!DNL Target]-verzoek van de sessie. U kunt echter alleen vijftig profielparameters doorgeven per aanvraag.

Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt: [https://target.enablementadobe.com/data-providers/reducedCalls.html](https://target.enablementadobe.com/data-providers/reducedCalls.html)

## Ondersteunende materialen

* [Gegevensleveranciers gebruiken met Adobe Target](use-data-providers-to-integrate-third-party-data.md)

* [Documentatie gegevensleveranciers](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/targetgobalsettings.html#data-providers)