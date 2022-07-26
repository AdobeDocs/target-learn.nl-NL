---
title: A4T-rapporten instellen in Analysis Workspace voor activiteiten voor automatisch doel
description: Zodra u uw Analytics voor de integratie van het Doel (A4T) op zijn plaats hebt en u activiteiten Auto-Target in werking stelt, hoe kunt u ervoor zorgen u correct resultaten interpreteert? Voer de volgende stappen uit om A4T-rapporten in Analysis Workspace te configureren om de verwachte resultaten te verkrijgen bij het uitvoeren van Auto-Target-activiteiten.
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 58006a25-851e-43c8-b103-f143f72ee58d
source-git-commit: 2571964b557f696d8e0377b922d96e90611f2327
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# A4T-rapporten instellen in [!DNL Analysis Workspace] for [!DNL Auto-Target] activiteiten

>[!IMPORTANT]
>
>Voor [!UICONTROL Auto-Target] activiteiten, moet u de rapportage controleren [!DNL Analytics Workspace] en maakt u handmatig een A4T-deelvenster.

De [!UICONTROL Analytics for Target] (A4T) integratie voor [!DNL Auto-Target] activiteiten gebruiken [!DNL Adobe Target]Met ML-algoritmen (ensemble Machine Learning) kunt u de beste ervaring kiezen voor elke bezoeker op basis van zijn profiel, gedrag en context, terwijl u een [!DNL Adobe Analytics] doel-metrisch.

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in [!DNL Adobe Analytics] [!DNL Analysis Workspace], enkele wijzigingen in de standaardwaarde **[!UICONTROL Analytics for Target]** het deelvenster moet correct worden geïnterpreteerd [!DNL Auto-Target] activiteiten, als gevolg van verschillen tussen experimentele activiteiten (handleiding A/B en automatische toewijzing) en personalisatieactiviteiten ([!UICONTROL Auto-Target]).

Deze zelfstudie doorloopt de aanbevolen wijzigingen voor het analyseren [!UICONTROL Auto-Target] activiteiten in [!DNL Workspace], die gebaseerd zijn op de volgende sleutelbegrippen:

* De **[!UICONTROL Control vs Targeted]** De dimensie kan worden gebruikt om tussen de ervaringen van de Controle versus die te onderscheiden die door [!UICONTROL Auto-Target] ensemble ML algorithm.
* Bezoekingen moeten worden gebruikt als de normaliserende maatstaf bij het bekijken van baanbrekingen van prestaties op ervaringsniveau. Daarnaast [De standaardtelmethode van Adobe Analytics kan bezoeken omvatten waarbij de gebruiker geen activiteiteninhoud ziet](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-faq/a4t-faq-viewing-reports.html?lang=en#metrics), maar dit standaardgedrag kan worden gewijzigd door een segment met het juiste bereik te gebruiken (details verderop).
* Visit-lookback scoped attributie-ook gekend als &quot;bezoek lookback venster&quot;op het voorgeschreven attribuut model-wordt gebruikt door [!DNL Adobe Target]ML-modellen tijdens de trainingsfasen en hetzelfde (niet-standaard) attributiemodel moet worden gebruikt bij het afbreken van de metrische doelstelling.

## A4T maken voor [!UICONTROL Auto-Target] in [!DNL Workspace]

Een A4T maken voor [!UICONTROL Auto-Target] rapport, of begin met **[!UICONTROL Analytics for Target]** in [!DNL Workspace], zoals hieronder wordt getoond, of beginnen met een vrije-vormlijst. Maak vervolgens de volgende selecties:

1. **[!UICONTROL Control Experience]**: U kunt elke ervaring kiezen; u zult deze keuze later echter overschrijven. Let op: voor [!UICONTROL Auto-Target] De ervaring met controle is in feite een controlestrategie, die ofwel a) willekeurig dienst doet bij alle ervaringen, ofwel b) één ervaring dient (deze keuze wordt gemaakt op het moment dat de activiteit wordt gecreëerd in [!DNL Adobe Target]). Zelfs als u voor keuze (b) koos—uw [!UICONTROL Auto-Target] activiteit aangewezen een specifieke ervaring als controle-u zou nog de benadering moeten volgen die in dit leerprogramma voor het analyseren van A4T voor wordt geschetst [!UICONTROL Auto-Target] activiteiten.
2. **[!UICONTROL Normalizing Metric]**: Selecteer Bezoeken.
3. **[!UICONTROL Success Metrics]**: Hoewel u om het even welke metrisch(e) kunt selecteren waarop om te melden, zou u rapporten over het algemeen over zelfde metrisch moeten bekijken die voor optimalisering tijdens activiteitenverwezenlijking binnen werd gekozen [!DNL Target].

![Figuur1.png](assets/Figure1.png)
*Afbeelding 1: [!UICONTROL Analytics for Target] deelvenster instellen voor [!UICONTROL Auto-Target] activiteiten.*

>[!NOTE]
>
>Als u uw [!UICONTROL Analytics for Target] deelvenster voor [!UICONTROL Auto-Target] activiteiten, kiest u een ervaring in het beheer en kiest u [!UICONTROL Visits] als normaliserend metrisch, en kies het zelfde doel metrisch dat voor optimalisering tijdens werd gekozen [!DNL Target] activiteiten creëren.

## Gebruik de [!UICONTROL Control vs.Targeted] dimensie die moet worden vergeleken [!DNL Target] ML-model samenvoegen tot uw besturingselement

Het standaard A4T-paneel is ontworpen voor klassieke (handmatige) A/B-tests of [!UICONTROL Auto-Allocate] activiteiten waarbij het doel is de prestaties van individuele ervaringen te vergelijken met die van de controleervaring. In [!UICONTROL Auto-Target] de activiteiten, maar de eerste ordervergelijking moet tussen de *strategie* en de *strategie* (met andere woorden, het bepalen van de totale prestatie van de [!UICONTROL Auto-Target] het ML-model samenvoegen boven de controlestrategie).

Voor deze vergelijking gebruikt u de opdracht **[!UICONTROL Control vs Targeted (Analytics for Target)]** dimensie. Sleep en zet neer om de **[!UICONTROL Target Experiences]** dimensie in het standaardA4T rapport.

Deze vervanging maakt de standaardberekeningen voor het optillen en vertrouwen in het deelvenster A4T ongeldig. Om verwarring te voorkomen, kunt u deze metriek uit het standaardpaneel verwijderen, verlatend het volgende rapport:

![Figuur2.png](assets/Figure2.png)

*Afbeelding 2: Het aanbevolen basislijnrapport voor [!DNL Auto-Target] activiteiten. Dit rapport is gevormd om gericht verkeer (gediend door het ensemble model van ML) tegen uw verkeer van de Controle te vergelijken.*

>[!NOTE]
>
>Op dit moment zijn nummers voor optillen en vertrouwen niet beschikbaar voor [!UICONTROL Control vs Targeted] afmetingen voor A4T-rapporten voor [!UICONTROL Auto-Target]. Totdat ondersteuning is toegevoegd, kunt u optillen en vertrouwen handmatig berekenen door de [betrouwbaarheidscalculator](https://experienceleague.adobe.com/docs/target/assets/complete_confidence_calculator.xlsx?lang=en).

## Uitsplitsingen op ervaringsniveau toevoegen

Als u meer inzicht wilt krijgen in de manier waarop het ensemble ML-model presteert, kunt u de onderverdelingen op ervaringsniveau van de **[!UICONTROL Control vs Targeted]** dimensie. In [!DNL Workspace], sleept u de **[!UICONTROL Target Experiences]** dimensie op uw rapport, dan onderverdeeld elk van de Controle en de gerichte dimensies afzonderlijk.

![Figuur3.png](assets/Figure3.png)
*Figuur 3: Verdeling van de gerichte dimensie door de Ervaringen van het Doel*

Hier wordt een voorbeeld van het resulterende rapport weergegeven.

![Figuur4.png](assets/Figure4.png)
*Figuur 4: Een norm [!UICONTROL Auto-Target] rapporteren met uitsplitsingen op ervaringsniveau. Merk op uw doel metrisch zou kunnen verschillend zijn, en uw strategie van de Controle kan één enkele ervaring hebben.*

>[!TIP]
>
>In [!DNL Workspace]klikt u op het tandwielpictogram om de percentages in het dialoogvenster [!UICONTROL Conversion Rate] om de focus op de ervaringsomrekeningskoersen te houden. De conversiekoersen worden vervolgens opgemaakt als decimalen, maar worden dienovereenkomstig als percentages geïnterpreteerd.

## Waarom &quot;Bezoekingen&quot; de juiste normalisatiemethode is voor [!UICONTROL Auto-Target] activiteiten

Bij het analyseren van een [!UICONTROL Auto-Target] activiteit, altijd kiezen [!UICONTROL Visits] als standaard normaliserend metrisch. [!UICONTROL Auto-Target] personalisatie kiest een ervaring voor een bezoeker eenmaal per bezoek ( formeel , eenmaal per bezoek ) [!DNL Adobe Target] sessie), wat betekent dat de ervaring die een gebruiker wordt getoond, tijdens elk bezoek kan veranderen. Als u [!UICONTROL Unique Visitors] als het normaliseren metrisch, zou het feit dat één enkele gebruiker veelvoudige ervaringen (over verschillende bezoeken) zou kunnen uiteindelijk tot verwarrende omzettingspercentages leiden.

Dit wordt in een eenvoudig voorbeeld geïllustreerd: overwegen een scenario waarin twee bezoekers een campagne aangaan die slechts twee ervaringen heeft. De eerste bezoeker bezoekt tweemaal. Zij worden toegewezen aan Experience A tijdens het eerste bezoek, maar beleven B tijdens het tweede bezoek (vanwege hun profielstatus die veranderde bij dat tweede bezoek). Na het tweede bezoek converteert de bezoeker een bestelling. De conversie wordt toegeschreven aan de ervaring die het laatst is opgedaan (Experience B). De tweede bezoeker bezoekt ook twee keer, en wordt Ervaring B getoond beide keer, maar nooit omzet.

Laten we de verslagen op bezoekersniveau en op bezoekersniveau vergelijken:

| Ervaring | Unieke bezoekers | Bezoeken | Conversies | Norm van bezoeker. Conv. Snelheid | Bezoek norm. Conv. Snelheid |
| --- | --- | --- | --- | --- | --- |
| A | 1 | 1 | - | 0% | 0% |
| B | 2 | 3 | 1 | 50% | 33,3% |
| Totalen | 2 | 4 | 1 | 50% | 25% |

*Tabel 1: Voorbeeld waarin bezoekers-genormaliseerde en bezoek-genormaliseerde rapporten voor een scenario worden vergeleken waarin de besluiten aan een bezoek kleven (en niet bezoeker, zoals met regelmatige tests A/B). De bezoeker-genormaliseerde metriek zijn verwarrend in dit scenario.*

Zoals uit de tabel blijkt, is er een duidelijke incongruentie van bezoekersaantallen. Ondanks het feit dat er in totaal twee unieke bezoekers zijn, is dit geen som van afzonderlijke unieke bezoekers voor elke ervaring. Hoewel de conversiekoers op bezoekersniveau niet noodzakelijkerwijs verkeerd is, hebben conversietarieven op bezoekniveau bij vergelijking van individuele ervaringen waarschijnlijk veel meer zin. Formeel is de eenheid van analyse (&quot;bezoeken&quot;) dezelfde als de eenheid van beslissingswaanzin, wat betekent dat uitsplitsingen van meetgegevens op ervaringsniveau kunnen worden toegevoegd en vergeleken.

## Filter voor feitelijke bezoeken aan de activiteit

De [!DNL Adobe Analytics] standaardmethode voor het tellen van bezoeken aan een [!DNL Target] activiteit zou bezoeken kunnen omvatten waar de gebruiker niet met [!DNL Target] activiteit. Dit is te wijten aan de manier waarop [!DNL Target] activiteitstoewijzingen blijven bestaan in de [!DNL Analytics] context bezoeker. Het aantal bezoeken aan de [!DNL Target] de activiteit kan soms worden opgevoerd , wat leidt tot een verlaging van de omrekeningskoersen .

Als u liever melding wilt maken van bezoeken waar de gebruiker daadwerkelijk met de [!UICONTROL Auto-Target] activiteit (door toegang tot de activiteit, een display/visit-gebeurtenis of een conversie), kunt u:

1. Maak een specifiek segment dat resultaten van het [!DNL Target] de betrokken activiteit, en vervolgens
1. Filter de [!UICONTROL Visits] metrisch gebruikend dit segment.

**Het segment maken:**

1. Selecteer **[!UICONTROL Components > Create Segment]** in de [!DNL Workspace] werkbalk.
2. Voer een **[!UICONTROL Title]** voor uw segment. In het onderstaande voorbeeld krijgt het segment de naam [!DNL "Hit with specific Auto-Target activity"].
3. Sleep de **[!UICONTROL Target Activities]** dimensie van het segment **[!UICONTROL Definition]** sectie.
4. Gebruik de **[!UICONTROL equals]** operator.
5. Zoeken naar uw specifieke [!DNL Target] activiteit.
6. Selecteer het tandwielpictogram en selecteer vervolgens **[!UICONTROL Attribution model > Instance]** zoals weergegeven in onderstaande afbeelding.
7. Klik op **[!UICONTROL Save]**.

![Figuur5.png](assets/Figure5.png)
*Figuur 5: Gebruik een segment zoals dat hier wordt getoond om het [!UICONTROL Visits] Metrisch in uw A4T voor [!UICONTROL Auto-Target] verslag*

Nadat het segment is gemaakt, filtert u het [!UICONTROL Visits] metrisch, dus [!UICONTROL Visits] metrisch omvat alleen bezoeken waar de gebruiker interactie had met de [!DNL Target] activiteit.

**Naar filter [!UICONTROL Visits] dit segment gebruiken:**

1. Sleep het nieuwe segment van de componentenwerkbalk en houd de muisaanwijzer boven de basis van het segment **[!UICONTROL Visits]** metrisch label tot een blauw **[!UICONTROL Filter by]** wordt weergegeven.
2. Laat het segment los. Het filter wordt op die metrische waarde toegepast.

Het uiteindelijke deelvenster wordt als volgt weergegeven.

![Figuur 6.png](assets/Figure6.png)
*Figuur 6: Rapportpaneel met het segment Activiteit voor automatisch aanwijzen toegepast op het segment [!UICONTROL Visits] metrisch. Dit zorgt alleen voor bezoeken waarbij een gebruiker daadwerkelijk met de [!DNL Target] de betrokken activiteit is in het verslag opgenomen .*

## Zorg ervoor dat de maatstaf van het doel en de kenmerk zijn uitgelijnd op het optimalisatiecriterium

De integratie A4T maakt de [!UICONTROL Auto-Target] Te gebruiken ML-model *opgeleid* dezelfde conversiegebeurtenisgegevens gebruiken die [!DNL Adobe Analytics] gebruiken voor *prestatierapporten genereren*. Er zijn echter bepaalde veronderstellingen die moeten worden gebruikt bij de interpretatie van deze gegevens bij de opleiding van de modellen van het XML, die verschillen van de standaardveronderstellingen die tijdens de rapportagefase in [!DNL Adobe Analytics].

In het bijzonder de [!DNL Adobe Target] In ML-modellen wordt een &quot;visit-scoped&quot;-attributiemodel gebruikt. Met andere woorden, zij gaan ervan uit dat een conversie moet plaatsvinden tijdens hetzelfde bezoek als een weergave van inhoud voor de activiteit, zodat de conversie &quot;toegeschreven&quot; kan worden aan het besluit van het ML-model. Dit is vereist voor [!DNL Target] de tijdige opleiding van haar modellen te waarborgen; [!DNL Target] kan maximaal 30 dagen wachten op een conversie (het standaardtoewijzingsvenster voor rapporten in [!DNL Adobe Analytics]), alvorens deze op te nemen in de opleidingsgegevens voor haar modellen.

Het verschil tussen de door de [!DNL Target] modellen (tijdens training) versus de standaardtoewijzing die wordt gebruikt in het opvragen van gegevens (tijdens het genereren van rapporten) kunnen tot discrepanties leiden. Het kan zelfs lijken dat de modellen van het ML slecht presteren, terwijl de kwestie eigenlijk bij attributie ligt.

>[!TIP]
>
>Als de modellen van ML voor metrisch optimaliseren die verschillend van dat van de metriek wordt toegeschreven u in een rapport bekijkt, kunnen de modellen niet zoals verwacht presteren! Om dit te vermijden, verzeker de doelmetriek op uw rapport de zelfde metrische definitie en attributie gebruiken die door de modellen van XML van Doel wordt gebruikt.

De exacte metrische definitie en attribuutinstellingen zijn afhankelijk van de [optimalisatiecriterium](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#supported) u hebt opgegeven tijdens het maken van activiteiten.

### Doelgedefinieerde conversies of Analytische gegevens met *Metrische waarde maximaliseren per bezoek*

Wanneer metrisch een omzetting van het Doel of een metriek Analytics met is **Metrische waarde maximaliseren per bezoek**, staat de doel metrische definitie voor veelvoudige omzettingsgebeurtenissen toe om in het zelfde bezoek voor te komen.
Ga als volgt te werk om doelmetriek weer te geven met dezelfde toewijzingsmethode die door Adobe Target ML-modellen wordt gebruikt:

![gearicon.png](assets/gearicon.png)

1. Blader vanuit het resulterende menu naar **[!UICONTROL Data settings]**.
1. Selecteren **[!UICONTROL Use non-default  attribution model]** (indien nog niet geselecteerd):

![non-default attributionmodel.png](assets/non-defaultattributionmodel.png)

1. Klik op **[!UICONTROL Edit]**.
1. Selecteren **[!UICONTROL Model]**: **[!UICONTROL Participation]**, en **[!UICONTROL Lookback window]**: **[!UICONTROL Visit]**.

![ParticipationbyVisit.png](assets/ParticipationbyVisit.png)

1. Klik op **[!UICONTROL Apply]**.

Deze stappen zorgen ervoor dat uw rapport het doel metrisch aan de vertoning van de ervaring zal toeschrijven, als de doel metrische gebeurtenis gebeurde *elke keer* (&quot;deelname&quot;) aan hetzelfde bezoek dat een ervaring heeft opgedaan.

### Metrische gegevens voor analyse met *Unieke conversietarieven voor bezoek*

**Bepaal het bezoek met positief metrisch segment**

In het scenario waarin u hebt geselecteerd *De unieke conversiesnelheid voor bezoekers maximaliseren* als optimalisatiecriterium is de correcte definitie van de omrekeningskoers het deel van de bezoeken waarin de metrische waarde positief is. Dit kan worden bereikt door een segment te creëren dat neer aan bezoeken met een positieve waarde van metrisch filtreert, en dan de bezoeken metrisch filtreert.


1. Selecteer de optie **[!UICONTROL Components > Create Segment]** in de werkruimtewerkbalk.
2. Voer een **[!UICONTROL Title]** voor uw segment. In het onderstaande voorbeeld krijgt het segment de naam [!DNL "Visits with an order"].
3. Sleep metrische basis u in uw optimalisatiedoel in het segment gebruikte. In het onderstaande voorbeeld gebruiken we de **orders** metrisch, zodat de omrekeningskoers het deel van de bezoeken waar een order wordt geregistreerd, meet.
4. Bij de hoogste linkerzijde van de container van de segmentdefinitie, uitgezochte **[!UICONTROL Include]** **Bezoek**.
5. Gebruik de **[!UICONTROL is greater than]** operator, en stel de waarde in op 0 (dit segment omvat bijvoorbeeld bezoeken waarbij de metrische volgordes positief zijn)
6. Klik op **[!UICONTROL Save]**.

![Figuur 7.png](assets/Figure7.png)
*Figuur 7: Het filtreren van de segmentdefinitie aan bezoeken met een positieve orde. Afhankelijk van optimalisatiemetrisch van uw activiteit, zult u orden met aangewezen metrisch moeten vervangen*

**Dit toepassen op de bezoeken in metrisch gefilterde activiteit**

Dit segment kan nu worden gebruikt om te filteren op bezoeken met een positief aantal bestellingen en bij een treffer voor de [!DNL Auto-Target]activiteit. De procedure om metrisch te filtreren is gelijkaardig aan vóór, en na het toepassen van het nieuwe segment op reeds-gefiltreerde bezoek metrisch, zou het rapportpaneel als Figuur 8 moeten kijken

![Figuur8.png](assets/Figure8.png)
*Figuur 8: Het rapportpaneel met de correcte metrisch van de uniek-bezoek-omzetting - d.w.z. het aantal bezoeken waar een slag van de activiteit werd geregistreerd, en waar omzettingsmetrisch (orden in dit voorbeeld) niet-nul was.*


## Laatste stap: Een conversiesnelheid maken waarmee de bovenstaande magie wordt vastgelegd

Met de wijzigingen van de [!UICONTROL Visit] en doelmetriek in voorafgaande secties, de definitieve wijziging u aan uw gebrek A4T zou moeten maken voor [!UICONTROL Auto-Target] het melden paneel moet omzettingspercentages tot stand brengen die de correcte verhouding-dat van doel metrisch met de juiste attributie, aan een geschikt gefiltreerd zijn [!UICONTROL Visits] metrisch.

Doe dit door een Berekende Metrisch te creëren gebruikend de volgende stappen:

1. Selecteer **[!UICONTROL Components > Create Metric]** in de [!DNL Workspace] werkbalk.
1. Voer een **[!UICONTROL Title]** voor uw metrische waarde. Bijvoorbeeld &quot;Bezoek-gecorrigeerde Omzetsnelheid voor Activiteit XXX.&quot;
1. Selecteren **[!UICONTROL Format]** = Percentage en **[!UICONTROL Decimal Places]** = 2.
1. Sleep het relevante doel metrisch voor uw activiteit (bijvoorbeeld, [!UICONTROL Activity Conversions]) in de definitie en gebruik het tandwielpictogram op dit doel-metrisch om het attributiemodel aan te passen (Deelname|Bezoek), zoals eerder beschreven.
1. Selecteren **[!UICONTROL Add > Container]** vanaf de rechterbovenhoek van het **[!UICONTROL Definition]** sectie.
1. Selecteer de operator voor delen (&#39;&#39;) tussen de twee containers.
1. Sleep het eerder gemaakte segment met de naam &quot;Actief met specifieke [!UICONTROL Auto-Target] activiteit&quot;in dit leerprogramma-voor dit specifieke [!DNL Auto-Target] activiteit.
1. Sleep de **[!UICONTROL Visits]** metrisch in de segmentcontainer.
1. Klik op **[!UICONTROL Save]**.

>[!TIP]
>
> U kunt deze metrisch ook tot stand brengen gebruikend [snel berekende metrische functionaliteit](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html?lang=en).

De volledige berekende metrische definitie wordt hier getoond.

![Figuur9.png](assets/Figure9.png)
*Figuur 9: De voor bezoeken en attributie gecorrigeerde definitie van de omrekeningskoers van het model. (Merk op dit metrisch is afhankelijk van uw doel metrisch en activiteit. Met andere woorden, deze metrische definitie is niet herbruikbaar over activiteiten.)*

>[!IMPORTANT]
>
>De omzettingssnelheid-metrische waarde uit het deelvenster A4T is niet gekoppeld aan de omzettingsgebeurtenis of de normaliserende metrische waarde in de tabel. Wanneer u de wijzigingen aanbrengt die in deze zelfstudie worden voorgesteld, wordt de conversiesnelheid niet automatisch aangepast aan de wijzigingen. Daarom als u de wijziging aan één (of allebei) de conversiegebeurtenisattributie en normaliserend metrisch maakt, dan moet u als definitieve stap herinneren om de Conversiesnelheid, zoals hierboven getoond ook te wijzigen.

## Overzicht: Eindmonster [!DNL Workspace] deelvenster voor [!UICONTROL Auto-Target] rapporten

Als u alle bovenstaande stappen in één venster combineert, wordt in de onderstaande afbeelding een volledige weergave getoond van het aanbevolen rapport voor [!UICONTROL Auto-Target] A4T-activiteiten. Dit verslag is hetzelfde als het verslag van de [!DNL Target] De modellen van ML om uw doel metrisch te optimaliseren, en het neemt alle nuances en aanbevelingen op die in dit leerprogramma worden besproken. Dit verslag ligt ook het dichtst bij de in de traditionele [!DNL Target]-rapporteringsgestuurd [!UICONTROL Auto-Target] activiteiten.

![Figuur10.png](assets/Figure10.png)
*Figuur 10: De uiteindelijke A4T [!UICONTROL Auto-Target] rapporteren in [!DNL Adobe Analytics] [!DNL Workspace], waarin alle aanpassingen van de metrische definities worden gecombineerd die in de vorige secties van dit document zijn beschreven.*
