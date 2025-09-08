# h3 Hello web server

## x) Lue ja tiivistä

- IP-pohjaiset virtuaalipalvelimet tarvitsevat jokaiselle verkkotunnukselle oman IP-osoitteen, kun taas nimiin perustuvat käyttävät verkkotunnusta (hostname), jonka avulla samalla IP-osoitteella tulevat sivustot voidaan erotella.
- Tämän johdosta nimiin perustuva tapa ei tarvitse yhtä paljon IP-osoitteita ja on monesti myös helpompi ratkaisu.
- Serverin nimen (ServerName) määrittäminen jokaiselle virtuaalipalvelimelle on tärkeää.
- Nimiin perustuvan virtuaalipalvelimen asennus (Apache)
  | Asennus ja konfigurointi|
  |-------------------------|
  |$ sudo apt-get -y install apache2|
  |$ echo "Default"|sudo tee /var/www/html/index.html|
  
  |Virtuaalipalvelimen määrittely|
  |------------------------------|
  |$ sudoedit /etc/apache2/sites-available/pyora.example.com.conf|
  |$ cat /etc/apache2/sites-available/pyora.example.com.conf|
  |<VirtualHost *:80>|
  |ServerName pyora.example.com|
  |ServerAlias www.pyora.example.com|
  |DocumentRoot /home/xubuntu/publicsites/pyora.example.com|
  |<Directory /home/xubuntu/publicsites/pyora.example.com>|
  |Require all granted|
  |</Directory>|
  |</VirtualHost>|
  |$ sudo a2ensite pyora.example.com|
  |$ sudo systemctl restart apache2|

  |Sisällön luominen|
  |-----------------|
  |$ mkdir -p /home/xubuntu/publicsites/pyora.example.com/|
  |$ echo pyora > /home/xubuntu/publicsites/pyora.example.com/index.html|

  |Testaus|
  |-------|
  |$ curl -H 'Host: pyora.example.com' localhost|
  |$ curl localhost|

- Lähteet: https://httpd.apache.org/docs/2.4/vhosts/name-based.html, https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

## a) Testaa, että weppipalvelimesi vastaa localhost-osoitteesta

- Apache-palvelin asennettu jo aiemmin edeltävän oppitunnin yhteydessä.
  
<img width="630" height="252" alt="Läksy_3_1" src="https://github.com/user-attachments/assets/c4212797-2285-4b70-ad55-53efbc2ae4c3" />

- Nyt testattu, että palvelin vastaa localhost-osoitteesta. Katsottu myös palvelimen status.

## b) Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit (eli selitä yksityiskohtaisesti jokainen kohta ja numero, etsi tarvittaessa lähteitä).

<img width="632" height="173" alt="Läksy_3_2" src="https://github.com/user-attachments/assets/5e49b21c-998f-4bd2-ab86-b270d36056f0" />

- Kaikissa riveissä 127.0.0.1 on localhostin IP-osoite.
- "GET" on HTTP-pyyntö ts. mitä ladattiin. / haetaan juurihakemistoa ts. etusivua. HTTP/1.1 on käytetty protokollaversio. /favicon.ico haetaan verkkosivuston ikonia (näkyy esim. välilehdessä).
- Ensimmäiset luvut HTTP-pyynnön jälkeen (200, 304, 404) on HTTP-statuskoodeja. 200 tarkoittaa onnistunutta palvelinpyyntöä ja vastausta. 304 tarkoittaa, että sivu ei ole muuttunut edellisen käynnin jälkeen, ja voidaan hyödyntää välimuistia. 404 tarkoittaa, ettei haettua asiaa ole löytynyt.
- Toinen kolminumeroinen luku statuskoodien jälkeen on vastauksen koko tavuina (248, 304, 247)
- Loppuosassa on käyttäjän selain ja käyttöjärjestelmä.

Lähteet: tehtävän tiedonhaussa hyödynnetty Microsoft Copilotia.

## c) Etusivu uusiksi

<img width="440" height="369" alt="Läksy_3_4" src="https://github.com/user-attachments/assets/ec954e97-9bdf-4250-ad44-a4e082ec4c1a" />

<img width="384" height="115" alt="Läksy_3_5" src="https://github.com/user-attachments/assets/cc498406-e850-4568-b8ca-175a3eee4e90" />

<img width="395" height="127" alt="Läksy_3_7" src="https://github.com/user-attachments/assets/9dd02d58-0411-466d-8676-7de305b49d20" />

## d) Tee validi HTML5-sivu

<img width="432" height="278" alt="Läksy_3_6" src="https://github.com/user-attachments/assets/69124831-14bf-48c2-8d90-229370afc447" />





