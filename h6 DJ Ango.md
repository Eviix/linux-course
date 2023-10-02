### Kaikki testit tehty käyttäen Yoga Slim 7 Pro 14ACH5, oracle virtualbox 7, Debian 12
Processor: AMD Ryzen™ 5 5600H (6C / 12T, 3.3 / 4.2GHz, 3MB L2 / 16MB L3)

Graphics: Integrated AMD Radeon™ Graphics

Chipset: AMD SoC Platform

Memory: 16GB Soldered DDR4-3200

Memory Slots: Memory soldered to systemboard, no slots, dual-channel

Max Memory :16GB soldered memory, not upgradable

Storage: 512GB SSD M.2 2280 PCIe® 3.0x4 NVMe®

# h6 DJ Ango

## x) Lue ja tiivistä: 
### Karvinen 2023: Python Web - Idea to Production - 2023

- Python weppipalvelu - ideasta tuotantoon toteutuksella pääsee rakentamaan weppipalvelu Pythonilla ja myös asentamaan sen julkiselle palvelimelle.
- Se pystyy palvelemaan asiakkaita usealla eri laitteella moiteettomasti.
- Käyttäjien ei tarvitse asentaa mitään.
- Yhtäaikainen muokkas mahdollisuus käyttäjillä.
- Aina uusin versio automaattisesti käytössä.

### Karvinen 2022: Django 4 Instant Customer Database Tutorial

- Opitaan luomaan asiakastietokannan web-käyttöliittymällä käyttäen Django 4.
- Aluksi tehdään kehitysympärtön asennukset: asennetaan virtualenv: sudo apt-get -y install virtualenv,
luodaan virtuaaliympäristö: virtualenv --system-site-packages -p python3 env/ ja lopuksi aktivoidaan virtuaaliympäristö: source env/bin/activate
- Asennetaan Django, tämän jälkeen päästään luomaan uusi projekti, jonka jälkeen voidaan käynnistää kehityspalvelin seuraavasti --> ./manage.py runserver
- Tässä vaiheessa voidaan siirtyä admin-käyttöliittymän asennukseen, joka onnistuu seuraavasti --> avataann admin-käyttöliittymä: http://127.0.0.1:8000/admin/, päivitetään kaikki tietokannat: ./manage.py makemigrations ja ./manage.py migrate ja lopuksi luodaan superkäyttäjä ./manage.py createsuperuser.
- Lopuksi voidaan luoda uusia käyttäjiä ja asiakastietokantoja.

### Karvinen 2022: Deploy Django 4 - Production Install

- Opitaan julkaisemaan Python Djangolla luotuja verkkosovelluksia internetissä oikealla tuotantopalvelimella Apache 2.4:llä ja mod_wsgi:n avulla.
- Vaaditaan, että perustaidot terminaalinkäytöstä on hallussa.

### a) Asenna Django-kehitysympäristö

- Aloitin tehtävän seuraamalla Teron tehtyjä ohjeita, jotka löytyvät https://terokarvinen.com/2022/django-instant-crm-tutorial/
- Ohjeiden lukemisen jälkeen tein ensimmäisen toimeenpiteen, eli latasin Djangon:
```
$ sudo apt-get -y install virtualenv
$ virtualenv --system-site-packages -p python3 env/
```

![Add file: Upload](Images/Django_install.jpg)

- Tässä vaiheessa on hyvä tietää, että pipiä ei kannata käyttää sudo-komennon kanssa, sillä se voi aiheuttaa turvallisuusongelmia ja käyttöoikeusongelmia.  
- Nyt voimme siirtyä uuteen virtuaaliympäristöön ja tehdä sen sisällä tarvittavat asennus toimenpiteet:
```
$ source env/bin/activate
$ which pip /home/daniel/env/bin/pip
```
- Python-paketin lisääminen tekstitiedostoon, sisällön lataaminen ja version tarkastaminen:
```
$ micro requirements.txt
$ cat requirements.txt

$ pip install -r requirements.txt
$ django-admin --version
```
![Add file: Upload](Images/requirements_django.jpg)

Nyt voimme kokeilla toimiiko django seuraavasti:
```
$ django-admin startproject daniel

$ cd daniel
$ ./manage.py runserver
```
- Lopuksi menemme --> http://127.0.0.1:8000/
![Add file: Upload](Images/test_django.jpg)

### b) esimerkkitietokanta ja Django admin-liiyymä

- Jatkoin tehtävää tekemällä ensiksi päivitykset tietokantaan:
```
$ ./manage.py makemigrations
$ ./manage.py migrate
```
![Add file: Upload](Images/Update_database.jpg)

- Seuraavaksi lähdin lisäämään käyttäjää (superkäyttäjä):
```
$ ./manage.py createsuperuser 
```
- Täytin tarvittavat tiedot käyttäjälle ja loin sen, jonka jälkeen pystyin kirjautumaan sisään -> http://127.0.0.1:8000/admin/
![Add file: Upload](Images/Create_superuser.jpg)

- Seuraavaksi vuorossa on asiakastietokannan luominen:
```
## Aloitetaan luomalla crm/ kansio
$ ./manage.py startapp crm
## 'crm' rivin lisääminen
$ micro daniel/settings.py
```
- Modelien lisäys:
```
$ micro crm/models.py
from django.db import models

class Customer(models.Model):
   name = models.CharField(max_length=300)
```
- Tehdään migraatiot:
```
$ ./manage.py makemigrations
$ ./manage.py migrate
```
- Loput admin muutokset:
```
$ micro crm/admin.py
from django.contrib import admin
from . import models

admin.site.register(models.Customer)
```
![Add file: Upload](Images/crm_add.jpg)

- Voimme nyt käynnistää serverin ja nähdä uusi customer model adminissa 
```
$ ./manage.py runserver
```
- Asiakkaan lisämisen jälkeen näkymä näyttää tältä:
![Add file: Upload](Images/customer_add.jpg)

### c) Tee Djangon tuotantotyyppinen asennus omalle, paikalliselle virtuaalikoneellesi



## Lähteet:
Karvinen 2023: https://terokarvinen.com/2023/python-web-idea-to-production/#osaamistavoitteet/ Luettu 02.10.2023

Karvinen 2022: https://terokarvinen.com/2022/django-instant-crm-tutorial/ Luettu 02.10.2023

Karvinen 2022: https://terokarvinen.com/2022/deploy-django/ Luettu 02.10.2023
