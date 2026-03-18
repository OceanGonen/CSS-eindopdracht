Ik wil een controlpanel maken dat een POV-ruimteschip cockpit simuleerd, waarbij een dynamisch sterrenveld achter je bewegen waardoor het lijkt alsof je door 3d space vliegt.


## **Donderdag 26/02 (Voorjaarsvakantie)**
Doel: De fundering leggen van een interactieve sci-fi cockpit en een sterrenveld creëren.

Behaald:

- De visuele basis van het schip opgebouwd met header en section. Door middel van clip-path: polygon() heb ik de vorm uitgesneden.

- Een dynamisch sterrenveld opgezet met span elementen. Door 11n selectors en negatieve animation-delays lijkt de ruimte oneindig en staan de sterren bij het laden van de pagina direct verspreid over het scherm.

- Een functionele hendel gebouwd met verborgen radio-buttons met de :has() selector.

  
## **Woensdag 04/03**
Doel: De "Warp Drive" realiseren met animatie en visuele feedback.

Behaald:

- De sterren herschreven naar 12 groepen (12n) om gaten in het sterrenveld te dichten. Door rotate(var(--angle)) te combineren met scaleY wijzen alle warp-trails nu perfect naar het middelpunt, wat een diepte-effect geeft.
<img width="1138" height="468" alt="image" src="https://github.com/user-attachments/assets/24f3ddf3-f8e3-4024-9e91-a3bbaaedf58d" />


- Een transitie ontwikkeld voor de sprong naar warp. Tijdens de 3 seconden countdown trekken de sterren langzaam naar het midden (FOV animatie), wat een "Field of View" effect simuleert voordat de sprong plaatsvindt.
<img width="926" height="317" alt="image" src="https://github.com/user-attachments/assets/f75d1f3a-3e09-4e82-aaaf-fe189273263d" />


Feedback Systeem:

- "Enter" en "Exit" flitsen toegevoegd via pseudo-elementen op de body. Een blauwe gloed en flikkerende interieurverlichting.

- De cockpit trilt via translate animaties (warp-shake).

- De windshield crack meer laten poppen met CSS-filters (invert, brightness, drop-shadow).

Technische uitdagingen & Leerpunten:

Het is onmogleijk om meerdere animaties (freeze-space en warp-tunnel) op één element te draaien zonder dat de sterren terugspringen naar het midden. 


Bronnen:

MDN – CSS :has():  https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:has

Drafts – Using CSS state animations: https://drafts.csswg.org/css-animations-2/#animation-play-state

CSS-Tricks – Guide to CSS Animation logic: https://css-tricks.com/almanac/functions/h/hue-rotate/

## **Week reflectie**
Het doel van deze week was uitdagend: een POV-ervaring bouwen van een ruimteschip dat door een 3D-ruimte lijkt te vliegen, zonder scripts. De afgelopen dagen heb ik gewerkt aan de fundering, de snelheid en de interactie van dit schip.

**De start:**
Ik begon bij de basisvormen. Om de leegte buiten te vullen, heb ik een sterrenveld gemaakt van simpele span-elementen. Een belangrijk leermoment hier was het gebruik van de 11n selector en negatieve animation-delays. Hierdoor staan de sterren bij het openen van de pagina meteen verspreid over het scherm, in plaats van dat ze allemaal tegelijk vanaf het midden beginnen te vliegen. 

**De sprong naar Warp:**
Nadat de basis stond, was het tijd voor de Warp Drive. De uitdaging was om diepte te creëren. Door de sterren in 12 groepen te verdelen en ze te draaien met rotate(var(--angle)), wijzen alle lichtstrepen nu perfect naar één verdwijnpunt. Het toevoegen van een 3-seconden countdown was een extra detailtje wat ik leuk vond om toe te voegen; het "Field of View" effect waarbij de sterren eerst naar binnen trekken voordat ze exploderen in warp-trails, geeft echt het gevoel van acceleratie. Ik liep hier wel tegen de grens van CSS aan: het is voor zover ik weet onmogelijk om twee verschillende animaties op één element te laten draaien zonder dat de boel verspringt. 

**Interactie:** 
Daarna lag de focus op de knoppen en de besturing. Het implementeren van een stuur die de planeet en de sterren de andere kant op duwt (parallax), maakte een cool effect. 

**Terugblik:**
Als ik naar de week terugkijk, zie ik de kracht van CSS selectors. Het slim gebruiken van de :has() selector voor de logica en @property voor de willekeurige planeten laat zien dat CSS veel meer kan dan alleen stylen. Het was een week van finetunen: van het laten trillen van de cockpit tijdens warp tot het timen van een snelheids hendel. Het resultaat is een cockpit die ook een beetje karakter heeft.










## **Donderdag 12/03**
Doel:
Het realiseren van een methode vinden om planeten te genereren zonder gebruik te maken van JavaScript.

Behaald:

Interactieve besturing: Ik heb een stuursysteem geïmplementeerd dat reageert op de muis en pijltoetsen. Via JavaScript wordt de rotatie berekend en als CSS-variabele (--steer) doorgegeven. Hierdoor bewegen de sterren en planeten (de sterren iets minder dan de planeten voor het dieptegevoel) en geven de cockpit het effect van naar links en rechts gaan.
<img width="721" height="475" alt="image" src="https://github.com/user-attachments/assets/359809e4-68ec-4dae-a8bd-c25a1519d5dc" />
<img width="530" height="36" alt="image" src="https://github.com/user-attachments/assets/fcab693e-cb27-479f-911e-0ef261972428" />


Ook heb ik een fuel gauge gemaakt met een visuele gag dat wanneer je erop klikt gaat de meting naald naar Empty. 
<img width="280" height="150" alt="image" src="https://github.com/user-attachments/assets/ac2aea0a-2a2c-4974-a3e9-d45cbc063dc0" /> <img width="285" height="135" alt="image" src="https://github.com/user-attachments/assets/bac26db3-4ef1-4753-838a-af5872e617d7" />



CSS rng: Voor de rng planeten met behulp van Nils Binder z'n code dat volledig op CSS draait. Door gebruik te maken van @property draait er op de body een constante animatie die waarden voor kleur, grootte en positie genereert met een snelheid van 0.1s. Met de :has(:checked) selector op de radio-buttons van de snelheidshandel wordt de animation-play-state van de body gepauzeerd wanneer de hendel op "Cruise" staat. Dit bevriest de variabelen op een willekeurig moment, waardoor er telkens een andere planeet verschijnt. Het werkt alleen nog niet helemaal zoals ik het wil bij het aftellen van de warp countdown, maar daar gaan we morgen naar kijken. 
<img width="765" height="371" alt="image" src="https://github.com/user-attachments/assets/5e0d89a6-7903-4655-a9eb-0be1fc21fe8c" />


Visuele uitwerking:

Gelaagde structuur: De planeet is in een apart article-element geplaatst. Dit element dient als container voor de zichtbaarheid. Tijdens de countdown van 3 seconden fadet deze container uit naar opacity: 0. Helaas werkte dat niet omdat CSS geen states van een animatie kan onthouden om daar een nieuwe animatie opzetten. 

Gesynchroniseerde overgang: De RNG-animatie op de body heeft een animation-delay van 3.1s gekregen. Hierdoor blijven de coördinaten van de huidige planeet statisch terwijl hij wegfadet. Pas als de container volledig onzichtbaar is, begint de gokkast weer te draaien voor de volgende bestemming. Helaas werkte dit niet omdat CSS of de browser dan de "default planet" pakt om de animatie mee te doen, ookal was er eerst een compleet ander planeet. 

Technische uitdagingen & Leerpunten:

Timing: De grootste uitdaging was het voorkomen van de regenboog aan planeten (het snel wisselen van kleuren) tijdens de actieve fase. Door de delay van de animatie langer te maken dan de transitie van de fade, vindt de wissel nu plaats in een onzichtbare staat.

Bronnen:
Nils Binder - https://codepen.io/enbee81/pen/wvOVypZ?editors=1100

MDN – CSS @property

CSS-Tricks – Guide to Stacking Contexts

W3C – CSS Animations Level 2 spec (Play-state logic)


## **Woensdag 18/03**
Doel:
Voldoen aan alle eisen van de opdracht: Pakkende titel en font, het toevoegen van een "Thema" door middel van een nachtvisie Toggle.

Behaald:

Interactieve Nachtvisie:

Een Toggle gemaakt in de bovenste sectie van de cockpit. Door gebruik te maken van transform-origin: 20% center en een specifieke cubic-bezier(0.895, 0.03, 0.685, 0.22) timing, simuleert de hendel zwaartekracht: hij valt met een versnelling omlaag. https://codepen.io/oliviale/pen/xxboXzo

Deze hendel is de Theme Switcher. Via de :has(input[name="theme"]:checked) selector op de body wordt een soort nachtkijker-modus geactiveerd.
<img width="1412" height="730" alt="image" src="https://github.com/user-attachments/assets/be8b1ae3-6416-459c-a22a-f79a1ad37094" />

Visuele filters: Alleen de ruimte (sterren en planeten) wordt aangetast door een groen monochroom filter (sepia, hue-rotate, saturate). De cockpit zelf blijft notmaal. Alleen bij de fuelgauge zie je ook dat het groen oplicht, wat niet de bedoeling is, maar het is het gevolg van een 'happy accident', aangezien door een te algemene selector de <span>'s in de fuel gauge oplichten en knipperen net als de sterren tijdens de warptunnel animatie. Nu is het een minder happy accident, maar wil ik niet de selectors aanpassen als ik de knipperde UI opoffer daarvoor.
<img width="312" height="164" alt="image" src="https://github.com/user-attachments/assets/74480eca-5f73-4a9d-86a3-13c3f78c474b" />

Als laatste heb ik een space font gedownload en een simpele, hopelijk pakkende titel.
https://www.1001fonts.com/space-fonts.html


Technische uitdagingen & Leerpunten:

Zwaartekracht simuleren: Het was een uitdaging om het witte bolletje op de hendel pas te laten rollen als de hendel verticaal genoeg stond. Dit is opgelost door een transition-delay van 0.2s toe te voegen aan het balletje, waardoor de hendel eerst een stukje moet "vallen" voordat de beweging start.

Gelaagde filters: Het bleek lastig om alleen de ruimte groen te kleuren zonder het hele schip mee te nemen. Door de filters specifiek op de span (sterren) en figure (planeet) te zetten en een pseudo-element (body::after) met een lage z-index te gebruiken voor de scanlijnen, is de cockpit 'vrijgehouden' van de Night Vision.

Bronnen:

Olivia Ng – CSS Gravity Toggle Logic

MDN – CSS filter property (Night Vision implementation)

CSS-Tricks – transform-origin deep dive
