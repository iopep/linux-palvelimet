# h5 Nimekäs

## a) Nimi. Laita julkinen nimi osoittamaan koneeseesi.

En halunnut ostaa oikeaa julkista nimeä, sillä en tee sillä toistaiseksi mitään. Hankin nimen siinä vaiheessa, jos / kun tarvitsen sitä pysyvämmin. Nykyään on jo liikaa erilaisia kuukausitilauksia vähän joka suuntaan, joten tämä on tällaista henkilökohtaista hallinnan tunteen lisäämistä. Summa summarum simuloin nimen toimintaa paikallisesti hosts-tiedoston avulla. Ohjeita tehtävän suorittamiseen hain Copilotilla ja ChatGPT:llä. Lisäksi lueskelin seuraavia lähteitä:

1. https://serverfault.com/questions/332663/simulate-different-domains-on-the-same-machine
2. https://stackoverflow.com/questions/2904736/best-way-to-simulate-a-domain
3. https://serverfault.com/questions/1031180/dns-server-for-fake-domain-for-internal-testing-usage-only-on-linux

- Eli virtuaalikone auki ja ssh-yhteys virtuaalipalvelimeen (ssh ilkka@tähänomaip).
  
<img width="425" height="284" alt="Läksy_5_1" src="https://github.com/user-attachments/assets/28641f6f-f31b-4df8-80a3-af25db89a978" />

- Muokattu /etc/hosts -tiedostoa ja lisätty sinne oman virtuaalipalvelimen ip-osoite ja perään testi-domain (huuhaamaa.local). Käytetty .local-päätettä, ettei domain yritä yhdistää millekään oikealle sivustolle.

<img width="427" height="254" alt="Läksy_5_2" src="https://github.com/user-attachments/assets/2c7d32ad-6580-4cc2-994c-74581acfa74a" />

- Luotu uusi virtuaalipalvelimen konfiguraatio (sudo nano /etc/apache2/sites-available/huuhaamaa.conf).

<img width="216" height="56" alt="Läksy_5_3" src="https://github.com/user-attachments/assets/afc2107f-e470-4387-aaae-115ee1958c47" />

- Otettu konfiguraatio käyttöön.

<img width="533" height="286" alt="Läksy_5_4" src="https://github.com/user-attachments/assets/3656d408-58a6-481d-a75b-56beddfcd0b4" />

- Testattu huuhaamaa.local ja törmätty ongelmiin.
- Palattu hieman lähteistä löytämissä ohjeissa taakse päin ja todettu, että /etc/hosts tiedostoon tehdyt muokkaukset tehty kirjautuneena ssh-yhteydellä virtuaalipalvelimelle. Ilmeisesti tämä olisi pitänyt tehdä paikallisesti virtuaalikoneella, joten avattu toinen terminaali ja testattu tätä (sudo nano /etc/hosts/).

<img width="403" height="254" alt="Läksy_5_5" src="https://github.com/user-attachments/assets/823649e4-15ed-47b4-8285-4d76efa1b86a" />

- Lisätty virtuaalipalvelimen ip-osoite ja perään haluttu testi-domain (huuhaamaa.local).

<img width="412" height="234" alt="Läksy_5_6" src="https://github.com/user-attachments/assets/cc2997ed-3e68-46c3-80df-ed89b5fda975" />

- Testattu uudestaan selaimessa menemällä huuhaamaa.local ja tällä kertaa homma pelittänyt.

## b) Alidomain. Tee kaksi uutta alidomainia, jotka osoittavat omaan koneeseesi.

- Muokattu virtuaalipalvelimen konfiguaartiotiedostoa (sudo nano /etc/apache2/sites-available/huuhaamaa.conf).

<img width="430" height="105" alt="Läksy_5_7" src="https://github.com/user-attachments/assets/105b0cf5-3b94-4881-b755-923650f8060d" />

- Lisätty alidomainit (totta.huuhaamaa.local & tarua.huuhaamaa.local).
- Otettu konfigraatio käyttöön ja ladattu Apache-palvelin uudelleen (sudo a2ensite huuhaamaa.conf
sudo systemctl reload apache2).

<img width="485" height="51" alt="Läksy_5_8" src="https://github.com/user-attachments/assets/6e4530ac-b6f9-45cc-b272-7bfe303ddd77" />

- Lisätty paikalliseen /etc/hosts tiedostoon alidomainit.

<img width="350" height="102" alt="Läksy_5_9" src="https://github.com/user-attachments/assets/199e2342-a63a-4006-a95a-2aeadee3452c" />

<img width="292" height="108" alt="Läksy_5_10" src="https://github.com/user-attachments/assets/e29edb13-b73e-460f-b029-e969b4d52bfa" />

- Testattu alidomainien toimivuus.

## c) Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla

Koska tein aiemmat tehtävät paikallisesti simuloiden, testattu tässä tehtävässä vain ulkopuolisia sivustoja.

<img width="236" height="85" alt="Läksy_5_11" src="https://github.com/user-attachments/assets/cb9a9697-1aae-4e32-b17c-81716edc937c" />

- Yritetty tutkailla man dig ja man host -komennoilla niiden sisältöä, mutta ylläolevat ilmoitukset pamahtaneet terminaaliin. Kyselty Copilotilta mahdollisia syitä, joka ehdottanut kokeilemaan asentamaan tarvittavat paketit (sudo apt update, sudo apt install dnsutils &  instalsudo apt install bind9-host).
- Nämä asennustoimenpiteet auttaneet ja päästy tarkastelemaan manuaalia tarvittavilta osin.

<img width="372" height="245" alt="Läksy_5_12" src="https://github.com/user-attachments/assets/2805b11e-ad1f-4626-970a-4b2ce70eca73" />

- Kokeiltu host ja dig -komentoja osoitteelle rannekkeet.fi

<img width="369" height="255" alt="Läksy_5_13" src="https://github.com/user-attachments/assets/9d677d24-4305-42aa-9271-897c154f59e8" />

- Kokeiltu samat komennot myös osoitteelle google.com

- Eroja havaittu lähinnä host google.com -komennon palauttamassa viimeisessä rivissä (google.com has HTTP service bindings 1 . alpn="h2,h3").
- Etsin tietoa Copilotilla ja ChatGPT:llä siitä, mitä tämä tarkoittaa käytännössä, mutta kokonaisselostukset menivät itseltä hieman ohi. Rivi viittaa kuitenkin ilmeisesti mahdollisuuteen muodostaa yhteys nopeammin (palvelin- ja protokollatietoja voidaan välittää DNS:n kautta tjsp. Ihan tarkkaan en kokonaisuutta ymmärtänyt, joten en viitsi yrittää selittää sitä yhtään monimutkaisemmin).
- Yhteisiä palautuksia ovat ip-osoitteet ja sähköpostipalvelin.

<img width="266" height="97" alt="Läksy_5_14" src="https://github.com/user-attachments/assets/a30766a5-b7a0-427c-835b-9fa6ec7ade40" />

- Testattu komentoa host -t ns osoitteille. Tämä palauttaa domainien nimipalvelimet (Name Servers). Nimipalvelimet vastaavat domainin DNS-kyselyihin (lähde: Copilot).



  Muut lähteet: https://terokarvinen.com/2024/linux-palvelimet-2024p1-alkusyksy-ici003as2a-3010/




