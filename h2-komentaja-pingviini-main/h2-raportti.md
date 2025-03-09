### h2 Komentaja-Pingviini

x) ## Tiivistys Command Line Basics Revisited
## peruskäytön komennot
-$ pwd näyttää nykyisen hakemiston

-$ ls näyttää infoa tiedostoista hakemistossa

-$ cd vaihtaa hakemistoa

-$ less näyttää tiedoston yksi sivu kerrallaan
## tiedostojen käsittely
-$ nano ja pico ovat helppoja tekstieditoreja

-$ mkdir luo hakemiston

-$ mv siirtää/nimeää tiedoston tai hakemiston

-$ cp kopio

-$ rm, rm-v poistaa tiedoston/hakemiston 
## etäkäyttö
-$ ssh avaa etäyhteyden 

-$ scp kopio tiedostoja etäyhteydellä
## ohjelmistojen hallinta
-$ sudo spt-get update päivittää pakettitiedot

-$ sudo apt-get install ohjelmien asennus

-$ sudo apt-get purge poistaa ohjelman

## help
-$ wget -h lataa tiedostoja internetistä

-$ man käyttöohje

-$ --help lyhyt ohje

a) ## Micro
![VirtualBoxVM_9JiQXNHuT9](https://github.com/user-attachments/assets/480125a8-1784-4340-902e-9e23baad0973)

Avasin terminaalin ja latasin Micro editorin käyttämällä komentoja
$ sudo apt-get update
$ sudo apt-get install micro
Avasin micron komennolla
$ micro
![VirtualBoxVM_omlpReMCsD](https://github.com/user-attachments/assets/14dce6a7-15c3-404d-a767-3095858b018a)

b) ## Kolme ohjelmaa
Vietin seuraavat 30 minuuttia etsimällä eri ohjelmia ja mitä haluaisin kokeilla käyttämällä komentoa 
$ apt-cache search 
Päädyin lataamaan Doomin, nethack-consolin ja ufo-pelin
![VirtualBoxVM_3Z8PBoCJPJ](https://github.com/user-attachments/assets/9a29e10c-faf4-4b5f-90d2-cee019ca55f9)
![VirtualBoxVM_CvDmPihKBY](https://github.com/user-attachments/assets/ca6ed06c-6c06-4545-b858-ea72a1ea4e7c)
nethack
![VirtualBoxVM_BG9Jjtmiej](https://github.com/user-attachments/assets/d049d017-2bd4-4a51-b2ad-45b467671622)

ufo-peli ei toiminut hyvin, varmaan koska virtualboxin asetukset oli huonosti optimoitu, jonka huomasin myöhemmin.


c)
Tässä kansioita joita tutkin, mutta niissä ei ollut juurikaan mitään ihmeellistä
![VirtualBoxVM_yQx9MDRVkD](https://github.com/user-attachments/assets/27e955d5-0daa-4e1b-8b95-46c695e3e071)
![VirtualBoxVM_pgjnoGT53r](https://github.com/user-attachments/assets/c219fb4b-c7e8-4415-8ed6-017705e27167)
![VirtualBoxVM_Stmk8I4WT5](https://github.com/user-attachments/assets/060f49be-985c-401d-b891-81a11257c036)


d) # The Friendly M

Aloitin tutkimaan grep komentoja Komennolla 
$ man grep
![VirtualBoxVM_bLrRlHXBuJ](https://github.com/user-attachments/assets/d88179b2-6db4-4d42-bc47-20fb98432894)


Loin ensin uuden tiedoston "hedelmät.txt", jota käytin grep komentojen tutkimiseen
![VirtualBoxVM_HxYivLbmbs](https://github.com/user-attachments/assets/6b77f25e-7a41-45d9-900c-5f1feba02624)


$ grep "omena" hedelmät.txt etsii rivit, joilla on omena

$ grep --color "omena" hedelmät.txt värittää sanan omena

$ grep -c "omena" hedelmät.txt laskee kuinka monta omenaa löytyy


En tiedä miksi omena ja banaani fuusioitui toisiinsa, mutta omenaanaani kuullostaa herkulliselta.


e) ## Pipe
![VirtualBoxVM_efOl6ikKuy](https://github.com/user-attachments/assets/a9d34fdb-3a0a-43f4-88f0-b1c274fa140f)

$ ls /bin: Listaa /bin-kansion sisällön.
|: Siirtää edellisen komennon tulosteen seuraavalle komennolle.
wc -l: Laskee rivien määrän (tässä tapauksessa tiedostojen lukumäärän).

f) ## Rauta
![VirtualBoxVM_NHY4hd2cwS](https://github.com/user-attachments/assets/62384231-9197-40db-9225-76e634fc40d6)
![VirtualBoxVM_9MR9hJlLdz](https://github.com/user-attachments/assets/4e4f3533-aba6-4395-b81e-3a84dfb6c990)

Koneen rauta

CPU: AMD Ryzen 5 3600: 6-ydintä

GPU: AMD Radeon RX 6800 XT 16GB VRAM

16Gb RAM-Muistia

VirtualBox

128KiB BIOS

4Gb System memory

Verkko 82540EM Gigabit Ethernet Controller- emuloitu verkkokortti VirtualBoxissa


Koska tein ensimmäiset harjoitukset eri koneella, nyt huomasin, että VirtualBoxin asetuksia en muistanut muuttaa, ainakin virtuaalikoneelle varattua muistin määrää voisi nostaa ja prosessoriydinten määrää. Näin pitäisi suorituskyvyn parantua, mutta näissä tehtävissä ei ollut ongelmia.

h) ## plug-in

![VirtualBoxVM_JIe73EIAQK](https://github.com/user-attachments/assets/38c01420-00e3-4907-bc09-e90e46f126e5)

## Lähteet

https://terokarvinen.com/2020/command-line-basics-revisited/

https://www.geeksforgeeks.org/grep-command-in-unixlinux/


