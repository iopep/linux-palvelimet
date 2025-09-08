## h3 Hello web server

# x) Lue ja tiivistä

- IP-pohjaiset virtuaalipalvelimet tarvitsevat jokaiselle verkkotunnukselle oman IP-osoitteen, kun taas nimiin perustuvat käyttävät verkkotunnusta (hostname), jonka avulla samalla IP-osoitteella tulevat sivustot voidaan erotella.
- Tämän johdosta nimiin perustuva tapa ei tarvitse yhtä paljon IP-osoitteita ja on monesti myös helpompi ratkaisu.
- Serverin nimen (ServerName) määrittäminen jokaiselle virtuaalipalvelimelle on tärkeää.
Lähde: https://httpd.apache.org/docs/2.4/vhosts/name-based.html
- Nimiin perustuvan virtuaalipalvelimen asennus (Apache)
  - Asennus ja konfigurointi
      |$ sudo apt-get -y install apache2 |
      |$ echo "Default"|sudo tee /var/www/html/index.html |
  - Virtuaalipalvelimen määrittely
      $ sudoedit /etc/apache2/sites-available/pyora.example.com.conf
      $ cat /etc/apache2/sites-available/pyora.example.com.conf
      <VirtualHost *:80>
        ServerName pyora.example.com
        ServerAlias www.pyora.example.com
         DocumentRoot /home/xubuntu/publicsites/pyora.example.com
      <Directory /home/xubuntu/publicsites/pyora.example.com>
         Require all granted
      </Directory>
      </VirtualHost>
      $ sudo a2ensite pyora.example.com
      $ sudo systemctl restart apache2
  - Sisällön luominen
    - $ mkdir -p /home/xubuntu/publicsites/pyora.example.com/
      $ echo pyora > /home/xubuntu/publicsites/pyora.example.com/index.html
  - Testaus
    - $ curl -H 'Host: pyora.example.com' localhost
      $ curl localhost
