### Nimipalvelun vuokraaminen

## Rauta

Kotiverkko

Windows 11 Pro 64Bit

CPU: AMD Ryzen 5 3600: 6-ydintä 3.60GHz

GPU: AMD Radeon RX 6800 XT 16GB VRAM

16,0 Gt RAM-Muistia
![kuva](https://github.com/user-attachments/assets/f2ea1737-7cca-4ad0-b4db-09c38adc61f3)

## NameCheap

a) 

Aion käyttää hyödykseni GitHub Education Student Developer Pack- tarjousta ja vuokrata nimen NameCheapin kautta. Aion käyttää ilmaista domainia kurssin aikana.

![Näyttökuva 2025-02-24 140244](https://github.com/user-attachments/assets/b700e2ff-a569-465b-98e4-1e54c4161280)

## Based
b) 

Menin NameCheapin sivuilla oman domainin "Advanced DNS" asetuksiin ja lisäsin oman Name Based Virtual Hostin IP-osoitteeni domainin A-tietueeksi

![kuva](https://github.com/user-attachments/assets/44e9eb25-108b-4079-be80-93ff5931a8f0)

Olin aikaisemmin tehnyt jo tehnyt "joonasglad.com.conf" tiedoston, joten minun piti muuttaa se oikeaksi palvelimellani
![kuva](https://github.com/user-attachments/assets/1b5fabcd-d64a-47e5-9237-2252a0836ca7)
![kuva](https://github.com/user-attachments/assets/7bea16f1-fb76-4d65-be18-468fce866753)

Sitten myös poiskytkin vanhan sivuston ja otin uuden konfiguroinnin käyttöön komennoilla

```
$ sudo a2dissite joonasglad.com.conf
$ sudo a2ensite joonasglad.me.conf
$ sudo systemctl reload apache2
```

## Kotisivut
c)

Aloitin tekemällä kotisivuilleni kaksi alasivua, directoryyn ~/var/www/html

![kuva](https://github.com/user-attachments/assets/1d490a0a-6aed-47e3-8a83-7c70f94ab688)

Testaus että kotisivu toimii:

![kuva](https://github.com/user-attachments/assets/58da4bb1-023b-4049-9e38-3a9e76799a07)

Sitten loin vain yksinkertaiset alasivut jotka linkittyy kotisivujen kanssa:

blogi

![kuva](https://github.com/user-attachments/assets/38562e87-97b3-429e-8363-41066b9a7b54)

projektit

![kuva](https://github.com/user-attachments/assets/31bb524e-caf0-4e9d-b383-9d3c445901e6)

## Alidomainit
d)
Menin NameCheapissa "Advanced DNS" asetuksiin ja lisäsin kaksi alidomainia, toinen A-tietue ja toinen CNAME

![kuva](https://github.com/user-attachments/assets/0ab79d77-13a2-4084-9c88-e92994fa6029)

Lisäsin alidomainit joonasglad.me.conf tiedostoon Server Alias kohtaan

![kuva](https://github.com/user-attachments/assets/16f093aa-0105-43e5-8bf5-95f147289277)

## DNS-tietojen tutkiminen

e)

host- komento
![kuva](https://github.com/user-attachments/assets/9e96933e-e2d2-434d-a8b4-825d6fc482bf)

A-tietue on oikein: joonasglad.me → 209.38.42.247


dig komennon asensin käyttäen ohjeita sivustolta: https://superuser.com/questions/141623/installing-dig-on-debian

```
apt-get install -y dnsutils
```
dig- komento

![kuva](https://github.com/user-attachments/assets/078e4dc4-34be-422c-9d01-3b74530e69e6)

Kysytään A-tietuetta domainista joonasglad.me
Query time: 12 ms – DNS-kyselyn vastausaika.
SERVER: DNS-palvelin, joka vastasi kyselyyn 67.207.67.2


Kokeilin seuraavaksi pienen yrityksen sivuja, jonka mainos tuli vastaan.

![kuva](https://github.com/user-attachments/assets/65c1a326-e8d9-4a68-a465-1b28fb57b335)
Domain väriveljet.fi osoittaa IP-osoitteeseen 94.237.114.154.
![kuva](https://github.com/user-attachments/assets/0b761384-8ff0-4f1b-9e3e-789eb541551d)

Sitten kokeilin microsoft.com 

![kuva](https://github.com/user-attachments/assets/6cdbe70d-a8a4-42f0-8323-f6641648a673)
![kuva](https://github.com/user-attachments/assets/fea1fa96-84d1-4834-a84b-bcd6fa3613a3)

 microsoft.com palauttaa useita IP-osoitteita, kaikki Azure-alueella
 Jokaisen A-tietueen TTL on 70 sekuntia.

## Lähteet

https://terokarvinen.com/linux-palvelimet/#h5-nimekas

https://education.github.com/pack

https://cloud.digitalocean.com/

https://www.namecheap.com/

https://superuser.com/questions/141623/installing-dig-on-debian





