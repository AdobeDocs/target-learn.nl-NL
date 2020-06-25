---
title: Adobe Target met Adobe Mobile Services SDK v4 voor Android
description: Adobe Target met Adobe Mobile Services SDK v4 voor Android is het perfecte startpunt voor Android-ontwikkelaars die Adobe Mobile Services SDK v4 al gebruiken en de app-ervaringen willen aanpassen aan Adobe Target.
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# Overzicht

_Adobe Target met Adobe Mobile Services SDK v4 voor Android_ is het perfecte startpunt voor Android-ontwikkelaars die Adobe Mobile Services SDK v4 al gebruiken en de app willen aanpassen aan Adobe Target.

Er is een demo-app voor Android beschikbaar waarmee u de lessen kunt voltooien. Nadat u deze zelfstudie hebt voltooid, kunt u de implementatie starten [!DNL Target] in uw eigen Android-app.

Na het voltooien van deze zelfstudie kunt u het volgende doen:

* De [Adobe Mobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/android/getting-started-android/requirements.html) -instelling valideren
* Voer de volgende soorten [!DNL Target] verzoeken uit:
   * Voorvertoning van [!DNL Target] inhoud
   * Meerdere [!DNL Target] locaties (selectievakjes) in één aanvraag in batch plaatsen
   * Blokkeringsaanvragen (wordt uitgevoerd voordat de app wordt weergegeven)
   * Niet-blokkerende aanvragen (wordt uitgevoerd op de achtergrond)
   * In real time (niet in cache plaatsen)
   * Opslaan van cache herstellen
* Parameters toevoegen aan aanvragen voor verbeterde personalisatie
* Soorten publiek en aanbiedingen maken
* Schermindelingen aanpassen
* Nieuwe functies uitrollen met functiemarkering

## Vereisten

In deze lessen wordt aangenomen dat u:

* Toegang tot de Adobe Target-interface op Adobe-id- en fiatterniveau hebben (zie de onderstaande verificatiestappen)
* Ken uw Adobe Target-clientcode zodat u aanvragen kunt indienen bij uw eigen account. De clientcode wordt weergegeven in de Adobe Target-interface op het scherm Setup > Implementation > Edit at.js.
* Heb toegang tot en ben vertrouwd met het gebruikersinterface van de [Mobiele Diensten](https://mobilemarketing.adobe.com)
* Een IDE voor mobiele app ontwikkelen voor Android. Deze zelfstudie bevat [Android Studio](https://developer.android.com/studio/install) in verschillende stappen en schermafbeeldingen

Als u niet de vereiste toegang tot de Oplossingen van Experience Cloud hebt, contacteer uw Beheerder van Experience Cloud.

Ook wordt aangenomen dat u bekend bent met de ontwikkeling van Android in Java. U hoeft geen Java-expert te zijn om de lessen te kunnen voltooien, maar u krijgt er meer uit als u de code eenvoudig kunt lezen en begrijpen.

### Toegang tot Adobe Target verifiëren

Deze les vereist toegang tot Adobe Target. Voordat u de volgende stappen doorloopt, moet u ervoor zorgen dat u toegang hebt tot Adobe Target door het volgende te doen:

1. Meld u aan bij de [Adobe Experience Cloud](https://experience.adobe.com/)
1. Klik in het beginscherm van Experience Cloud op [!DNL Target]:
   ![Experience Cloud-startscherm](assets/aec_homeScreen_clickTarget.png)
1. Ga naar de lijst Activiteiten in Adobe Target, zoals hieronder wordt afgebeeld. Je moet zien dat de gebruiker toegang op fiveau heeft. Als u toegang tot het niveau van de fiatteur niet kunt hebben [!DNL Target] of niet kunt verifiëren, gelieve één van de Beheerders van Experience Cloud van uw bedrijf te contacteren, om deze toegang te verzoeken en deze zelfstudie te hervatten zodra het wordt verleend:

   ![Adobe-gebruikersinterface](assets/targetUI_approver.png)

## Over de lessen

In deze lessen implementeert u Adobe Target in een demo-reisapp genaamd &#39;We.Travel&#39; met uw eigen Adobe Target-account. Aan het einde van de zelfstudie stuurt u persoonlijke berichten aan de gebruiker op basis van hun gebruik van de app! De laatste personalisatie-ervaringen zien er als volgt uit:

![We.Reizen, app definitief](assets/overview_final_result.jpg)

Nadat u de implementatie binnen de We.Travel-app hebt doorlopen, kunt u beginnen met het gebruik [!DNL Target] in uw eigen mobiele app.

Laten we beginnen!

**[VOLGENDE: &quot;Download en werk de voorbeeldtoepassing bij&quot; >](download-and-update-the-sample-app.md)**
