---
title: Functiemarkering
description: Adobe Target kan worden gebruikt om te experimenteren met UX-functies, zoals kleur, kopiëren, knoppen, tekst en afbeeldingen, en om deze functies aan specifieke doelgroepen te bieden.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 034d13f2-63b1-44b0-b3dc-867efe37672f
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Functiemarkering

Eigenaars van producten voor mobiele apps hebben de flexibiliteit nodig om nieuwe functies in hun app te implementeren zonder te hoeven investeren in meerdere app-releases. Om de doeltreffendheid te testen, kunnen zij ook de eigenschappen geleidelijk willen uitrollen tot een percentage van de gebruikersbasis. Adobe Target kan worden gebruikt om te experimenteren met UX-functies, zoals kleur, kopiëren, knoppen, tekst en afbeeldingen, en om deze functies aan specifieke doelgroepen te bieden.

In deze les maken we een &quot;feature flag&quot;-aanbieding die kan worden gebruikt als trigger om specifieke toepassingsfuncties in te schakelen.

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Een nieuwe locatie toevoegen aan de aanvraag voor de batchprefetch
* Een [!DNL Target] -activiteit maken met een aanbieding die wordt gebruikt als een functiemarkering
* De functiemarkering in uw app laden en valideren

## Een nieuwe locatie toevoegen aan de Prefetch-aanvraag aan de thuisactiviteit

In de demo-app uit onze vorige lessen voegen we een nieuwe locatie met de naam &quot;wetravel_feature_flag_recs&quot; toe aan het prefetch-verzoek in de Home Activity en laden we deze met een nieuwe Java-methode naar het scherm.

>[!NOTE]
>
>Één van de voordelen van het gebruiken van een prefetch verzoek is dat het toevoegen van een nieuw verzoek geen extra netwerkoverheadkosten toevoegt of extra ladingswerk veroorzaakt aangezien het verzoek binnen het prefetch verzoek wordt verpakt

Controleer eerst of de constante wetravel_feature_flag_recs is toegevoegd aan het bestand Constant.java:

![ voegt de constante van de eigenschapvlag ](assets/feature_flag_constant.jpg) toe

Hier volgt de code:

```java
public static final String wetravel_feature_flag_recs = "wetravel_feature_flag_recs";
```

Voeg nu de locatie toe aan de prefetch-aanvraag en laad een nieuwe functie met de naam `processFeatureFlags()` :

![ Code van de Vlag van de Eigenschap ](assets/feature_flag_code.jpg)

Hier volgt de volledige bijgewerkte code:

```java
public void targetPrefetchContent() {
    List<TargetPrefetchObject> prefetchList = new ArrayList<>();

    Map<String, Object> params1;
    params1 = new HashMap<String, Object>();
    params1.put("at_property", "7962ac68-17db-1579-408f-9556feccb477");

    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, params1));
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, params1));
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_feature_flag_recs, params1));

    Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
        @Override
        public void call(final Boolean status) {
            HomeActivity.this.runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    String cachingStatus = status ? "YES" : "NO";
                    System.out.println("Received Response from prefetch : " + cachingStatus);
                    engageMessage();
                    processFeatureFlags();
                    setUp();

                }
            });
        }};
    Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
}

public void processFeatureFlags() {
    Target.loadRequest(Constant.wetravel_feature_flag_recs, "", null, null, null,
            new Target.TargetCallback<String>(){
                @Override
                public void call(final String s) {
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            System.out.println("Feature Flags : " + s);
                            if(s != null && !s.isEmpty()) {
                                //enable or disable features
                            }
                        }
                    });
                }
            });
}
```

### Valideer de aanvraag voor een functiemarkering

Zodra de code wordt toegevoegd, stel de Mededinger op de Activiteit van het Huis in werking en bekijk Logcat voor de bijgewerkte reactie:

![ bevestigt de plaats van de eigenschapmarkering ](assets/feature_flag_code_logcat.jpg)

## Een JSON-aanbieding met functiemarkering maken

We gaan nu een eenvoudige JSON-aanbieding maken die fungeert als vlag of trigger voor een specifiek publiek, het publiek dat de functie-uitrol in zijn app zou ontvangen. Maak een nieuwe aanbieding in de interface van [!DNL Target] :

![ creeer de Vlag JSON van de Eigenschap ](assets/feature_flag_json_offer.jpg)

Laten wij het &quot;Vlag van de Eigenschap v1&quot;met de waarde &lbrace;&quot;toelaten&quot;:1 noemen

![ feature_flag_v1 JSON-aanbieding ](assets/feature_flag_json_name.jpg)

## Een activiteit maken

Laten we nu een A/B-testactiviteit maken met die aanbieding. Zie de vorige les voor gedetailleerde stappen voor het maken van een activiteit. De activiteit zal slechts één publiek voor dit voorbeeld nodig hebben. In een levend scenario, kunt u specifieke douanepubliek voor specifieke eigenschaproll-outs willen opbouwen, dan de activiteit plaatsen om dat publiek te gebruiken. In dit voorbeeld wijzen we alleen verkeer 50/50 toe (50% voor bezoekers die de functie-updates zouden zien en 50% voor bezoekers die een standaardervaring zouden zien). Hier is de configuratie voor de activiteit:

1. Geef de activiteit de naam &quot;Feature Flag&quot;
1. Selecteer de locatie &quot;wetravel_feature_flag_recs&quot;
1. Wijzig de inhoud in de JSON-aanbieding met de functie Vlag 1

   ![ Config van de Activiteit van de Vlag van de Eigenschap van de Eigenschap ](assets/feature_flag_activity.jpg)

1. Klik op **[!UICONTROL Add Experience]** om ervaring B toe te voegen.
1. De locatie &quot;wetravel_feature_flag_recs&quot; behouden
1. **[!UICONTROL Default Content]** behouden voor de inhoud
1. Klik op **[!UICONTROL Next]** om naar het [!UICONTROL Targeting] -scherm te gaan

   ![ Config van de Activiteit van de Vlag van de Eigenschap van de Eigenschap ](assets/feature_flag_activity_2.jpg)

1. Controleer in het scherm [!UICONTROL Targeting] of de methode [!UICONTROL Traffic Allocation] is ingesteld op de standaardinstelling (Handmatig) en of elke ervaring de standaardtoewijzing van 50% heeft. Selecteer **[!UICONTROL Next]** om naar **[!UICONTROL Goals & Settings]** te gaan.

   ![ Config van de Activiteit van de Vlag van de Eigenschap van de Eigenschap ](assets/feature_flag_activity_3.jpg)

1. Stel de waarde **[!UICONTROL Primary Goal]** in op **[!UICONTROL Conversion]** .
1. Stel de handeling in op **[!UICONTROL Viewed an Mbox]** . We gebruiken de locatie &quot;wetravel_context_dest&quot; (aangezien deze locatie zich op het bevestigingsscherm bevindt, kunnen we deze gebruiken om te zien of de nieuwe functie tot meer conversies leidt).
1. Klik op **[!UICONTROL Save & Close]**.

   ![ Config van de Activiteit van de Vlag van de Eigenschap van de Eigenschap ](assets/feature_flag_activity_4.jpg)

Activeer de activiteit.

## Valideer de kenmerkvlagactiviteit

Gebruik nu de emulator om te controleren op de aanvraag. Aangezien we de focus hebben ingesteld op 50% van de gebruikers, wordt een percentage van 50% weergegeven waarin de markering van de functie de waarde `{enable:1}` bevat.

![ Bevestiging van de Vlag van de Eigenschap ](assets/feature_flag_validation.jpg)

Als u de waarde `{enable:1}` niet ziet, betekent dat dat u niet voor de ervaring bent aangewezen. Als tijdelijke test kunt u het voorstel afdwingen om te tonen:

1. Deactiveer de activiteit.
1. Verander de verkeerstoewijzing in 100% op de nieuwe eigenschapervaring.
1. Opslaan en opnieuw activeren.
1. Veeg de gegevens over de emulator en start de app opnieuw.
1. De aanbieding moet nu de waarde `{enable:1}` retourneren.

In een live scenario kan de reactie van `{enable:1}` worden gebruikt om meer aangepaste logica in uw app in te schakelen voor het weergeven van de specifieke functieset die u voor het doelpubliek wilt weergeven.

## Conclusie

Mooi werk! U hebt nu de vaardigheden nodig om eigenschappen aan specifiek gebruikerspubliek uit te voeren.
