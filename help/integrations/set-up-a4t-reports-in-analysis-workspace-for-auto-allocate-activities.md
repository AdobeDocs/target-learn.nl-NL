---
title: A4T-rapporten instellen in [!DNL Analysis Workspace] for [!UICONTROL Auto-Allocate] Activiteiten
description: Hoe kan ik A4T-rapporten configureren in [!DNL Analysis Workspace] om de verwachte resultaten op te halen wanneer de toepassing wordt uitgevoerd [!UICONTROL Auto-Allocate] activiteiten.
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 7d53adce-cc05-4754-9369-9cc1763a9450
source-git-commit: bd8283d3c0e5fa9e690e377bc4dfbf6a147dd577
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# A4T-rapporten instellen in [!DNL Analysis Workspace] for [!DNL Auto-Allocate] activiteiten

An [!DNL Auto-Allocate] de activiteit identificeert een winnaar onder twee of meer ervaringen en wijst automatisch meer verkeer aan de winnaar toe terwijl de test blijft lopen en leren. De [!UICONTROL Analytics for Target] (A4T) integratie voor [!UICONTROL Auto-Allocate] kunt u uw rapportgegevens weergeven in [!DNL Adobe Analytics]en u kunt zelfs optimaliseren voor aangepaste gebeurtenissen of maateenheden die zijn gedefinieerd in [!DNL Analytics].

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in [!DNL Adobe Analytics] [!DNL Analysis Workspace], enkele wijzigingen in de standaardwaarde **[!UICONTROL Analytics for Target]** het deelvenster moet correct worden geïnterpreteerd [!DNL Auto-Allocate] activiteiten, als gevolg van nuances in [optimalisatiecriteria](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank}.

Deze zelfstudie doorloopt de aanbevolen wijzigingen voor het analyseren [!DNL Auto-Allocate] activiteiten in [!DNL Analysis Workspace]. De belangrijkste concepten zijn:

* [!UICONTROL Visitors] moet altijd worden gebruikt als de normaliserende metrische waarde in [!DNL Auto-Allocate] activiteiten.
* Wanneer de metrische waarde een [!DNL Adobe Analytics] De juiste teller voor de conversiesnelheid is afhankelijk van het type optimalisatiecriteria dat is gekozen tijdens het instellen van de activiteit.
   * Het optimalisatiecriterium voor het optimaliseren van de unieke conversiesnelheid van bezoekers heeft een conversiesnelheid waarvan de teller een telling is van de unieke bezoekers met een positieve waarde van de metrische waarde.
   * De &quot;metrische waarde maximaliseren per bezoeker&quot; heeft een omrekeningskoers waarvan de teller de normale metrische waarde in [!DNL Adobe Analytics]. Dit wordt standaard opgegeven in het gedeelte **[!UICONTROL Analytics for Target]** in [!DNL Analysis Workspace].
* Wanneer uw optimalisatiemetrisch een [!DNL Target] gedefinieerde metrische conversie, standaard **[!UICONTROL Analytics for Target]** in [!DNL Analysis Workspace] handgrepen voor het configureren van het deelvenster.
* Voor alles [!UICONTROL Auto-Allocate] activiteiten die vóór de [!DNL Target Standard/Premium] Release van 23.3.1 (30 maart 2023) [!DNL Analytics Workspace] en [!DNL Target] dezelfde waarde weergeven voor [!UICONTROL Confidence].

   Voor alles [!UICONTROL Auto-Allocate] activiteiten die na 30 maart 2023 zijn gecreëerd, de betrouwbaarheidsintervalwaarden die zijn vastgesteld in [!DNL Analysis Workspace] niet de [conservatievere statistieken gebruikt door [!UICONTROL Auto-Allocate]](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html#section_98388996F0584E15BF3A99C57EEB7629){target=_blank} indien deze activiteiten *beide* van de volgende voorwaarden:

   * [!DNL Analytics] als rapportagebron (A4T)
   * [!DNL Analytics] optimalisatiewaarden

   Indien *beide* Als deze voorwaarden bestaan, moeten de betrouwbaarheidswaarden uit het A4T-deelvenster worden verwijderd. Verwijs in plaats daarvan naar deze waarden in [!DNL Target] rapportage.

## A4T maken voor [!DNL Auto-Allocate] in [!DNL Analysis Workspace]

Een A4T maken voor [!DNL Auto-Allocate] rapport begint met **[!UICONTROL Analytics for Target]** in [!DNL Analysis Workspace], zoals hieronder weergegeven. Maak vervolgens de volgende selecties:

1. **[!UICONTROL Control Experience]**: U kunt elke gewenste ervaring kiezen.
2. **[!UICONTROL Normalizing Metric]**: Selecteer Bezoekers. [!DNL Auto-Allocate] normaliseert altijd de omrekeningskoersen door unieke bezoekers.
3. **[!UICONTROL Success Metrics]**: Selecteer de metrische waarde die u ook hebt gebruikt tijdens het maken van activiteiten. Als dit een [!DNL Target] gedefinieerde metrische conversie, selecteren **Activiteitenconversie**. Anders selecteert u de [!DNL Adobe Analytics] metrisch die u gebruikte.

![[!UICONTROL Analytics for Target] deelvenster instellen voor [!DNL Auto-Allocate] activiteiten.](assets/AAFigure1.png)

*Afbeelding 1: [!UICONTROL Analytics for Target] deelvenster instellen voor [!DNL Auto-Allocate] activiteiten.*

>[!NOTE]
>
> U kunt ook een vooraf gebouwde **[!UICONTROL Analytics for Target]** als u in het rapportscherm op de koppeling klikt [!DNL Adobe Target].

## [!DNL Target] [!UICONTROL Conversion] metriek of [!DNL Analytics] maatstaven met de optimalisatiecriteria voor &quot;Metrische waarde maximaliseren per bezoeker&quot;

De standaardhandgrepen van het A4T-deelvenster [!DNL Auto-Allocate] activiteiten waarin het doel metrisch is [!DNL Target] conversie of [!DNL Analytics] metrisch met optimalisatiecriterium &quot;Maximaliseer de Metrische Waarde per Bezoeker.&quot;

Er wordt één voorbeeld van dit deelvenster weergegeven voor de [!UICONTROL Revenue] metrisch, waarbij &quot;Metrische waarde maximaliseren per bezoeker&quot;als optimalisatiecriteria op het tijdstip van de activiteitenverwezenlijking werd geselecteerd. Zoals eerder vermeld, [!DNL Auto-Allocate] gebruikt conservatievere betrouwbaarheidsberekeningen in vergelijking met de berekeningen in de **[!UICONTROL Analytics for Target]** deelvenster. Adobe raadt u aan om de betrouwbaarheidsmetrische gegevens uit het A4T-deelvenster te verwijderen en de bijbehorende meetgegevens voor de lagere en bovenste lift. Verwijs in plaats daarvan naar deze waarden in [!DNL Target] rapportage.

![[!UICONTROL Analytics for Target - AutoAllocate Report] deelvenster](assets/AAFigure2.png)

*Afbeelding 2: Het aanbevolen rapport voor [!DNL Auto-Allocate] activiteiten met een [!DNL Analytics] criteria voor het optimaliseren van metrische waarden per bezoeker. Voor deze typen metriek en [!DNL Target] gedefinieerde conversiemetriek, standaard **[!UICONTROL Analytics for Target]**in [!DNL Analysis Workspace] kan worden gebruikt.*

## [!DNL Analytics] maatstaven met de optimalisatiecriteria voor de optimalisatiegraad van &quot;Unieke bezoekersconversie maximaliseren&quot;

Wanneer een [!DNL Adobe Analytics] metrisch wordt gebruikt met een optimalisatiecriterium van *Unieke conversiesnelheid bezoeker maximaliseren*, de standaardwaarde **[!UICONTROL Analytics for Target]** in [!DNL Analysis Workspace] moet worden gewijzigd.

De succesmetrische waarde is nu een telling van unieke bezoekers voor wie de omzettingsmetrische waarde positief was. Dit kan worden bereikt door een segment te maken dat filtert om te slagen met een positieve waarde van metrisch. Maak dit segment als volgt:

1. Selecteer **[!UICONTROL Components]** > **[!UICONTROL Create Segment]** in de [!DNL Analysis Workspace] werkbalk.
1. Sleep de metrische waarde die tijdens het maken van de activiteit wordt gebruikt van het linkerdeelvenster naar het deelvenster **[!UICONTROL Definition]** van het segment.
1. Waarden van de metrische waarde selecteren die **groter dan** een numerieke waarde van 0.
1. Van de **[!UICONTROL Include]** vervolgkeuzelijst, selecteert u **[!UICONTROL Visitors]**.
1. Geef uw segment een geschikte naam.

In de onderstaande afbeelding ziet u een voorbeeld van het maken van segmenten. Hier selecteert u [!UICONTROL Visitors With Positive Revenue].

![[!UICONTROL Visitors with Positive Revenue] segment in [!DNL Analysis Workspace]](assets/AAFigure3.png)

*Figuur 3: Segment maken voor [!DNL Adobe Analytics] maatstaven met optimalisatiecriteria die gelijk zijn aan &quot;[!UICONTROL Maximize Unique Visitor Conversion Rate].&quot; In dit voorbeeld is de metrische waarde [!UICONTROL Revenue], en het optimalisatiedoel is het maximaliseren van het aantal bezoekers met positieve inkomsten.*

Nadat het aangewezen segment is gecreeerd, het gebrek  **[!UICONTROL Analytics for Target]** in [!DNL Analysis Workspace] kan worden gewijzigd.

1. Een seconde toevoegen **Unieke bezoekers** metrisch naast de bestaande [!UICONTROL Visitors] metrische kolom.
2. Sleep het nieuwe segment onder de eerste kolom om een deelvenster te maken dat lijkt op Figuur 4. Let op het verschil: het aantal unieke bezoekers met een positief inkomen is een fractie van het totale aantal unieke bezoekers dat aan elke ervaring is toegewezen .

   ![Figuur4.png](assets/AAFigure4.png)

   *Figuur 4: Filteren [!UICONTROL Unique Visitors] door het nieuwe segment*

3. Een omrekeningskoers kan [snel berekend](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html) door zowel de eerste als de tweede kolom te markeren, klikt u met de rechtermuisknop en selecteert u **[!UICONTROL Create Metric from selection]** > **[!UICONTROL Divide]**.

   De standaardconversiesnelheid moet worden verwijderd en vervangen door deze nieuwe berekende maatstaf, zoals in de onderstaande afbeelding wordt getoond. Mogelijk moet u de nieuwe berekende metrische waarde bewerken om als een **[!UICONTROL Format]** > **[!UICONTROL Percent]** tot twee decimalen zoals getoond.

   ![Figuur5.png](assets/AAFigure5.png)

   *Figuur 5: De definitieve [!UICONTROL Auto-Allocate] deelvenster met de conversiekoersen voor een metrisch getal met binaire inkomsten*

## Samenvatting

De stappen in deze zelfstudie toonden aan hoe u de configuratie op de juiste manier kunt configureren [!DNL Analysis Workspace] om weer te geven [!UICONTROL Auto-Allocate] rapportage van gegevens.

Samenvatten:

* Wanneer de metrische waarde een [!DNL Target] gedefinieerde metrische of [!DNL Adobe Analytics] Met het optimalisatiecriterium &#39;Metrische waarde maximaliseren per bezoeker&#39; moet het standaardwerkruimtenet worden gebruikt dat met bezoekers is geconfigureerd als een normalisatiemethode.
* Wanneer de metrische waarde een [!DNL Adobe Analytics] Met het optimalisatiecriterium &#39;De unieke conversiesnelheid van bezoekers maximaliseren&#39; moet u een conversiesnelheid gebruiken die wordt gedefinieerd als de fractie bezoekers voor wie de meting positief is. Dit doet u door een overeenkomstig segment te maken dat de [!UICONTROL Unique Visitor] metrisch.
