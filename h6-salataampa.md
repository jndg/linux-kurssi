### Salataampa

## Rauta

Kotiverkko

Windows 11 Pro 64Bit

CPU: AMD Ryzen 5 3600: 6-ydintä 3.60GHz

GPU: AMD Radeon RX 6800 XT 16GB VRAM

16,0 Gt RAM-Muistia
![kuva](https://github.com/user-attachments/assets/f2ea1737-7cca-4ad0-b4db-09c38adc61f3)

## x) Tiivistys

https://letsencrypt.org/how-it-works/

Let's Encryptin ja ACME-protokollan tavoite on HTTPS-palvelimen asennus ja sertifikaatin hankkiminen automaattisesti, ilman ihmisen väliintuloa. Sertifikaattien hallinta toimii verkkopalvelimella.

Verkkotunnuksen validointi:
  ```
-Agentti todistaa CA:lle hallitsevansa verkkotunnusta.
-Todistus tehdään joko DNS-tietueella tai HTTP-tiedostolla.
-CA tarkistaa haasteen ja hyväksyy tunnistuksen.
```

Sertifikaatin myöntäminen ja hallinta:
```
-Agentti pyytää, uusii ja peruu sertifikaatteja allekirjoitetuilla viesteillä.
-CA myöntää sertifikaatin ja tallentaa sen julkisiin CT-lokeihin.
-Peruutukset ilmoitetaan selaimille OCSP:n kautta.
```
Käyttö olemassa olevan verkkopalvelimen kanssa:

https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server

```
-Jos palvelin käyttää porttia 80 --http, tarvitsee --http.webroot-asetuksen.
-Tämä tallentaa http-01-haasteen .well-known/acme-challenge-hakemistoon ilman uuden palvelimen käynnistämistä.
-Hakemiston on oltava julkisesti saatavilla verkkotunnuksen juurena.
-Jos hakemisto ei ole suoraan saatavilla, voi käyttää URL-uudelleenkirjoitusta.

```

 SSL:
```
-Name-based virtual hostit voivat käyttää SSL:ää, mutta kaikki verkkotunnukset jakavat saman sertifikaatin.
-SSLCipherSuite voi rajoittaa tai sallia tietyt salausalgoritmit.
-Yleinen SSLCipherSuite-asetus koskee koko palvelinta, mutta sitä voi muuttaa Location-lohkoilla eri URL-poluille.
-SSL-parametrit voidaan neuvotella uudelleen, jos tietty URL vaatii vahvempia salauksia.
```

## a) Let's Encrypt -sertifikaatti lego-työkalulla domainille
Kun aloitin tehtävien tekemisen, apache2 ei aluksi toiminut

![kuva](https://github.com/user-attachments/assets/0814b44c-af18-4c21-837e-e3b3a66bd241)

Menin katselemaan error lokeja

![kuva](https://github.com/user-attachments/assets/64176abb-fece-40f7-8f02-e3959f93167a)
![kuva](https://github.com/user-attachments/assets/76702163-1c08-4fa6-85a6-d33247c41026)

Olin epähuomiossa tallentanut sivustoni conffi tiedoston ilman ">" merkkiä, joten tämä error johtui siitä. Korjasin tilanteen lisäämällä puuttuvan merkin ja käynnistin apache2 uudelleen.

Potkaisin demonia

Verkkosivut toimii nyt; 

![kuva](https://github.com/user-attachments/assets/6805af8d-db36-409e-958e-c31d7a4c4d87)

Sitten latasin legon

![kuva](https://github.com/user-attachments/assets/2211f82d-8a4b-47d1-8f78-0420669820e9)

Seuraamalla ohjeita, koska minulla on jo voimassa oleva palvelin portissa 80*, seuraavaksi loin uuden hakemiston weppisivun document-rootiin komennolla
```
$ mkdir -p /home/joonas/public_html/.well-known/acme-challenge
```
ja annoin kirjoitus oikeudet myös hakemistoon

Seuraavaksi hankin sertifikaatin domainilleni käyttämällä ohjeiden mukaan lego-komentoa
```
$ lego --accept-tos --email you@example.com --http --http.webroot /path/to/webroot --domains example.com run
```

![kuva](https://github.com/user-attachments/assets/ffc22ea8-d9fe-4650-8405-2754230cadbe)


Loin varmuuskopion legon suosituksia seuraten.

Seuraavaksi otin SSL-sertifikaatin käyttöön Apachessa.

Varmistin ensin että ssl-moduuli on käytössä komennoilla
```
$ sudo a2enmod ssl
$ sudo systemctl restart apache2
```
Tarkistin että sertifikaatit ovat domainilleni, näitä pystyi tarkistelemaan vain root-oikeuksilla. Sertifikaatit olivat oikein.
![kuva](https://github.com/user-attachments/assets/e01e6b62-e3ec-4ad3-a84e-f98f1135cad8)

Seuraavaksi muokkasin domainin VirtualHost-konfiguraatiota, niin että otetaan käyttöön ssl (portti 443) sekä HTTP-redirect (portti 80) käyttäen ohjeita jotka löysin täältä: https://stackoverflow.com/questions/11621053/redirect-http-to-https-on-default-virtual-host-without-servername

```
RewriteEngine on
RewriteCond %{HTTPS} off [OR] 
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [NC,R=301,L]
```

Konfiguraation kanssa meni yllättävän kauan, käytin myös ChatGPT apuna:
![kuva](https://github.com/user-attachments/assets/17e8c164-36f6-4d91-96e0-892820fdbb13)

Olisin voinut luoda kokonaan uudenkin konfiguraation, joka olisi luultavasti ollut helpompaa. Ongelmana oli virheilmoitus
```
AH00526: Syntax error on line 7 of /etc/apache2/sites-enabled/joonasglad.me.conf:
Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
```

Tämä tarkoitti, että Apache ei tunne "RewriteEngine"
Ratkaisin asian ottamalla mod_rewrite-moduulin käyttöön komennnolla
```
$ sudo a2enmod rewrite
$ sudo systemctl restart apache2
```
jonka jälkeen konfiguraatio toimi.

![kuva](https://github.com/user-attachments/assets/8663671b-b880-48a4-88be-92e330bb8d0f)

b) TLS- konfiguraation testaus SSLLabs

![kuva](https://github.com/user-attachments/assets/d1adc554-4928-4491-83a7-04898b04ed65)

![kuva](https://github.com/user-attachments/assets/823a38bc-498c-4cad-87e9-6912a5f04548)

![kuva](https://github.com/user-attachments/assets/82631b05-36a5-4544-8fff-2db635b097f4)

## Lähteet

https://terokarvinen.com/linux-palvelimet/

https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample

https://foorumi.linux.fi/

https://stackoverflow.com/questions/11621053/redirect-http-to-https-on-default-virtual-host-without-servername

https://letsencrypt.org/getting-started/

https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/

https://www.ssllabs.com/ssltest/analyze.html?d=joonasglad.me










