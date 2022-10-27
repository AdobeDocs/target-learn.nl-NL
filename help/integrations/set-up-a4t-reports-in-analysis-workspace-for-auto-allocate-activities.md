---
title: A4T-rapporten instellen in Analysis Workspace voor automatisch toegewezen activiteiten
description: Zodra u uw Analytics voor de integratie van het Doel (A4T) op zijn plaats hebt en u auto-Wijs activiteiten in werking stelt, hoe kunt u ervoor zorgen u correct resultaten interpreteert? Voer de volgende stappen uit om A4T-rapporten in Analysis Workspace te configureren om de verwachte resultaten te verkrijgen bij het uitvoeren van activiteiten voor automatisch toewijzen.
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: null
source-git-commit: eb7232f1c6ed52860aa5ef86b50427fb96ab7894
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---

# A4T-rapporten instellen in Analysis Workspace voor [!DNL Auto-Allocate] activiteiten

An [!DNL Auto-Allocate] de activiteit identificeert een winnaar onder twee of meer ervaringen en wijst automatisch meer verkeer aan de winnaar toe terwijl de test blijft lopen en leren. De integratie Analytics for Target (A4T) voor [!DNL Auto-Allocate] kunt u uw rapportgegevens bekijken in Adobe Analytics en zelfs optimaliseren voor aangepaste gebeurtenissen of metriek die zijn gedefinieerd in Adobe Analytics.

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in Adobe Analytics Analysis Workspace, zijn enkele wijzigingen in de standaard **[!UICONTROL Analytics for Target]** het deelvenster moet correct worden geïnterpreteerd [!DNL Auto-Allocate] activiteiten, als gevolg van nuances in [optimalisatiecriteria](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#supported).

Deze zelfstudie doorloopt de aanbevolen wijzigingen voor het analyseren [!DNL Auto-Allocate] activiteiten in Workspace. De belangrijkste concepten zijn:

* Bezoekers dienen altijd te worden gebruikt als de normaliserende metrische waarde in [!DNL Auto-Allocate] activiteiten.
* Wanneer de metrische waarde een Adobe Analytics Metric is, hangt de juiste teller voor de omrekeningskoers af van het type optimalisatiecriteria dat tijdens het instellen van de activiteit is gekozen.
   * Het optimalisatiecriterium voor het optimaliseren van de unieke conversiesnelheid van bezoekers heeft een conversiesnelheid waarvan de teller een telling is van de unieke bezoekers met een positieve waarde van de metrische waarde.
   * De &quot;maximize metadata value per bezoeker* heeft een omzettingssnelheid waarvan de teller de normale metrische waarde in Adobe Analytics is. Dit wordt standaard opgegeven in het gedeelte **[!UICONTROL Analytics for Target]** in Workspace.
* Wanneer uw optimalisatiemetrische waarde een door Doel gedefinieerde omzettingsmeting is, wordt de standaardwaarde **[!UICONTROL Analytics for Target]** in Workspace kunt u het deelvenster configureren.
* De vertrouwensnummers in Workspace weerspiegelen niet de [conservatievere statistieken die door Auto-Toewijzing worden gebruikt](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html?lang=en#section_98388996F0584E15BF3A99C57EEB7629), en moet daarom worden geschrapt.


## A4T maken voor [!DNL Auto-Allocate] deelvenster in werkruimte

Een A4T maken voor [!DNL Auto-Allocate] rapport begint met **[!UICONTROL Analytics for Target]** in Workspace, zoals hieronder wordt weergegeven. Maak vervolgens de volgende selecties:

1. **[!UICONTROL Control Experience]**: U kunt elke ervaring kiezen
2. **[!UICONTROL Normalizing Metric]**: Selecteer Bezoekers - Automatisch toewijzen normaliseert de conversietarieven altijd door unieke bezoekers.
3. **[!UICONTROL Success Metrics]**: Selecteer de metrische waarde die u tijdens het creëren van activiteit hebt gebruikt - als dit een Doel bepaalde metrische omzetting was, selecteer **Activiteitenconversie**. Anders, selecteer metrisch Adobe Analytics die u gebruikte.

![AAFigure1.png](assets/AAFigure1.png)
*Afbeelding 1: Analyse voor instellen deelvenster Doel voor [!DNL Auto-Allocate] activiteiten.*

>[!NOTE]
>
> U kunt ook een vooraf gebouwde **[!UICONTROL Analytics for Target]** als u op de koppeling klikt in het rapportscherm in Adobe Target.

## Metrische gegevens of analysegegevens voor doelconversie met optimalisatiecriteria voor de optie &quot;Metrische waarde maximaliseren per bezoeker&quot;

De standaardhandgrepen van het A4T-deelvenster [!DNL Auto-Allocate] activiteiten waarbij het doel metrisch een Omzetting van het Doel, of een Metrische Analyse met optimalisatiecriterium &quot;Maximize Metric Value Per Visitor.&quot; is

Een voorbeeld van dit deelvenster wordt weergegeven voor de belastingmethode, waarbij &quot;Metrische waarde maximaliseren per bezoeker&quot; is geselecteerd als de optimalisatiecriteria op het moment dat de activiteit wordt gemaakt. Zoals eerder vermeld, [!DNL Auto-Allocate] gebruikt conservatievere betrouwbaarheidsberekeningen in vergelijking met de berekeningen van de **[!UICONTROL Analytics for Target]** deelvenster. Daarom wordt u aangeraden de betrouwbaarheidsmetrische gegevens en de bijbehorende meetwaarden voor de lagere en bovenste lift te verwijderen.

![Figuur2.png](assets/AAFigure2.png)
*Afbeelding 2: Het aanbevolen rapport voor [!DNL Auto-Allocate] activiteiten met een metrische analyse Maximaliseer Metrische Waarde per Bezoeker optimalisatiecriteria. Voor deze typen metriek en door Doel gedefinieerde conversiemetriek wordt de standaardinstelling **[!UICONTROL Analytics for Target]**kan worden gebruikt.*


## Analysemetrieken met optimalisatiecriteria voor de optimalisatie &#39;Unieke beeldconversiesnelheid maximaliseren&#39;

Wanneer een Adobe Analytics wordt gebruikt met een optimalisatiecriterium van *Unieke conversiesnelheid bezoeker maximaliseren*, de standaardwaarde **[!UICONTROL Analytics for Target]** in de werkruimte moet worden gewijzigd.

De succesmetrische waarde is nu een telling van unieke bezoekers voor wie de omzettingsmetrische waarde positief was. Dit kan worden bereikt door een segment te maken dat filtert om te slagen met een positieve waarde van metrisch. Maak dit segment als volgt:

1. Selecteer **Componenten** > **Segment maken** in de werkruimtewerkbalk.
1. Sleep de metrische waarde die tijdens het maken van de activiteit wordt gebruikt van het linkerdeelvenster naar het deelvenster **Definitie** van het segment.
1. Waarden van de metrische waarde selecteren die **groter dan** een numerieke waarde van 0.
1. Van de **Inclusief** vervolgkeuzelijst, selecteren **Bezoekers**
1. Geef uw segment een geschikte naam

In de onderstaande afbeelding ziet u een voorbeeld van het maken van segmenten, waarbij we bezoekers selecteren voor wie de inkomsten positief zijn.

![Figuur3.png](assets/AAFigure3.png)
*Figuur 3: Segment maken voor Adobe Analytics-metriek met optimalisatiecriteria die gelijk zijn aan Maximize Unique Visitor Conversion Rate. In dit voorbeeld is de metrische waarde Opbrengst en is het optimalisatiedoel het maximaliseren van het aantal bezoekers met positieve inkomsten.*

Zodra het aangewezen segment is gecreeerd, het gebrek  **[!UICONTROL Analytics for Target]** kan worden gewijzigd.

1. Een seconde toevoegen **Unieke bezoekers** metrische waarde langs de bestaande meetkolom voor bezoekers
2. Sleep het net gemaakte segment onder de eerste kolom om een deelvenster te maken dat lijkt op Figuur 4. Let op het verschil: het aantal unieke bezoekers met positieve inkomsten is een fractie van het totale aantal unieke bezoekers dat aan elke ervaring is toegewezen.
   ![Figuur4.png](assets/AAFigure4.png)
   *Figuur 4: Unieke bezoekers filteren op het nieuwe segment*
3. Een omrekeningskoers kan [snel berekend](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html?lang=en) door zowel de eerste als de tweede kolom te markeren, klikt u met de rechtermuisknop en selecteert u **Metrisch maken van selectie** > **Verdelen**. De standaardconversiesnelheid moet worden verwijderd en vervangen door deze nieuwe berekende maatstaf, zoals in de onderstaande afbeelding wordt getoond. Mogelijk moet u de nieuwe berekende metrische waarde bewerken om als een **Indeling** > **Percentage** tot twee decimalen zoals getoond.
   ![Figuur4.png](assets/AAFigure5.png)

   *Figuur 4: Het uiteindelijke deelvenster Automatisch toewijzen waarin de conversiekoersen voor een metrische omzettingsmethode met binaire inkomsten worden weergegeven*


## Conclusie

De stappen hierboven hebben aangetoond hoe te correct te vormen [!DNL Workspace] om rapportgegevens automatisch toewijzen weer te geven. Samenvatten:

* Wanneer metrisch een Doel bepaalde omzettings metrisch of Metrisch van Adobe Analytics met optimalisatiecriterium is *Metrische waarde maximaliseren per bezoeker*, moet het standaardwerkruimtepaneel worden gebruikt dat met bezoekers is geconfigureerd als een normalisatiemethode.
* Wanneer metrisch metrisch Adobe Analytics met optimalisatiecriterium &quot;Maximize Unique Visitor Conversion Rate&quot; is, moet u een omzettingspercentage gebruiken dat als fractie van bezoekers wordt bepaald voor wie metrisch positief is. Dit wordt gedaan door een overeenkomstig segment te creëren, dat unieke bezoeker metrisch filtert.
