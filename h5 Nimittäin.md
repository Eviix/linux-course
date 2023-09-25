### Kaikki testit tehty käyttäen Yoga Slim 7 Pro 14ACH5, oracle virtualbox 7, Debian 12
Processor: AMD Ryzen™ 5 5600H (6C / 12T, 3.3 / 4.2GHz, 3MB L2 / 16MB L3)

Graphics: Integrated AMD Radeon™ Graphics

Chipset: AMD SoC Platform

Memory: 16GB Soldered DDR4-3200

Memory Slots: Memory soldered to systemboard, no slots, dual-channel

Max Memory :16GB soldered memory, not upgradable

Storage: 512GB SSD M.2 2280 PCIe® 3.0x4 NVMe®

# h5 Nimittäin

## x) Lue ja tiivistä: 
### New Default Website with Apache2 – Show your homepage at top of example.com, no tilde

Apache2 asennus:
```
$ sudo apt-get update
$ sudo apt-get -y install apache2
```
Apachesta on hyvä tietää se, että se voi pyörittää useaa virtuaalipalvelinta samanaikaisesti ja ne pystytään määritellä polussa "http://etc/apache2/sites-available/"

Uusi virtuaalipalvelin voidaan luoda seuraavasti:

Esimerkki: sudoedit /etc/apache2/sites-available/daniel.conf 
```
<VirtualHost *:80>
  DocumentRoot /home/daniel/public_html/
  <Directory /home/daniel/public_html/>
    Require all granted
  </Directory>
</VirtualHost>
```
Se saadaan otettua käyttöön seuraavalla komennolla: "sudo a2ensite tero.conf"

Nyt voidaan siirtyä kotisivun luomiseen:
```
Kotihakemistoon siiryminen tapahtuu "cd" komennolla.
Public_html-hakemisto: mkdir public_html/
Siirtyminen sinne tapahtuu: cd public_html/
Lopuksi luodaan index.html --> muokkaamiseen voidaan käyttää nano komentoa, eli "nano index.html".
Nyt voidaan mennä kotisivuille localhostin kautta ja se voidaan validoida sivulla: https://validator.w3.org/
```

### Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address
Käytännössä sama logiikka kuin edellisessä artikkelissa.

Lisäämällä rivejä "sudoedit /etc/hosts", nimipalveluida voidaan tällä simuloida.
### Name-based Virtual Host Support
- IP-pohjaisessa virtuaalipalvelussa jokaiselle palvelimelle tarvitaan oma IP-osoite, kun taas nimipohjaisessa virtuaalipalvelussa useat eri palvelimet voivat jakaa saman IP-osoitteen.
- Palvelimelle saapuvat pyynnöt käsitellään ensin IP-osoitteen ja portin perusteella, sitten verrataan ServerName- ja ServerAlias-ohjeita.

## a) Domain-nimi  
Ensiksi menin NameCheap sivustolle ja vuokrasin itselleni domain-nimen. Github education tarjoaa vuodeksi ilmaisen domainin, joten hyödynsin tämän tarjouksen.

![Add file: Upload](Images/Domain_name.JPG)

Seuraavaksi siirryin NameCheap sivun Advanced DNS -välilehdelle, jossa pystyin lisätä kaksi uutta recordia. Lisäsin www & @ ja annoin niille IP-osoitteen ja samalla TTL (time to live)-ajaksi 1-min.

![Add file: Upload](Images/Advanced_DNS.JPG)

Kuvasta huomaa, että käytin samaa IP-osoitetta, joka löytyy Linoden palvelimesta:

![Add file: Upload](Images/Linode-running.JPG)

Tämän jälkeen tein kaikki muutokset mitä tein myös viime viikon tehtävässä "[h4 Maailma kuulee](https://github.com/Eviix/linux-course/blob/main/h4%20Maailma%20kuulee.md)".

Aivan alkuun kirjauduin viime viikolla tehtyyn käyttäjään --> ssh daniel@182.105.81.54 ja tein tarvittavat toimenpiteet palvelimen luomiseen:
```
sudo apt-get update
sudo apt-get install ufw apache2 
```
Tämän jälkeen tein porttien avauksen SSH:ta ja HTTP:tä varten, sekä laitoin palomuurin päälle:
```
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp 
sudo ufw enable
```

index.html, jonka loin viime viikon tehtävässä pitäisi nytten toimia domain-nimellä:

![Add file: Upload](Images/Danielin_sivu.JPG)

## b) host- ja dig-analyysi

En ollut ennen perehtynyt host ja dig komentoihin, joten aivan alkuun käytin man host & man dig komentoa. Lyhyesti voitaisi sanoa, että niitä käytetään domain-nimen ja niiden DNS-tietojen tarkasteluun ja kyselyyn.

Ensiksi kokeilin host komentoa:
```
host danielristikari.me
```
Sain ainakin selville, että mitä IP-osoitetta danielristikari.me sivusto käyttää, sekä sähköpostipalvelimien osoitteita.

![Add file: Upload](Images/Host-komento.jpg)

Seuraavaksi kokeilin dig komentoa:

```
dig danielristikari.me
```
Sain tästä ainakin selville sen, että IP-osoite on 172.105.81.54 ja Kysely kesti 8 millisekuntia. Tajusin myös sen, että se suoritettiin palvelimelta "139.162.130.20", jossa käytettiin UDP-protokollaa. NOERROR liittyi siihen, että kyselyssä ei tullut mitään virheitä.

![Add file: Upload](Images/Dig_komento.jpg)

## c) Etusivu uusiksi
Päivitin ensiksi paketit jonka jälkeen loin VirtualHostin --> sudoedit /etc/apache2/sites-available/daniel.conf
```
<VirtualHost *:80>
 DocumentRoot /home/daniel/public_html/
 <Directory /home/daniel/public_html/>
   Require all granted
 </Directory>
</VirtualHost>
```
Tämän jälkeen tarkistim, että se löytyy oikeasta paikasta

![Add file: Upload](Images/Tarkastus_conf.jpg)

Seuraavaksi otin käyttöön VirtualHostin komennolla:
```
sudo a2ensite daniel.conf
```
Otin myös vanhan pois päältä:
```
sudo a2dissite 000-default.conf
```
Lopulta käynnistin palvelimen uudelleen:
```
sudo service apache2 restart
```

Sain virheilmoituksen, kun koitin tehdä sudo a2ensite daniel.conf & sudo a2dissite 000-default.conf:
```
sudo a2ensite daniel.conf
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_ADDRESS = "fi_FI.UTF-8",
	LC_NAME = "fi_FI.UTF-8",
	LC_MONETARY = "fi_FI.UTF-8",
	LC_PAPER = "fi_FI.UTF-8",
	LC_IDENTIFICATION = "fi_FI.UTF-8",
	LC_TELEPHONE = "fi_FI.UTF-8",
	LC_MEASUREMENT = "fi_FI.UTF-8",
	LC_TIME = "fi_FI.UTF-8",
	LC_NUMERIC = "fi_FI.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
Site daniel already enabled
```

## Lähteet:
Karvinen 2016: https://terokarvinen.com/2016/02/16/new-default-website-with-apache2-show-your-homepage-at-top-of-example-com-no-tilde/ Luettu 24.9.2023

Karvinen 2018: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ Luettu 24.9.2023

Apache Software Foundation 2023: https://httpd.apache.org/docs/2.4/vhosts/name-based.html Luettu 24.9.2023

https://www.namecheap.com/



