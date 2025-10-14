---
title: Wat is de Adobe Recommendations API?
description: Deze zelfstudie begeleidt ontwikkelaars door praktische praktijk gebruikend de Aanbevelingen APIs van Adobe Target om de catalogi van Aanbevelingen en douanecriteria te vormen en te beheren, evenals het gebruiken van levering API om aanbevelingen inhoud terug te winnen.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration, Overview
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: 10f80056-fb71-4362-86bc-d161f596cb91
source-git-commit: 542ff406fc24df54a2f1b007422492341ea46507
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Adobe Recommendations API-overzicht

APIs relevant voor [!DNL Recommendations] omvat [&#x200B; admin APIs &#x200B;](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=nl-NL) die u toestaan:

* Uw catalogus met aanbevolen producten of inhoud beheren
* Uw [!DNL Recommendations] -algoritmen en -activiteiten beheren

Gebruikend [!DNL Target] [&#x200B; levering API &#x200B;](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=nl-NL) met Aanbevelingen, kunt u ook:

* U kunt aanbevelingen ophalen in JSON-, HTML- of XML-objecten, zodat deze kunnen worden weergegeven in web, mobiel, e-mail, internet van dingen (IOT) en andere kanalen.

## Beschrijving van zelfstudie

In deze zelfstudie worden ontwikkelaars door praktische handelingen geleid met behulp van de API&#39;s van [!DNL Recommendations] voor het configureren en beheren van [!DNL Recommendations] -catalogi en aangepaste criteria, en het gebruik van de API voor levering om aanbevolen inhoud op te halen. Aan het einde van deze zelfstudie kunt u het volgende doen:

* Entiteiten configureren en beheren met de API voor aanbevelingen
* Aangepaste criteria configureren en beheren met de API voor aanbevelingen
* Begrijp hoe te om Aanbevelingen met levering API te gebruiken om aanbevelingen in niet-HTML apparaten te gebruiken

## Publiek

Deze zelfstudie is bedoeld voor ontwikkelaars die geen ervaring hebben met doel-API&#39;s of aanbevelingen.

## Voorwaarden

Het gebruiken van Admin APIs van het Doel vereist [&#x200B; de authentificatieopstelling van Adobe &#x200B;](https://experienceleague.adobe.com/docs/target-dev/developer/api/configure-authentication.html?lang=nl-NL){target="_blank"}. Zorg ervoor u dit hebt gevormd voorafgaand aan het beginnen van met dit leerprogramma.

## Bronnen

Neem nota van de volgende middelen, die noodzakelijk zijn om dit leerprogramma te begrijpen en het met succes te volgen:

| Bron | Details |
| --- | --- |
| Postman | Krijg [&#x200B; Postman app &#x200B;](https://www.postman.com/downloads/) voor uw werkend systeem. Postman basic is gratis bij het maken van accounts. Hoewel Postman niet vereist is voor het gebruik van Adobe Target API&#39;s in het algemeen, maakt het API-workflows eenvoudiger en biedt Adobe Target verschillende Postman-verzamelingen om de API&#39;s van uit te voeren en te leren hoe ze werken. De rest van deze zelfstudie gaat uit van praktische kennis van Postman. Voor hulp, gelieve te verwijzen de [&#x200B; documentatie van Postman &#x200B;](https://learning.getpostman.com/). |
| Verwijzingen | Gedurende de rest van deze zelfstudie wordt aangenomen dat u bekend bent met de volgende bronnen:<UL><li>[&#x200B; Adobe I/O Github &#x200B;](https://github.com/adobeio)</li><li>[&#x200B; de documentatie van Adobe I/O van het Doel &#x200B;](https://developers.adobetarget.com/api/#introduction)</li><li>{de documentatie van 0} Aanbevelingen API [&#128279;](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

[&#x200B; daarna &quot;beheer uw Catalogus van Aanbevelingen&quot; > &#x200B;](https://experienceleague.adobe.com/docs/target-dev/developer/api/recommendations-api/manage-catalog.html?lang=nl-NL){target="_blank"}
