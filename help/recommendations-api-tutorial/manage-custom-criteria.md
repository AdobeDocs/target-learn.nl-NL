---
title: Aangepaste criteria beheren
keywords: recommendations;adobe recommendations;premium;api;apis
description: Adobe Target Recommendations bevat een specifieke set API's waarmee u uw catalogus met aanbevolen producten en/of inhoud kunt beheren. uw aanbevelingen, algoritmen en campagnes beheren; en aanbevelingen doen in JSON-, HTML- of XML-objecten die moeten worden weergegeven in webkanalen, mobiele apparaten, e-mail, IOT en andere kanalen.
kt: 3815
audience: developer
doc-type: tutorial
activity: use
feature: api
topics: recommendations;adobe recommendations;premium;api;apis
solution: Adobe Target
author: Judy Kim
translation-type: tm+mt
source-git-commit: 78b30bc0018527f9d8b2a5b50edee86e877d14c7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Aangepaste criteria beheren

Soms [!DNL Recommendations] kunnen algoritmen die door worden geleverd, bepaalde items die u wilt promoten, niet weergeven. In een dergelijke situatie bieden aangepaste criteria u een manier om een specifieke reeks aanbevolen items voor een bepaald sleutelitem of een bepaalde categorie te leveren. U definieert de toewijzing tussen het hoofditem of de categorie en de aanbevolen items en importeert die toewijzing als aangepaste criteria. Dit proces wordt beschreven in de documentatie [van de](https://docs.adobe.com/content/help/en/target/using/recommendations/criteria/recommendations-csv.html)douanecriteria. Zoals vermeld in die documentatie, kunt u douanecriteria tot stand brengen uitgeven en schrappen door het [!DNL Target] gebruikersinterface (UI). Hier vindt u echter [!DNL Target] ook een reeks API&#39;s met aangepaste criteria waarmee u uw aangepaste criteria gedetailleerder kunt beheren.

>[!IMPORTANT]
>
>Volg deze gebruiksaanwijzing voor aangepaste criteria:
>
> Voer alle handelingen (maken, bewerken, verwijderen) voor een bepaald aangepast criterium uit met behulp van de API&#39;s, of doe alles (maken, bewerken, verwijderen) via de interface. Het beheren van uw aangepaste criteria via een combinatie van de interface en de API kan leiden tot conflicterende informatie of onverwachte resultaten. Als u bijvoorbeeld een aangepast criterium maakt in de gebruikersinterface, maar dit vervolgens bewerkt via de API, worden uw updates in de gebruikersinterface niet weergegeven, ook al wordt het op de achtergrond bijgewerkt, zoals zichtbaar via de API.

## Aangepaste criteria maken

Als u aangepaste criteria wilt maken met de API [Aangepaste criteria](https://developers.adobetarget.com/api/recommendations/#operation/createCriteriaCustom)maken, is de syntaxis:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

>[!WARNING]
>
>Aangepaste criteria die zijn gemaakt met de Create Custom Criteria API (Aangepaste criteria maken), zoals in deze exercitie wordt beschreven, worden weergegeven in de gebruikersinterface, waar ze blijven bestaan. U kunt ze niet bewerken of verwijderen uit de gebruikersinterface. U kunt ze bewerken of verwijderen **via de API**, maar ze blijven in de [!DNL Target] gebruikersinterface staan. Als u de optie voor het bewerken of verwijderen uit de gebruikersinterface wilt behouden, maakt u aangepaste criteria met de gebruikersinterface per [de documentatie](https://docs.adobe.com/content/help/en/target/using/recommendations/criteria/recommendations-csv.html)in plaats van de API Aangepaste criteria maken te gebruiken.

Ga alleen verder met deze zelfstudie nadat u de bovenstaande waarschuwing hebt gelezen en u vertrouwd bent met het maken van nieuwe aangepaste criteria die vervolgens niet uit de gebruikersinterface kunnen worden verwijderd.

1. Verifieer `TENANT_ID` en `API_KEY` voor **Create douanecriteria** verwijs naar de Postman milieuvariabelen die vroeger worden gevestigd. Gebruik de onderstaande afbeelding om deze te vergelijken.

   ![CreateCustomCriteria1](assets/CreateCustomCriteria1.png)

2. Voeg uw **Body** toe als **raw** JSON die de locatie van uw CSV-bestand met aangepaste criteria definieert. Gebruik het voorbeeld in de documentatie van de [Create Aangepaste Criteria API](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom) als malplaatje, die uw `environmentId` en andere waarden zonodig verstrekt. Voor dit voorbeeld, gebruiken wij LAST_PURCHASED als sleutel.

   ![CreateCustomCriteria2](assets/CreateCustomCriteria2.png)

3. Verzend het verzoek en bekijk de reactie, die de details van de douanecriteria bevat u enkel creeerde.

   ![CreateCustomCriteria3](assets/CreateCustomCriteria3.png)

4. Als u wilt controleren of er aangepaste criteria zijn gemaakt, navigeert u in Adobe Target naar **[!UICONTROL Recommendations]>[!UICONTROL Criteria]**en zoekt u de criteria op naam of gebruikt u de API **Aangepaste criteria**weergeven in de volgende stap.

   ![CreateCustomCriteria4](assets/CreateCustomCriteria4.png)

In dit geval hebben we een fout. Laten we de fout onderzoeken door de aangepaste criteria nauwkeuriger te bekijken met de API **** voor aangepaste criteria voor lijst.

## Aangepaste criteria weergeven

Als u een lijst met al uw aangepaste criteria wilt ophalen, gebruikt u de API [Aangepaste criteria](https://developers.adobetarget.com/api/recommendations/#operation/getAllCriteriaCustom)weergeven. De syntaxis is:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom`

1. Verifieer `TENANT_ID` en `API_KEY` zoals vroeger, en verzend het verzoek. Let in de reactie op de id van de aangepaste criteria en op details met betrekking tot het eerder vermelde foutbericht.
   ![ListCustomCriteria](assets/ListCustomCriteria.png)

In dit geval is de fout opgetreden omdat de servergegevens onjuist zijn. Dit betekent dat [!DNL Target] er geen toegang is tot het CSV-bestand dat de definitie van aangepaste criteria bevat. Bewerk de aangepaste criteria om dit te corrigeren.

## Aangepaste criteria bewerken

Met de API [Aangepaste criteria](https://developers.adobetarget.com/api/recommendations/#operation/updateCriteriaCustom)bewerken kunt u de details van een definitie met aangepaste criteria wijzigen. De syntaxis is:

`POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Verifieer `TENANT_ID` en `API_KEY`, zoals voorheen.
   ![EditCustomCriteria1](assets/EditCustomCriteria1.png)

1. Geef de criteria-id op van de (enkele) aangepaste criteria die u wilt bewerken.
   ![EditCustomCriteria2](assets/EditCustomCriteria2.png)

1. Geef in het body-gedeelte bijgewerkte JSON de juiste serverinformatie. (Geef voor deze stap FTP-toegang op tot een server die u kunt openen.)
   ![EditCustomCriteria3](assets/EditCustomCriteria3.png)

1. Verzend de aanvraag en noteer het antwoord.
   ![EditCustomCriteria4](assets/EditCustomCriteria4.png)

Controleer het succes van de bijgewerkte douanecriteria, gebruikend de **Get Aangepaste Criteria API**.

## Aangepaste criteria ophalen

Gebruik de API [Aangepaste criteria](https://developers.adobetarget.com/api/recommendations/#operation/getCriteriaCustom)ophalen om de details van aangepaste criteria voor specifieke aangepaste criteria weer te geven. De syntaxis is:

`GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geef de criteria-id op van de aangepaste criteria waarvan u de details wilt ophalen. Verzend het verzoek en bekijk het antwoord.
   ![GetCustomCriteria.png](assets/GetCustomCriteria.png)
1. Verifieer succes. (Controleer in ons geval of er geen verdere FTP-fouten zijn.)
   ![GetCustomCriteria1.png](assets/GetCustomCriteria1.png)
1. (Optioneel) Controleer of de update correct wordt weergegeven in de gebruikersinterface.
   ![GetCustomCriteria2.png](assets/GetCustomCriteria2.png)

## Aangepaste criteria verwijderen

Verwijder met de eerder vermelde criteria-id uw aangepaste criteria met de API [Aangepaste criteria](https://developers.adobetarget.com/api/recommendations/#operation/deleteCriteriaCustom)verwijderen. De syntaxis is:

`DELETE https://mc.adobe.io/{{TENANT_ID}}/target/recs/criteria/custom/:criteriaId`

1. Geef de criteria-id op van de (enkele) aangepaste criteria die u wilt verwijderen. Klik op **Verzenden**.
   ![DeleteCustomCriteria1](assets/DeleteCustomCriteria1.png)

1. Controleer of de criteria zijn verwijderd met Aangepaste criteria ophalen.
   ![DeleteCustomCriteria2](assets/DeleteCustomCriteria2.png)In dit geval geeft de verwachte fout van 404 aan dat de verwijderde criteria niet kunnen worden gevonden.

>[!NOTE]
>Ter herinnering: de criteria worden niet verwijderd uit de [!DNL Target] gebruikersinterface, ook al is deze verwijderd, omdat deze zijn gemaakt met de API voor aangepaste criteria maken.

Gefeliciteerd! U kunt nu via de [!DNL Recommendations] API gegevens maken, weergeven, bewerken, verwijderen en ophalen over aangepaste criteria. In de volgende sectie gebruikt u de API voor [!DNL Target] aflevering om aanbevelingen op te halen.

[Next &quot;Fetch Recommendations with the Server-side Delivery API&quot; >](fetch-recs-server-side-delivery-api.md)
