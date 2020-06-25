---
title: Download en werk de voorbeeldtoepassing Web.Travel bij
seo-title: Download de voorbeeldapp en controleer de SDK voor mobiele services
description: 'De voorbeeldtoepassing We.Travel wordt vooraf geïmplementeerd met de Adobe Mobile Services SDK v4. U hoeft deze alleen bij te werken, zodat deze naar uw eigen Experience Cloud Org- en Solution-accounts verwijst.   '
seo-description: De voorbeeldtoepassing We.Travel wordt vooraf geïmplementeerd met de Adobe Mobile Services SDK v4. U hoeft deze alleen bij te werken, zodat deze naar uw eigen Experience Cloud Org- en Solution-accounts verwijst.
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---


# Download en werk de voorbeeldtoepassing Web.Travel bij

De voorbeeldtoepassing We.Travel wordt vooraf geïmplementeerd met de Adobe Mobile Services SDK v4. U hoeft deze alleen bij te werken, zodat deze naar uw eigen Experience Cloud Org- en Solution-accounts verwijst.

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Download en open de voorbeeldapp We.Travel in Android Studio
* De SDK-instellingen voor mobiele services controleren en bijwerken voor [!DNL Target]

## Download de Web.Travel-app

* Download de [sample-app-android-SDKv4-Base-Version.zip](assets/sample-app-android-SDKv4-Base-Version.zip)
* Het ZIP-bestand decomprimeren
* Open de toepassing in Android Studio als een bestaand project (negeer eventuele fouten over &quot;Ongeldige VCS-hoofdtoewijzing&quot;).
* Voer de app in een emulator uit om te bevestigen dat de app is gemaakt en dat u het beginscherm kunt zien
* Blader naar de app en controleer of u het boekingsproces kunt voltooien (selecteer een betalingsoptie en druk op Doorgaan om het factureringsscherm over te slaan!)

   ![Open het scherm](assets/wetravel_homeScreen.png)![appConfirmation](assets/wetravel_confirmationScreen.png)

## De SDK-instellingen voor mobiele services controleren en bijwerken voor [!DNL Target]

De SDK van Adobe Mobile Services is vooraf geïnstalleerd in de Web-app [volgens de documentatie](https://docs.adobe.com/content/help/en/mobile-services/android/getting-started-android/requirements.html). Nu gaat u de installatie bijwerken zodat deze naar uw eigen [!DNL Target] account verwijst.

Maak eerst een nieuwe toepassing in de gebruikersinterface voor mobiele services:

1. Meld u aan bij de interface [](https://mobilemarketing.adobe.com)Adobe Mobile Services.
1. Ga naar de [!UICONTROL Manage Apps]zelfstudie en klik **[!UICONTROL Add]** om een nieuwe app toe te voegen die u kunt gebruiken in deze zelfstudie (**[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**).
1. Kies een Analytics-rapportsuite met niet-productiegegevens, geef de toepassing een naam, selecteer het **[!UICONTROL Standard]** type en klik op **[!UICONTROL Save]**.
1. Nadat de app is toegevoegd, voegt u uw [!DNL Target] clientcode toe aan het volgende scherm in de [!UICONTROL SDK Target Options] sectie (u vindt uw clientcode in de [!DNL Target] interface onder **[!UICONTROL Setup]** > **[!UICONTROL Implementation]** > **[!UICONTROL Edit Settings]**, naast de `at.js` knop Downloaden).
1. De [!UICONTROL Request Timeout] instelling bepaalt hoe lang de toepassing wacht op de reactie van de [!DNL Target] server voordat de time-outinstructies worden uitgevoerd. Laat de standaardinstelling ongewijzigd.
1. Schakel de optie in [!UICONTROL Visitor ID Service] en zorg dat de optie [!UICONTROL Organization] is geselecteerd in de vervolgkeuzelijst.
1. Sla uw wijzigingen op door **[!UICONTROL Save]** rechtsboven in het venster te klikken (niet in de sectie [!UICONTROL Universal Links], [!UICONTROL App Links] opties of [!UICONTROL Push Services] sectie).
1. Blader naar het gedeelte Downloads App SDK onder aan de pagina en download het configuratiebestand:

   ![Het configuratiebestand downloaden](assets/config_file.jpg)

1. Vervang het `ADBMobileConfig.json` bestand in de map met Android Studio-projectmiddelen (app > src > main > assets).

1. Open nu het `ADBMobileConfig.json` bestand en controleer of het de verwachte wijzigingen bevat, zoals de [!DNL Target] clientcode en uw Analytics-gegevens:
   ![Het configuratiebestand downloaden](assets/client_code.jpg)

Als u uw montages niet ziet, bevestig dat u de juiste **[!UICONTROL Save]** knoop in de [!UICONTROL Mobile Services] interface klikte en het dossier aan de correcte plaats kopieerde.

Gefeliciteerd! U hebt de SDK bijgewerkt met uw [!DNL Target] accountgegevens! Wij zullen extra bevestiging van de configuratie doen nadat wij [!DNL Target] verzoeken in de volgende les toevoegen.

**[VOLGENDE: &quot;Target-verzoeken toevoegen&quot; >](add-requests.md)**
