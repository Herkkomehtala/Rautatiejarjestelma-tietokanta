# Vaatimusmäärittely
![project_header](uploads/f66130cee1e1cbc289dc645dad96a2ba/project_header.png)

**Työryhmä**  

* Mehtälä Herkko, TTV20S2  

## Sisällysluettelo

1. [Johdanto](#johdanto)  
2. [Yleiskuvaus](#yleiskuvaus)  
3. [Toiminnot](#toiminnot)  
4. [Muut ominaisuudet](#muut-ominaisuudet)


### Johdanto

Projektin tavoitteena on luoda asiakkaalle rautatiejärjestelmän tietokanta. Työntilaaja vaati kattavan junahallintajärjestelmän tietokannan, joka tarkoittaa, että tietokannassa tulee huomioida sekä junat, huoltoraportit, matkustukset, henkilöstöt, liput ja rahtitavarat. Projektin tietokanta on rajattu niin, että sillä ei voi hallita rautatieverkkoa vaan korkeintaan valvoa sitä.    

### Yleiskuvaus

Ensimmäiseksi toteutetaan järjestelmän tarvitsema tietokanta, jonka jälkeen sinne lisätään testaukseen tarvittava data. Tietokanta toteutetaan 'MySQL Workbench' -ohjelmistolla. Tietokantajärjestelmä sijoitetaan lopulta JAMK:in tietokantapalvelimelle. Oikeudet tietokantaan määritellään tietokantaohjelmiston omilla toiminnoilla.  

### Toiminnot

Pakolliset toiminnot ovat:  

1. Työntilaaja pystyy hakemaan tietoa junayhtiön junista, henkilökunnasta ja junaliikenteestä. 
2. Käyttäjä pystyy hakemaan tietoja omasta lipustaan, lippuhistoriasta ja omat käyttäjätiedot.     
3. Henkilökunta pystyy hakemaan tietoja junamatkasta kuten lähtemis- ja saapumisasemat ja kuinka kauan matka kestää.  
4. Tietokannasta voidaan hakea junamatkan lastiluettelo.  
5. Tietokannasta voidaan hakea junamatkojen henkilökunta ja matkustajat.  
6. Tietokannasta voidaan laskea henkilökunnan työtunnit.

Tärkeät toiminnot ovat:  

1. Junayhtiöt voivat hakea tietyn junan kaikki matkatunnit.  
2. Tietokannasta voidaan tarkastella junien huoltoraportteja tietyltä aikaväliltä.
3. Voidaan valvoa tietylle asemalle tulleita rahtitavaroita. 

**Tietokannan käyttötavat**

- Kuluttaja: Kuluttaja voi hakea tietoa omista matkalipuistaan, junamatkoista, matkakohteista ja omasta matkahistoriasta.  

- Junayhtiöt: Voivat kysyä tietoa junistaan, niiden huoltoraporteista, sekä matkojen henkilöstöstä.  

- Rautatieliikenneseuranta: Seurannalla voidaan lukea asemien rautatieliikennettä ja niiden kautta kulkevasta rahtitavarasta.  

**Ulkoiset liittymät**  
- Baliisi kulunvalvonta komponentit.  
- Junien liikenteenohjausjärjestelmät.  
- 'European Train Control System' tulevaisuudessa.  

### Muut ominaisuudet

**Suorituskyky**  
- Vasteajat tyypillisellä tietokoneella (Windows 10, jossa 4GB RAM ja 3 GHz:n prosessori n. 10000 rivin tietomäärällä) alle 1 sekuntti. Tällä mahdollistetaan, että tietokanta toimisi mahdollisimman reaaliaikaisesti.  

**Tietoturva**  
- Tietokanta tulee luoda tavalla, jotta lopullisessa toteutuksessa kuluttajien, yhtiöiden, lastiluettelojen ja lippujen data voidaan salata. Tietokannassa tulee olla jaetut oikeudet ja mahdollistetaan tietokannan varmuuskopiointi.  

**Siirrettävyys**  
- Tietokanta rakennetaan siten, että sen voi siirtää palvelimelta toiselle esimerkiksi kloonaamalla käyttämällä MySQL Workbench 'Migration' -työkalua.  

**Ylläpidettävyys**  
- Ajan tasalla oleva järjestelmädokumentaatio.  
- Vaatimusmäärittelydokumentti.  
- ER-kaavio ja rajoitusten tarkka kartoitus.  
- Järjestelmän testaus ja päivitys.  

**Käytettävyys**  
- Tietokannan kehityksen aikana suoritetaan asiakaskuuleminen jolla kehitetään järjestelmän käytettävyyttä.  




