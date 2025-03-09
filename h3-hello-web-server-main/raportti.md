## Alustus

Olin viikon kipeänä joten vähän myöhässä aloitan 6.2 klo 16:48

# Rauta
Kotiverkko

Windows 11 Pro 64Bit

CPU: AMD Ryzen 5 3600: 6-ydintä 3.60GHz

GPU: AMD Radeon RX 6800 XT 16GB VRAM

16,0 Gt RAM-Muistia

VirtualBox asetukset:
![Näyttökuva 2025-02-06 165513](https://github.com/user-attachments/assets/dcf89a94-bb0d-4b42-8a84-6876f0473a67)

## x) tiivistys

-IP-based Virtual Hosts käyttää IP-osoitetta tunnistamaan oikean palvelimen

-Name-based Virtual Hosts palvelin luottaa asiakkaan lähettämään hostname-tietoon HTTP-otsikoissa

-Apachella voi hostaa useita verkkosivuja samalla IP-osoitteella

# a) Testaa, että weppipalvelimesi vastaa localhost-osoitteesta. Asenna Apache-weppipalvelin, jos se ei ole jo asennettuna. 18:00

![Näyttökuva 2025-02-06 181156](https://github.com/user-attachments/assets/4e3bc900-950b-4091-82a4-69e6fa336df4)

Tarkastelin apache2 lokeja, koska weppipalvelimeni ei näkynyt. Päättelin lokeista että Apachella ei ole tarvittavia käyttöoikeuksia Documentroottiin.

Ratkaisin ongelman vaihtamalla documentrootin 

$ sudo mkdir -p /var/www/publicsites

$ sudo cp -R /home/joonas/publicsites/* /var/www/publicsites/

Ja sen jälkeen vaihdoin vielä konfiguraatiotiedostoon oikean document rootin
![Näyttökuva 2025-02-06 185433](https://github.com/user-attachments/assets/d7d9fcc3-ca61-476c-915d-e87bbf1d28b2)


b) Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit (eli selitä yksityiskohtaisesti jokainen kohta ja numero, etsi tarvittaessa lähteitä). 18:30 

$ sudo tail -f /var/log/apache2/access.log

![Näyttökuva 2025-02-06 190157](https://github.com/user-attachments/assets/824fde43-b834-44f1-8a1b-6f0a5a936dd0)

-Lokeissa ainakin näkyy että pyyntö on lähtenyt IP-osoitteesta 127.0.0.1 joka on localhost


# c) Etusivu uusiksi 19:30

Loin ensin uuden conf tiedoston flunssa.example.com.conf

![Näyttökuva 2025-02-06 193343](https://github.com/user-attachments/assets/32c523c3-dd3b-476f-ac37-39fa54cd9d75)


![Näyttökuva 2025-02-06 194803](https://github.com/user-attachments/assets/23ccc264-69d9-4ded-b43e-6e7ff3930c3f)

 Huomasin sitten että pitikin olla nimi hattu, joten muutin vain nimeksi hattu.example.com.conf
 
![Näyttökuva 2025-02-06 195627](https://github.com/user-attachments/assets/1e6ecabb-b10e-40a1-b9bc-720b80381034)


![Näyttökuva 2025-02-06 195452](https://github.com/user-attachments/assets/593ad439-b110-4140-9ff2-b44d78e33b44)

Poistin vanhan sivun käyttäen komentoa
 $ sudo a2dissite

 Sitten loin uuden sivun seuraten ohjeita mitä aikaisemmin käytettiin

![Näyttökuva 2025-02-06 205543](https://github.com/user-attachments/assets/81793e90-13c1-42f0-b166-ebc94ebe946c)

# e) HTML5 sivu

![Näyttökuva 2025-02-06 210354](https://github.com/user-attachments/assets/45882619-7159-4d70-b7b5-18314c8573c1)

# f) curl komento

![Näyttökuva 2025-02-06 210754](https://github.com/user-attachments/assets/4d391089-c0de-4755-ba55-a905b3b2ec96)

voi tarkistaa palvelimen vastauksen ja saada perustietoa ilman, että koko sisältöä ladataan.

## Lähteitä

https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

https://httpd.apache.org/docs/2.4/vhosts/name-based.html

https://stackoverflow.com/questions/48442884/how-to-specify-directory-name-to-create-virtual-host-in-apache2




