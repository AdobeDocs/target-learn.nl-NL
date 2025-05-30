---
title: Parameters toevoegen aan de verzoeken
description: In deze les zullen wij de metriek van de levenscyclus van de Adobe en douaneparameters aan de verzoeken toevoegen van het Doel in de vorige les. Deze metriek en parameters zullen voor het creëren van gepersonaliseerde publiek later in het leerprogramma worden gebruikt.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 0250e55f-a233-4060-84e1-86d1f88a6106
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---

# Parameters toevoegen aan de verzoeken

In deze les zullen wij metriek van de levenscyclus van de Adobe en douaneparameters aan de [!DNL Target] verzoeken toevoegen die in de vorige les worden toegevoegd. Deze metriek en parameters zullen voor het creëren van gepersonaliseerde publiek later in het leerprogramma worden gebruikt.

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* De Adobe mobiele levenscycluscijfers toevoegen
* Parameters toevoegen aan een prefetch-aanvraag
* Parameters toevoegen aan een live locatie
* De parameters voor beide aanvragen valideren

## De levenscyclusparameters toevoegen

Laat de [ Adobe mobiele levenscyclusmetriek ](https://experienceleague.adobe.com/docs/mobile-services/android/metrics.html?lang=nl-NL) toe. Hierdoor worden parameters toegevoegd aan locatieaanvragen die uitgebreide informatie bevatten over het apparaat van de gebruiker en de betrokkenheid bij de app. In de volgende les maken we een publiek met behulp van gegevens die de levenscyclusaanvraag bevat.

Als u levenscyclusmetriek wilt inschakelen, opent u de HomeActivity-controller opnieuw en voegt u `Config.collectLifecycleData(this);` toe aan de functie onResume():

![ Verzoek van de Levenscyclus ](assets/lifecycle_code.jpg)

### De levenscyclusparameters voor de Prefetch-aanvraag valideren

Voer de emulator uit en gebruik Logcat om de levenscyclusparameters te valideren. Filter voor &quot;prefetch&quot; om de prefetch-reactie te zoeken en de nieuwe parameters te zoeken:
![ Bevestiging van de Levenscyclus ](assets/lifecycle_validation.jpg)

Hoewel wij slechts `Config.collectLifecycleData()` aan de controlemechanisme HomeActivity hebben toegevoegd, zou u de levenscyclusmetriek moeten zien die met het verzoek van het Doel wordt verzonden op uw scherm DankU, ook.

## De parameter at_property toevoegen aan de Prefetch-aanvraag

Adobe Target-eigenschappen worden gedefinieerd in de [!DNL Target] -interface en worden gebruikt om grenzen vast te stellen voor het aanpassen van apps en websites. De parameter at_property identificeert het specifieke bezit waar uw aanbiedingen en activiteiten worden betreden en gehandhaafd. We voegen een eigenschap toe aan de aanvragen voor de prefetch en live-locatie.

>[!NOTE]
>
>Afhankelijk van uw licentie worden de opties voor eigenschappen al dan niet weergegeven in de interface van [!DNL Target] . Als u deze opties niet hebt, of als u geen Eigenschappen in uw bedrijf gebruikt, overslaan enkel naar de volgende sectie van deze les.

U kunt de waarde at_property ophalen in de interface [!DNL Target] onder [!UICONTROL Setup] > [!UICONTROL Properties] .  Als u de cursor op de eigenschap plaatst, selecteert u het pictogram van het codefragment en kopieert u de waarde `at_property` :

![ Exemplaar at_property ](assets/at_property_interface.jpg)

Voeg het als parameter voor elke plaats in het prefetch verzoek als dit toe:
![ voegt parameter at_property ](assets/params_at_property.jpg) toe
Hier is de bijgewerkte code voor de functie `targetPrefetchContent()` (werk de tekst van de tijdelijke aanduiding _[!UICONTROL your at_property value goes here]_&#x200B;bij!):

```java
public void targetPrefetchContent() {
        List<TargetPrefetchObject> prefetchList = new ArrayList<>();

        Map<String, Object> params1;
        params1 = new HashMap<String, Object>();
        params1.put("at_property", "your at_property value goes here");

        prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, params1));
        prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, params1));
        Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
            @Override
            public void call(final Boolean status) {
                HomeActivity.this.runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                        String cachingStatus = status ? "YES" : "NO";
                        System.out.println("Received Response from prefetch : " + cachingStatus);
                        engageMessage();
                        setUp();

                    }
                });
            }};
        Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
    }
```

### Opmerking over parameters

Voor toekomstige projecten, kunt u extra parameters willen uitvoeren. De methode `createTargetPrefetchObject()` staat drie typen parameters toe: `locationParams` , `orderParams` en `productParams` . Zie de documentatie voor [ meer details bij het toevoegen van deze parameters aan het prefetch verzoek ](https://experienceleague.adobe.com/docs/mobile-services/android/target-android/c-mob-target-prefetch-android.html?lang=nl-NL).

U kunt ook verschillende locatieparameters toevoegen aan elke locatie in de prefetch-aanvraag. Bijvoorbeeld, kon u een andere Kaart creëren genoemd param2, een nieuwe parameter in het zetten, dan plaats param2 in één plaats en param1 met de andere plaats. Hier volgt een voorbeeld:

```java
prefetchList.add(Target.createTargetPrefetchObject(location1_name, params1);
prefetchList.add(Target.createTargetPrefetchObject(location2_name, params2);
```

## Valideer de parameter at_property in de Prefetch-aanvraag

Voer nu de emulator uit en gebruik Logcat om te controleren of de eigenschap at_property de aanvraag en de reactie voor beide locaties weergeeft:
![ bevestigt de parameter at_property ](assets/parameters_at_property_validation.jpg)

## Aangepaste parameters toevoegen aan de aanvraag voor Live locatie

De live locatieaanvraag (wetravel_context_dest) is toegevoegd aan de vorige les zodat we een relevante promotie kunnen weergeven op het laatste bevestigingsscherm van het boekingsproces. Wij zouden de bevordering willen personaliseren die op de bestemming van de gebruiker wordt gebaseerd en dat doen wij dat als parameter aan het verzoek toevoegen. Wij zullen een parameter voor de tropoorsprong en at_property waarde eveneens toevoegen.

Voeg de volgende parameters toe aan de targetLoadRequest() functie in de ControllerYouActivity:
![ voegt Parameters aan het Levende Verzoek van de Plaats toe ](assets/parameters_live_location.jpg)
Hier is de bijgewerkte code voor de functie targetLoadRequest() (zorg dat u de plaatsaanduidingstekst &#39;add your at_property value here&#39; bijwerkt!):

```java
public void targetLoadRequest(final ArrayList<Recommandation> recommandations) {
    Map<String, Object> locationParams = new HashMap<>();
    locationParams.put("at_property","add your at_property value here");
    locationParams.put("locationSrc", (""+Utility.getInSharedPreference(ThankYouActivity.this,Constant.departure,"")));
    locationParams.put("locationDest", (""+Utility.getInSharedPreference(ThankYouActivity.this,Constant.destination,"")));

    Target.loadRequest(Constant.wetravel_context_dest, "", null, null, locationParams, new Target.TargetCallback<String>() {
        @Override
        public void call(final String response) {
        try {
            runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    AppDialogs.dialogLoaderHide();
                    filterRecommendationBasedOnOffer(recommandations, response);
                    recommandationbAdapter.notifyDataSetChanged();
                }
            });
        } catch (Exception e) {
            e.printStackTrace();
        }
        }
    });
    Target.clearPrefetchCache();
}
```

### Valideer de parameters van de Douane in het Levende Verzoek van de Plaats

Voer de emulator uit en open Logcat. Filter voor een van de parameters om te controleren of het verzoek de benodigde parameters bevat:
![ bevestigt de Parameters van de Douane in het Levende Verzoek van de Plaats ](assets/parameters_live_location_validation.jpg)

>[!NOTE]
>
>Bevestigingsverzoeken en parameters voor bestellingen: hoewel niet gebruikt in dit demoproject, worden orderdetails meestal vastgelegd in een echte implementatie, zodat in [!DNL Target] orderdetails kunnen worden gebruikt als metriek/afmetingen. Gelieve te verwijzen naar de documentatie voor instructies op hoe te [ het verzoek en de parameters van de ordesbevestiging uitvoeren ](https://experienceleague.adobe.com/docs/mobile-services/android/target-android/c-target-methods.html?lang=nl-NL).

>[!NOTE]
>
>Analytics for Target (A4T): Adobe Analytics kan worden geconfigureerd als rapportagebron voor [!DNL Target] . Hierdoor kunnen alle metriek/dimensies die door de Doel-SDK worden verzameld, in Adobe Analytics worden weergegeven. Zie het [ Overzicht A4T ](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t.html?lang=nl-NL) voor meer details.

Mooi werk! Nu er parameters zijn, zijn we klaar om die parameters te gebruiken om publiek en aanbiedingen te maken in Adobe Target.

**[VOLGENDE: &quot;creeer Soorten publiek en Aanbiedingen&quot; >](create-audiences-and-offers.md)**
