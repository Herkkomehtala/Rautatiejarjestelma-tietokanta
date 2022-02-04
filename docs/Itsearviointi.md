![self_assesment](uploads/e4189b3056311a08a127234834884256/self_assesment.png)  

# Itsearviointi

**HERKKO MEHTÄLÄ**  

Arvosana: 4,5  
Tehtäväni projektissa:  
* Projektin vaatimusmäärittelyn luominen.  
* Projektin käsitemallin luominen.  
* Relaatiokaavion luominen MySQL Workbenchillä.  
* Testidatan lisääminen tietokantaan.  
* Kyselyiden ja näkymien luominen.  
* Triggerit ja niiden proseduurit.  
* Indeksien luominen.  
* Projektin dokumentointi.  

Projektin alkuun saattaminen vaatimusmäärittelyn jälkeen oli hieman ongelmallista. Tunsin usein aika turhaantuneelta, kun koitin suunnitella näin kattavaa tietokantaa tyhjästä joka ei johtanut mihinkään. Läpimurto tapahtui kun päätin rajata projektin ensin pelkkään matkalippujen hallitsemiseen ja ostoon. Tietokannan pilkkominen pienempiin osiin osoittautui merkittäväksi tekijäksi projektin onnistumisen kannalta.  

Toinen yllättävä ongelma johon törmäsin oli attribuuttejen tietotyyppien valinta. Jouduin usein kikkailemaan erilaisten aikaan liittyvien tietotyyppien kanssa, koska näitä ei pysty yleensä summaamaan keskenään. Läpimurto tähän oli, kun löysin netistä `TIME_TO_SEC()` funktion, jolla pystyin muuttamaan kaikki `TIME` -tietotyypit sekunneiksi, summasin kyseiset sekunnit, ja muutin ne takaisin `TIME` -tietotyyppiin `SEC_TO_TIME()` -funktiolla. Tulevaisuudessa tulen miettimään enemmän attribuuttien tietotyyppejä, jotta voisin välttyä kyseisiltä kikoilta.  

Loppujen lopuksi olen erittäin tyytyväinen minun tietokantaratkaisuun. Työaikaa oli varattu harjoitustyöhön n. 32 tuntia per henkilö, joka on vastaa aika lähelle minun panostamaa aikaa tähän projektiin. Onnistuin saavuttamaan lähes kaikki vaatimusmäärittelyssä esitetyt asiat ja sain luotua toimivan ja oikeaa käyttötapausta kuvaavan tietokantajärjestelmän. Projektin aikana opin huomattavan määrän asioita tietokantajärjestelmistä. Tämän takia arvioisin tämän työn 4,5 arvosanan tasoiseksi.