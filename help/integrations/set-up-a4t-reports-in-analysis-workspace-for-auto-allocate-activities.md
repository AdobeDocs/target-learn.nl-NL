---
title: Hoe te opstelling A4T Rapporten in  [!DNL Analysis Workspace]  voor [!UICONTROL Auto-Allocate] Activiteiten
description: Hoe vorm ik [!UICONTROL Analytics for Target] (A4T) rapporten in  [!DNL Adobe] [!DNL Analysis Workspace] wanneer het runnen van [!UICONTROL Auto-Allocate] activiteiten.
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 7d53adce-cc05-4754-9369-9cc1763a9450
source-git-commit: 190a67832f378e15090115420bfaf8a4af4b9cb9
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 0%

---

# A4T-rapporten instellen in [!DNL Analysis Workspace] voor [!DNL Auto-Allocate] -activiteiten

Een [[!UICONTROL Auto-Allocate] activiteit ](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html) {target=_blank} in [!DNL Adobe Target] identificeert een winnaar onder twee of meer ervaringen en wijst automatisch bezoekersverkeer aan de winnaar toe terwijl de test blijft lopen en leren. Met de integratie [!UICONTROL Analytics for Target] (A4T) voor [!UICONTROL Auto-Allocate] kunt u rapportgegevens weergeven in [!DNL Adobe Analytics] en kunt u optimaliseren voor aangepaste gebeurtenissen of metriek die zijn gedefinieerd in [!DNL Analytics] .

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in [!DNL Adobe Analytics] [!DNL Analysis Workspace] , kunnen enkele wijzigingen in het standaard [!UICONTROL Analytics for Target] -deelvenster nodig zijn om [!UICONTROL Auto-Allocate] -activiteiten correct te interpreteren. Deze aanpassingen zijn nodig toe te schrijven aan de nuances in [ metrische criteria van optimalisering ](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported) {target=_blank}.

Elk type van optimalisatiemetrisch vereist een verschillende rapportconfiguratie in A4T, als volgt:

* Een [!DNL Analytics] -metrische waarde gebruiken

   * [!UICONTROL Maximize metric value per visitor]
   * [!UICONTROL Maximize unique visitor conversion rate]

* Een door [!DNL Target] gedefinieerde metrische omzetting gebruiken

Dit leerprogramma behandelt algemene begeleiding A4T, en criteria-specifieke stappen van de rapportconfiguratie.

## Metrische gegevens voor analyse met optimalisatiecriteria &quot;[!UICONTROL Maximize Metric Value Per Visitor]&quot;

**Definitie**: (Algemene Metrische Waarde) / (# van Bezoekers)

Om het rapport te vormen, breng de volgende veranderingen in het rapport A4T aan:

| Vereiste wijzigingen | [!DNL Target] -triggerrapport | A4T-deelvensterrapport |
| --- | --- | --- |
| Metrische waarde maximaliseren voor een [!DNL Analytics] -metrische waarde | <ul><li>Verwijder [!UICONTROL Confidence] metriek.</li><li>Verwijderen [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)] . Houd [!UICONTROL Lift (Med)] .</li><li>Schakel de percentagepresentatie uit in de kolom [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li><li>Wijzig de naam van de metrische waarde voor de [!UICONTROL Conversion] frequentie in &quot;Metrisch / Bezoeker&quot;.</li></ul> | <ul><li>Verwijder [!UICONTROL Confidence] metriek.</li><li>Verwijder [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)] Keep [!UICONTROL Lift (Med)] .</li><li>Schakel de percentagepresentatie uit in de kolom [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li><li>Wijzig de naam van de metrische waarde voor de [!UICONTROL Conversion] frequentie in &quot;Metrisch / Bezoeker&quot;.</li><li>Zorg ervoor dat de datum- en tijdbereiken overeenkomen met de waarden die u in het [!DNL Target] -rapport ziet. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li></ul> |

![ Maximaliseer metrische waarde voor opbrengst ](/help/integrations/assets/maximize-metric-value-revenue.png)

## [!DNL Analytics] metriek met [!UICONTROL Unique Visitor Conversion Rate] optimalisatiecriteria

**Definitie**: (# van Unieke Bezoekers met een positieve waarde van metrisch) / (Totaal # van Unieke Bezoekers)

Voorbeeld: stel dat de optimalisatiemetrische waarde [!UICONTROL Revenue] is. Er zijn vijf unieke bezoekers in de activiteit en drie van deze unieke bezoekers kopen een aankoop. In dit voorbeeld is deze waarde = (3 bezoekers voor wie [!UICONTROL Revenue] positief is) / (5 unieke bezoekers) = 0,6 = 60%.

>[!NOTE]
>
>Conversiesnelheid waarnaar hier wordt verwezen, kan verwijzen naar handelingen buiten bestellingen, zoals klikken, afbeeldingen enzovoort. In deze gevallen zou het criterium nog steeds het maximaliseren zijn van het aantal bezoekers dat klikt of de pagina bekijkt.

Om het rapport te vormen, breng de volgende veranderingen in het rapport A4T aan:

| Vereiste wijzigingen | Doel-teweeggebracht rapport | A4T-deelvensterrapport |
| --- | --- | --- |
| Omzettingen maximaliseren voor een [!DNL Analytics] metrisch | <ul><li>Verwijder [!UICONTROL Confidence] metriek.</li><li>Verwijder alle drie de meetgegevens van [!UICONTROL Lift] .</li><li>Schakel de percentagepresentatie uit in de kolom [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li></ul> | <ul><li>Verwijder [!UICONTROL Confidence] metriek.</li><li>Verwijder alle drie de meetgegevens van [!UICONTROL Lift] .</li><li>Maak een segment om bezoekers met een positieve metrische waarde te filteren die de geanalyseerde activiteit hebben bekeken. Zie [ een segment ](#segment) hieronder creëren.</li><li>Vervang de automatisch gevulde [!UICONTROL Conversion Rate] -meting, zodat deze het verschil tussen [!UICONTROL Unique visitors] aangeeft, door een positieve metrische waarde en unieke bezoekers. Zie [ metrische het Tarief van de Omzetting bijwerken ](#update-conversion-metric) hieronder.</li><li>Schakel de percentagepresentatie uit in de kolom [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li><li>Zorg ervoor dat de datum- en tijdbereiken overeenkomen met de waarden die u in het [!DNL Target] -rapport ziet. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li></ul> |

### Standaardrapport van A4T-panel - aanvullende richtlijnen

De volgende secties bevatten meer informatie over extra begeleiding aangezien u opstelling uw standaardA4T paneelrapport.

#### Een segment maken {#segment}

1. Klik op het plusteken **&quot;+&quot;** naast **[!UICONTROL Segments]** in de linkertrack.

   ![ plus teken naast segmenten in het linkerspoor.](/help/integrations/assets/plus-sign.png)

1. Titel het segment &quot;Bezoekers met positieve metrische waarde&quot;.
1. Selecteer onder **[!UICONTROL Definition]** naast **[!UICONTROL Include]** de optie **[!UICONTROL Visitor]** .
1. Selecteer onder **[!UICONTROL Definition]** de optimalisatiemetrische waarde in uw activiteit.

   In dit voorbeeld wordt [!UICONTROL Revenue] aangenomen als de optimalisatiemetrische waarde.

1. Selecteer de operator &quot;[!UICONTROL is greater than]&quot; en geef vervolgens &quot;0&quot; op.

   Deze instellingen filteren voor alle bezoekers met een positieve metrische waarde.

1. Klik op **[!UICONTROL Save]**.

   ![ Positieve metrische waarde ](/help/integrations/assets/positive-metric-value.png)

1. Voeg het nieuwe segment met de naam &quot;Bezoekers met positieve metrische waarde&quot; toe aan het deelvenster A4T.
1. Sleep de metrische waarde van [!UICONTROL Unique Visitors] naar dezelfde kolom als &quot;Bezoekers met positieve metrische waarde&quot;.

   Deze configuratie leidt tot een segment van alle unieke bezoekers voor wie de metrische waarde positief is. In dit voorbeeld zijn alle unieke bezoekers met een omzet die groter was dan nul.

#### De metrische waarde van [!UICONTROL Conversion Rate] bijwerken {#update-conversion-metric}

1. Als u dat nog niet hebt gedaan, verwijdert u de bestaande kolom [!UICONTROL Conversion Rate] uit het deelvenster, zoals hieronder wordt uitgelegd.
1. Voeg een metrische waarde toe door op het plusteken (+) naast de sectie **[!UICONTROL Metrics]** in de linkertrack te klikken.
1. Geef de metrische &quot;Conversiesnelheid&quot; een naam en definieer deze als &quot;( [!UICONTROL Unique Visitors] met positieve metrische waarde)&quot; gedeeld door &quot;Unieke bezoekers&quot;, zoals hieronder wordt weergegeven.

   Voeg het nieuwe segment (stappen hieronder gedefinieerd) van &quot;Bezoekers met positieve metrische waarde&quot;, de operator voor delen, de metrische waarde &quot;Unieke bezoekers&quot; in de teller en &quot;Unieke bezoekers&quot; als noemer toe.

   ![ het tarief van de Omzetting in paneel A4T.](/help/integrations/assets/conversion-rate.png)

1. Klik op **[!UICONTROL Save]**.

1. Sleep de nieuwe metrische waarde voor Conversiesnelheid naar het bestaande deelvenster.
1. Klik op het tandwielpictogram en schakel het selectievakje **[!UICONTROL Percent]** uit, omdat deze waarde tot verwarring kan leiden.

   De correcte configuratie van het rapport zou een resultaat moeten opleveren dat op de volgende illustratie lijkt:

   ![ Unieke het bezoekomrekeningskoers in A4T paneelrapport ](/help/integrations/assets/a4t-aa-maximize-metric-value-revenue.png)

## [!DNL Target] - gedefinieerde conversiesnelheid

Om het rapport te vormen, breng de volgende veranderingen in het rapport A4T aan:

| Vereiste wijzigingen | Doel-teweeggebracht rapport | A4T-deelvensterrapport |
| --- | --- | --- |
| [!DNL Analytics] rapporteren met [!DNL Target] metrische conversie | <ul><li>Verwijder [!UICONTROL Confidence] metriek.</li><li>Verwijderen [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)] . Lift (gemiddeld) houden.</li><li>Schakel de percentagepresentatie uit in de kolom [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li></ul> | <ul><li>Verwijder [!UICONTROL Confidence] metriek.</li><li>Verwijderen [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)] . Houd [!UICONTROL Lift (Med)] .</li><li>Schakel de percentagepresentatie uit in de kolom [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li><li>Zorg ervoor dat de datum- en tijdbereiken overeenkomen met de waarden die u in het [!DNL Target] -rapport ziet. Zie [ Algemene begeleiding voor A4T ](#guidance) hieronder.</li></ul> |

De correcte configuratie van het rapport zou een resultaat moeten opleveren dat op de volgende illustratie lijkt:

![ de omzettingen van de Activiteit ](/help/integrations/assets/optimized-table.png)

## Algemene richtsnoeren voor A4T {#guidance}

U kunt naar een vooraf gebouwd [!UICONTROL Analytics for Target] paneel navigeren door de verbinding van het rapportscherm in [!UICONTROL Target] te klikken (dit wordt naar later in deze gids verwezen als &quot; [!DNL Target] - teweeggebracht rapport&quot;). U kunt ook het deelvenster A4T maken in [!DNL Analytics] (details verderop in deze sectie).

In de volgende secties wordt aangegeven welke configuraties vereist zijn, afhankelijk van welke van deze methoden u kiest. De volgende stappen dienen echter als algemene leidraad voor A4T:

* Verwijder de betrouwbaarheidsmetriek uit het deelvenster A4T, ongeacht de methode voor het maken van het deelvenster (beide worden hieronder beschreven). Verwijs in plaats daarvan naar deze waarden in [!DNL Target] -rapporten. Bovendien kunnen winnaars van activiteiten worden geïdentificeerd in [!DNL Target] -rapporten. De details op de identificatie van de activiteitenwinnaar kunnen in [ worden gevonden identificeren de activiteit winnaar ](#winner) hieronder sectie.
>>
* Om verwarring te voorkomen, uncheck de &quot;[!UICONTROL Percent]&quot;presentatie van [!UICONTROL Conversion Rate] metrisch. Zie [ het percentage van de [!UICONTROL Conversion Rate] kolom ](#hide-percentage) hieronder verbergen.
>>
* Als u een A4T-deelvenster maakt, moet u ervoor zorgen dat de datum- en tijdbereiken overeenkomen met die van uw [!DNL Target] -rapport. Zie [ de datum en de tijd in het paneel A4T ](#aligning-date-and-time) hieronder richten.

### Het percentage verbergen in de kolom [!UICONTROL Conversion Rate] {#hide-percentage}

1. Klik het **versnelling** pictogram naast de titel van de [!UICONTROL Conversion Rate] kolom.

   ![ pictogram van het Gear in de kolom van het Tarief van de Omzetting ](/help/integrations/assets/coversion-rate-gear-icon.png)

   Het dialoogvenster [!UICONTROL Column] -instellingen wordt weergegeven:

   ![ de montages van de Kolom dialoogdoos ](/help/integrations/assets/column-settings-dialog-box.png){width="200"}

1. Schakel het selectievakje **[!UICONTROL Percent]** uit.

   Het deelvenster A4T bevat nu geen percentages als de [!UICONTROL Conversion Rate] en de overeenkomende waarden [!DNL Target] , zoals hieronder wordt getoond:

   ![ de kolom van het Tarief van de Omzetting die geen percentages toont ](/help/integrations/assets/no-percentages.png)

### De datum en tijd uitlijnen in het deelvenster A4T {#aligning-date-and-time}

1. Controleer onder elk deelvenster het datumbereik waarnaar het deelvenster verwijst om te controleren of het datumbereik overeenkomt met dat van het [!DNL Target] -rapport.

   ![ waaier van de Datum in paneel A4T ](/help/integrations/assets/date-range.png)

1. Stel in [!DNL Analytics] het tijdbereik in op 12.00 - 11.59 uur.

### De winnaar van de activiteit identificeren {#winner}

[!DNL Auto-Allocate] winnaars van activiteit worden geselecteerd wanneer er een winnende omzettingspercentage met betrouwbaarheidswaarden groter dan of gelijk aan 95% is. Naar deze waarden moet worden verwezen in de [!DNL Target] -rapporten, aangezien betrouwbaarheidsberekeningen de conservatievere methoden weergeven die [!DNL Target] aanbeveelt voor [!UICONTROL Auto-Allocate] -activiteiten. Zie [ Statistische garanties van auto-Wijs ](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/determine-winner.html#section_7AF3B93E90BA4B80BC9FC4783B6A389C) {target=_blank} in *[!UICONTROL Adobe Target Business Practitioner Guide]* toe.

>[!NOTE]
>
De badges &quot;Geen Winner nog&quot; en &quot;Winner&quot; zijn niet beschikbaar in het deelvenster A4T in [!DNL Analysis Workspace] . De winnaar die in [!DNL Target] -rapporten voor [!UICONTROL Auto-Allocate] -activiteiten wordt weergegeven, moet ook worden genegeerd. Zie [ auto-Wijs ](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#aa) toe {target=_blank} in *steun A4T voor auto-Wijs en auto-Doel activiteiten* in *[!UICONTROL Adobe Target Business Practitioner Guide]*.

### Het deelvenster A4T voor [!UICONTROL Auto-Allocate] maken in [!DNL Analysis Workspace]

1. Als u een A4T-deelvenster wilt maken voor een [!UICONTROL Auto-Allocate] activiteitenrapport, begint u met het [!UICONTROL Analytics for Target] -deelvenster in [!DNL Analysis Workspace] , zoals hieronder wordt weergegeven.

   ![ Analytics voor Doel - auto-Wijs rapport ](/help/integrations/assets/a4t-auto-allocate-report.png) toe

1. Maak de volgende selecties:

   * **[!UICONTROL Control Experience]**: kies een ervaring.
   * **[!UICONTROL Normalizing Metric]**: Selecteer **[!UICONTROL Visitors]** (dit staat standaard in het deelvenster A4T). [!UICONTROL Auto-Allocate] normaliseert conversietarieven altijd door unieke bezoekers.
   * **Metriek van het Succes**: Selecteer zelfde (optimalisering) metrisch die u tijdens activiteitenverwezenlijking gebruikte. Selecteer **[!UICONTROL Activity Conversion]** als dit een [!DNL Target] -gedefinieerde omzettingsmetrische waarde is. Anders selecteert u de metrische waarde van [!DNL Adobe Analytics] die u hebt gebruikt.









