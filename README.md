Ik wil een controlpanel maken dat een POV-ruimteschip cockpit simuleerd, waarbij een dynamisch sterrenveld achter je bewegen waardoor het lijkt alsof je door 3d space vliegt.


Donderdag 26/02 (Voorjaarsvakantie)
Doel: De fundering leggen van een interactieve sci-fi cockpit en een sterrenveld creëren.

Behaald:

- De visuele basis van het schip opgebouwd met header en section. Door middel van complexe clip-path: polygon() waarden heb ik de karakteristieke, hoekige cockpit-vormen uitgesneden.

- Een dynamisch sterrenveld opgezet met span elementen. Door 11n selectors en negatieve animation-delays lijkt de ruimte oneindig en staan de sterren bij het laden van de pagina direct verspreid over het scherm.

- Een functionele hendel gebouwd met verborgen radio-buttons met de :has() selector.

  
Woensdag 04/03 
Doel: De "Warp Drive" realiseren met animatie en visuele feedback.

Behaald:

- De sterren herschreven naar 12 groepen (12n) om gaten in het sterrenveld te dichten. Door rotate(var(--angle)) te combineren met scaleY wijzen alle warp-trails nu perfect naar het middelpunt, wat een realistisch diepte-effect geeft.

- Een transitie ontwikkeld voor de sprong naar warp. Tijdens de 3 seconden countdown trekken de sterren langzaam naar het midden (FOV animatie), wat een "Field of View" effect simuleert voordat de sprong plaatsvindt.

Feedback Systeem:

- "Enter" en "Exit" flitsen toegevoegd via pseudo-elementen op de body. Een blauwe gloed en flikkerende interieurverlichting.

- De cockpit trilt via heftige translate animaties (warp-shake).

- De windshield crack geoptimaliseerd met CSS-filters (invert, brightness, drop-shadow).

Technische uitdagingen & Leerpunten:

Het bleek uitdagend om meerdere animaties (freeze-space en warp-tunnel) op één element te draaien zonder dat de sterren terugspringen naar het midden. Dit is opgelost door de transform startposities exact te matchen in de keyframes.


Bronnen:

MDN – CSS :has()

MDN – Using CSS animations

CSS-Tricks – Guide to CSS Animation logic


Donderdag 12/03 

Doel:
Het realiseren van een interactief stuursysteem en een methode vinden om planeten te genereren zonder gebruik te maken van JavaScript voor de visuele weergave.

Behaald:

Interactieve besturing: Ik heb een stuursysteem geïmplementeerd dat reageert op de pijltjestoetsen. Via JavaScript wordt de rotatie berekend en als CSS-variabele (--steer-n) doorgegeven. Hierdoor bewegen de sterren synchroon mee en geven de cockpit het effect van ronddraaien.
<img width="569" height="341" alt="image" src="https://github.com/user-attachments/assets/dfe20b01-aab4-448f-8f62-5acf7a1f3b11" />


CSS "Slot Machine" Generator: Voor de planeten heb ik een systeem gebouwd met behulp van Nils Binder dat volledig op CSS draait. Door gebruik te maken van @property draait er op de body een constante animatie die waarden voor kleur, grootte en positie genereert met een snelheid van 0.1s.

Snapshot-mechanisme: Met de :has(:checked) selector op de radio-buttons van de snelheidshandel wordt de animation-play-state van de body gepauzeerd wanneer de hendel op "Cruise" staat. Dit bevriest de variabelen op een willekeurig moment, waardoor er telkens een andere planeet verschijnt. Het werkt alleen nog niet helemaal zoals ik het wil bij het aftellen van de warp countdown, maar daar gaan we morgen naar kijken. 
<img width="765" height="371" alt="image" src="https://github.com/user-attachments/assets/5e0d89a6-7903-4655-a9eb-0be1fc21fe8c" />


Visuele uitwerking:

Gelaagde structuur: De planeet is in een apart article-element geplaatst. Dit element fungeert als container voor de zichtbaarheid. Tijdens de countdown van 3 seconden fadet deze container uit naar opacity: 0. Helaas werkte dat niet omdat CSS geen states van een animatie kan onthouden om daar een nieuwe animatie opzetten. 

Gesynchroniseerde overgang: De RNG-animatie op de body heeft een animation-delay van 3.1s gekregen. Hierdoor blijven de coördinaten van de huidige planeet statisch terwijl hij wegfadet. Pas als de container volledig onzichtbaar is, begint de gokkast weer te draaien voor de volgende bestemming. Helaas werkte dit niet omdat CSS of de browser dan de "default planet" pakt om de animatie mee te doen, ookal was er eerst een compleet ander planeet. 

Technische uitdagingen & Leerpunten:

Timing: De grootste uitdaging was het voorkomen van de "regenboog-flits" (het snel wisselen van kleuren) tijdens de actieve fase. Door de delay van de animatie langer te maken dan de transitie van de fade, vindt de wissel nu plaats in een onzichtbare staat.

Bronnen:
Nils Binder - https://codepen.io/enbee81/pen/wvOVypZ?editors=1100

MDN – CSS @property

CSS-Tricks – Guide to Stacking Contexts

W3C – CSS Animations Level 2 spec (Play-state logic)
