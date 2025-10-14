---
title: Download en werk de voorbeeldtoepassing Web.Travel bij
description: De voorbeeldtoepassing We.Travel wordt vooraf geïmplementeerd met de Adobe Mobile Services SDK v4. U hoeft deze alleen bij te werken, zodat deze naar uw eigen Experience Cloud Org- en Solution-accounts verwijst.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 244bcf7a-b59b-4dd1-bd05-0a55ce7a7132
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Download en werk de voorbeeldtoepassing Web.Travel bij

De voorbeeldtoepassing We.Travel wordt vooraf geïmplementeerd met de Adobe Mobile Services SDK v4. U hoeft deze alleen bij te werken, zodat deze naar uw eigen Experience Cloud Org- en Solution-accounts verwijst.

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Download en open de voorbeeldapp We.Travel in Android Studio
* De SDK-instellingen voor mobiele services controleren en bijwerken voor [!DNL Target]

## Download de Web.Travel-app

* Download [&#x200B; steekproef-app-android-SDKv4-Base-Version.zip &#x200B;](assets/sample-app-android-SDKv4-Base-Version.zip)
* Het ZIP-bestand decomprimeren
* Open app in Android Studio als bestaand project (negeer eventuele fouten over &quot;Ongeldige VCS-hoofdtoewijzing&quot;)
* Voer de app in een emulator uit om te bevestigen dat de app is gemaakt en dat u het beginscherm kunt zien
* Blader naar de app en controleer of u het boekingsproces kunt voltooien (selecteer een betalingsoptie en druk op Doorgaan om het factureringsscherm over te slaan!)

  ![&#x200B; open het app &#x200B;](assets/wetravel_homeScreen.png)![&#x200B; Bevestigingsscherm &#x200B;](assets/wetravel_confirmationScreen.png)

## De SDK-instellingen voor mobiele services controleren en bijwerken voor [!DNL Target]

Adobe Mobile Services SDK is vooraf geïnstalleerd binnen de We.Travel app [&#x200B; volgens de documentatie &#x200B;](https://experienceleague.adobe.com/docs/mobile-services/android/getting-started-android/requirements.html?lang=nl-NL). Nu gaat u de installatie bijwerken zodat deze naar uw eigen [!DNL Target] -account verwijst.

Maak eerst een nieuwe toepassing in de gebruikersinterface voor mobiele services:

1. Login aan de [&#x200B; interface van de Diensten van Adobe Mobiele &#x200B;](https://mobilemarketing.adobe.com/).
1. Ga naar [!UICONTROL Manage Apps] en klik vervolgens op **[!UICONTROL Add]** om een nieuwe toepassing toe te voegen die u in deze zelfstudie wilt gebruiken ( **[!UICONTROL Manage Apps]** > **[!UICONTROL Add]** ).
1. Kies een Analytics-rapportsuite met niet-productiegegevens, geef de app een naam, selecteer het **[!UICONTROL Standard]** -type en klik op **[!UICONTROL Save]** .
1. Nadat de app is toegevoegd, voegt u uw [!DNL Target] clientcode toe aan het volgende scherm in de [!UICONTROL SDK Target Options] -sectie (u vindt de clientcode in de [!DNL Target] -interface onder **[!UICONTROL Setup]** > **[!UICONTROL Implementation]** > **[!UICONTROL Edit Settings]** naast de knop Downloaden `at.js` ).
1. De instelling [!UICONTROL Request Timeout] bepaalt hoe lang de toepassing wacht op de reactie van de [!DNL Target] -server voordat de time-outinstructies worden uitgevoerd. Laat de standaardinstelling ongewijzigd.
1. Schakel de optie [!UICONTROL Visitor ID Service] in en zorg dat de optie [!UICONTROL Organization] is geselecteerd in de vervolgkeuzelijst.
1. Sla uw wijzigingen op door op **[!UICONTROL Save]** rechtsboven in het venster te klikken (niet op de knop in de sectie [!UICONTROL Universal Links] , [!UICONTROL App Links] of [!UICONTROL Push Services] ).
1. Blader naar de sectie SDK-downloads voor de app onder aan de pagina en download het configuratiebestand:

   ![&#x200B; Download het Dossier Config &#x200B;](assets/config_file.jpg)

1. Vervang het bestand `ADBMobileConfig.json` in de map met Android Studio-projectmiddelen (app > src > main > assets).

1. Open nu het bestand `ADBMobileConfig.json` en controleer of het de verwachte wijzigingen bevat, zoals de [!DNL Target] Client Code en uw Analytics-gegevens:
   ![&#x200B; Download het Dossier Config &#x200B;](assets/client_code.jpg)

Als u de instellingen niet ziet, controleert u of u op de knop right **[!UICONTROL Save]** in de [!UICONTROL Mobile Services] -interface hebt geklikt en het bestand naar de juiste locatie hebt gekopieerd.

Gefeliciteerd! U hebt de SDK bijgewerkt met uw [!DNL Target] -accountgegevens! Nadat we [!DNL Target] -verzoeken in de volgende les hebben toegevoegd, wordt de configuratie verder gevalideerd.

**[VOLGENDE: &quot;voeg de Verzoeken van het Doel toe&quot; >](add-requests.md)**
