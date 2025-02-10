### Maailma kuulee 

## X) Tiivistys 

Teoriasta käytäntöön pilvipalvelimen avulla

a) Vuokraa julkinen palvelin ja asenna se, Susanna suosittelee GitHub Education pakettia.

d) Susanna ottaa SSH-yhteyden virtuaalipalvelimeen ja asentaa palomuurin. Sen jälkeen hän avaa SSH-portin ja ottaa palomuurin käyttöön.

e) Susanna asentaa DigitalOceanin virtuaalikoneelle Apache-webbipalvelimen ja tekee kotisivut.

f) Susanna päivitti palvelimen ohjelmat avaamalla SSH-yhteyden. 

-Molemmat tekstit käsittelevät virtuaalipalvelimen asennusta, käyttäjätilien luontia, palomuurin asetuksia ja ohjelmistopäivityksiä. SSH-yhteyden avaamista, root-tilin lukitsemista ja Apache-palvelimen asentamista.

## Rauta

Kotiverkko

Windows 11 Pro 64Bit

CPU: AMD Ryzen 5 3600: 6-ydintä 3.60GHz

GPU: AMD Radeon RX 6800 XT 16GB VRAM

16,0 Gt RAM-Muistia

![Näyttökuva 2025-02-09 213757](https://github.com/user-attachments/assets/b6bc5911-4376-4b69-ad5b-c69d7dfe8c44)

## a) Virtuaalipalvelimen vuokraus

Päätin vuokrata virtuaalipalvelimen DigitalOceanilta käyttäen GitHub Educationia.

Crete Droplets ja valitsin Debian 12 basic asetuksilla joka maksaa 6$ kuukaudessa.

![Näyttökuva 2025-02-09 223408](https://github.com/user-attachments/assets/69a6bd5b-447f-483c-bc62-2490baf02f6b)

![Näyttökuva 2025-02-10 154141](https://github.com/user-attachments/assets/8a1517c1-2db8-4164-b16a-59734b4691ea)


## b) alkutoimet virtuaalipalvelimelle

Ensin laitoin palomuurin kuntoon, hetki meni päätä raapiessa kun tuli "BAD Port" viesti, mutta se johtui kirjoitusvirheestä.

![kuva](https://github.com/user-attachments/assets/39bcc4d6-e427-4635-8fe6-71db74b07e16)

Sitten otin ssh-yhteyden virtuaalipalvelimeen, siitä tietää että on hyvä salasana että se menee ainakin kerran väärin.
$ ssh root@209.38.42.247
![kuva](https://github.com/user-attachments/assets/5aba7dc5-846a-4d27-955b-ad78add12b47)

Loin uuden käyttäjän komennolla $ sudo adduser joonas 

ja annoin käyttäjälle sudo oikeudet komennolla $ sudo adduser joonas sudo

Sen jälkeen otin uudelleen yhteyden ssh komennolla $ ssh joonas@209.38.42.247

![kuva](https://github.com/user-attachments/assets/67c63bbc-2694-4b90-a474-bcdc6b929b1a)

Sitten lukitsin rootin komennolla  $ sudo usermod --lock root

![kuva](https://github.com/user-attachments/assets/b5d5fd88-4de7-4b8b-8e62-7fedda4d30ce)

Tajusin onneksi vielä että minun pitää tehdä palomuuri asetukset vielä joten käytin komentoja

$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get install ufw

$ sudo ufw allow 22/tpc

$ sudo ufw allow 80/tpc

$ sudo ufw enable


## c) Asenna weppipalvelin omalle virtuaalipalvelimellesi.

Asensin Apache2 komennolla $ sudo apt-get install apache2

![kuva](https://github.com/user-attachments/assets/090ad4ae-6964-432e-8dc2-e1a77826949e)

Asennuksen jälkeen tarkastin, että saan palvelimelle yhteyden.

![kuva](https://github.com/user-attachments/assets/0c1cf398-5a6c-4598-8bc5-a6b613c5eee6)

Muutin vielä oletussivun $ echo komennolla

![kuva](https://github.com/user-attachments/assets/893a85aa-1c26-4b2a-93b8-72e6297ccbaa)


## Lähteet

Tehtävänanto: https://terokarvinen.com/linux-palvelimet/#h4-maailma-kuulee

Tiivistys ja ohjeet DigitalOceanin käyttöön: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

Tehtävät: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/





