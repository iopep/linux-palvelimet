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


