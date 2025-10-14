---
title: Lay-outs aanpassen
description: In deze laatste les bouwen wij twee verpersoonlijkingsactiviteiten in Doel voor ons publiek. Leer de activiteiten in de app te laden en weer te geven en te valideren dat de inhoud op het juiste moment op de juiste locaties wordt weergegeven.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
author: Daniel Wright
exl-id: a9f033d9-9f72-4154-88f5-d36423a404d0
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Lay-outs aanpassen

Nu is het tijd om alles samen te brengen en de gepersonaliseerde ervaringen te creëren. Een _Activiteit_ is het [!DNL Target] mechanisme dat de plaatsen, het publiek, en aanbiedingen samen verbindt, zodat wanneer het verzoek van app wordt gemaakt, [!DNL Target] met de gepersonaliseerde inhoud antwoordt. In [!DNL Target] bouwen we twee verpersoonlijkingsactiviteiten en valideren we dat gepersonaliseerde inhoud op het juiste moment en op de juiste locatie wordt weergegeven voor de juiste gebruiker.

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Activiteiten bouwen in Adobe Target
* De activiteiten in de voorbeeldtoepassing valideren

## Activiteiten maken in Adobe Target

Leer hoe u engagegebruikers en contextafhankelijke aanbiedingen kunt maken.

### Eerste activiteit - &quot;Gebruikers inschakelen&quot;

Hier volgt een overzicht van de activiteiten die we gaan ontwikkelen:

| Publiek | Locaties | Aanbiedingen |
|---|---|---|
| Nieuwe mobiele App-gebruikers | wetravel_enter_home, wetravel_enter_search | Home: Nieuwe gebruikers inschakelen, zoeken: Nieuwe gebruikers inschakelen |
| Mobiele App-gebruikers retourneren | wetravel_enter_home, wetravel_enter_search | Home: Terugsturen van gebruikers, default_content |

Ga als volgt te werk in de interface [!DNL Target] :

1. Selecteer **[!UICONTROL Activities]** > **[!UICONTROL Create Activity]** > **[!UICONTROL Experience Targeting]** .

   ![&#x200B; creeer Activiteit &#x200B;](assets/activity_create_1.jpg)

1. Klik op **[!UICONTROL Mobile App]**.
1. Selecteer de **[!UICONTROL Form composer]** .
1. Selecteer uw werkruimte (dezelfde werkruimte die u ook hebt gebruikt in vorige lessen).
1. Selecteer uw bezit (het zelfde bezit u in vorige lessen gebruikte).
1. Klik op **[!UICONTROL Next]**.

   ![&#x200B; creeer Activiteit &#x200B;](assets/activity_create_2.jpg)

1. Wijzig de titel van de activiteit in **[!UICONTROL Engage Users]** .
1. Selecteer **[!UICONTROL ellipsis]** > **[!UICONTROL Change Audience]** .
   ![&#x200B; de Nieuwe Mobiele Gebruikers van de Toepassing veranderen publiek &#x200B;](assets/activity_create_3.jpg)
1. Stel het publiek in op **[!UICONTROL New Mobile App Users]** .
1. Klik op **[!UICONTROL Done]**.
   ![&#x200B; Nieuwe Mobiele Publiek van de Gebruikers van de Toepassing &#x200B;](assets/activity_create_4.jpg)

1. Verander de plaats in _wetravel_commit_home_.
1. Selecteer de vervolgkeuzepijl naast Standaardinhoud en selecteer **[!UICONTROL Change HTML Offer]** .

   ![&#x200B; Nieuwe Mobiele Publiek van de Gebruikers van de Toepassing &#x200B;](assets/activity_create_5.jpg)

1. Selecteer de **[!UICONTROL Home: Engage New Users]** -aanbieding.
1. Selecteer **[!UICONTROL Done]** .

   ![&#x200B; Nieuwe Mobiele Publiek van de Gebruikers van de Toepassing &#x200B;](assets/activity_create_6.jpg)

1. Selecteer **[!UICONTROL Add Location]** .
   ![&#x200B; Nieuwe Mobiele Publiek van de Gebruikers van de Toepassing &#x200B;](assets/activity_create_7.jpg)

1. Selecteer de _wetravel_commit_search_ plaats.
1. Wijzig het HTML-voorstel.

   ![&#x200B; Nieuwe Mobiele Publiek van de Gebruikers van de Toepassing &#x200B;](assets/activity_create_8.jpg)

1. Selecteer de **[!UICONTROL Search: Engage New Users]** -aanbieding.
1. Klik op **[!UICONTROL Done]**.

   ![&#x200B; Nieuwe Mobiele Publiek van de Gebruikers van de Toepassing &#x200B;](assets/activity_create_9.jpg)

U hebt zojuist een publiek verbonden met locaties en aanbiedingen en zo de persoonlijke ervaring voor de nieuwe mobiele App-gebruikers gecreëerd! De ervaring moet er nu als volgt uitzien:

![&#x200B; Ervaring A Definitief &#x200B;](assets/activity_engage_users_a_final.jpg)

Maak nu een ervaring voor het retourneren van gebruikers van mobiele apps:

1. Selecteer **[!UICONTROL Add Experience Targeting]** aan de linkerkant.
1. Selecteer het publiek **[!UICONTROL Returning Mobile App Users]** .
1. Selecteer **[!UICONTROL Done]** .
   ![&#x200B; Terugkerend Mobiel publiek van de Gebruikers van de Toepassing &#x200B;](assets/activity_create_11.jpg)

Gebruik nu het zelfde proces wij vroeger gebruikten om de nieuwe ervaring te vormen. De configuratie voor de beleving van de Mobiele App van de Gebruikers die terugkeren zou als volgt moeten kijken:

![&#x200B; Terugkerend Mobiele de Gebruikers van de Toepassing Definitief &#x200B;](assets/activity_engage_users_b_final.jpg)

Laten we doorgaan naar het volgende scherm in de configuratie:

1. Klik op **[!UICONTROL Next]** om naar het **[!UICONTROL Targeting]** -scherm te gaan.
1. Gebruik de standaardinstellingen voor Targeting. Als u ervaringen voor publiek had dat (b.v. _de Gebruikers van New York_ en _Eerste Gebruikers_) overlapte, kon u de prioritaire orde op dit scherm schikken.
1. Klik op **[!UICONTROL Next]** om naar **[!UICONTROL Goals & Settings]** te gaan.

   ![&#x200B; de Activiteit van de Gebruikers van de Ingenieur - richtend Standaard &#x200B;](assets/activity_engage_users_targeting.jpg)

Laten we nu de activiteiteninstellingen voltooien:

1. Stel de waarde **[!UICONTROL Primary Goal]** in op **[!UICONTROL Conversion]** .
1. Plaats de actie aan **[!UICONTROL Viewed an mbox]** > _wetravel_context_dest_ (Aangezien deze plaats op het bevestigingsscherm is, kunnen wij het gebruiken om omzettingen te meten).

   ![&#x200B; de Activiteit van de Gebruikers van de Overeenkomst - Doelen &#x200B;](assets/activity_create_12.jpg)

1. Houd alle andere montages op het scherm aan de gebreken.
1. Klik op **[!UICONTROL Save & Close]** om de activiteit op te slaan.
1. Activeer **[!UICONTROL Activity]** op het volgende scherm.

![&#x200B; Ervaring B Publiek &#x200B;](assets/activity_create_13.jpg)

Onze eerste activiteit is nu live en klaar om te testen!

### Tweede activiteit - &quot;Contextuele aanbiedingen&quot;

Hier volgt een overzicht van de tweede activiteit die we gaan ontwikkelen:

| Publiek | Locatie | Aanbiedingen |
| --- | --- | --- |
| Doel: San Diego | wetravel_context_dest | Bevordering van San Diego |
| Doel: Los Angeles | wetravel_context_dest | Promotie voor Los Angeles |

Herhaal hetzelfde proces als hierboven voor de volgende activiteit - &quot;Contextuele aanbiedingen&quot;. De definitieve configuratie voor beide ervaringen wordt hieronder getoond:

#### San Diego

![&#x200B; Contextuele Aanbiedingen - Ervaring A &#x200B;](assets/activity_contextual_a_final.jpg)

#### Los Angeles

![&#x200B; Contextuele Aanbiedingen - Ervaring B &#x200B;](assets/activity_contextual_b_final.jpg)

Bij de stap Doelstellingen en instellingen wijzigen we het primaire doel in de locatie op het bevestigingsscherm van de reservering:

1. Stel onder **[!UICONTROL Reporting Settings]** de waarde **[!UICONTROL Primary Goal]** in op **[!UICONTROL Conversion]** .
1. Plaats de actie aan **[!UICONTROL Viewed an mbox]** > _wetravel_context_dest_ (in deze activiteit, is dit metrisch fundamenteel betekenisloos aangezien dit ook de zelfde plaats is die de ervaring) levert.
1. Klik op **[!UICONTROL Save & Close]**.

![&#x200B; Contextuele Aanbiedingen - Ervaring &#x200B;](assets/activity_create_14.jpg)

Activeer de Activiteit op het volgende scherm.

Onze tweede activiteit is live en klaar om te testen!

## Het thuisvoorstel valideren

Voer de emulator uit en controleer of de eerste aanbieding onder aan het thuisscherm wordt weergegeven. Als u een terugkerende gebruiker met 5 of meer app lanceert bent, zou u _welkome rug_ getoonde aanbieding zien. Als u een nieuwe gebruiker (minder dan 5 app lanceert) bent, zou u het _nieuwe gebruiker_ bericht moeten zien:

![&#x200B; bevestigt de Aanbieding van het Huis &#x200B;](assets/layout_home_validate.jpg)

Als de nieuwe gebruikersaanbieding niet wordt weergegeven, probeert u de gegevens voor uw emulator te wissen. De volgende keer dat u de app start, wordt de app opnieuw ingesteld op 1. Dit gebeurt onder **[!UICONTROL Tools]** > **[!UICONTROL AVD Manager]** . Mogelijk moet u Android Studio opnieuw starten als Logcat niet correct werkt:

![&#x200B; Sluiterende Mededinger &#x200B;](assets/layout_home_validate_avd_wipe.jpg)

U kunt de reactie in Logcat ook bevestigen door voor _wetravel_commit_home_ te filtreren:

![&#x200B; bevestigt de Aanbieding van het Huis - Logcat &#x200B;](assets/layout_home_validate_logcat.jpg)

## Zoekvoorstel valideren

Selecteer **[!UICONTROL San Jose]** als uw **[!UICONTROL Departure]** en **[!UICONTROL San Diego]** als uw **[!UICONTROL Destination]** en klik **[!UICONTROL Find Bus]** om naar beschikbare bussen te zoeken.

Voor het resultatenscherm, zou u het _bericht van de gebruiksfilters_ moeten zien. Als u een terugkerende gebruiker bent met 5 of meer toepassingslanceringen, zal geen bericht hier verschijnen aangezien de standaardinhoud voor deze plaats (die leeg is) wordt geplaatst:

![&#x200B; bevestigt de Aanbieding van het Onderzoek &#x200B;](assets/layout_search_validate.jpg)

## Valideer de contextafhankelijke aanbiedingen op het scherm Bedankt

Doorgaan met het boekingsproces:

* Selecteer een bus op het resultatenscherm.
* Selecteer een licentie op het uitcheckscherm.
* Selecteer **[!UICONTROL Credit Card]** op het betalingsscherm (laat de betalingsinformatie leeg - er vindt geen eigenlijke boeking plaats).

Aangezien San Diego als bestemming werd geselecteerd, zou u _DJ SAM_ aanbiedingsbanner op het bevestigingsscherm moeten zien:

![&#x200B; bevestig de Aanbieding van de Context - San Diego &#x200B;](assets/layout_context_san_diego.jpg)

Selecteer nu **[!UICONTROL Done]** en probeer een andere boeking uit te voeren met Los Angeles als bestemming. Het bevestigingsscherm zou de _Universele banner van Studios_ moeten tonen:

![&#x200B; bevestigt de Aanbieding van de Context - Los Angeles &#x200B;](assets/layout_context_los_angeles.jpg)

## Conclusie

Gefeliciteerd! Hiermee wordt het belangrijkste gedeelte van de Adobe Target SDK 4.x voor de zelfstudie van Android afgesloten. U hebt nu de vaardigheden om personalisatie te implementeren in Android apps! U kunt deze documentatie en de demo-app gebruiken als referentie voor uw toekomstige projecten.

Volgende: Functiemarkering is een andere functie die kan worden geïmplementeerd met Adobe Target in Android. Als u meer wilt weten over het markeren van functies, checkt u de volgende les uit.

**[VOLGENDE: Vlaggen van de Eigenschap >](feature-flagging.md)**
