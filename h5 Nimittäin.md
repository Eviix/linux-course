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


