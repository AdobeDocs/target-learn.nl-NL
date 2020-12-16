---
title: Gegevensleveranciers gebruiken om gegevens van derden te integreren in Adobe Target
seo-title: Gegevensleveranciers gebruiken om gegevens van derden te integreren in Adobe Target
description: Gegevensleveranciers zijn een mogelijkheid waarmee u gegevens van derden eenvoudig aan Doel kunt doorgeven.  Een derde partij zou een weerdienst, een DMP, of zelfs uw eigen Webdienst kunnen zijn. Vervolgens kunt u deze gegevens gebruiken om een publiek te maken, inhoud te benoemen en het profiel van de bezoeker te verrijken.
audience: marketer
difficulty: 5
author: Daniel Wright
doc-type: use
activity-type: feature-video
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Gegevensleveranciers gebruiken om gegevens van derden te integreren in Adobe Target

[!UICONTROL Data Providers] is een mogelijkheid waarmee u eenvoudig gegevens van derden aan Target kunt doorgeven.  Een derde partij zou een weerdienst, een DMP, of zelfs uw eigen Webdienst kunnen zijn. Vervolgens kunt u deze gegevens gebruiken om een publiek te maken, inhoud te benoemen en het profiel van de bezoeker te verrijken.

>[!VIDEO](https://video.tv.adobe.com/v/22349/?quality=12)

## Gegevensleveranciers gebruiken

1. De deskundige van de implementatie voegt code vóór at.js (of in de sectie van de Kopbal van de Bibliotheek van at.js) toe die de API vraag aan de derde maakt, de reactie ontleedt en met naam/waardeparen van de reactie specificeert om naar [!DNL Target] te verzenden.
1. at.js beheert flikkering en neemt de naam/waardeparen als douaneparameters in het globale verzoek van het Doel op.
1. Marketer bouwt publiek in de [!DNL Target] interface die op deze douaneparameters wordt gebaseerd.
1. Marketer gebruikt dit publiek om ervaringen, activiteiten en metriek als doel in te stellen en om het publiek te melden.

>[!NOTE]
>
>[!UICONTROL Data Providers] vereist at.js 1.3 of hoger

## Ondersteunende materialen

* [Gegevensleveranciers implementeren in at.js en Adobe Target](implement-data-providers-to-integrate-third-party-data.md)
* [Documentatie gegevensleveranciers](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/targetgobalsettings.html#data-providers)