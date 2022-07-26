---
title: Hoe te om de Tokens van de Reactie en de Gebeurtenissen van de Douane bij.js te gebruiken
description: Leer hoe te om de Tokens van de Reactie en de Gebeurtenissen van de Douane te gebruiken at.js om profielinformatie van Doel aan derdesystemen te delen.
role: Developer
level: Experienced
topic: Personalization, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: d6ce5367-a453-4e6c-8545-9fa676977f04
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# De Tokens van de Reactie van het gebruik en bij.js de Gebeurtenissen van de Douane met Adobe Target

Met responsietokens en `at.js` Aangepaste gebeurtenissen kunt u profielgegevens van [!DNL Target] naar systemen van derden delen. Elk object in het profiel [!DNL Target] van de bezoeker, inclusief aangepaste profielkenmerken, geografische informatie, activiteitsdetails en ingebouwde profielen, kan worden toegevoegd aan de [!DNL Target]-reactie, waar u aangepaste JavaScript kunt gebruiken om te integreren met een derde.

>[!VIDEO](https://video.tv.adobe.com/v/23253/?quality=12)

## Hoe te om de Tokens van de Reactie en de Gebeurtenissen van de Douane bij.js te gebruiken

1. Bepaal welke gegevens u nodig hebt van [!DNL Target]
1. Zet de Tokens van de Reactie voor de gegevens aan die u door de knevel op het Opstelling ->scherm van de Tokens van de Reactie te draaien nodig hebt
1. Bepaal welke gebeurtenislistener u moet gebruiken
1. Schrijf de JavaScript die nodig is om naar de Adobe Target-gebeurtenis te luisteren, de reactietokens te lezen en te doen wat u nodig hebt voor uw integratie
1. Implementeer uw gebeurtenislistener JavaScript met behulp van een aangepaste code in Launch na de handeling Doel laden of voeg deze toe aan de sectie Bibliotheekvoettekst van at.js in het scherm Setup->Implementatie en sla een nieuw bestand at.js op
1. QA en uw integratie publiceren

## Aanvullende bronnen

* [De Experience Cloud Debugger gebruiken met Adobe Target](../troubleshooting/troubleshoot-with-the-experience-cloud-debugger.md)
* [Documentatie over responstoken](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html?lang=en)
* [Aangepaste gebeurtenisdocumentatie at.js](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js-implementation/functions-overview/atjs-custom-events.html?lang=en)
* [Gegevensleveranciers gebruiken in Adobe Target](use-data-providers-to-integrate-third-party-data.md)
