---
title: Hoe te om de Leveranciers van Gegevens te gebruiken om Gegevens van de derde te integreren
description: Deze zelfstudie introduceert gebruikers aan gegevensleveranciers. Leer hoe u de functie Data Providers kunt gebruiken om gegevens van derden eenvoudig door te geven aan Adobe Target.
role: User, Developer
level: Experienced
topic: Personalization, Integrations
feature: Implementation, Integrations, APIs/SDKs
doc-type: feature video
kt: null
author: Daniel Wright
exl-id: 1892136e-14e3-4e52-8b1f-aee806d2f83a
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Gegevensleveranciers gebruiken om gegevens van derden te integreren in Adobe Target

[!UICONTROL Data Providers] is een mogelijkheid waarmee u eenvoudig gegevens van derden aan Target kunt doorgeven.  Een derde partij zou een weerdienst, een DMP, of zelfs uw eigen Webdienst kunnen zijn. Vervolgens kunt u deze gegevens gebruiken om een publiek te maken, inhoud te benoemen en het profiel van de bezoeker te verrijken.

>[!VIDEO](https://video.tv.adobe.com/v/22349/?quality=12)

## Gegevensleveranciers gebruiken

1. Implementatiedeskundige voegt code toe vóór at.js (of in de sectie Bibliotheekkoptekst van at.js) die de API-aanroep naar de derde uitvoert, de reactie parseert en opgeeft met naam/waardeparen in het antwoord dat naar [!DNL Target] moet worden verzonden.
1. at.js beheert flikkering en neemt de naam/waardeparen als douaneparameters in het globale verzoek van het Doel op.
1. Marketer maakt een publiek in de interface [!DNL Target] op basis van deze aangepaste parameters.
1. Marketer gebruikt dit publiek om ervaringen, activiteiten en metriek als doel in te stellen en om het publiek te melden.

>[!NOTE]
>
>[!UICONTROL Data Providers] vereist at.js 1.3 of hoger

## Ondersteunende materialen

* [Gegevensleveranciers implementeren in at.js en Adobe Target](implement-data-providers-to-integrate-third-party-data.md)
