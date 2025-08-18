---
title: Adobe Target met Adobe Mobile Services SDK v4 voor Android
description: Adobe Target met Adobe Mobile Services SDK v4 voor Android is het perfecte startpunt voor Android-ontwikkelaars die Adobe Mobile Services SDK v4 al gebruiken en willen beginnen met het aanpassen van hun app-ervaringen met Adobe Target.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile, Overview
doc-type: tutorial
kt: 3040
exl-id: 20f8ed4f-a86d-4c5e-9296-71a93724caa3
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Adobe Target met Adobe Mobile Services SDK v4 voor Android - Overzicht

_Adobe Target met Adobe Mobile Services SDK v4 voor Android_ is het perfecte uitgangspunt voor de ontwikkelaars van Android die reeds Adobe Mobile Services SDK v4 gebruiken en app ervaringen met Adobe Target willen beginnen te verpersoonlijken.

Er is een demo Android-app beschikbaar waarmee u de lessen kunt voltooien. Nadat u deze zelfstudie hebt voltooid, bent u klaar om [!DNL Target] te gaan implementeren in uw eigen Android-app!

Na het voltooien van deze zelfstudie kunt u het volgende doen:

* Valideer [ Adobe Mobile Services SDK ](https://experienceleague.adobe.com/docs/mobile-services/android/getting-started-android/requirements.html?lang=en) opstelling
* Voer de volgende typen [!DNL Target] -aanvragen uit:
   * Voorvertoning van [!DNL Target] -inhoud
   * Meerdere [!DNL Target] locaties (mboxes) in één aanvraag in batch plaatsen
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

* Een Adobe-id en een toegangsnummer op goedkeuringsniveau tot de Adobe Target-interface hebben (zie de verificatiestappen hieronder)
* Ken uw Adobe Target-clientcode zodat u aanvragen kunt indienen bij uw eigen account. De clientcode wordt weergegeven in de Adobe Target-interface op het tabblad   Setup > Implementation > Edit at.js settings screen
* Heb toegang tot en ben vertrouwd met het [ Mobiele gebruikersinterface van de Diensten ](https://mobilemarketing.adobe.com/)
* Hebt u een IDE voor de ontwikkeling van mobiele apps voor Android. Dit leerprogramma kenmerkt {de Studio van 0} Android [ in diverse stappen en screenshots](https://developer.android.com/studio/install)

Als u niet de vereiste toegang tot de Oplossingen van Experience Cloud hebt, contacteer uw Beheerder van Experience Cloud.

Bovendien wordt aangenomen dat u bekend bent met de Android-ontwikkeling in Java. U hoeft geen Java-expert te zijn om de lessen te kunnen voltooien, maar u krijgt er meer uit als u de code eenvoudig kunt lezen en begrijpen.

### Toegang tot Adobe Target verifiëren

Deze les vereist toegang tot Adobe Target. Voordat u de volgende stappen doorloopt, moet u ervoor zorgen dat u toegang hebt tot Adobe Target door het volgende te doen:

1. Logboek in [ Adobe Experience Cloud ](https://experience.adobe.com/)
1. Klik in het beginscherm van Experience Cloud op [!DNL Target] :
   ![ het Homescherm van Experience Cloud ](assets/aec_homeScreen_clickTarget.png)
1. Ga naar de lijst Activiteiten in Adobe Target, zoals hieronder wordt afgebeeld. Je moet zien dat de gebruiker toegang op fiveau heeft. Als u geen toegang hebt tot [!DNL Target] of als u de toegang op het niveau van de fiatteur niet kunt verifiëren, gelieve één van de Beheerders van Experience Cloud van uw bedrijf te contacteren, om deze toegang te verzoeken en deze zelfstudie te hervatten zodra het wordt verleend:

   ![ UI van Adobe ](assets/targetUI_approver.png)

## Informatie over de lessen

In deze lessen implementeert u Adobe Target in een demo-reisapp genaamd &#39;We.Travel&#39; met uw eigen Adobe Target-account. Aan het einde van de zelfstudie stuurt u persoonlijke berichten aan de gebruiker op basis van hun gebruik van de app! De laatste personalisatie-ervaringen zien er als volgt uit:

![ Wij.Travel app definitief ](assets/overview_final_result.jpg)

Nadat u de implementatie binnen de We.Travel-app hebt doorlopen, kunt u [!DNL Target] gebruiken in uw eigen mobiele app.

Laten we beginnen!

**[VOLGENDE: &quot;Download en werk de Steekproef App&quot;bij >](download-and-update-the-sample-app.md)**
