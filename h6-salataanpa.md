# h6 Salataanpa

## x) Lue ja tiivistä
- Let's Encrypt ja ACME protcol mahdollistavat HTTPS-yhteyttä käyttävän palvelimen pystyttämisen ja luotettavan sertifioinnin.
- Verkkotunnuksen hallinta todistetaan Let's Encryptille esimerkiksi DNS-tietueella.
- Onnistuneen tunnistuksen jälkeen HTTPS-varmenteita voi manageerata auktorisoitujen avainparien avulla.
- SSL-konfiguraation tulee sisältää vähintää seuraavat sisällöt:
  LoadModule ssl_module modules/mod_ssl.so

|Listen 443                                               |
|<VirtualHost *:443>                                      |
|    ServerName www.example.com                           |
|    SSLEngine on                                         |
|    SSLCertificateFile "/path/to/www.example.com.cert"   |
|    SSLCertificateKeyFile "/path/to/www.example.com.key" |
|</VirtualHost>                                           |
