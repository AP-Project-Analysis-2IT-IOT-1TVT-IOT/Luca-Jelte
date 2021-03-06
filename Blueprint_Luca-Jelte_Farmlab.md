# Farmlab



AP Hogeschool<br>
Luca Van Laer en Jelte Boumans

## Opdrachtgever
Maarten Luyts: Productowner en projectbegeleider.

## Samenvatting

Het Farmlab is een project voor IoT studenten van het 2e jaar. Er wordt verder gebouwd op vorige iteraties. *Momenteel wordt er verder gebouwd op de vierde iteratie. 

Het Farmlab is een kast met 3 niveau’s. Op elk niveau groeien planten via hydrocultuur. Dit houd in dat de wortels van de planten niet in de grond zitten, maar direct in water liggen. Doormiddel van voedingsstoffen in het water kunnen ze verder groeien. Op deze wijze kan men landbouw in de hoogte uitbreiden.

De onderdelen van de kast worden volledig geautomatiseerd zodat ze remote kunnen worden gecontroleerd, bestuurd en gescheduled.
## Situatie As-Is

Momenteel wordt er gewerkt aan de vierde iteratie van de kast. Al de documentatie van de vorige groepen/iteraties kan men hier vinden:

- https://github.com/jp19-lafa/Documentation/wiki
- https://ap-it-gh.github.io/lf-xy1-docs/#/ | https://ap-it-gh.github.io/lf-xy2-docs/#/
- https://ap-it-gh.github.io/ssys21-docs-labfarm/#/README

Momenteel zijn er 3 hoofdproblemen waar men aan werkt:

<ol>
  <li>Ordelijke opbouw van de kast</li>
  <ul>
    <li>Management van kabels</li>
    <ul>
      <li>Kabels op lengte maken</li>
      <li>Kabelbescherming toevoegen</li>
    </ul>
    <li>Makkelijke installatie en afbraak</li>
    <ul>
      <li>Gebruik maken van een klik/schuif systeem</li>
    </ul>
    <li>3D printed supports herwerken</li>
    <ul>
      <li>Gewicht verminderen</li>
      <li>Lager maken</li>
    </ul> 
  </ul>
  <li>Automatisatie</li>
  <ul>
    <li>Instellen per plant </li>
    <li>Automatische aansturing van alle onderdelen</li>
  </ul>
  <li>PCBs herwerken</li>
  <ul>
    <li>Op maat gemaakte cases</li>
    <li>ESP32 integreren (vervangt nodeMCU)</li>
    <li>Zekeringen toevoegen</li>
    <li>Hoeken afronden</li>
    <li>Grotere smd pads</li>
    <li>Silkscreen standariseren</li>
    <li>Plaats om mosfets plat te leggen</li>
    <li>Betere koeling voorzien</li>
  </ul>
</ol>
[1]

In grote lijnen wilt men versie 3 van het Farmlab:
- Gebruiksvriendelijker maken
- Automatiseren


## Situatie To-Be

In iteratie vier legt men de probleemstellingen van versie vier bloot om ze verder te verwerken. Dit houdt in dat de verschillende onderdelen waaruit de kast is opgebouwd verder worden verfijnd en geoptimaliseerd. Zo kan de kast voor een periode van 1 maand zelfstandig werken met remote besturing. 

De vijf onderdelen zijn: 
<ul>
  <li>Pomp controller</li>
  De pomp controller moet in staat zijn om het water op het gepaste moment rond te pompen. Zo vermijd men dat er algen of andere planten in het water groeien. Dit proces moet     geautomatiseerd worden om te vermijden dat de gebruiker de pomp manueel moet aanzetten.
  <li>LED Controller/Lichtsensor</li>
  De LED controller moet in staat zijn om een gepast aantal en soort licht te produceren voor de specifieke planten. 
  <li>XY-Systeem</li>
  Het XY-systeem bevindt zich aan de achterkant van de kast. Dit systeem kan aan de hand van een camera en AI image processing herkennen in welk groeistadium een plant is.         Optioneel kan deze plant ook worden geoogstd. Met deze informatie kan men de pomp aansturen of de belichting aanpassen. Momenteel is het XY-systeem op de kast gemonteerd en     kan het bewegen binnen het XY-vlak. Er is een camera aanwezig maar geen AI systeem.
  <li>Temperatuursensor</li>
  Er zijn temperatuursensoren gemonteerd om de omgevingstemperatuur te meten. Zo kan men de temperatuur van de kamer waar de kast zich bevindt monitoren. Daarmee kan   de gebruiker bijvoorbeeld gewaarschuwd worden over een te lage temperatuur.
  <li>Watersensor</li>
  Met de sensoren in de watertank kan men de PH waarde en het waterniveau meten. De gebruiker blifjt dan op de hoogte van de PH waarde van het water en kan dit         bijvullen indien nodig.
</ul>  

Van de vijf onderdelen moeten de PCBs herwerkt worden. Deze moeten gebruik maken van ESP32 in de plaats van ESP12. Het management van kabels moet worden herbekeken en verbeterd. 
Via standardisatie kan men alle onderdelen makkelijk namaken om kopieën van de kast te maken.



## Projectdefinitie
### Planning
- Wekelijks resultaten leveren
- Elke donderdag samen 3 uur werken
- Doorheen de week individueel werken
- Tools: Github


| Hoofdlijnen |  Datum      | Student    |
| ----------- | ----------- |----------- |
| Opmaak blueprint| 2 Dec       |Luca Van Laer|
| As is / To be| 2 Dec      |Jelte Boumans|
| DFD opstellen| 14 Dec |Jelte Boumans|
| Blokschema opstellen| 15 Dec |Luca Van Laer|
| Beschrijving DFD gemaakt| 16 Dec |Jelte Boumans & Luca Van Laer|
| Interfaces, infrastructuur impact, security analyse, docs, bronnen| 17 Dec |Jelte Boumans & Luca Van Laer|

### Planning uitvoering (2de semester)
| Hoofdlijnen |  Datum      | Student    |
| ----------- | ----------- |----------- |
| Aanpassen PCB Ledcontroller| 2de semester       |TBD|
| Aanpassen PCB lichtsensor| 2de semester       |TBD|
| Aanpassen PCB temperatuursensor| 2de semester       |TBD|
| Aanpassen PCB watersensor| 2de semester       |TBD|
| Checken pomp controller| 2de semester       |TBD|
| X-Y syteem| 2de semester      |Luca Van Laer & Jelte Boumans|
| Kast kabelmanagement| 2de semester      |TBD|
| Kast uittesten voor een maand| 2de semester      |TBD|

## Functioneel design
<ul>
  <li>Pomp controller</li>
      De pomp controller moet in staat zijn om het water op het gepaste moment rond te pompen. Hierdoor kunnen er geen algen of andere planten in het water groeien doordat het water te lang heeft stil gestaan. Dit proces moet automatisch gebeuren zodat de gebruiker niet om de zoveel tijd manueel de pomp moet aanzetten. Daarnaast is er nog een tweede pomp om de voedingsstoffen toe te voegen aan het water zodat de planten optimaal kunnen groeien. Ook deze wordt geautomatiseerd en remote aanpasbaar zodat de hoeveelheden voedingstoffen kunnen worden aangepast indien nodig. Tot nu toe werd er gewerkt met een pomp die manueel werd aangestuurd en zitten ze in het proces om te kijken of al de buizen waterdicht zijn. 
  <li>Led Controller</li>
      De led controller moet in staat zijn om het gepaste licht te produceren voor de specifieke plant gebasseerd op het omgevingslicht gemeten via de light sensor. Deze moet remote aanpasbaar zijn zodat, indien de 'gezondheid'van de plant achteruit gaat, de gebruiker deze kan aanpassen zonder zich naar de kast te moeten verplaatsen en dit in de code moet gaan aanpassen. Per niveau is er een led controller zodat de leds per niveau kunnen worden aangepast. 
  <li>Light sensor</li>
       De light sensor detecteert het omgevings licht en geeft dit door aan de led controller. De led controller past de licht sterkte van de led dan aan om de gepaste lux te bekomen. Bijvoorbeeld onze plant moet ten minste 15000 lux krijgen. Als het omgevingslicht dan 10000 lux is zal de light sensor aan de led controller doorgeven dat deze nog 5000 lux moet voorzien. Komt er een wolk voor de zon en daalt de lux zal dit automatisch gecompenseerd worden door de led controller. Per niveau is er een light sensor zodat deze de leds van dat enkel dat niveau kan aanpassen.
  <li>X-Y systeem</li>
      Het XY systeem is het systeem dat zich aan de achterkant van de kast bevindt. Dit systeem dient om, aan de hand van een camera en AI, te herkennen wanneer de plant die in de kast wordt geteeld volgroeid is en deze dan met het XY systeem te oogsten. Daarnaast kan dit systeem informatie sturen over het groeiproces van de plant, het pomp systeem aanpassen indien nodig alsook de belichting. Het XY systeem met zijn AI is als ware de brein van het Farmlab. Momenteel is het XY systeem op de kast gemonteerd en kan dit bewegen in het XY-vlak maar is er nog geen camera of AI systeem geïnstalleerd. 
  <li>Temperatuur sensor</li>
      De temperatuur sensor meet de omgevings temperatuur. Aan de hand van deze data kan er dan iets voorzien worden om de temperatuur te doen stijgen of dalen. Dit wordt meegenomen in de analyse maar zal enkel toegevoegd worden indien er nog tijd over is. Op dit moment zou dit ons te ver afleiden. 
  <li>Water sensor</li>
      De water sensor bepaald of er genoeg water in de buizen is en stuurt de pompcontroller aan indien dit niet het geval is. Hierdoor is er op elk moment voldoende water aanwezig in de buizen zodat de plant voldoende voeding kan opnemen. 
</ul>  

Deze onderdelen worden in het technisch design verder uitgepunt.


## Technisch design

### Smart Object (Hardware Analyse)
### Kast
![image](https://user-images.githubusercontent.com/91600019/144228425-952029da-4239-4ce4-bf58-538cb70fdf7a.png)
### Ontwerp kast
![image](https://user-images.githubusercontent.com/91600019/144228812-acda100e-8fd4-431b-b07b-b1d94918728a.png)
[2]

### Buis Support versie 3
V3 is momenteel het finale design van de supports. Na het monteren van de V2's zijn er enkele problemen gevonden tijdens het monteren van de supports en de buizen. De volgende 2 aanpassingen zorgen ervoor dat de montage makkelijker gaat. Zoals bij V2 word V3 ook verticaal geprint en is er nood aan supports.
- De verbreding van de poten aan de onderkant zorgen ervoor dat tijdens het monteren van de supports aan het hout met vijzen deze makkelijker bereikbaar zijn.
- De toevoeging van uitsparingen voor M4 moeren in het onderste gedeelte zorgen ervoor dat de moeren in de print vastgezet kunnen worden.
[3]

### Buis support top
![image](https://user-images.githubusercontent.com/91600019/144415593-ff1d9519-1c01-4641-bc63-75d436ce7a8c.png)
### Buis support bottom
![image](https://user-images.githubusercontent.com/91600019/144415648-35df6548-4976-4d9e-8b02-2e6f26a9a01a.png)

### Groeibakje V4
Versie 4 is anders gebouwd dan de vorige versies en is ook de eind versie voor de groeibakjes. De afmetingen voor de basis en gaten blijven hetzelfde, alleen de opbouw is wat anders. Het model gaat eerste paar 16mm naar boven en dan pas begint die schuin te gaan tot de bovenste offset-plane. Vandaar gaat het schuin zodat de planten hun wortels rechtstreeks in het water groeien. De techniek hiervoor is van een cirkel naar een vierkant die bij een schuine offset plane gemaakt is geweest een daarna loft te gebruiken om ze bij elkaar te verbinden. 
[4]

![image](https://user-images.githubusercontent.com/91600019/144416435-30955e32-0042-47d6-a0a0-b1ceff3f6622.png)

| Ring |  Groeibakje      | 
|-----------|-----------|
| hoogte: 8mm| hoogte: 46mm       |
| breedte binneste diameter: 60mm| breedte diameter1: 60mm      |
| breedte buitenste diameter: 65mm| breedte diameter2: 40mm      |
|| de dikte van de binnenkant: 0.5mm      |

### Opsplitsen PCB's
### Blokdiagram 
![image](https://raw.githubusercontent.com/AP-Project-Analysis-2IT-IOT-1TVT-IOT/Luca-Jelte/main/BlokDiagrammen/blokdiagram_farmlab.drawio.png)

### Hardware keuze
| Naam        |Spanning (V)   |Stroom (A)   |
| ----------- | ----------- |----------- |
| Pomp|5|0,9-1,7|
| Raspbery Pi|5|600mA-1,2|
| ESP32|3,3|240mA|
| Stepper Motor driver|12-24|2,5(MAX)|
| Led strip|12|400mA|

### Comunicatie keuze

**Mogelijkheden:**
| Type        |Voordelen   |Nadelen   |
| ----------- | ----------- |----------- |
| Wifi|-Groot bereik<br>-Makkelijk uitbreidbaar<br>-Middelmatige afstand<br>-Snel<br>-Security instelbaar<br>-Connectie naar Raspberry Pi server mogelijk |-Verbruikt relatief veel energie|
|Bluetooth|-Makkelijk<br>-Relatief zuinig|-Korte afstand<br>-Traag<br>-Geen security<br>-Ondersteund weinig apparaten (max 8)|
|Bedraad |-Makkelijk op korte afstand<br>-Minder kans op externe verstoringen<br>-Geen antenne nodig|-Niet ideaal voor lange afstand (onoverzichtelijk)<br>-Moeilijk uitbreidbaar|

**Onze keuze:**

- Bedrade communicatie willen we enkel voor zeer korte afstanden gebruiken of indien er geen ander optie is.
- Draadloze communicatie gaan we gebruiken voor het grootste deel van het project, het geeft ons de meeste uitbreidmogelijkheden en zorgt dat alles overzichtelijk blijft.
Verder is er gekozen voor WiFi. Deze biedt de meest betrouwbare communicatie voor meer dan 12 devices. Aangezien er volgens een main controller / node systeem wordt gewerkt is dit essentieel.

### Keuze voeding

**Mogelijkheden:**
| Type        |Voordelen   |Vadelen   |
| ----------- | ----------- |----------- |
| Batterij |-Draadloos/ordelijk |-Moeten opgeladen worden|
| Bedrade voeding | -Makkelijk |-Meer bekabeling in de kast|

**Onze keuze:**

Er wordt gegaan voor 'the best of both worlds'. Dit houdt in dat er voor elke controller zo draadloos mogelijk wordt gebouwt, dus met behulp van batterijen. Er wordt wel steeds een backup aansluiting voorzien voor bekabelde voeding.

### Batterij keuze

**Mogelijkheden:**
| Type        |Spanning|Max stroom|Voordelen   |Nadelen   |
| ----------- | ----------- |----------- |----------- |----------- |
| 18650 | 4,2 |4 |-Makkelijk<br>-Hoge stroom|Groot - Moet in houder|
| Lithium Ion batterij (PRT-13854 ROHS) | 3,7 |2,5|-Klein/plat<br>-Geen houder nodig<br>-Voltage dicht bij ESP input voltage|- Minder capaciteit|

**Onze keuze:**

Aangezien er voor de sensor geen grote capaciteit of vermogen nodig is, is er gekozen voor de Lithium Ion batterij. Deze zou ook zonder houder kunnen bevestigen worden aan de PCB. De 18650 batterijen daarentegen nemen onnodig veel plek in.


### Analyse LEDController

### Blokdiagram

![Blokdiagram LEDController](https://ap-it-gh.github.io/ssys21-docs-labfarm/Images/Blokdiagram_LED_Controller.jpg)


### Analyse Licht Sensor

### Blokdiagram

![Blokdiagram LightSensorController](https://ap-it-gh.github.io/ssys21-docs-labfarm/Images/Blokdiagram_Licht_Sensor.jpg)

### Component keuze

**Mogelijkheden:**
| Naam        |Min dynamic range (Lux)|Max dynamic range (Lux)|Voeding   |Interface 	   |Prijs|
| ----------- | ----------- |----------- |----------- |----------- |----------- |
|[lichtweerstand](https://www.kiwi-electronics.nl/nl/lichtgevoelige-weerstand-ldr-416)| 1 |10|1V-200V| Analoog | 1,95€ |
| [TSL2561](https://www.adafruit.com/product/439) | 0.1 |40000 | 2,7-3,6V | I2C  	|+-5€ |
| [TSL2591](https://shop.mchobby.be/en/environnemental-press-temp-hum-gas/1599-tsl2591-sensor-lux-luminosite-lumiere-digital-3232100015999-adafruit.html) | 188µ | 	88000 |3,3-5V | I2C |  	8,69€ |
|[TSL2591](https://www.kiwi-electronics.nl/nl/si1145-digital-uv-index-ir-visible-light-sensor-1574) | NaN | NaN | 3-5V | I2C | 11,99€ |

De 'TSL2561' geeft de nodige accuraatheid voor een schappelijke prijs.


### Analyse PompController

### Blokdiagram

![Blokdiagram PompController](https://ap-it-gh.github.io/ssys21-docs-labfarm/Images/Blokdiagram_Pomp_Controller.jpg)


### Analyse Temperatuursensor

### Blokdiagram

![Blokdiagram TemperatuurSensor](https://ap-it-gh.github.io/ssys21-docs-labfarm/Images/Blokdiagram_Temperatuur_Sensor.jpg)

### Component keuze

**Mogelijkheden:**
| Naam |Min temp (°C)|Max temp (°C)|Accuraatheid (°C)|Min spanning (V)| Min voltage (V) |Mounting|Soort|Prijs|
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| DHT11 | 0 | 50 | 2 | 3 | 5 | thru hole | packet | 2,45 |
| DHT22 | -4 | 80 | 0.5 | 3 | 5 | thru hole | packet | 9,95 |
| HIH8121-021-001 | -25 | 85 | 0.5 | 2.3 | 5.5 | SMD | apart | 7,78 |
| HIH6130-021-001 | -40 | 125 | 0.5 | 2.3 | 5.5 | thru hole | apart | 8,41 |
| SHT31-DIS-B | -40 | 125 | 0.2 | 2.15 | 5.5 | SMD reflow | apart | 4,5 |


De 'HIH6130-021-001' temperatuur en vochtigheidssensor voldoet aan de belangrijkste eisen. Voldoende range van meetbare temperaturen en minder dan 1°C accuraatheid. Extra accuraatheid zouden kunnen bekomen worden met de 'SHT31-DIS-B', deze kan echter in de beginfases niet gebruikt worden omdat deze enkel met SMD reflow op een PCB geplaatst kan worden. Deze methode is vrij duur omdat deze stencils nodig heeft en dit niet ideaal is in de test/ontwerp fase. 


### Analyse WaterSensor


## Smart Object (Software Analyse)
### Data

Data wordt grotendeels verstuurd tussen de centrale RaspberryPi (broker MQTT en NodeRED) en de ESP32's aanwezig op de PCB's.
Alle data die tussen deze 2 uitgestuurd worden zullen van het type string zijn.

<ol>
  <li>PompController: </li>
  <ul>
    <li>NodeRED -> RaspberryPi broker -> ESP32 op pompcontroller:</li>
    <ul>
      <li>Topics: farm/x/pomp/water OF farm/x/pomp/nutrients</li>
      <li>String "on" => Pomp gaat aan</li>
      <li>String "off" => Pomp gaan uit</li>
    </ul>
  </ul>
  <li>LEDController:  </li>
  <ul>
    <li>NodeRED -> RaspberryPi broker -> ESP32 op LEDController:</li>
    <ul>
      <li>Topics: farm/x/licht/level/y => y = level 1,2 OF 3</li>
      <li>String "on" => LED's op level y gaat aan</li>
      <li>String "off" => LED's op level y gaat uit </li>
    </ul>
  </ul>
  <li>Lichtcontroller: </li>
  <ul>
    <li>ESP32 op LichtSensorController -> RaspberryPi broker -> NodeRED</li>
    <ul>
      <li>Topics: farm/x/pomp/water OF farm/x/pomp/nutrients</li>
      <li>Topics: farm/x/lichtsensor/level/y => y = level 1,2 OF 3</li>
      <li>Er worden Strings gestuurd die het aantal lux doorgeeft dat de sensor meet</li>
    </ul>
  </ul>
</ol>

### Flowchart
  
  ![image](https://ap-it-gh.github.io/ssys21-docs-labfarm/Images/MQTTDiagram.jpg)

### Specificaties

| HTTP        |MQTT   |
| ----------- | ----------- |
| Vrij zwaar protocol: de header van een package is al groter dan 1 bericht van MQTT (min +- 26 bytes header vs enkele bytes MQTT message) | Weinig data → meer keuzes op fysieke laag, trage links worden mogelijk |
| Software stack / Software stack / Library Library is vrij zwaar heeft een zeer kleine footprint | Lightweight → protocol last ook in kleine devices, sensors.. met weinig geheugen & cpu power. |
| Geen ingebouwde Standaard enkele QoS mogelijkheden| Standaardisatie, compatibilieit → elk device kan hetzelfde protocol gebruiken → MQTT bouwt verder op de TCP/IP stack |
| | Vereenvoudiging → bij complexe configuraties (zie principe MQTT) |

=> Er gaat gebruik worden gemaakt van MQTT omdat dit protocol gemaakt is om kleinere bytes aan data door te sturen en dit makkelijk te implementeren is in de opstelling.

### IOT Dashboard/Platform

**We hebben een platform nodig om:**

- Verzamelde data weer te geven
- Controle opdrachten te sturen
- Automatisatie programma's te beheren

|Node-RED|Thingsboard|Freeboard.io|
| ----------- | ----------- | ----------- |
| Open-source | Open-source+ professional(betalend) | Open-source |
| Flows | Entities |  |
| no API | API |  |
| Supports MQTT out of the box | Supports MQTT out of the box | Does not support MQTT out of the box (Not actively developed Plugin available) |
| Makkelijk om snel data te kunnen verwerken naar een dashboard aan de hand van flows | Eerder gemaakt voor professionele klanten, werkt met verschillende entities voor apparaten en klanten. |  |

=> Er wordt Node-Red gebruikt omdat dit ingebouwde MQTT support heeft (Wat Freeboard.io niet heeft) en omdat dit op maat is van het project (Thingsboard zou te uitgebreid zijn)

## Beschrijving van de mogelijke interfaces
![image](https://raw.githubusercontent.com/AP-Project-Analysis-2IT-IOT-1TVT-IOT/Luca-Jelte/main/BlokDiagrammen/DFD%20interface.png)

In bovenstaand dataflow diagram ziet men het interface en de flow van data tussen zichzelf en alle subsystemen. Via het node red interface kan men alle binnenkomende data bekijken op een makkelijke en gebruiksvriendelijke manier. Men kan ook de uitgaande data op bepaalde manieren manipuleren. Bijvoorbeeld het XY-systeem manueel laten langsgaan om foto's te maken.

### NodeRED Editor View
![image](https://user-images.githubusercontent.com/91600019/146913720-16b7405d-04fb-4f1d-abab-c27d51c1804f.png)
[5]

### NodeRED UI
![image](https://user-images.githubusercontent.com/91600019/146913785-c37c27c9-7c5a-4eb9-8020-5b3c3a8c6749.png)
[5]


## Beschrijving van eventuele datamigratie
![image](https://raw.githubusercontent.com/AP-Project-Analysis-2IT-IOT-1TVT-IOT/Luca-Jelte/main/BlokDiagrammen/dataflow.drawio.png)

In bovenstaand dataflow diagram ziet men de datamigratie van de Raspberry Pi tussen alle subsystemen. De lichtsensoren meten een bepaald aantal lux en het LED controller system verstuurt dit als string. De "water related" sensoren zijn PH, temperatuur en water level. De camera neemt periodiek een aantal foto's die naar het NodeRED systeem worden doorgestuurd. De LEDs worden aangestuurd met simpele on/off signalen naar het betreffende level. De stappenmotoren krijgen een bestemming aan. De Pi stuurt de nodige data om alles aan te sturen.


## Beschrijving van eventuele impact op de huidige infrastructuur

### Op hardware niveau

- De kasten gaan aanpassingen krijgen om de kabels goed weg te steken.
- Alle PCB's zullen opnieuw gemaakt worden.
- Alle microcontroller's zullen veranderd worden naar ESP32.

### Op software niveau

- De Pi webserver moet genoeg opslag hebben om de foto's op te slagen.
- De NodeRED pagina moet de motoren kunnen laten zien.
- De gebruiker moet het xy systeem manueel kunnen laten rondgaan.


## Analyse van security en eventuele autorisatierollen

Op basis van security kan er niet veel worden aangepast. Het WiFi netwerk waar data over wordt verstuurd is beveiligd en de Pi webserver is enkel op afstand toegankelijk via het NodeRED interface. Men moet op het lokale netwerk kunnen inloggen om dit te bereiken.

De security zou verbeterd kunnen worden door bijvoorbeeld een aantal logins te bewaren om het interface van de kast achter een passwoord te steken.
Het loginsysteem kan dan bijvoorbeeld admin rollen, read only rollen en read/write rollen bevatten. Deze worden hieronder licht uitgelegd.

#### Eventuele autorisatierollen:

#### Admin
- Heeft rechten om alles aan te passen.
-	Beveiligd met wachtwoord.
-	Kan het automatisatieproces aanpassen via parameters.

#### Standaard Gebruiker
-	Kan alles zien maar niets aanpassen/beïnvloeden.
-	Geen toegang tot knoppen of andere invoer.
-	Kan het automatisatieproces niet beïnvloeden.


## Documentatie

- In de code worden regels voorzien van nodige en nuttige commentaar. Dan kan men deze makkelijk lezen en/of aanpassen.
- Er wordt na finale werking een handleiding opgesteld voor toekomstige gebruikers.


## Bronvermelding

[1]:
Wimme, D. G., & Leander, L., & Andres, D. (2021).
https://ap-it-gh.github.io/ssys21-docs-labfarm/#/MDFiles/Probleemstelling?id=deelproblemen

[2]:
Wimme, D. G., & Leander, L., & Andres, D. (2021).
https://ap-it-gh.github.io/ssys21-docs-labfarm/#/MDFiles/Modular/kast

[3]:
Wimme, D. G., & Leander, L., & Andres, D. (2021).
https://ap-it-gh.github.io/ssys21-docs-labfarm/#/MDFiles/Hardware_analyse/3D-Ontwerpen

[4]:
Wimme, D. G., & Leander, L., & Andres, D. (2021).
https://ap-it-gh.github.io/ssys21-docs-labfarm/#/MDFiles/Hardware_analyse/3D-Ontwerpen

[5]:
Wimme, D. G., & Leander, L., & Andres, D. (2021).
https://ap-it-gh.github.io/ssys21-docs-labfarm/#/MDFiles/SoftwareGuide
