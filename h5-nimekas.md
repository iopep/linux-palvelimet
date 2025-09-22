# h5 Nimekäs

## a) Nimi. Laita julkinen nimi osoittamaan koneeseesi.

En halunnut ostaa oikeaa julkista nimeä, sillä en tee sillä toistaiseksi mitään. Hankin nimen siinä vaiheessa, jos / kun tarvitsen sitä pysyvämmin. Nykyään on jo liikaa erilaisia kuukausitilauksia vähän joka suuntaan, joten tämä on tällaista henkilökohtaista hallinnan tunteen lisäämistä. Summa summarum simuloin nimen toimintaa paikallisesti hosts-tiedoston avulla. Ohjeita tehtävän suorittamiseen hain Copilotilla ja ChatGPT:llä. Lisäksi lueskelin seuraavia lähteitä:

1. https://serverfault.com/questions/332663/simulate-different-domains-on-the-same-machine
2. https://stackoverflow.com/questions/2904736/best-way-to-simulate-a-domain
3. https://serverfault.com/questions/1031180/dns-server-for-fake-domain-for-internal-testing-usage-only-on-linux

- Eli virtuaalikone auki ja ssh-yhteys virtuaalipalvelimeen (ssh ilkka@tähänomaip).
  
<img width="425" height="284" alt="Läksy_5_1" src="https://github.com/user-attachments/assets/28641f6f-f31b-4df8-80a3-af25db89a978" />

- Muokattu /etc/hosts -tiedostoa ja lisätty sinne oman virtuaalipalvelimen ip-osoite ja perään testi domain. Käytetty .local-päätettä, ettei domain yritä yhdistää millekään oikealle sivustolle.
- Luotu uusi virtuaalipalvelimen konfiguraatio (sudo nano /etc/apache2/sites-available/huuhaamaa.conf)
<img width="427" height="254" alt="Läksy_5_2" src="https://github.com/user-attachments/assets/2c7d32ad-6580-4cc2-994c-74581acfa74a" />

