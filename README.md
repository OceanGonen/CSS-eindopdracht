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
