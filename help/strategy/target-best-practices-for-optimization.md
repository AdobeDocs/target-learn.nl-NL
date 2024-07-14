---
title: Aanbevolen werkwijzen voor optimalisatie
description: Leer de zes basisprincipes van de Adobe van optimalisering en hoe u ze toepast.
solution: Target
role: Leader, Architect, Developer, Admin
feature: Overview
level: Beginner
exl-id: dd29faea-bb67-4128-b261-fa407ba7158c
source-git-commit: 20bd1eb17ef6e287f7b76e14f727456e12d6f115
workflow-type: tm+mt
source-wordcount: '1244'
ht-degree: 0%

---

# Aanbevolen procedures voor optimalisatie met Adobe Target

Leer de zes basisprincipes van de Adobe van optimalisering en hoe u ze toepast.

Als het gaat om het opbouwen van een sterke digitale aanwezigheid, zijn er een aantal uitdagingen waarvoor uw team zal staan. Niet alleen bent u belast met het in dienst nemen van honderden, zelfs duizenden klanten, bovenop dat, tonen uw klanten een verscheidenheid van uniek gedrag en voorkeur die in tijd zullen veranderen en het is aan u om niet alleen die veranderingen bij te houden, maar hen te voorzien en uw strategieën efficiënt en nauwkeurig uit te voeren. Het is een race tegen concurrenten in een onbepaalde inhoudsmarathon, die constante herhaling en best-in-class technologie vereist.

Een oplossing voor deze veelzijdige uitdaging is optimalisatie met Adobe Target, dat ervoor zorgt dat u een evoluerende digitale aanwezigheid hebt die relevant, waardevol en vrij van wrijving is. De technische architectuur en de kanalen waarin u [!DNL Target] implementeert, verschillen aanzienlijk per klant. Wij hebben echter een lijst met best practices en optimalisatiestrategieën opgesteld die elk team kan gebruiken om de volledige mogelijkheden van dit krachtige hulpmiddel te benutten.

## Optimalisatie begrijpen

Optimalisatie wordt gedefinieerd als &quot;het optimaal of het doeltreffendst gebruiken van een situatie of bron&quot;. Het is de meest efficiënte manier om ervoor te zorgen dat u over kwalitatieve gegevens beschikt die aantonen dat de veranderingen die u aanbrengt waardevol zijn. Om echt te optimaliseren, moet u de impact en de waarde van uw inspanningen kunnen meten. Anders zullen de wijzigingen die u aanbrengt, hogere kosten met zich brengen, met een minimale toename. Om dit effectief en efficiënt te bereiken, moet u beginnen met strategische planning. Zonder een strategisch plan in uw optimalisering op te nemen, zou u simpelweg raden.

### Zes essentiële onderdelen van optimalisatie

1. **Strategize**: Identificeer kansen voor activiteiten die met bedrijfsdoelstellingen worden gericht en die op gegevens gebaseerd zijn.
1. **Prioritize**: Rang en planningsactiviteiten die op bedrijfsgroepering, niveau van inspanning en potentiële invloed worden gebaseerd.
1. **Ontwerp**: Creeer definitieve beelden van activiteitenervaringen en ontwikkelt activiteitenplannen met gedetailleerde criteria.
1. **bouwt en in werking stelt**: Ontwikkel activiteit met inbegrip van [!DNL Target] opstelling, codeontwikkeling, en het testen QA.
1. **Analyseer**: Begin [!DNL Target] activiteit aan productie en monitorprestaties voor de duur van de activiteit.
1. **Akte en herhaling**: Ontwikkel aanbevelingen die op test of de prestaties van de verpersoonlijkingsactiviteit worden gebaseerd.

Het weten dat de verandering een constante is, zou onze optimaliseringsstrategie een herhalende uitvoeringscyclus moeten zijn om aan de voortdurend veranderende behoeften van uw klanten te voldoen (zie Figuur 1 hieronder).

![ Optimalisering &amp; verpersoonlijking ](assets/optimize-and-personalize.png)

_Figuur 1 - de Interactieve Cyclus van de optimalisering_

## Een optimalisatiestrategie ontwikkelen

Het ontwikkelen van een optimalisatiestrategie kan worden opgesplitst in: (1) Een testactiviteitenplan opstellen en (2) Basisprincipes van optimalisatie begrijpen.

1: Het testactiviteitenplan moet worden gedocumenteerd. Dit zorgt ervoor dat u een minimale kwaliteitsnorm hebt wanneer het over uw toepassing van de testactiviteit komt. Uw testactiviteitenplan moet het volgende bevatten:

* **Naam &amp; Beschrijving:** Intuïtieve activiteitennaam en beschrijving van wat het experiment op wordt geconcentreerd. &quot;Hoe? Wat? Wanneer? Waar? Waarom?&quot;

* **Doel:** Doel van de activiteit en het gerichte bedrijfsdoel het wordt ontworpen om te beïnvloeden.

* **Samenvatting:** Een hypothese is een voorspelling u voorafgaand aan het runnen van een experiment creeert. Het geeft duidelijk aan wat wordt getest, wat volgens jou het resultaat zal zijn en waarom je denkt dat dat het geval is. Door het experiment uit te voeren zal je hypothese blijken of verwerpen.

Een volledige hypothese bestaat uit drie delen:

* Als _veranderlijk_
* Dan _resultaat_
* Omdat _rationale_

* **Plaats:** URL, paginasectie, en apparatentype.
* **Grijs Metrisch van het Goal:** Hoe zal succes worden gemeten?
* **Secundaire Metriek:** Andere waardevolle zeer belangrijke prestatiesindicatoren (KPIs) om met het doel van verder begrip effect &amp; plannende herhalingen te evalueren.
* **Publiek van de Activiteit:** Beschrijving van vereiste het filtreren van de testblootstelling.
* **Meldend Soorten publiek:** Lijst van beschrijvingen van bezoekersondergroepen die voor analyse moeten worden gebruikt.
* **Begeleidingen van de Ervaring:** Mockups, voorbeelden draadframes, en beschrijvingen.

**Algemene Nota:** Om het even welk element van een webpage die bedrijfswaarde kan drijven of waardevol inzicht in bezoekersgedrag kan worden getest. Enkele gangbare soorten testactiviteiten zijn:

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

2: De tweede fase van de strategie bestaat uit het begrijpen van de basisbeginselen van optimalisatie, waaronder het begrijpen van de testelementen zelf. De testelementen van Optimalisering omvatten:

     A. De Waarde van het element 
    
     dit wordt bereikt door een stap terug te nemen om te vragen, waarom een bepaald element op uw plaats bestaat, en dient de inhoud een specifiek doel? Deze vragen zijn een goede plek om te beginnen als uw site net een nieuw ontwerp heeft voltooid of als er onlangs een nieuwe functie is geïntroduceerd. De tactiek die wordt gebruikt om elementwaarde te bepalen wordt bedoeld als het Testen van de Opname/van de Uitsluiting. Met de functie voor insluiten/uitsluiten kunt u de waarde op de pagina waarop het element wordt weergegeven goed lezen.
    
     B. De Presentatie van het element 
    
     dit is waar u over de algemene blik en het gevoel van het element zou denken en hoe dat de algemene paginapresentatie beïnvloedt. De tactiek die voor een presentatie wordt gebruikt, is het focussen op het aanbrengen van onbelangrijke wijzigingen in de inhoud en de elementenpagina.
    
     C. De Functie van het element 
    
     hier vragen wij, doet het element op de pagina wat het wordt verondersteld te doen? Is de interactie succesvol en werkt zoals bedoeld? Is de interactie natuurlijk, of een wrijvingspunt? De tactiek die voor functie wordt gebruikt is ervaringen te bouwen die op makkelijk te gebruiken functionaliteit zonder extra kosteneffect worden geconcentreerd.

## Optimalisatie versus personalisatie

Nu we de onderdelen van de strategie hebben geanalyseerd en opgesomd, is het belangrijk een onderscheid te maken tussen optimalisatie-inspanningen en Personalization-inspanningen. Optimalisatie is het optimaal of het doeltreffendst gebruiken van een situatie of bron, terwijl Personalization het ontwerpen of produceren van iets is om aan iemands individuele behoeften te voldoen.

Op hoog niveau:

* Optimalisatie is gericht op testen om te bepalen wat het meest efficiënt en het best presteert voor ALLE gebruikers die met uw digitale aanwezigheid werken.
* Personalization is bezig met testen om te bepalen wat het meest efficiënt en het best presteert voor SOMMIGE van hen die met uw digitale aanwezigheid communiceren.

Wanneer u de nadruk legt op optimalisatie, zijn de meest voorkomende testactiviteiten:

* **het testen A/B:** Echt - tijd het testen van twee of meer pagina&#39;s of paginaelementen tegen elkaar om kwantitatief inzicht in klantenvoorkeur te verkrijgen.
* **Multivariate het testen:** Vergelijkend combinaties aanbiedingen onder elementen op een pagina om te zien welke combinatie het beste presteert. Bovendien zal de multivariate test identificeren welk element van de pagina beste omzettingen verbetert.

Wanneer u zich richt op Personalization, zult u waarschijnlijk dezelfde testactiviteiten zien als in Optimalisatie, maar ze zijn gericht op een meer specifiek publiek. Als u bijvoorbeeld een A/B-test uitvoert, kunt u waarschijnlijk pagina&#39;s en publiek toevoegen binnen de ervaringen om uw Personalization te bevorderen.

Personalization bevat ook het type Experience Targeting-testactiviteit, dat inhoud levert aan specifieke doelgroepen op basis van een reeks gedefinieerde regels en criteria. Wanneer u groeit en verdiept in Personalization, kunt u op deze manier ook een aantal van de premiumfuncties van Target benutten, zoals:

* Type Automated Personalization-activiteiten
* Type adviesactiviteiten

## Optimalisatie vóór personalisatie

Op basis van het bovenstaande raadt de Adobe u aan te optimaliseren voordat u de afbeelding personaliseert en Personalization van breed naar korrelig te verplaatsen. Om de Activiteiten van Personalization van brein tot korrelig te rijpen, zult u beginnen een één-aan-vele (brede) verpersoonlijkings (het gebruiken van A/B het testen), dan beweging in één-aan-één verpersoonlijkings (korrelige) stijl (het gebruiken van de Geautomatiseerde verpersoonlijkingsactiviteiten).

Voor meer informatie, te luisteren gelieve aan [ webinar over het begrijpen van en het optimaliseren van uw implementatie van Adobe Target ](https://adobecustomersuccess.adobeconnect.com/pkfafpzd9yarmp4/), met Bedrijfs Consultant, Katie Cozby.

Leer meer over strategie en gedachte leiderschap bij de [ hub van het Succes van de Klant ](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html).
