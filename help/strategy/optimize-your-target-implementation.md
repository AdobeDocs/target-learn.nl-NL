---
title: Uw Adobe Target-implementatie optimaliseren
description: Bekijk een overzicht van de Adobe Target-implementatie en -structuur. Leer hoe u de instelling van uw organisatie kunt begrijpen en controleren. Leer de algemene technieken en tips voor het oplossen van problemen bij het maken van een kennisopslagplaats voor uw team.
solution: Target
feature: Overview
role: Leader, User
exl-id: 49b69f41-0993-437c-bb69-84392be427df
source-git-commit: 20bd1eb17ef6e287f7b76e14f727456e12d6f115
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---

# Uw Adobe Target-implementatie optimaliseren

Als u nog niet vertrouwd bent met uw organisatie en vertrouwd wilt raken met de functies van een test- en optimalisatiepraktijk, kunt u met dit artikel aan de slag. We beginnen met een overzicht van Adobe Target-implementatie en -structuur. U zult leren hoe te om de opstelling van uw organisatie te begrijpen en te controleren. Tot slot zullen wij gemeenschappelijke het oplossen van problementechnieken en uiteinden bij het creëren van een kennisbewaarplaats voor uw team bespreken.

Adobe Target is een hulpprogramma waarmee u unieke inhoud kunt testen en toewijzen aan verschillende bezoekers. Voor een overzicht van de beschikbare eigenschappen, [ bezoek deze gids ](https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en).

## Doelimplementatie en -structuur

Voordat we gaan duiken in het implementatieproces voor Adobe Target of hoe het gestructureerd is, is het handig om eerst een aantal basisprincipes van de software te begrijpen.

Adobe Target is een hulpprogramma waarmee u unieke inhoud kunt testen en toewijzen aan verschillende bezoekers zonder de native websitecode te wijzigen. Doel wijzigt tijdelijk de gebruikerservaring en houdt het gedrag van gebruikers na het zien van de wijziging bij. Het doel biedt ook de mogelijkheid om de ervaring voor eindgebruikers te wijzigen op basis van profielgegevens of eerdere acties.

Er zijn drie fundamentele types van Doelactiviteit:

1. A/B-test
2. MVT (Multivariate Test)
3. Ervaring testen

**test A/B** vergelijkt twee of meer ervaringen om te zien welke het best omzettingen door een vooraf gespecificeerde testperiode verbetert. De A/B-test is een sterk gecontroleerd experiment met verkeersmetingen, gesplitst naar percentages in plaats van naar een regel, waardoor u:

* de testgegevens te analyseren.
* om inzicht te krijgen in uw publiek.
* om te bepalen welke ervaring het beste presteert.

**Multivariate het testen** (MVT) vergelijkt combinaties aanbiedingen onder elementen op een pagina om te zien welke combinatie het beste voor een specifiek publiek presteert. Deze test identificeert ook welk element van de pagina het best omzettingen gedurende een vooraf gespecificeerde testperiode verbetert. MVT biedt:

* Een manier om meerdere aanbiedingen in meerdere elementen weer te geven.
* Een methode om de resulterende unieke ervaring tegen een specifiek doel te testen.
* Inzicht in welke elementen de grootste negatieve of positieve invloed hebben op de interactie tussen bezoekers.

**het testen van de Ervaring van 0} (Ervaren het richten) levert inhoud aan een specifiek publiek dat op een reeks van tellers-bepaalde regels en criteria wordt gebaseerd.** Deze methode biedt een manier om specifieke inhoud te richten op een specifiek publiek op basis van een set gedefinieerde toewijzingsregels.

Hoe werkt Target?

Hier is een voorbeeld op hoog niveau van hoe het Doel werkt:

1. Een bezoeker vraagt een pagina van uw server, en het toont in browser.
1. In de browser van de bezoeker wordt een cookie van de eerste partij ingesteld om het gedrag op te slaan.
1. De pagina roept vervolgens Adobe Target aan.
1. De inhoud wordt weergegeven op basis van de regels van de activiteit van de gebruiker.
1. Adobe Target legt specifieke metriek vast zoals die in de activiteitenconfiguratie wordt bepaald om de impact van de testervaringen te meten.

Het doel is gebaseerd op een &#39;global Mbox&#39; die de mogelijkheid biedt alles op de pagina te beïnvloeden. Deze functie wordt bij het laden van de pagina geïmplementeerd als een hardcoded koppeling naar het bestand at.js of wordt als Adobe Launch geleverd met een tagbeheer.

## Begrijp uw huidige implementatie

Om inzicht te krijgen in uw huidige implementatie, raadt de Adobe u aan om de implementatie van uw doelgebruikersinterface samen met het tagbeheer en de implementatie van het laden van pagina&#39;s te bekijken.

**om uw [!DNL Target] gebruikersinterface te herzien:**

1. Uw revisie starten op de gebruikersinterface van [!DNL Target] :

   * Bekijk de [!DNL Target] technologiestapel
   * Bevestig de beschikbare functies
   * Identificeer waar de plaatsing live is

1. Activiteiten voor beste praktijken evalueren:

   * Herzie historische campagnes voor programmarijpheid

1. Oude activiteiten deactiveren:

   * Middelen archiveren en opschonen [!DNL Target] die niet langer momenteel of in de toekomst worden gebruikt

1. Doelgroepen bekijken.

1. Omgevingsdefinities en bijbehorende domeinen controleren.

1. Profielscripts controleren voor toepassing

   * Alle profielmanuscripten lopen op elke doelvraag
   * Houd vraagefficiency door niet toepasselijke manuscripten te verwijderen

U kunt als volgt het tagbeheer en het laden van de pagina controleren:

1. Bevestig het volgende in Tagbeheer:

   * De implementatie van de verwachte [!DNL Target] JavaScript-code
   * De juiste oplossing voor het verbergen van inhoud
   * Stel de vereiste regels in om de aanroepen van [!DNL Target] te vullen met de verwachte parameters

1. Bevestig het volgende tijdens het laden van de pagina:

   * Overeenkomende versienummers voor de aanvraag-URL en [!DNL Target] aanvraag-URL
   * Bevolkte ID-waarde voor Ervaren cloud (Cloud Body)
   * Verwachte integratiewaarden presenteren (Cloud Body)
   * [!DNL Target] gevulde parameters op de juiste pagina&#39;s

## [!DNL Target] controleactiviteiten

Als u wilt voorkomen dat elke pagina handmatig wordt doorlopen om [!DNL Target] -activiteiten te controleren, gebruikt u de Adobe Auditor om inzicht te krijgen in de huidige technische status van uw implementatie. De Auditor van de Adobe wordt aangedreven door ObservePoint en kan opstelling zijn om op een manueel niveau in werking te stellen, om de kwesties op hoog niveau van de implementatie op uw plaats te identificeren.

De Adobe controleur verstrekt:

* Een hoge gezondheid op de site
* Snelle uitnodigingen voor implementatieproblemen

Adobe beveelt aan maandelijks handmatig audits uit te voeren om:

* Niet-gecodeerde pagina&#39;s identificeren
* Inconsistente versies identificeren
* Verouderde versies zoeken
* Geef gedetailleerde informatie die u kunt exporteren

## Algemene probleemoplossing

>[!NOTE]
>
>Adobe raadt u aan het Adobe Experience Platform Debugger te installeren.

Hier volgen algemene tips voor het oplossen van problemen wanneer u de Experience invoert:

### Cache en cookies*

* Cache en cookies wissen
* Wees voorzichtig met het gebruik van de privémodus (de privémodus in Firefox kan bijvoorbeeld blokkeren [!DNL Target])

### Bent u gekwalificeerd voor de activiteit?

* Controleer of u dezelfde stappen hebt uitgevoerd als het publiek dat in de activiteit gebruikte
* Gebruik `mboxTrace` - of reactietokens om profiel- en segmentwaarden te controleren

### Algemene tips voor het oplossen van problemen bij het valideren van visuele/functionele

Als u in de [!DNL Target] -ervaring werkt en de verwachte visuele ervaring niet ziet:

Controleer het [!DNL Target] antwoord:

* Als de code niet wordt uitgevoerd:

1. Conflicterende activiteiten controleren
1. Contact opnemen met de klantenservice

* Als de code wordt uitgevoerd:

1. Werk de code in dat scenario opnieuw bij

## Behoud van een kennisopslagplaats

Een kennisopslagplaats is een onlineplatform dat wordt gebruikt voor het documenteren en delen van informatie. De kennisopslagplaats bevat specifieke informatie voor uw implementatie en kan teamspecifieke informatie bevatten.

In het ideale geval zou de gegevensopslagruimte bewerken en automatisch opslaan binnen het platform moeten toestaan. Zodra het aanvankelijk wordt gevormd, is het gemakkelijk om bijgewerkt te handhaven en te houden. Inhoud in de kennisopslagplaats wordt op basis van gebruikersrollen gekromd.

De typische documenten in een Bewaarplaats van de Kennis omvatten:

* **document van het Overzicht** - een document dat wordt gebruikt om programmadoelstellingen, doelstellingen, processen en structuur duidelijk te verklaren
* **bewaarplaats van de Ideatie** - een document wordt gebruikt om potentiële ideeën te beheren en voorrang te geven die niet klaar voor het testende proces zijn
* **roadmap van het Programma** - een document dat wordt gebruikt om alle aspecten van het testen activiteiten te beheren zodra de ideeën klaar zijn om het het testen proces te beginnen
* **document van het Plan van de Activiteit** - een document dat wordt gebruikt om informatie te schetsen nodig om activiteiten te bouwen en te lanceren
* **document van het Plan van de Activiteit** - een document dat wordt gebruikt om resultaten en geadviseerde volgende stappen aan belanghebbenden mee te delen
* **dashboard van het Programma** - een document dat wordt gebruikt om programmaprestaties, kadentie, en opbrengstvoordelen in tijd te volgen.

Voor meer informatie, herzie ons [ webinar ](https://adobecustomersuccess.adobeconnect.com/p4p7xlp7dh42mp4/) met senior Consultant, Wilder Freed.

Leer meer over strategie en gedachte leiderschap bij de [ hub van het Succes van de Klant ](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html).
