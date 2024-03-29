---
title: A4T-rapporten instellen in [!DNL Analysis Workspace] for [!DNL Auto-Target] Activiteiten
description: Hoe kan ik A4T-rapporten configureren in [!DNL Analysis Workspace] om de verwachte resultaten op te halen wanneer de toepassing wordt uitgevoerd [!UICONTROL Auto-Target] activiteiten?
badgePremium: label="Premium" type="Positive" url="https://experienceleague.adobe.com/docs/target/using/introduction/intro.html#premium newtab=true" tooltip="Zie wat er in Target Premium is opgenomen."
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
thumbnail: null
kt: null
exl-id: 58006a25-851e-43c8-b103-f143f72ee58d
source-git-commit: 78e5b5f7fa8f4c1a08c06c6d2b0e1a5242cd464c
workflow-type: tm+mt
source-wordcount: '2480'
ht-degree: 0%

---

# A4T-rapporten instellen in [!DNL Analysis Workspace] for [!DNL Auto-Target] activiteiten

>[!IMPORTANT]
>
>Voor [!UICONTROL Auto-Target] activiteiten, moet u de rapportage controleren [!DNL Analytics Workspace] en maakt u handmatig een A4T-deelvenster.

De [!UICONTROL Analytics for Target] (A4T) integratie voor [!DNL Auto-Target] de activiteiten gebruiken [!DNL Adobe Target] tags toepassen voor het leren van machines (ML) om de beste ervaring voor elke bezoeker te kiezen op basis van hun profiel, gedrag en context, en dit alles tijdens het gebruik van een [!DNL Adobe Analytics] doel-metrisch.

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in [!DNL Adobe Analytics] [!DNL Analysis Workspace], enkele wijzigingen in de standaardwaarde **[!UICONTROL Analytics for Target]** het deelvenster moet correct worden geïnterpreteerd [!DNL Auto-Target] activiteiten, wegens verschillen tussen experimentele activiteiten (handboek [!UICONTROL A/B Test] en [!UICONTROL Auto-Allocate]) en personaliseringsactiviteiten ([!UICONTROL [!UICONTROL Auto-Target]]).

Deze zelfstudie doorloopt de aanbevolen wijzigingen voor het analyseren [!UICONTROL Auto-Target] activiteiten in [!DNL Analysis Workspace], die gebaseerd zijn op de volgende sleutelbegrippen:

* De **[!UICONTROL Control vs Targeted]** dimensie kan worden gebruikt om onderscheid te maken tussen [!UICONTROL Control] ervaringen in vergelijking met die van de [!UICONTROL Auto-Target] ensemble ML algorithm.
* Bezoekingen moeten worden gebruikt als de normaliserende maatstaf bij het bekijken van onderverdelingen van prestaties op ervaringsniveau. Daarnaast [De standaardmethode voor tellen van Adobe Analytics kan bezoeken omvatten waarbij de gebruiker geen activiteiteninhoud ziet](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-faq/a4t-faq-viewing-reports.html#metrics){target=_blank}, maar dit standaardgedrag kan worden gewijzigd door een segment met het juiste bereik te gebruiken (details verderop).
* Visit-lookback scoped attributie, ook gekend als &quot;bezoek lookback window&quot;op het voorgeschreven attribuutmodel, wordt gebruikt door [!DNL Adobe Target] De modellen van ML tijdens hun opleidingsfasen, en het zelfde (niet gebrek) attributiemodel zouden moeten worden gebruikt wanneer het breken van doel metrisch.

## A4T maken voor [!UICONTROL Auto-Target] deelvenster in [!DNL Analysis Workspace]

Een A4T maken voor [!UICONTROL Auto-Target] rapport, of begin met **[!UICONTROL Analytics for Target]** deelvenster in [!DNL Analysis Workspace], zoals hieronder wordt getoond, of beginnen met een vrije-vormlijst. Maak vervolgens de volgende selecties:

1. **[!UICONTROL Control Experience]**: U kunt een ervaring kiezen, maar u zult deze keuze later overschrijven. Let op: voor [!UICONTROL Auto-Target] De ervaring met controle is in feite een controlestrategie, die ofwel a) willekeurig dienst doet bij alle ervaringen, ofwel b) één ervaring dient (deze keuze wordt gemaakt op het moment dat de activiteit wordt gecreëerd in [!DNL Adobe Target]). Zelfs als u voor keuze b) hebt gekozen, [!UICONTROL Auto-Target] een specifieke ervaring als controle aangewezen. U moet de in deze zelfstudie beschreven aanpak voor het analyseren van A4T voor [!UICONTROL Auto-Target] activiteiten.
2. **[!UICONTROL Normalizing Metric]**: Select [!UICONTROL Visits].
3. **[!UICONTROL Success Metrics]**: Hoewel u om het even welke metriek kunt selecteren waarop te melden, zou u rapporten over het algemeen over zelfde metrisch moeten bekijken die voor optimalisering tijdens activiteitenverwezenlijking binnen werd gekozen [!DNL Target].

   ![[!UICONTROL Analytics for Target] deelvenster instellen voor [!UICONTROL Auto-Target] activiteiten.](assets/Figure1.png)

   *Afbeelding 1: [!UICONTROL Analytics for Target] deelvenster instellen voor [!UICONTROL Auto-Target] activiteiten.*

>[!TIP]
>
>Als u uw [!UICONTROL Analytics for Target] deelvenster voor [!UICONTROL Auto-Target] activiteiten, kiest u een ervaring in het beheer en kiest u [!UICONTROL Visits] als normaliserend metrisch, en kies het zelfde doel metrisch dat voor optimalisering tijdens werd gekozen [!DNL Target] activiteiten creëren.

## Gebruik de [!UICONTROL Control vs.Targeted] dimensie die moet worden vergeleken [!DNL Target] ML-model samenvoegen tot uw besturingselement

Het standaard A4T-deelvenster is ontworpen voor klassiek (handmatig) [!UICONTROL A/B Test] of [!UICONTROL Auto-Allocate] activiteiten waarbij het doel is de prestaties van individuele ervaringen te vergelijken met die van de controleervaring. In [!UICONTROL Auto-Target] de activiteiten, maar de eerste orde van vergelijking moet betrekking hebben op de *strategie* en de beoogde *strategie*. Met andere woorden, het bepalen van de totale prestatie van de [!UICONTROL Auto-Target] Sluit het model van ML over de controlestrategie.

Voor deze vergelijking gebruikt u de opdracht **[!UICONTROL Control vs Targeted (Analytics for Target)]** dimensie. Sleep en zet neer om de **[!UICONTROL Target Experiences]** dimensie in het standaardA4T rapport.

Deze vervanging maakt de standaardinstelling ongeldig [!UICONTROL Lift and Confidence] berekeningen in het A4T-deelvenster. Om verwarring te voorkomen, kunt u deze metriek uit het standaardpaneel verwijderen, verlatend het volgende rapport:

![[!UICONTROL Experiences by Activity Conversions] deelvenster in [!DNL Analysis Workspace]](assets/Figure2.png)

*Figuur 2: Het geadviseerde basislijnrapport voor [!DNL Auto-Target] activiteiten. Dit rapport is gevormd om gericht verkeer (gediend door het ensemble model van ML) tegen uw controleverkeer te vergelijken.*

>[!NOTE]
>
>Momenteel [!UICONTROL Lift and Confidence] getallen zijn niet beschikbaar voor [!UICONTROL Control vs Targeted] afmetingen voor A4T-rapporten voor [!UICONTROL Auto-Target]. Totdat ondersteuning is toegevoegd, [!UICONTROL Lift and Confidence] kan handmatig worden berekend door de [betrouwbaarheidscalculator](https://experienceleague.adobe.com/docs/target/assets/complete_confidence_calculator.xlsx).

## Onderverdelingen op ervaringsniveau toevoegen voor metriek

Om meer inzicht te krijgen in hoe het ensemble ML model presteert, kunt u ervaring-vlakke onderverdelingen van onderzoeken **[!UICONTROL Control vs Targeted]** dimensie. In [!DNL Analysis Workspace], sleept u de **[!UICONTROL Target Experiences]** dimensie op uw rapport, dan onderverdeeld elk van de controle en gerichte dimensies afzonderlijk.

![[!UICONTROL Experiences by Activity Conversions] deelvenster in [!DNL Analysis Workspace]](assets/Figure3.png)

*Afbeelding 3: De doeldimensie indelen door de ervaring van het doel*

Hier wordt een voorbeeld van het resulterende rapport weergegeven.

![[!UICONTROL Experiences by Activity Conversions] deelvenster in [!DNL Analysis Workspace]](assets/Figure4.png)

*Figuur 4: Een norm [!UICONTROL Auto-Target] rapporteren met uitsplitsingen op ervaringsniveau. Merk op dat uw doel metrisch zou kunnen verschillend zijn, en uw controlestrategie één enkele ervaring zou kunnen hebben.*

>[!TIP]
>
>In [!DNL Analysis Workspace]klikt u op het tandwielpictogram om de percentages in het dialoogvenster [!UICONTROL Conversion Rate] om de focus op de ervaringsomrekeningskoersen te houden. De omrekeningskoersen worden vervolgens opgemaakt als decimalen, maar worden dienovereenkomstig als percentages geïnterpreteerd.

## Waarom &quot;[!UICONTROL Visits]&quot; is de juiste normalisatie-metrische waarde voor [!UICONTROL Auto-Target] activiteiten

Wanneer u een [!UICONTROL Auto-Target] activiteit, altijd kiezen [!UICONTROL Visits] als standaard normaliserend metrisch. [!UICONTROL Auto-Target] personalisatie kiest een ervaring voor een bezoeker eenmaal per bezoek ( formeel , eenmaal per bezoek ) [!DNL Target] sessie), wat betekent dat de ervaring die een bezoeker wordt getoond, bij elk bezoek kan veranderen. Als u [!UICONTROL Unique Visitors] als het normaliseren metrisch, zou het feit dat één enkele gebruiker veelvoudige ervaringen (over verschillende bezoeken) zou kunnen uiteindelijk tot verwarrende omzettingspercentages leiden.

Een eenvoudig voorbeeld illustreert dit punt: denk aan een scenario waarin twee bezoekers een campagne starten die slechts twee ervaringen heeft. De eerste bezoeker bezoekt tweemaal. Zij worden toegewezen aan Experience A tijdens het eerste bezoek, maar beleven B tijdens het tweede bezoek (vanwege hun profielstatus die veranderde bij dat tweede bezoek). Na het tweede bezoek converteert de bezoeker een bestelling. De conversie wordt toegeschreven aan de ervaring die het laatst is opgedaan (Experience B). De tweede bezoeker bezoekt ook twee keer, en wordt Ervaring B getoond beide keer, maar nooit omzet.

Laten we de bezoekers vergelijken met de bezoekers:

| Ervaring | Unieke bezoekers | Bezoeken | Conversies | Bezoeker-genormaliseerde omzettingssnelheid | Bezoek-genormaliseerde Omzetsnelheid |
| --- | --- | --- | --- | --- | --- |
| A | 1 | 1 | - | 0% | 0% |
| B | 2 | 3 | 1 | 50% | 33.3% |
| Totalen | 2 | 4 | 1 | 50% | 25% |

*Tabel 1: Voorbeeld waarin bezoekers genormaliseerde en op bezoek genormaliseerde rapporten werden vergeleken voor een scenario waarin beslissingen aan een bezoek kleven (en niet aan bezoekers, zoals bij regelmatige A/B-tests). De bezoeker-genormaliseerde metriek zijn verwarrend in dit scenario.*

Zoals uit de tabel blijkt, is er een duidelijke incongruentie van bezoekersaantallen. Ondanks het feit dat er in totaal twee unieke bezoekers zijn, is dit geen som van afzonderlijke unieke bezoekers voor elke ervaring. Hoewel de conversiekoers op bezoekersniveau niet noodzakelijkerwijs verkeerd is, hebben conversietarieven op bezoekniveau bij vergelijking van individuele ervaringen waarschijnlijk veel meer zin. Formeel is de eenheid van analyse (&quot;bezoeken&quot;) dezelfde als de eenheid van beslissingswaanzin, wat betekent dat uitsplitsingen van meetgegevens op ervaringsniveau kunnen worden toegevoegd en vergeleken.

## Filter voor feitelijke bezoeken aan de activiteit

De [!DNL Adobe Analytics] standaardtelmethode voor bezoeken aan een [!DNL Target] activiteit zou bezoeken kunnen omvatten waarin de gebruiker niet met [!DNL Target] activiteit. Dit komt door de manier waarop [!DNL Target] activiteitstoewijzingen blijven bestaan in de [!DNL Analytics] context bezoeker. Het aantal bezoeken aan de [!DNL Target] de activiteit kan soms worden opgevoerd , wat leidt tot een verlaging van de omrekeningskoersen .

Als u liever melding wilt maken van bezoeken waarbij de gebruiker daadwerkelijk met de [!UICONTROL Auto-Target] activiteit (via toegang tot de activiteit, een weergave- of bezoekgebeurtenis of een conversie), kunt u:

1. Maak een specifiek segment dat resultaten van het [!DNL Target] de betrokken activiteit, en vervolgens
1. Filteren op [!UICONTROL Visits] metrisch gebruikend dit segment.

**Het segment maken:**

1. Selecteer de **[!UICONTROL Components > Create Segment]** in de [!DNL Analysis Workspace] werkbalk.
2. Geef een **[!UICONTROL Title]** voor uw segment. In het onderstaande voorbeeld krijgt het segment de naam [!DNL "Hit with specific Auto-Target activity"].
3. Sleep de **[!UICONTROL Target Activities]** dimensie van het segment **[!UICONTROL Definition]** sectie.
4. Gebruik de **[!UICONTROL equals]** operator.
5. Zoeken naar uw specifieke [!DNL Target] activiteit.
6. Klik op het tandwielpictogram en selecteer **[!UICONTROL Attribution model > Instance]** zoals weergegeven in onderstaande afbeelding.
7. Klik op **[!UICONTROL Save]**.

![Segment in [!DNL Analysis Workspace]](assets/Figure5.png)

*Figuur 5: Gebruik een segment zoals hier getoond om te filtreren [!UICONTROL Visits] Metrisch in uw A4T voor [!UICONTROL Auto-Target] verslag*

Nadat het segment is gemaakt, filtert u het [!UICONTROL Visits] metrisch, dus [!UICONTROL Visits] metrisch omvat alleen bezoeken waar de gebruiker interactie had met de [!DNL Target] activiteit.

**Naar filter [!UICONTROL Visits] dit segment gebruiken:**

1. Sleep het nieuwe segment van de componententoolbar, en houd over de basis van **[!UICONTROL Visits]** metrisch label tot een blauw **[!UICONTROL Filter by]** wordt weergegeven.
2. Laat het segment los. Het filter wordt toegepast op die metrische waarde.

Het uiteindelijke venster ziet er als volgt uit:

![[!UICONTROL Experiences by Activity Conversions] deelvenster in [!DNL Analysis Workspace]](assets/Figure6.png)

*Afbeelding 6: Rapportagevenster met het segment &quot;Activiteit aanpassen met specifieke automatische doelactiviteit&quot; toegepast op het [!UICONTROL Visits] metrisch. Dit segment zorgt ervoor dat alleen bezoeken waarbij een gebruiker daadwerkelijk met het [!DNL Target] de betrokken activiteit is in het verslag opgenomen .*

## Zorg ervoor dat de maatstaf van het doel en de kenmerk zijn uitgelijnd op het optimalisatiecriterium

De integratie A4T maakt de [!UICONTROL Auto-Target] Te gebruiken ML-model *opgeleid* dezelfde conversiegebeurtenisgegevens gebruiken die [!DNL Adobe Analytics] gebruiken voor *prestatierapporten genereren*. Er zijn echter bepaalde veronderstellingen die moeten worden gebruikt bij de interpretatie van deze gegevens bij de opleiding van de modellen van het ML, die verschillen van de standaardveronderstellingen die tijdens de rapportagefase in [!DNL Adobe Analytics].

In het bijzonder de [!DNL Adobe Target] In ML-modellen wordt een &quot;visit-scoped&quot;-attributiemodel gebruikt. In de ML-modellen wordt er dus van uitgegaan dat een conversie moet plaatsvinden tijdens hetzelfde bezoek als een weergave van inhoud voor de activiteit, zodat de conversie &quot;toegeschreven&quot; kan worden aan de beslissing van het ML-model. Dit is vereist voor [!DNL Target] de tijdige opleiding van haar modellen te waarborgen; [!DNL Target] kan maximaal 30 dagen wachten op een conversie (het standaardtoewijzingsvenster voor rapporten in [!DNL Adobe Analytics]), alvorens deze op te nemen in de opleidingsgegevens voor haar modellen.

Het verschil tussen de door de [!DNL Target] modellen (tijdens training) versus de standaardtoewijzing die wordt gebruikt in het opvragen van gegevens (tijdens het genereren van rapporten) kunnen tot discrepanties leiden. Het kan zelfs lijken dat de modellen van ML slecht presteren, terwijl de kwestie eigenlijk bij attributie ligt.

>[!TIP]
>
>Als de modellen van XML voor metrisch optimaliseren die verschillend van dat van de metriek wordt toegeschreven u in een rapport bekijkt, zouden de modellen niet kunnen uitvoeren zoals verwacht. Om dit te vermijden, zorg ervoor dat de doelmetriek op uw rapport de zelfde metrische definitie en de attributie gebruiken die door wordt gebruikt [!DNL Target] ML-modellen.

De exacte metrische definitie en attribuutinstellingen zijn afhankelijk van de [optimalisatiecriterium](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank} u hebt opgegeven tijdens het maken van activiteiten.

### door het doel gedefinieerde omzettingen, of [!DNL Analytics] cijfers met *Metrische waarde maximaliseren per bezoek*

Wanneer de metrische waarde een [!DNL Target] conversie, of een [!DNL Analytics] cijfers met **Metrische waarde maximaliseren per bezoek**, staat de doel metrische definitie voor veelvoudige omzettingsgebeurtenissen toe om in het zelfde bezoek voor te komen.

Doelmetriek bekijken die de zelfde attribuutmethodologie hebben die door wordt gebruikt [!DNL Target] In ML-modellen voert u de volgende stappen uit:

1. Houd de muisaanwijzer boven het tandwielpictogram van het doel:

   ![gearicon.png](assets/gearicon.png)

1. Blader vanuit het resulterende menu naar **[!UICONTROL Data settings]**.
1. Selecteren **[!UICONTROL Use non-default  attribution model]** (indien nog niet geselecteerd).

   ![non-default attributionmodel.png](assets/non-defaultattributionmodel.png)

1. Klik op **[!UICONTROL Edit]**.
1. Selecteren **[!UICONTROL Model]**: **[!UICONTROL Participation]**, en **[!UICONTROL Lookback window]**: **[!UICONTROL Visit]**.

   ![ParticipationbyVisit.png](assets/ParticipationbyVisit.png)

1. Klik op **[!UICONTROL Apply]**.

Deze stappen zorgen ervoor dat uw rapport het doel metrisch aan de vertoning van de ervaring kenmerkt, als de doel metrische gebeurtenis gebeurde *elke keer* (&quot;deelname&quot;) aan hetzelfde bezoek dat een ervaring heeft opgedaan.

### [!DNL Analytics] cijfers met *Unieke conversietarieven voor bezoek*

**Bepaal het bezoek met positief metrisch segment**

In het scenario waarin u hebt geselecteerd *De unieke conversiesnelheid voor bezoekers maximaliseren* als optimalisatiecriterium is de correcte definitie van de omrekeningskoers het deel van de bezoeken waarin de metrische waarde positief is . Dit kan worden bereikt door een segment te creëren dat neer aan bezoeken met een positieve waarde van metrisch filtreert, en dan de bezoeken metrisch filtreert.

1. Selecteer de optie **[!UICONTROL Components > Create Segment]** in de [!DNL Analysis Workspace] werkbalk.
2. Geef een **[!UICONTROL Title]** voor uw segment.

   In het onderstaande voorbeeld krijgt het segment de naam [!DNL "Visits with an order"].

3. Sleep metrische basis u in uw optimalisatiedoel in het segment gebruikte.

   In het onderstaande voorbeeld gebruiken we de **orders** metrisch, zodat de omrekeningskoers het deel van de bezoeken waar een order wordt geregistreerd, meet.

4. Bij de hoogste linkerzijde van de container van de segmentdefinitie, uitgezochte **[!UICONTROL Include]** **Bezoek**.
5. Gebruik de **[!UICONTROL is greater than]** en stelt de waarde in op 0.

   Als u de waarde instelt op 0, betekent dit dat dit segment bezoeken bevat waarbij de metrische orders positief zijn.

6. Klik op **[!UICONTROL Save]**.

![Figuur 7.png](assets/Figure7.png)

*Figuur 7: Het filtreren van de segmentdefinitie aan bezoeken met een positieve orde. Afhankelijk van optimalisatiemetrisch van uw activiteit, moet u orden met aangewezen metrisch vervangen*

**Dit toepassen op de bezoeken in metrisch gefilterde activiteit**

Dit segment kan nu worden gebruikt om te filteren op bezoeken met een positief aantal bestellingen en bij een treffer voor de [!DNL Auto-Target] activiteit. De procedure om metrisch te filtreren is gelijkaardig aan vóór, en na het toepassen van het nieuwe segment op reeds gefilterde bezoek metrisch, zou het rapportpaneel als Figuur 8 moeten kijken

![Figuur8.png](assets/Figure8.png)

*Figuur 8: Het rapportpaneel met de correcte metrische uniek-bezoek conversie: het aantal bezoeken waar een slag van de activiteit werd geregistreerd, en waar omzettingsmetrisch (orden in dit voorbeeld) niet-nul was.*

## Eindstap: een conversiesnelheid maken waarmee de bovenstaande magie wordt vastgelegd

Met de wijzigingen van de [!UICONTROL Visit] en doelmetriek in de voorafgaande secties, de definitieve wijziging u aan uw gebrek A4T zou moeten maken voor [!DNL Auto-Target] het melden paneel moet omzettingspercentages tot stand brengen die de correcte verhouding-dat van het gecorrigeerde doel metrisch, aan correct gefiltreerde metrische &quot;Bebezoeken&quot;zijn.

Dit doet u door een [!UICONTROL Calculated Metric] met behulp van de volgende stappen:

1. Selecteer de **[!UICONTROL Components > Create Metric]** in de [!DNL Analysis Workspace] werkbalk.
1. Geef een **[!UICONTROL Title]** voor uw metrische waarde. Bijvoorbeeld &quot;Bezoek-gecorrigeerde Omzetsnelheid voor Activiteit XXX.&quot;
1. Selecteren **[!UICONTROL Format]** = Percentage en **[!UICONTROL Decimal Places]** = 2.
1. Sleep het relevante doel metrisch voor uw activiteit (bijvoorbeeld, [!UICONTROL Activity Conversions]) in de definitie en gebruik het tandwielpictogram op dit doel-metrisch om het attributiemodel aan te passen (Deelname|Bezoek), zoals eerder beschreven.
1. Selecteren **[!UICONTROL Add > Container]** vanaf de rechterbovenhoek van het **[!UICONTROL Definition]** sectie.
1. Selecteer de operator voor delen (&#39;&#39;) tussen de twee containers.
1. Sleep het eerder gemaakte segment met de naam &quot;Actief met specifieke [!UICONTROL Auto-Target] activiteit&quot; in deze zelfstudie voor deze specifieke [!DNL Auto-Target] activiteit.
1. Sleep de **[!UICONTROL Visits]** metrisch in de segmentcontainer.
1. Klik op **[!UICONTROL Save]**.

>[!TIP]
>
> U kunt deze metrisch ook tot stand brengen gebruikend [snel berekende metrische functionaliteit](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html).

De volledige berekende metrische definitie wordt hier getoond.

![Figuur9.png](assets/Figure9.png)

*Afbeelding 7: De voor het bezoek gecorrigeerde en voor kenmerk gecorrigeerde definitie van de omrekeningskoers van het model. (Merk op dit metrisch is afhankelijk van uw doel metrisch en activiteit. Met andere woorden, deze metrische definitie is niet herbruikbaar over activiteiten.)*

>[!IMPORTANT]
>
>De [!UICONTROL Conversion] De metrische snelheid van het deelvenster A4T is niet gekoppeld aan de conversiegebeurtenis of de normaliserende metrische waarde in de tabel. Wanneer u de wijzigingen aanbrengt die in deze zelfstudie worden voorgesteld, worden de [!UICONTROL Conversion] wordt niet automatisch aangepast aan de wijzigingen. Daarom als u de wijziging in de attributie van de omzettingsgebeurtenis of normaliserend metrisch (of allebei) maakt, moet u als definitieve stap herinneren ook om te wijzigen [!UICONTROL Conversion] tarief, zoals hierboven getoond.

## Samenvatting: eindmonster [!DNL Analysis Workspace] deelvenster voor [!UICONTROL Auto-Target] rapporten

In de onderstaande afbeelding ziet u een volledige weergave van het aanbevolen rapport voor het combineren van alle bovenstaande stappen in één venster [!UICONTROL Auto-Target] A4T-activiteiten. Dit verslag is hetzelfde als het verslag van de [!DNL Target] ML modellen om uw doel metrisch te optimaliseren. Het verslag bevat alle nuances en aanbevelingen die in deze zelfstudie worden besproken. Dit verslag ligt ook het dichtst bij de in de traditionele [!DNL Target]-rapporteringsgestuurd [!UICONTROL Auto-Target] activiteiten.

Klik om de afbeelding uit te vouwen.

![Definitief A4T-rapport in [!DNL Analysis Workspace]](assets/Figure10.png "A4T-rapport in Analysis Workspace"){width="600" zoomable="yes"}

*Figuur 10: De uiteindelijke A4T [!UICONTROL Auto-Target] rapporteren in [!DNL Adobe Analytics] [!DNL Workspace], waarin alle aanpassingen aan metrische definities worden gecombineerd die in de vorige secties van deze zelfstudie worden beschreven.*
