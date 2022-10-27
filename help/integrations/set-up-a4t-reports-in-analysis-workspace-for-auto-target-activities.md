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
source-git-commit: e1acb84970b967625e0b6c7495067ed6456a6aa3
workflow-type: tm+mt
source-wordcount: '2575'
ht-degree: 0%

---

# A4T-rapporten instellen in Analysis Workspace voor [!DNL Auto-Target] activiteiten

De integratie Analytics for Target (A4T) voor [!DNL Auto-Target] De activiteiten gebruiken de algoritmen van het de machine van Adobe Target van het ensemble leren (ML) om de beste ervaring voor elke bezoeker te kiezen die op hun profiel, gedrag, en context wordt gebaseerd, allen terwijl het gebruiken van het doel van Adobe Analytics metrisch.

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in Adobe Analytics Analysis Workspace, zijn enkele wijzigingen in de standaard **[!UICONTROL Analytics for Target]** het deelvenster moet correct worden geïnterpreteerd [!DNL Auto-Target] activiteiten, als gevolg van verschillen tussen experimentele activiteiten (handleiding A/B en automatische toewijzing) en personalisatieactiviteiten ([!DNL Auto-Target]).

Deze zelfstudie doorloopt de aanbevolen wijzigingen voor het analyseren [!DNL Auto-Target] activiteiten in Workspace, die zijn gebaseerd op de volgende sleutelconcepten:

* De **[!UICONTROL Control vs Targeted]** De dimensie kan worden gebruikt om tussen de ervaringen van de Controle versus die te onderscheiden die door [!DNL Auto-Target] ensemble ML algorithm.
* Bezoekingen moeten worden gebruikt als de normaliserende maatstaf bij het bekijken van baanbrekingen van prestaties op ervaringsniveau. Daarnaast [De standaardtelmethode van Adobe Analytics kan bezoeken omvatten waarbij de gebruiker geen activiteiteninhoud ziet](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-faq/a4t-faq-viewing-reports.html?lang=en#metrics), maar dit standaardgedrag kan worden gewijzigd door een segment met het juiste bereik te gebruiken (details verderop).
* Visit-lookback scoped attributie-ook gekend als &quot;bezoek lookback venster&quot;op het voorgeschreven attributiemodel-wordt gebruikt door de modellen van XML van Adobe Target tijdens hun opleidingsfasen, en het zelfde (niet gebrek) attributiemodel zou moeten worden gebruikt wanneer het breken van doel metrisch.

## A4T maken voor [!DNL Auto-Target] deelvenster in werkruimte

Een A4T maken voor [!DNL Auto-Target] rapport, of begin met **[!UICONTROL Analytics for Target]** in Workspace, zoals hieronder wordt weergegeven, of begint met een vrije-vormtabel. Maak vervolgens de volgende selecties:

1. **[!UICONTROL Control Experience]**: U kunt elke ervaring kiezen; u zult deze keuze later echter overschrijven. Let op: voor [!DNL Auto-Target] De ervaring met controle is in feite een controlestrategie, die ofwel a) willekeurig dienst doet tussen alle ervaringen, ofwel b) één ervaring dient (deze keuze wordt gemaakt op het moment dat activiteiten worden gecreëerd in Adobe Target). Zelfs als u voor keuze (b) koos—uw [!DNL Auto-Target] activiteit aangewezen een specifieke ervaring als controle-u zou nog de benadering moeten volgen die in dit leerprogramma voor het analyseren van A4T voor wordt geschetst [!DNL Auto-Target] activiteiten.
2. **[!UICONTROL Normalizing Metric]**: Selecteer Bezoeken.
3. **[!UICONTROL Success Metrics]**: Hoewel u om het even welke metrisch(e) kunt selecteren waarop om te melden, zou u rapporten over het algemeen over zelfde metrisch moeten bekijken die voor optimalisering tijdens activiteitenverwezenlijking in Adobe Target werd gekozen.

![Figuur1.png](assets/Figure1.png)
*Afbeelding 1: Analyse voor instellen deelvenster Doel voor [!DNL Auto-Target] activiteiten.*

>[!NOTE]
>
>Om uw Analytics voor het paneel van het Doel voor activiteiten te plaatsen Auto-Target, verkies om het even welke controleervaring, kies Bezoeken als normaliserend metrisch, en kies het zelfde doel metrisch dat voor optimalisering tijdens de verwezenlijking van de activiteit van het Doel werd gekozen.

## Gebruik de besturingselementen versus de doeldimensie om het samenstellende XML-model van Adobe Target te vergelijken met uw besturingselement

Het standaard A4T-deelvenster is ontworpen voor klassieke (handmatige) A/B-tests of Auto-Allocate-activiteiten, waarbij het doel is de prestaties van individuele ervaringen te vergelijken met de ervaring in het beheer. In [!DNL Auto-Target] de activiteiten, maar de eerste ordervergelijking moet tussen de *strategie* en de *strategie* (met andere woorden, het bepalen van de totale prestatie van de [!DNL Auto-Target] het ML-model samenvoegen boven de controlestrategie).

Voor deze vergelijking gebruikt u de opdracht **[!UICONTROL Control vs Targeted (Analytics for Target)]** dimensie. Sleep en zet neer om de **[!UICONTROL Target Experiences]** dimensie in het standaardA4T rapport.

Deze vervanging maakt de standaardberekeningen voor het optillen en vertrouwen in het deelvenster A4T ongeldig. Om verwarring te voorkomen, kunt u deze metriek uit het standaardpaneel verwijderen, verlatend het volgende rapport:

![Figuur2.png](assets/Figure2.png)
*Afbeelding 2: Het aanbevolen basislijnrapport voor [!DNL Auto-Target] activiteiten. Dit rapport is gevormd om gericht verkeer (gediend door het ensemble model van ML) tegen uw verkeer van de Controle te vergelijken.*

>[!NOTE]
>
>De aantallen van de Optillen en van het Vertrouwen zijn momenteel niet beschikbaar voor Controle vs gerichte dimensies voor A4T rapporten voor auto-Doel. Totdat ondersteuning is toegevoegd, kunt u optillen en vertrouwen handmatig berekenen door de [betrouwbaarheidscalculator](https://experienceleague.adobe.com/docs/target/assets/complete_confidence_calculator.xlsx?lang=en).

## Uitsplitsingen op ervaringsniveau toevoegen

Als u meer inzicht wilt krijgen in de manier waarop het ensemble ML-model presteert, kunt u uitsplitsingen op ervaringsniveau van de **[!UICONTROL Control vs Targeted]** dimensie. Sleep in Workspace de **[!UICONTROL Target Experiences]** dimensie op uw rapport, dan onderverdeeld elk van de Controle en de gerichte dimensies afzonderlijk.

![Figuur3.png](assets/Figure3.png)
*Figuur 3: Verdeling van de gerichte dimensie door de Ervaringen van het Doel*

Hier wordt een voorbeeld van het resulterende rapport weergegeven.

![Figuur4.png](assets/Figure4.png)
*Figuur 4: Een norm [!DNL Auto-Target] rapporteren met uitsplitsingen op ervaringsniveau. Merk op uw doel metrisch kan verschillend zijn, en uw strategie van de Controle kan één enkele ervaring hebben.*

>[!TIP]
>
>Klik in Workspace op het tandwielpictogram om de percentages in de kolom Conversiesnelheid te verbergen, zodat de focus op de conversiesnelheden blijft. De conversiekoersen worden vervolgens opgemaakt als decimalen, maar worden dienovereenkomstig als percentages geïnterpreteerd.

## Waarom &quot;Bezoekingen&quot; de juiste normalisatiemethode is voor [!DNL Auto-Target] activiteiten

Bij het analyseren van een [!DNL Auto-Target] activiteit, kies altijd Bezoekingen als gebrek normaliserend metrisch. [!DNL Auto-Target] voor personalisatie wordt een ervaring gekozen voor een bezoeker eenmaal per bezoek (formeel, eenmaal per Adobe Target-sessie), wat betekent dat de ervaring die een gebruiker wordt getoond, tijdens elk bezoek kan veranderen. Dus als u Unieke bezoekers als normaliserende metrisch gebruikt, zou het feit dat één enkele gebruiker veelvoudige ervaringen (over verschillende bezoeken) kan uiteindelijk zien tot verwarrende omzettingspercentages leiden.

Dit wordt in een eenvoudig voorbeeld geïllustreerd: een scenario overwegen waarin twee bezoekers een campagne starten die slechts twee ervaringen heeft. De eerste bezoeker bezoekt tweemaal. Zij worden toegewezen aan Experience A tijdens het eerste bezoek, maar beleven B tijdens het tweede bezoek (vanwege hun profielstatus die veranderde bij dat tweede bezoek). Na het tweede bezoek converteert de bezoeker een bestelling. De conversie wordt toegeschreven aan de ervaring die het laatst is opgedaan (Experience B). De tweede bezoeker bezoekt ook twee keer, en wordt Ervaring B getoond beide keer, maar nooit omzet.

Laten we de verslagen op bezoekersniveau en op bezoekersniveau vergelijken:

| Ervaring | Unieke bezoekers | Bezoeken | Conversies | Norm van bezoeker. Conv. Snelheid | Bezoek norm. Conv. Snelheid |
| --- | --- | --- | --- | --- | --- |
| A | 1 | 1 | - | 0% | 0% |
| B | 2 | 3 | 1 | 50% | 33,3% |
| Totalen | 2 | 4 | 1 | 50% | 25% |

*Tabel 1: Voorbeeld waarin bezoekers-genormaliseerde en bezoek-genormaliseerde rapporten voor een scenario worden vergeleken waarin de besluiten aan een bezoek kleven (en niet bezoeker, zoals met regelmatige tests A/B). De bezoeker-genormaliseerde metriek zijn verwarrend in dit scenario.*

Zoals uit de tabel blijkt, is er een duidelijke incongruentie van bezoekersaantallen. Ondanks het feit dat er in totaal twee unieke bezoekers zijn, is dit geen som van afzonderlijke unieke bezoekers voor elke ervaring. Hoewel de conversiekoers op bezoekersniveau niet noodzakelijkerwijs verkeerd is, hebben conversiekoersen op bezoekniveau veel meer zin als men individuele ervaringen vergelijkt. Formeel is de eenheid van analyse (&quot;bezoeken&quot;) dezelfde als de eenheid van beslissingswaanzin, wat betekent dat uitsplitsingen van meetgegevens op ervaringsniveau kunnen worden toegevoegd en vergeleken.

## Filter voor feitelijke bezoeken aan de activiteit

De standaardtelmethode van Adobe Analytics voor bezoeken aan een doelactiviteit kan bezoeken omvatten waarbij de gebruiker niet met de doelactiviteit heeft gewerkt. Dit is toe te schrijven aan de manier waarop de de activiteitstoewijzingen van het Doel in de de bezoekerscontext van de Analyse worden voortgeduurd. Als gevolg daarvan kan het aantal bezoeken aan de doelactiviteit soms worden opgevoerd, wat leidt tot een verlaging van de omrekeningskoersen.

Als u liever een melding wilt maken van bezoeken waarbij de gebruiker daadwerkelijk heeft gereageerd op de activiteit Auto-Target (door toegang tot de activiteit, een display/visit-gebeurtenis of een conversie), kunt u:

1. Maak een specifiek segment met resultaten van de betreffende doelactiviteit en
1. Filter de metrische bezoekers die dit segment gebruiken.

**Het segment maken:**

1. Selecteer **[!UICONTROL Components > Create Segment]** in de werkruimtewerkbalk.
2. Voer een **[!UICONTROL Title]** voor uw segment. In het onderstaande voorbeeld krijgt het segment de naam [!DNL "Hit with specific Auto-Target activity"].
3. Sleep de **[!UICONTROL Target Activities]** dimensie van het segment **[!UICONTROL Definition]** sectie.
4. Gebruik de **[!UICONTROL equals]** operator.
5. Zoek naar uw specifieke activiteit van het Doel.
6. Selecteer het tandwielpictogram en selecteer **[!UICONTROL Attribution model > Instance]** zoals weergegeven in onderstaande afbeelding.
7. Klik op **[!UICONTROL Save]**.

![Figuur5.png](assets/Figure5.png)
*Figuur 5: Gebruik een segment zoals hier getoond om metrische Visits in uw A4T voor te filtreren [!DNL Auto-Target] verslag*

Zodra het segment is gecreeerd, gebruik het om metrisch van Bebezoeken te filtreren, zodat omvat metrische bezoeken slechts bezoeken waar de gebruiker met de activiteit van het Doel interactie optrad.

**Bezoeken filteren met dit segment:**

1. Sleep het nieuwe segment van de componentenwerkbalk en houd de muisaanwijzer boven de basis van het segment **[!UICONTROL Visits]** metrisch label tot een blauw **[!UICONTROL Filter by]** wordt weergegeven.
2. Laat het segment los. Het filter wordt op die metrische waarde toegepast.

Het uiteindelijke deelvenster wordt als volgt weergegeven.

![Figuur 6.png](assets/Figure6.png)
*Figuur 6: Rapportpaneel met het segment Activiteit voor automatisch aanwijzen toegepast op het segment [!UICONTROL Visits] metrisch. Dit zorgt ervoor dat alleen bezoeken worden opgenomen wanneer een gebruiker daadwerkelijk met de betreffende doelactiviteit heeft gewerkt.*

## Zorg ervoor dat de maatstaf van het doel en de kenmerk zijn uitgelijnd op het optimalisatiecriterium

De integratie A4T maakt [!DNL Auto-Target]ML-model *opgeleid* dezelfde conversiegebeurtenisgegevens gebruiken die Adobe Analytics gebruikt om *prestatierapporten genereren*. Er zijn echter bepaalde veronderstellingen die moeten worden gebruikt bij de interpretatie van deze gegevens bij de opleiding van de modellen van het XML-systeem, die verschillen van de standaardveronderstellingen die tijdens de rapportagefase in Adobe Analytics zijn gemaakt.

In het bijzonder gebruiken de modellen van XML van Adobe Target een bezoek-scoped attributiemodel. Met andere woorden, zij gaan ervan uit dat een conversie moet plaatsvinden tijdens hetzelfde bezoek als een weergave van inhoud voor de activiteit, zodat de conversie &quot;toegeschreven&quot; kan worden aan het besluit van het ML-model. Dit is nodig om te garanderen dat Target zijn modellen tijdig kan opleiden; Het doel kan niet tot 30 dagen wachten op een conversie (het standaardtoewijzingsvenster voor rapporten in Adobe Analytics), alvorens het in de trainingsgegevens voor zijn modellen op te nemen.

Het verschil tussen de door de modellen van Target (tijdens de training) gebruikte attributie en de standaardattributie die wordt gebruikt bij het opvragen van gegevens (tijdens het genereren van rapporten) kan dus tot discrepanties leiden. Het kan zelfs lijken dat de modellen van het ML slecht presteren, terwijl de kwestie eigenlijk bij attributie ligt.


>[!TIP]
>
>Als de modellen van ML voor metrisch optimaliseren die verschillend van dat van de metriek wordt toegeschreven u in een rapport bekijkt, kunnen de modellen niet zoals verwacht presteren! Om dit te vermijden, verzeker de doelmetriek op uw rapport de zelfde metrische definitie en attributie gebruiken die door de modellen van XML van Doel wordt gebruikt.

De exacte metrische definitie en attribuutinstellingen zijn afhankelijk van de [optimalisatiecriterium](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#supported) u hebt opgegeven tijdens het maken van activiteiten.


### Doelgedefinieerde conversies of Analytische gegevens met *Metrische waarde maximaliseren per bezoek*

Wanneer metrisch een omzetting van het Doel of een metriek Analytics met is **Metrische waarde maximaliseren per bezoek**, staat de doel metrische definitie voor veelvoudige omzettingsgebeurtenissen toe om in het zelfde bezoek voor te komen.
Ga als volgt te werk om doelmetriek weer te geven met dezelfde toewijzingsmethode die door Adobe Target ML-modellen wordt gebruikt:

1. Houd de muisaanwijzer boven het tandwielpictogram van de gewenste meting:
   ![gearicon.png](assets/gearicon.png)
1. Blader vanuit het resulterende menu naar **[!UICONTROL Data settings]**.
1. Selecteren **[!UICONTROL Use non-default  attribution model]** (indien nog niet geselecteerd):
   ![non-default attributionmodel.png](assets/non-defaultattributionmodel.png)
1. Klik op **[!UICONTROL Edit]**.
1. Selecteren **[!UICONTROL Model]**: **[!UICONTROL Participation]**, en **[!UICONTROL Lookback window]**: **[!UICONTROL Visit]**.
   ![ParticipationbyVisit.png](assets/ParticipationbyVisit.png)
1. Klik op **[!UICONTROL Apply]**.

Deze stappen verzekeren uw rapport het doel metrisch aan de vertoning van de ervaring zal toeschrijven, als de doel metrische gebeurtenis gebeurde *elke keer* (&quot;deelname&quot;) aan hetzelfde bezoek dat een ervaring heeft opgedaan.

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

Met de wijzigingen aan het Bezoek en de doelstellingen metriek in voorafgaande secties, zou de definitieve wijziging u aan uw gebrek A4T voor moeten maken [!DNL Auto-Target] het melden paneel moet omzettingspercentages tot stand brengen die de correcte verhouding-dat van het gecorrigeerde doel metrisch, aan correct gefiltreerde metrische &quot;Bebezoeken&quot;zijn.

Doe dit door een Berekende Metrisch te creëren gebruikend de volgende stappen:

1. Selecteer **[!UICONTROL Components > Create Metric]** in de werkruimtewerkbalk.
1. Voer een **[!UICONTROL Title]** voor uw metrische waarde. Bijvoorbeeld &quot;Bezoek-gecorrigeerde Omzetsnelheid voor Activiteit XXX.&quot;
1. Selecteren **[!UICONTROL Format]** = Percentage en **[!UICONTROL Decimal Places]** = 2.
1. Sleep het relevante doel metrische voor uw activiteit (bijvoorbeeld, de Omzettingen van de Activiteit) in de definitie, en gebruik het tandwielpictogram op dit doel metrisch om het attributiemodel aan (Deelname aan te passen|Bezoek), zoals eerder beschreven.
1. Selecteren **[!UICONTROL Add > Container]** vanaf de rechterbovenhoek van het **[!UICONTROL Definition]** sectie.
1. Selecteer de operator voor delen (&#39;&#39;) tussen de twee containers.
1. Sleep het eerder gemaakte segment met de naam &quot;Actief met specifieke [!DNL Auto-Target] activiteit&quot;in dit leerprogramma-voor dit specifieke [!DNL Auto-Target] activiteit.
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

## Overzicht: Laatste voorbeeldwerkruimtevenster voor [!DNL Auto-Target] rapporten

Als u alle bovenstaande stappen in één venster combineert, wordt in de onderstaande afbeelding een volledige weergave getoond van het aanbevolen rapport voor [!DNL Auto-Target] A4T-activiteiten. Dit rapport is het zelfde als dat gebruikt door de machine het leren modellen van Target om uw doel metrisch te optimaliseren, en het neemt alle nuances en aanbevelingen op die in dit leerprogramma worden besproken. Dit verslag sluit ook het dichtst aan bij de telmethoden die worden gebruikt in de traditionele door Target gestuurde rapportage [!DNL Auto-Target] activiteiten.

![Figuur10.png](assets/Figure10.png)
*Figuur 10: De uiteindelijke A4T [!DNL Auto-Target] in Adobe Analytics Workspace, waarin alle aanpassingen aan metrische definities worden gecombineerd die in de vorige secties van dit document zijn beschreven.*
