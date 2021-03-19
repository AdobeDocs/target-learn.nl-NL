---
title: Adobe Target-verzoeken toevoegen
description: 'De Adobe Mobile Services SDK (v4) biedt Adobe Target-methoden en -functionaliteit waarmee u uw app kunt aanpassen met verschillende ervaringen voor verschillende gebruikers.   '
role: Ontwikkelaar
level: Intermediair
topic: Mobiel, persoonlijke instellingen
feature: Mobiel implementeren
doc-type: tutorial
kt: 3040
thumbnail: null
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '1810'
ht-degree: 0%

---


# Adobe Target-verzoeken toevoegen

De Adobe Mobile Services SDK (v4) biedt Adobe Target-methoden en -functionaliteit waarmee u uw app kunt aanpassen met verschillende ervaringen voor verschillende gebruikers. Doorgaans worden een of meer verzoeken vanuit de app naar de Adobe Target gedaan om de gepersonaliseerde inhoud op te halen en het effect van die inhoud te meten.

In deze les, zult u de Wij.Travel app voor verpersoonlijking door [!DNL Target] verzoeken uit te voeren voorbereiden.

## Vereisten

Zorg dat u de voorbeeldtoepassing [downloadt en bijwerkt](download-and-update-the-sample-app.md).

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Meerdere [!DNL Target] aanbiedingen in de cache plaatsen (d.w.z. gepersonaliseerde inhoud) die een aanvraag voor een batchprefetch gebruiken
* Vooraf ingestelde [!DNL Target] locaties laden
* Een [!DNL Target]-locatie in realtime laden (niet vooraf ingesteld)
* Vooraf ingestelde locaties uit cache wissen
* Valideer vooraf ingestelde en real-time verzoeken

## Terminologie

Hieronder vindt u een aantal belangrijke doelterminologie die we in de rest van deze zelfstudie zullen gebruiken.

* **Verzoek:**  een netwerkaanvraag naar de Adobe Target-servers
* **Aanbieding:**  een codefragment of andere op tekst gebaseerde inhoud, gedefinieerd in de  [!DNL Target] gebruikersinterface (of met API), dat in de reactie wordt geleverd. Doorgaans JSON wanneer [!DNL Target] wordt gebruikt in systeemeigen mobiele apps.
* **Locatie:**  een door de gebruiker gedefinieerde naam die aan een aanvraag wordt gegeven, gebruikt in de  [!DNL Target] interface om aanbiedingen aan specifieke verzoeken te koppelen
* **Batchaanvraag:**  één aanvraag die meerdere locaties bevat
* **Prefetch-aanvraag:**  één aanvraag die aanbiedingen ophaalt en deze in het geheugen ophaalt voor toekomstig gebruik in de app
* **Batchvoorkeursaanvraag:**  één aanvraag die prefetches bieden voor meerdere locaties
* **Publiek:**  een groep bezoekers, gedefinieerd in de  [!DNL Target] interface of gedeeld  [!DNL Target] vanuit andere Adobe-toepassingen (bijvoorbeeld &quot;iPhone X bezoekers&quot;, &quot;bezoekers in Californië&quot;, &quot;Eerste app geopend&quot;)
* **Activiteit:**  een  [!DNL Target] constructie, die in het  [!DNL Target] gebruikersinterface (of met API) wordt bepaald die plaatsen, aanbiedingen en Soorten publiek verbindt om een gepersonaliseerde ervaring tot stand te brengen

## Een aanvraag voor een batchvoorvertoning toevoegen

Het eerste verzoek dat wij in Wij.Travel zullen uitvoeren is een partijprefetch verzoek met twee [!DNL Target] plaatsen op het Homescherm. In een recentere les, zullen wij aanbiedingen voor deze plaatsen vormen die berichten tonen helpen nieuwe gebruikers door het boekingsproces begeleiden.

Met een Prefetch-aanvraag wordt [!DNL Target]-inhoud zo min mogelijk opgehaald door de Adobe Target-serverreactie (aanbieding) in cache te plaatsen. Een batch-prefetch-aanvraag haalt meerdere aanbiedingen op en plaatst deze in het cachegeheugen, elk gekoppeld aan een andere locatie. Alle vooraf ingestelde locaties worden in het cachegeheugen opgeslagen op het apparaat voor toekomstig gebruik in de gebruikerssessie. Door meerdere locaties vooraf in te stellen op het Basisscherm, kunnen we aanbiedingen ophalen die later kunnen worden gebruikt wanneer de bezoeker door de app navigeert. Raadpleeg de [prefetch documentatie](https://docs.adobe.com/content/help/en/mobile-services/android/target-android/c-mob-target-prefetch-android.html) voor meer informatie over prefetch methoden.

### De aanvraag Batch Prefetch toevoegen

Werk de HomeActivity-controller (de broncode van het Homescherm) bij. Deze bevindt zich onder app > main > java > com.wetravel > Controller. De twee in rood weergegeven codeblokken worden toegevoegd:

We beginnen met de HomeActivity-controller (de broncode van het Homescherm), die zich bevindt onder app > main > java > com.wetravel > Controller.

De twee in rood weergegeven codeblokken worden toegevoegd:

![Prefetch-code voor HomeActivity](assets/homeactivity.jpg)

Schuif omlaag naar het einde van de code van HomeActivity en voeg de code hieronder toe na de functie `setHeader()` en *het vervangen van* de huidige functie `onResume()`:

```java
@Override
protected void onResume() {
    super.onResume();
    targetPrefetchContent();
}

public void targetPrefetchContent() {
    List<TargetPrefetchObject> prefetchList = new ArrayList<>();
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, null));
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, null));
    Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
        @Override
        public void call(final Boolean status) {
            HomeActivity.this.runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    String cachingStatus = status ? "YES" : "NO";
                    System.out.println("Received Response from prefetch : " + cachingStatus);
                    setUp();

                }
            });
        }};
    Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
}
```

Uw winde zal u waarschijnlijk waarschuwen dat u niet de [!DNL Target] klassen in het dossier hebt ingevoerd. Zorg ervoor dat u de [!DNL Target]-klassen boven aan de HomeActivity-controller importeert, zoals hieronder in het rood wordt weergegeven:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

![De doelklassen importeren](assets/import.jpg)

U zult waarschijnlijk ook fouten voor &quot;kunnen geen symbool veranderlijke wetravel_engt_home&quot;vinden en &quot;kan symboolvariabele wetravel_engt_search&quot;niet vinden. Voeg deze toe aan het `Constant.java`-bestand (in app > src > main > java > com > wetravel > Utils):

```java
public static final String wetravel_engage_home = "wetravel_engage_home";
public static final String wetravel_engage_search = "wetravel_engage_search";
```

![Locatienamen toevoegen aan het bestand Constant.java](assets/constants.jpg)

### Codeuitleg voor batchvoorkeursaanvraag

| Code | Beschrijving |
|--- |--- |
| `targetPrefetchContent()` | Een door de gebruiker gedefinieerde functie (geen onderdeel van de SDK) die [!DNL Target]-methoden gebruikt om twee [!DNL Target]-locaties op te halen en in cache op te slaan. |
| `prefetchContent()` | De [!DNL Target] SDK-methode die de prefetch-aanvraag verzendt |
| `Constant.wetravel_engage_home` | Vooraf ingestelde [!DNL Target]-locatienaam die de inhoud van het aanbod op het Homescherm weergeeft |
| `Constant.wetravel_engage_search` | Vooraf geplaatste [!DNL Target] locatienaam die zijn aanbiedingsinhoud op het Scherm van de Resultaten van het Onderzoek zal tonen. Aangezien dit een tweede locatie in de prefetch is, wordt deze Prefetch-aanvraag een &quot;Prefetch-batchaanvraag&quot; genoemd. |
| setUp() | Een door de gebruiker gedefinieerde functie die het beginscherm van de app rendert nadat de [!DNL Target] aanbiedingen zijn voorafgegaan |

### Info over Asynchroon versus Synchroon

Met de code die wij net hebben uitgevoerd, wordt het prefetch verzoek gemaakt als synchrone, blokkerende vraag, enkel alvorens het huisscherm teruggeeft. Toen wij de nieuwe code in het controlemechanisme HomeActivity kleedden, verplaatsten wij `setUp()` functieuitvoering van de `onResume()` functie tot na het verzoek van het Doel. Dit kan nuttig zijn in scenario&#39;s waar u inhoud wilt personaliseren wanneer app eerst opent omdat het ervoor zorgt dat de gepersonaliseerde inhoud van de servers van het Doel is teruggekeerd (of uit tijd) alvorens het eerste scherm teruggeeft. Om de verzoeken toe te staan om asynchroon (in de achtergrond) te laden, enkel roepen `setUp()` binnen de `onCreate()` functie in plaats daarvan.

### De aanvraag Batch Prefetch valideren

Maak de app opnieuw en open de Android-emulator. (De volgende schermafbeeldingen gebruiken Pixel 2 op Android Q versie 9+, API niveau 29). In het Prefetch-antwoord moet &quot;ontvangen prefetch-reactie&quot; worden gelezen:

Wanneer het startscherm wordt weergegeven, moet de prefetch-aanvraag worden geladen. Met Logcat, filter voor [!DNL "Target"] om het verzoek en de reactie te zien:

![Valideer de aanvragen op het Homescherm](assets/prefetch_validation.jpg)

Als u geen succesvolle reactie ziet, verifieer montages in het `ADBMobileConfig.json` dossier en codesyntaxis in het dossier HomeActivity.

Twee locaties worden nu in cache geplaatst op het apparaat. De locatienamen worden over enkele ogenblikken geladen in de [!DNL Target]-interface, waar ze in verschillende vervolgkeuzemenu&#39;s kunnen worden geselecteerd wanneer u ze in een activiteit gebruikt.

### Aanvragen voor laden toevoegen voor elke in cache geplaatste locatie

Nu de locaties vooraf zijn ingesteld en de reacties op deze locaties in het cachegeheugen zijn opgeslagen, voegen we de methode `Target.loadRequest()` toe waarmee de aanbiedingsinhoud wordt opgehaald uit het cachegeheugen, zodat u deze kunt gebruiken om de toepassing bij te werken. Wij zullen een nieuwe douanemethode genoemd `engageMessage()` toevoegen die met het prefetch verzoek zal lopen. `engageMessage()` zal bellen  `Target.loadRequest()`. `engageMessage()` loopt vóór  `setUp()` om ervoor te zorgen dat het ladingsverzoek wordt geroepen alvorens het scherm opstelling is.

Eerst, voeg `engageMessage()` vraag &amp; methode voor wetravel_commit_home plaats in HomeActivity toe:

![Eerste aanvraag voor laden toevoegen](assets/wetravel_engage_home_loadRequest.jpg)

Hier volgt de bijgewerkte code:

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
    public void engageMessage() {
        Target.loadRequest(Constant.wetravel_engage_home, "", null, null, null,
            new Target.TargetCallback<String>(){
                @Override
                public void call(final String s) {
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            System.out.println("Engage Message : " + s);
                            if(s != null && !s.isEmpty()) Utility.showToast(getApplicationContext(), s);
                        }
                    });
                }
            });
    }
```

Voeg nu `engageMessage()` vraag &amp; methode voor de wetravel_engt_search plaats in SearchBusActivity toe. Merk op dat de `engageMessage()` vraag in de `onResume()` methode vóór de vraag aan `setUpSearch()` wordt geplaatst zodat loopt het alvorens het scherm opstelling is:

![Tweede aanvraag voor laden toevoegen](assets/wetravel_engage_search_loadRequest.jpg)

Hier volgt de bijgewerkte code:

```java
    @Override
    public void onResume() {
        super.onResume();
        engageMessage();
        setUpSearch();
    }
    public void engageMessage() {
        Target.loadRequest(Constant.wetravel_engage_search, "", null, null, null,
                new Target.TargetCallback<String>(){
                    @Override
                    public void call(final String s) {
                        runOnUiThread(new Runnable() {
                            @Override
                            public void run() {
                                System.out.println("Engage Message : " + s);
                                if(s != null && !s.isEmpty()) Utility.showToast(getApplicationContext(), s);
                            }
                        });
                    }
                });
    }
```

Aangezien u enkel de methodes van het Doel aan SearchBusActivity hebt toegevoegd, ben zeker om de [!DNL Target] klassen in te voeren:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

## Een aanvraag in realtime toevoegen

Het volgende verzoek dat we aan de app toevoegen, wordt een realtime aanvraag op het scherm Bedankt. Met &quot;real-time&quot; bedoelen we dat zowel het verzoek als het antwoord onmiddellijk zullen worden toegepast (niet in cache geplaatst voor later). In een recentere les, zullen wij een ervaring gebruikend dit verzoek bouwen, die aan de reisbestemming van de gebruiker gepersonaliseerd is.

Laten we dus een aanvraag in real time toevoegen op het scherm Dankuwel. In het bestand BedanktYouActivity voeren we de wijzigingen in het rood aan:
![Voeg een plaats in real time op het Dank u Scherm toe](assets/thankyou.jpg)

Blader naar het einde van het bestand DankuwelActivity. Maak een commentaarregel van de drie regels in de functie `getRecommandations()` en voeg de aanroep van de functie `targetLoadRequest()` toe:

```java
// AppDialogs.dialogLoaderHide();
// recommandations.addAll(recommandation.recommandations);
// recommandationbAdapter.notifyDataSetChanged();
```

Voeg deze coderegel toe aan de functie `getRecommandations()`:

```java
targetLoadRequest(recommandation.recommandations);
```

Nu moeten we de functie `targetLoadRequest()` definiëren:
![Voeg een locatie in real time toe op het scherm Bedankt](assets/thankyou2.jpg)

Voeg dit codeblok na de functie `filterRecommendationBasedOnOffer()` toe:

```java
public void targetLoadRequest(final ArrayList<Recommandation> recommandations) {
    Target.loadRequest(Constant.wetravel_context_dest, "", null, null, null, new Target.TargetCallback<String>() {
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
}
```

Aangezien u enkel de methodes van het Doel aan DankYouActivity hebt toegevoegd, ben zeker om de klassen van het Doel in te voeren:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

### targetLoadRequest() Codeuitleg

| Code | Beschrijving |
|--- |--- |
| `targetLoadRequest()` | Een door de gebruiker gedefinieerde functie (geen onderdeel van de SDK) die `Target.loadRequest()` activeert en de locatie wetravel_context_dest laadt en weergeeft |
| `Target.loadRequest()` | De methode van SDK die het verzoek aan de server van het Doel doet |
| Constant.wetravel_context_dest | De plaatsnaam die aan het verzoek wordt toegewezen dat wij later zullen gebruiken wanneer wij de activiteit in de [!DNL Target] interface bouwen |
| `filterRecommendationBasedOnOffer()` | Een door de gebruiker gedefinieerde functie in de app die de aanbieding van de locatie overneemt vanuit het doelantwoord en die bepaalt hoe de app moet worden gewijzigd op basis van de inhoud van de aanbieding |
| `recommandations.addAll()` | Een door de gebruiker gedefinieerde functie in de app die standaard werd uitgevoerd wanneer het scherm Dankuwel werd geladen, maar die nu wordt uitgevoerd nadat het antwoord Doel is ontvangen en geparseerd door `filterRecommendationBasedOnOffer()` |

Dit was een meer geavanceerde update die we naar de app maakten met het verzoek dat we aan het thuisscherm toevoegden. Laten we even even kijken wat we deden:

1. We hebben het eerdere gedrag van de app onderbroken door drie standaardpromoties weer te geven door opmerkingen te maken over de coderegels
1. We hebben de toepassing gevraagd een nieuwe functie uit te voeren, die we willekeurig targetLoadRequest noemden
1. We hebben de functie `targetLoadRequest` gedefinieerd om een verzoek aan Target uit te voeren met de methode Target.loadRequest en de functie `filterRecommendationBasedOnOffer()` onmiddellijk uit te voeren wanneer de aanbiedingsreactie [!DNL Target] is ontvangen
1. De functie `filterRecommendationBasedOnOffer()` interpreteert de reactie en bepaalt welke promoties op het scherm moeten worden toegepast

Dit is een gebruikspatroon dat veel wordt gebruikt bij het gebruik van [!DNL Target] in mobiele apps.  Het is beide zeer krachtig, omdat u bijna elk aspect van uw mobiele app kunt aanpassen. Het vereist ook coördinatie tussen de toepassingscode en de aanbiedingen die wij later in de [!DNL Target] interface zullen bepalen. Vanwege deze coördinatie is het mogelijk dat u uw app in de App Store moet bijwerken om de activiteit te kunnen starten. In sommige gevallen kunt u dit doen voor het gebruik van personalisatie.

### Valideer het Real-time Verzoek

Open de Android-emulator en voer alle stappen uit om een trip te boeken: Home > Zoekresultaten > Selectie plaatsen, Betalingsopties (elke betalingsoptie met lege gegevens werkt).

Kijk op het scherm &#39;Hartelijk dank&#39; naar Logcat voor het antwoord. De reactie moet als volgt luiden: &quot;Standaardinhoud is geretourneerd voor &quot;wetravel_context_dest&quot;:

![Een locatie in realtime toevoegen op het scherm Bedankt](assets/thankyou_validation.jpg)

## Vooraf ingestelde locaties uit cache wissen

Er kunnen situaties zijn waarin vooraf ingestelde locaties tijdens een sessie moeten worden gewist. Wanneer bijvoorbeeld een reservering plaatsvindt, is het verstandig om de in de cache opgeslagen locaties te wissen, aangezien de gebruiker nu ‘betrokken’ is en het boekingsproces begrijpt. Als zij een andere reis tijdens hun zitting boeken, zullen zij niet de originele plaatsen op het homescherm en het scherm van onderzoeksresultaten nodig hebben om hun het boeken te begeleiden. Het zou zinvoller zijn om de locaties uit het cachegeheugen te wissen en nieuwe aanbiedingen voor misschien een verkorte tweede boeking of een ander relevant scenario vooraf in te stellen. De logica kan aan het homescherm en het scherm van onderzoeksresultaten worden toegevoegd om nieuwe plaatsen voor te bereiden als het boeken tijdens de zitting heeft plaatsgevonden.

Voor dit voorbeeld, zullen wij enkel vooraf ingestelde plaatsen voor de zitting ontruimen wanneer het boeken plaatsvindt. Dit wordt gedaan door de `Target.clearPrefetchCache()` functie te roepen. Stel de functie in de functie `targetLoadRequest()` in, zoals hieronder wordt getoond:

```java
Target.clearPrefetchCache()
```

![Vooraf ingestelde locaties uit cache wissen](assets/clearPrefetch.jpg)

Gefeliciteerd! Uw app beschikt nu over het framework voor personalisatie. In de volgende les, zullen wij onze verpersoonlijkingsmogelijkheden verbeteren door parameters aan deze plaatsen toe te voegen.

**[VOLGENDE: &quot;Parameters toevoegen&quot; >](add-parameters.md)**
