---
title: Hoe te om at.js 2.0 in Één enkele Toepassing van de Pagina (SPA) uit te voeren
description: Adobe Target at.js 2.0 biedt rijke functiesets die uw bedrijf uitrusten om personalisatie uit te voeren op client-side technologieën van de volgende generatie. Voer de volgende stappen uit om at.js 2.0 te implementeren in een toepassing voor één pagina (SPA).
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 955f0571-5791-4dbb-9931-e6d5c8bb42a7
source-git-commit: fcd2273ba373dc2b3bc59a77f1925cdb7b2ed3ee
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Adobe Target-code in.js 2.0 implementeren in een toepassing voor één pagina (SPA)

Adobe Target `at.js` 2.0 biedt rijke functiesets die uw bedrijf de mogelijkheid bieden om personalisatie uit te voeren op de volgende generatie clienttechnologieën. Deze versie is gericht op het upgraden van `at.js` voor harmonieuze interacties met toepassingen van één pagina (SPAs).

>[!VIDEO](https://video.tv.adobe.com/v/26248?quality=12)

## Hoe te om at.js 2.0 in een SPA uit te voeren

* Implementeer `at.js` 2.0 in de &lt;head> van de toepassing Eén pagina.
* Voer de `adobe.target.triggerView()` functie uit wanneer de meningsveranderingen in uw SPA. Hiervoor kunnen diverse technieken worden gebruikt, zoals het luisteren naar wijzigingen in URL-hashes, het luisteren naar aangepaste gebeurtenissen die door uw SPA zijn geactiveerd of het rechtstreeks insluiten van de `triggerView()` -code in uw toepassing. Kies de optie die het beste werkt voor uw specifieke toepassing met één pagina.
* De weergavenaam is de eerste parameter van de functie `triggerView()` . Gebruik eenvoudige, duidelijke en unieke namen, zodat u ze gemakkelijk kunt selecteren in de visuele ervaringscomposer van Target.
* U kunt meningen in kleine meningsveranderingen, evenals in niet-SPA contexten zoals half-onderaan een oneindige het scrollen pagina teweegbrengen.
* `at.js` 2.0 en `triggerView()` kunnen worden geïmplementeerd via een oplossing voor tagbeheer, zoals Adobe Experience Platform Launch.

## at.js 2.0 Beperkingen

Houd rekening met de volgende beperkingen van `at.js` 2.0 voordat u een upgrade uitvoert:

* Interdomeintracering wordt niet ondersteund in `at.js` 2.0
* De URL-parameters mboxOverride.browserIp en mboxSession worden niet ondersteund in `at.js` 2.0
* De oudere functies mboxCreate, mboxDefine, mboxUpdate zijn afgekeurd in `at.js` 2.0. De standaardinhoud zal worden getoond en geen netwerkverzoeken zullen worden gemaakt.

## Bibliotheekvoettekstcode die in de video wordt gebruikt

De onderstaande code is tijdens de video toegevoegd aan het gedeelte Bibliotheekvoettekst van de `at.js` -bibliotheek. Deze gebeurtenis wordt geactiveerd wanneer de app voor het eerst wordt geladen en vervolgens bij eventuele hash-wijzigingen in de app. Het gebruikt een schoongemaakte versie van de knoeiboel als meningsnaam, en &quot;huis&quot;wanneer de knoeiboel leeg is. Merk op dat om het KUUROORD te identificeren, de code de tekst &quot;reacties/&quot;in URL zoekt, die zeer waarschijnlijk op uw plaats zal moeten worden bijgewerkt. Houd er ook rekening mee dat het voor uw SPA geschikter kan zijn om `triggerView()` af te vuren van aangepaste gebeurtenissen of door de code rechtstreeks in uw app in te sluiten.

```javascript
function sanitizeViewName(viewName) {
  if (viewName.startsWith('#')) {
    viewName = viewName.substr(1);
  }
  if (viewName.startsWith('/')) {
    viewName = viewName.substr(1);
  }
  return viewName;
}
function triggerView(viewName) {
  viewName = sanitizeViewName(viewName) || 'home';
  // Validate if the Target Libraries are available on your website
  if (typeof adobe != 'undefined' && adobe.target && typeof adobe.target.triggerView === 'function') {
    adobe.target.triggerView(viewName);
    console.log('AT: View triggered on page load: '+viewName)
  }
}
//fire triggerView when the SPA loads and when the hash changes in the SPA
if(window.location.pathname.indexOf('react/') >-1){
    triggerView(location.hash);
}
window.onhashchange = function() {
    if(window.location.pathname.indexOf('react/') >-1){
        triggerView(location.hash);
    }
}
```

## Aanvullende bronnen

* [&#x200B; Begrijpend hoe at.js 2.0 werkt (de Diagrammen van de Architectuur) &#x200B;](understanding-how-atjs-20-works.md)
* [Adobe Target-composer voor visuele ervaring gebruiken voor toepassingen van één pagina (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
