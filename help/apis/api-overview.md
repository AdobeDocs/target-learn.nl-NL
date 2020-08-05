---
title: Adobe Target API-overzicht
keywords: recommendations;adobe recommendations;premium;api;apis
description: Adobe Target Recommendations bevat een specifieke set API's waarmee u uw catalogus met aanbevolen producten en/of inhoud kunt beheren. uw aanbevelingen, algoritmen en campagnes beheren; en aanbevelingen doen in JSON-, HTML- of XML-objecten die moeten worden weergegeven in webkanalen, mobiele apparaten, e-mail, IOT en andere kanalen.
kt: null
audience: developer
doc-type: tutorial
activity: use
feature: api
topics: recommendations;adobe recommendations;premium;api;apis
solution: Adobe Target
author: Judy Kim
translation-type: tm+mt
source-git-commit: b66dbae616c9559f5d1b7bbedf2d9b383840973b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Adobe Target API-overzicht

Adobe Target API&#39;s kunnen worden gegroepeerd op type.

| API-type | Wat het u toelaat doen | Koppeling downloaden |
| --- | --- | --- |
| Beheer | Maak, wijzig en verwijder activiteiten, publiek, aanbiedingen en andere objecten (zoals [!DNL Recommendations] entiteiten, criteria, ontwerpen, enz.). De API&#39; [!DNL Recommendations] s zijn een type API voor beheerders.) | <UL><li>[Postmanverzameling voor Admin API](https://developers.adobetarget.com/api/#admin-postman-collection)</li><li>[Recommendations API Postman Collection](https://developers.adobetarget.com/api/recommendations/#section/Postman)</li></ul> |
| Aflevering | Haal geoptimaliseerde en gepersonaliseerde inhoud op van [!DNL Target] voor levering aan een eindgebruiker. | [Doellevering-API Postman-verzameling](https://developers.adobetarget.com/api/delivery-api/#section/Getting-Started/Postman-Collection) |
| Rapportage | Resultaten van exportactiviteiten en andere rapportresultaten. | Rapportage-API&#39;s worden opgenomen in de Postman-verzameling [van](https://developers.adobetarget.com/api/#admin-postman-collection)Target Admin API. |
| Profiel | Ophalen en wijzigen van gebruikersprofielen die zijn opgeslagen in Adobe Target. | [Postmanverzameling van API-doelprofiel](https://developers.adobetarget.com/api/#profiles) |

Let op het verschil tussen API&#39;s voor **beheer** (inclusief de API&#39; [!DNL Recommendations] s), waarmee u verschillende aspecten van Adobe Target kunt configureren, en API&#39;s voor **levering**, waarmee u inhoud kunt ophalen. Admin APIs vereist authentificatie, terwijl levering APIs niet.

Om Adobe Target Admin APIs te gebruiken, moet u eerst authentificatie vormen gebruikend Adobe I/O.

[Volgende &quot;Verificatie configureren&quot; >](configure-io-target-integration.md)
