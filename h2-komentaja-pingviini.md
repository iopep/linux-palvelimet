## h2 Komentaja Pingviini

# x) Lue ja tiivistä

- Toimenpiteet suoritetaan mahdollisimman vähillä käyttöoikeuksilla. Ainoastaan toiminnot, jotka vaativat laajempia oikeuksia, suoritetaan käyttämällä sudo-komentoa. Sudo tarkoittaa rajattomia käyttöoikeuksia. 
- Tiedostojen hakemista varten Linuxissa täytyy muistaa vain muutama hakemisto. Nämä ovat samoja kaikissa Linux-järjestelmissä:
  -  /
  - /home/
  - /home/nimi/
  - /etc/
  - /media/
  - /var/log/
    
 Lähde: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited#help
-	Vaikka komentorivin peruskomennot vaikuttivat ennen viime oppituntia melko heprealta, niin niiden perusidea tarttui yllättävän nopeasti mieleen ihan vain kokeilemalla ja ”leikkimällä”.

# a) Micro. Asenna micro-editori

<img width="692" height="469" alt="homework_2_1" src="https://github.com/user-attachments/assets/6acbaae8-d2ef-4468-922b-bca2189fe881" />

Micro-editorin asennus.

<img width="576" height="360" alt="homework_2_2" src="https://github.com/user-attachments/assets/61adf2fd-8c82-4810-b586-63de19051915" />

Editori asennettu.

# b) Kolmen komentoriviohjelman asennus ja testaus

<img width="673" height="457" alt="homework_2_3" src="https://github.com/user-attachments/assets/0f84318c-87d3-425e-aa82-eaceca54f08d" />

Komentoriviohjelmien asennus.

<img width="673" height="457" alt="homework_2_4" src="https://github.com/user-attachments/assets/da918c99-c35e-4d11-848a-f2378612175b" />

Git-testausta.

<img width="673" height="457" alt="homework_2_5" src="https://github.com/user-attachments/assets/ff71296b-4aab-4fde-b2cb-97e28d949e93" />

<img width="673" height="457" alt="homework_2_6" src="https://github.com/user-attachments/assets/08a0ac54-c747-450b-9d23-c9bc8a74acb1" />

Curl-testausta.

<img width="673" height="457" alt="homework_2_7" src="https://github.com/user-attachments/assets/99abb689-bc81-400b-876a-3cc4eaf1357b" />

<img width="673" height="457" alt="homework_2_8" src="https://github.com/user-attachments/assets/740332a7-49d3-48ad-a711-66c26ccb276f" />

Htop-testausta.

# c) Tärkeät kansiot

Tässä tehtävässä käytetty lähteenä Microsoft Copilotin hakua tiedon etsintään ja komentojen selvittämiseen.

<img width="673" height="457" alt="homework_2_9" src="https://github.com/user-attachments/assets/5b82a875-87ea-4cbf-b9de-ef330097e2c6" />

Root-hakemistossa ( / ) olevat boot-kansio sisältää kaikki ne tiedot joita tarvitaan käynnistysvaiheessa (ennen varsinaisen käyttöjärjestelmän latautumista). 

<img width="277" height="109" alt="homework_2_10" src="https://github.com/user-attachments/assets/6f2650e8-f9d1-4ce8-b6e4-e7df8cde125a" />

/home-kansiossa on kansio "ilkka", joka sisältää kaikki minun henkilökohtaiset tiedostot, kansiot ym. eli se on henkilökohtainen kotihakemistoni.

<img width="413" height="44" alt="homework_2_11" src="https://github.com/user-attachments/assets/62677327-9048-49df-816a-dc56f6def23c" />

/home/ilkka-kansiossa on kansio "rmtest", joka sisältää edellisen oppitunnin harjoituskansioita ja kikkailuita.

<img width="385" height="152" alt="homework_2_12" src="https://github.com/user-attachments/assets/08aeb624-dabd-49ed-889e-857a5922322c" />

/etc-kansiossa on tiedosto hostname, joka sisältää järjestelmän tunnistenimen, tässä tapauksessa "linux-test".

<img width="255" height="27" alt="homework_2_13" src="https://github.com/user-attachments/assets/30656e67-0d64-4c59-9414-7573c459aa7f" />

/media-kansiossa oleva cdrom0-kansio on liitoskohta cd- tai dvd-asemalle.

<img width="518" height="62" alt="homework_2_14" src="https://github.com/user-attachments/assets/f76e54cf-b06e-4c26-8ebc-7d9271356f85" />

/var/log-kansiossa oleva sysstat-kansio sisältää työkaluja järjestelmän seurantaan.

# d) The Friendly M.

<img width="265" height="93" alt="homework_2_15" src="https://github.com/user-attachments/assets/c2dad635-e838-480b-b992-5ed6cf7a613c" />

Esimerkkejä grep-komennon käytöstä. Apuna eri käyttötapojen etsinnässä käytetty Microsoft Copilotia.

# e) Pipe

<img width="285" height="37" alt="homework_2_16" src="https://github.com/user-attachments/assets/2f3f1aa1-9a41-49f2-903c-f25529baa324" />

# f) Rauta

<img width="500" height="349" alt="homework_2_17" src="https://github.com/user-attachments/assets/d25a4faf-9495-4249-8204-00f4a9d58c0f" />

- H/W path kertoo kyseisen laitteen sijainnin laitteistopuussa.
- Device näyttää laitteen nimen, mikäli tämä on saatavilla.
- Class-kohdassa näkyy laitetyyppi eli esimerkiksi prosessori, muisti jne.
- Description antaa lisätietoja kyseisestä laitteesta. Esimerkiksi "processor" kohdassa näkyy prosessorin tarkat laitetiedot.
- short- ja sanitize-komentojen avulla näytetään tiivistetty listaus järjestelmästä. Tästä on poistettu yksilöivät tunnisteet ja tiedot, joten kyseisen listauksen jakaminen esimerkiksi osana tätä tehtävää on turvallista. Short-komento näyttää tiivistetyn listauksen ja sanitize-komento turvallisen version eli poistaa mm. MAC-osoitteet.
- Listausta voidaan hyödyntää esimerkiksi, jos on jotain ongelmia ja tarvitaan ulkopuolista apua. Tällöin järjestelmän kokoonpanotiedot voidaan jakaa turvallisesti ja hyödyntää ongelmanratkaisussa.


















