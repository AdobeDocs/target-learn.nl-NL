---
title: Hoe te om de Leveranciers van Gegevens te gebruiken om Gegevens van de derde te integreren
description: Deze zelfstudie introduceert gebruikers aan Data Providers. Leer hoe u de functie Data Providers kunt gebruiken om gegevens van derden eenvoudig door te geven aan Adobe Target.
role: Bedrijfs Praktijk, Ontwikkelaar
level: Ervaren
topic: Personalisatie, integratie
feature: Implementatie, integratie, API's/SDK's
doc-type: feature video
kt: null
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '216'
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