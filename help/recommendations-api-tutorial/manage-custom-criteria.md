---
title: Aangepaste criteria beheren
description: Dit gedeelte van de zelfstudie begeleidt ontwikkelaars bij het uitvoeren van de stappen die nodig zijn om Adobe Target API's te gebruiken voor het beheren, maken, weergeven, bewerken, ophalen en verwijderen van Adobe Target Recommendations-criteria.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: ee63bd3e-200a-4c08-b364-9f17a479033b
source-git-commit: cee2618bb92284da1f82d108a0aff0d39340a15b
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Aangepaste criteria beheren

Soms worden de algoritmen geleverd door [!DNL Recommendations] bepaalde objecten die u wilt promoten, niet kunnen weergeven. In een dergelijke situatie bieden aangepaste criteria u een manier om een specifieke reeks aanbevolen items voor een bepaald sleutelitem of een bepaalde categorie te leveren. U definieert de toewijzing tussen het hoofditem of de categorie en de aanbevolen items en importeert die toewijzing als aangepaste criteria. Dit proces wordt beschreven in het dialoogvenster [documentatie met aangepaste criteria](https://experienceleague.adobe.com/docs/target/using/recommendations/criteria/recommendations-csv.html?lang=en). Zoals vermeld in die documentatie, kunt u douanecriteria tot stand brengen uitgeven en schrappen door [!DNL Target] gebruikersinterface (UI). Maar [!DNL Target] biedt ook een set API&#39;s met aangepaste criteria waarmee u uw aangepaste criteria gedetailleerder kunt beheren.

>[!IMPORTANT]
>
>Volg deze gebruiksaanwijzing voor aangepaste criteria:
>
> Voer alle handelingen (maken, bewerken, verwijderen) voor een bepaald aangepast criterium uit met behulp van de API&#39;s, of doe alles (maken, bewerken, verwijderen) via de interface. Het beheren van uw aangepaste criteria via een combinatie van de interface en de API kan leiden tot conflicterende informatie of onverwachte resultaten. Als u bijvoorbeeld een aangepast criterium maakt in de gebruikersinterface, maar dit vervolgens bewerkt via de API, worden uw updates in de gebruikersinterface niet weergegeven, ook al wordt het op de achtergrond bijgewerkt, zoals zichtbaar via de API.

## Aangepaste criteria maken

Aangepaste criteria maken met de opdracht [Aangepaste criteria-API maken](https://developers.adobetarget.com/api/recommendations/#operation/createCriteriaCustom), is de syntaxis:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

>[!WARNING]
>
>Aangepaste criteria die zijn gemaakt met de Create Custom Criteria API (Aangepaste criteria maken), zoals in deze exercitie wordt beschreven, worden weergegeven in de gebruikersinterface, waar ze blijven bestaan. U kunt ze niet bewerken of verwijderen uit de gebruikersinterface. U kunt ze bewerken of verwijderen **via API**, maar in beide gevallen blijven ze in de [!DNL Target] UI. Als u de optie voor het bewerken of verwijderen van de interface wilt behouden, maakt u de aangepaste criteria met behulp van de interface per [de documentatie](https://experienceleague.adobe.com/docs/target/using/recommendations/criteria/recommendations-csv.html?lang=en)in plaats van de API Aangepaste criteria maken te gebruiken.

Ga alleen verder met deze zelfstudie nadat u de bovenstaande waarschuwing hebt gelezen en u vertrouwd bent met het maken van nieuwe aangepaste criteria die vervolgens niet uit de gebruikersinterface kunnen worden verwijderd.

1. Verifiëren `TENANT_ID` en `API_KEY` for **Aangepaste criteria maken** verwijzen naar de eerder vastgestelde Postman-omgevingsvariabelen. Gebruik de onderstaande afbeelding om deze te vergelijken.

   ![CreateCustomCriteria1](assets/CreateCustomCriteria1.png)

2. Voeg uw **Lichaam** als **ruw** JSON die de locatie van uw CSV-bestand met aangepaste criteria definieert. Gebruik het voorbeeld in het dialoogvenster [Aangepaste criteria-API maken](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom) documentatie als sjabloon, die uw `environmentId` en andere waarden indien nodig. Voor dit voorbeeld, gebruiken wij LAST_PURCHASED als sleutel.

   ![CreateCustomCriteria2](assets/CreateCustomCriteria2.png)

3. Verzend het verzoek en bekijk de reactie, die de details van de douanecriteria bevat u enkel creeerde.

   ![CreateCustomCriteria3](assets/CreateCustomCriteria3.png)

4. Als je wilt controleren of je aangepaste criteria zijn gemaakt, navigeer dan in Adobe Target naar **[!UICONTROL Recommendations]>[!UICONTROL Criteria]** en zoek uw criteria op naam of gebruik de **Aangepaste criteria-API weergeven** in de volgende stap.

   ![CreateCustomCriteria4](assets/CreateCustomCriteria4.png)

In dit geval hebben we een fout. Laten we de fout onderzoeken door de aangepaste criteria nauwkeuriger te bekijken met de **Aangepaste criteria-API weergeven**.

## Aangepaste criteria weergeven

Als u een lijst met al uw aangepaste criteria wilt ophalen, gebruikt u de opdracht [Aangepaste criteria-API weergeven](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom). De syntaxis is:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

1. Verifiëren `TENANT_ID` en `API_KEY` als voorheen, en verzend het verzoek. Let in de reactie op de id van de aangepaste criteria en op details met betrekking tot het eerder vermelde foutbericht.
   ![ListCustomCriteria](assets/ListCustomCriteria.png)

In dit geval is de fout opgetreden omdat de serverinformatie onjuist is, wat betekent [!DNL Target] heeft geen toegang tot het CSV-bestand dat de definitie van aangepaste criteria bevat. Bewerk de aangepaste criteria om dit te corrigeren.

## Aangepaste criteria bewerken

Als u de details van een definitie voor aangepaste criteria wilt wijzigen, gebruikt u de optie [Aangepaste criteria-API bewerken](https://developers.adobetarget.com/api/recommendations/#operation/updateCriteriaCustom). De syntaxis is:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Verifiëren `TENANT_ID` en `API_KEY`, zoals eerder.
   ![EditCustomCriteria1](assets/EditCustomCriteria1.png)

1. Geef de criteria-id op van de (enkele) aangepaste criteria die u wilt bewerken.
   ![EditCustomCriteria2](assets/EditCustomCriteria2.png)

1. Geef in het body-gedeelte bijgewerkte JSON de juiste serverinformatie. (Geef voor deze stap FTP-toegang op tot een server die u kunt openen.)
   ![EditCustomCriteria3](assets/EditCustomCriteria3.png)

1. Verzend de aanvraag en noteer het antwoord.
   ![EditCustomCriteria4](assets/EditCustomCriteria4.png)

Laten we het succes van de bijgewerkte aangepaste criteria controleren met de opdracht **API voor aangepaste criteria ophalen**.

## Aangepaste criteria ophalen

Als u de details van aangepaste criteria voor specifieke aangepaste criteria wilt bekijken, gebruikt u de opdracht [API voor aangepaste criteria ophalen](https://developers.adobetarget.com/api/recommendations/#operation/getCriteriaCustom). De syntaxis is:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geef de criteria-id op van de aangepaste criteria waarvan u de details wilt ophalen. Verzend het verzoek en bekijk het antwoord.
   ![GetCustomCriteria.png](assets/GetCustomCriteria.png)
1. Verifieer succes. (Controleer in ons geval of er geen verdere FTP-fouten zijn.)
   ![GetCustomCriteria1.png](assets/GetCustomCriteria1.png)
1. (Optioneel) Controleer of de update correct wordt weergegeven in de gebruikersinterface.
   ![GetCustomCriteria2.png](assets/GetCustomCriteria2.png)

## Aangepaste criteria verwijderen

Verwijder uw aangepaste criteria met de eerder vermelde criteria aan de hand van de [Aangepaste criteria-API verwijderen](https://developers.adobetarget.com/api/recommendations/#operation/deleteCriteriaCustom). De syntaxis is:

`DELETE https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geef de criteria-id op van de (enkele) aangepaste criteria die u wilt verwijderen. Klikken **Verzenden**.
   ![DeleteCustomCriteria1](assets/DeleteCustomCriteria1.png)

1. Controleer of de criteria zijn verwijderd met Aangepaste criteria ophalen.
   ![DeleteCustomCriteria2](assets/DeleteCustomCriteria2.png)
In dit geval geeft de verwachte fout van 404 aan dat de verwijderde criteria niet kunnen worden gevonden.

>[!NOTE]
>Ter herinnering: de criteria worden niet verwijderd uit de [!DNL Target] UI, ook al is deze verwijderd, omdat deze is gemaakt met de API Aangepaste criteria maken.

Gefeliciteerd! U kunt nu details over aangepaste criteria maken, weergeven, bewerken, verwijderen en ophalen met de opdracht [!DNL Recommendations] API. In de volgende sectie gebruikt u de opdracht [!DNL Target] Leverings-API om aanbevelingen op te halen.

[Next &quot;Fetch Recommendations with the Server-side Delivery API&quot; >](https://developer.adobe.com/target/before-administer/recs-api/fetch-recs-server-side-delivery-api/){target=&quot;_blank&quot;}
