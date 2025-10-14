---
title: Hoe te opstelling A4T Rapporten in  [!DNL Analysis Workspace]  voor  [!DNL Auto-Target]  Activiteiten
description: Hoe vorm ik A4T rapporten in  [!DNL Analysis Workspace]  om de verwachte resultaten te krijgen wanneer het runnen van [!UICONTROL Auto-Target] activiteiten?
badgePremium: label="Premium" type="Positive" url="https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=nl-NL#premium newtab=true" tooltip="Kijk wat er in Target Premium is opgenomen."
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
source-wordcount: '2430'
ht-degree: 0%

---

# A4T-rapporten instellen in [!DNL Analysis Workspace] voor [!DNL Auto-Target] -activiteiten

>[!IMPORTANT]
>
>Voor [!UICONTROL Auto-Target] -activiteiten moet u de rapportage controleren in [!DNL Analytics Workspace] en handmatig een A4T-deelvenster maken.

De [!UICONTROL Analytics for Target] (A4T) integratie voor [!DNL Auto-Target] -activiteiten gebruikt de [!DNL Adobe Target] ensemble machine learning (ML)-algoritmen om de beste ervaring voor elke bezoeker te kiezen op basis van hun profiel, gedrag en context, en dit alles terwijl een [!DNL Adobe Analytics] target-metrische waarde wordt gebruikt.

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in [!DNL Adobe Analytics] [!DNL Analysis Workspace] , zijn enkele wijzigingen in het standaard **[!UICONTROL Analytics for Target]** -deelvenster vereist om [!DNL Auto-Target] -activiteiten correct te interpreteren, vanwege verschillen tussen experimentatieactiviteiten (handmatig [!UICONTROL A/B Test] en [!UICONTROL Auto-Allocate]) en personalisatieactiviteiten ([!UICONTROL [!UICONTROL Auto-Target]]).

In deze zelfstudie worden de aanbevolen wijzigingen voor het analyseren van [!UICONTROL Auto-Target] -activiteiten in [!DNL Analysis Workspace] besproken. Deze zijn gebaseerd op de volgende sleutelconcepten:

* De **[!UICONTROL Control vs Targeted]** -dimensie kan worden gebruikt om een onderscheid te maken tussen [!UICONTROL Control] -ervaringen en [!UICONTROL Auto-Target] -ervaringen die door het algoritme ensemble ML worden aangeboden.
* Bezoekingen moeten worden gebruikt als de normaliserende maatstaf bij het bekijken van onderverdelingen van prestaties op ervaringsniveau. Bovendien [&#x200B; Adobe Analytics&#39; standaard tellende methodologie zou bezoeken kunnen omvatten waar de gebruiker niet eigenlijk activiteiteninhoud &#x200B;](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-faq/a4t-faq-viewing-reports.html?lang=nl-NL#metrics){target=_blank} ziet, maar dit standaardgedrag kan worden gewijzigd door een geschikt bereiksegment (details hieronder) te gebruiken.
* Visit-lookback scoped attributie, ook gekend als &quot;bezoek lookback venster&quot;op het voorgeschreven attributiemodel, wordt gebruikt door de modellen van [!DNL Adobe Target] ML tijdens hun opleidingsfasen, en het zelfde (niet gebrek) attributiemodel zou moeten worden gebruikt wanneer het breken van doel metrisch.

## Het deelvenster A4T voor [!UICONTROL Auto-Target] maken in [!DNL Analysis Workspace]

Als u een A4T-rapport voor [!UICONTROL Auto-Target] wilt maken, begint u met het **[!UICONTROL Analytics for Target]** -deelvenster in [!DNL Analysis Workspace] , zoals hieronder wordt weergegeven, of begint u met een vrije-vormtabel. Maak vervolgens de volgende selecties:

1. **[!UICONTROL Control Experience]**: U kunt een ervaring kiezen, maar u zult deze keuze later overschrijven. Voor [!UICONTROL Auto-Target] -activiteiten is de ervaring met besturing in feite een besturingsstrategie, die ofwel a) Willekeurig dient voor alle ervaringen, ofwel b) Eén ervaring dient (deze keuze wordt gemaakt op het moment dat de activiteit wordt gemaakt in [!DNL Adobe Target] ). Zelfs als u voor keuze b) hebt gekozen, geeft uw [!UICONTROL Auto-Target] -activiteit een specifieke ervaring aan als het besturingselement. U moet de in deze zelfstudie beschreven aanpak blijven volgen voor het analyseren van A4T voor [!UICONTROL Auto-Target] -activiteiten.
2. **[!UICONTROL Normalizing Metric]**: Selecteer [!UICONTROL Visits] .
3. **[!UICONTROL Success Metrics]**: Hoewel u metrische gegevens kunt selecteren waarop u wilt rapporteren, moet u rapporten over dezelfde maatstaf weergeven die u hebt gekozen voor optimalisatie tijdens het maken van activiteiten in [!DNL Target] .

   ![[!UICONTROL Analytics for Target] paneelopstelling voor [!UICONTROL Auto-Target] activiteiten. &#x200B;](assets/Figure1.png)

   *Figuur 1: [!UICONTROL Analytics for Target] paneelopstelling voor [!UICONTROL Auto-Target] activiteiten.*

>[!TIP]
>
>Als u het deelvenster [!UICONTROL Analytics for Target] wilt instellen voor [!UICONTROL Auto-Target] -activiteiten, kiest u een beheerervaring, kiest u [!UICONTROL Visits] als de normalisatiemethode en kiest u dezelfde maatstaf voor het doel die u hebt gekozen voor optimalisatie tijdens het maken van [!DNL Target] -activiteit.

## Gebruik de dimensie [!UICONTROL Control vs.Targeted] om het [!DNL Target] ensemble ML model te vergelijken met uw besturingselement

Het standaard A4T-deelvenster is ontworpen voor klassieke (handmatige) [!UICONTROL A/B Test] - of [!UICONTROL Auto-Allocate] -activiteiten waarbij het doel is de prestaties van afzonderlijke ervaringen te vergelijken met die van de besturingservaring. In [!UICONTROL Auto-Target] activiteiten, echter, zou de eerste ordevergelijking tussen de controle *strategie* en de gerichte *strategie* moeten zijn. Met andere woorden, het bepalen van de lift van de algemene prestaties van het [!UICONTROL Auto-Target] ensemble ML model over de controlestrategie.

Voor deze vergelijking gebruikt u de **[!UICONTROL Control vs Targeted (Analytics for Target)]** -dimensie. Sleep en zet neer om de **[!UICONTROL Target Experiences]** dimensie in het standaardA4T rapport te vervangen.

Deze vervanging maakt de standaard [!UICONTROL Lift and Confidence] -berekeningen in het deelvenster A4T ongeldig. Om verwarring te voorkomen, kunt u deze metriek uit het standaardpaneel verwijderen, verlatend het volgende rapport:

![[!UICONTROL Experiences by Activity Conversions] in [!DNL Analysis Workspace]](assets/Figure2.png)

*Figuur 2: Het geadviseerde basislijnrapport voor [!DNL Auto-Target] activiteiten. Dit rapport is gevormd om gericht verkeer (gediend door het ensemble model van ML) tegen uw controleverkeer te vergelijken.*

>[!NOTE]
>
>Momenteel zijn [!UICONTROL Lift and Confidence] getallen niet beschikbaar voor [!UICONTROL Control vs Targeted] afmetingen voor A4T-rapporten voor [!UICONTROL Auto-Target] . Tot de steun wordt toegevoegd, [!UICONTROL Lift and Confidence] kan manueel worden gegevens verwerkt door de [&#x200B; betrouwbaarheidscalculator &#x200B;](https://experienceleague.adobe.com/docs/target/assets/complete_confidence_calculator.xlsx?lang=nl-NL) te downloaden.

## Onderverdelingen op ervaringsniveau toevoegen voor metriek

Om meer insight te krijgen in hoe het ensemble ML model presteert, kunt u ervaring-vlakke onderverdelingen van de **[!UICONTROL Control vs Targeted]** dimensie onderzoeken. Sleep in [!DNL Analysis Workspace] de **[!UICONTROL Target Experiences]** -dimensie naar uw rapport en onderbreek elk van de besturingselementen en de doeldimensies afzonderlijk.

![[!UICONTROL Experiences by Activity Conversions] in [!DNL Analysis Workspace]](assets/Figure3.png)

*Figuur 3: Het onderbreken van de gerichte afmeting door de Ervaringen van het Doel*

Hier wordt een voorbeeld van het resulterende rapport weergegeven.

![[!UICONTROL Experiences by Activity Conversions] in [!DNL Analysis Workspace]](assets/Figure4.png)

*Figuur 4: Een standaard [!UICONTROL Auto-Target] rapport met ervaring-vlakke onderverdelingen. Merk op dat uw doel metrisch verschillend zou kunnen zijn, en uw controlestrategie één enkele ervaring zou kunnen hebben.*

>[!TIP]
>
>Klik in [!DNL Analysis Workspace] op het tandwielpictogram om de percentages in de kolom [!UICONTROL Conversion Rate] te verbergen, zodat de focus op de omzettingssnelheden blijft. De omrekeningskoersen worden vervolgens opgemaakt als decimalen, maar worden dienovereenkomstig als percentages geïnterpreteerd.

## Waarom &quot;[!UICONTROL Visits]&quot; de juiste normalisatiemethode is voor [!UICONTROL Auto-Target] -activiteiten

Wanneer u een [!UICONTROL Auto-Target] -activiteit analyseert, kiest u altijd [!UICONTROL Visits] als de standaardmethode voor normalisatie. Met [!UICONTROL Auto-Target] personalisatie wordt een ervaring geselecteerd voor een bezoeker eenmaal per bezoek (formeel, eenmaal per [!DNL Target] -sessie). Dit betekent dat de ervaring die wordt getoond aan een bezoeker tijdens elk bezoek kan veranderen. Als u [!UICONTROL Unique Visitors] dus gebruikt als de normalisatiemethode, zou het feit dat één gebruiker meerdere ervaringen kan zien (tijdens verschillende bezoeken), leiden tot verwarrende conversietarieven.

Een eenvoudig voorbeeld illustreert dit punt: denk aan een scenario waarin twee bezoekers een campagne starten die slechts twee ervaringen heeft. De eerste bezoeker bezoekt tweemaal. Zij worden toegewezen aan Experience A tijdens het eerste bezoek, maar beleven B tijdens het tweede bezoek (vanwege hun profielstatus die veranderde bij dat tweede bezoek). Na het tweede bezoek converteert de bezoeker een bestelling. De conversie wordt toegeschreven aan de ervaring die het laatst is opgedaan (Experience B). De tweede bezoeker bezoekt ook twee keer, en wordt Ervaring B getoond beide keer, maar nooit omzet.

Laten we de bezoekers vergelijken met de bezoekers:

| Ervaring | Unieke bezoekers | Bezoeken | Conversies | Bezoeker-genormaliseerde omzettingssnelheid | Bezoek-genormaliseerde Omzetsnelheid |
| --- | --- | --- | --- | --- | --- |
| A | 1 | 1 | - | 0% | 0% |
| B | 2 | 3 | 1 | 50% | 33,3% |
| Totalen | 2 | 4 | 1 | 50% | 25% |

*Lijst 1: Voorbeeld die bezoeker-genormaliseerde en bezoek-genormaliseerde rapporten voor een scenario vergelijkt waarin de besluiten aan een bezoek (en niet bezoeker, zoals met regelmatige tests A/B) kleven. Bezoeker-genormaliseerde metriek zijn verwarrend in dit scenario.*

Zoals uit de tabel blijkt, is er een duidelijke incongruentie van bezoekersaantallen. Ondanks het feit dat er in totaal twee unieke bezoekers zijn, is dit geen som van afzonderlijke unieke bezoekers voor elke ervaring. Hoewel de conversiekoers op bezoekersniveau niet noodzakelijkerwijs verkeerd is, hebben conversietarieven op bezoekniveau bij vergelijking van individuele ervaringen waarschijnlijk veel meer zin. Formeel is de eenheid van analyse (&quot;bezoeken&quot;) dezelfde als de eenheid van beslissingswaanzin, wat betekent dat uitsplitsingen van meetgegevens op ervaringsniveau kunnen worden toegevoegd en vergeleken.

## Filter voor feitelijke bezoeken aan de activiteit

De standaardmethode voor het tellen van [!DNL Adobe Analytics] voor bezoeken aan een [!DNL Target] -activiteit kan bezoeken bevatten waarin de gebruiker niet heeft gereageerd op de [!DNL Target] -activiteit. Dit is te wijten aan de manier waarop [!DNL Target] -activiteitstoewijzingen worden voortgezet in de [!DNL Analytics] -bezoekerscontext. Als gevolg hiervan kan het aantal bezoeken aan de [!DNL Target] -activiteit soms worden opgevoerd, wat resulteert in een verlaging van de omrekeningskoersen.

Als u liever melding wilt maken van bezoeken waarop de gebruiker daadwerkelijk heeft gereageerd op de [!UICONTROL Auto-Target] -activiteit (door toegang tot de activiteit, een weergave- of bezoekgebeurtenis of een conversie), kunt u het volgende doen:

1. Maak een specifiek segment dat resultaten van de desbetreffende [!DNL Target] -activiteit bevat en
1. Filter de metrische waarde van [!UICONTROL Visits] met dit segment.

**om het segment tot stand te brengen:**

1. Selecteer de optie **[!UICONTROL Components > Create Segment]** op de werkbalk van [!DNL Analysis Workspace] .
2. Geef een **[!UICONTROL Title]** voor het segment op. In het onderstaande voorbeeld krijgt het segment de naam [!DNL "Hit with specific Auto-Target activity"] .
3. Sleep de **[!UICONTROL Target Activities]** -dimensie naar de sectie segment **[!UICONTROL Definition]** .
4. Gebruik de operator **[!UICONTROL equals]** .
5. Zoek naar uw specifieke [!DNL Target] activiteit.
6. Klik op het tandwielpictogram en selecteer **[!UICONTROL Attribution model > Instance]** zoals in de onderstaande afbeelding wordt getoond.
7. Klik op **[!UICONTROL Save]**.

![&#x200B; Segment in [!DNL Analysis Workspace]](assets/Figure5.png)

*Figuur 5: Gebruik een segment zoals hier getoond om [!UICONTROL Visits] metrisch in uw A4T voor [!UICONTROL Auto-Target] rapport* te filtreren

Nadat het segment is gemaakt, kunt u het gebruiken om de [!UICONTROL Visits] -meting te filteren. De [!UICONTROL Visits] -meting omvat dus alleen bezoeken waar de gebruiker interactie heeft gehad met de [!DNL Target] -activiteit.

**om [!UICONTROL Visits] te filtreren gebruikend dit segment:**

1. Sleep het nieuwe segment van de componentenwerkbalk en houd de muisaanwijzer boven de basis van het metrische label van **[!UICONTROL Visits]** totdat er een blauwe **[!UICONTROL Filter by]** -prompt wordt weergegeven.
2. Laat het segment los. Het filter wordt toegepast op die metrische waarde.

Het uiteindelijke venster ziet er als volgt uit:

![[!UICONTROL Experiences by Activity Conversions] in [!DNL Analysis Workspace]](assets/Figure6.png)

*Figuur 6: Meldend paneel met het &quot;Actief van de Activiteit van het Actief van het Staal met specifiek Auto-Doel&quot;segment dat op [!UICONTROL Visits] wordt toegepast. Dit segment zorgt ervoor dat alleen bezoeken waarin een gebruiker daadwerkelijk met de [!DNL Target] activiteit in kwestie communiceerde, in het rapport worden opgenomen.*

## Zorg ervoor dat de maatstaf van het doel en de kenmerk zijn uitgelijnd op het optimalisatiecriterium

De integratie A4T staat het [!UICONTROL Auto-Target] model van XML toe om *worden getraind* gebruikend de zelfde gegevens van de omzettingsgebeurtenis die [!DNL Adobe Analytics] gebruikt aan *prestatiesrapporten* produceren. Er zijn echter bepaalde veronderstellingen die moeten worden gebruikt bij de interpretatie van deze gegevens bij de training van de ML-modellen, die verschillen van de standaardveronderstellingen die tijdens de rapportagefase in [!DNL Adobe Analytics] zijn gemaakt.

In het bijzonder gebruiken de [!DNL Adobe Target] ML-modellen een &#39;visit-scoped&#39;-attributiemodel. In de ML-modellen wordt er dus van uitgegaan dat een conversie moet plaatsvinden tijdens hetzelfde bezoek als een weergave van inhoud voor de activiteit, zodat de conversie &quot;toegeschreven&quot; kan worden aan de beslissing van het ML-model. [!DNL Target] kan niet tot 30 dagen wachten op een conversie (het standaardtoewijzingsvenster voor rapporten in [!DNL Target] ) voordat deze in de trainingsgegevens voor zijn modellen wordt opgenomen. Dit is vereist voor [!DNL Adobe Analytics] .

Het verschil tussen de attributie die wordt gebruikt door de [!DNL Target] -modellen (tijdens training) en de standaardtoewijzing die wordt gebruikt in het opvragen van gegevens (tijdens het genereren van rapporten) kan dus tot discrepanties leiden. Het kan zelfs lijken dat de modellen van ML slecht presteren, terwijl de kwestie eigenlijk bij attributie ligt.

>[!TIP]
>
>Als de modellen van XML voor metrisch optimaliseren die verschillend van dat van de metriek wordt toegeschreven u in een rapport bekijkt, zouden de modellen niet kunnen uitvoeren zoals verwacht. Om dit te vermijden, zorg ervoor dat de doelmetriek op uw rapport de zelfde metrische definitie en attributie gebruiken die door de [!DNL Target] modellen van ML wordt gebruikt.

De nauwkeurige metrische definitie, en attributie montages hangen van het [&#x200B; optimalisatiecriterium &#x200B;](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=nl-NL#supported){target=_blank} af u tijdens activiteitenverwezenlijking specificeerde.

### Het doel bepaalde omzettingen, of [!DNL Analytics] metriek met *maximaliseert Metrische Waarde per Bezoek*

Wanneer metrisch a [!DNL Target] omzetting is, of een [!DNL Analytics] metriek met **Maximaliseer Metrische Waarde per Bezoek**, staat de doel metrische definitie voor veelvoudige omzettingsgebeurtenissen toe om in het zelfde bezoek voor te komen.

Voer de volgende stappen uit om doelmetriek weer te geven die dezelfde toewijzingsmethode hebben die wordt gebruikt door de [!DNL Target] ML-modellen:

1. Houd de muisaanwijzer boven het tandwielpictogram van het doel:

   ![&#x200B; gearicon.png &#x200B;](assets/gearicon.png)

1. Ga in het resulterende menu naar **[!UICONTROL Data settings]** .
1. Selecteer **[!UICONTROL Use non-default  attribution model]** (als dit nog niet het geval is).

   ![&#x200B; niet-default attributionmodel.png &#x200B;](assets/non-defaultattributionmodel.png)

1. Klik op **[!UICONTROL Edit]**.
1. Selecteer **[!UICONTROL Model]**: **[!UICONTROL Participation]** en **[!UICONTROL Lookback window]**: **[!UICONTROL Visit]** .

   ![&#x200B; ParticipationbyVisit.png &#x200B;](assets/ParticipationbyVisit.png)

1. Klik op **[!UICONTROL Apply]**.

Deze stappen zorgen ervoor dat uw rapport het doel metrisch aan de vertoning van de ervaring kenmerkt, als de doel metrische gebeurtenis *om het even welke tijd* (&quot;participatie&quot;) in het zelfde bezoek dat een ervaring werd getoond gebeurde.

### [!DNL Analytics] metriek met *de Unieke Tarieven van de Omzetting van het Bezoek*

**bepaal het bezoek met positief metrisch segment**

In het scenario waar u *selecteerde maximaliseer het Unieke Tarief van de Omzetting van het Bezoek* als optimalisatiecriterium, is de correcte definitie van het omzettingstarief de fractie van bezoeken waarin de metrische waarde positief is. Dit kan worden bereikt door een segment te creëren dat neer aan bezoeken met een positieve waarde van metrisch filtreert, en dan de bezoeken metrisch filtreert.

1. Selecteer net als voorheen de optie **[!UICONTROL Components > Create Segment]** op de werkbalk van [!DNL Analysis Workspace] .
2. Geef een **[!UICONTROL Title]** voor het segment op.

   In het onderstaande voorbeeld krijgt het segment de naam [!DNL "Visits with an order"] .

3. Sleep metrische basis u in uw optimalisatiedoel in het segment gebruikte.

   In het hieronder getoonde voorbeeld, gebruiken wij de **orden** metrisch, zodat het omzettingspercentage de fractie van bezoeken meet waar een orde wordt geregistreerd.

4. Bij de bovenkant verlaten van de container van de segmentdefinitie, uitgezochte **[!UICONTROL Include]** **Bezoek**.
5. Gebruik de operator **[!UICONTROL is greater than]** en stel de waarde in op 0.

   Als u de waarde instelt op 0, betekent dit dat dit segment bezoeken bevat waarbij de metrische orders positief zijn.

6. Klik op **[!UICONTROL Save]**.

![&#x200B; Figure7.png &#x200B;](assets/Figure7.png)

*Figuur 7: Het filtreren van de segmentdefinitie aan bezoeken met een positieve orde. Afhankelijk van metrische optimalisering van uw activiteit, moet u orden met aangewezen metrisch vervangen*

**pas dit op de bezoeken in metrisch gefiltreerde activiteit toe**

Dit segment kan nu worden gebruikt om te filteren op bezoeken met een positief aantal bestellingen en waar een hit is opgetreden voor de [!DNL Auto-Target] -activiteit. De procedure om metrisch te filtreren is gelijkaardig aan vóór, en na het toepassen van het nieuwe segment op reeds gefilterde bezoek metrisch, zou het rapportpaneel als Figuur 8 moeten kijken

![&#x200B; Figure8.png &#x200B;](assets/Figure8.png)

*Figuur 8: Het rapportpaneel met correcte uniek-bezoek metrische conversie: het aantal bezoeken waar een slag van de activiteit werd geregistreerd, en waar metrische omzetting (orden in dit voorbeeld) niet-nul was.*

## Eindstap: een conversiesnelheid maken waarmee de bovenstaande magie wordt vastgelegd

Met de wijzigingen in de [!UICONTROL Visit] en doelmetriek in de voorafgaande secties, zou de definitieve wijziging u aan uw gebrek A4T voor [!DNL Auto-Target] het melden paneel moeten maken omzettingen tot stand brengen die de correcte verhouding-dat van het gecorrigeerde doel metrisch, aan correct gefiltreerde metrisch &quot;Bezoeken&quot;zijn.

Doe dit door een [!UICONTROL Calculated Metric] te maken met behulp van de volgende stappen:

1. Selecteer de optie **[!UICONTROL Components > Create Metric]** op de werkbalk van [!DNL Analysis Workspace] .
1. Geef een **[!UICONTROL Title]** voor de metrische waarde op. Bijvoorbeeld &quot;Bezoek-gecorrigeerde Omzetsnelheid voor Activiteit XXX.&quot;
1. Selecteer **[!UICONTROL Format]** = Percentage en **[!UICONTROL Decimal Places]** = 2.
1. Sleep de relevante metrische doelstelling voor uw activiteit (bijvoorbeeld, [!UICONTROL Activity Conversions]) in de definitie, en gebruik het tandwielpictogram op dit doel metrisch om het attributiemodel aan (Deelname aan te passen|Bezoek), zoals eerder beschreven.
1. Selecteer **[!UICONTROL Add > Container]** rechtsboven in de sectie **[!UICONTROL Definition]** .
1. Selecteer de operator voor delen (&#39;&#39;) tussen de twee containers.
1. Sleep het eerder gemaakte segment met de naam &quot;Actief met specifieke [!UICONTROL Auto-Target] activiteit&quot; in deze zelfstudie voor deze specifieke [!DNL Auto-Target] -activiteit.
1. Sleep de metrische waarde van **[!UICONTROL Visits]** in de segmentcontainer.
1. Klik op **[!UICONTROL Save]**.

>[!TIP]
>
> U kunt metrisch ook tot stand brengen gebruikend [&#x200B; snel berekende metrische functionaliteit &#x200B;](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html?lang=nl-NL).

De volledige berekende metrische definitie wordt hier getoond.

![&#x200B; Figuur9.png &#x200B;](assets/Figure9.png)

*Figuur 7: De bezoek-gecorrigeerde en attributie-gecorrigeerde metrische definitie van de modelomzettingssnelheid. (Merk op dit metrisch is afhankelijk van uw doel metrisch en activiteit. Met andere woorden, is deze metrische definitie niet herbruikbaar over activiteiten.)*

>[!IMPORTANT]
>
>De maateenheid voor de [!UICONTROL Conversion] -snelheid in het deelvenster A4T is niet gekoppeld aan de conversiegebeurtenis of de normalisatie-metrische waarde in de tabel. Wanneer u de wijzigingen aanbrengt die in deze zelfstudie worden voorgesteld, wordt de snelheid van [!UICONTROL Conversion] niet automatisch aangepast aan de wijzigingen. Daarom als u de wijziging in de attributie van de omzettingsgebeurtenis of normaliserend metrisch (of allebei) maakt, moet u zich als laatste stap herinneren om de [!UICONTROL Conversion] tarief, zoals hierboven getoond ook te wijzigen.

## Samenvatting: deelvenster Laatste voorbeeld [!DNL Analysis Workspace] voor [!UICONTROL Auto-Target] -rapporten

Als u alle bovenstaande stappen in één venster verenigt, wordt in de onderstaande afbeelding een volledige weergave getoond van het aanbevolen rapport voor [!UICONTROL Auto-Target] A4T-activiteiten. Dit rapport is het zelfde als dat gebruikt door de [!DNL Target] modellen van ML om uw doel metrisch te optimaliseren. Het verslag bevat alle nuances en aanbevelingen die in deze zelfstudie worden besproken. Dit rapport ligt ook het dichtst bij de telmethoden die worden gebruikt in traditionele [!DNL Target] -reporting gedreven [!UICONTROL Auto-Target] -activiteiten.

Klik om de afbeelding uit te vouwen.

![&#x200B; Definitief A4T rapport in [!DNL Analysis Workspace]](assets/Figure10.png " A4T rapport in Analysis Workspace "){width="600" zoomable="yes"}

*Figuur 10: Het definitieve A4T [!UICONTROL Auto-Target] rapport in [!DNL Adobe Analytics] [!DNL Workspace], dat alle aanpassingen aan metrische definities combineert die in de vorige secties van dit leerprogramma worden beschreven.*
