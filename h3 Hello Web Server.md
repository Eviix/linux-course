# x) Tiivistelmä: Karvinen 2006-2022 - Install Apache Web Server on Ubuntu

## Asennus

### $ sudo apt-get install apache2

Tällä komennolla saadaan asennettua Apache 2 -verkkopalvelimen.

## Testaus

###  $ firefox "http://localhost"

Tällä saadaan testattua Apachen toimivuutta.

### $ ip addr

Tällä saadaan selvitettyä miten palvelin on saavutettavissa verkossa.

Esim:

### $ firefox "http://1.2.3.4"

Täyden verkkotunnuksen voi tarkistaa "$ host 1.2.3.4", jos DNS toimii verkossasi.

## Käyttäjä kotisivut

### $ sudo a2enmod userdir
### $ sudo systemctl restart apache2

Tällä mahdollistetaan verkkosisällön luomisen public_html -kansioon.

## Käyttäjän kotisivujen testaus 

Kotihakemistoon pääseminen:

### $ cd

Luodaan kansio niemtlä "public.html":

### $ mkdir public_html

Käyttäjänimen tarkistaminen: 

### $ whoami

Lopuksi avataan Käyttäjäsi kotsisivu muodossa "http://localhost/~kayttajanimi/".

# a) Apache asennus






