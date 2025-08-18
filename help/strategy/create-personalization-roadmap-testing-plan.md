---
title: QuickStart voor personalisatie testen en routekaart maken
description: Leer een framework dat u kunt gebruiken om uw personalisatieactiviteiten te valideren en een routekaart voor personalisatie te maken die via Adobe Target en Adobe Analytics kan worden uitgevoerd.
solution: Target,Analytics
level: Intermediate
role: Leader, Architect, Developer, Admin
exl-id: c0b6f9a0-7074-4e25-81e6-9781a54e2156
source-git-commit: 20bd1eb17ef6e287f7b76e14f727456e12d6f115
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 0%

---

# QuickStart voor personalisatie testen en routekaart maken

Personalization kan krachtig zijn, maar moet worden gevalideerd door te testen om te kunnen garanderen dat het echt waarde heeft. Testen is de meest effectieve strategie om te bepalen wie, hoe en wat u moet personaliseren.

In het tweede decennium van de 21ste eeuw beginnen organisaties als u met verouderde consumentengerichte strategieën en onjuiste gegevensanalyse. Dit is het tijdperk van personalisering, een tijdperk waarin de consumenten niets minder dan een aangepaste ervaring hebben verwacht. Personalization op bedrijfsniveau is een complex en voortdurend veranderend proces, maar wanneer het effectief wordt gedaan zal het klantentevredenheid maximaliseren en beduidend ROI verhogen.

Het volgende artikel biedt een framework dat u kunt gebruiken voor het valideren van verpersoonlijkingsactiviteiten en het maken van een routekaart voor verpersoonlijking die via Adobe Target en Adobe Analytics kan worden uitgevoerd. Het Adobe QuickStart-framework omvat:

1. **identificeer verpersoonlijkingskansen** - de analyse van hefboomgegevens om kansen te identificeren om zeer belangrijke prestatiesindicatoren op uw plaats, gebonden aan de bedrijfsdoelstellingen van uw organisatie te beïnvloeden.

1. **ontwikkelt gebruiksgevallen** - bepaal doelstellingen van uw verpersoonlijkingsactiviteit met specifieke bezoekersattributen in mening, ben uitdrukkelijk betreffende hoe de gekrulde inhoud de ervaring van de bezoeker zal verbeteren, vooraf bepaalt welk succes zal kijken als en welke acties van de testlessen kunnen worden genomen.

1. **creeer een roadmap** - aggregeer een lijst en geef voorrang aan de gevallen van het verpersoonlijkingsgebruik, zorg ervoor dat uw inspanningen op hoogwaardige activiteiten worden geconcentreerd; verwacht om gebruiksgevallen en roadmap te verfijnen en te herzien die op lessen worden gebaseerd.

1. **Ontwerp en voer** uit - bouw en lanceer de activiteiten van Adobe Target om gekromde inhoud voor uw prioritaire publiek te leveren.

1. **neem actie op resultaten** - analyseer activiteitenprestaties en vat activiteitenresultaten, inzichten, aanbevelingen, en volgende stappen samen.

## Stap 1: Identificeer verpersoonlijkingsmogelijkheden{#personalization}

Dit is het beginpunt waar u begint met het vormen van de Personalization-routekaart. Wanneer het runnen van een succesvol verpersoonlijkingsprogramma, is het essentieel om zich op uw belangrijkste bedrijfsdoelstellingen en belangrijkste prestatiesindicatoren te concentreren. De inspanningen van Personalization moeten dienovereenkomstig worden afgestemd om waarde te bieden. Paul Morris, Adobe Business Consultant, zegt: &quot;Als alles wat je doet deze doelen bereikt, is het zeer waarschijnlijk dat jouw programma een belangrijke rol zal spelen. Als u echter een verstrooide aanpak voor het testen hebt, zult u waarschijnlijk wat wins vinden, maar uw algemene programma zal bijna niet zo succesvol zijn.&quot;

>[!NOTE]
>
>Als u niet onmiddellijk weet wat uw belangrijkste bedrijfsdoelstellingen zijn, is het belangrijk om hen zo spoedig mogelijk te identificeren. Zorg ervoor dat:


* Stel de afstemming tussen uw bedrijfsdoelstellingen en uw haalbare hypothese tot stand. Dit zal u toelaten om aan gebruiksgevallen voorrang te geven die de grootste waarde aan uw zaken leveren.

* Uw doelstellingen meetbaar maken voor traceringsdoeleinden en correleren met impact op de omzet.

* Richt elke kans één enkel doel metrisch zou moeten beïnvloeden.

Soms heb je doelen die aanvankelijk ook ontastbaar lijken, zoals merkwaarde of loyaliteit. Het is van cruciaal belang dat je deze kunt meten om ze te gebruiken als doelmaatstaf voor Personalization-activiteiten. Typisch, kunnen deze types van doelstellingen nog worden gericht aan opbrengsteffect zoals levenswaarde van de levensklant of acquisitiekosten.Aangezien u vooruitgaat, zeker ben om programmaprestaties tegen uw belangrijkste bedrijfsdoelstellingen periodiek te herzien in het verzekeren van waarde van uw programma van Personalization wordt gedreven.

Focus gegevensanalyse om specifieke gebieden van uw website te identificeren die kunnen worden verbeterd. Adobe raadt aan om Adobe Analytics te starten om gevallen van doelgericht gebruik te genereren. Als u een Analyseteam op zijn plaats hebt, vraag hen om het volgende te bekijken:

1. Persoonlijke preform lijsten - een ideatieeigenschap die onbeperkte onderbrekingen verstrekt en u kan helpen om het even welke vragen of veronderstellingen beantwoorden die u kunt hebben.
1. Geavanceerde segmentatie - Met IQ voor segmentatie kunt u bezoekers in verschillende gedeelten van uw site vergelijken.
1. Juristische revisies - Bepaal welke delen van uw site het meest profiteren van Personalization. Met deze revisies kunt u een stap terug doen en door uw site lopen zoals een klant zou doen.
1. De analyse van de concurrent - de Kansen zijn, andere ondernemingen staan voor de zelfde uitdagingen die u doet. Deze analyse is niet beperkt tot ondernemingen in dezelfde bedrijfstak.

Het doel van deze stap is een actioneerbare insight te genereren in de vorm van een hypothese. Een hypothese is een voorspelling die u maakt voordat u een experiment uitvoert. Het geeft duidelijk aan wat er wordt veranderd, wat je denkt dat het resultaat zal zijn en waarom je denkt dat dat het geval is. Door het experiment uit te voeren zal je hypothese blijken of verwerpen. Aan het eind van deze stap, zou u een reeks hypothesen voor verpersoonlijkingskansen moeten hebben die uw website en bezoekerstevredenheid zullen verbeteren.

## Stap 2: Gebruiksscenario&#39;s ontwikkelen{#use-cases}

Begin met de hypothesen die in Stap 1 worden geproduceerd, dan ontwikkel uw activiteiten rond hen. Nu kunt u de pre-vormlijsten ontwikkelen die in Stap 1A worden gecreeerd; elk van KPIs heeft een reeks hypotheses, die dan individuele tests binnen Adobe Target worden. Als u moeite hebt om dit punt te bereiken, begint u zo eenvoudig mogelijk, bijvoorbeeld met de aandacht voor de retourbezoekers die uw site frequent gebruiken. Denk na over de manieren u uw homepage aan uw terugkerende bezoekers kunt aanpassen. Als u eenmaal een aantal hypothesen hebt, moet u elke activiteit definiëren om daadwerkelijk voorrang te geven aan elk geval van gebruik.

1. Bepaal het prioritaire publiek dat u gepersonaliseerde inhoud aan wilt dienen, bedachtend van de unieke bezoekersattributen die bepalen wie zij zijn en wat zij (b.v., bestaande klant versus vooruitgangsklant) de wil en de behoeften van het prioritaire publiek zouden met uw bedrijfsdoelstellingen moeten richten

1. Identificeer de specifieke plaats in de reis van de bezoeker waar de gepersonaliseerde inhoud het meest impactful zal zijn. Focus op pagina&#39;s waarop u bezoekers van verschillende personen of bezoekers met verschillende behoeften/intenties zou verwachten.

1. Begin wat ontwerpwerk van uw variant te plannen. De inhoud moet zorgvuldig worden geobserveerd met de specifieke behoeften van het publiek en wil in gedachten houden, rekening houdend met de plaats waar zij zich op reis bevinden. De juiste inhoud moet verschillend en gedifferentieerd zijn.

## Stap 3: Creeer een roadmap, aggregeer en geef voorrang aan gebruiksgevallen

Samenvoegen een uitvoerige lijst van verpersoonlijkingskansen die bij een minimum de plaats, het idee, en de prioriteit van de verpersoonlijkingsactiviteiten vangen.

De Prioritiseringsstap wordt opgesplitst in twee factoren:

**Waarde:** Gebruikt het industriesonderzoek, benchmarking, en gelijkaardige gebruiksgevallen van het verleden om de verwachte waarde te begrijpen die elk van uw hypothesen kan drijven. U wilt dat uw waarde rechtstreeks aan een van uw belangrijkste bedrijfsresultaten (KBO&#39;s) wordt gekoppeld en in een standaardindeling is, zodat elk van uw gebruiksgevallen met elkaar kan worden vergeleken. De meest gangbare methode is om een monetaire waarde toe te passen op elk geval van gebruik ter vergelijking.

* Kosten - Er zijn natuurlijke kosten verbonden aan het opbouwen van uw ontwerpvarianten binnen Doel en dan de potentiële uitrol. Nu zult u de kosten moeten schatten verbonden aan elk gebruiksgeval. De kosten omvatten, de tijd en de middelen die worden vereist om testervaringen, het plannen, en post testanalyse te bouwen.

Adobe raadt u aan elk van uw gebruiksgevallen op een schaal van 1 tot 5 te plaatsen, waarbij 1 eenvoudig en 5 complex is. U hebt nu een reeks prioritaire activiteiten die u in Adobe Target kunt testen. Deze activiteiten zullen de basis van uw jaarlijkse personaliseringsactiviteiten vormen. Adobe beveelt aan de routekaart van Personalization regelmatig opnieuw te evalueren. De lessen uit elke activiteit zouden uw toekomstgerichte roadmapprioriteiten moeten beïnvloeden. Leerlingen en aanbevelingen zullen doeltreffender zijn als ze tijdig worden opgevolgd. De prioriteiten van het hele jaar kunnen veranderen maar het uitvoeren van een iteratieve methodologie zorgt ervoor dat u altijd strategisch actieplan op zijn plaats hebt en dat u tegen uw team en bedrijfsdoelstellingen kunt volgen.

## Stap 4: Ontwerpen en uitvoeren

Gebruikend de documentatie die wordt gecreeerd om de het gebruikscase van het verpersoonlijkingsgebruik te strategen, construeer de Activiteit van Personalization binnen Doel om gekrulde inhoud voor uw prioritaire publiek te leveren. Zorg ervoor dat het type activiteit, de montages, de ervaringen, en de rapporteringseigenschappen aan de doelstellingen van het gebruiksgeval worden gericht. Ontwerp, QA, en Lancering van uw verpersoonlijkingsinspanning zijn het meest efficiënt wanneer de val in bestaande organisatieprocessen.

## Stap 5: Actie nemen over de resultaten

Zodra uw verpersoonlijkingsactiviteit een representatieve steekproef van bezoekers heeft in dienst genomen, kunt u analyse beginnen leveraging de inzichten om volgende stappen te begeleiden. Zorg ervoor dat u gegevens gebruikt in uw analyse, dat u aanbevelingen koppelt aan uw hypothese van het gebruikscase en dat u duidelijk de impact op bedrijfsdoelstellingen illustreert.

### Meer informatie

Wij adviseren dat u deze video kijkt die elk van deze stappen bespreekt: [ https://adobecustomersuccess.adobeconnect.com/pvsqvdvunpai/ ](https://adobecustomersuccess.adobeconnect.com/pvsqvdvunpai/)

Leer meer over strategie en gedachte leiderschap bij de [ hub van het Succes van de Klant ](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html?lang=nl-NL).