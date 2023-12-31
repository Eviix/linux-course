### Kaikki testit tehty käyttäen Yoga Slim 7 Pro 14ACH5, oracle virtualbox 7, Debian 12
Processor: AMD Ryzen™ 5 5600H (6C / 12T, 3.3 / 4.2GHz, 3MB L2 / 16MB L3)

Graphics: Integrated AMD Radeon™ Graphics

Chipset: AMD SoC Platform

Memory: 16GB Soldered DDR4-3200

Memory Slots: Memory soldered to systemboard, no slots, dual-channel

Max Memory :16GB soldered memory, not upgradable

Storage: 512GB SSD M.2 2280 PCIe® 3.0x4 NVMe®

# h7 Hello world

## x) Kaikki läksyt tähän

- Viikko 1: https://github.com/Eviix/linux-course/blob/main/h1-oma-linux.md
- Viikko 2: https://github.com/Eviix/linux-course/blob/main/h2%20Komentaja%20Pingviini.md
- Viikko 3: https://github.com/Eviix/linux-course/blob/main/h3%20Hello%20Web%20Server.md
- Viikko 4: https://github.com/Eviix/linux-course/blob/main/h4%20Maailma%20kuulee.md
- Viikko 5: https://github.com/Eviix/linux-course/blob/main/h5%20Nimitt%C3%A4in.md 
- Viikko 6: https://github.com/Eviix/linux-course/blob/main/h6%20DJ%20Ango.md

## y) Lue ja tiivistä

### Karvinen 2018: Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04

- "Hello, World!" on yksinkertainen ohjelma ja se on yleensä ensimmäinen asia, joka opetetaan millä tahansa ohjelmointikielellä ja sillä saadaan testattua myös, että ohjelmointiympäristö toimii oikein.
- Toimiva Hello, World! muutamalla eri ohjelmointikielellä:

Python3:
````
$ cat hellotero.py
print("Hello Tero")
$ python3 hellotero.py
Hello Tero
````
Bash:
````      
$ cat hellotero.sh
echo "Hello Tero"
$ bash hellotero.sh
Hello Tero
````
C:
````
$ cat hellotero.c
#include <stdio.h>
int main()
{
printf("Hello Tero\n");
}
$ gcc hellotero.c -o helloteroc
$ ./helloteroc
Hello Tero
````
- Tästä voidaan nopeasti päätellä, että Python3 ja Bash vaatii vähemmän riviä koodia kuten esim. C.

Lähde: Karvinen 2018: https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/ Luettu 08.10.2023

## a) Käännä "Hei maailma" Pythonilla, Javalla ja C-kielellä.

- Lähdin tekemään tehtävää ensiksi komennolla: ````$ sudo apt-get update````, jotta kaikki paketit olisivat ajan tasalla.
- Asensin alkuun ohjelmistöympäristön, joka tukee python3 ja javaa ````$ sudo apt-get install -y ipython3 openjdk-17-jdk```` sillä sitä ei ole sisäänrakennettu linuxiin toisin kuin C.
- Asennus oli melko laaja ja siinä meni itselläni hetki, mutta asennuksen jälkeen sain käynnistettyä sen ````$ ipython3````
![Add file: Upload](Images/ipython3.jpg)
- Testasin vielä, että javan ohjelmistoympäristö asentui ````$ javac````
![Add file: Upload](Images/javac.jpg)

- Nyt päästään varsiniaseen tehtävään. Kokeilin ensiksi pythonilla, että miten hello world toimii. Käytin micro tekstieditoria ja loin sillä helloworld.py nimisen tiedoston ````($ micro helloworld.py)````.
````
$ cat helloworld.py
------------------
print("Hello, World!")
------------------
$ python3 helloworld.py
Hello, World!
````
![Add file: Upload](Images/helloworld_python.jpg)

- Seuraavana vuorossa javan kokeilu ````($ micro HelloWorld.java)````:
````
$ cat HelloWorld.java
------------------   
public class HelloWorld
{
 public static void main(String[] args)
 {
 System.out.println("Hello, World!");
 }
}
------------------
$ javac HelloWorld.java
$ java HelloWorld   
Hello, World!
````
![Add file: Upload](Images/javac_testing.jpg)
- Lopuksi siirryin C:n kokeiluun ````($ micro helloworld.c)````:
 ````
$ cat helloworld.c
------------------
#include <stdio.h>
int main()
{
  printf("Hello, World!\n");
}
------------------
$ gcc helloworld.c -o helloworldc 
$ ./helloworldc
Hello, World!
````
![Add file: Upload](Images/c_test.jpg)

## b) Käännä "Hei maailma" jollain muulla kielellä (kuin Python, Java, C).
- Päätin kokeilla rubya tässä osiossa, eli aloitin normaaliin tapaan luomalla tekstitiedoston ````($ micro helloworld.rb)````:
````
$ cat helloworld.rb
------------------
puts "Hello, World!"
------------------
$ ruby helloworld.rb
Hello, World!
````
- Tässä vaiheessa huomasin, että rubya ei ollut ollenkaan olemassa linuxissa, joten asensin sen komennolla ````$ sudo apt-get install ruby-full````.

![Add file: Upload](Images/ruby_test.jpg)
- Loppukommentiksi voisin sanoa, että ruby muistutti paljon pythonia lyhyen koodin takia. En ollut siis ennen rubya käyttänyt.

## c) Python laskin.

- Olin heti alussa tehnyt jo pythonin asennuksen komennolla: ````$ sudo apt-get install -y ipython3 openjdk-17-jdk````, joten se löytyi minulta jo ennastaan. ````$ ipython3```` käynnisti ohjelman.
![Add file: Upload](Images/ipython3_test.jpg)

## d) Tee shell script
- Aloitin tehtävän tekemällä kotihakemistoon uuden kansion nimeltä "scripts":
````
cd
mkdir scripts
cd scripts
````
- Tämän jälkeen loin microlla uuden tekstitiedoston nimeltä update.sh ja loin sinne uuden scriptin.
````
#!/bin/bash

echo "Päivitetään pakettilista..."
sudo apt update
echo "Pakettilista päivitetty."
echo "Skripti suoritettu loppuun."
````
- Koitin suorittaa skriptin komennolla ````$ ./update.sh````, mutta sillä ei ollut oikeuksia suorittaa sitä.
````
chmod +x update.sh
````
- Nyt skripti toimii niin kuin halusinkin.
![Add file: Upload](Images/sh_test.jpg)

## e) Tee uusi komento Linuxiin
- Hyödynsin tässä tehtävässä d) kohdassa tehtyä skriptiä. Varmistin ensiksi, että minulta löytyy ````/usr/local/bin````.

- Tämän jälkeen loin microlla uuden tekstitiedoston nimeltä update.sh ja loin sinne uuden scriptin.

````
cd /usr/local/bin
ls (kansiossa ei ollut vielä mitään)
````
- Tämän jälkeen tein kopion ````/scripts/update.sh````, jonka halusin siirtää ````/usr/local/bin```` ja annoin sille samalla oikeudet.
````
sudo cp ~/scripts/update.sh /usr/local/bin/
sudo chmod +x /usr/local/bin/update.sh
````
- Tämän tehtyä pystyin ajamaan update.sh komentoa suoraan omasta kotihakemistosta.

![Add file: Upload](Images/uusi_komento.jpg)

## f) Intelligent intelligence

- Päätin tässä ottaa ensimmäisen labra harjoitustyön, joka tuli kohdalleni: [syksy -21](https://terokarvinen.com/2021/final-lab-for-linux-server-course-linux-palvelimet-ict4tn021-3016/)
- Alottaisin tämän komennoilla ````sudo apt-get update```` ja ````sudo apt-get upgrade````.
- Lisätään käyttäjä ja annetaan sille sudo oikeudet: ````sudo adduser daniel```` ja ````sudo adduser daniel sudo````.
- Siirryin kotihakemistoon ````cd```` ja loin lab.txt tiedoston --> micro lab.txt (oletan, että microa ei olla vielä asennettuna, joten ````sudo snap install micro --classic````).
````
Nimi: Daniel
Linkki kotitehtäväpakettiin: ----------
````
- Asentaisin pwgenin: ````sudo apt install -y pwgen````. Tämän jälkeen voisin kirjoittaa, vaikka ````pwgen -s 20 10````, joka loisi 10 salasanaa, jotka ovat 20 merkkiä pitkiä.
- Jos haluaisin suojata lab.txt tiedoston, niin tekisin näin: ````chmod 600 lab.txt````. Tämä antaa oikeudet vain tiedoston omistajalle eikä ulkopuoliset voi lukea sitä.

## f) Labra Debian 12

- Asensin labraa varten uuden Debian 12, johon en ollut tehnyt mitään, joten kyseessä oli täysin tyhjä virtuaalikone.
  

![Add file: Upload](Images/labra_debian12.jpg)

## Lähteet: 
- Karvinen 2018: https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/ Luettu 08.10.2023
