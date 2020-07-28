---
title: Adobe Target-toepassing in.js 2.0 implementeren in een toepassing voor één pagina (SPA)
seo-title: Adobe Target-toepassing in.js 2.0 implementeren in een toepassing voor één pagina (SPA)
description: De nieuwste versie van at.js verstrekt rijke eigenschapreeksen die uw zaken uitrusten om verpersoonlijking op volgende-generatie, cliënt-zijtechnologieën uit te voeren. Deze nieuwe versie wordt geconcentreerd op bevordering at.js om harmonieuze interactie met enige paginatoepassingen (SPAs) te hebben.
audience: developer
difficulty: 3
author: Daniel Wright
doc-type: implement
activity-type: technical-video
translation-type: tm+mt
source-git-commit: 37443ae4c1cdda387c8db0053201d520fa1ec224
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# Adobe Target-toepassing in.js 2.0 implementeren in een toepassing voor één pagina (SPA)

De nieuwste versie van `at.js` verstrekt rijke eigenschapreeksen die uw zaken uitrusten om verpersoonlijking op volgende-generatie, cliënt-zijtechnologieën uit te voeren. Deze nieuwe versie wordt geconcentreerd op bevordering `at.js` om harmonieuze interactie met enige paginatoepassingen (SPAs) te hebben.

>[!VIDEO](https://video.tv.adobe.com/v/26248?quality=12)

## Hoe te om at.js 2.0 in een SPA uit te voeren

* Implementeer `at.js` 2.0 in de &lt;head> van de toepassing Eén pagina.
* Voer de `adobe.target.triggerView()` functie uit wanneer de meningsveranderingen in uw SPA. Verschillende technieken kunnen worden gebruikt om dit te doen, zoals het luisteren naar veranderingen van het knoeiboel URL, het luisteren naar douanegebeurtenissen die door uw SPA in brand worden gestoken, of het direct inbedden van de `triggerView()` code in uw toepassing. Kies de optie die het beste werkt voor uw specifieke toepassing met één pagina.
* De weergavenaam is de eerste parameter van de `triggerView()` functie. Gebruik eenvoudige, duidelijke en unieke namen, zodat u ze gemakkelijk kunt selecteren in de Target-composer voor visuele beleving.
* U kunt meningen in kleine meningsveranderingen, evenals in niet-SPA contexten zoals half-onderaan een oneindige het scrollen pagina teweegbrengen.
* `at.js` 2.0 en `triggerView()` kunnen worden geïmplementeerd via een oplossing voor tagbeheer, zoals Adobe Experience Platform Launch.

## at.js 2.0 Beperkingen

Houd rekening met de volgende beperkingen van `at.js` 2.0 voordat u de upgrade uitvoert:

* Interdomeintracering wordt niet ondersteund in `at.js` 2.0
* De URL-parameters mboxOverride.browserIp en mboxSession worden niet ondersteund in `at.js` 2.0
* De oudere functies mboxCreate, mboxDefine, mboxUpdate zijn afgekeurd in `at.js` 2.0. De standaardinhoud zal worden getoond en geen netwerkverzoeken zullen worden gemaakt.

## Bibliotheekvoettekstcode gebruikt in de video

De onderstaande code is tijdens de video toegevoegd aan het gedeelte Bibliotheekvoettekst van de `at.js` bibliotheek. Deze gebeurtenis wordt geactiveerd wanneer de app voor het eerst wordt geladen en vervolgens bij eventuele hash-wijzigingen in de app. Het gebruikt een schoongemaakte versie van de knoeiboel als meningsnaam, en &quot;huis&quot;wanneer de knoeiboel leeg is. Merk op dat om het KUUROORD te identificeren, de code de tekst &quot;reacties/&quot;in URL zoekt, die zeer waarschijnlijk op uw plaats zal moeten worden bijgewerkt. Houd ook in mening, dat het voor uw SPA geschikter zou kunnen zijn om `triggerView()` van douanegebeurtenissen af te vuren of door de code direct in uw app in te bedden.

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

* [Begrijpen hoe at.js 2.0 werkt (architectuurdiagrammen)](understanding-how-atjs-20-works.md)
* [Adobe Target-composer voor visuele ervaring gebruiken voor toepassingen van één pagina (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
* [Upgrade van 1.js 1.x naar 1.js 2.0-documentatie](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/upgrading-from-atjs-1x-to-atjs-20.html)