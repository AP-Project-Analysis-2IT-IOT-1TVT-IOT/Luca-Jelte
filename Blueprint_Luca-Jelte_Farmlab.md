# Farmlab



AP Hogeschool<br>
Luca Van Laer en Jelte Boumans

## Opdrachtgever
Maarten Luyts: Productowner en projectbegeleider.

## Samenvatting

Het Farmlab is een project voor IoT studenten van het 2e jaar. Er wordt verder gebouwd op vorige iteraties. *Momenteel bouwen wij verder op de vierde iteratie. 

Het Farmlab is een kast met 3 niveau’s. Op elk niveau groeien planten via hydrocultuur. Dit houd in dat de wortels van de planten niet in de grond zitten, maar direct in water liggen. Doormiddel van voedingsstoffen in het water kunnen ze verder groeien. Op deze wijze kan men landbouw in de hoogte uitbreiden.

De onderdelen van de kast worden volledig geautomatiseerd zodat ze remote kunnen worden gecontroleerd, bestuurd en gescheduled.
## Situatie As-Is

Momenteel werken we aan de vierde iteratie van de kast. Al de documentatie van de vorige groepen/iteraties kan men hier vinden:

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

In grote lijnen wilt men versie 3 van het Farmlab:
- Gebruiksvriendelijker maken
- Automatiseren

*Tekst uit https://ap-it-gh.github.io/ssys21-docs-labfarm/#/MDFiles/Probleemstelling?id=deelproblemen*<br>
*Tekst uit https://ap-it-gh.github.io/ssys21-docs-labfarm/#/README*



## Situatie To-Be

In iteratie vier legt men de probleemstellingen van versie vier bloot om ze verder te verwerken. Dit houdt in dat de verschillende onderdelen waaruit de kast is opgebouwd verder worden verfijnd en geoptimaliseerd. Zo kan de kast voor een periode van 1 maand zelfstandig werken met remote besturing. 

De drie onderdelen zijn: 
<ul>
  <li>Pomp controller</li>
  De pomp controller moet in staat zijn om het water op het gepaste moment rond te pompen. Zo vermijd men dat er algen of andere planten in het water groeien. Dit proces moet     geautomatiseerd worden om te vermijden dat de gebruiker de pomp manueel moet aanzetten.
  <li>LED Controller/Lichtsensor</li>
  De LED controller moet in staat zijn om een gepast aantal en soort licht te produceren voor de specifieke planten. 
  <li>XY-Systeem</li>
  Het XY-systeem bevindt zich aan de achterkant van de kast. Dit systeem kan aan de hand van een camera en AI image processing herkennen in welk groeistadium een plant is.         Optioneel kan deze plant ook worden geoogstd. Met deze informatie kan men de pomp aansturen of de belichting aanpassen. Momenteel is het XY-systeem op de kast gemonteerd en     kan het bewegen binnen het XY-vlak. Er is een camera aanwezig maar geen AI systeem.
</ul>  

Van de vijf onderdelen moeten de PCBs herwerkt worden. Deze moeten gebruik maken van ESP32 in de plaats van ESP12. Het management van kabels moet worden herbekeken en verbeterd. 
Via standardisatie kan men alle onderdelen makkelijk namaken om kopieën van de kast te maken.



### Projectdefinitie
## Planning
- Kanban
- Wekelijks resultaten leveren
- Elke donderdag samen 3 uur werken
- Doorheen de week individueel werken
- Tools: Office Word, Github


| Hoofdlijnen |  Datum      | Student    |
| ----------- | ----------- |----------- |
| Opmaak blueprint| 2 Dec       |Luca Van Laer|
| As is / To be| 2 Dec      |Jelte Boumans|

## Planning uitvoering (2de semester)

## Functioneel design

### kast
![image](https://user-images.githubusercontent.com/91600019/144228425-952029da-4239-4ce4-bf58-538cb70fdf7a.png)
### kast ontwerp
![image](https://user-images.githubusercontent.com/91600019/144228812-acda100e-8fd4-431b-b07b-b1d94918728a.png)

### schema
![image](https://user-images.githubusercontent.com/91600019/144229006-644931ab-e276-4dd6-99b1-0a40964e349c.png)


De kast bestaat uit verschillende onderdelen:

<ol>
  <ul>
      <li>LED Controller</li>
      <li>Lichtsensor</li>
      <li>Pomp controller</li>
      <li>XY-Systeem</li>
  </ul>
</ol>

Deze onderdelen worden in het technisch design verder uitgepunt.


## Technisch design
### Smart Object (Hardware Analyse)
### Smart Object (Software Analyse)
## Beschrijving van de mogelijke interfaces
## Beschrijving van eventuele datamigratie
## Beschrijving van eventuele impact op de huidige infrastructuur
## Analyse van security en eventuele autorisatierollen
## Documentatie
## Bronvermelding
