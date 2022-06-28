---
title: Recommendations-catalogus beheren met API's
description: Dit gedeelte van de zelfstudie begeleidt ontwikkelaars bij het doorlopen van de stappen die nodig zijn om Adobe Target API's te gebruiken voor het maken, bijwerken, opslaan, ophalen en verwijderen van entiteiten in uw Recommendations-catalogus.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: 8060b69b-e8e5-4fe7-895f-742410d8ed45
source-git-commit: cee2618bb92284da1f82d108a0aff0d39340a15b
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 1%

---

# Uw [!DNL Recommendations] Catalogus met API&#39;s

U hebt nu geleerd hoe u een toegangstoken kunt genereren met behulp van de JWT-verificatiestroom en zo de Adobe Target Admin API&#39;s met Adobe I/O kunt gebruiken.

U kunt de [Recommendations API&#39;s](https://developers.adobetarget.com/api/recommendations/) om items toe te voegen, bij te werken of te verwijderen uit uw catalogus met aanbevelingen. Net als bij de andere Adobe Target Admin API&#39;s, [!DNL Recommendations] API&#39;s vereisen verificatie.

>[!TIP]
>
>Verzend de **[!UICONTROL IMS: JWT Generate + Auth via User Token]** verzoek wanneer u uw toegangstoken voor authentificatie moet verfrissen, aangezien het na 24 uren verloopt. Zie [Adobe API-verificatie configureren](https://developer.adobe.com/target/before-administer/configure-authentication/){target=&quot;_blank&quot;} voor instructies.

![JWT3ff](assets/configure-io-target-jwt3ff.png)

>[!NOTE]
>
>Haal voordat u verdergaat de [Recommendations Postman-collectie](https://developers.adobetarget.com/api/recommendations/#section/Postman).

## Items maken en bijwerken met de API Entiteiten opslaan

Om uw [!DNL Recommendations] productdatabase die de API gebruikt in plaats van een CSV-productfeed of [!DNL Target] aanvragen om op productpagina&#39;s te starten, gebruikt u de [Entiteiten-API opslaan](https://developers.adobetarget.com/api/recommendations/#operation/saveEntities). Met deze aanvraag wordt een item in één keer toegevoegd of bijgewerkt [!DNL Target] milieu. De syntaxis is:

```
POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities
```

Bijvoorbeeld, sparen Entiteiten kunnen worden gebruikt om punten bij te werken wanneer bepaalde drempels worden voldaan-zoals drempels voor inventaris of prijs-om die punten te markeren en hen te verhinderen worden geadviseerd.

1. Navigeren naar **[!DNL Target]> [!UICONTROL Setup] > [!UICONTROL Hosts] >[!UICONTROL Environments]** om [!DNL Target] Omgeving-id waarin u een item wilt toevoegen of bijwerken.

   ![SaveEntities1](assets/SaveEntities01.png)

2. Verifiëren `TENANT_ID` en `API_KEY` verwijzen naar de eerder vastgestelde Postman-omgevingsvariabelen. Gebruik de onderstaande afbeelding om deze te vergelijken. Wijzig zo nodig de koppen en het pad in de API-aanvraag, zodat deze overeenkomen met de waarden in de onderstaande afbeelding.

   ![SaveEntities3](assets/SaveEntities03.png)

3. Voer uw JSON in als **ruw** code in de **Lichaam**. Vergeet niet uw milieu-id op te geven met de `environment` variabele. (In het onderstaande voorbeeld is de milieu-id 6781.)

   ![SaveEntities4.png](assets/SaveEntities04.png)

   >!![NOTE]
   Hieronder ziet u een voorbeeld van JSON waarmee entiteit.id kit2001 wordt toegevoegd aan de bijbehorende entiteitswaarden voor een product van Toaster Oven, in omgeving 6781.

   ```
      {
      "entities": [{
              "name": "Toaster Oven",
              "id": "kit2001",
              "environment": 6781,
              "categories": [
                  "housewares:appliances"
              ],
              "attributes": {
                  "inventory": 77,
                  "margin": 23,
                  "message": "crashing helicopter",
                  "pageUrl": "www.foobar.foo.com/helicopter.html",
                  "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                  "value": 19.2
              }
          }]
      }
   ```

4. Klikken **Verzenden**. U dient het volgende antwoord te ontvangen.

   ![SaveEntities5.png](assets/SaveEntities05.png)

Het JSON-object kan worden geschaald om meerdere producten te verzenden. In deze JSON worden bijvoorbeeld twee entiteiten opgegeven.

```
    {
        "entities": [{
                "name": "Toaster Oven",
                "id": "kit2001",
                "environment": 6781,
                "categories": [
                    "housewares:appliances"
                ],
                "attributes": {
                    "inventory": 89,
                    "margin": 11,
                    "message": "Toaster Oven",
                    "pageUrl": "www.foobar.foo.com/helicopter.html",
                    "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                    "value": 102.5
                }
            },
            {
                "name": "Blender",
                "id": "kit2002",
                "environment": 6781,
                "categories": [
                    "housewares:appliances"
                ],
                "attributes": {
                    "inventory": 36,
                    "margin": 5,
                    "message": "Blender",
                    "pageUrl": "www.foobar.foo.com/helicopter.html",
                    "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                    "value": 54.5
                }
            }
        ]
    }
```

1. Nu is het jouw beurt! Gebruik de **Entiteiten opslaan** API om de volgende items aan uw catalogus toe te voegen. Gebruik het JSON-voorbeeld hierboven als beginpunt. (U moet de JSON uitbreiden tot extra entiteiten.)

   ![SaveEntities6.png](assets/SaveEntities06.png)

Die laatste twee items horen niet thuis. Laten we ze controleren met de **Entiteit ophalen** API, en indien nodig, schrapt hen gebruikend **Entiteiten verwijderen** API.

## Itemdetails ophalen met de Get Entiteit API

Om de details van een bestaand punt terug te winnen, gebruik [EntiteitsAPI ophalen](https://developers.adobetarget.com/api/recommendations/#operation/getEntity). De syntaxis is:

```
GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities/[entity.id]
```

De gegevens van de entiteit kunnen slechts voor één enkele entiteit tegelijkertijd worden teruggewonnen. Met Entiteit ophalen kunt u controleren of er updates zijn gemaakt in de catalogus zoals u had verwacht, of kunt u de inhoud van de catalogus op een andere manier controleren.

1. Geef in de API-aanvraag de id van de entiteit op met de variabele `entityId`. In het volgende voorbeeld worden gegevens geretourneerd voor de entiteit waarvan de entiteitId=kit2004.

   ![GetEntiteit1](assets/GetEntity1.png)

2. Verifiëren `TENANT_ID` en `API_KEY` verwijzen naar de eerder vastgestelde Postman-omgevingsvariabelen. Gebruik de onderstaande afbeelding om deze te vergelijken. Wijzig zo nodig de koppen en het pad in de API-aanvraag, zodat deze overeenkomen met de waarden in de onderstaande afbeelding.

   ![GetEntiteit2](assets/GetEntity2.png)

3. Verzend de aanvraag.

   ![GetEntiteit3](assets/GetEntity3.png)
Als er een fout optreedt die aangeeft dat de entiteit niet is gevonden, zoals in het bovenstaande voorbeeld wordt getoond, controleert u of u het verzoek naar de juiste instantie verzendt [!DNL Target] milieu.

   >[!NOTE]
   Als geen milieu uitdrukkelijk wordt gespecificeerd, krijg de pogingen van de Entiteit om de entiteit van uw te krijgen [standaardomgeving](https://experienceleague.adobe.com/docs/target/using/administer/hosts.html?lang=en) alleen. Als u van om het even welke milieu buiten uw standaardomgeving wenst te trekken, moet u milieu-identiteitskaart specificeren

4. Voeg zo nodig de `environmentId` en de aanvraag opnieuw verzenden.

   ![GetEntiteit4](assets/GetEntity4.png)

5. Nog een verzenden **Entiteit ophalen** verzoek, dit keer om de entiteit te inspecteren waarvan entiteitId=kit2005.

   ![GetEntiteit5](assets/GetEntity5.png)

Stel dat u besluit dat deze entiteiten uit de catalogus moeten worden verwijderd. Laten we de **Entiteiten verwijderen** API.

## Items verwijderen met de API Entiteiten verwijderen

Als u items uit uw catalogus wilt verwijderen, gebruikt u de [Entiteiten-API verwijderen](https://developers.adobetarget.com/api/recommendations/#operation/deleteEntities). De syntaxis is:

```
DELETE https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities?ids=[comma-delimited-entity-ids]&environment=[environmentId]
```

>[!WARNING]
Deze API verwijdert entiteiten waarnaar wordt verwezen door id&#39;s die u opgeeft.
Als er geen id&#39;s voor entiteiten zijn opgegeven, worden alle entiteiten in de opgegeven omgeving verwijderd. Als er geen milieu-id is opgegeven, worden entiteiten uit alle omgevingen verwijderd. Wees voorzichtig!

1. Navigeren naar **[!DNL Target]> [!UICONTROL Setup] > [!UICONTROL Hosts] >[!UICONTROL Environments]** om [!DNL Target] Omgeving-id waaruit u items wilt verwijderen.

   ![DeleteEntities1](assets/SaveEntities01.png)

2. Geef in de API-aanvraag de entiteit-id&#39;s op van de entiteiten die u wilt verwijderen met behulp van de syntaxis `&ids=[comma-delimited-entity-ids]` (een queryparameter). Wanneer u meerdere entiteiten verwijdert, scheidt u de id&#39;s met komma&#39;s.

   ![DeleteEntities2](assets/DeleteEntities2.png)

3. De milieu-id opgeven met de syntaxis `&environment=[environmentId]`anders worden entiteiten in alle omgevingen verwijderd.

   ![DeleteEntities3](assets/DeleteEntities3.png)

4. Verifiëren `TENANT_ID` en `API_KEY` verwijzen naar de eerder vastgestelde Postman-omgevingsvariabelen. Gebruik de onderstaande afbeelding om deze te vergelijken. Wijzig zo nodig de koppen en het pad in de API-aanvraag, zodat deze overeenkomen met de waarden in de onderstaande afbeelding.

   ![DeleteEntities4](assets/DeleteEntities4.png)

5. Verzend de aanvraag.

   ![DeleteEntities5](assets/DeleteEntities5.png)

6. De resultaten verifiëren met **Entiteit ophalen**, die nu moet aangeven welke verwijderde entiteiten niet kunnen worden gevonden.

   ![Entiteiten verwijderen6](assets/DeleteEntities6.png)

   ![Entiteiten verwijderen6](assets/DeleteEntities7.png)

Gefeliciteerd! U kunt nu de opdracht [!DNL Recommendations] API&#39;s voor het maken, bijwerken, verwijderen en ophalen van gegevens over de entiteiten in uw catalogus. In de volgende sectie leert u hoe u aangepaste criteria kunt beheren.

[Volgende &quot;Aangepaste criteria beheren&quot; >](https://developer.adobe.com/target/before-administer/recs-api/manage-custom-criteria/){target=&quot;_blank&quot;}
