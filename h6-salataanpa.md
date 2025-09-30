# h6 Salataanpa

## x) Lue ja tiivistä
- Let's Encrypt ja ACME protcol mahdollistavat HTTPS-yhteyttä käyttävän palvelimen pystyttämisen ja luotettavan sertifioinnin.
- Verkkotunnuksen hallinta todistetaan Let's Encryptille esimerkiksi DNS-tietueella.
- Onnistuneen tunnistuksen jälkeen HTTPS-varmenteita voi manageerata auktorisoitujen avainparien avulla.
- SSL-konfiguraation tulee sisältää vähintää seuraavat sisällöt:

  <img width="243" height="75" alt="Läksy_6_1" src="https://github.com/user-attachments/assets/2682c1b6-7afe-4009-9492-6b0da18dd8fb" />

- Lähteet:
1. https://letsencrypt.org/how-it-works/
2. https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample

## b) A-rating. Testaa jonkin sivuston TLS.

- Testattu sivuston www.ilmatieteenlaitos.fi TLS käyttäen SSLLabsia (https://www.ssllabs.com/ssltest/)

<img width="545" height="441" alt="Läksy_6_2" src="https://github.com/user-attachments/assets/79cc073d-a73a-40f5-ad5e-0f9c2bb6ff1b" />

<img width="525" height="174" alt="Läksy_6_3" src="https://github.com/user-attachments/assets/1310e749-3d41-44ae-acaf-a36f56004511" />

- Yleisarvosana B kertoo ns. tiivistetyn arvion kyseisen sivuston TLS-suojauksesta. B arvosanana tarkoittaa pisteitä väliltä 65-79. B yleisarvosanana ei ole heikko, mutta kertoo siitä, että jotkin osiot sivuston salauksessa saattavat olla vanhentuneiden käytäntöjen mukaisia. (lähde: https://github.com/ssllabs/research/wiki/SSL-Server-Rating-Guide)

<img width="541" height="384" alt="Läksy_6_4" src="https://github.com/user-attachments/assets/62fbca16-f5a0-4afd-af77-fb3540999b83" />

- Arvioinnin yhteenvedon tarkastelusta voi huomata, että osa-alue Protocol support on selkeästi tiputtanut yleisarvosanaa A --> B.
- Protocol support osion painoarvo on 30 % kokonaisarvosanasta. Protocol supportin pistemäärä lasketaan seuraavasti:
  1. Ohjelma tarkastelee serverin käyttämän parhaan protokollan pistemäärän.
  2. Tähän lisätään huonoimman käytetyn protokollan pistemäärä.
  3. Tulos jaetaan kahdella.
     
  | Protokolla | Pisteiden lasku | 
  |---------|------| 
  | SSL 2.0 | 0 % |
  | SSL 3.0 | 80 % |
  | TLS 1.0 | 90 % |
  | TLS 1.1 | 95 % |
  | TLS 1.2 | 100 % |
  | TLS 1.3 | 100 % |

  Lähde: https://github.com/ssllabs/research/wiki/SSL-Server-Rating-Guide

<img width="498" height="362" alt="Läksy_6_5" src="https://github.com/user-attachments/assets/b76f69a5-a9ca-419b-9f4a-a255b85280b6" />

<img width="476" height="412" alt="Läksy_6_6" src="https://github.com/user-attachments/assets/088adb79-a556-4dca-af01-6e4423a72d74" />

- Tarkemmat tiedot testin tuloksista eivät kertoneet itselleni mitään ennestään mitään, joten tutkailin lähdettä https://learn.microsoft.com/en-us/power-platform/admin/server-cipher-tls-requirements. Ilmeisesti sivuston protokollaosion pisteitä laskee sen tarjoamat suojausyhdistelmät TLS 1.2 salauksessa. Sivusto tarjoaa toisena vaihtoehtona heikommaksi tiedettyjä salausversioita, mikä mahdollisesti (?) tiputtaa yleisarvosanaa. TLS 1.3 puolella samaa ongelmaa ei ole.





