---
title: Aangepaste criteria beheren
description: Dit gedeelte van de zelfstudie begeleidt ontwikkelaars bij het uitvoeren van de stappen die nodig zijn om Adobe Target API's te gebruiken voor het beheren, maken, weergeven, bewerken, ophalen en verwijderen van Adobe Target Recommendations-criteria.
role: Ontwikkelaar
level: Intermediair
topic: Personalisatie, administratie, integratie, ontwikkeling
feature: API's/SDK's, Recommendations, Beheer en Configuratie
doc-type: tutorial
kt: 3815
thumbnail: null
author: Judy Kim
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 0%

---


# Aangepaste criteria beheren

Soms kunnen de algoritmen die door [!DNL Recommendations] worden geleverd, bepaalde items die u wilt promoten, niet oppervlakkig weergeven. In een dergelijke situatie bieden aangepaste criteria u een manier om een specifieke reeks aanbevolen items voor een bepaald sleutelitem of een bepaalde categorie te leveren. U definieert de toewijzing tussen het hoofditem of de categorie en de aanbevolen items en importeert die toewijzing als aangepaste criteria. Dit proces wordt beschreven in [de documentatie van de douanecriteria](https://docs.adobe.com/content/help/en/target/using/recommendations/criteria/recommendations-csv.html). Zoals vermeld in die documentatie, kunt u douanecriteria tot stand brengen uitgeven en schrappen door [!DNL Target] gebruikersinterface (UI). [!DNL Target] biedt echter ook een set API&#39;s met aangepaste criteria waarmee u uw aangepaste criteria gedetailleerder kunt beheren.

>[!IMPORTANT]
>
>Volg deze gebruiksaanwijzing voor aangepaste criteria:
>
> Voer alle handelingen (maken, bewerken, verwijderen) voor een bepaald aangepast criterium uit met behulp van de API&#39;s, of doe alles (maken, bewerken, verwijderen) via de interface. Het beheren van uw aangepaste criteria via een combinatie van de interface en de API kan leiden tot conflicterende informatie of onverwachte resultaten. Als u bijvoorbeeld een aangepast criterium maakt in de gebruikersinterface, maar dit vervolgens bewerkt via de API, worden uw updates in de gebruikersinterface niet weergegeven, ook al wordt het op de achtergrond bijgewerkt, zoals zichtbaar via de API.

## Aangepaste criteria maken

Als u aangepaste criteria wilt maken met de [Aangepaste criteria-API](https://developers.adobetarget.com/api/recommendations/#operation/createCriteriaCustom) maken, is de syntaxis:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

>[!WARNING]
>
>Aangepaste criteria die zijn gemaakt met de Create Custom Criteria API (Aangepaste criteria maken), zoals in deze exercitie wordt beschreven, worden weergegeven in de gebruikersinterface, waar ze blijven bestaan. U kunt ze niet bewerken of verwijderen uit de gebruikersinterface. U kunt ze **via API** bewerken of verwijderen, maar in beide gevallen blijven ze wel zichtbaar in de gebruikersinterface van [!DNL Target]. Als u de optie voor het bewerken of verwijderen van de interface wilt behouden, maakt u aangepaste criteria met de UI per [de documentatie](https://docs.adobe.com/content/help/en/target/using/recommendations/criteria/recommendations-csv.html) in plaats van de API Aangepaste criteria maken.

Ga alleen verder met deze zelfstudie nadat u de bovenstaande waarschuwing hebt gelezen en u vertrouwd bent met het maken van nieuwe aangepaste criteria die vervolgens niet uit de gebruikersinterface kunnen worden verwijderd.

1. Verifieer `TENANT_ID` en `API_KEY` voor **Aangepaste criteria maken** verwijzing naar de vroeger vastgestelde Postman-omgevingsvariabelen. Gebruik de onderstaande afbeelding om deze te vergelijken.

   ![CreateCustomCriteria1](assets/CreateCustomCriteria1.png)

2. Voeg uw **Body** toe als **raw** JSON die de locatie van uw CSV-bestand met aangepaste criteria definieert. Gebruik het voorbeeld in de [Create Custom Criteria API](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom) documentatie als sjabloon en geef uw `environmentId` en andere waarden op als dat nodig is. Voor dit voorbeeld, gebruiken wij LAST_PURCHASED als sleutel.

   ![CreateCustomCriteria2](assets/CreateCustomCriteria2.png)

3. Verzend het verzoek en bekijk de reactie, die de details van de douanecriteria bevat u enkel creeerde.

   ![CreateCustomCriteria3](assets/CreateCustomCriteria3.png)

4. Als u wilt controleren of uw aangepaste criteria zijn gemaakt, navigeert u in Adobe Target naar **[!UICONTROL Recommendations]>[!UICONTROL Criteria]** en zoekt u uw criteria op naam of gebruikt u de **Aangepaste criteria-API** in de volgende stap.

   ![CreateCustomCriteria4](assets/CreateCustomCriteria4.png)

In dit geval hebben we een fout. Onderzoek de fout door de douanecriteria nauwkeuriger te onderzoeken, gebruikend **de Criteria API van de Douane van de Lijst**.

## Aangepaste criteria weergeven

Om een lijst van al uw douanecriteria samen met details voor elk terug te winnen, gebruik [Aangepaste Criteria API van de Lijst](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom). De syntaxis is:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

1. Verifieer `TENANT_ID` en `API_KEY` zoals vóór, en verzend het verzoek. Let in de reactie op de id van de aangepaste criteria en op details met betrekking tot het eerder vermelde foutbericht.
   ![ListCustomCriteria](assets/ListCustomCriteria.png)

In dit geval is de fout opgetreden omdat de serverinformatie onjuist is. Dit betekent dat [!DNL Target] geen toegang heeft tot het CSV-bestand dat de definitie van aangepaste criteria bevat. Bewerk de aangepaste criteria om dit te corrigeren.

## Aangepaste criteria bewerken

Als u de details van een definitie van een aangepast criterium wilt wijzigen, gebruikt u de [Aangepaste criteria-API](https://developers.adobetarget.com/api/recommendations/#operation/updateCriteriaCustom) bewerken. De syntaxis is:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Verifieer `TENANT_ID` en `API_KEY`, zoals voordien.
   ![EditCustomCriteria1](assets/EditCustomCriteria1.png)

1. Geef de criteria-id op van de (enkele) aangepaste criteria die u wilt bewerken.
   ![EditCustomCriteria2](assets/EditCustomCriteria2.png)

1. Geef in het body-gedeelte bijgewerkte JSON de juiste serverinformatie. (Geef voor deze stap FTP-toegang op tot een server die u kunt openen.)
   ![EditCustomCriteria3](assets/EditCustomCriteria3.png)

1. Verzend de aanvraag en noteer het antwoord.
   ![EditCustomCriteria4](assets/EditCustomCriteria4.png)

Controleer het succes van de bijgewerkte douanecriteria, gebruikend **krijgen de Criteria van de Douane API**.

## Aangepaste criteria ophalen

Als u de details van aangepaste criteria voor specifieke aangepaste criteria wilt weergeven, gebruikt u [Aangepaste criteria-API](https://developers.adobetarget.com/api/recommendations/#operation/getCriteriaCustom) ophalen. De syntaxis is:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geef de criteria-id op van de aangepaste criteria waarvan u de details wilt ophalen. Verzend het verzoek en bekijk het antwoord.
   ![GetCustomCriteria.png](assets/GetCustomCriteria.png)
1. Verifieer succes. (Controleer in ons geval of er geen verdere FTP-fouten zijn.)
   ![GetCustomCriteria1.png](assets/GetCustomCriteria1.png)
1. (Optioneel) Controleer of de update correct wordt weergegeven in de gebruikersinterface.
   ![GetCustomCriteria2.png](assets/GetCustomCriteria2.png)

## Aangepaste criteria verwijderen

Verwijder met de eerder vermelde criteria-id uw aangepaste criteria met de [Aangepaste criteria-API](https://developers.adobetarget.com/api/recommendations/#operation/deleteCriteriaCustom) verwijderen. De syntaxis is:

`DELETE https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geef de criteria-id op van de (enkele) aangepaste criteria die u wilt verwijderen. Klik **Send**.
   ![DeleteCustomCriteria1](assets/DeleteCustomCriteria1.png)

1. Controleer of de criteria zijn verwijderd met Aangepaste criteria ophalen.
   ![DeleteCustomCriteria2](assets/DeleteCustomCriteria2.png)
In dit geval geeft de verwachte fout van 404 aan dat de verwijderde criteria niet kunnen worden gevonden.

>[!NOTE]
>Ter herinnering: de criteria worden niet verwijderd uit de interface [!DNL Target], ook al is deze verwijderd, omdat deze is gemaakt met de API Aangepaste criteria maken.

Gefeliciteerd! U kunt nu met de API [!DNL Recommendations] details maken, weergeven, bewerken, verwijderen en ophalen. In de volgende sectie gebruikt u de leverings-API [!DNL Target] om aanbevelingen op te halen.

[Next &quot;Fetch Recommendations with the Server-side Delivery API&quot; >](fetch-recs-server-side-delivery-api.md)
