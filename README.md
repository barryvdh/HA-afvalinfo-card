# HA-afvalinfo-card
Diverse lovelace cards voor de [Afvalinfo](https://github.com/heyajohnny/afvalinfo "Afvalinfo") integratie voor Home Assistant.

Afvalinfo ondersteunt verreweg de meeste gemeenten in Nederland (zie [Afvalinfo](https://github.com/heyajohnny/afvalinfo "Afvalinfo") welke).
Maar levert je enkel de nodige sensoren. Je zult dus zelf hier een lovelace card voor moeten maken of een automatisering om bv een push bericht te ontvangen de dag voordat het afval naar buiten moet.
In deze repo probeer ik enkele lovelace cards en automatiseringen te verzamelen om direct te gebruiken of ter inspiratie.
Om alles zo makkelijk mogelijk te maken heb ik ervoor gekozen om alles zodanig te maken dat het meeste door simpelweg te copy/pasten zal werken.
Zo maakt de afvalinfo integratie bijvoorbeeld gebruik van een ID die je in de (optioneel) configuratie kunt opgeven.
Hierdoor krijgen de sensors een niet universele benaming waardoor het veel code en aanpassingen nodig heeft om te functioneren.
Om dit op te vangen wordt gebruik gemaakt van wildcards.
Meer details hierover verder in deze handleiding.

Heb je zelf een mooie card of automatisering of variatie gemaakt maak hier gerust een PR voor aan dan zal ik deze in de lijst opnemen.
Belangrijk hierbij is dat dit zo universeel mogelijk moet werken door gebruik te maken van dezelfde wildcards etc zodat het voor eindgebruikers zo makkelijk mogelijk is om alles werkend te krijgen.

## Installatie Afvalinfo Integratie

Om te beginnen is uiteraard de Afvalinfo integratie nodig.
Volg de instructie op [Afvalinfo](https://github.com/heyajohnny/afvalinfo "Afvalinfo").

Hieronder volgt een beknopte installatieinstructie:

1. Installeer HACS als je dat nog niet gedaan hebt. Meer informatie en instructies: [HACS](https://hacs.xyz/docs/setup/prerequisites "HACS").
2. Installeer [Afvalinfo](https://github.com/heyajohnny/afvalinfo "Afvalinfo") in HACS
3. Herstart HA
4. Gebruik configuratie zoals in [configuration.yaml](https://github.com/bafplus/HA-afvalinfo-card/blob/main/configuration.yaml "configuration.yaml") in deze repo. Loop even alle regels door en pas in ieder geval je gemeente en adresgegevens aan. Bij elke functie staat een opmerking over het hoe en wat.
5. Herstart HA

Gefeliciteerd! Je hebt nu de afvalintegratie geinstalleerd en heb je 9 sensoren in HA (7 sensoren voor elke afvalsoorten en 2 algemene sensoren voor het afval van vandaag en morgen). Let op! Het kan even duren voordat er data binnenkomt.

## Installatie benodigdheden voor de cards in deze repo
### Installatie lovelace-auto-entities
Om de cards te laten werken en omdat de afvalinfo integratie geen universele benaming van sensoren gebruikt is gebruik gemaakt van een plugin die wildcards ondersteund in lovelace cards. Dit om de code zo simpel mogelijk te houden zodat het vrijwel copy/paste werkt zonder al te veel aan te hoeven passen. Wel zo makkelijk :-)
### Afbeeldingen, iconen en naam sensoren
Alle sensoren hebben dezelfde icoontjes en hebben als naam de naam van de sensor. Middels deze aanpassing wijzen we voor elke sensor een eigen Friendly name, icoon en afbeelding toe zodat wij deze niet overal hoeven aan gte passen in de code maar op 1 centrale plek.
1. In de rootmap van HA (waar configuration.yaml staat) heb je als het goed is een customize.yaml staan. Zo niet maak deze dan aan en open deze in bv File Editor.
2. Copy paste de code van [customize.yaml](https://github.com/bafplus/HA-afvalinfo-card/blob/main/customize.yaml "customize.yaml") in deze repo
3. Controleer goed of alle namen van de sensoren kloppen en pas deze waar nodig aan. Vooral het 3e deel in de sensornaam kan bij jou anders zijn vanwege het ID.  
4. Sla het bestand op.
5. Ga naar je configuration.yaml en zet de volgende code helemaal aan het BEGIN van je yaml. Als hier al "Homeassistant:" dan hoef je alleen de 2e regel toe te voegen.
```yaml
homeassistant:
  customize: !include customize.yaml
```
6. Sla je configuration.yaml op. Dit zorgt ervoor dat je customize.yaml voortaan gebruikt gaat worden in HA
7. ga naar instellingen->instellingen en klik op "controleer configuratie", als deze ok is herstart HA
### Benodigde iconen
1. Open de map WWW in de root van HA (waar ook je configuration.yaml staat) in bv File Editor
2. Maak een map "images"
3. Plaats alle iconen in de map [icons](https://github.com/bafplus/HA-afvalinfo-card/tree/main/icons "icons") in deze map. Dus dat het pad uiteindelijk /www/images/naamvanicoon.png is.




