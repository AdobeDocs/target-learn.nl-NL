---
title: Soorten publiek en aanbiedingen maken in Adobe Target
description: In deze les bouwen we publiek en aanbiedingen in Adobe Target voor de drie locaties die we in de vorige lessen hebben geïmplementeerd. Deze zullen worden gebruikt om gepersonaliseerde ervaringen in de volgende les te tonen.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 4b153e4f-a979-49a8-8c26-f7ac95162a2f
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# Soorten publiek en aanbiedingen maken in Adobe Target

In deze les gaan we naar de interface van [!DNL Target] en bouwen we publiek en aanbiedingen voor de drie locaties die we in de vorige lessen hebben geïmplementeerd.

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Soorten publiek maken in Adobe Target
* Aanbiedingen maken in Adobe Target

Meer specifiek, in deze les zullen wij publiek en aanbiedingen tot stand brengen nodig om de gevallen van het verpersoonlijkingsgebruik te verwezenlijken die aan het begin van het leerprogramma worden bepaald. We willen de schermen Home en Search gebruiken om gebruikers van apps te helpen hun reizen te boeken, en we willen het scherm Bedankt gebruiken om bepaalde relevante promoties weer te geven op basis van de bestemming van de gebruiker. Hier is een lijst die vertegenwoordigt wat wij in deze les voor elke plaats zullen bouwen:

| Locatie | Publiek | Voorstel |
| --- | --- | --- |
| wetravel_enter_home | Nieuwe mobiele App-gebruikers | &quot;Selecteer uw Oorsprong &amp; Doel om naar beschikbare busroutes te zoeken&quot; |
| wetravel_enter_search | Nieuwe mobiele App-gebruikers | &quot;Gebruik filters om de zoekresultaten te beperken tot een lager niveau&quot; |
| wetravel_enter_home | Mobiele App-gebruikers retourneren | &quot;Welkom terug! Gebruik de Bodemcode BACK30 tijdens het afrekenen om een korting van 10% te krijgen.&quot; |
| wetravel_enter_search | Mobiele App-gebruikers retourneren | standaardinhoud |
| wetravel_context_dest | Doel: San Diego | &quot;DJ&quot; |
| wetravel_context_dest | Doel: Los Angeles | &quot;Universal&quot; |

## Selecteer uw Workspace

Als uw bedrijf Eigenschappen en Werkruimten gebruikt om grenzen te vestigen voor het personaliseren van apps en websites-en u uitvoerde de parameter at_property in laatste les-u zou eerst moeten ervoor zorgen dat u in correcte Workspace bent alvorens met deze les te werk te gaan. Als u geen Eigenschappen en Werkruimten gebruikt, negeer enkel deze stap. Selecteer Workspace die u in de vorige les gebruikte om de at_property waarde te kopiëren:

![ Voorbeeld van Workspace ](assets/workspace.jpg)

## Soorten publiek maken

Laten we nu het publiek maken dat we zullen gebruiken om de app aan te passen.

### Een publiek maken voor nieuwe gebruikers

Het publiek van Adobe Target wordt gebruikt om specifieke groepen bezoekers te identificeren. Aanbiedingen kunnen dan worden gericht op die specifieke groepen. Voor de eerste twee plaatsen, zullen wij een &quot;Nieuwe Gebruikers&quot;publiek gebruiken:

1. Klik op **[!UICONTROL Audiences]** in de bovenste navigatie.
1. Klik op **[!UICONTROL Create Audience]** .
   ![ creeer een Nieuw publiek van de Gebruiker ](assets/audience_new_mobile_app_users_1.jpg)

1. Voer **[!UICONTROL New Mobile App Users]** in als de publieksnaam.
1. Selecteer **[!UICONTROL Add Rule]** .
1. Selecteer een **[!UICONTROL Custom]** -regel.
   ![ creeer een Nieuw publiek van de Gebruiker ](assets/audience_new_mobile_app_users_2.jpg)

1. Selecteer **[!UICONTROL a.Launches]** .
1. Selecteer **[!UICONTROL is less than]** .
1. Ga **5** in.
1. Sla het nieuwe publiek op.
   ![ creeer een Nieuw publiek van de Gebruiker ](assets/audience_new_mobile_app_users_3.jpg)

### Een publiek maken voor terugkerende gebruikers

Volg dezelfde stappen als hierboven beschreven om een publiek te maken voor terugkerende gebruikers.

1. Noem het publiek _Terugkerend Mobiele Gebruikers van de Toepassing_.
1. Gebruik **[!UICONTROL a.Launches is greater than or equal to 5]** als de aangepaste regel.
1. Sla het nieuwe publiek op.

   ![ creeer een Terugkerend publiek van de Gebruiker ](assets/audience_returning_mobile_app_users.jpg)

>[!NOTE]
>
>Alle levenscyclusmetriek en afmetingen die in de mobiele SDK van [!DNL Target] worden verzameld, worden voorafgegaan door &quot;a&quot; (bijvoorbeeld a.Launches) en zijn beschikbaar in de optie &quot;Aangepast&quot; van het keuzemenu en kunnen worden gebruikt om een publiek te maken.

### Creeer een Publiek voor Gebruikers die een Trip aan San Diego boeken

Nu maken we een paar soorten publiek voor een aantal bestemmingen die worden aangeboden door de app We.Travel. In de laatste les hebben wij de bestemming als plaatsparameter in het wetravel_context_dest locatieverzoek overgegaan. Deze parameter is beschikbaar in de optie Aangepast van het keuzemenu.

>[!NOTE]
>
>Als een parameter die u verwacht te zien in de vervolgkeuzelijst Aangepast niet in de interface [!DNL Target] wordt weergegeven, controleert u nogmaals of deze daadwerkelijk wordt doorgegeven in de aanvraag. Als u hebt gecontroleerd dat dat in het verzoek is maar niet in de interface [!DNL Target] wordt geladen, kunt u enkel de parameternaam typen en op Enter drukken om uw publiek te blijven definiëren

1. Noem het publiek _Doel: San Diego_.
1. Gebruik een douaneregel met deze definitie: _locationDest bevat San Diego_.
1. Sla het nieuwe publiek op.

   ![ creeer &quot;San Diego&quot;Publiek ](assets/audience_locationDest_san_diego.jpg)

### Een publiek maken voor gebruikers die een reis naar Los Angeles boeken

1. Noem het publiek _Doel: Los Angeles_
1. Gebruik een douaneregel met deze definitie: _locationDest bevat Los Angeles_
1. Sla het nieuwe publiek op.

![ creeer &quot;Los Angeles&quot;Publiek ](assets/audience_locationDest_los_angeles.jpg)

## Aanbiedingen maken

Laten we nu aanbiedingen maken om deze berichten weer te geven. Ter herinnering, aanbiedingen zijn fragmenten met code/inhoud, die worden geleverd in het antwoord [!DNL Target] . Deze worden meestal gemaakt in de gebruikersinterface van [!DNL Target] , maar kunnen ook worden gemaakt via API of via de Experience Fragments-integratie met Adobe Experience Manager. In mobiele apps zijn JSON-aanbiedingen gebruikelijk. In deze zelfstudie gebruiken we HTML-aanbiedingen die kunnen worden gebruikt om inhoud in de standaardtekst (inclusief JSON) in de app te leveren.

### De aanbieding voor nieuwe gebruikers maken

Laten we eerst aanbiedingen voor de berichten aan Nieuwe gebruikers maken:

1. Klik op **[!UICONTROL Offers]** in de bovenste navigatie.
1. Klik op **[!UICONTROL Create]**.
1. Selecteer **[!UICONTROL HTML Offer]** .

   ![ creeer de Aanbieding van het Huis ](assets/offer_home_1.jpg)

1. Noem het voorstel _Huis: De Nieuwe Gebruikers van de Mogelijkheid_.
1. Ga _Uitgezochte Source en Bestemming in om naar beschikbare bussen_ als code te zoeken.
1. Sla het nieuwe voorstel op.

   ![ creeer de Aanbieding van HTML van het Huis ](assets/offer_home_2.jpg)

### De aanbieding voor terugkerende gebruikers maken

Laten we nu de ene aanbieding voor terugkerende gebruikers maken (de tweede aanbieding is standaardinhoud die als niets wordt weergegeven):

1. Noem het aanbieding _Huis: Terugkerende Gebruikers_.
1. Ga _Welkom terug! Gebruik de Bodemcode BACK30 tijdens het afrekenen om een korting van 10% te krijgen._ als de HTML-code.
1. Sla het nieuwe voorstel op.

   ![ creeer de Aanbieding van HTML van het Huis ](assets/offer_home_returning_users.jpg)

### De San Diego-aanbieding maken

Wanneer &quot;DJ&quot; wordt geretourneerd aan de activiteit Dankuwel, geeft logica in de functie filterRecommendationBasedOnOffer() een banner weer voor &quot;Rock Night with DJ SAM&quot;:

1. Noem de aanbieding _Bevordering voor San Diego_.
1. Ga _DJ_ als code van HTML in.
1. Sla het nieuwe voorstel op.

![ creeer &quot;San Diego&quot;Aanbieding ](assets/offer_san_diego.jpg)

### Aanbieding maken voor gebruikers die naar Los Angeles gaan

Wanneer &quot;Universal&quot; wordt geretourneerd naar de activiteit Dankuwel, wordt voor logica in de functie filterRecommendationBasedOnOffer() een banner voor &quot;Universal Studios&quot; weergegeven:

1. Noem de aanbieding _Bevordering voor Los Angeles_.
1. Ga _Universeel_ als code van HTML in.
1. Sla het nieuwe voorstel op.

![ creeer &quot;Los Angeles&quot;Aanbieding ](assets/offer_los_angeles.jpg)

## Conclusie

Nu hebben we ons publiek en onze aanbiedingen. In de volgende les bouwen we activiteiten die de locaties, het publiek en de aanbiedingen aan elkaar koppelen om de gepersonaliseerde ervaringen te creëren!

**[VOLGENDE: &quot;Personaliseer Lay-outs&quot; >](personalize-layouts.md)**
