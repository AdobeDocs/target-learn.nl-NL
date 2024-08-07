---
title: Hoe te om bij.js 2.0 in een Enige Toepassing van de Pagina uit te voeren (SPA)
description: Adobe Target at.js 2.0 biedt rijke functiesets die uw bedrijf uitrusten om personalisatie uit te voeren op client-side technologieën van de volgende generatie. Voer de volgende stappen uit om 0.js 2.0 te implementeren in een toepassing voor één pagina (SPA).
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 955f0571-5791-4dbb-9931-e6d5c8bb42a7
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Adobe Target- in.js 2.0 implementeren in een toepassing voor één pagina (SPA)

Adobe Target `at.js` 2.0 biedt rijke functiesets die uw bedrijf de mogelijkheid bieden om personalisatie uit te voeren op de volgende generatie clienttechnologieën. Deze versie is gericht op het upgraden van `at.js` voor harmonieuze interacties met toepassingen van één pagina (SPA).

>[!VIDEO](https://video.tv.adobe.com/v/26248?quality=12)

## Hoe te om bij.js 2.0 in een SPA uitvoeren

* Implementeer `at.js` 2.0 in de &lt;head> van de toepassing Eén pagina.
* Implementeer de functie `adobe.target.triggerView()` wanneer de weergave verandert in de SPA. Hiervoor kunnen verschillende technieken worden gebruikt, zoals het luisteren naar wijzigingen in URL-hashes, het luisteren naar aangepaste gebeurtenissen die door uw SPA worden geactiveerd of het rechtstreeks insluiten van de `triggerView()` -code in uw toepassing. Kies de optie die het beste werkt voor uw specifieke toepassing met één pagina.
* De weergavenaam is de eerste parameter van de functie `triggerView()` . Gebruik eenvoudige, duidelijke en unieke namen, zodat u ze gemakkelijk kunt selecteren in de visuele ervaringscomposer van Target.
* U kunt weergaven activeren in kleine weergavewijzigingen en in niet-SPA contexten, zoals een pagina waarop oneindig wordt geschoven.
* `at.js` 2.0 en `triggerView()` kunnen worden geïmplementeerd via een oplossing voor tagbeheer, zoals Adobe Experience Platform Launch.

## at.js 2.0 Beperkingen

Houd rekening met de volgende beperkingen van `at.js` 2.0 voordat u een upgrade uitvoert:

* Interdomeintracering wordt niet ondersteund in `at.js` 2.0
* De URL-parameters mboxOverride.browserIp en mboxSession worden niet ondersteund in `at.js` 2.0
* De oudere functies mboxCreate, mboxDefine, mboxUpdate zijn afgekeurd in `at.js` 2.0. De standaardinhoud zal worden getoond en geen netwerkverzoeken zullen worden gemaakt.

## Bibliotheekvoettekstcode die in de video wordt gebruikt

De onderstaande code is tijdens de video toegevoegd aan het gedeelte Bibliotheekvoettekst van de `at.js` -bibliotheek. Deze gebeurtenis wordt geactiveerd wanneer de app voor het eerst wordt geladen en vervolgens bij eventuele hash-wijzigingen in de app. Het gebruikt een schoongemaakte versie van de knoeiboel als meningsnaam, en &quot;huis&quot;wanneer de knoeiboel leeg is. Om de SPA te identificeren, zoekt de code naar de tekst &quot;reactie/&quot; in de URL, die waarschijnlijk op uw site moet worden bijgewerkt. Houd er ook rekening mee dat het geschikter is als uw SPA `triggerView()` afsluit van aangepaste gebeurtenissen of als u de code rechtstreeks in uw app insluit.

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

* [ Begrijpend hoe at.js 2.0 werkt (de Diagrammen van de Architectuur) ](understanding-how-atjs-20-works.md)
* [Adobe Target-composer voor visuele ervaring gebruiken voor toepassingen van één pagina (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
