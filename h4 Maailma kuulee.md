### Kaikki testit tehty käyttäen Yoga Slim 7 Pro 14ACH5, oracle virtualbox 7, Debian 12

# h4 Maailma kuulee
## x) Lue ja tiivistä: Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS
Artikkelissa käydään kaikki oleellinen läpi ja toimii hyvänä oppaana, kun halutaan perustaa virtuaalipalvelin (VPS), käyttäen DigitalOceania ja DNS-nimen määrittämiseen NameCheap-palvelua.
Artikkelissa korostetaa vahvojen salasanojen käytön tärkeyttä, eli aina pitää käyttää hyviä salasanoja, jotka eivät ole helposti murrettavissa. Github tarjoaa näitä palveluita koulutuspakettina opiskelijoille, jolla pääsee tutustumaan ilmaiseksi VPS:ään ja .me-verkkotunnukseen.

## a) Virtuaalipalvelimen hankkiminen
Mietin pitkää, että mitä käyttäisin virtuaalipalvelimen luomiseen. Tarkoitus oli ensiksi käyttää DigitalCoeania, mutta en saanut githubilta vastausta minun education student packin hakemukseen. Päädyin valitsemaan Linoden, sillä se ei maksanut yhtään ja sai vielä $100.00 edestä creditejä.
Ainoa negatiivinen asia mitä sanoisin oli se, että kortin tiedot jäi sivulle, enkä voi niitä poistaa sieltä, joten pitää keksiä joku ratkaisu tuohon, sillä en mielelläni jätä sivustolle kortin tietoja pitkäksi aikaa.


![Add file: Upload](Images/Linonde-plan.JPG)

Aloitin tosiaan valitsemalla Linode planin ja tähän hätään otin kaikista halvimman, eli tuon shared cpu:n ja nanode 1 GB.

![Add file: Upload](Images/Linode-running.JPG)

Linode palvelin on nyt päällä ja seuraavaksi kirjaudun sisään palvelimeen rootina ja tarkistan samalla ip a komennolla, että olen yhteydessä Linoden palvelimeen:
### ssh root@172.105.81.54
### ip a

![Add file: Upload](Images/Root-login.jpg)



