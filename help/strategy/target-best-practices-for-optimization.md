---
title: Aanbevolen procedures voor optimalisatie
description: 'Leer zes essentiële Adobe om ze toe te passen. '
solution: Target
source-git-commit: fd679d3fc2c72b9852d8129adf8c1187bf22b25f
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---

# Aanbevolen procedures voor optimalisatie met Adobe Target

Leer zes essentiële Adobe om ze toe te passen.

Als het gaat om het opbouwen van een sterke digitale aanwezigheid, zijn er een aantal uitdagingen waarvoor uw team zal staan. Niet alleen bent u belast met het in dienst nemen van honderden, zelfs duizenden klanten, bovenop dat, tonen uw klanten een verscheidenheid van uniek gedrag en voorkeur die in tijd zullen veranderen en het is aan u om niet alleen die veranderingen bij te houden, maar hen te voorzien en uw strategieën efficiënt en nauwkeurig uit te voeren. Het is een race tegen concurrenten in een onbepaalde inhoudsmarathon, die constante herhaling en best-in-class technologie vereist.

Een oplossing voor deze veelzijdige uitdaging is optimalisatie met Adobe Target, dat ervoor zorgt dat u een evoluerende digitale aanwezigheid hebt die relevant, waardevol en vrij van wrijving is. De technische architectuur en de kanalen waarin u opstelt [!DNL Target] We hebben echter een lijst met best practices en optimalisatiestrategieën opgesteld die elk team kan gebruiken om de volledige mogelijkheden van dit krachtige hulpmiddel te benutten.

## Optimalisatie begrijpen

Optimalisatie wordt gedefinieerd als &quot;het optimaal of het doeltreffendst gebruiken van een situatie of bron&quot;. Het is de meest efficiënte manier om ervoor te zorgen dat u over kwalitatieve gegevens beschikt die aantonen dat de veranderingen die u aanbrengt waardevol zijn. Om echt te optimaliseren, moet u de impact en de waarde van uw inspanningen kunnen meten. Anders zullen de wijzigingen die u aanbrengt, hogere kosten met zich brengen, met een minimale toename. Om dit effectief en efficiënt te bereiken, moet u beginnen met strategische planning. Zonder een strategisch plan in uw optimalisering op te nemen, zou u simpelweg raden.

### Zes essentiële onderdelen van optimalisatie

1. **Strategiseren**: Identificeer kansen voor activiteiten die met bedrijfsdoelstellingen worden gericht en die op gegevens gebaseerd zijn.
1. **Prioriteit**: Rank- en planningsactiviteiten op basis van de afstemming van het bedrijf, het inspanningsniveau en het potentiële effect.
1. **Ontwerp**: Voltooide visuals van activiteitenervaringen maken en activiteitenplannen met gedetailleerde criteria ontwikkelen.
1. **Samenstellen en uitvoeren**: Ontwikkel activiteit met inbegrip van [!DNL Target] opstelling, codeontwikkeling, en het testen QA.
1. **Analyseren**: Starten [!DNL Target] activiteiten voor de productie en de monitoring van de prestaties gedurende de activiteiten.
1. **Handelen en herhalen**: Ontwikkelen van aanbevelingen op basis van prestatie van test- of personalisatieactiviteit.

Het weten dat de verandering een constante is, zou onze optimaliseringsstrategie een herhalende uitvoeringscyclus moeten zijn om aan de voortdurend veranderende behoeften van uw klanten te voldoen (zie Figuur 1 hieronder).

![Optimalisatie en personalisatie](assets/optimize-and-personalize.png)

_Afbeelding 1 - Interactieve optimalisatiecyclus_

## Een optimalisatiestrategie ontwikkelen

Het proces voor de ontwikkeling van een optimalisatiestrategie kan worden onderverdeeld in: (1) Een testactiviteitenplan maken en (2) de basisbeginselen van optimalisatie begrijpen.

1: Het testactiviteitenplan moet worden gedocumenteerd. Dit zorgt ervoor dat u een minimale kwaliteitsnorm hebt wanneer het over uw toepassing van de testactiviteit komt. Uw testactiviteitenplan moet het volgende bevatten:

* **Naam en beschrijving:** Intuïtieve activiteitnaam en beschrijving van waar het experiment op is gericht. &quot;Hoe? Wat? Wanneer? Waar? Waarom?&quot;

* **Doel:** Doel van de activiteit en het gerichte bedrijfsdoel dat het wordt ontworpen om effect te sorteren.

* **Hypothese:** Een hypothese is een voorspelling die u maakt voordat u een experiment uitvoert. Het geeft duidelijk aan wat wordt getest, wat volgens jou het resultaat zal zijn en waarom je denkt dat dat het geval is. Door het experiment uit te voeren zal je hypothese blijken of verwerpen.

Een volledige hypothese bestaat uit drie delen:

* Indien _variabele_
* Vervolgens _resultaat_
* Omdat _motivering_

* **Locatie:** URL, paginasectie en apparaattype.
* **Metrisch doel:** Hoe wordt het succes gemeten?
* **Secundaire cijfers:** Andere waardevolle prestatiekernindicatoren (KPI&#39;s) die moeten worden geëvalueerd met het oog op een beter begrip van de impact- en planningiteraties.
* **Activiteit publiek:** Beschrijving van de vereiste filters voor blootstelling van de test.
* **Publiek rapporteren:** Lijst met beschrijvingen van subsets van bezoekers die voor analyse moeten worden gebruikt.
* **Ervaring concepten:** Mockups, voorbeelden, draadframes en beschrijvingen.

**Algemene opmerking:** Om het even welk element van een webpagina die bedrijfswaarde of waardevol inzicht in bezoekersgedrag kan drijven kan worden getest. Enkele gangbare soorten testactiviteiten zijn:

* Koptekst
* Inhoudstekst
* Knoptekst
* Pagina-indeling
* Fotografie
* Knopkleur
* Element-indeling
* Verwijdering en toevoeging van elementen
* Navigatievolgorde
* Navigatie taxonomie
* Zoeken naar accenten

2: De tweede fase van de strategie is het begrijpen van de basisbeginselen van optimalisatie, die het begrip van testelementen zelf omvat. De testelementen van Optimalisering omvatten:

    A. Waarde element
    
    Dit wordt bereikt door een stap terug te nemen om te vragen, waarom een bepaald element op uw plaats bestaat, en dient de inhoud een specifiek doel? Deze vragen zijn een goede plaats om te beginnen als uw site net een nieuw ontwerp heeft voltooid of als er onlangs een nieuwe functie is geïntroduceerd. De tactiek die wordt gebruikt om elementwaarde te bepalen wordt bedoeld als het Testen van de Opname/van de Uitsluiting. Met de functie voor insluiten/uitsluiten kunt u de waarde op de pagina waarop het element wordt weergegeven goed lezen.
    
    B. Elementpresentatie
    
    Dit is waar u over de algemene blik en het gevoel van het element zou denken en hoe dat de algemene paginapresentatie beïnvloedt. De tactiek die voor een presentatie wordt gebruikt, is het focussen op het aanbrengen van onbelangrijke wijzigingen in de inhoud en de elementenpagina.
    
    C. Elementfunctie
    
    Hier vragen we ons af of het element op de pagina doet wat het geacht wordt te doen. Is de interactie succesvol en werkt zoals bedoeld? Is de interactie natuurlijk, of een wrijvingspunt? De tactiek die voor functie wordt gebruikt is ervaringen te bouwen die op makkelijk te gebruiken functionaliteit zonder extra kosteneffect worden geconcentreerd.

## Optimalisatie versus personalisatie

Nu we de onderdelen van de strategie hebben geanalyseerd en opgesomd, is het belangrijk een onderscheid te maken tussen optimalisatie-inspanningen en inspanningen op het gebied van personalisatie. Optimalisatie is het optimaal of het doeltreffendst gebruiken van een situatie of bron, terwijl personalisatie het ontwerpen of produceren van iets is om aan iemands individuele vereisten te voldoen.

Op hoog niveau:

* Optimalisatie is gericht op testen om te bepalen wat het meest efficiënt en het best presteert voor ALLE gebruikers die met uw digitale aanwezigheid werken.
* Personalisatie is een test om te bepalen wat het meest efficiënt en het best presteert voor SOMMIGE van hen die met uw digitale aanwezigheid in wisselwerking staan.

Wanneer u de nadruk legt op optimalisatie, zijn de meest voorkomende testactiviteiten:

* **A/B-tests:** In real time testen van twee of meer pagina&#39;s of pagina-elementen tegen elkaar om kwantitatief inzicht in klantenvoorkeur te krijgen.
* **Meervoudige tests:** Combinaties van aanbiedingen vergelijken tussen elementen op een pagina om te zien welke combinatie het beste presteert. Bovendien zal de multivariate test identificeren welk element van de pagina beste omzettingen verbetert.

Wanneer u zich richt op Personalisatie, zult u waarschijnlijk dezelfde testactiviteiten zien als in Optimalisering, maar zij zijn gericht op specifiekere doelgroepen. Bij A/B-tests voegt u waarschijnlijk pagina&#39;s en publiek toe binnen de ervaringen om uw persoonlijke voorkeur te bevorderen.

Personalisatie omvat ook de ervaring die het type van testactiviteit richt, dat inhoud aan specifiek publiek levert dat op een reeks bepaalde regels en criteria wordt gebaseerd. Wanneer u aan Personalisatie begint te groeien en te verdiepen, zult u ook een aantal van de belangrijkste functies van Target benutten, zoals:

* Type Automated Personalization-activiteiten
* Type adviesactiviteiten

## Optimalisatie vóór personalisatie

Gezien het bovenstaande, adviseert Adobe dat u optimaliseert alvorens u, en vooruitgaat Personalisatie van breed aan korrelig aanpast. Om de Activiteiten van de Personalisatie van breed tot korrelig te rijpen, zult u beginnen gebruikend een één-aan-vele (brede) verpersoonlijkings (het gebruiken van A/B het testen), dan beweging in één-aan-één verpersoonlijkings (korrelige) stijl (het gebruiken van Geautomatiseerde verpersoonlijkingsactiviteiten).

Ga voor meer informatie naar [webinar over het begrijpen en optimaliseren van uw Adobe Target-implementatie](https://adobecustomersuccess.adobeconnect.com/pkfafpzd9yarmp4/), met Business Consultant, Katie Cozby.
