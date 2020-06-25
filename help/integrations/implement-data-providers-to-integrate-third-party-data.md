---
title: Gegevensleveranciers implementeren om gegevens van derden te integreren in Adobe Target
seo-title: Gegevensleveranciers implementeren om gegevens van derden te integreren in Adobe Target
description: Implementatiedetails en voorbeelden van het gebruik van de functie Adobe Target Data Providers om gegevens van externe gegevensleveranciers op te halen en door te geven in de Target-aanvraag.
audience: developer
difficulty: 5
author: Daniel Wright
doc-type: implement
activity-type: technical-video
translation-type: tm+mt
source-git-commit: 37443ae4c1cdda387c8db0053201d520fa1ec224
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Implementeren [!UICONTROL Data Providers] om gegevens van derden te integreren in Adobe Target

Implementatiedetails en voorbeelden van hoe u de Adobe Target- [!UICONTROL Data Providers] functie kunt gebruiken om gegevens van externe gegevensleveranciers op te halen en door te geven in de Target-aanvraag.

>[!NOTE]
>
>[!UICONTROL Data Providers] vereist `at.js` 1.3 of hoger

## Implementeer de basiscomponenten van gegevensleveranciers

>[!VIDEO](https://video.tv.adobe.com/v/22348/?quality=12)

Een kort overzicht van de basiscomponenten van een code `dataProvider` en hoe u de code in de juiste volgorde kunt krijgen.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[https://target.enablementadobe.com/data-providers/simple.html](https://target.enablementadobe.com/data-providers/simple.html)

## Integreren met een externe API

>[!VIDEO](https://video.tv.adobe.com/v/22345/)

Een realistischer voorbeeld, die een weer API integreren.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[https://target.enablementadobe.com/data-providers/3rdparty.html](https://target.enablementadobe.com/data-providers/3rdparty.html)

## Integreren met meerdere providers

>[!VIDEO](https://video.tv.adobe.com/v/22346/)

Hoe te om gegevens van veelvoudige leveranciers in uw globaal [!DNL Target] verzoek op te nemen.\
Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt:
[https://target.enablementadobe.com/data-providers/combined.html](https://target.enablementadobe.com/data-providers/combined.html)

## Effect paginabelasting minimaliseren

>[!VIDEO](https://video.tv.adobe.com/v/22347/)

Minimaliseer de invloed op de laadtijd van de pagina door gegevens in een voorwerp van de zittingsopslag op te slaan. U kunt de waarden ook doorgeven als profielparameters met behulp van het `profile.` voorvoegsel en deze alleen doorgeven in het eerste [!DNL Target] verzoek van de sessie. U kunt echter alleen vijftig profielparameters doorgeven per aanvraag.

Hier vindt u een werkvoorbeeld met de code die in de video wordt gebruikt: [https://target.enablementadobe.com/data-providers/reducedCalls.html](https://target.enablementadobe.com/data-providers/reducedCalls.html)

## Ondersteunende materialen

* [Gegevensleveranciers gebruiken met Adobe Target](use-data-providers-to-integrate-third-party-data.md)

* [Documentatie gegevensleveranciers](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/targetgobalsettings.html#data-providers)