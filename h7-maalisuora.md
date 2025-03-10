### Maalisuora

## Rauta

Kotiverkko

Windows 11 Pro 64Bit

CPU: AMD Ryzen 5 3600: 6-ydintä 3.60GHz

GPU: AMD Radeon RX 6800 XT 16GB VRAM

16,0 Gt RAM-Muistia
![kuva](https://github.com/user-attachments/assets/f2ea1737-7cca-4ad0-b4db-09c38adc61f3)

## a) Hei maailma!

Aloitin tehtävän tekemisen asentamalla python3 ja java (jdk), bash on asennettuna valmiiksi linux-järjestelmissä.

![kuva](https://github.com/user-attachments/assets/2b477954-653d-47cc-9d20-2bbf4f949780)

![kuva](https://github.com/user-attachments/assets/a804b096-c749-4fdc-9af4-a59b72ff4d0e)

![kuva](https://github.com/user-attachments/assets/e69169f6-4e6d-46c9-908b-3848bcf477cf)

Bash:

![kuva](https://github.com/user-attachments/assets/07e7a604-b94f-4a5f-b2ac-2854ba2f9659)

![kuva](https://github.com/user-attachments/assets/435687e7-8cd5-4101-9671-710b8640c02f)

![kuva](https://github.com/user-attachments/assets/b71dd726-cea3-4446-ae20-9840cbd3c420)

Python3:

![kuva](https://github.com/user-attachments/assets/03ae47d1-29fc-4c4d-8b32-8320251b17f2)

![kuva](https://github.com/user-attachments/assets/71c87a06-d5c2-4aca-9cdb-dffdb3938adf)

![kuva](https://github.com/user-attachments/assets/2fa73708-2929-4706-91e5-e24691a19c7a)

Java:

![kuva](https://github.com/user-attachments/assets/f1fe885b-0d45-401a-a67e-b84614067203)

![kuva](https://github.com/user-attachments/assets/a4da4620-d307-4dd3-9cb4-879071010e57)

![kuva](https://github.com/user-attachments/assets/f87c1e17-f5e0-43bd-9807-83589a07e19b)

## C) Oma komento

Aloitin oman komennon tekemisen tekemällä timezone nimisen tiedoston

![kuva](https://github.com/user-attachments/assets/dfd72193-56de-44ef-b359-cc4c28048596)

Sitten loin skriptin, joka näyttää aikavyöhykkeen ajan:
```
#!/bin/bash
# timezone - Show timezone
# Tekijä: [Joonas Glad]

#Check timezone
if [ -z "$1" ]; then
    echo "Usage: timezone [TIMEZONE]"
    echo "Example: timezone UTC/EET"
    echo "Example: timezone Europe"
    exit 1
fi

# Display the time in the given timezone
echo "Current time in $1:"
env TZ="$1" date +"%d-%m-%Y %T %Z"


```

Testasin komentoa bash timezone EET:

![kuva](https://github.com/user-attachments/assets/c7349593-1f92-4048-ba5a-d406ef808c6b)

bash timezone ja bash timezone UTC:

![kuva](https://github.com/user-attachments/assets/0ebed7f3-f9ba-442b-8532-6ce12c3d8780)

Tein tiedoston root-käyttäjällä, toivottavasti se ei aiheuta ongelmaa. Seuraavaksi siirsin tiedoston **/usr/local/bin**

![kuva](https://github.com/user-attachments/assets/434854eb-9832-47b0-8c10-aa2d6c64381f)

ja annoin tiedostolle käyttöoikeudet


![kuva](https://github.com/user-attachments/assets/d953c511-e850-47e8-9e5e-34f07aa94d81)


Toimii normaalilla käyttäjällä komento:

![kuva](https://github.com/user-attachments/assets/a42d0220-4f7f-481b-9af6-8bd848b7b395)

d)

Loin kansion report ja lisäsin sinne index.md tiedoston

![kuva](https://github.com/user-attachments/assets/fde587e6-3134-4f31-9369-fda333720c0e)

![kuva](https://github.com/user-attachments/assets/2edf79a2-481a-4881-b99b-eac71c415585)

![kuva](https://github.com/user-attachments/assets/86cb9b6e-9394-4397-9e61-e6c79bd9928d)


Sitten muokkasin poistamalla read ja execute oikeuksia group ja others

![kuva](https://github.com/user-attachments/assets/39868824-c848-4bec-a63e-40a3ba4a0f04)




## Lähteet:

Tehtävänanto:
https://terokarvinen.com/linux-palvelimet/

Tehtävä a)
https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/

Tehtävä c)
https://terokarvinen.com/2007/12/04/shell-scripting-4/
16.3. Time / Date Commands: https://tldp.org/LDP/abs/html/timedate.html#CLOCKREF

Tehtävä d)
https://terokarvinen.com/2024/arvioitava-laboratorioharjoitus-2024-linux-palvelimet/










