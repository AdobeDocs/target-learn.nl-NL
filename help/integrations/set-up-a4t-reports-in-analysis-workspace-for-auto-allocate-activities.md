---
title: A4T-rapporten instellen in [!DNL Analysis Workspace] for [!UICONTROL Auto-Allocate] Activiteiten
description: Hoe kan ik configureren [!UICONTROL Analytics for Target] (A4T) rapporten in [!DNL Adobe] [!DNL Analysis Workspace] bij uitvoering [!UICONTROL Auto-Allocate] activiteiten.
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 7d53adce-cc05-4754-9369-9cc1763a9450
source-git-commit: 190a67832f378e15090115420bfaf8a4af4b9cb9
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# A4T-rapporten instellen in [!DNL Analysis Workspace] for [!DNL Auto-Allocate] activiteiten

An [[!UICONTROL Auto-Allocate] activiteit](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html){target=_blank} in [!DNL Adobe Target] identificeert een winnaar onder twee of meer ervaringen en wijst automatisch bezoekersverkeer aan de winnaar toe terwijl de test blijft lopen en leren. De [!UICONTROL Analytics for Target] (A4T) integratie voor [!UICONTROL Auto-Allocate] Hiermee kunt u rapportgegevens weergeven in [!DNL Adobe Analytics]en kunt u optimaliseren voor aangepaste gebeurtenissen of maateenheden die zijn gedefinieerd in [!DNL Analytics].

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in [!DNL Adobe Analytics] [!DNL Analysis Workspace], enkele wijzigingen in de standaardwaarde [!UICONTROL Analytics for Target] deelvenster kan nodig zijn voor een juiste interpretatie [!UICONTROL Auto-Allocate] activiteiten. Deze wijzigingen zijn nodig vanwege de nuances in [optimalisatiemetrische criteria](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank}.

Elk type van optimalisatiemetrisch vereist een verschillende rapportconfiguratie in A4T, als volgt:

* Een [!DNL Analytics] metrisch

   * [!UICONTROL Maximize metric value per visitor]
   * [!UICONTROL Maximize unique visitor conversion rate]

* Een [!DNL Target]-gedefinieerde metrische omzetting

Dit leerprogramma behandelt algemene begeleiding A4T, en criteria-specifieke stappen van de rapportconfiguratie.

## Metrische gegevens voor analyse met &quot;[!UICONTROL Maximize Metric Value Per Visitor]&quot; optimalisatiecriteria

**Definitie**: (Totale metrische waarde) / (# bezoekers)

Om het rapport te vormen, breng de volgende veranderingen in het rapport A4T aan:

| Vereiste wijzigingen | [!DNL Target]-triggerrapport | A4T-deelvensterrapport |
| --- | --- | --- |
| Metrische waarde maximaliseren voor een [!DNL Analytics] metrisch | <ul><li>Verwijderen [!UICONTROL Confidence] metriek.</li><li>Verwijderen [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)]. Behouden [!UICONTROL Lift (Med)].</li><li>De percentagepresentatie uitschakelen in het menu [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li><li>De naam van de [!UICONTROL Conversion] tarief metrisch aan &quot;Metrisch/Bezoeker.&quot;</li></ul> | <ul><li>Verwijderen [!UICONTROL Confidence] metriek.</li><li>Verwijderen [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)] Behouden [!UICONTROL Lift (Med)].</li><li>De percentagepresentatie uitschakelen in het menu [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li><li>De naam van de [!UICONTROL Conversion] tarief metrisch aan &quot;Metrisch/Bezoeker.&quot;</li><li>Zorg ervoor dat de datum- en tijdbereiken overeenkomen met de waarden die u in het dialoogvenster [!DNL Target] verslag. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li></ul> |

![Maximaliseer metrische waarde voor opbrengst](/help/integrations/assets/maximize-metric-value-revenue.png)

## [!DNL Analytics] metriek met &quot;[!UICONTROL Unique Visitor Conversion Rate]&quot; optimalisatiecriteria

**Definitie**: (# van unieke bezoekers met een positieve waarde van de norm) / (totaal aantal unieke bezoekers)

Voorbeeld: stel dat de optimalisatiemethode [!UICONTROL Revenue]. Er zijn vijf unieke bezoekers in de activiteit en drie van deze unieke bezoekers kopen een aankoop. In dit voorbeeld is deze waarde = (3 bezoekers voor wie [!UICONTROL Revenue] is positief) / (5 totaal unieke bezoekers) = 0,6 = 60%.

>[!NOTE]
>
>Conversiesnelheid waarnaar hier wordt verwezen, kan verwijzen naar handelingen buiten bestellingen, zoals klikken, afbeeldingen enzovoort. In deze gevallen zou het criterium nog steeds het maximaliseren zijn van het aantal bezoekers dat klikt of de pagina bekijkt.

Om het rapport te vormen, breng de volgende veranderingen in het rapport A4T aan:

| Vereiste wijzigingen | Doel-teweeggebracht rapport | A4T-deelvensterrapport |
| --- | --- | --- |
| Omzettingen maximaliseren voor een [!DNL Analytics] metrisch | <ul><li>Verwijderen [!UICONTROL Confidence] metriek.</li><li>Alle drie verwijderen [!UICONTROL Lift] metriek.</li><li>De percentagepresentatie uitschakelen in het menu [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li></ul> | <ul><li>Verwijderen [!UICONTROL Confidence] metriek.</li><li>Alle drie verwijderen [!UICONTROL Lift] metriek.</li><li>Maak een segment om bezoekers met een positieve metrische waarde te filteren die de geanalyseerde activiteit hebben bekeken. Zie [Een segment maken](#segment) hieronder.</li><li>De automatisch gevulde gegevens vervangen [!UICONTROL Conversion Rate] metrisch, dus dat is de scheiding tussen [!UICONTROL Unique visitors] met een positieve metrische waarde en unieke bezoekers. Zie [De metrische conversiesnelheid bijwerken](#update-conversion-metric) hieronder.</li><li>De percentagepresentatie uitschakelen in het menu [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li><li>Zorg ervoor dat de datum- en tijdbereiken overeenkomen met de waarden die u in het dialoogvenster [!DNL Target] verslag. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li></ul> |

### Standaardrapport van A4T-panel - aanvullende richtlijnen

De volgende secties bevatten meer informatie over extra begeleiding aangezien u opstelling uw standaardA4T paneelrapport.

#### Een segment maken {#segment}

1. Klik op de knop **&quot;+&quot;-teken** naast **[!UICONTROL Segments]** in het linkerspoor.

   ![Het plusteken naast segmenten in de linkerrails.](/help/integrations/assets/plus-sign.png)

1. Titel het segment &quot;Bezoekers met positieve metrische waarde&quot;.
1. Onder **[!UICONTROL Definition]**, naast **[!UICONTROL Include]**, selecteert u **[!UICONTROL Visitor]**.
1. Onder **[!UICONTROL Definition]** selecteert u de optimalisatiemetrische waarde in uw activiteit.

   In dit voorbeeld, veronderstel [!UICONTROL Revenue] als optimalisatiemetrisch.

1. Selecteer &quot;[!UICONTROL is greater than]&quot;, geeft u vervolgens &quot;0&quot; op.

   Deze instellingen filteren voor alle bezoekers met een positieve metrische waarde.

1. Klik op **[!UICONTROL Save]**.

   ![Positieve metrische waarde](/help/integrations/assets/positive-metric-value.png)

1. Voeg het nieuwe segment met de naam &quot;Bezoekers met positieve metrische waarde&quot; toe aan het deelvenster A4T.
1. Sleep de [!UICONTROL Unique Visitors] metrisch in dezelfde kolom als de &quot;Bezoekers met positieve metrische waarde&quot;.

   Deze configuratie leidt tot een segment van alle unieke bezoekers voor wie de metrische waarde positief is. In dit voorbeeld zijn alle unieke bezoekers met een omzet die groter was dan nul.

#### Werk de [!UICONTROL Conversion Rate] metrisch {#update-conversion-metric}

1. Als u dat nog niet hebt gedaan, verwijdert u de bestaande [!UICONTROL Conversion Rate] in het deelvenster, zoals hieronder wordt uitgelegd.
1. Voeg metrisch toe door &quot;+&quot;teken naast te klikken **[!UICONTROL Metrics]** in het linkerspoor.
1. Geef de metrische &quot;Conversiesnelheid&quot; een naam en definieer deze als &quot;(&quot;[!UICONTROL Unique Visitors] met positieve metrische waarde)&quot; gedeeld door &quot;Unieke Bezoekers&quot;, zoals hieronder aangegeven.

   Voeg het nieuwe segment (stappen hieronder gedefinieerd) van &quot;Bezoekers met positieve metrische waarde&quot;, de operator voor delen, de metrische waarde &quot;Unieke bezoekers&quot; in de teller en &quot;Unieke bezoekers&quot; als noemer toe.

   ![Conversiesnelheid in het deelvenster A4T.](/help/integrations/assets/conversion-rate.png)

1. Klik op **[!UICONTROL Save]**.

1. Sleep de nieuwe metrische waarde voor Conversiesnelheid naar het bestaande deelvenster.
1. Klik op het tandwielpictogram en schakel vervolgens de optie **[!UICONTROL Percent]** selectievakje, omdat deze waarde tot verwarring kan leiden.

   De correcte configuratie van het rapport zou een resultaat moeten opleveren dat op de volgende illustratie lijkt:

   ![Unieke conversiekoers bezoek in het rapport van het A4T-deelvenster](/help/integrations/assets/a4t-aa-maximize-metric-value-revenue.png)

## [!DNL Target]-gedefinieerde omrekeningskoers

Om het rapport te vormen, breng de volgende veranderingen in het rapport A4T aan:

| Vereiste wijzigingen | Doel-teweeggebracht rapport | A4T-deelvensterrapport |
| --- | --- | --- |
| [!DNL Analytics] rapporteren met [!DNL Target] omzettingsmetrisch | <ul><li>Verwijderen [!UICONTROL Confidence] metriek.</li><li>Verwijderen [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)]. Lift (gemiddeld) houden.</li><li>De percentagepresentatie uitschakelen in het menu [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li></ul> | <ul><li>Verwijderen [!UICONTROL Confidence] metriek.</li><li>Verwijderen [!UICONTROL Lift (Low)] en [!UICONTROL Lift (High)]. Behouden [!UICONTROL Lift (Med)].</li><li>De percentagepresentatie uitschakelen in het menu [!UICONTROL Conversion Rate] om verwarring te voorkomen. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li><li>Zorg ervoor dat de datum- en tijdbereiken overeenkomen met de waarden die u in het dialoogvenster [!DNL Target] verslag. Zie [Algemene richtsnoeren voor A4T](#guidance) hieronder.</li></ul> |

De correcte configuratie van het rapport zou een resultaat moeten opleveren dat op de volgende illustratie lijkt:

![Activiteitenomzettingen](/help/integrations/assets/optimized-table.png)

## Algemene richtsnoeren voor A4T {#guidance}

U kunt naar een vooraf ontworpen [!UICONTROL Analytics for Target] door in het rapportscherm op de koppeling te klikken [!UICONTROL Target] (dit wordt later in deze handleiding aangeduid als &quot;[!DNL Target]-triggerrapport&quot;). U kunt ook het A4T-deelvenster maken in [!DNL Analytics] (details verderop in deze sectie).

In de volgende secties wordt aangegeven welke configuraties vereist zijn, afhankelijk van welke van deze methoden u kiest. De volgende stappen dienen echter als algemene leidraad voor A4T:

* Verwijder de betrouwbaarheidsmetriek uit het deelvenster A4T, ongeacht de methode voor het maken van het deelvenster (beide worden hieronder beschreven). Verwijs in plaats daarvan naar deze waarden in [!DNL Target] rapportage. Bovendien kunnen winnaars van activiteiten worden geïdentificeerd in [!DNL Target] rapportage. Gegevens over de identificatie van de winnaars zijn te vinden in de [De winnaar van de activiteit identificeren](#winner) hieronder.
>>
* Schakel de optie &quot;[!UICONTROL Percent]&quot; presentatie van de [!UICONTROL Conversion Rate] metrisch. Zie [Het percentage verbergen in het pop-upmenu [!UICONTROL Conversion Rate] kolom](#hide-percentage) hieronder.
>>
* Als u een A4T paneel bouwt, zorg ervoor dat de datum en de tijdwaaiers dat aanpassen van uw [!DNL Target] verslag. Zie [De datum en tijd uitlijnen in het deelvenster A4T](#aligning-date-and-time) hieronder.

### Het percentage verbergen in het pop-upmenu [!UICONTROL Conversion Rate] kolom {#hide-percentage}

1. Klik op de knop **tandwiel** pictogram naast de titel van het pictogram [!UICONTROL Conversion Rate] kolom.

   ![Pictogram vistuig in de kolom Conversiesnelheid](/help/integrations/assets/coversion-rate-gear-icon.png)

   De [!UICONTROL Column] dialoogvenster met instellingen wordt weergegeven:

   ![Kolominstellingen, dialoogvenster](/help/integrations/assets/column-settings-dialog-box.png){width="200"}

1. Hef de selectie van **[!UICONTROL Percent]** selectievakje.

   Uw A4T-deelvenster bevat nu geen percentages als de [!UICONTROL Conversion Rate] en overeenkomsten [!DNL Target], zoals hieronder weergegeven:

   ![Kolom Conversiesnelheid die geen percentages toont](/help/integrations/assets/no-percentages.png)

### De datum en tijd uitlijnen in het deelvenster A4T {#aligning-date-and-time}

1. Controleer onder elk deelvenster het datumbereik waarnaar het deelvenster verwijst om te controleren of het datumbereik overeenkomt met dat van het dialoogvenster [!DNL Target] verslag.

   ![Datumbereik in het deelvenster A4T](/help/integrations/assets/date-range.png)

1. In [!DNL Analytics]stelt u het tijdbereik in op 12.00 - 11.59 uur.

### De winnaar van de activiteit identificeren {#winner}

[!DNL Auto-Allocate] winnaars van de activiteit worden geselecteerd wanneer er een winnende omrekeningskoers is met betrouwbaarheidswaarden groter dan of gelijk aan 95%. Naar deze waarden moet worden verwezen in het dialoogvenster [!DNL Target] rapporten, aangezien betrouwbaarheidsberekeningen de conservatievere methodes weerspiegelen [!DNL Target] aanbevolen voor [!UICONTROL Auto-Allocate] activiteiten. Zie [Statistische garanties voor automatische toewijzing](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/determine-winner.html#section_7AF3B93E90BA4B80BC9FC4783B6A389C){target=_blank} in de *[!UICONTROL Adobe Target Business Practitioner Guide]*.

>[!NOTE]
>
De badges &quot;No Winner yet&quot; en &quot;Winner&quot; zijn niet beschikbaar in het deelvenster A4T in [!DNL Analysis Workspace]. Ook de winnaar &quot;star&quot;-badge weergegeven in [!DNL Target] rapporten voor [!UICONTROL Auto-Allocate] activiteiten moeten worden genegeerd. Zie [Automatisch toewijzen](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#aa){target=_blank} in *A4T-ondersteuning voor activiteiten voor automatisch toewijzen en automatisch richten* in de *[!UICONTROL Adobe Target Business Practitioner Guide]*.

### A4T maken voor [!UICONTROL Auto-Allocate] deelvenster in [!DNL Analysis Workspace]

1. Een A4T-deelvenster maken voor een [!UICONTROL Auto-Allocate] activiteitenverslag, beginnen met de [!UICONTROL Analytics for Target] deelvenster in [!DNL Analysis Workspace], zoals hieronder weergegeven.

   ![Analyses voor doel - rapport Automatisch toewijzen](/help/integrations/assets/a4t-auto-allocate-report.png)

1. Maak de volgende selecties:

   * **[!UICONTROL Control Experience]**: Kies een ervaring.
   * **[!UICONTROL Normalizing Metric]**: Select **[!UICONTROL Visitors]** (Wordt standaard opgenomen in het deelvenster A4T). [!UICONTROL Auto-Allocate] normaliseert altijd de omrekeningskoersen door unieke bezoekers.
   * **Succeswaarden**: Selecteer dezelfde metrische waarde (optimalisatie) die u tijdens het maken van activiteiten hebt gebruikt. Als dit een [!DNL Target]-gedefinieerde metrische conversie, selecteer **[!UICONTROL Activity Conversion]**. Anders selecteert u de [!DNL Adobe Analytics] metrisch die u gebruikte.









