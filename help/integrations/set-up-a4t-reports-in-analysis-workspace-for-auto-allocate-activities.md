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
source-git-commit: 8ef61ac0abf008039561bebe7d8d20b84f447487
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 0%

---

# A4T-rapporten instellen in [!DNL Analysis Workspace] for [!DNL Auto-Allocate] activiteiten

An [!DNL Auto-Allocate] activiteit identificeert een winnaar onder twee of meer ervaringen en wijst automatisch uw verkeer aan de winnaar toe terwijl de test blijft lopen en leren. De [!UICONTROL Analytics for Target] (A4T) integratie voor [!UICONTROL Auto-Allocate] stelt u in staat om uw rapportgegevens te bekijken in [!DNL Adobe Analytics]en u kunt zelfs optimaliseren voor aangepaste gebeurtenissen of maateenheden die zijn gedefinieerd in [!DNL Analytics].

Hoewel uitgebreide analysemogelijkheden beschikbaar zijn in [!DNL Adobe Analytics] [!DNL Analysis Workspace], enkele wijzigingen in de standaardwaarde **[!UICONTROL Analytics for Target]** deelvenster kan nodig zijn voor een juiste interpretatie [!DNL Auto-Allocate] activiteiten, vanwege nuances in [optimalisatiemetrische criteria](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank}.

Deze zelfstudie doorloopt de aanbevolen wijzigingen voor het analyseren [!DNL Auto-Allocate] activiteiten in [!DNL Analysis Workspace]. De belangrijkste concepten zijn:

* [!UICONTROL Visitors] moet altijd worden gebruikt als de normaliserende metrische waarde in [!DNL Auto-Allocate] activiteiten.
* Wanneer metrisch een [!DNL Adobe Analytics] De berekening van de conversiesnelheid varieert, afhankelijk van het type optimalisatiecriteria dat tijdens het instellen van de activiteit is gedefinieerd.
   * De conversiesnelheid &quot;maximaliseren van de metrische waarde per bezoeker&quot;: de teller is de normale metrische waarde in [!DNL Adobe Analytics] (dit wordt standaard opgegeven in het dialoogvenster [!UICONTROL Analytics for Target] deelvenster in [!DNL Analysis Workspace]).
      * Dit betekent: maximaliseert het aantal conversies per bezoeker (&quot;tel elke bezoeker&quot;).
      * Voor deze methode is geen extra segment vereist om overeen te stemmen met de in het dialoogvenster [!DNL Target] UI.
   * De conversiesnelheid &quot;unieke bezoekersconversie maximaliseren&quot;: teller is een telling van de unieke bezoekers met een positieve waarde van de metrische waarde.
      * Dit betekent: maximaliseert het aantal bezoekers dat zich omzet (&quot;aantal eenmaal per bezoeker&quot;).
      * Deze methode *DOES* vereisen dat bij de rapportage een extra segment wordt gemaakt dat overeenkomt met de in de [!DNL Target] UI.

* Wanneer uw optimalisatiemetrische waarde een [!DNL Target] gedefinieerde metrische conversie, standaard **[!UICONTROL Analytics for Target]** deelvenster in [!DNL Analysis Workspace] handgrepen voor het configureren van het deelvenster.
* Voor alles [!UICONTROL Auto-Allocate] activiteiten die vóór de [!DNL Target Standard/Premium] Release van 23.3.1 (30 maart 2023) [!DNL Analytics Workspace] en [!DNL Target] dezelfde waarde weergeven voor [!UICONTROL Confidence].

  Voor alles [!UICONTROL Auto-Allocate] activiteiten die na 30 maart 2023 zijn gecreëerd, de betrouwbaarheidsintervalwaarden die zijn vastgesteld in [!DNL Analysis Workspace] niet de [conservatievere statistieken gebruikt door [!UICONTROL Auto-Allocate]](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html#section_98388996F0584E15BF3A99C57EEB7629){target=_blank} indien deze activiteiten *beide* van de volgende voorwaarden:

   * [!DNL Analytics] als rapportagebron (A4T)
   * [!DNL Analytics] optimalisatiewaarden

  De betrouwbaarheidswaarden moeten uit het A4T-deelvenster worden verwijderd. Verwijs in plaats daarvan naar deze waarden in [!DNL Target] rapportage.

## A4T maken voor [!DNL Auto-Allocate] deelvenster in [!DNL Analysis Workspace]

Een A4T-deelvenster maken voor een [!DNL Auto-Allocate] rapport begint met **[!UICONTROL Analytics for Target]** deelvenster in [!DNL Analysis Workspace], zoals hieronder weergegeven. Maak vervolgens de volgende selecties:

1. **[!UICONTROL Control Experience]**: U kunt elke gewenste ervaring kiezen.
1. **[!UICONTROL Normalizing Metric]**: Selecteer Bezoekers (bezoekers worden standaard opgenomen in het deelvenster A4T). [!DNL Auto-Allocate] normaliseert altijd de omrekeningskoersen door unieke bezoekers.
1. **[!UICONTROL Success Metrics]**: Selecteer dezelfde metrische waarde die u tijdens het maken van activiteiten hebt gebruikt. Als dit een [!DNL Target] gedefinieerde metrische conversie, selecteert u **Activiteitenconversie**. Anders selecteert u de [!DNL Adobe Analytics] metrisch die u gebruikte.

![[!UICONTROL Analytics for Target] deelvenster instellen voor [!DNL Auto-Allocate] activiteiten.](assets/AAFigure1.png)

*Afbeelding 1: [!UICONTROL Analytics for Target] deelvenster instellen voor [!DNL Auto-Allocate] activiteiten.*

U kunt ook een vooraf gebouwde **[!UICONTROL Analytics for Target]** als u in het rapportscherm op de koppeling klikt [!DNL Adobe Target].

## [!DNL Target] [!UICONTROL Conversion] metriek of [!DNL Analytics] maatstaven met de optimalisatiecriteria voor &quot;Metrische waarde maximaliseren per bezoeker&quot;

Wanneer het doel metrisch of is:

* Metrisch voor doelconversie
* Analysemetrisch met het optimalisatiecriterium &quot;Maximize Metric Value per Visitor&quot;

Het standaardA4T paneel vormt automatisch het rapport.

Er wordt één voorbeeld van dit deelvenster weergegeven voor de [!UICONTROL Revenue] metrisch, waarbij &quot;Metrische waarde maximaliseren per bezoeker&quot;als optimalisatiecriteria op het tijdstip van de activiteitenverwezenlijking werd geselecteerd. Zoals eerder vermeld, [!DNL Auto-Allocate] gebruikt conservatievere betrouwbaarheidsberekeningen in vergelijking met de berekeningen in de **[!UICONTROL Analytics for Target]** deelvenster. Adobe raadt u aan om de betrouwbaarheidsmetrische gegevens uit het A4T-deelvenster te verwijderen en de bijbehorende meetgegevens voor de lagere en bovenste lift. Verwijs in plaats daarvan naar de betrouwbaarheidswaarden in [!DNL Target] rapportage.

>[!NOTE]
>
>Vertrouwenswaarden in A4T-rapportage zijn minder conservatief dan [!DNL Target] melden en voortijdig een winnaar aangeven voor een [!UICONTROL Auto-Allocate] activiteit.


![[!UICONTROL Analytics for Target - AutoAllocate Report] deelvenster](assets/AAFigure2.png)

*Afbeelding 2: Het aanbevolen rapport voor [!DNL Auto-Allocate] activiteiten met [!DNL Analytics] criteria voor het optimaliseren van metrische waarden per bezoeker. Voor deze typen metriek, en [!DNL Target] gedefinieerde conversiemetriek, standaard **[!UICONTROL Analytics for Target]**deelvenster in [!DNL Analysis Workspace] kan worden gebruikt.*

## [!DNL Analytics] maatstaven met de optimalisatiecriteria voor de optimalisatiegraad van &quot;Unieke bezoekersconversie maximaliseren&quot;

Het optimalisatiecriterium &quot;Unieke bezoekerconversiesnelheid maximaliseren&quot; verwijst naar het aantal bezoekers voor wie de metrische waarde positief is. Als de conversiekoers bijvoorbeeld als inkomsten wordt gedefinieerd, zou het criterium &quot;Unieke bezoekersconversiesnelheid maximaliseren&quot; optimaliseren voor het aantal unieke bezoekers voor wie de inkomsten groter waren dan 0. Met andere woorden, dit criterium zou het maximaliseren van het aantal bezoekers dat inkomsten genereert, in plaats van de waarde van de inkomsten zelf.

>[!NOTE]
>
>Conversiesnelheid waarnaar hier wordt verwezen, kan verwijzen naar handelingen buiten bestellingen, zoals klikken, afbeeldingen enzovoort. In deze gevallen zou het criterium nog steeds het maximaliseren zijn van het aantal bezoekers dat klikt of de pagina bekijkt.

De [!DNL Analytics for Target] deelvenster in [!DNL Analysis Workspace] moet worden gewijzigd als dit optimalisatiecriterium wordt gebruikt met een [!DNL Adobe Analytics] metrisch.

Wanneer dit optimalisatiecriterium wordt gebruikt, is succesmetrisch een telling van unieke bezoekers voor wie omzettings metrisch positief was. Daarom moet om deze waarde te bekijken, een nieuw segment worden gecreeerd dat filters om met een positieve waarde voor metrisch te raken.

Maak dit segment als volgt:

1. Selecteer de **[!UICONTROL Components]** > **[!UICONTROL Create Segment]** in de [!DNL Analysis Workspace] werkbalk.
1. Sleep de metrische waarde die tijdens het maken van de activiteit wordt gebruikt van het linkerdeelvenster naar het deelvenster **[!UICONTROL Definition]** van het segment.
1. Waarden van de metrische waarde selecteren die **groter dan** een numerieke waarde van 0.
1. Van de **[!UICONTROL Include]** vervolgkeuzelijst, selecteert u **[!UICONTROL Visitors]**.
1. Geef uw segment een geschikte naam.

Een voorbeeld van de segmentverwezenlijking wordt getoond in het hieronder cijfer, waar succesmetrisch is [!UICONTROL Visitors With Positive Revenue].

![[!UICONTROL Visitors with Positive Revenue] segment in [!DNL Analysis Workspace]](assets/AAFigure3.png)

*Afbeelding 3: Segment maken voor [!DNL Adobe Analytics] maatstaven met optimalisatiecriteria die gelijk zijn aan &quot;[!UICONTROL Maximize Unique Visitor Conversion Rate].&quot; In dit voorbeeld is de metrische waarde [!UICONTROL Revenue], en het optimalisatiedoel is het maximaliseren van het aantal bezoekers met positieve inkomsten.*

Nadat het aangewezen segment is gecreeerd, kunt u het gebrek wijzigen  **[!UICONTROL Analytics for Target]** deelvenster in [!DNL Analysis Workspace] om de waarden voor het optimalisatiecriterium weer te geven. Dit wordt bereikt door het volgende te doen:

1. Een seconde toevoegen **Unieke bezoekers** metrisch naast de bestaande [!UICONTROL Visitors] metrische kolom.
2. Sleep het nieuwe segment onder de eerste kolom om een deelvenster te maken dat lijkt op Figuur 4. Let op het verschil in waarden van de kolommen: het aantal unieke bezoekers met positieve inkomsten moet een fractie zijn van het totale aantal unieke bezoekers dat aan elke ervaring is toegewezen (zoals hieronder wordt getoond).

   ![Figuur4.png](assets/AAFigure4.png)

   *Figuur 4: Filteren [!UICONTROL Unique Visitors] door het nieuwe segment*

3. Een omrekeningskoers kan [snel berekend](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html) door zowel de eerste als de tweede kolom te markeren, klikt u met de rechtermuisknop en selecteert u **[!UICONTROL Create Metric from selection]** > **[!UICONTROL Divide]**.

   De standaardconversiesnelheid moet worden verwijderd en vervangen door deze nieuwe berekende maatstaf, zoals in de onderstaande afbeelding wordt getoond. Mogelijk moet u de nieuwe berekende metrische waarde bewerken om als een **[!UICONTROL Format]** > **[!UICONTROL Percent]** tot twee decimalen zoals getoond.

   ![Figuur5.png](assets/AAFigure5.png)

   *Figuur 5: De definitieve [!UICONTROL Auto-Allocate] deelvenster met de conversiekoersen voor een metrisch getal met binaire inkomsten*

## Samenvatting

De stappen in deze zelfstudie toonden aan hoe u de configuratie op de juiste manier kunt configureren [!DNL Analysis Workspace] op weergave [!UICONTROL Auto-Allocate] rapportage van gegevens.

Samenvatten:

* Wanneer de metrische waarde een [!DNL Target] gedefinieerde metrische of [!DNL Adobe Analytics] Met het optimalisatiecriterium &#39;Metrische waarde maximaliseren per bezoeker&#39; moet het standaardwerkruimtenet worden gebruikt dat met bezoekers is geconfigureerd als een normalisatiemethode.
* Wanneer metrisch een [!DNL Adobe Analytics] Metrisch met optimalisatiecriterium &quot;Maximize Unique Visitor Conversion Rate,&quot;u moet de fractie van bezoekers met positieve metrische waarde over totale bezoekers bepalen. Dit doet u door een overeenkomstig segment te maken dat de [!UICONTROL Unique Visitor] op die metrische waarde.
