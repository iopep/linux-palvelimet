## h3 Hello web server

# x) Lue ja tiivistä

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

# a) Testaa, että weppipalvelimesi vastaa localhost-osoitteesta

- Apache-palvelin asennettu jo aiemmin edeltävän oppitunnin yhteydessä.
  
<img width="630" height="252" alt="Läksy_3_1" src="https://github.com/user-attachments/assets/c4212797-2285-4b70-ad55-53efbc2ae4c3" />
- Nyt testattu, että palvelin vastaa localhost-osoitteesta. Katsottu myös palvelimen status.

